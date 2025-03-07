Let $X,Y$ be normed spaces, $X$ a [[Banach spaces|Banach space]].
We denote the set of all linear bounded operators from $X$ to $Y$ as:
$$
B(X,Y) := \{T : X \to Y \mid T \text{ linear and bounded}\}
$$
We equip $B(X,Y)$ with the usual operator norm $\Vert\cdot\Vert_{X\to Y}$.

> [!definition]
> Let $X,Y$ be normed spaces, $T : X \to Y$.
> A subset $M \subseteq B(X,Y)$ is **bounded pointwise** on $X$ if:
> $$
> \forall x \in X \quad \exists C_x \geq 0 \quad \text{ s.t. } \Vert T_n x \Vert_Y \leq C_x \quad \forall n
> $$
> $M$ is **uniformly bounded** if:
> $$
> \exists C > 0 \text{ s.t. } \Vert T_n \Vert_{X\to Y} \leq C \quad \forall n
> $$

As usual the difference is the order of the quantifiers.

> [!theorem]
> For every subset $M \subseteq B(X,Y)$, $M$ is bounded pointwise on $X$ iff $M$ is uniformly bounded.
> 

A cool application:
> [!proposition]
> Let $X,Y$ be normed spaces, $X$ a Banach space.
> Let $T_n \in B(X,Y)$ with $\lim_{n\to\infty} T_nx$ exists for all $x \in X$.
> Then $T:X\to Y$ defined by $Tx := \lim_{n\to\infty} T_n x$ is **linear and bounded**
> > [!proof]-
> > $M := \{T_n\}$ is bounded pointwise on $X$. Using Banach-steinhaus we know that there is a $C > 0$ such that $\Vert T_n \Vert \leq C$ for all $n$. 
> > Let's compute the operator norm of $T$:
> > $$
> > \Vert T \Vert = \sup\{ \Vert Tx \Vert_Y \mid \Vert x \Vert_X = 1\}
> > $$
> > using the definition of $T$
> > $$
> > \Vert Tx \Vert_Y = \Vert \lim_{n\to\infty}T_n x \Vert_Y = \lim_{n\to\infty}\Vert T_n x \Vert_Y \leq C
> > $$
> > we can take out the limit since the norm is a continuous function. Hence $T$ is bounded (linearity is obvious.) $\square$

