# Graph Isomorphism

Dua grafi $G = (V(G), E(G))$ e $H = (V(H), E(H))$ sono *isomorfi* se esiste una biiezione tra i vertici $f : V(G) \mapsto V(H)$ tale che $\forall u,v \in G$:

$$
\{u,v\} \in E(G) \iff \{f(u),f(v)\} \in E(H)  
$$
**Osservazione** Sia $f$ che $f^{-1}$ sono *omeomorfismi* (morfismo).

> Quindi per verificare che due grafi sono isomorfi devo trovare una biiezione che preserva le adiacenze.

**Remark** E' chiaro che $G \cong H$ se e solo se $G^c \cong H^c$.

Dua grafi $G = (V(G), E(G))$ e $H = (V(H), E(H))$ sono *omeomorfi* se esiste una biiezione tra i vertici $f : V(G) \mapsto V(H)$ tale che $\forall u,v \in G$:

$$
\{u,v\} \in E(G) \implies \{f(u),f(v)\} \in E(H)
$$

**Def** Un *Automorfismo* è un isomorfismo da $G$ in se.

**Osservazione** Il numero di biiezioni da un insieme finito $X$ in se stesso, sono le *permutazioni*, pertanto sono $\vert X \vert!$. Questo è un upperbound sugli automorfismi di un grafo.

**Def**  Viene chiamata _classe di isomorfismo di $G$_ l'insieme di tutti i grafi isomorfi a $G$.

## Invarianti

Non esiste una lista di invarianti completa. 
1. L'ordine $|V(G)|$.
2. La taglia $|E(G)|$.
3. Il numero di componenti connesse $\lambda(G)$
4. La successione dei gradi $\{d_1,\dots,d_n\}$.
5. Il numero di stabilità $\alpha(G)$.
6. Il numero di clique $\omega(G)$.
7. Il numero cromatico $\chi(G)$.


