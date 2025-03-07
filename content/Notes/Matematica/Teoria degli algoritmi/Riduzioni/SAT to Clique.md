Sia $F$ un'istanza del problema SAT, ovvero la soddisfacibilità di formule booleana in forma CNF.
Mostriamo una rimappatura dell'instanza in un'istanza del problema della Clique, che rispetta le proprietà della [[Riduzione polinomiale]].

I nodi del grafo sarannò creai in base ai letterali di ciascuna clausola. Posso immaginare il grafo diviso in cluster, ogni claster è una clausola, e contiene i rispettivi letterali. 
Definisco gli archi del grafo nella seguente maniera: dato ogni vertice, lo collego a tutti gli altri, eccetto le negazioni di se stesso (non collego i letterali $\neg l$  a $l$). 

Ovviamente è una procedura linare nella lunghezza della formula. 

Si dimostra banalmente che la formula è SAT se e solo se esiste una Clique di ordine $m$, dove $m$ è il numero di clausole della formula CNF.

