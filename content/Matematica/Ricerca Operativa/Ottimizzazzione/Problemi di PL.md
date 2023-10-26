Nel contesto PL, vincoli e funzione obbiettivo lineare, posso enunciare risultato più precisi riguardo l' [[Esistenza delle soluzioni ottime]] in generale.

Problema di PL:
$$
\min_{x\in C} c^Tx \qquad x \in P
$$
con $P \subseteq \mathbb{R}^n$ poliedro.

Enunciamo il _teorema fondamentale della programmazione lineare_:
## Teorema fondamentale della PL
Si consideri un problema di PL  e si assuma che $P$ non contenga rette. Allora una e una sola delle seguenti affermazioni è vera:
1. L’insieme ammissibile è vuoto: $P = ∅$ 
2. 2. Esiste una direzione $d ∈ rec(P)$ per cui $c^T d < 0$ e allora il problema è illimitato inferiormente 
3. 3. Per ogni direzione $d ∈ rec(P)$ si ha $c^Td ≥ 0$ e allora il problema ammette soluzione ottima e almeno una soluzione ottima cade su un vertice.

## Dim
E' chiaro come le tre affermazioni si escludano a vicenda. Se $P = \emptyset$ allora anche $rec(P)=\emptyset$ quindi non esistono direzioni di recessione con le proprietà **2** o **3**. E' ovvio anche che queste due si escludono, essendo una la negazione dell'altra.
Restano da dimostrare le due implicazioni in **2** e **3**, ovvero la limitarezza/illimitatezza in basae all'esistenza o meno di quelle particolari direzioni di recessione.

- Supponiamo che esista $d \in rec(P)$ tale che $c^Td < 0$. Dalla definizione di direzione di recessione sappiamo che per ogni $x_0 \in P$:
$$
x_0 + \lambda d \in P \qquad \forall \lambda \geq 0
$$
ma allora lungo questa retta la funzione obbiettivo assume valori aritrariamente piccoliper $\lambda$ abbastanza grandi:
$$
c^T(x_0+\lambda d)= c^T x_0 + \lambda c^T d
$$
- Supponiamo che esista $d\in rec(P)$ tale che $c^Td \geq 0$. Vogliamo far vedere almeno una soluzione ottima è su un vertice, e che il problema non è illimitato inferiormente. Sfruttiamo il fatto che non contenendo rette, ognu punto di $P$ può essere espresso come:
$$
x = \sum_i \lambda_i v_i + d \qquad \sum_i \lambda_i = 1 \quad \lambda\geq 0
$$
combinazione convessa dei vertici e una direzione di recessione. Calcolando la funzione obbiettivo su un $x$ espresso in questa forma:
$$
c^Tx = \sum_i \lambda_i c^Tv_i + c^Td \geq \sum_i\lambda_i c^T v_i \geq c^T v_m
$$
dove $v_m$ è il vertice dove la funzione obbiettivo ha valore minimo. $\square$
>> Recap

La funzione calcolata in un punto generico si può riformulare come funzione dei coefficienti della combinazione convessa e direzione di recessione del poliedro. in questo caso semplice si vede come il valore è somma di coefficienti positivi della funzione calcolata sui vertici, da qui si vede come il minimo è su uno di essi.

### Oss
Cosa ci dice/rassicura questo teorema?
1. Intanto ci dice che per i problemi di PL il 4 caso di  [[Esistenza delle soluzioni ottime]] come outcome possibile per un problema di ottimizzazione (ed esemplificato dal comportamento del problema $\min_{x\leq 0} e^x$ ) non può accadere per problemi di PL. 
2. Poi ci dà l’esistenza anche in assenza di compattezze o coercività. 
3. Inoltre ci dà anche dei criteri ben precisi per determinare l’illimitatezza o l’esistenza di soluzione ottime. 
4. Infine ci dà anche informazioni che sono preziose dal punto di vista algoritmico, su dove trovare una soluzione ottima. Sottolineamo che verificare se esiste una direzione d ∈ rec(P) per cui $c^T d < 0$ o se, al contrario, per ogni direzione d ∈ rec(P) si ha $c^Td ≥ 0$ è un compito teoricamente fattibile, Infatti ricodiamo che per il Teorema 3.84 possiamo scrivere rec(P) = cone(d 1 , . . . , dq ) (si veda anche l’osservazione 3.87). E' immediato allora verificare che esiste una d ∈ rec(P) con c T x ≤ 0 se e solo se $c^Td_i < 0$ per almeno una direzione $d_i$ , $i = 1, . . . , k$. Quindi questa verifica può essere teoreicamente fatta in un numero finito (anche se potenzialmente molto grande) di passi.
