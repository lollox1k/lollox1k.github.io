Recall that a function $f : X \to \mathbb{R}$ is $\mathcal{S}$-measurable if the preimage of every Borel set $B$ is in the $\sigma$-algebra $\mathcal{F}$:
$$
\forall B \in \mathcal{B} \quad f^{-1}(B) \in \mathcal{S}
$$

We review the usual pointwise and uniform convergence.

**Def** Suppose $X$ is a set, $\{f_n\}_{n \geq 1}$ is a sequence of functions from $X$ to $\mathbb{R}$, and $f$ is a function from $X$ to $\mathbb{R}$.
- The sequence $\{f_n\}_{n\geq 1}$ **converges pointwise** on $X$ to $f$ if
$$
\lim_{n\to\infty} f_n(x) = f(x) \quad 
$$
for each $x \in X$. That is, $\forall x \in X$ and $\forall \epsilon > 0$ there exists $N_x$ such that
$$
|f_n(x)-f(x)|< \epsilon \quad \forall n \geq N_x
$$
- The sequence $\{f_n\}_{n\geq 1}$ **converges uniformly** on $X$ to $f$ if for every $\epsilon > 0$ there exists an $N$ such that
$$
|f_n(x)-f(x)|< \epsilon \quad \forall n \geq N, \quad \forall x \in X
$$

Like the difference between continuity and uniform continuity, the difference lies in the order of the quantifiers. Clearly uniform convergence implies pointwise convergence, a basic counterexample is the sequence 
$$
f_n(x) = \mathbb{1}_{[-\frac 1n,+\frac 1n]}(x)
$$
which converges pointwise the the function $f(0)=1$ and $f(x) = 0$ if $x\neq 0$, but not uniformly.

Also if $f_n \to f$ and $f_n \in C$ doesn not imply $f \in C$, a counterexample is just a smooth version of the previous characteristic function. On the other hand, if $f_n \rightrightarrows f$ then also $f \in C$.

**Proposition** If a sequence $\{f_n\}_{n\geq 1}$of continuous function converges uniformly to a function $f$, then $f \in C(X)$.
**Dim** Let $x \in X$, for all $\epsilon > 0$
$$
|f(x)-f(y)| \leq |f_n(x)-f(x)| + |f_n(x)-f_n(y)| + |f_n(y)-f(y)|
$$
since we have uniform convergence there exists $N$ such that $\forall n \geq N$ the first and last term on the right are less than $\frac \epsilon 3$. Since $f_n$ is continuous, there exists a $\delta > 0$ such that if $|x-y| < \delta$ the second term is less than $\frac \epsilon 3$. $\square$.


In a finite measure space, pointwise convergence is _almost_ uniform convergence, in the sense that it converges uniformly except on a set of arbitrary small measure.

**Theorem** (Egorov) Let $(X,\mathcal{S},\mu)$ be a finite measure space. Suppose $\{f_n\}_{n\geq 1}$ is a sequence of $\mathcal{S}$-measurable functions from $X$ to $\mathbb{R}$ such that $f_n\to f$. Then for every $\epsilon > 0$ there exists a set $E \subseteq X$ such that $\mu(X\setminus E) < \epsilon$ and $f_n \rightrightarrows f$ on $E$.
**Proof** The definition of pointwise convergence can rewritten as: for every $k \geq 1$
$$
\bigcup_{N = 1}^\infty \bigcap_{n=N}^\infty \left\{x \in X\,:\,|f_n(x)-f(x)| < \frac 1k\right\} = X
$$
$$
\bigcup_{N=1}^\infty A_{N,k} = X
$$
where we have defined the sets $A_{N,k}$, which are in $\mathcal{S}$ since $f_n-f$ is still $\mathcal{S}$-measurable.

Since this is an increasing sequence of sets, the [[Continuity of mesure]] implies
$$
\lim_{N\to\infty} \mu(A_{N,k}) = \mu(X)
$$
thus there exists $N_k$ such that
$$
\mu(X)-\mu(A_{N,k}) < \frac{\epsilon}{2^k} \quad \forall N \geq N_k
$$
Sia 
$$
E = \bigcap_{k=1}^\infty A_{N_k,k}
$$
then 
$$
\mu(X\setminus E) = \mu\left(X\setminus \bigcap_{k=1}^\infty A_{N_k,k}\right) = \mu\left( \bigcup_{k=1}^\infty X\setminus A_{N_k,k}\right)
$$
$$
\leq \sum_{k=1}^\infty \mu(X\setminus A_{N_k,k}) < \epsilon
$$
We must verify uniform convergence in $E$, for every $\epsilon > 0$ we can finde $k\geq 1$ such that $\frac 1k \leq \epsilon$, by definition $E \subseteq A_{N_k,k}$ so 
$$
|f_n(x)-f(x)| < \frac 1k \leq \epsilon \quad \forall n \geq N_k
$$
for all $x \in E$, hence $f_n \rightrightarrows f$. $\square$



Every measurable function can be approximated from below by simple functions, in the sense that we can find an increasing sequence of simple function such that $\phi_n \to f$, moreover if $f$ is bounded $\phi_n \rightrightarrows f$.

**Proposition** Let $(X,\mathcal{S})$ be a measurable space and $f : X \to [-\infty,+\infty]$ be $\mathcal{S}$-measurable. Then there exists a sequence ${\phi_n}_{n\geq 1}$ of simple functions such that
- $|\phi_n(x)| \leq |\phi_{n+1}(x)| \leq f(x)|$ for all $n$ and all $x \in X$.
- $\phi_n \to f$ (pointwise)
- if $f$ is bounded, $\phi_n \rightrightarrows f$.
**Proof** We construct the usual stair functions:
$$
\phi_n(x) = \begin{cases}
\quad n \quad\text{ if }\quad f(x) > k \\
\,-n \quad\text{ if }\quad f(x) < -k \\
\frac{\lfloor 2^n f(x)\rfloor}{2^n} \quad\text{ otherwise }
\end{cases}
$$
it's a simple function, and the definition implies that where $f(x) \in [-n,n]$
$$
|\phi_n(x)-f(x)| \leq \frac 1{2^n}
$$
which shows the second and third claim. $\square$


The next result is surprising, a Borel function is almost continuous, in the sense that there exists a large closed set on where continuous.

**Theorem** (Luzin) Suppose $f : \mathbb{R} \to \mathbb{R}$ is a Borel measurable function. Then for every $\epsilon > 0$ there exists a closed set $F \subseteq \mathbb{R}$ such that $\lambda(\mathbb{R}\setminus F) < \epsilon$ and $g|_F$ is continuous on $F$.
**Proof** The claim is clear if $g$ is a simple functions: any Borel set can be approximated from the inside with a closed set, and from the outside with an open set. If we restrict the function on the disjoint close sets, $g$ is continuous. Now by the previous proposition we can find a sequence of simple function that convergences pointwise to $g$, restrict the domain such that they are continuous, then use Egorov's theorem and the fact that uniform convergence preserves continuity.
