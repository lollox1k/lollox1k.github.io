## Poincarré return theorem

**Theorem** Let $g$ be a continuous, bijective transformation that preserves volumes defined in Euclidean space to itself. Suppose that there exists a finite region $D$  such that $gD = D$. Then for every neighourhood $U$ of every point of $D$, there exists a point $x \in U$ that eventually returns in $U$, that is 
$$
g^n x \in U \qquad \text{ for some } n > 0
$$
**Proof** Consider the images of the neighborhood $U$:
$$
U, gU,\, \dots\,, g^nU
$$
since $g$ preserves volumes, they have the same (non-zero) volume. If they didn't intersetc, the volume of $D$ would be infinite, so there exists some $k, l \geq 0$, $k > l$ such that
$$
g^kU \bigcap g^lU \neq \emptyset
$$
since $g$ is bijective, we can define its inverse. Applying the inverse of $g^l$ we get
$$
g^{k-l}U \bigcap U \neq \emptyset
$$
since this set is non-empty, we have just showd that there exists an element $y \in g^{k-l}U \bigcap U$ that is inside the starting neighborhood $U$ and also in $g^{k-l}U$. One could pick $y = g^{k-l}x$. $\square$

