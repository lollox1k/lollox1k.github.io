# Power method

Is the _simplest eigenvalue algorithm_, it finds the eigenvalue of largest modulus.

Consider a diagonalizable matrix $A$, then the eigenvectors form a basis for $\mathbb{C}^n$. Therefore, for every vector $x^0$, it's expantion in the eigen-base:
$$
x^0 = \sum_{i=1}^n \alpha_i v_i
$$
If we apply iterativly $x$ to the matrix $A$, i.e. $x^k = A^k x^0$, in the eigenvector base this is just:
$$
x^k = \sum_{i=1}^n \alpha_i\lambda_i^k v_i
$$
putting in evidence the biggest eigenvalue $\lambda_n$
$$
x^k = \lambda_n^k \left(  \alpha_n v_n + \sum_{i=1}^{n-1} \alpha_i \left[\frac{\lambda_i}{\lambda_j}\right]^kv_i\right)
$$
in the limit $k\to\infty$, the terms $\left[\frac{\lambda_i}{\lambda_j}\right]^k \to 0$ since $\lambda_i < \lambda_n$.

The error therm goes to zero lineart as $o(\frac{|\lambda_{n-1}|}{|\lambda_n|})$. So the convergence is better if the greates eigenvalue if well separated from the rest of the spectrum.

To avoid overflow or underflow ($\lambda_n^k \to \infty$ or to $0$) each iteration we normalize the vector.

**Remaks** the starting vector should have a nonzero component in $v_n$, i.e. it should not be perperdicular to $v_n$. This is however unlikely, and rounding error will introduce nonzero component helping us!

If the is more than one max eigenvalue, the algorithm will converge to an eigenspace.

## Shifts

Consider the _shifted matrix_ $A-\sigma I$, for $\sigma \in \mathbb{R}$. The spectrum of the shifted matrix is just the spectrum of $A$ shift $-\sigma$, the eigenvectors are the same:
$$
(A-\sigma I)v = (\lambda -\sigma) v 
$$
With shifts we can compute other eigenvalues insted of the greates absolute value one!

It can also be used to speed up convergence by decreasing the factor $\frac{|\lambda_n|}{|\lambda_{n-1}|}$.
