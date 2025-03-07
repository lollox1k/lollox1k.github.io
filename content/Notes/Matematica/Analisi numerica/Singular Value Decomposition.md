# Singular Value Decompositon

**Teorema** 
($SVD$ completa). Sia $A \in \mathcal{C}^{m\times n}$, con $m \geq n$. Allora esistono due matrici unitarie $U \in \mathbb{C}^{m\times m}$ e $V \in \mathbb{C}^{n\times n}$ tali che:
$$
U^H A V = \Sigma = diag(\sigma_1,\dots,\sigma_n) \in \mathbb{R}^{m\times n}
$$
dove $\sigma_1 \geq \sigma_2 \geq \dots \geq g_n \geq 0$  detti **valori singolari** sono univocamente determinati.
**Osservazione** Le matrici unitarie $U$ e $V$ non sono uniche, infatti itroducendo una matrice (unitaria) di fase: $S = diag(e^{i\theta_1},e^{i\theta_2},\dots)$ 

**Dim**
Per induzione su $n$, vale per tutte le matrici con $m\geq n$.
- $n=1$, le matrici sono vettori con $k\geq n$ componenti, quindi del tipo $A = a = (a_1,a_2,\dots a_k)^T$. 
Poniamo $\sigma_1 = \Vert A \Vert_2$, e scegliamo $U \in \mathbb{C}^{k\times k}$ la matrice del [[Riflettore di Householder]] associata al vettore $u = a + \sigma_1 e^{i \arg{a_1}} e_1^{(k)}$, che è unitaria ed hermitiana. Scegliendo opportunamente $V = [e^{i\theta}]$ fa si che $U^H A V = Uae^{i\theta} = -\sigma_1 e^{i \arg{a_1}} = \sigma_1 e_1^{(k)} \in \mathbb{R}^{k\times 1}$.
- $n > 1$ facciamo vedere che se la tesi vale per matrici in $\mathbb{C}^{k\times (n-1)}$ con $k \geq n-1$, allora vale anche per matrici in $\mathbb{C}^{m\times n}$ con $m\geq n$.

Per la definizione di norma spettrale, esiste un versore tale che:
$$
||A||_2 = ||Ax||_2
$$
definisco un nuovo versore:
$$
y := \frac{Ax}{||Ax||} \implies Ax = \sigma_1y
$$
dove con abbiamo posto $\sigma_1 = ||Ax|| = ||A||$.

