
Suppose we have a _transient_ random walk, or one that is "killed" when it reaches the subset of state $Z$ in a finite irredicible markov chain.
An interesting question is the quantity:

**Def** Let $G$ be a finite connected network. The _Green function_ of the random walk on $G$ killed ad $Z$ is defined as
$$
\mathcal{G}_Z(a,x) := \mathbb{E}_a\left[\sum_{n=0}^\infty \mathbb{1}(X_n=x)\right]
$$
the expected number of visits to state $x$ strictly before reaching $Z$.
Since we assume the network is finite and connected, this quantity is finite. Also if $z \in Z$ then $\mathcal{G}_Z(a,z) = 0$.

**Proposition** (Green function as voltage) Let $G$ be a finite connected network. When a voltage is imposed at $\{a\}\cup Z$ such that $v(Z)=0$ and at $a$ such that $||i|| = 1$ (unit flow), then
$$
v(x) = \frac{\mathcal{G}_Z(a,x)}{c(x)}
$$
is the voltage function of the network.

**Proof** It satisfies the boundary conditions since $v(z)=0$ and $v(a)$ equals the [[Escape probabiliy]] divided by $c(a)$.

Also, since $\mathcal{G}$ satisfies [[Reversibile Markov Chains|Detailed Balance]]:
$$
\frac{\mathcal{G}_Z(a,x)}{c(x)} = \frac{\mathcal{G}_Z(x,a)}{c(a)}
$$
we can show that it's [[Harmonic functions|harmonic]] by first step analysis:
$$
\mathcal{G}_Z(x,a) = \sum_{y \sim x} \mathcal{G}_Z(y,a)p_{xy}, \quad \square
$$
