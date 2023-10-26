# The QR algorithm

The QR algorithm for computing eigenvalues is one of the best known algorithms in numerical analysis. It was developed by G.F. Francis in the $1950$s.

The QR algorithm efficiently provides approximations for _all_ eigenvalues and eigenvectors of a matrix.

### Versione base

$A^0=A$
_For_ $k = 1,2,\dots$
	$A^{k-1} = Q^kR^k$
	$A^k = R^kQ^k$
_End_

**Osservazione** Per costruzione le matrici $A^{k-1}$ e $A^k$ sono unitariamente simili:
$$
A^k = R^kQ^k
$$
moltiplicando a sinistra per $Q^k$ e a destra per ${Q^k}^H$ :
$$
Q_k^HA^kQ_k = A^{k-1}
$$
Anche questa versione semplice dell'algoritmo realizza numericamente una [[Decomposizione di Schur]] della matrice $A$, ovver la successione $\{A^k\} \to U$.
Tale schema è stato raffinato, sia per indebolire le condizioni necessarie per la convergenza che per aumentarne la rapidità.

### Prima variante

Il primo migioramento consiste nel trasformare la matrice $A$ in una matrice $H$ di _hessemberg superiore_ unitariamente simile (per preservare lo spettro). L'idea è che ora si devono annullare solo gli $n-1$ elementi della sottodiagonale.

Inoltre ad ogni passo si effettueranno solo $O(n^2)$ operazioni contro le $O(n^3)$ necessarie per la fattorizzazione QR e il prodotto tra matrici.

Inoltre se $A$ è hermitiana, $H$ è tridiagonale, dunque le operazioni si riducono a $O(n)$.

**Teorema** Se gli autovalori di $A$ hanno tutti moduli distinti, ovvero $|\lambda_1| > |\lambda_2| > \dots > |\lambda_n|$, allora la successione $\{H^k\} \to U$. La velocità di convergenza a zero degli $n-1$ elementi sottodiagonali di $H^k$, chiamati $h_{i,i-1}^k$ $i = 2,\dots,n$ è data da:
$$
|h_{i,i-1}^k| = O\left(\left|\frac{\lambda_i}{\lambda_{i-1}}\right|^k\right)
$$

### Seconda variante: shift e deflazione

Il teorema precedente mostra come la velocità di convergenza del metodo QR dipende da quanto sono ben separati gli autovalori. Con il seguente accorgimento è possibile incrementare la velocità di convergenza.

#### Shift

Assumiamo di avere per ogni iterazione uno _shift_ $\mu_k$. Lo schema con shift:
$H^0=Q^HAQ$
_For_ $k = 1,2,\dots$
	$H^{k-1} - \mu_kI= Q^kR^k$
	$H^k = R^kQ^k + \mu_kI$
_End_

le matrici $H^k$ continuano ad essere unitariamente simili.

Troviamo un $\mu_k$ ottimale ad ogni passo. Euristicamente, siccome la convergenza è dal basso verso l'alto, la migliore stima di $\lambda_n$ si ha per l'elemento $h_{n,n}^k$. 

Lo shift viene chiamato così perchè _shifta lo spettro_. Dunque la velocità di convergenza, per il teorema precedente, risulta:
$$
|h_{n,n-1}^k| = O\left(\left|\frac{\lambda_n-\mu_k}{\lambda_{n-1}-\mu_k}\right|^k\right)
$$
quindi abbiamo reso piccolo il numeratore.
Come condizione di stop controlliamo che l'elemento $h_{n,n-1}^k$ sia abbastanza piccolo:
$$
|h_{n,n-1}^k| < \epsilon(|h_{n-1,n-1}^k|+|h_{n,n}^k|)
$$
Si può dimostrare che la convergenza a zero è quadratica.

#### Deflazione

Giunti a convergenza, la strategia della deflazione si traduce nell’applicare la medesima procedura alla matrice ridotta (ovvero porre in maniera ricorsiva $n \to n-1$ fino a $n=2$.