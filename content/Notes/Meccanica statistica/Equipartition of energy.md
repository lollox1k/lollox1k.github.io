

Let $x_i = q_i, p_i$, the following
$$
\left\langle x_i \frac{\partial H}{\partial x_k}\right\rangle = \delta_{ij} k_B T
$$

**Proof** (For the [[Ensemble canonico|canonical ensemble]]) 
$$
\left\langle x_i \frac{\partial H}{\partial x_k}\right\rangle =  \frac 1 Z\int  x_i \frac{\partial H} {\partial x_k}e^{-\beta H}\,d\Gamma
$$
using that 
$$
\frac {\partial}{\partial x_i}\left(x_i H\right) = \delta_{ij}H + x_i \frac{\partial H}{\partial x_k}
$$
$$
= \frac 1 Z\int \frac {\partial}{\partial x_i}\left(x_i H\right) e^{-\beta H}d\Gamma - \delta_{ij} \frac 1 Z \int H e^{-\beta H}d\Gamma
$$
the first term is zero, the second is just the average energy $U$
$$
= \delta_{ij} U
$$
but in the canonical ensemble this is the same as 
$$
= \delta_{ij} \frac{1}{\beta} = \delta_{ij} k_B T
$$

A famouse use of this theorem is that any quadratic term in the hamiltonian
$$
H = \sum_i \alpha_i x_i^2
$$result in a $\frac{1}{2} k_B T$ term in the total average energy, since
$$
\sum_i\left\langle x_i \frac{\partial H}{\partial x_i}\right\rangle
= \sum_i\langle x_i 2\alpha x_i \rangle = 2 \langle H \rangle
$$
so that 
$$
\langle H \rangle = \sum_i \frac 12 k_B T
$$


