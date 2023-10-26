**Def** The _Wiener measure_ on $C([0,1])$ is the probability measure $\mu$ on the measurable space $(C[0,1], \mathcal{B}(C[0,1]))$ with the following properties:
1. $x(t) \sim N(0,t)$ for all $t \in [0,1]$, that is
$$
\mathbb{P}(x(t) \in I) = \int_I \frac{1}{\sqrt{2\pi t}} e^{-u^2/2t} du
$$
2. indipendence of the increments: given $0 \leq t_1 < t_2 \dots t_n \leq 1$, the random variables
$$
x(t_2)-x(t_1), \dots, x(t_n)-x(t_{n-1})
$$
are indipendent.

**Remark** By $x(0) \sim N(0,0)$ we mean $x(0)=0$ almost surely.

## Existence

We will follow this strategy: construct an explicit sequence of probability measures $(\mu_n)_{n \geq 1}$ on $C[0,1]$, which will be shown to converge to the Wiener measure.

Let $(\xi_k)_{k \geq 1}$ be a sequence of i.i.d real-valued random variables with
$$
\mathbb{E}[\xi_1] = 0 \qquad \mathbb{E}[\xi_1^2] = \sigma^2 \in (0,\infty)
$$
the result doesn not matter on the exact law, you could use $\xi_1 \sim rad(1/2)$ or $\xi_1 \sim N(0,\sigma^2)$.

We use this sequence to define a random walk on $\mathbb{R}$:
$$
S_n = \sum_{k=1}^n \xi_k \qquad S_0 = 0
$$
we make this random walk into a continuos function by linear interpolation, for $t \in [0,1]$ define
$$
X_t^n := \frac{S_{\lfloor nt \rfloor}}{\sigma \sqrt{n}} + (nt-\lfloor nt \rfloor)\frac{\xi_{\lfloor nt \rfloor+1}}{\sigma \sqrt{n}}
$$
this is a sequence in $C[0,1]$, we donte by $(\mu_n)_{n\geq 1}$ their associated sequence of probability measures. 

### Convergence of the FDDS

We start by showing that the FDDs of $X^n$ converge to the ones of the Wiener measure. 
First let's prove that $X_t^n \implies N(0,t)$ for any given $t \in (0,1]$, the case $t=0$ is obvious.

Let's show that the interpolating part goes to zero in probability using [[Chebyschev inequality]]
$$
\mathbb{P}(|\psi(n,t)| > \epsilon) \leq \frac{\mathbb{E}[\psi(n,t)2]}{\epsilon^2} \leq \frac{\xi^2}{\sigma^2n\epsilon^2} = \frac{1}{n\epsilon^2} \to 0
$$
as $n \to \infty$.
Then 
$$
\frac{S_{\lfloor nt \rfloor}}{\sigma \sqrt{n}} \implies N(0,t)
$$
from the [[Central Limit Theorem]].

We now prove that the FDDs converge, for $k=2$ (the general case follows from induction).
We need to show that
$$
\left(\frac{S_{\lfloor ns \rfloor}}{\sigma \sqrt{n}}, \frac{S_{\lfloor nt \rfloor}}{\sigma \sqrt{n}}\right) \implies \left(B_s,B_t\right)
$$
since we already proved that $\psi(n,t) \to 0$ in probability.

**Remark** $X_n \implies X$ and $Y_n \implies Y$ doesn not imply $(X_n,Y_n) \implies (X,Y)$. A counter example is $X_n = N(0,1)$ and $Y_n = (-1)^n N(0,1)$. 
However this holds when $X_n$ and $Y_n$, $X$ and $Y$ are indipendent. We can exploit this result using increments
$$
\left(\frac{S_{\lfloor ns \rfloor}}{\sigma \sqrt{n}}, \frac{S_{\lfloor nt \rfloor}}{\sigma \sqrt{n}}-\frac{S_{\lfloor ns \rfloor}}{\sigma \sqrt{n}}\right) \implies \left(B_s,B_t-B_s\right)
$$
the functions $h(x,y-x) = (x,y)$ is continuos, hence by the continuos mapping theorem our goal follows.

Which follows from  the convergence in distribution of the marginals
$$
\frac{S_{\lfloor ns \rfloor}}{\sigma \sqrt{n}} \implies B_s
$$
$$
\frac{S_{\lfloor nt \rfloor}}{\sigma \sqrt{n}}-\frac{S_{\lfloor ns \rfloor}}{\sigma \sqrt{n}} \implies B_t-B_s
$$

### Relative compactness
