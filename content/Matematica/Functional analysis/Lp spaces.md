Let $\mu$ be a positive measure on the set $E$, and $u : E \to \mathbb{C}$ a measurable function, then we can define
$$
\Vert u \Vert_{L^p} := \left( \int_E |u|^p d\mu\right)^\frac 1p, \quad p \in (0, +\infty),
$$
$$
\Vert u \Vert_{L^\infty} := \inf \{C \,:\, |u| \leq C\quad a.e.\}
$$


For $p \in [1,+\infty]$ these functions are a _norm_. The only non-trivial condition to check is the triangle inequality: [[Minkowsky's inequality]].

Also $\Vert u \Vert  = 0$ if $u = 0$ a.e., so it's a semi-norm. Just work with the equivalence classes, where $u \sim v$ iff $u=v$ a.e.

In the case of finite measure space, there is a nice inclusion property:
**Proposition** Suppose $(X,\mathcal{A}, \mu)$ is a finite measure space $(\mu(X) < \infty)$ and $0 < p < q < \infty$. Then
$$
\Vert u \Vert_p \leq \mu(X)^{\frac{q-p}{pq}} \,\Vert u \Vert_q
$$
in particular $L^q \subseteq L^p$.

**Oss** In a sense $L^\infty$ is the limit of $L^p$ when $p \to \infty$, for a finite measure space, since:
$$
\Vert f \Vert_p \leq \mu(X)^{\frac 1 p} \Vert f\Vert_\infty \rightarrow \Vert f \Vert_\infty \quad \text{ when }p\to\infty
$$
on the other hand, for any $\epsilon > 0$ the set
$$
\mu(x \,\text{ s.t. } \,\Vert f\Vert_\infty-f(x) < \epsilon) =\delta > 0
$$
has positive measure. This implies
$$
\int |f|^pd\mu \geq \delta(\Vert f\Vert_\infty -\epsilon)^p
$$
taking the $\liminf$ on gets that $\lim_p \Vert f\Vert_p = \Vert f\Vert_\infty$.

**Proof** Let $u \in L^q$, Apply [[Holder inequality]] to $u^p$ and $1$. Since we want on the right the $q$ norm, use as  indices $\frac{q}{p}$ and its conjugated:
$$
\Vert u^p \cdot 1 \Vert_1 \leq \Vert u \Vert_q^p \cdot \Vert 1 \Vert_{\frac{q}{q-p}}
$$
$$
\Vert u \Vert_p^p \leq \Vert u \Vert_q^p \,\mu(X)^{\frac{q-p}q} \quad \square
$$

**Remark** the result is true only for finite measure spaces. A cool counterexample, in which also the opposite inclusion $L^p \subseteq L^q$ when $p \leq q$ is also true is $\mathbb{Z}$ equipped with the counting measure. Indeed
$$
\Vert f \Vert_q = \sum_{n \in \mathbb{Z}}|f(n)|^p
$$


**Proposition** Let $p \in [1, +\infty]$. The space $L^p(\mu)$ is complete: suppose that $\{f_n\}$ is a sequence such that $\forall \epsilon > 0$, there exists $N \geq 0$ such that
$$
\Vert f_j - f_k \Vert_p < \epsilon, \quad \forall i,k \geq N
$$
(The sequence is Cauchy). Then there exists an element $f \in L^p$ such that
$$
\lim_{n\to\infty} \Vert f- f_n\Vert_p =0
$$

**Proof** Suppose now that $p \in [1,+\infty)$. First we build a limit candidate, then we show that this limit belongs to $L^p$. Since the sequence is Cauchy, we can fine a subsequence $\{f_{n_k}\}$ such that
$$
\Vert f_{n_{k+1}-f_{n_k}} \Vert_p < \frac{1}{2^k}
$$
to simplify the notation we identify the subsequence as the original sequence.

Clearly one can write with a telescopic series
$$
f_n = f_1 + \sum_{k=1}^{n-1} (f_{k+1}-f_k)
$$

we now define the candidate limit function $f$ as a series
$$
f := f_1 + \sum_{k\geq 1} (f_{k+1}-f_k)
$$
and similalry
$$
g := \lim_{n\to\infty} g_n =|f_1| + \sum_{k\geq 1} |f_{k+1}-f_k|
$$
Note that $g_n \uparrow g$. 
Applying the [[Minkowsky's inequality]] and taking the limit we get
$$
\lim_n\Vert g_n\Vert_p\leq \Vert f_1\Vert_p + \sum_{k\geq 0} \Vert f_{k+1}-f_k \Vert_p < \infty
$$
using [[Monotone Convergence Theorem]]
$$
\Vert g \Vert_p = \lim_n \Vert g_n \Vert_p < \infty
$$
so that $g \in L^p$.  This implies that $g$ is finite a.e., so that $f_n$ is absolutely convergent a.e., meaning that it's also convergent a.e. and the definition of $f$ makes sense. Also $f_n \leq g_n$ and we can conclude that also $f \in L^p$. 

By construction 
$$
f_{n_k} \to f \qquad a.e.
$$
we need to prove that this converges in $L^p$ also
$$
|f(x) - f_n(x)|^p \leq [2\max(|f(x)|, |f_n(x)|)]^p
$$
$$
\leq 2^p |f(x)|^p + 2^p|f_n(x)|^p
$$
$$
\leq 2^p|g(x)|^p + 2^p|g_n(x)|^p \leq 2^{p+1}|g(x)|^p
$$
taking the limit and using [[Dominated convergence theorem]] we get
$$
\lim_{n\to\infty} \Vert f-f_n\Vert_p^p = \int \lim_n |f-f_n|^p d\mu = 0
$$


The last step is to show that also the original sequence converges to $f$.
$$
\Vert f-f_n\Vert_p \leq \Vert f-f_{n_k}\Vert_p + \Vert f_{n_k}-f_n\Vert_p
$$
since $f_{n_k} \to f$ there exists an $N \geq 0$ such that $\forall k \geq N$ the first term on the left is less than $\frac\epsilon 2$. Since the original sequence was Cauchy there also exists an $M \geq 0$ such that the second term on the right is less than $\frac\epsilon 2$. We can conclude that
$$
\Vert f-f_n \Vert_p \to 0
$$

The completeness of $L^\infty$ is straight forward, since the sequence is Cauchy $\forall \epsilon  > 0$ there exists $N \geq 0$ such that $\forall m > n \geq N$ it holds almost everywhere that
$$
|f_m(x)-f_n(x)| < \epsilon \qquad a.e.
$$
For a fixed $\epsilon$ these sets of measure zero where the inequality does not holds can depend on $m$ and $n$, consider the (contable) union
$$
Z = \bigcup_{m>n\geq N} Z_{m,n}
$$
this set has also measure zero. Clearly for each $x \in X\setminus Z$ we have pointwise convergence (since $\mathbb{R}$ is complete), hence it makes sense to define $f$ as the pointwise limit of $f_n$ on this set. The convergence is also uniform on $X\setminus Z$, so that
$$
\Vert f-f_n \Vert_\infty \to 0 \qquad \square
$$


# Dense subsets
> [!proposition]
> Let $1 \leq p < +\infty$. Simple functions are _dense_ in $L^p(\Omega)$: for any $f \in L^p(\Omega)$ there exists a sequence $\{h_k\}$ of simple functions such that:
> $$
> \lim_{n\to\infty} \Vert f - h_k \Vert_p = 0
> $$
> > [!proof]-
> > Write $f = f_+ - f_-$, then we can assume w.l.o.g. that $f \geq 0$.
> >  By the definition of [[Lebesgue's integral]], we can find a sequence of simple functions such that
> >  $$
> >  \int h_n d\mu \xrightarrow{n\to\infty} \sup\left\{ \int g_k d\mu\,\mid\, 0 \leq g_k \leq |f|^p, \,g_k\text{ simple} \right\}
> >  $$
> > So the case $p=1$ is proven. To prove the general case observe that:
> >  $$
> >  |f-h_n|^p \leq |f|^p
> >  $$
> > Since $|f - h_n|^p \to 0$ pointwise, using [[Dominated convergence theorem]]:
> > $$
> > \Vert f-h_n \Vert_p^p = \int |f-h_n|^p d\mu \xrightarrow{n\to\infty} 0 \qquad \square
> > $$
> >


> [!proposition]
> Let $1 \leq p < +\infty$. [[Distributions|Test functions]] $C_c^\infty(\Omega)$ are _dense_ in $L^p(\Omega)$: for any $f \in L^p(\Omega)$ there exists a sequence $\{\psi_k\} \subset C_c^\infty(\Omega)$ such that:
> $$
> \lim_{n\to\infty} \Vert f - \psi_k \Vert_p = 0
> $$
> > [!proof]-
> >  By definition 



