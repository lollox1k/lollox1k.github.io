# Anello 
Si chiama Anello una famiglia di insiemi $\mathcal{R}$ chiusa per intersezione (prodotto) e differenza simmetrica (somma) finita. Siano $A,B \in \mathcal{R}$:
1. $A\bigcap B \in \mathcal{R}$
2. $A \Delta B \in \mathcal{R}$

Dalle proprietà della differenza simmetrica ed intersezione, segue che un anello è chiuso per tutte le altre operazioni tra insiemi (finite) [[Operation on sets]].

Siccome è non vuoto e chiuso per differenza simmetrica, contiene l'insieme vuoto.

#### Anello con unità 
Se esiste un insieme $E$ tale che per ogni $A \in \mathcal{R}$ si ha:
$$
E \bigcap A = A
$$
allora diciamo che $\mathcal{R}$ ha l'unità (elemento neutro per intersezione, vista come moltiplicazione), e chiamiamo l'insieme $E$ unità. 

Un anello con unità è chiamato un' algebra.

#### Costruzione di un anello partendo da un semi-anello
Abbastanza ovvio, completo il semianello aggiungendo tutte le unioni finite egli elementi del semi anello.

Indichiamo l'anello generato da un semi-anello come $\mathcal{R}(\mathcal{A})$. 

Vale la rappresentazione: $\forall E \in \mathcal{R}(\mathcal{A})$  $E = \cup^M A_i$ con $A_i \in \mathcal{A}$ e disgiunti.

#### Estensione di funzioni additive da un semianello ad un anello 
Segue dalla costruzione dell'anello e dalla rappresentazione come unione finita di elementi del semianello:
$$
\nu(E) := \sum^M \nu(A_i) = \sum^M \mu(A_i)
$$
Si deve fare vedere che è ben definita, esistono più rappresentazioni come unione finita di insiemi disgiunti del semianello, ma il risultato non deve dipendere dalla decomposizione. 


#### Ben definita
Siano date due scomposizioni dell'insieme $E$ , devo dimostrare che:
$$
\sum \mu(F_i) = \sum \mu(E_i)
$$
Prendiamo un elmento $E_i$, possiamo scriverlo come unione finita di elmenti nel semianello:
$$
E_i \subseteq E = \bigcup F_j
$$
$$
E_i = E_i \bigcap E = E_i \bigcap \cup F_j = \bigcup E_i \cap F_j
$$
$E_i$ e $F_j$ sono nel semianello, che è chiuso per intersezioni finite, quindi anche $E_i \cap F_j$ è nel semi anello, possiamo applicare $\mu$ e sfruttare l'additività:
$$
\mu(E_i) = \sum_j \mu(E_i \cap F_j)
$$
Tornando all'insieme $E$ nell'anello:
$$
\nu(E) = \sum_i \mu(E_i) = \sum_i \sum_j \mu(E_i \cap F_j)
$$
E' un'espressione simmetrica per $E_i$ e  $F_j$, posso ripetere il ragionamento partendo da un $F_i$.

#### Additività
Ovvia.

#### Unicità
Supponiamo esistano due estensioni $\nu_i$ e $\nu_2$, che concordano sugli insiemi del semianell. Concordano a che sull'anello?

Ovviamente sì, basta sfruttare la scomposizione (assegnamo i valori agli elmenti dell'anello come somma di valori di elementi del semianello, dove le due funzioni concordano.)

#### La sigma additività si trasmette?
Se la funzione sul semianello è sigma additiva, lo è anche quella estesa sull' anello?
Si sfrutta ancora la scomposizione (finita).
Siano $A, A_i \in \mathcal{R}(\mathcal{A})$ con $A_i$ disgiunti e $A = \cup A_i$ 
facciamo vedere che $\nu(A) = \sum\nu(A_i)$ 
$$
A = \bigcup_i^M E_i
$$
$$
A_n = \bigcup_j^{L(n)} E_{nj} \qquad \nu(A_n) = \sum_j^{L(n)} \mu(E_{nj})
$$
$$
A = \bigcup_{n=1}^\infty A_n = \bigcup_{n=1}^\infty \bigcup_{j=1}^L E_{nj}
$$
$$
E_i = E_i \bigcap A = E_i \bigcap \cup_{n=1}^\infty A_n = E_i \bigcap \cup_{n=1}^\infty \cup_{j=1}^{L(n)}E_{nj} = \bigcup_{n=1}^\infty \bigcup_{j=1}^{L(n)} E_i \cap E_{nj}
$$
Abbiamo quindi espresso $E_i$, un elmento del semi anello come somma numebrabile di elementi del semianello (che è chiuso per intersezione finita). Sfruttiamo la sigma additività di $\mu$ sul semianello:
$$
\mu(E_i) = \sum_{n=1}^\infty \sum_{j=1}^{L(n)} \mu(E_i \cap E_{nj})
$$
Abbiamo finito, basta scrivere $A$ come unione finita degli $E_i$:
$$
\nu(A) := \sum_i^M \mu(E_i) = \sum_{i=1}^M \sum_{n=1}^\infty \sum_{j=1}^{L(n)} \mu(E_i \cap E_{nj})  
$$
Vogliamo riottenere $\nu(A_n)$ dall'espressione di destra, basta usare l'identità:
$$
\mu(E_{nj}) = \sum_i^M \mu(E_i \cap E_{nj})
$$