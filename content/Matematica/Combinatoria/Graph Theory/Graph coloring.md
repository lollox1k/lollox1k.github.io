# Graph coloring

### Alcune definizioni

**Def** Una *colorazione* di un [[Grafo semplice]] $G$ è una funzione $f : V(G) \mapsto C$ che mappa i vertici del grafo in un insieme finito $C$, con la proprietà che se $\{u,v\} \in E(V)$, ovvero due vertici sono adiacenti, allora $f(u) \neq f(v)$, hanno un "colore" diverso.

**Def**  Il _numero cromatico_ di una grafo $\chi(G)$ è definito come la _minima cardinalità possibile_  di una colorazione del grafo $G$:
$$
\chi(G) := \min\{ \;\vert f(V(G))\vert \; : \; f \text{ colorazione di } G\}
$$
**Osservazione** Se $F \subseteq G$ è sotto grafo, allora $\chi(F) \leq \chi(G)$. Infatti la restrizione della colorazione di $G$ ai vertici di $F$ è ancora una colorazione per $F$, ma il viceversa non è sempre vero. Quindi il minimo è fatto su un insieme più grande. Data una colorazione ottimale $h$ di $G$ e la sua restrizione:
$$
\chi(F) \leq \vert h(V(F))\vert \leq \vert h(V(G))\vert = \chi(G)
$$
## Relazioni con gli altri invarianti
1. **Clique**
Se un grafo $G$ ha numero di clique $\omega(G) = k$, ovvero contiene una $k$-clique, il suo numero cromatico dovrà essere maggiore di $k$: 
$$
\omega(G) \leq \chi(G)
$$
infatti ho bisogni di  $k$ colori per colorare $K_k$, che è sottografo di $G$, quindi per l'osservazione precedente
$$
\omega(G) = n = \chi(K_k) \leq \chi(G) \qquad \square
$$
2. **Stabile**
O indipendet set. Il numero di stabilità di un grafo $\alpha(G)$ è la massima cardinalità di un indipendet set contenuto in $G$. Vale $\alpha(G) = \omega (\overline G)$. Dalla definizione di colorazione, segue che le preimmagini della colorazione fissato un colore siano un insieme stabile. Quindi una colorazione è una decomposizione di un grafo in insiemi stabili.

**Proposizione** Sia $\alpha(G)$ il numero di stabilità del grafo $G$ (l'ordine dell'insieme stabile massimo che contiene), allora vale il seguente lower-bound per il numero cromatico di $G$:
$$
\frac{\vert V(G) \vert}{\alpha(G)} \leq \chi(G)
$$
($\alpha(G) \geq 1$ per ogni grafo non vuoto).
**Dim**  Sfrutto il fatto che la preimmagine di una colorazione è un insieme stabile, e tutte le preimmagini sono una partizione dei veritici:
$$
V(G) = \dot\bigcup_{c \in C} f^{-1}(c) \qquad |V(G)| = \sum_{i=1}^{\chi(G)} |f^{-1}(c_i)| \leq \chi(G)\alpha(G) \quad \square
$$
**Osservazione** Se ho una $n$-partizione in stabili del grafo $G$, allora $\chi(G) \leq n$.

Si può ottenere un upper bound che riguarda il numero di stabilità:
**Proposition** Let $G$ be a graph of order $n$, then
$$
\chi(G) \leq 1 + n- \alpha(G)
$$
**Proof** Let $S \subseteq G$ be a maximal indipendent set of $G$. We can assign it the same color. For the remaining $n-\alpha(G)$ vertices, assign different colors. This is a valid coloration, so
$$
\chi(G) \leq 1 + n -\alpha(G) \qquad \square
$$


