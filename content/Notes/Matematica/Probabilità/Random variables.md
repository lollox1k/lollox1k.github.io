# Random variables

**Def** A _real random variable_ is a [[Funzioni misurabili|measurable function]] $X : (\Omega,\mathcal{F}) \mapsto (\mathbb{R},\mathcal{B})$.

Where $\mathcal{B}$ is the usual Borel $\sigma$-algebra. 

### Examples

Given a measurable set $A \in \mathcal{F}$, its characteristic function is a random variable:
$$
\mathbb{1}_A(\omega) := \begin{cases}
1 \text{ if } \omega \in A \\
0 \text{ if } \omega \notin A
\end{cases}
$$
Infact, if we study the preimages, every Borel set $B \in \mathcal{B}$:
$$
\mathbb{1}_A(B)^{-1} = \begin{cases}
\emptyset \quad\text{ if } \quad 1,0 \notin B\\
\Omega \quad\text{ if } \quad 1,0 \in B\\
A \quad\text{ if } \quad 1 \in B, \,0 \notin B\\
A^C \quad\text{ if } \quad 1 \notin B, \,0 \in B\\
\end{cases}
$$
which are all measurable.

## The law of a random variable
To each random variable $X$ on a given probability space we can associate a probability mesure $\mathcal{L}_X$, that we refer to as the _law_, or the _distribution_ of $X$.

**Def** The law of a random variable $X$ on a probability space $(\Omega, \mathcal{F}, \mathbb{P})$ is the probability mesure $\mathcal{L}_X : \mathcal{B} \mapsto [0,1]$ on $(\mathbb{R},\mathcal{B})$ defined by:
$$
\mathcal{L}_X(A) := \mathbb{P}(X^{-1}(A)) = \mathbb{P}(X\in A)
$$
where the event in the last term is a standard notation for $\{\omega \in \Omega \,:\, X(\omega) \in A\}$.

Since the sets $(-\infty,a]$ with $a \in \mathbb{R}$ form a [[Pi-system]] that generates $\mathcal{B}$, it follow from the [[Teorema unicità dell'enstenzione|uniqueness lemma]] the law is uniquely specified by its value on such sets:
$$
\mathcal{L}_X((-\infty,x]) := \mathbb{P}(X^{-1}((-\infty,x])) = \mathbb{P}(X \leq x)
$$
We can define a function $F_X : \mathbb{R} \mapsto [0,1]$ called _distribution function_ of $X$ defined by $F_X(x) := \mathbb{P}(X\leq x)$.

