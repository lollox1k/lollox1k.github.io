# Formula di Cayley


**Teorema** Il numero di Alberi con vertici etichettati di ordine $n$, ovvero il numero di alberi di copertura di $K_n$, è $T(n) = n^{n-2}$.

**Proof** (_Prufer's code_)
Prufer ha trovato una biiezione tra alberi etichettati e stringhe di lunghezza $n-2$ di $n$ caratteri, un insieme di cardinalità facile da calcolare.

The following is an algorithm to generate the prufer code of a given tree.
$$
c : T \to [n]^{n-2}
$$
**Prufer's method to assign a code to a labeled tree**
Given a tree $T$, with labeled vertices $1,\dots,n$.
1. Let $i=0$, and let $T_0=T$.
2. Find the leaf on $T_i$ with the smallest label and call it $v$.
3. Record in the sequence of labels $v$'s  (only) neighbor.
4. Remove $v$ from $T_i$ and create a new $T_{i+1}$.
5. If $T_{i+1} = K_2$, then stop. Otherwise $i++$ and go back to step 2.

> sostanzialmente stiamo potando le foglie dell'albero in ordine crescente di label, ed annotando dove erano attaccate! _Prufer's pruning!_

**Osservazione 1** Ogni vertice $v$ appare $d(v)-1$ volte nella sequenza (le foglie non compaiono).

**Osservazione 2** La fermandomi quando rimangono solo due vertici ottengo una stringa lunga $n-2$. Potrei completarla univocamente ad una stringa di $n-1$ caratteri con il massimo label rimasto! Il codice completo rappresenta, insieme alla sequenza dei vertici rimossi gli $n-1$ archi di $T$.

**Osservazione 3** Ad ogni passo ho sempre almeno due foglie, quindi non toglierò mai il vertice con il label più grande $v_n$.

**Prufer's method to assign a labeled tree to a code**
Given a sequence $\sigma = a_1,a_2,\dots,a_k$ of entries from the set $\{1,\dots,k+2\}$.
1. Draw $k+2$ vertices; lebel them $v_1,v_2,\dots, v_{k+2}$. Let $S = \{1,2,\dots,k+2\}$.
2. Let $i=0$, let $\sigma_0 = \sigma$. Let $S_0 = S$.
3. Let $j$ be the smallest number in $S_i$ that does not appear in the sequence $\sigma_i$.
4. Place an edge between vertex $v_j$ and the vertex whose subscript appears first in the sequence $\sigma_i$.
5. Remove the first number in the sequence $\sigma_i$ to create e new sequence $\sigma_{i+1}$. Remove the $j$ element from the set $S_i$ to create $S_{i+1}$.
6. If the sequence $\sigma_{i+1}$ is empty, place an edge between the two vertices whose subscripts are in $S_{i+1}$, and stop. Otherwise, increment $i$ by $1$ and return to step $3$.

We need to prove that such function is a biijection.

**Dim**  First we prove that is an injection, that is: if $T \neq T'$ then $c(T)\neq c(T')$.
This is obvious, since given a prufer's code, we can reconstruct (this is another biijection) the complete one, which is the edges of each tree. So different trees (different edges) means different codes.

Remains to prove surjectivity, that is, for each string $(a_1,a_2,\dots,a_{n-2}) \in [n]^{n-2}$ we can construct a tree $T$ such that  $c(T)=(a_1,a_2,\dots,a_{n-2})$. 
Again, we can construct a complete code from the string, each column is an edge of the $n$ vertices. We need to prove that this make sense, that this a tree. 
Each column, is distinct, since once a vertex appears in the lower part of the code, it's removed from the tree, so it won't appear ever next.
Since there are $n-1$ (distinct) edges and $n$ vertices by contruction, we need to prove that is acyclic. We claim that the graph constructed adding edges from right to left, is always acyclic, since when adding the vertex in the lower part of the code, it's always different from the top right vertices, and also the bottom right, so it can't build a cycle! Hence the final graph is a tree. $\square$

### Dimostrazione con la teoria delle specie

Idea: creare una biiezione tra gli insiemi $\mathcal{V}(n)$ dei _vertebrati_ etichettati e $\mathcal{E}(n)$ le endofunzioni di $[n]$.

