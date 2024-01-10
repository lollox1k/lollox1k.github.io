# Teorema di Birkoff-von Neumann

Un'altra conseguenza del [[Teorema di Hall|teorema di Hall]] per matrici $0$-$1$.

E' chiaro che un insieme di $1$ indipendenti forma una matrice di permutazione. E' anche ovvio che la somma per righe e colonne da sempre $1$ come risulato.

**Def** Una matrice ad elementi non negativi $A$ viene detta _stocastica_ per righe (colonne) se la somma dei suoi elementi per riga (colonna) è pari ad uno.

**Def** Una matrice $A$ stocastica sia per righe che per colonne viene detta _bistocastica_.

Dunque una matrice di permutazione $P$ è bistocastica. La possiamo interpretare come la matrice di transizione di un processo di Markov deterministico.

Il teorema di Birkoff-von Neumann dice che ogni matrice bistocastica è combinazione convessa di matrici di permutazione.

Facciamo vedere che ogni matrice bistocastica soddisfa la condizione di Hall, dove gli $1$ sono gli elementi non nulli.

**Lemma** Una matrice bistocastica soddisfa la condizione di Hall.
**Dim** Ovvio, se trovassimo un sottoinsieme di righe che non soddisfa la condizione di Hall, la somma per righe fa $k\lambda$, e se per assurdo questi elementi non nulli si trovasserso su meno di $k$ colonne avrei $k\lambda = k'\lambda$ con $k' < k$, assurdo. $\square$

**Corollario** Il permanente di una matrice bistocastica $A$ è diverso da zero $per(A) \neq 0$.

Infatti ogni termine non nullo della somma del permanente è un insieme di rappresentanti distinti.

**Teorema** (Birkoff-von Neumann) Sia $A = (a)_{ij}$ una matrice bistocastica $n\times n$ di somma $\lambda > 0$ su righe e colonne. Allora $A$ è somma di multipli non negativi di matrici di permutazione:
$$
A = \lambda_1 P_1 + \dots \lambda_m P_m, \quad \lambda_i \geq 0
$$
per un opportuno $m$.

**Dim** Per induzione sul numero di elementi diversi da zero della matrici. Essendo $\lambda >0$ vi sono almeno $n$ elementi di questo tipo allora ne ho uno ed uno solo per ogni righa e colonna e tutti valgono $\lambda$, quindi $A = \lambda P$.
Supponiamo ora che abbiamo $k > n$ elementi diversi da zero. Scegliamo un insieme indipendente $S$ di elementi diversi da zero, uno per ogni riga, sia $\lambda_1$ il più piccolo di questi. Creo una nuova matrice con un elemento nullo in più:
$$
A' = A - \lambda_1 P_1
$$
dove $P_1$ è la matrice di permutazione che corrisponde all'insieme indipendente $S$. La nuova matrice $A'$, se non è la matrice nulla, ha ancora elementi non negativi ed è bistocastica con somma $\lambda- \lambda_1$, ma ha un elemento nullo in più! Passo induttivo. $\square$

Questa dimostrazione fornisce di fatto un algoritmo per trovare la decomposizione.

**Oss** Se la matrice ha $\lambda =1$, allora la combinazione conica diventa convessa.