# Metodo CG

Il metodo del gradiente coniugato (Hestenes-Stiefel 1950) costruisce la _nuova direzione di discesa_ come _combinazione lineare della direzione precedente e del residuo_.

**Pseudo codice**

Direzione di ricerca iniziale $p_0 = r_0$
_for_ $k = 0,1,\dots$
	calcolo step $\alpha_k = \frac{r_k^Tr_k}{p_k^TAp_k}$
	update soluzione $x_{k+1} = x_k + \alpha_k p_k$
	update residuo $r_{k+1} = r_k - \alpha_kAp_k$
	calcolo step $\beta_{k+1} = \frac{r_{k+1}^Tr_{k+1}}{r_k^Tr_k}$
	update direzione discesa $p_{k+1} = r_{k+1} + \beta_{k+1}p_k$
_end_

**Osservazioni** Le quantità $r_k^Tr_k$ e $Ap_k$ compaiono due volte, pertando conviene memorizzarle per evitare calcoli unitili (il residuo compare anche nell'iterazione successiva).

Il calcolo del passo $\alpha_k$ dinamico segue sempre una  _minimzation rule_, infatti:
$$
\alpha_k = \frac{r_k^Tp_k}{p_k^TAp_k} = \frac{r_k^T(r_k + \beta_kp_{k-1}))}{p_k^TAp_k} = \frac{r_k^Tr_k}{p_k^TAp_k}
$$
siccome per l'[[Metodi del gradiente#Steepest descent (SD)|osservazione di ortogonalità]] tra i residui e le direzioni di ricerca precedenti $r_k^Tp_{k-1} = 0$.


Si può dare una caratterizzazione equivalente del passo $\beta_k$.
**Lemma** Se si ha, per $k\geq 1$, $r_k^Tr_{k+1}=0$ e, per $k>1$, $p_{k-2}^TAp_{k-1}=0$, allora vale
$$
\beta_k = -\frac{r_k^TAr_{k-1}}{p_{k-1}^TAp_{k-1}} \qquad \text{ per } k\geq 1
$$
Tuttavia questa formulazione è computazionalmente meno conveniente.


Enuciamo ora un teorema fondamentale che caratterizza il metodo CG.

**Teorema** Siano stati compiuti $k$ passi, allora vale la seguente indentità tra sottospazi:
$$
span\{p_0,\dots,p_j\} = span\{r_0,\dots,r_j\} \qquad \text{ per } 0 < j \leq k
$$
inoltre i residuo sono mutualmente ortogonali, e le direazioni di discesa sono $A$-coniugate (ortogonali):
$$
r_k^Tr_j = 0 \qquad p_k^TAp_j = 0 \qquad \text{ per } j < k 
$$
**Dim** La prima identità tra gli span è immediata, segue dalla definizione della direzione di discesa:
$$
p_j = r_j + \beta_j p_{j-1} \quad 1 \leq j \leq k\qquad p_0 = r_0
$$
Per dimostrare l'ortogonalità procediamo per induzione su $k$. 
La base $k=1$ è vera, infatti:
$$
r_1^Tr_0 = r_1^Tp_0 = 0
$$
siccome lo step è ottimale, mentre
$$
p_1^TAp_0 = (r_1+\beta_1 p_0)^TAp_0
$$
e usando l'altra caratterizzazione di $\beta_k$ per $k=1$ risulta nullo.
Assumiamo i risultato veri al passo $k-1$, con $k > 1$, mostriamo l'ortgonoalità dei residui:
$$
r_k^Tr_j = (r_{k-1}-\alpha_{k-1}Ap_{k-1})^Tr_j = r_{k-1}^Tr_j -\alpha_{k-1}p_{k-1}^TAr_j = 0
$$
infatti per induzione, se $j < k-1$, il primo addendo è nullo, il secondo segue sempre dall'ipotesi induttiva e dall'uguaglianza degli span.

Resta il caso $j = k-1$, qui possiamo usare la definizione di $\alpha_{k-1}$:
$$
r_{k-1}^Tr_{k-1}-\frac{r_{k-1}^Tr_{k-1}}{p_{k-1}^TAp_{k-1}}p_{k-1}^TAr_{k-1} = 0
$$
Infatti il denominatore si può riscrivere come
$$
p_{k-1}^TAp_{k-1} = p_{k-1}^TA(r_{k-1}+\beta_{k-1}p_{k-2})
$$
e per ipotesi induttiva l'addendo con $\beta_{k-1}$ è nullo.

Resta da dimostrare che le direzioni di discesa sono $A$-coniugate.
$$
p_k^TAp_j = (r_k+\beta_kp_{k-1})^TAp_j = r_k^TAp_j + \beta_k p_{k-1}^TAp_j
$$
Se $j < k-1$ per ipotesi induttiva il secondo termine è nullo, il primo sempre per ipotesi induttiva e per l'uguaglianza degli span.
Per dimostrae il caso $j = k-1$, si utilizza la definzione di $\beta_k$ del _lemma_:
$$
r_k^TAp_{k-1} + \beta_k p_{k-1}^TAp_{k-1} = r_k^TAp_{k-1} -\frac{r_k^TAp_{k-1}}{p_{k-1}^TAp_{k-1}}p_{k-1}^TAp_{k-1} = 0 \quad \square
$$

>Una conseguenza fondametale di questo teorema, è che (al netto di errori di calcolo) il metodo CG è un metodo diretto!

**Teorema** Sia $A \in \mathbb{R}^{n\times n}$ simmetrica e definita positiva, applicando il metodo CG al problema $Ax=b$, a partire da una qualsiasi solizione $x_0$, si ha convergenza in al più $n$ passi alla soluzione esatta.

