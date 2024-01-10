# Numero di condizionamento 
Abbiamo già visto che il [[Fondamenti dell'analisi numerica#Sistemi di equazioni lineari | numero di condizionamento]] di una matrice invertibile è definito come:
$$
K_{p(A)}:= \Vert A^{-1} \Vert_{p}\Vert A \Vert_p
$$
dove abbiamo messo in evidenza che in generale dipende dalla norma scelta.
Mostriamo alcune proprietà:
1. $K(A) \geq 1$
$$
1 = \Vert Id \Vert_{p}= \Vert A^{-1} A \Vert_{p}\leq \Vert A^{-1} \Vert_p \Vert A \Vert_p = K_p(A)
$$
2. $K(A)= K(A^{-1})$
3. $\forall z \in \mathbb{C}$ $z \neq 0$ si ha $K(zA)=K(A)$
4. Se $A$ è unitaria, $K(A)=1$.

Definiamo il numero di condizionamento di una matrice singolare $S$ come infinito: $K(S)=\infty$.

Quando usiamo la norma $p=2$, possiamo caratterizzare ulteriormente il numero di condizionamento $K_2(A)$, sfruttando la relazione:
$$
\Vert A \Vert_{2}= \sqrt{\rho(A^{T}A)}=
$$
In generale vale, per ogni norma indotta da una vettoriale, vale
$$
\rho(A) \leq \Vert A \Vert
$$
Nel caso della norma due, l'ugualgianza vale per matrici normali. In questo caso, siccome gli autovalori dell'inversa sono l'inverso degli autovalori, quindi per i moduli:
$$
K_{2}(A)= \frac{|\lambda_{max}|}{|\lambda_{min}|}
$$

Un'altra caratterizzazione del numero di condizionamento, è vederlo come l'inverso di una distanza tra le matrici singolari. Definendo una distanza:
$$
dist_{p(A)}:= \left\{ \frac{\Vert \delta A \Vert_p}{\Vert A \Vert_{p} \,:\,}A+\delta A \text{ è singolare } \right\}
$$

vale:
$$
dist_{p(A)}= \frac{1}{K_p(A)}
$$
Da questa definizione segue come corollario:
**Corollario** Se $\Vert A^{-1} \Vert \Vert \delta A \Vert < 1$ Allora $A+\delta A$ non è singolare.
Siccome vale $K_p(A)dist_p(A)=1$, e $dist_p(A)$ è un minimo sull'insieme delle matrici, quando $A+\delta A$ è  singolare si ha:
$$
1 \leq \Vert \delta A \Vert_{p}\Vert A^{-1} \Vert
$$
quindi se vale il complementare, la matrice deve essere non singolare.

## Sensibilità alle perturbazioni
A causa degli _errori di arrotondamento_ un metodo numerico impiegato per la risoluzione di un sistema lineare non fornirà una soluzione esatta del sistema di partenza, ma soltanto una soluzione approssimata che verifica un _sistema perturbato_. In altre parole, un metodo numerico genera una soluzione (esatta) $x + \delta x$ del sistema perturbato
$$
(A+\delta A)(x+\delta x) = b + \delta b
$$
vogliamo stimare $\delta x$ in funzione delle perturbazioni $\delta A$ e $\delta b$.
E' facile capire che entrerà in gioco il numero di condizionamento della matrice.

**Teorema** 
Siano $A \in \mathbb{C}^{n\times n}$ una matrice non singolare e $\delta A \in \mathbb{C}^{n\times n}$ tale che $A+\delta A$ rimane non singolare. Allora se $x \in \mathbb{C}^n$ è soluzione di $Ax=b$, con $b \neq 0$, e $\delta x$ tale che $x+\delta x$ risolve il sistema perturbato, si ha che:
$$
\frac{\Vert \delta x \Vert}{\Vert x \Vert} \leq \frac{K(A)}{1-K(A)\Vert \delta A \Vert / \Vert A \Vert} \left(\frac{\Vert \delta b \Vert}{\Vert b \Vert }+ \frac{\Vert \delta A \Vert}{\Vert A \Vert}\right)
$$
**Dim**
Dal corollario precedente segue che $\Vert A^{-1} \delta A\Vert < 1$, siccome per ipotesi $A+\delta A$ è non singolare. Quindi anche la matrice $Id + A^{-1}\delta A$ è non singolare, e valgono i bound sulla sua inversa:
$$
\Vert (I + A^{-1}\delta A )^{-1} \Vert \leq \frac{1}{1-\Vert A^{-1}\delta A\Vert} \leq \frac{1}{1-\Vert A^{-1}\Vert \Vert \delta A \Vert }
$$
ricavando $\delta x$ dal sistema si ha:
$$
\delta x = (A+\delta A)^{-1} (\delta b - \delta Ax) 
$$
Riscrivendo il primo fattore:
$$
(A+\delta A)^{-1} = (I+\delta A^{-1} A)A^{-1}
$$
e passando alle norme, ottengo:
$$
\Vert \delta x \Vert \leq \frac{\Vert A^{-1}\Vert }{1-\Vert A^{-1}\Vert \Vert \delta A \Vert }(\Vert \delta b \Vert + \Vert \delta A \Vert \Vert x \Vert)
$$

**Corollario**
Segue un corolllario utile. Assumendo di essere nelle stessi ipotesi del teorema, vale:
$$
\frac{1}{K(A)} \frac{\Vert \delta b \Vert}{\Vert b \Vert} \leq \frac{\Vert\delta x\Vert}{\Vert x\Vert} \leq K(A)  \frac{\Vert \delta b \Vert}{\Vert b \Vert}
$$
**Corollario**
Per matrici unitarie, per le quali $K(U)=1$, la perturbazione relativa sulla soluzione è proprio uguale a quella sui dati.
