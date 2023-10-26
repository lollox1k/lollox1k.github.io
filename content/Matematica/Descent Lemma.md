# Descent lemma
Un risultato elementare, che pone un bound su una funzione L-continua con una funzione quadratica, col termine quadratico che dipende dalla costante di Lipshitz.
## Lemma 
Sia $f : \mathbb{R}^n \to \mathbb{R}$ una funzione $L$-continua, ovvero esiste $L > 0$ tale che:
$$
\Vert \nabla f(y)-\nabla f(x)\Vert \leq L \Vert y-x\Vert, \qquad \forall x,y \in \mathbb{R}^n
$$
Allora vale il bound:
$$
f(y)\leq f(x) + \nabla f(x)^T(y-x)+\frac{L}{2}\Vert y-x \Vert^2
$$
### Dim 
Definiamo la funzione scalare $g(t) := f(ty + (1-t)x)$, si vede che $g(0)=f(x)$ e $g(1)=f(y)$. Siccome è differenziabile, vale il teorema fondamentale del calcolo:
$$
f(y)-f(x)=g(1)-g(0)=\int_0^1 g(t)'dt
$$
esplicitando la derivata otteniamo:
$$
\int_0^1 \nabla f(ty - (t-1)x)^T(y-x)dt
$$
ora vogliamo poter usare la $L$-continuità, sommiamo e sottraiamo $\nabla f(x)$:
$$
\nabla f(x)^T(y-x)+\int_0^1 [\nabla f(x+t(y-x)) -\nabla f(x)]^T(y-x)dt
$$
passiamo ai moduli, usiamo Cauchy-Swartz per ottenere l'upper bound:
$$
\leq \nabla f(x)^T(y-x) +L\int_0^1 t\Vert y-x \Vert^2 dt =  \leq \nabla f(x)^T(y-x) + \frac{L}{2}\Vert y-x \Vert^2
$$
ottenendo la tesi. $\square$