**Dim** Segue direttamente dal teorema precedente, infatti $r_n = 0$ siccome $span\{r_0,\dots,r_{n-1}\} = \mathbb{R}^n$ e $r_n^Tr_j = 0$ per $j < n$. Quindi $x_n = x$, ovvero la tesi. $\square$

## Velocità di convergenza

Si può dimostrare che il _fattore di abbattimento dell'errore_ del metodo CG è
$$
\frac{2\left(\frac{\sqrt{k_2(A)}-1}{\sqrt{k_2(A)}+1}\right)^{k+1}}{1+\left(\frac{\sqrt{k_2(A)}-1}{\sqrt{k_2(A)}+1}\right)^{2(k+1)}}
\approx
2\left(\frac{\sqrt{k_2(A)}-1}{\sqrt{k_2(A)}+1}\right)^k \qquad k >>1
$$
quindi _migliore_ di quello di [[Metodi del gradiente#Steepest descent (SD)|Steepest descent]].

## Metodo precondizionato PCG

Per migliorare il condizionamento del sistema $Ax=b$ possiamo usare le [[Precondizionatori|tecniche di precondizionamento]] che preservino la proprietà di $A$ di simmetria e definita positiva, ad esempio con la fattorizzazione di Cholesky incompleta:
$$
L_{inc}^{-1}AL_{inc}^{-T}x = L_{inc}^{-1}b
$$
Tuttavia quando si implementa, non si calcola esplicitamente il nuovo sistema lineare precondizionato, ma si lavoro su di esso _implicitamente_.
Per illustrare questa strategia, ragioniamo con il prodotto scalare indotto da un precondizionarore $P$ simmetrico e definitio positivo; valgono le seguenti osservazioni:
**Osservazione** Se $A$ è simmetrica e definita positiva, allora $P^{-1}A$ risulta simmetrica e definita positiva rispetto al $P$-prodotto scalare.
**Dim** Segue dalla definizione:
$$
(P^{-1}Ax,y)_P = x^TA^TP^{-T}Py = x^TAy = x^TPP^{-1}Ay = (x,P^{-1}Ay)_P
$$
$$
(P^{-1}Ax,x)_P = x^TAx > 0 \qquad \forall x \neq 0
$$
Inoltre si sta minimizzando il medesimo funzionale:
$$
\Phi_P(x) = \frac{1}{2}x^TP(P^{-1}A)x - x^TPP^{-1}b = \Phi(x)
$$
Quindi si lavoro con il $P$-prodotto scalare sul sistema $P^{-1}A$.

Come si modifica lo pseudocodice?

_Calcolo il residuo del sistema precondizionato_ $P^{-1}Ax=P^{-1}b$
$z = P^{-1}x$. Se usiamo $P = L_{inc}L_{inc}^T$ possiamo risolverlo usando forward e backward.

_Calcolo dello step ottimale_
$\alpha_k = \frac{(z_k,z_k)_P}{(p_k,P^{-1}Ap_k)_P}$
svolgendo i conti viene fuori:
$$
\alpha_k = \frac{r_k^Tz_k}{p_k^TAp_k}
$$
_calcolo step per dir discesa_:
Anche qui risulta
$$
\beta_{k+1} = \frac{r_{k+1}^Tz_{k+1}}{r_k^Tz_k}
$$
Direzione di ricerca iniziale $p_0 = z_0$

_for_ $k = 0,1,\dots$
	calcolo step $\alpha_k = \frac{r_k^Tr_k}{p_k^TAp_k}$
	update soluzione $x_{k+1} = x_k + \alpha_k p_k$
	update residuo $r_{k+1} = r_k - \alpha_kAp_k$
	calcolo step $\beta_{k+1} = \frac{r_{k+1}^Tr_{k+1}}{r_k^Tr_k}$
	update direzione discesa $p_{k+1} = r_{k+1} + \beta_{k+1}p_k$
_end_


### Criterio di arresto
Generalmente si usa il rapporto tra la norma euclidea del residuo con la norma euclidea del termine noto
$$
\frac{\Vert r_k\Vert_2}{\Vert b \Vert_2}< \text{ tol }
$$
non il residuo precondizionato! Non vale la pena calcolare la norma dell'energia del residuo ad ogni passo.


## Interpretazione come metodo di Krylov

Il metodo CG può essere visto come un metodo di Krylov in cui la soluzione al passo $k$ è scelta per minimizzare la norma dell'energia dell'errore.

**Teorema** Sia $A \in \mathbb{R}^{n\times n}$, simmetrica definita positiva (SPD), applicando il metodo CG con $x_0 = 0$, la soluzione approssimata $x_k$ risulta l'unico vettore che rende minima la norma dell'energia dell'errore, ovvero:
$$
\Vert e_k \Vert_A = \min_{v \in K_k(A,r_0)} \Vert x-v\Vert_A
$$
**Dim** Supponiamo che $\hat x = x_k - \Delta x$ sia la soluzione al problema di minimizzazione, Facciamo vedere che $\Delta x = 0$. Calcoliamo la $A$-norma dell'errore:
$$
\Vert \hat e \Vert^2_A = (e_k+\Delta x)^TA(e_k+\Delta x) = e_kTAe_k + \Delta x^TA\Delta x + 2e_k^TA\Delta x
$$
ma $Ae_k = r_k$ ed è ortogonale a $\Delta x  \in K_k(A,r_0)$.  Ma $A$ è definita positiva, dunque:
$$
\Vert \hat e\Vert^2_A \geq \Vert e_k \Vert^2_A
$$
con uguaglianza se e solo se $\Delta x = 0$, ovvero $\hat x = x_k$. $\square$




