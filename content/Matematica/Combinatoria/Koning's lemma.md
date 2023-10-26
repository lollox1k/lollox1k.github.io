> Big skinny trees are tall.

**Theorem** (Konig's Lemma) If $T$ is an infinite tree (this implies infinite vertices and infinite edges) and each level of $T$ is finite, then $T$ contains an infinite path.

**Proof** Let's choose a _root_ $r$, this defines layers of the tree $L_0,L_1,\dots$  
Consider the function $f : V(G)\setminus (L_0 \cup L_1)  \to L_1$ that maps all (infinite) vertices in layers $L_2,L_3,\dots$ to the (finite) vertices in $L_1$. So it follows from teh [[Infinite pigeonhole principle]] that there must exists at least one vertex $v_1 \in L_1$ such that the preimage $f^{-1}(v_1)$ is infinite. Choose this vertex as the secondo in the path. Now remove layer $L_0$ from the graph, set $v_1$ as the new root and repeat. $\square$ 