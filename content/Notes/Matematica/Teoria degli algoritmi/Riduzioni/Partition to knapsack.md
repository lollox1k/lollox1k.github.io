[[Riduzione polinomiale]]
Nel partition si richiede l'esistenza o meno di un sottoinsieme $S \subseteq X$ di un insieme di interi positivi finito $|X| < \infty$ dato tale che:
$$
\sum_{x\in S} x = \sum_{x \notin S} x
$$
Ne  knapsack si ha come input in insieme finito di "oggetti" che hanno un peso intero $w_i>0$ ed un profitto intero $p_i$>0, ed un valore di peso massimo $W$.  E' evidente il problema di ottimizzazione vincolato al peso massimo, il problema di decisione associato sarà dire se esiste un sottoinsieme degli oggetti che pesa meno di $W$ ed ha profitto totale maggiore uguale a $P$.

### Riduzione partition $\leq$ Knapsack
Chiamando la somma totale dei numeri dell'insieme $X$ T, è ovvio che:
$$
\sum_{x\in S} x + \sum_{x\notin S} x = T
$$
ed essendo uguali:
$$
\sum_{x\in S} x = \sum_{x\notin S} x = T/2
$$
Quindi se è possibile fare questa divisione, esistono anche due insiemi la cui somma totale è $T/2$ (la condizione che la somma totale sia pari è necessaria ma non sufficiente). Identifichiamo il profitto e peso totale $P$ e $W$  del problema knapsack con $T/2$., ed i singoli pesi/profitti con i valori del numero $p_i = w_i = x_i$. 

Vediamo l'altro verso. Chiamiamo $Z$ (da zaino) il sottoinsieme degli oggetti tale che il loro peso totale è minore uguale a $W$, ed il profitto maggiore uguale a $P$. 
$$
\sum_{i \in Z} p_i \geq P
$$
$$
\sum_{i\in Z} w_i \leq W
$$
Ma abbiamo definito $p_i=w_i=x_i$, quindi queste somme sono uguali. 
Vale:
$$
\sum_{i \in Z} w_i = \sum_{i\in Z} x_i \leq W = T/2
$$
analogamente
$$
\sum_{i\in Z} p_i = \sum_{i \in Z} x_i \geq P = T/2
$$
ma questo implica:
$$
\sum_{i \notin Z} x_i = T -\sum_{i \in Z} x_i = T/2
$$
quindi abbiamo diviso gli oggetti di partenza in due sottoinsiemi con uguale somma totale. $QED$.

