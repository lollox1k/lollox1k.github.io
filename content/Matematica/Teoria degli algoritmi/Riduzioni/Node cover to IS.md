Node cover, Vertex cover
Input: $G=(V,E)$, $k$
Question: $\exists C \subseteq V$ t.c. 
- $|c| \leq k$
- $\forall uv \in E$, $u\in C$ oppure $v\in C$
Vogliamo un insieme di vertici che tocca ogni arco e di dimensione minore di $k$.

La [[Riduzione polinomiale]]  si ottiene  dall' IS con lo stesso grafo, ma con $k' = N-k$ dove $N$ è il numero di vertici.