# Handshake Lemma
The sum of all degrees of vertices in a graph is two times the number of edges:
$$
\sum_{v\in V} d(v) = 2 \vert E \vert
$$
**Dim 1** (_double counting_) Ogni arco ha due vertici, ergo compare esattamente due volta nella somma a sinistra. $\square$

**Dim 2** (_adiacency matrix_) Sia $A(G) \in \{0,1\}^{n\times n}$ la matrice di adiacenza del grafo $G$, ovvero $a_{i,j} = a_{j,i} = 1$ se i nodi $i,j$ sono collegati, ovvero $ij \in E$. Dunque ad ogni arco corrispondono due $1$ sulla matrice. Inoltre sommando i valori della matrice lungo la colonna (riga) $i$-esima si ottiene il grado del vertice $i$:
$$
\sum_{j \in V} a_{i,j} = d(i)
$$
sommando tutte le colonne quindi ottengo la somma dei gradi dei nodi. $\square$

