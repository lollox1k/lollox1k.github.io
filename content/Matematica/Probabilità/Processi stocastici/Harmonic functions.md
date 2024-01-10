# Harmonic functions

### Markov Chain on a graph
Consider a finite or countable graph $G = (V,E)$ with weighted edges $c(ij) \geq 0$. We can define a [[catene di Markov|Markov chain]] with state space $I = V$ and transition matrix normalizing all the wights for a given vertex
$$
P_{ij} := \frac{c(ij)}{\sum_{i\sim k} c(ik)}
$$
If the graph is connected, the chain will be _irreducible_.

**Def** (_Harmonic function_)
A function $F : V \to \mathbb{R}$ is _Harmonic_ at $x \in V$ if
$$
F(x) = \sum_{x \sim y} p(x,y)F(y)
$$
If $F$ is harmonic at each point of a set $W$, then we say that $f$ is harmonic on $W$.

>In words, $F(x)$ is the wighted average of the values of $F$ at the neighbors of $x$. In general, this is still true, but the average is taken with weights. 

### Maximum principle

**Theorem** (_Maximum principle_) Let $W$ be a set of states of a Markov chain on a finite or countable state space $𝖵$. If $F : V \to\mathbb{R}$ is a function that is harmonic on $W$ and the supremum of $F$ on $𝖵$ is achieved at some element $x_0 \in W$, then $F$ is constant on all states accessible from $x_0$ in the chain absorbed off of $W$.

**Proof** Since $F$ is harmonic on $W$ and $x_0 \in W$
$$
F(x_0) = \sum_{x_0 \sim y} F(y)p(x_0,y)
$$
since $\sum_{x_0 \sim y}p(x_0,y)=1$ 
$$
F(x_0)\sum_{x_0\sim y} p(x_0,y) = \sum_{x_0 \sim y} F(y)p(x_0,y)
$$
$$
\sum_{x_0\sim y} p(x_0,y)(F(y)-F(x_0))=0
$$
this implies $F(y)=F(x_0)$, that is the function $F$ is constant on neighbours of $x_0$ (distance $n = 1$). Using induction on the distance from $x_0$, we can prove the same for all reachabl states. $\square$

**Theorem** (_Uniqueness principle_) Let $W$ be a finite proper subset of states of a Markov chain on a finite or countable state space $𝖵$. Suppose that $𝖵 \setminus W$ is accessible from every state in $W$ for the chain absorbed off of $W$. If $f , g: 𝖵 \to \mathbb{R}$ are two functions that are both harmonic on $W$ and agree off $W$ (that is, $f(x) = g(x)$ for all $x \notin W$), then $f = g$.

**Proof** We use the maximum principle on the function $h := f-g$, which is still harmonic on $W$ (linear combinantions of harmonic functions is still harmonic, it follows from the linearity of the definition).

Since $f$ and $g$ agree outside $W$, $h(x) = 0$ for all $x \notin W$. We claim $h \leq 0$. Since $W$ is finite, the function assumes finite values, hence the supremum is atteined at some $x_0 \in V$. If the supremum of $h$ is outside $W$, then $\sup(h) = 0$, so our claim is true. 
If the supremum is atteined in $W$ from some $x_0$, then by the maximum principle (since $V \setminus W$ is accessible from every state in $W$) again $\sup(h) = 0$, so $h \leq 0$. 

Repeat with the function $\tilde h := g-f = -h$, we can show that $\tilde h \leq 0$, this implies $h = 0$ on all $V$. $\square$

Given a function defined on a subset of states, the _Dirichlet problem_ asks whether the given function can be extended to all states of the Markov chain so as to be harmonic wherever it was not originally defined. The answer is often yes:

**Theorem** (_Existence Principle_) Let $W$ be a proper subset of states of a Markov chain on a finite or countable state space $𝖵$. If $f_0 : 𝖵 \setminus W \to \mathbb{R}$ is bounded, then $\exists f : 𝖵 \to \mathbb{R}$  such that $f \vert(𝖵 \setminus W) = f_0$ and $f$ is harmonic on $W$.

**Proof** For any starting point $x$ of the Markov chain, let $X$ be the first vertex in $𝖵 \setminus W$ visited by the Markov chain if $𝖵 \setminus W$ is indeed visited. Let $Y := f_0(X)$ when $𝖵 \setminus W$ is visited and $Y := 0$ otherwise. Define the function
$$
f (x) := E_x[Y]
$$
this function is well defined, since $f(x) < \infty$ thaks to the boundness assumption for $f_0$, and it is harmonic, in fact using first step analysis:
$$
f(x) = \sum_{y \in V \setminus W} f_0(y)P_x(X=y)
$$
$$
= \sum_{z}\sum_{y \in V \setminus W} f_0(y)P_x(X=y| \text{ first step to z})P_x(\text{ first step to z})
$$
$$
= \sum_{z}\sum_{y \in V \setminus W} f_0(y)P_z(X=y)p(x,z)
$$
$$
= \sum_z f(z) p(x,z)
$$
And clearly $f(x)=f_0(x)$ when $x \in V\setminus W$, therefore we have found the harmonic extention we were looking for. $\square$
