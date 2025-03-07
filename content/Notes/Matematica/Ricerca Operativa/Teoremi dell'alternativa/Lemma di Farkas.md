# Lemma di Farkas
Il sistema:
$$
Ax=b, \quad x \geq 0
$$
ammette soluzione se e solo se il sistema
$$
y^TA \geq 0, \quad y^Tb < 0
$$
è inammissibile.
### Dim 
Riscriviamo il sistema di partenza per applicare il [[Teorema di Gale]].
$$
\begin{cases} Ax=b\\x\geq0\end{cases} \iff \begin{cases}Ax \leq b\\ -Ax\leq -b\\ -x \leq 0\end{cases}
$$
Combiniamo tutto in una matrice ed usiamo Gale:
$$
y^T\begin{pmatrix} A\\-A\\-I\end{pmatrix} = 0, \qquad y^T\begin{pmatrix}b\\-b\\0\end{pmatrix} < 0, \qquad y\geq0
$$
scriviamo il vettore $y^T =(u^T,v^T,w^T)$, analizziamoli separatamente
$$
u^TA-v^TA-w= 0,\qquad u^Tb-v^Tb < 0, \qquad u,v,w\geq0
$$
introduciamo il vettore $z := u-v$, e notando che $w\geq 0$ otteniamo:
$$
z^TA \geq 0, \qquad z^Tb < 0
$$
le restrizioni sul segno sono sparite, ecco dimstrato il lemma di Farkas. $\square$

### Corollario
In maniera praticamente analoga si dimostra il seguente corollario, che serve per ottenere le [[Condizioni di ottimalità Duali KKT]] a partire dalle condizioni di ottimalità vincolata primali.
Il Sistema
$$
B\lambda + C\mu = g, \qquad \lambda \geq 0
$$
ammette soluzioni se e solo se il sistema
$$
\begin{cases}B^Td \leq 0\\ C^Td = 0 \\g^Td > 0\end{cases}
$$
non ammette soluzioni.

#### Dim 
Riscriviamo il primo sistema ed applichiamo Gale:
$$
\begin{pmatrix}B \quad C\\ -B \quad -C   \\ -I \quad 0\end{pmatrix} \begin{pmatrix}\lambda \\ \mu\end{pmatrix} \leq \begin{pmatrix} g \\ -g \\ 0\end{pmatrix} 
$$
si ha il sistema opposto:
$$
y^T\begin{pmatrix}B \quad C\\ -B \quad -C   \\ -I \quad 0\end{pmatrix} = 0, \qquad y^T\begin{pmatrix} g \\ -g \\ 0\end{pmatrix} < 0 
$$
riscriviamo il vettore $y^T = (u^T, v^T,w^T)$ 
$$
u^TB - v^TB-w^T = 0, \quad u^TC - v^TC = 0, \qquad u^Tg - v^Tg < 0
$$
introducendo il vettore $d = u-v$, che non ha più restrizioni di segno ed eliminando il vettore positivo $w$ otteniamo:
$$
\begin{cases}
d^TB \geq 0\\
d^TC = 0\\
d^Tg < 0
\end{cases}
$$
moltiplicando per $-1$, e passando alle trasposte ottengo il secondo sistema della tesi. $\square$
