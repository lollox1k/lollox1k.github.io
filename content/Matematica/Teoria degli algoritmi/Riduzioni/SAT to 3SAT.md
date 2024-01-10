Partiamo da una formula CNF con clausole di lunghezza variabile, vogiamo generare un'istanza del 3SAT quindi avere solo clausole da 3 letterali in un numero di passi al più polinomniale [[Riduzione polinomiale]].
Per le clausole già di 3 letterali non devo fare niente, per quelle minori aggiungo copie dei letterali:
- Per 1 clausole:
$$
(l) \iff (l\lor z_1 \lor z_2)\land (l \lor \neg z_1 \lor z_2) \land (l \lor z_1 \lor \neg z_2) \land (l \lor \neg z_1 \lor \neg z_2)
$$
Otteniamo una formula che è logicamente equivalente, indipendentemente dal valore di $z_1$ e $z_2$, infatti se $l=0$ non esiste un assegnamento per le $z_1,z_2$ che rende vera la formula.
- Per 2 clasuole:
$$
(l_1 \lor l_2) \iff (l_1 \lor l_2 \lor z) \land (l_1 \lor l_2 \lor \neg z) 
$$
Ancora una volta otteniamo una formula logicamente equivalente, il valore di verità del letterale $z$ non influenza la formula.

- Per quelle più lunghe la questione è delicata, devo aggiungere $k-3$ nuove variabili dove $k$ è il numero di letterali della clausola ($k>3$):
$$
(l_1 \lor \dots \lor l_k) \to (l_1 \lor l_2 \lor z_1) \land (l_3 \lor \neg z_1 \lor z_2) \land \dots \land (l_{k-1}\lor l_k \lor \neg z_{k-3})
$$
In questo caso non abbiamo una formula logicamente equivalente a quella di partenza, ma una formula che è soddisfacibile se e solo se quella di partenza lo è, che è quello che ci basta per il problema 3SAT. 

Primo verso: se la clausola di partenza è UNSAT, allora tutti e letterali non sono messi a vero. Partendo dalla prima clausola, notiamo che deve valere $z_1 = 1$, ma per costruzione vale la catena di implicazioni:
$$
z_1 \to z_2 \to \dots \to z_{k-3}
$$
ma per rendere vera l'ultima clausola necessitiamo che $z_{k-3} = 0$. 

Secondo verso: dato un assegnamento che soddisfa la clausola di partenza, si può estendere alle $z_i$ affinchè anche la formula ridotta sia soddisfatta. Senza perdità di generalità assumo che il letterale soddisfatto non compaia nelle clausole agli estremi (l'ordine dei letterali è arbitrario).

Un assegnamento che soddisfa la clausola di partenza deve mettere a vero almeno uno dei letterali $l_i$ , quindi la corrispondente clausola nella nuova formula è soddisfatta:
$$
(l_1 \lor l_2 \lor z_1) \land \dots \land (l_i \lor \neg z_{i-3} \lor z_{i-2})\land \dots \land (l_{k-1}\lor l_k \lor \neg z_{k-3})
$$

Abbiamo quindi piena libertà per i letterali $z_{i-3}$ e $z_{i-2}$.  Come prima in generale dobbiamo avere $z_1 = 1$ e $z_{k-3} = 0$.  La differenza rispetto al primo caso è che la libertà di scelta dei letterali della clausola che contiene il letterale messo a vero ci permette di "spezzare" la catena di implicazioni, basta porre $z_{i-2} = 0$. $QED$