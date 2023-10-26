# Kolmogorov 0-1 law

**Def** Given a collection of random variables $(X_n)_{n\geq 1}$ we define the $\sigma$-algebras $\mathcal{T_n}$ by $\mathcal{T}_n := \sigma(X_n,X_{n+1},\dots)$. Then the _tail_ $\sigma$-algebra is defined by
$$
\mathcal{T} := \bigcap_{n\geq 1} \mathcal{T}_n.
$$
> Intuition: The events which are in the tail sigma algebra are those which are unaffected by finitely many variables.

Let's see some examples of such events.

**Examples** 
- $\{\sum_{n=1}^{\infty} X_n < \infty\} \in \mathcal{T}$  since this is equivalent to having a finite tail:
- $\{\lim_{n\to\infty} X_n \text{ exists }\}$


**Theorem** (Kolmogorov) Let $(X_n)_{n\geq 1}$ denote a collection of indipendent random variables. Then the tail $\sigma$-algebra is trivial, meaning $\mathbb{P}(A) \in \{0,1\}$ for all $A \in \mathcal{T}$.

**Proof** Let's show that $\mathcal{T}$ is _indipendent of itself_. We introduce the $\sigma$-algebras
$$
\mathcal{X}_n := \sigma(X_1,X_2,\dots,X_n)
$$
$$
\mathcal{T}_n := \sigma(X_{n+1},X_{n+2},\dots).
$$
Since the variables are indipendnet, $\mathcal{X}_n$ and $\mathcal{T}_n$ are indipendent. Since $\mathcal{T} \subseteq \mathcal{T_n}$, $\mathcal{T}$ is indipendent of $\mathcal{X_n}$ for all $n$. 
Now let $\mathcal{X}_{\infty} := \sigma((X_n)_{n \geq 1})$. It suffices to show that $\mathcal{T}$ is indipendent of $\mathcal{X}_\infty$, from the inclusion $\mathcal{T} \subseteq \mathcal{X}_\infty$ the thesis will follow.
To show this indipendence, observe that
$$
\mathcal{X}_\infty = \sigma \left(\bigcup_{n\geq 1} \mathcal{X}_n \right)
$$
and that $\bigcup_{n\geq 1} \mathcal{X}_n$ is a [[Pi-system]], and $\mathcal{T}$ is clearly indipendent since it is for all $\mathcal{X}_n$. $\square$

