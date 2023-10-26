# Fattorizzazione QR

Sia $A \in \mathbb{C}^{m\times n}$, esistono una matrice unitaria $Q \in \mathbb{C}^{m\times m}$ ed una matrice trapezoidale siperiore $R \in \mathbb{C}^{m\times n}$ tale che:
$$
A = QR
$$
**Osservazione** Non è unica: introducendo una matrice di fase $S = diag(\theta_1,\dots,\theta_m)$ con $|\theta_i| = 1$ numeri completti di modulo uno (è unitaria), allora vale anche $A = (QS)(S^HR)$, infatti $QS$ è ancora unitaria e $S^HR$ è ancora trapezoidale superiore.  

**Dimostrazione** Dimostriamo costruittivamente l'esistenza della fattorizzazione, possiamo usare i [[Riflettore di Householder]] per annullare gli elementi di $A$ sotto la diagonale ed ottenere $R$ colonna dopo colonna:
$$
U_n\dots U_2\,U_1 A = R
$$
Costruiamo la matrice unitaria del passo $k$ nella seguente maniera:
$$
U_k = 
\begin{pmatrix}
I_{k-1} & 0 \\
0 & U^{(m-k+1)}
\end{pmatrix}
$$
Dove $U^{(m-k+1)}$ è il riflettore associato al vettore
$$
u_k = (x_k,\dots,x_m)^T + \sigma_k e_1^{(m-k+1)}\qquad \sigma_k ||(x_k,\dots,x_m)||_2 e^{i\arg(x_k)}
$$
in maniera tale che azzererà le componenti $x_{k+1},\dots,x_m$, infatti $U_k$ è il riflettore elementare associato al vettore:
$$
u = \begin{pmatrix}
0 \\
u_k
\end{pmatrix}
$$
quindi lascia invariate el prime $k-1$ componenti.
Invertiamo i riflettori:
$$
A = U_1^{-1}\dots U_n^{-1}R = U_1^{H}\dots U_n^{H}R = QR
$$
Siccome i riflettori sono unitari (il prodotto continua ad esserlo). $\square$


### Costo computazionale
Si puà dimostrare che il costo è di $2n^2(m-n/3) + O(mn)$. Dunque, se siamo nel caso quadrato $m=n$ il costo diventa di $4/3n^3 + O(n^2)$, ovvero il doppio della fattorizzazione $LU$. 
Pertanto, come metodo diretto per risolvere un sistema lineare, conviene usare $LU$.

### Stabilità

Si possono dimostrare i seguenti bound sugli elementi delle matrici:
$$
\max_{ij} |q_{ij}| \leq 1 \qquad \max_{ij} \leq \sqrt{n}\max_{ij} |a_{ij}|
$$
Siccome la maggiorazione sugli elementi di $R$ dipende dalla dimensione $n$, si dive essere _stabile in senso debole_. Tuttavia risulta più stabile di $LU$ in cui la dipendenza dalla dimensione era del tipo esponenziale $2^{n-1}$.

## Fattorizzazzione ridotta

Se $A$ è di rango massimo ($n$), allora posso ignorare gli zeri della matrice trapezoidale e considerare solo la sua parte triangolare ed eliminare le ultime colonne di $Q$ (che sarebbero state moltiplicate per zero):
$$
A = Q_nR_n, \qquad Q_n \in \mathbb{C}^{m\times n}\quad R_n \in \mathbb{C}^{n\times n}
$$
Se siamo in questo caso, e richiediamo ad esempio che gli elementi diagonali della matrice $R_n$ siano positivi (posso farlo tramite una matrice di fase $S$), allora $Q_n$ e $R_n$ sono _univocamente determinati_, ed $R_n$ coincide con il fattore $L$ della [[Fattorizzazione di Cholesky]] della matrice (hermitiana def. positiva) $A^HA$:
$$
A^HA = R_n^HR_n
$$
siccome $Q_n^HQ = I_n$.