Costruisco due matrici unitarie $U_1$ e $V_1$ che hanno per colonna $y$ ed $x$ rispettivamente. Facciamo il conto $U_1^HAV_1$, in particolare la prima colonna (l'unica che so calcolare)
$$
U_1^HAV_1 e_1 = U_1^HAx = \sigma_1 U_1^Hy = \sigma_1 e_1
$$
duque, in generale
$$
A_1 := U_1^HAV_1 = 
\begin{pmatrix}
\sigma_1 & w^H\\
0 & B
\end{pmatrix}
$$
Dimostriamo che $w^H = 0^H$. Supponiamo per assurdo $w \neq 0$, definiamo il vettore $z := (\sigma_1, w)$, e calcoliamo il prodotto con $A_1$.
$$
||A_1z||_2^2 = ||z||_2^4 + ||Bw||_2^2 
$$
voglio far apparire il raggio spettrale al quadrato, divido per la norma al quadrato di $z$ (posso siccome $z\neq 0$ avendo supposto $w\neq 0$ ):
$$
\frac{||A_1z||^2}{||z||^2} = ||z||^2 + \frac{||Bw||_2^2 }{||z||^2} \geq ||z||^2 = \sigma_1^2 + ||w||^2 > \sigma_1^2
$$
contraddizione con la definizione di raggio spettrale. Dunque $w=0$.
$$
A_1 = 
\begin{pmatrix}
\sigma_1 & 0^H\\
0 & B
\end{pmatrix}
$$
Ora noto che $B \in \mathbb{C}^{(m-1)\times (n-1)}$, dunque posso usare l'ipotesi induttiva:
$$
U_2^H B V_2 = \Sigma_2
$$
Facciamo vedere che $\sigma_1 \geq \sigma_2$. Calcoliamo il raggio spettrale di $A_1^HA_1$:
$$
\sigma_1^2 = \rho(A_1^HA_1) = \rho 
\begin{pmatrix}
\sigma_1^2 & 0^H\\
0 & B^HB
\end{pmatrix} = \max\{\sigma_1^2, ||B||_2^2\}
$$
E' chiaro che moltiplicando a sinistra ed a destra la matrice $A_1$ con le matrici:
$$
\begin{pmatrix}
1 & 0^H \\
0 & U_2
\end{pmatrix} 
\qquad 
\begin{pmatrix}
1 & 0^H \\
0 & V_2
\end{pmatrix}
$$
Ottengo la tesi, ovvero:
$$
U^H A V = \Sigma \qquad\square
$$
**Osservazione** A differenza dei valori singolari, $U$ e $V$ _non sono univocamente determinate_, infatti se $S \in \mathbb{C}^{n\times n}$ è una matrice di fase e $Z \in \mathbb{C}^{(m-n)\times(m-n)}$ è una matrice unitria, continua a valere:
$$
A = U\begin{pmatrix}
S & 0 \\
0 & Z 
\end{pmatrix}
\Sigma S^H V^H
$$
## Interpretazione dei valori singolari

Sono una generalizzazzione degli autovalori per matrici rettangolari. Se condieriamo le $m$ colonne di $U$ e le $n$ colonne di $V$, dalla decomposizione otteniamo che:
$$
A = U\Sigma V^H = \sum_{i=1}^n \sigma_i u_iv_i^h
$$
quindi:
$$
Av_i = \sigma_i u_i \qquad A^Hu_i = \sigma_i v_i \quad i=1:n
$$
infatti $v_i$ vengono detti _vettori singolari destri_ di $A$ e i $u_i$ _vettori singolari sinistri_ di $A$.

## SVD ridotta

Sia $\sigma_k$ l'ultimo valore singolare non nullo. Dati i molti elementi nulli di $\Sigma$, possiamo introdurre una fattorizzazione ridotta:
$$
A = U_k\Sigma_k V_k^H
$$
con $\Sigma_k \in \mathbb{R}^{k\times k}$ diagonale, $V_k \in \mathbb{C}^{n\times k}$ e $U_k \in \mathbb{C}^{m\times k}$.

**Proposizione** ($\ker$) Sia $\sigma_1 \geq \sigma_2 \geq \dots \geq sigma_k > \sigma_{k+1} \dots = 0$. Ovvero $\sigma_k$ ultimo valore singolare non nullo. Allora il $\ker(A)$ è generato dai vettori singolari destri $v_{k+1},\dots, v_n$.
**Dim** $x \in \ker(A)$ significa $U\Sigma V^H x = 0$, siccome $U$ è unitaria è equivale a $\Sigma V^Hx = 0$, ma per costruzione tutte le componenti $k+1,\dots,m$ sono nulle, dunque basta richiedere $V_k^Hx = 0$ ovvero $x$ deve essere ortogonale alle prime $k$ colonne di $V$, quindi deve essere nello span delle altre colonne. $\square$

**Proposizione** $range(A)$ Sia $\sigma_1 \geq \sigma_2 \geq \dots \geq sigma_k > \sigma_{k+1} \dots = 0$. Ovvero $\sigma_k$ ultimo valore singolare non nullo. Allora il $range(A)$ è generato dai primi $u_1,\dots u_k$ vettori singolari di sinistri.
**Dim** $y \in range(A)$ signficia $\exists x \mathbb{C}^n$ tale che $U_k\Sigma_k V_k^Hx = y$. Chiamiamo $z := \Sigma_k V_k^Hx$, la condizione diventa
$$
U_k z = y
$$
ovvero $y$ _è nello spazio generato dalle prime $k$ colonne di $U$_. 
Viceversa, se $y = U_k z$ per un qualche $z \in \mathbb{C}^k$,  riesco a trovare un $x \in \mathbb{C}^n$ tale che:
$$
z = \Sigma_kV_k^Hx
$$
siccome $\Sigma_k V_k^H$ è invertibile (Rouché-Capelli).

**Corollario** Il rango di $A$ è uguale al numero di valori singolari non nulli.
**Dim** $rank(A) = dim(range(A)) = k$. $\square$

## Norme e valori singolari

**Proposizione** Per i valori singolari di $A \in \mathbb{C}^{m\times n}$ vale:
$$
\sigma_i = \sqrt{\lambda_i(A^HA)}
$$
(avendo supposto ordinati correttamente gli autovalori).

**Dim** Uso la SVD:
$$
A^HA = (U\Sigma V^H)^H(U\Sigma V^H) = V \Sigma^H \Sigma V^H
$$
La matrice $\Sigma^H\Sigma \in \mathbb{R}^{n\times n}$ non è altro che la matrice $diag(\sigma_1^2,\dots,\sigma_n^2)$.
Osserviamo come $A^HA$ e $\Sigma^H\Sigma$ siano _matrici simili_, dunque hanno lo stesso spettro. $\square$

**Corollario** Da queste considerazioni segue che:
- $||A||_2 = \sqrt{\rho(A^HA)} = \sigma_1$ 
- $||A||_F = \sqrt{\sum_{i=1}^n |\lambda_i|^2} = \sqrt{\sum_{i=1}^n \sigma_i}$  

**Corollario** Se $A$ è invertibile, allora vale $||A^{-1}||_2 = \frac{1}{\sigma_n}$
**Dim** Vale $A^{-1} = V \Sigma^{-1} U^H$, la norma spettrale è l'autovalore di modulo massimo, che sarà $\frac{1}{\sigma_n}$ (l'inverso del più piccolo).