## Algoritmo greedy e upper bound
Da un algoritmo greedy, che procede colorando uno stabile e poi rimuovendolo dal grafo, si ottiene l'upper bound:
$$
\chi(G) \leq d(G) + 1
$$
**Lemma**
Sia $V = V_1 \dot\cup V_2$ e $G_i = G[V_i]$ i due grafi indotti. Allora:
$$
\chi(G) \leq \chi(G_1) + \chi(G_2)
$$
**Dim**
"Incollo" le due colorazioni, creando una colorazione valida sul grafo di partenza:
$$
f : V_1 \dot\cup V_2 \mapsto C_1 \cup C_2
$$
suppongo di avere colori diversi, ovvero $C_1 \cap C_2 = \emptyset$.
$$
f(v) := 
\begin{cases} 
f_1(v) \text{ se } v \in V_1 \\ 
f_2(v) \text{ se } v \in V_2 \\
\end{cases}
$$
$f$ è una colorazione di $G$ con $|f(V)| = \chi(G_1) + \chi(G_2)$, ma non è necessariamente ottima. $\square$

**Dim** Dimostriamo l'upperbound per induzione sul grado del grafo.
Per $d=0$  $G$ è fatto di punti isolati, è $1$-colorabile:
$$
\chi(G) = 1 \leq 0 + 1
$$
Sia $G$ un grafo di grado $k < d$, allora $\chi(G) \leq k + 1 \leq d$.
Facciamo vedere che se $d(G) = d$ allora vale $\chi(G) \leq d + 1$.

L'idea è costruire la colorazione in modo greedy:
1. Coloro un vertice $v$;
2. Costruisco uno _stabile massimale_ $S$ che contiene $v$ e lo coloro del colore di $v$.
3. Rimuovo tutto lo stabile, cambio colore e ripeto.

**Claim** $d(G\setminus S) < d(G) = d$ 
Il grado di ogni vertice in $G\setminus S$ cala di almeno uno, altrimenti significa che non erano collegati a nessun vertice di $S$, quindi sarebbero stati inclusi nello stabile. $\square$

Ho fatto, questo significa che posso usare l'ipotesi induttiva su $G\setminus S$:
$$
\chi(G\setminus S) \leq k +1 < d +1
$$
ma $G\setminus S$ ed $S$ sono una bipartizione di $G$, quindi vale $\chi(G) \leq \chi(S) + \chi(G\setminus S)$, la essendo $S$ uno stabile è $1-$colorabile. Quindi:
$$
\chi(G) \leq \chi(G\setminus S) +1 \leq k+2 < d+2 
$$
che è equivalente a
$$
\chi(G) \leq d+1 \qquad \square
$$

### Colorability and complementary graph

**Proposition** Let $G$ be a graph of order $n$ and $\overline G$ its [[Grafo complementare|complementary graph]]. Then
1. $n \leq \chi(G)\chi(\overline G)$,
2. $2\sqrt{n} \leq \chi(G) + \chi(\overline G)$.

**Proof of 1** Use the lower bounds $\frac{n}{\alpha(\overline G)}\leq \chi(\overline G)$ and  $\omega(G) \leq \chi(G)$, and the fact that $\alpha(\overline G) = \omega(G)$. $\square$
**Proof of 2** Just add the two lower bounds:
$$
\frac{n}{\omega(G)} + \omega(G) \leq \chi(G) + \chi(\overline G)
$$
the function on the left side is 
$$
2\sqrt{n}\leq\frac{n+x^2}{x}
$$
and has a point of minimum when $\omega(G)=\sqrt{n}$, with value $2\sqrt{n}$. $\square$


## Morale sul numero cromatico
$$
1 \leq \omega(G) \leq \chi(G) \leq d(G) + 1 \leq |V(G)|
$$
**Osservazione** Due grafi dove si raggiunge l'upper bound $d(G)+1$ sono ovviamente i grafi completi $K_n$ e i cicli di ordine dispari $C_{2n+1}$.

**Question** Sotto quali ipotesi posso invece avere $\chi(G) \leq d(G)$? Il teorema di [[Teorema di Brooks]] risponde a questa domanda.

