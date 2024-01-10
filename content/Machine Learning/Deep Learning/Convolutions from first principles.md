We would like to build from scratch a new neural network taking as input an image and producing as output another image. For example in semantic segmentation, each pixel in the input image is linked to a class.

When a object moves in the image, we want the associated labels to move with it. Hence, before constructing such a neural network, we first need to figure out a way to build a layer having this property: _when an object is translated in an image, the output of the layer should be translated with the same translation_. This is what we will do here.

### Mathematical model
Let's simplify our setting, instead of images our input are just vectors (tensors of dimension $1$). A translation of this vector is also called a  _shift_.
Define an operator $S$ that shifts to the right each component (modulo $n$), it'easy to see that
$$
S =
\begin{pmatrix}
0 &\dots & \dots & 0 & 1 \\
1 & 0 & \dots & 0 & 0 \\
0 & 1 & 0 & 0 & 0 \\
\vdots & \ddots & \ddots &\\
0 & 0 & 0 & 1 & 0 \\
\end{pmatrix}
$$
Now our task it to find a linear layer $W$ which _commutes_ with respect to S_:
when the input is shifted, the output is also shifted:
$$
WS = SW
$$
One can start from a random matrix $W$, and then gradient descent to minimize the rescaled norm of the commutator:
$$
\min_W \frac{\Vert SW-WS\Vert_2^2}{\Vert W \Vert_2^2}
$$
we rescale to remove the trivial solution $W = 0$.

![[Pasted image 20231016125853.png]]

Note the diagonal structure! This is a _circulant matrix_.

**Def** (_circulant matrix_) Given a vector $a = (a_0, a_1, \dots, a_{n-1})$ we define  the associated matrix $C_a$​ whose first column is made up of these numbers and each subsequent column is obtained by a shift of the previous column:
$$
C_a =
\begin{pmatrix}
a_0 & a_{n-1} & a_{n-2}  & \cdots & a_1 \\
a_1 & a_0 & a_1 & \dots & a_2 \\
a_2 & a_1 &  &  & a_3 \\
\vdots & \vdots & \ddots &\\
a_{n-1} & a_{n-1} &  &  & a_0 \\
\end{pmatrix}
$$

Not we prove this characterization.
**Prop** A matrix $W$ is circulant iff it commutes with shift, $SW = WS$
**Proof** 
$(\implies)$ It's easy to check that for any circulant matric $C$ it holds that $SC = CS$.

$(\impliedby)$ First note that $S_{ik} = \delta(i-1 \mod n,k)$ where $\delta$ is the usual Kronecker symbol (we omit the$\mod n$ further), hence:
$$
(SW)_{ij} = \sum_k S_{ik}W_{kj} = \sum_k \delta(i-1,k)W_{kj} = W_{i-1,j}
$$
$$
(WS)_{ij} = \sum_k W_{ik}S_{kj} = \sum_k W_{ik}\delta(k-1,j) = W_{i,j+1}
$$
so that
$$
W_{i-1,j} = W_{i,j+1} \iff W_{ij} = W_{i+1,\,j+1} 
$$
this means that $W$ need to be constant along diagonals, i.e. it's a circulant matrix with the associated vector
$$
a_i := W_{0i} \qquad \square
$$

The get-away from this is that if you want to learni a shift-invariant lineare transformation, you only need to learn the vector $a$. In more dimensione this is a matrix, and you apply it by shifting: convolutional layers.

### Circular convolutions

What is the connection with convolution? If we apply any vector to a circulant matrix $y = C_a x$ we get
$$
y_i = \sum_k {C_a}_{ik}x_k = \sum_k a_{i-k}x_k = (a * x)_i
$$
this is the same as the (discrete) $1D$-convolution!

### Discrete DFT

All circulant matrix commute, this means that are simultaneously diagonalizable. Let's find the eigenvector of $S^{-1}$, the left shift operator.

The eigenvalues of $S^{-1}$ are the $n$-th roots of unity:
$$
\rho_m = e^{i\frac{2\pi m}{n}}, \qquad m \in \mathbb{Z}_n
$$
with eigenvectors
$$
v_m = (1, e^{i\frac{2\pi m}{n}}, e^{i\frac{4\pi m}{n}}, \dots)
$$
this basis diagonalize also all circulant matrices! Let's find now the eigenvalues for a generic circulant matrix $C_a$:

$$
C_a v_m = \lambda_m v_m
$$
solving the first row
$$
\sum_k a_k v_k = \lambda_m
$$
$$
\sum_k a_k \rho^k = \hat a_k
$$
which is the Discrete Fourier Transform.





$$

$$