Per vedere come questo si riconduce agli alberi, introduciamo gli _alberi radicati_.

**Def** Un albero radicato su $[n]$ è una coppia $(T,x)$ con $T$ albero e $x \in V(T)$ detta radice.

**Osservazione** E' ovvio che dato ogni albero non radicato di ordine $n$, posso costruire $n$ alberi radicati, quindi:
$$
AlbRad(n) = n T(n)
$$
**Def** Un vertebrato su $[n]$ è una terna $(T,c,t)$ con $T$ albero etichettato, $c \in [n]$ la _coda_, e $t \in [n]$ la _testa_ (coda e testa possono coincidere).

**Osservazione** E' ancora ovvio il legame tra i vertebrati e gli alberi:
$$
|\mathcal{V}(n)| = n^2T(n)
$$

Quindi mettendo in biiezione vertebrati ed endofunzioni su $[n]$, che sono banalmente $n^n$, segue immediatamente la formula di Caley.

**Teorama** (_Joyal_) Gli insiemi $\mathcal{V}(n)$ dei vertebrati su $[n]$ e l'insieme $\mathcal{F}(n)$ delle endofunzioni su $[n]$ sono equipotenti.

**Dim** Definiamo la _colonna vertebrale_ come (l'unico) cammino orientato dalla coda alla testa. L'idea è effettuare una "chirurgia", rimuovendo gli archi della colonna vertebrale, ottenendo una foresta. Ogni albero della foresta avrà un unico punto di contatto con la colonna, una _vertebra_. 

Quindi ho decomposto l'albero in sottoalberi indicizzati dalle vertebre:
$$
C = cv_1v_2\dots t \qquad V(T) = \bigcup_{v \in C} V(T_{v})
$$
dove gli alberi sono tutti disgiunti. 
$$
(T,c,t) \rightarrow (V(C), \text{ ordine tot su} V(C), \{T_x | x \in V(C)\})
$$
**Question** Questa decomposizione è biiettiva? Sì.

Ora dobbiamo fare una cosa simile per le endofunzioni.

**Def** Un elemento $a \in [n]$ si dice _ricorrente_ per $f$ se $\exists t>0$ tale che $f^t(a) = a$.
**Def** Un elemento non riccorente si dice _transiente_.

Chiamiamo $\mathcal{R}_f$ tutti gli elementi ricorrenti di $f$,i transianti saranno $[n]\setminus \mathcal{R}_f$.

**Proposizione 1** La restrizione di $f$ ai riccorenti è una biiezione.
**Dim** 
- $f(\mathcal{R}_f) \subseteq \mathcal{R}_f$. Per definizione se $x \in \mathcal{R}_f$ esiste un $t >0$ tale che $f^k(x)=x$. Allora è ovvio che anche $f(x) \in \mathcal{R}_f$, infatti $f^t(f(x))=f(x)$.
- E' iniettiva: siano $a,b \in \mathcal{R}_f$ e i loro rispettivi tempi di ricorrenza $t,s$. E' chiaro che $f^{ts}(a)=a$ e $f^{st}(b)=b$. Supponiamo ora $f(a)=f(b)$:
$$
a = f^t(a) = f^{ts}(a) = f^{st}(b) = f^s(b) = b \qquad \square
$$

**Proposizione 2** Sia $a \notin \mathcal{R}_f$ un elemento transiente, allora $\exists k >0$ tale che $f^k(a) \in \mathcal{R}_f$.
**Dim** Prendo $\{a,f(a),f^2(a),\dots, f^n(a)\} \subseteq [n]$. Per il principio dei cassetti, $\exists 0 < i < j$ tali che $f^i(a)=f^j(a)$, ma questo implica che:
$$
f^j(a) = f^{j-1}(f^i(a)) = f^i(a)
$$
dunque $f^i(a)$ è un ricorrente. $\square$

**Def** Se $a$ è un transiente, chiamo _punto di contatto_ di $a$ il primo dei ricorrenti che incontro iterando la funzione a partire da $a$.

Definiamo la funzione $f : \mathcal{V}_n \mapsto end(n)$ mandnando i vertici della colonna in base al loro ordine naturale e quello indotto dall'oridine (i vertici della colonna vengono permutati dall'endofunzione). Quelli sulle membra in base al primo vicino lungo il cammino diretto che li collega ad una vertebra.

