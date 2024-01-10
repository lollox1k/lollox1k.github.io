# Teorema di Bondy

E' un'applicazione degli [[Alberi]], nel constesto di compressione di stringhe.

**Teorema** (Bondy)
Fissato $n>0$, preso $X = [n]$, presi qualunque $A_1,\dots,A_n \subseteq X$ sottoinsiemi distinti, $\exists x \in [n]$ tale che $A_1\setminus x, A_2\setminus x, \dots A_n\setminus x$ sono ancora distinti.

Il teorema può anche essere espresso rappresentando i sottoinsiemi come stringhe binarie $\sigma_i$ di $n$ elementi, nella maniera usuale: se $x \in A$ allora il carattere $x$-esimo sarà $1$, zero altrimenti. Quindi il teorema mi garantisce che posso rimuovere una colonna, ed accorciare tutte le stringhe di uno senza perdere l'unicità.

**Dim 1** Costruisco un grafo $G$ con vertici gli $n$ sottoinsiemi della famiglia $V(G) = \{A_i : i \in [n]\}$, e li collego se:
$$
\{A_i, A_j\} \in E(G) \quad\iff\quad d_H(\sigma_i, \sigma_j) = 1
$$
ovvero se i due sottinsiemi _differiscono per un solo elemento_ (distanza di Hamming uno delle stringe).

Inoltre _etichetto l'arco_ con l'elemento per cui differeiscono.

**Claim 1** Se $G$ è aciclico, allora $|E(G)| \leq n-1$ per il [[Grafo semplice#Lemma aciclico|lemma]]. Quindi il numero di etichette presenti sul grafo sono al più $n-1$, dunque ne esiste per forza una che non compare, e che posso rimuovere senza far collidere le stringhe ridotte.

Facciamo vedere che si può sempre trasformare il grafo in uno aciclico con le stesse etichette.

Supponiamo che $G$ contenga un ciclo. L'osservazione chiave è che se un arco è etichettato con l'elemento $h$, allora dovrà apparire anche su qualche altro arco del ciclo. Infatti, se percorro il ciclo, ad ogni passo ho cambiato un elemento. Per tornare la stringa iniziale, devo ricancellare il cambiamento, quindi $h$ deve apparire almeno un'altra volta.
Allora sia $G' = G \setminus e$ dove l'arco rimosso è uno etichettato con $h$. Siccome $h$ compare almeno un'altra volta, $G'$ ha le stesse etichette di $G$, ed ha un ciclo in meno. 
Se $G'$ è aciclico, ho fatto. Altrimenti proseguo fino ad arrivare ad un grafo $G_0$ aciclico con le stesse etichette di $G$.

**Dim 2** (Machì-Malvenuto) L'idea è ordinare le stringhe caratteristiche in modo lessiconografico. Sia $\varphi(i)$ la prima coordinata in cui $\sigma_i$ e $\sigma_{i+1}$ differiscono. Questo implica che:
$$
|\varphi([n-1])| \leq n-1 \implies \exists j \notin \varphi([n-1])
$$
