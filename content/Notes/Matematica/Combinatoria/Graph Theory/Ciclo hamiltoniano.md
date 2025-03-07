# Ciclo Hamiltoniano

Ideato da Sir. Hamilton nel 1859 come gioco di società, the _Icosian Game_, perchè originariamente i vertici e gli archi corrispondevano ad un icosaedro. 

**Def** Un ciclo viene detto _hamiltoniano_ se visita tutti i vertici una e una sola volta.

Un grafo che contiene un ciclo hamiltoniano viene detto _grafo hamiltoniano_.

**Oss** Siccome richiediamo unicità dei vertici, deve essere un ciclo e non un circuito!

**Teorema** (G.A. Dirac) Sia $G$ un grafo di ordine $n \geq 3$. Se $\delta(G) \geq n/2$, allora $G$ è hamiltoniano.

**Dim** Consideriamo un cammino massimale $P$ con estremi $v_1,v_p$. Per la massimalità, tutti i vicini di $v_1$ e $v_p$ sono contenuti nel cammino. 
Claim: esiste $1 \leq j \leq p-1$ tale che $v_1 v_{j+1} \in E$ e $v_{j}v_p \in E$.
Se per assurdo non fosse così, ogni vicino $v_i$ di $v_p$ (ce ne sono come minimo $n/2$) non deve avere come vicino un vicino di $v_1$, questo significa:
$$
d(v_1) \leq p-1 -d(v_p)\leq p-1-\frac{n}{2} < n-\frac{n}{2} = \frac{n}{2} 
$$
contro l'ipotesi $\delta(G) \geq \frac{n}{2}$.
L'esistenza di questo $v_i$ permette di costruire un circuito hamiltoniano. $\square$
