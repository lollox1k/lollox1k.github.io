
The self-supervised task, also known as pretext task, guides us to a supervised loss function, e.g. by a Proxy task:

- _Rotate_: train a model to classify which rotation has been aplied, the idea is that this model need to learn a deep representation of the object
- _Relative position:_ choose a patch, give one of its neighbouring patches, let the model find where the patch was (classification)
- _jigsaw puzzle_: a more difficult task than the previous: shuffle the patches, the model need to find the permutation.
- _Colorization_: from grayscale to color.

Self-supervision _generates features_ that are good for downstream tasks.

For example in language modelling, we can predict a part of the input as a target.

### Contrastive learning
Learn representation such that similar samples are close to each other, dissimilar one are far.

Used in visio and language tasks, for example _face autentification_.

Just build a clever loss function:
$$
L_{cont}(x_i, x_j, \theta) = \mathbb{1}(y_i = y_j) \Vert f(x_i)-f(x_j) \Vert_2^2 + \mathbb{1}(y_i \neq y_j)\max(0, \epsilon -\Vert f(x_i)-f(x_j) \Vert_2)
$$
if the labels are equal, minimize le $L_2$ distance squared, if they are different, maximize the $L_2$ distance. Since the loss function need to be bounded from below, we introduce the max. Also we are fine if the distance is more than $\epsilon$, a positive "tollerance" parameter.

### Triplet Loss
Introduced in 2015 in FaceNet, the task was recognition of the same person at different poses and angles.

Given one anchor input $x$, we select a positive sample $x^+$ and a negative one $x^-$.

Our objective is to minimize the triplet loss:
$$
L_{trip}(x, x^+, x^-) = \sum_{x \in X} \max(0,\,\Vert f(x) - f(x^+)\Vert_2^2 - \Vert f(x) - f(x^-)\Vert_2^2 + \epsilon)
$$

### BYOL
It doesn't use negative example! 
Two identical networkds, _online_ and _target_.
We feed the same image, but with two different data transformation. 

The Loss is the cosine similarity between the networks (rescaled).
The weights of the target network are a time average of the weights of the online network:
$$
\xi = (1-\tau) \xi + \tau \theta
$$
we update online the $\theta$ weights of the online model.

After training one the online model is used, and the projection layer discarded.


### Barlow Twins
Again two identitcal networks but we feed the same image with a different transformation. The goal is to make the empirical cross-correlation matrix as close as possible to the identity.

![[Pasted image 20231016200458.png]]

$$
L_{BT} = \sum_{i} (1-C_{ii})^2 + \lambda \sum_i \sum_{j\neq i} C_{ij}^2
$$
where
$$
C_{ij} = \frac{\sum_b z_i^A z_j^B}{\sqrt{\sum_b (z_i^A)^2}\sqrt{\sum_b (z_i^B)^2}}
$$


