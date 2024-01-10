Famiglie aristocratiche nel periodo vittoriano erano preoccupate che il loro nome diventasse estinto,  Sir Francis Galton pose la seguente domanda:

>How many male children (on average) must each generation of a family have in order for the family name to continue in perpetuity?  

La risposta venne dal reverendo Henry William Watson nell'articolo _On the probability of extinction of families_ (1874).

Watson propose il seguente modello:
1. popolazione con un individuo al tempo zero: $n=0$, $Z_0 = 1$.
2. al tempo $n=1$ l'individuo produce $Z_1$ copie e muore, $Z_1$ è una variabile aleatoria in $\mathbb{N}_0$. 
3. ad ogni step successivo ciascuno degli individui produce un numero di figli, la distribuzione _offspring distribution_ è assunta sempre la stessa.
Ne segue che al tempo $n+1$  il numero di individui $Z_{n+1}$ sia:
$$
Z_{n+1} = \sum^{Z_n}_{k=1} Z_{n,k}
$$

Definiamo questo processo stocastico un branching process.

E' chiaro che tutta l'evoluzione è determinata dalla _offspring distribution_, la domanda di Galton diventa:
>Quali condizioni deve soddisfare la offspring distribution affinchè non avviene un'estinzione:
>$$
\mathbb{P}( Z_n \geq 1 \forall n \in \mathbb{N}_0) = 1
$$
la probabilità di avere zero individui sia zero.
