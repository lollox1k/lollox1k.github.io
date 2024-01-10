# Precondizionatori

>L'idea è _ridurre il numero di condizionamento_ di un problema, per migliorare la _stabilità_ e la _velocità_ di convergenza.

Sia $P_S$ una matrice non singolare, il sistema $Ax=b$ può essere riformulato in maniera equivalente come:
$$
P_S^{-1}Ax = P_S^{-1}b
$$
questo è un _precondizionamento a sinistra_. E' possibile anche precondizionare a _destra_:
$$
AP_D^{-1}y = b \qquad x = P_D^{-1}y 
$$
ed anche ad ambo le parti:
$$
P_S^{-1}AP_D^{-1}y = P_S^{-1}b \quad x = P_D^{-1}y
$$

### Caso hermitiano definito positivo

Assumiamo che il nostro problema abbia matrice dei coefficenti hermitana definita positiva, e vogliamo che il precondizionatore preservi questa proprietà (ad esempion usiamo un algoritmo che richiede questa ipotesi).

Scegliere $P_S$ (o $P_D$) hermitana positiva non garantisce che $P_S^{-1}A$ lo sia.
Al contrario, una stategia è scegliere $P_S = P_D = P^{1/2}$, infatti la matrice:
$$
P^{-1/2}AP^{-1/2}
$$
è ovviamente hermitiana, ed è definita positiva, infatti vale:
$$
x^H P^{-1/2}AP^{-1/2}x = (P^{-1/2}x)^HA(P^{-1/2}x) > 0 \quad \forall x \neq 0
$$
siccome $A$ è definita positiva.

> Come scegliere P hermitana definita positiva?

Euristicamente, vogliamo che $P$ _clusterizzi_ lo spettro di $A$, ovvero renda gli autovalori simili, in maniera tale da ridurre il più possibile il numero di condizionamento
$$
\mathcal{K}_2(P^{-1/2}AP^{-1/2}) = \frac{\lambda_1}{\lambda_2} \approx 1
$$
Siccome $P^{-1}A$ è simile a $P^{-1/2}AP^{-1/2}$.

Un'alternativa, di costo minore, è scegliere come $P_S = L$ e $P_D=L^H$ con $P= LL^H$ ottenuti dalla [[Fattorizzazione di Cholesky]] del precondizionatore.


## Fattorizzazioni incomplete

L'idea è _preservare la struttura di sparsità_ della matrice da precondizionare. Infatti le normali fattorizzazzioni soffrono del cosidetto fenomeno del _fill in_, oneroso dal punto di vista sia computazionale che di memoria.





