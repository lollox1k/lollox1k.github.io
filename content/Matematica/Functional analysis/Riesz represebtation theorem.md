**Theorem** Let $(X, \langle\cdot,\cdot\rangle)$ be a _complete_ Hilber space, and $L : X \to \mathbb{F}$ a continuos (or bounded) linear map. Then there exists a unique $x_L \in X$ such that
$$
L(x) = \langle x_L, x\rangle \qquad \forall x \in X
$$
moreover $\Vert L \Vert = \Vert x_L\Vert$.

**Proof** The main idea is to pick an element in the orthogonal complement of the Kernel. If $Ker(L) = X$, then the map is trivial (everthing is zero), in this case $x_L = 0$. 
Suppose now $Ker(L) \neq X$. Since $L$ is continuos, then $Ker(L)$ is a closed set (the preimage of $\{0\}$), then there exists an element $y \in Ker(L)^\perp$, since it's linear we can scale it such that  $\Vert y \Vert = 1$.

Consider a vector of the form
$$
z = L(x)y - L(y)x
$$
we observe that $z \in Ker(L)$, in fact
$$
L(z) = L(x)L(y) - L(y)L(x) = 0
$$
so that 
$$
0 = \langle y, z \rangle = \langle y, L(x)y - L(y)x \rangle
$$
$$
= L(x)\langle y, y\rangle - L(y)\langle y, x \rangle
$$
$$
= L(x) - L(y)\langle y,x \rangle
$$
if we set $x_L = L(y)y$ then
$$
L(x) = L(y)\langle y,x\rangle = \langle x_L, x \rangle
$$

To show uniqueness, suppose there exists another $x_L'$, taking the difference
$$
0 = \langle x_L, x \rangle - \langle x_L', x\rangle = \langle x_L-x_L', x \rangle, \quad \forall x \in X
$$
but the only element orthogonal to $X$ is the zero vector. 

Computing the operator norm
$$
\Vert L\Vert = \sup \{ |L(x)| : \Vert x \Vert = 1\}
$$
$$
= \sup \{ |\langle x_L, x\rangle| : \Vert x \Vert = 1\}
$$
but using [[Cauchy-Schwarz inequality]] 
$$
|\langle x_L, x\rangle| \leq \Vert x_L \Vert \Vert x \Vert = \Vert x_L \Vert
$$
this upper bound is thight, since
$$
| L(y)| = |\langle x_L, y \rangle|=\Vert x_L \Vert \quad \square 
$$



