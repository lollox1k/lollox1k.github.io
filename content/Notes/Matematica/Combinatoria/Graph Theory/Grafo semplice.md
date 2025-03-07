# Definizioni 
Un grafo semplice $G$ è una tupla $(V,E)$ con $V$ insieme *finito* e $E \subseteq \binom{V}{2}$.


**Osservazione notazione** il simbolo è lo stesso del coefficiente binomiale (la cardinalità massima è quella) ma intendiamo tutti i sottoinsieme di cardinalità esattamente 2 (è diverso dal prodotto cartesiano $V\times V$). In generale:
$$
\binom{X}{k} := \{ A \in 2^X \,\text{ t.c. }\, \vert A \vert = k\}
$$
$V = V(G)$ vertici del grafo $G$
$E = E(G)$ archi del grafo $G$

Se $\{u,v\} \in E$ si dice che i vertici $u$ e $v$ sono *adiacenti*.
Se $u \in e \in E$ si dice che il vertice $u$ è *incidente* sull'arco $e$.
Se $e = \{u,v\}$ i vertici $u$ e $v$ si dicono *estremi* dell'arco $e$.
L'*intorno* di un vertice $v$ è l'insieme dei vertici adiacenti. $\Gamma_G(v)$.
Il *grado di un vertice* $v$ è il numero di archi incidenti ovvero $d(v) = \vert \Gamma_G(v)\vert$.
Il *grado di un grafo* è il grado massimo dei suoi vertici: $d(G) = \max_v d(v)$.
Un vertice di grado nullo è detto *vertice isolato*.
Un grafo si dice *regolare o uniforme* se tutti i vertici hanno lo stesso grado.
Il numero di vertici $\vert V(G)\vert$ viene detto *ordine* di $G$.
Il numero di archi $\vert E(G)\vert$ viene detto *taglia* di $G$.
Es. il grafo vuoto ad $n$ vertici ha ordine $n$ e taglia nulla.
Il grafo completo bipartito $K_{n,m}$ ha ordine $n+m$ e taglia $n\cdot m$.


## Sottografi
Un *sottografo* di $G$ è un grafo $G'$ tale che $V(G') \subseteq V(G)$ e $E(G') \subseteq E(G)$.
Un sottografo viene detto *ricoprente* se $V(G') = V(G)$ (tolgo solo qualche arco).
Un sottografo $G'$ viene detto *indotto* se conservo tutti gli archi possibili, una volta tolto i vertici:
$$
E(G') = E(G) \bigcap \binom{V(G')}{2}
$$
il sottografo è indotto da $V'$, un sottoinsieme dei vertici.

## Grafo complementare
Il complementare $\overline G$ di un grafo $G$ è:
$$
V(\overline G) = V(G) \qquad E(\overline G) = \binom{V(G)}{2} \setminus E(G)
$$
ovvero ha archi "opposti". L'unione dei due grafi è il grafo completo.




### Lemma connessione
Un grafo connesso ad $n$ vertici ha almeno $n-1$ archi.
**Dim**
Per induzione:
$n=1$, niente da dimostrare. 
Supponiamo ora di avere un grafo connesso di ordine $n$, facciamo vedere che deve avere almeno $n-1$ archi. Costruiamo un suo sottografo rimuovendo un vertice $x \in V(G)$ $H = G \setminus \{x\}$. Il grafo ottenuto non è necessariamente connesso, siano $C_1,\dots,C_k$ le sue componenti connesse. In ogni componente connessa possiamo possiamo usare l'ipotesi induttiva:
$$
\forall i = 1,\dots,k \qquad |E(C_i)| \geq |V(C_i)|+1
$$
Ma tutte le $C_i$ sono connesse al vertice $\{x\}$, quindi ho soppresso almeno $k$ archi. Mettendo tutto insieme:
$$
|E(G)| \geq \sum_{i=1}^k |E(C_i)| +k \geq \sum_{i=1}^k (|V(C_i)|-1)+k = |V(G)|-1
$$
Dove il meno uno alla fine è il vertice $x$ che avevo rimosso. $\square$

Una domanda analoga: 
### Lemma aciclico
Qual è il numero massimo di archi per un grafo di ordine $n$ tale che sia aciclico: $n-1$.

**Dim** Per induzione:
$n=1$, niente da dimostrare.
Supponiamo $n>1$, in questo caso esiste almeno un vertice $v \in V(G)$ di grado uno, altrimenti avrei un ciclo per la [[Grafo semplice#Passeggiate, Cammini, Circuiti, Cicli|proposizione]] sopra (se il grafo non ha archi la disuguaglianza è soddisfatta). Creo un sottografo $H = G \setminus \{v\}$. $H$ continua ad essere aciclico, ma è di ordine $n-1$. Per ipotesi induttiva, vale $|E(H)| \leq |V(H)|-1$. Ma per come l'abbiamo costruito:
$$
|E(G)| = |E(H)|+1 \leq |V(H)| = |V(G)| - 1 \qquad \square
$$

**Proof 2** By strong induction. The base case $n=1$ is trivial.
Let $G$ be an acyclic graph of order $n$. Pick an edge $e \in E(G)$ and remove it to get an induced subgraph $G' = G\setminus \{e\}$.
This new graph has two properties:
1. $G'$ is still acyclic;
2. $\lambda(G') = \lambda(G) +1$, since every edge is a [[Cut,Bridges, Block decomposition of a Graph|bridge]], (acylic is the same as minimal connected).
Call $G_1,\dots, G_{\lambda(G')}$ its connected components, since $|V(G_i)| < n$, by the induction hypotesis 
$$
|E(G_i)| \leq |V(G_i)|-1
$$
We can write the size of our starting graph $G$ by summing:
$$
|E(G)| = 1+\sum_{i=1}^{\lambda(G')} |E(G_i)|
$$
the $+1$ is for the removed edge $e$.
$$
|E(G)| \leq 1 + \sum_{i=1}^{\lambda(G')}|V(G_i)|-1 = 1 + n -\lambda(G') = n - \lambda(G) \leq n-1
$$
since the number of connected components of a graph is at least $1$, we get our result. $\square$

**Remark** We have shown more!

Combining the two results, we get an interesting implication:

**Corollary** If $G$ is _connected_ and _acyclic_, then $|E(G)| = n-1$.

**Remark** The converse is not true, consider $C_n$ with an added isolated vertex.