Ora costruiamo il digrafo dell'endofunzione in maniera naturale. Ottengo dei cicli per i ricorrenti (possono essere più cicli separati), e degli alberi che si incontrano ad un ricorrente per i transienti. 

Metto in ordine naturale i vertici corrispondenti agli elementi ricorrenti, e sotto la loro immagine nell'endo funzione: è una permutazione che definisce il cammino coda-testa.

### Dimostrazione per ricorrenza con i coefficienti multinomiali

Sia $T(n; d_1, \dots d_n)$ il numero di alberi di copertura di $K_n$ con gradi dei vertici (etichettati) fissati. Siccome un albero è connesso deve valere $d_i \geq 1 \;\forall i \in [n]$. 
Quindi $T(n; d_1, \dots d_n) = 0$ se almeno uno dei $d_i = 0$.

Inoltre siccome è un albero sappiamo che:
$$
\sum_i d_i = 2(n-1)
$$
Ora sommiamo su tutte le sequenze di gradi ammissibili:
$$
T(n) = \sum_{(d_1,\dots,d_n)} T(n; d_1,\dots d_n) \quad \text{ con } \quad\sum_i d_i = 2n-2 \text{ e } d_i \geq 1 \;\forall i
$$

Dimostreremo che per ogni $n\geq 3$:
$$
|T(n; d_1,\dots, d_n)| = \binom{n-2}{d_1-1, \dots, d_n-1}
$$
sommando su tutti le successioni di grado ammesse otteniamo $n^{n-2}$.

**Osservazione** Si deve notare che la successione dei gradi in un albero etichettato (in generale, in un grafo qualunque), _non determina il grafo_ stesso.

Vogliamo trovare una relazione di ricorrenza su questi numeri, faremo vedere che vale:

**Proposizione** Se $\sum_i d_i = 2n-2$, $d_i\geq 1$ e . Allora: 
$$
|T(n;d_1,\dots\, d_n)| = \sum_{i=1}^{n-1} |T(n-1; d_1, \dots d_{i-1}, \dots \,, d_{n-1})|
$$
**Dim** il numero di alberi non cambia se permuto le etichette, quindi assumo $d_1\geq d_2 \geq \dots \geq d_n$. $v_n$ è una foglia, quindi se lo rimuovo ottengo un nuovo albero $T'$ con $V(T') = \{v_1,\dots, v_{n-1}\}$ ed archi $E(T') = E(T)\setminus \{v_nx\}$ dove $x$ è l'unico vicino di $v_n$. 
$T' \in T(n-1; d_1,\dots, d_i-1, \dots d_{n-1})$ se $x = v_i$. Quindi sommando su ogni $i$, ottengo:
$$
|T(n;d_1,\dots,d_n)| = \left| \bigcup_{i=1}^{n-1} T(n-1; d_1,\dots, d_i-1, \dots, d_{n-1})\right|
$$
ovviamente l'unione è disgiunta, successione dei gradi diversa implica grafo diverso. Questa è proprio la stessa regola di addizione/ricorsione dei [[Coefficienti multinomiali]].
Dimostriamo ora la formula iniziale sul numero di alberi etichettati data una successione dei gradi, per induzione. 
Il caso base $n=3$ funziona. Supponiamo ora la formula valga per $n-1$. Usando la formula di ricorsione ottenuta sopra, ottengo la tesi:
$$
|T(n;d_1,\dots,d_n)| = \sum_{i=1}^{n-1}\binom{n-3}{d_1-1, \dots d_i -2, \dots, d_{n-1}-1} = \binom{n-2}{d_1-1,\dots d_{n-1}-1,0}
$$

**Corollario** Questo era evidente già dal numero di codici di Prufer per una data sequenza di gradi, $d_1,d_2,\dots$. Potevo contarli con il coefficiente multinomiale e poi sommare su tutte le sequenze ammissibili, ed ottenere $n^{n-2}$.



