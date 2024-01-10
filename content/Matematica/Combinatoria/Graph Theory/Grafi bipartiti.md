# Grafi bipartiti
Un grafo $G$ si dice _bipartito_ se esiste una partizione dei suoi vertici $V(G) = V_1 \dot\cup V_2$  in due sottoinsiemi disgiunti tale che:
$$
\{x,y\} \in E(G) \quad\iff\quad x \in V_1, \;y \in V_2 \text{ o viceversa}
$$
quindi $V_1$ e $V_2$ sono _stabili_.
Questo concetto si estende in modo naturale a quello di grafo _n-partito_.

**Osservazione** Abbiamo visto che se $f$ è una colorazione di un grafo $G$ allora le controimmagini dei colori definiscono una partizione di V (G) in stabili [[Graph coloring#Relazioni con gli altri invarianti| vedi qui]]. 
Quindi possiamo dire che _$G$ è bipartito se e solo se $\chi(G) \leq 2$_ (il minore uguale è per includere il caso di grafo stabile, con nessun arco che è 1-colorabile e 1-partito, quindi anche 2-partito).

**Osservazione** Data la dualità tra $n$-partizione in stabili e $n$-colorabilità, in generale vale:
$$
\chi(G) = n \text{ con n cardinalità della partizione minima}
$$
**Esempio** Consideriamo il grafo _ipercubo_ di dimensione $n$ $H_n$, dove i vertici sono stringhe $\{0,1\}^n$, e sono collegati se i vertici dell'ipercubo corrispondente hanno uno spigolo tra loro (gli archi), siccome può essere bipartito è due colorabile, indipendentemente dalla dimensione $n$:
$$
V_P := \{ v \in V \;:\; v \text{ ha un numero pari di 1}\}
$$
$$
V_D := \{ v \in V \;:\; v \text{ ha un numero dispari di 1}\}
$$
è chiaramente una partizione dei vertici, i due insiemi sono indipendenti infatti se $\{x,v\} \in E(H_n)$, cambia al più una cifra della stringa: un uno diventa zero o viceversa, di conseguenza se prima gli uni (zeri) erano pari, ora diventano dispari e viceversa. $\square$

## Matching per grafi bipartiti

E' chiaro trovare un [[Matchings|matching]] perfetto in un grafo bipartito è impossibile almeno che $|V_1|=|V_2|$. Rilassiamo la condizione, richiedendo che il mathing saturi solo una delle due parti.

**Def** Sia $G$ un grafo bipartito con $|V_1| \leq |V_2|$, $M$ un suo matching. Diciamo che $M$ è un _matching completo_ se satura tutti i vertici di $V_1$.

La cosa interssante, è che un matching completo e un [[Teorema di Hall|insieme trasversale]] sono praticamente la stessa cosa, infatti posso tradurre una famiglia di sottoinsiemi in un grafo bipartito.

Quando è possibile trovare un matching completo?

**Teorema** (Hall). Sia $G$ un grafo bipartito. Allora esiste un matching completo se e solo se la condizione di Hall è soddisfatta:
$$
\forall S \subseteq V_1 \qquad |\Gamma(S)| = \sum_{x \in S} d(x) \geq |S|
$$
**Dim** Se esiste un matching completo, la condizione di Hall deve valere, infatti anche ogni suo sottinsieme $S \subseteq V_1$ è saturato dal matching, quindi deve valere $|S| \leq |\Gamma(S)|$ (scelgo solo uno dei vicini per ogni vertice in $S$).
Mostriamo ora che è una condizione anche sufficiente. Supponiamo che $|S| \leq |\Gamma(S)|$ per tutti i sottoinsiemi $S \subseteq V_1$, sia $M$ un matching massimo. Supponiamo per assurdo che esista un vertice $u \in V_1$ non $M$-saturato. 
Definiamo l'insieme dei vertici $A \subseteq V(G)$ che possono essere collegati al vertice $x$ tramite un cammino alternante. Sia $S = A \cap V_1$ e $T = A \cap V_2$. Siccome il matching $M$ è massimo, per il teorema di Berge non esiste un cammino alternante, quindi tutti i vertici di $T$ sono $M$-saturi, così come $S \setminus \{x\}$. Questo implica $|T| = |S|-1$, infatti da ogni cammino da $x$ in $S \setminus \{x\}$ visito un numero uguale di volte vertici in $S$ ed in $T$. 
Inoltre dalla definizione vale $\Gamma(S)=T$, infatti, supponiamo esista un vertice $y \in V_2$ e $s \in S$ tale che $sy \in E(G)$ ma $y \notin T$. Siccome non appartiene a $T$, non esiste un cammino alternante $x-y$, quindi l'arco $sy \in M$ (se non fosse nel matching potrei costruire un cammino alternante). Ma questo è assurdo, siccome esiste già un arco del matching che ha come estremo $s$. 
Mettendo insieme, ottengo l'assurdo
$$
|\Gamma(S)| = |T| = |S|-1 < |S| \qquad \square
$$
