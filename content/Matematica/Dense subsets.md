**Proposition** A subset $Y \subseteq X$ is dense iff for every non-empty open set $O \subseteq$ we have that $Y \bigcap O \neq \emptyset$.

**Proof** $(\implies)$ Since $Y$ is dense, this menas that the closure of $Y$ is the entire set $X$:
$$
\overline Y = X
$$
pick any non-empty open set $O$, then this is an open neighborhood of one of its elements. By definition of the closure, $O \bigcap Y \neq 0$.
$(\impliedby)$ Suppose that $x \notin \overline Y$. Then there exists a neighborhood of $x$ such that $N(x) \bigcap Y = \emptyset$. $\square$

