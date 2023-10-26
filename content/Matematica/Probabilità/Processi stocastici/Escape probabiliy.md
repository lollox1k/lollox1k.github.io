### Escape probability
Consider a random walk on a [[Electrical networks|random network]]. Fis a state $a \in V$ and a subset $Z \subset V$ such that $a \notin Z$. An interesting question is what is the probability of _escape from a_, that is, starting from $a$, what is the probability of arriving in $Z$ before returning to $a$:
$$
P_a[\tau_Z < \tau_a^+]
$$
Computing this probability is not an obious task. Luckly, it turns out that the function:
$$
v(x) := P_x[\tau_a < \tau_Z]
$$
it's [[Harmonic functions|harmonic]], so that we can apply the theory developed for voltage functions in eletrical networks.
The boundary values are $v(a) = 1$ and $v(Z)=0$. Such function exists and is unique by the [[Harmonic functions#Maximum principle|maximum principle]] for harmonic functions.

Let's prove that it's harmonic using first step analysis:
$$
P_x[\tau_a < \tau_Z] = \sum_{y \sim x} P_x[\tau_a < \tau_Z|\text{first step to }y]P_x[\text{first step to }y]
$$
$$
= \sum_{y \sim x} P_y[\tau_a < \tau_Z]P(x,y) \quad \square
$$
To compute the escape probability from $a$ 
$$
P_a[\tau_Z < \tau_a^+] = \sum_x p(a,x)[1-v(x)] = \sum_x \frac{c(a,x)}{c(a)}[v(a)-v(x)]
$$
$$
= \frac{1}{c(a)}\sum_x i(a,x)
$$
where $c(a) := \sum_{x \sim a} c(a,x)$ (recall that $c(x)$ is a stationary measure, i.e. [[Reversibile Markov Chains|detailed balance]] holds with respect to $c$).

Notice how the escape probability depends on the _total current_ out of $a$, so that we may regard the entire circuit between $a$ and $Z$ as a single conductor with an _effective conductance_ 
$$
C_{eff} := c(a)P_a[\tau_Z < \tau_a^+] =: \mathcal{C}(a \leftrightarrow Z)
$$

Thus the only computation required to answer our original question is computing $\mathcal{C}(a \leftrightarrow Z)$. To do this we can use the same reduction rules used when solving circuits!

### Expected number of vists before escape

It follows from the strong [[Markov property]] that the number of visits before escape is a geometric random variable
$$
\sum_{n=0}^{\tau_Z-1} \mathbb{1}(X_n=a) \sim Geom(P_a[\tau_Z < \tau_a^+])
$$
and thus has an expected value of 
$$
\mathbb{E}\left[\sum_{n=0}^{\tau_Z-1} \mathbb{1}(X_n=a)\right] = P_a[\tau_Z < \tau_a^+]^{-1} = c(a)C_{eff}^{-1}=c(a)R_{eff}
$$

### Probabilistic interpretetion of current

A simple model for the flow of charge in a real circuit is to assume that positive charges enter the circuit at $a$, and then do random Brownian motion in the circuit till they reach $Z$. Then the current of an edge is the expected number of passages of a charge. This is indeed true in our mathematical model:

**Proposition** (Current as edge crossings) Let $G$ be a finite connected network. Start a random walk at $a$ and kill it at $Z$. For $x \sim y$, let $S_{xy}$ be the number of transitions from $x$ to $y$. Then
$$
\mathbb{E}[S_{xy}] = \mathcal{G}_Z(a,x)p(x,y), \quad \mathbb{E}[S_{xy}-S_{yx}] = i(x,y)
$$
where $i$ is the current in $G$ when the potential applied at $a$ $v(a)$ is such that the total current flow from $a$ is one.
**Proof** 
$$
\mathbb{E}\left[ \sum_{n=0}^\infty \mathbb{1}(X_n=x, X_{n+1}=y)\right] =  \sum_{n=0}^\infty P(X_n=x, X_{n+1}=y)
$$
$$
= \sum_{n=0}^\infty P(X_n=x)p(x,y) = \mathbb{E}\left[ \mathbb{1}(X_n=x)\right]p(x,y) =  \mathcal{G}_Z(a,x)p(x,y)
$$
If the flow out of $a$ is one, then we can write the potential using the [[Green function of a random walk|Green function]] 
$$
v(x) = \frac{\mathcal{G}_Z(a,x)}{c(x)}
$$
so that we get
$$
\mathbb{E}[S_{xy}- S_{yx}] = \mathcal{G}_Z(a,x)p(x,y) - \mathcal{G}_Z(a,y)p(y,x)
$$
$$
= v(x)c(xy) - v(y)c(xy) = i(xy) \qquad \square
$$




