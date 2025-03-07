La dinamica del processo è unicamente determinata dalla distribuzione di offspring. 
Siamo interessati alla distribuzione del numero della popolazione ad ogni step.

>What is the distribution of $Z_n$, per ogni  $n \in \mathbb{N}_0$?

Come simuliamo il processo?
Per produrre $Z_{n+1}$ abbiamo bisogno di una funzione che prenda in input un numero random e la popolazione attuale $Z_n$.

La distribuzione di offspring prende valori in $\mathbb{N}_0$ $\{p_n\}_{n\in\mathbb{N}_0}$  dove $p_k = \mathbb{P}(X = k)$. (in realtà non è una distribuzione ma una proability mass function, pmf perchè è una variabile discreta).

Una strategia è fare $Z_n$ simulazioni e sommare quelle che conducono a $Z_{n+1}$.

I figli al tempo $n+1$ saranno:
$$
Z_{n+1} = X_{n,1} + \dots + X_{n,Z_n}
$$
Possiamo sfruttare le proprietà della funzione generatrice [[Generating functions]].

Siano $T,X_1,X_2, \dots$ variabili indipendenti a valori $\mathbb{N}_0$. Qual è la distribuzione della variabile:
$$
S := \sum_{n=1}^T X_n 
$$
notiamo che:
$$
\{S = k\} = \bigcup_{n=0}^\infty \{T = n\} \cap \{X_1 + \dots + X_n = k\}
$$
Inoltre, nel caso dei branching processes le variabili $X_i$ sono identicamente distribuite, ed ottreniamo:
$$
\psi_S(z) = \psi_T(\psi_X(z))
$$
infatti calcolando esplicitamente:
$$
\psi_S = \sum P[S=k]z^k = \sum_k \sum_n P[T=n]P[X_1 + \dots + X_n = k]z^k = \sum_n P[T=n]\psi_X^n = \psi_T(\psi_X(z))
$$
dove abbiamo usato la proprietà della funzione generatrice di una variaible somma di essere il prodotto delle p.g.f, e che le $X_i$ sono identicamente distribuite.

Applichiamo queste proprietà al processo di Galton-Watson, la variabile $S$ sarà:
$$
Z_n = \sum_{i=1}^{Z_{n-1}} X_{n,i}
$$
Sia $\psi$ fa funzione generatrice della offspring distribution e $\psi_{Z_n}$ la funzione generatrice della popolazione al tempo $n$, allora vale:
$$
\psi_{Z_n} = \psi_n 
$$
dove $\psi_n$ è la $n$-esima composizione. Tutto ciò segue induttivamente dal precedente teorema, infatti $n=1$ è vero per definzione, e $\psi_{Z_{n+1}} = \psi \circ \psi_{Z_n} = \psi \circ \psi_n = \psi_{n+1}$. 

Per rispondere alla domanda di Galton [[Motivazione storica]] definiamo la probabilità di estinzione:
$$
q := \lim_{n\to\infty} P[Z_n = 0]
$$
è evidente che è una funzione monotona crescente per $n$.
Per quali condizioni abbiamo $q=0$, $q=1$ o $q \in (0,1)$?

Assumiamo $p_1 \neq 1$. Allora:
1. Sia $F := \{ r \in [0,1] | \psi(r) = r\}$, allora $q = \min{F}$ 
2. abbiamo le equivalenze:
$$
q < 1 \iff \lim_{z\to 1}\psi'(z)>1 \iff \sum_{k=1}^\infty kp_k > 1
$$
#### Dim 
Notiamo che:
$$
\psi_X(0) = P[X=0]
$$
nel nostro caso $q_n = P[Z_n = 0] = \psi_{Z_n}(0) = \psi_n(0) = \psi(\psi_{n-1}(0) = \psi(q_{n-1})$, bella definizione ricorsiva. Essendo $\psi$ continua, e $q_n, q_{n-1}$ entrambe convergono a $q$, segue che:
$\psi(q) = q$ quindi $q \in F$. Sia $r$ un altro generico punto fisso di $\psi$. Mostriamo che vale $q \leq r$. 
Per prima cosa $q_n \leq q_{n+1} = \psi(q_n)$, quindi anche $\psi$ è monotona non decrescente. Allora:
$$
r \geq 0 = q_0 \qquad r = \psi(r) \geq \psi(q_0) = q_1 
$$
Segue induttivamente che $r \geq q_n$ per ogni $n$, quindi $r \geq q$.

Abbiamo quindi una procedura per calcolare la probabilità di estinzione:
- Calcola la funzione generatrice della offspring distribution
- trova i punti fissi, $q$ è il minimo.

Inoltre le equivalenze ci dicono in fretta una condizione per non avere proabilità di estinzione certa: 
- il valore atteso di figli deve essere strettamente  maggiore di 1
che si può esprimere come $\mu = \psi'(1)$.