Segue dirattmente che il numero di condizionamento spettrale può essere calcolato come:
$$
\mathcal{K}_2(A) = \frac{\sigma_1}{\sigma_n}
$$

## Approssimazione di rango basso

Sia $A \in \mathbb{C}^{m\times n}$, con $m\geq n$ di rango $k \leq n$, sia $1\leq r < n$ un intero. Sia $\mathcal{B}$ l'insieme di tutte le matrici $m\times n$ di rango minore uguale a $r$, vogliamo determinare $B^*  \in \mathcal{B}$ tale che:
$$
B^* = argmin_{B \in \mathcal{B}}||A-B||_2, \qquad \delta = ||A-B^*||_2
$$
**Teorema** Sia $A \in \mathbb{C}^{m\times n}$ di rango $k \leq n$. Sia $r < k$. Allora la soluzione del problema precedente è data da:
$$
B^* = A_r := U_r \Sigma_r V_r^H \qquad \delta = \sigma_{r+1}
$$
**Dim** Dimostriamo subito la seconda uguaglianza:
$$
||A-A_r||_2 = ||U^H(A-A_r)V||_2 = \sigma_{r+1}
$$
Supponaimo per assurdo che esista una $B \in \mathcal{B}$ tale che:
$$
||A-B||_2 < \sigma_{r+1}
$$
quindi una soluzione migliore di $A_r$. 
$B$ ha rango minore o uguale a $r$, il $\ker(B)$ ha dimensione almeno $n-r$. Sia  $z \in \ker(B)$ e $z \neq 0$, vale:
$$
||Az||_2 = ||(A-B)z||_2  \leq \Vert A-B\Vert \Vert z\Vert < \sigma_{r+1}\Vert z \Vert
$$
Consideriamo ora il sottospazio $S = span(v_1,\dots,v_{r+1})$. Per ogni vettore $z \in S$ vale:
$$
\Vert Az \Vert_2^2 = \Vert \Sigma V^Hz \Vert_2^2 = \left\Vert \Sigma \sum_{i=1}^{r+1}\alpha_i v_i\right\Vert_2^2 = \sum_{i=1}^{r+1} \Vert \sigma_i \alpha_i\Vert^2_2 \geq \sigma_{r+1}^2 \Vert z \Vert_2^2
$$
questa disuguaglianza è incompatible con quella di prima (tranne nell'origine), dunque il sottospazio $S$ deve essere disgiunto da $\ker(B)$, ma ciò è impossibile perchè la dimensione della loro somma ha dimensione almemo $n+1$, assurdo. $\square$

L'utilità del valore $\delta = \sigma_{r+1}$, è che ci permette di stimare la probabilità che gli errori di macchina rendano la matrice di rango inferiore.

Effettivamente per quanto abbiamo dimostrato prima, il [[Numero di condizionamento di una matrice]] non è altro che l'inverso della distanza con le matrici di rango inferiore normalizzata per la norma spettrake della matrice:
$$
\frac{\sigma_n}{\Vert A \Vert_2} = \frac{\sigma_n}{\sigma_1} = \frac{1}{\mathcal{K}_2(A)} = \left\{ \frac{\Vert\delta A\Vert_2}{\Vert A \Vert_2} \;:\, A + \delta A \text{ è singolare }\right\}
$$





