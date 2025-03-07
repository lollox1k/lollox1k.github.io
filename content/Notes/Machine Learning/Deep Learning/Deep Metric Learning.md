
In a _supervised setting_, the goal is to produce an embedding such that a fixed distance function is small for example in the same class, large for example in different classes.

Using contrastive methods, sometimes doesn't work well. For example you could end up with high variance between samples of the same class. A simple idea is to penalize this in the loss, the  **center loss**:

$$
L_{center} = L_{softmax} + \frac{\lambda}{2} \sum_{i=1}^N \Vert z_i - c_{y_i}\Vert_2^2
$$
where $c_{y_i}$ is the center of the class $y_i$ computed by averaging other examples of this class in the batch.