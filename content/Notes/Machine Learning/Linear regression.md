
We want to model a function $f : \mathbb{R}^n \to \mathbb{R}$, our hypotesis is that this function is linear, that is
$$
\hat y = w^T x, \qquad w \in \mathbb{R}^n
$$
where $w$ is a vector of parameters.

Task: predict $y$ from $x$ using $w^T x$.
Performance metric: MSE

We hypotewsis that reducing $MSE_{train}$ will also reduce $MSE_{test}$.

We pack our $m$ examples $x$ in a matrix $X \in \mathbb{R}^{m\times n}$ by stacking them in rows. We assume that $rank(X)=n$ (max rank) (i.e. no usless features).

With this matrix we can write the $MSE_{train}$ like
$$
\frac{1}{m} \Vert y- \hat y\Vert^2 = \frac{1}{m} \Vert y - Xw \Vert^2
$$

We can use [[Problema dei minimi quadrati|normal equation]] to minimze the residue!

$$
w = (X^TX)^{-1}X^Ty = X^+y
$$


