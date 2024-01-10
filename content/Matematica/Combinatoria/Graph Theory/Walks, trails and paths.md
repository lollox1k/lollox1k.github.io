## Passeggiate, Cammini, Circuiti, Cicli

Una *passeggiata* (*walk*) in un [[Grafo semplice|grafo]]$G$ dal vertice $x$ ad $y$ è una successione di vertici, archi alternata:
$$
W = x,e_1,z,\dots, e_n, y 
$$
> non aggiungo altre condizioni: posso ripetere vertici ed archi

La *lughezza* della passeggiata è il numero di archi che contiene.

Un *cammino* (*trail*) impongo che gli archi siano diversi. Se è $x=y$ si chiama *circuito*.

Un *cammino semplice* (*path*) è una *passeggiata* senza ripetizioni di vertici (quindi anche di archi). Se $x=y$ si parla di *ciclo*.

**Proposizione** Sia $G$ un grafo con $\delta(G)\geq 2$ (grado minimo almeno $2$). Allora esiste un ciclo.
**Dim** Sia $P$ un cammino massimale, e $u\in V$ uno dei suoi estremi. Siccome $d(u) \geq \delta(G) \geq 2$,  $u$ ha almeno un altro vicino. Se questo vicno non fosse già nel cammino, potrei costruire un cammino più lungo, contro la massimalità. Dunque esiste almeno un ciclo. $\square$

Vediamo una semplice caratterizzazione dei cicli $C_n$.
**Proposizione** Un grafo connesso $G$. Allora $G$ uniforme di grado $2$ se e solo se $G=C_n$.
**Dim** 
- ($\impliedby$) Banale.
- $(\implies)$ Per la proposizione precedente esiste un ciclo $C \subseteq G$. Supponiamo per assurdo che $\exists v \in V(G)$ tale che $v \notin C$. Siccome $G$ è connesso, riesco a trovare un vertice $x \in C$ ed uno $y \notin C$ tali che $\{x,y\} \in E(G)$. Ma allora $d(x) \geq 3$, assurdo. $\square$