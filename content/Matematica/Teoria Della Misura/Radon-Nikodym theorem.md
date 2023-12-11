

Let $(X, \mathcal{A})$ be a measurable space, $\lambda$ and $\mu$ two measure on this space.

**Def**  A measure $\mu$ algebra is called _absolutely continuous_ w.r.t. another measure $\lambda$ if
$$
\lambda(A)=0 \implies \mu(A)=0, \quad \forall A \in \mathcal{B}(\mathbb{R})
$$

this is written as $\mu << \lambda$.

**Def**  A measure $\mu$  is called _singular_ if there is a $N \in \mathcal{A}$ with 
$$
\lambda(N)=0 \quad \text{ and }\quad \mu(N^c)=0
$$
this is written as $\mu \perp \lambda$.

Usually one works with measures on the reals, so that the measurable space is $(\mathbb{R}, \mathcal{B}(\mathbb{R}))$ and $\lambda$ is the Lebesgue measure.

Some examples: 
- The zero measure is absolutely continuous w.r.t any measure.
- Every measure is absolutely continuous w.r.t itself.
- The Dirac measure $\delta_0$ is singular w.r.t. the Lebesgue measure, since:
$$
\delta_0(\{0\}^c) = 0 \quad\text{ and } \mathcal{L}(\{0\}) = 0
$$



**Theorem** (Radon-Nikodym and Lebesgue decomposition) Let $\mu : \mathcal{B} \to [0, \infty]$ any $\sigma$-finite measure on the borel sigma algebra of the reals. Then 
1. we can decompose it in two uniquely determined measures
$$
\mu = \mu_{ac} + \mu_{s}, \qquad \mu_{ac} << \mathcal{L}, \, \mu_s \perp \mathcal{L}
$$
2. There is a measurable map $g: \mathbb{R} \to [0,\infty)$ such that
$$
\mu_{ac}(A) = \int_A g d\mathcal{L}, \qquad \forall A \in \mathcal{B}(\mathbb{R})
$$
$g$ is called the _Radon-Nikodym derivative_.

**Proof** (Von-Neumann) First we prove a result for finite measure spaces, and then extend it to $\sigma$-finite spaces.

Let $(X, \mathcal{A})$ be a measurable space, and $\mu,\nu : \mathcal{A} \to [0,R]$ two finite measure such that $\nu << \mu$. Then $\sigma := \mu + \nu$ is also a finite measure on $X$ and $\sigma(A) = 0$ iff $\mu(A)=0$.

Consider the linear functional $T : L^2(X,\mathcal{A}, \sigma) \to \mathbb{R}$ defined by:
$$
T[u] := \int_X u d\mu
$$
$T$ is well defined because $\mu$ is finite and dominated by $\sigma$, so that
$$
L^2(\sigma) \subseteq L^2(\mu) \subseteq L^1(\mu)
$$
it's also bounded since 
$$
|T[u]| \leq  \Vert \mu \Vert_1 \leq \Vert \mu\Vert_2 \sqrt{\mu(X)}
$$
where we have used the [[Holder inequality]]. 
Then by [[Riesz representation theorem]] there exists a $g \in L^2(X,\mathcal{A}, \sigma)$ such that
$$
T[u] = \int_X ud\mu = \int_u ug\,d\sigma, \forall u \in L^2(\sigma)
$$
Then $\mu(A) = \int_A g\,d\sigma$ for any $A \in \mathcal{A}$, so that $0 < g \leq 1$ $\mu$ and $\sigma$ a.e. Consider the measurable set $Z := g^{-1}(0)$, if this has positive $\mu$ measure we get a contradiction. The same for the set $P := g^{-1}([1,\infty))$.

The second equality works also with any non-negative measurable functions (using the standard machinery, simple functions and then the [[Monotone Convergence Theorem]]]).

Since $\frac{1}{g}$ is non-negative and measurable, then 
$$
\int_A \frac{1}{g} \,d\mu = \int_A d\sigma = \sigma(A), \quad \forall A \in \mathcal{A}
$$

Since $\sigma$ is finite, $\frac{1}{g} \in L^1(\mu)$ and so is $f := \frac{1}{g}-1$. Then for evert $A \in \mathcal{A}$:
$$
\nu(A) = \sigma(A)-\mu(A) = \int_A \frac{1}{g} \,d\mu - \int_A d\mu = \int_A f d\mu
$$
It's easy to extend this result to $\sigma$-finite measures:
$$
\nu(A) = \nu(\bigcup_{n \geq 1} A_n) = \sum_{n\geq 1} \nu(A_n) = \sum_{n \geq 1} \int_{A_n} f_n d\mu = \int_A f\,d\mu
$$
where $f := \sum_{n \geq 1} f_n \mathbb{1}(A_n)$ (the limits can be exchanged by MON). $\square$
