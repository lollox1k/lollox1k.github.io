# Alberi di copertura

Dato un grafo connesso $G$, sicuramente ammette un [[alberi|albero]] di copertura (un sottografo che comprenende tutti vertici e che è un albero).

Un modo per contare tutti gli alberi di copertura di un grafo connesso è tramite il [[teorema di Kirchoff]]. 

La [[Formula di Caley]] conta il numero di alberi di copertura etichettati di $K_n$. Già sapere quanti sono a meno di [[Graph Isomorphism|isomorfismo]] è più complicato.  

Vediamo come costruire un grafo di copertura a partire da un grafo connesso è estremamente facile. Addirittura si può generalizzare al caso di archi pesati, è il problema del  _Mininum spanning tree_ o MST. E' un problema polinomiale, e due approcci greedy lo risolvono.

## Algoritmo di Kruskal 
Algoritmo greedy del 1956.

**Input** Un grafo connesso $G$ ed una funzione di costo $c : E(G) \to [0,\infty)$.
**Output** Un albero di copertura di costo minimo.

$F_0 = (V(G), \emptyset)$ ho $n$ componenti connesse, $n$ vertici, $0$ archi.
_While_ $\lambda(F_i) \neq 1$ 
	Si aggiunga l'arco $e_i$ di costo minimo tale che diminusica le componenti connesse di $F_i$
	$i++$

L'algoritmo termina in esattamente $n-1$ passi, la taglia di un albero.

**Teorema** Il sottografo ottenuto $F_{n-1}\subseteq G$ è un albero ricoprente di costo minimo di $G$.

**Dim** 
- $F_{n-1}$ è un albero, infatti ad ogni passo ho una foresta, alla fine ho una foresta con $n-1$, quindi è connesso. (Non creo mai cicli perchè scelgo archi in modo tale da diminuire le componenti connesse).
-  $c(F_{n-1}) = min \{ c(T) : T \text{ albero di copertura di } G\}$ ?   

Consideriamo un altro generico albero di copertura $T$, ordiniamo i suoi archi in base al costo in maniera crescente. Sappiamo che l'algoritmo prende archi con costi crescenti.

$$
\begin{aligned}
&\text{ archi di } F_{n-1} \qquad &c(e_1) \leq c(e_2) \leq \dots \leq c(e_{n-1}) \\

&\text{ archi di } T \qquad &c(a_1) \leq c(a_2) \leq \dots \leq c(a_{n-1})

\end{aligned}
$$

Se $\forall i$ $c(e_i) \leq c(a_i)$ allora banalmente è vero che $c(F_{n-1}) \leq c(T)$. Supponiamo non sia vero, quindi esiste un primo indice $s$ tale che $c(e_s) > c(a_s)$. Siccome i pesi sono ordinati in maniera crescente, questo vale anche per i successivi. Se il mio algoritmo non ha scelto $a_1,\dots,a_s$ che sono di costo minore di $e_s$ significa che includerli non diminuiva le componenti connesse:
$$
\lambda(e_1,\dots, e_{s-1}, a_1,\dots,a_s) = \lambda(e_1,e_2,\dots,e_{s-1})
$$
E' chiaro che aggiungere archi non può far diminuire le componenti connesse:
$$
\lambda(a_1,\dots,a_s) \geq \lambda(e_1,\dots, e_{s-1}, a_1,\dots,a_s) = \lambda(e_1,e_2,\dots,e_{s-1})
$$

Siccome sono entrambe foreste (sono dei sottografi di alberi) vale la [[Alberi#Caratterizzazione degli alberi|caratterizzazione tramite ordine e taglia]]:
$$
s+\lambda(a_1,\dots,a_s) = n = s-1 +\lambda(e_1,\dots, e_{s-1})
$$
ed arrivo all'assurdo:
$$
\begin{cases}
\lambda(e_1,\dots,e_{s-1}) = \lambda(a_1,\dots,a_s) + 1 \\
\lambda(a_1,\dots,a_s) \geq \lambda(e_1,\dots,e_{s-1})
\end{cases}
$$
$\square$ 


