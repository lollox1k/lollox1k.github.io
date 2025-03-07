# Metodo di Newton
Uno dei [[Gradient Methods]], che sotto opportune condizioni converge molto velocemente alla soluzione. 
Si può applicare sia alla ricerca di zeri di funzioni, e quindi anche a punti stazionari.

Sia $f : \mathbb{R}^n \to \mathbb{R}^m$ e continuamente differenziabile.
Il metodo nella sua forma pura ($\alpha^k = 1$ ) per la ricerca di radici è:
$$
x^{k+1}=x^k-[\nabla f(x^k)]^{-1}f(x^k)
$$
quindi è la _scelta della direzione_ $d^k = -[\nabla f(x^k)]^{-1}f(x^k)$.

Un risultato semplice è la _convergenza superlineare_, basta sviluppare con taylor al prim'ordine attorno al punto $x^*$ in cui vale $f(x^*)=0$.

In generale non è detto che converga. Vediamo delle condizioni sufficienti che garantiscono la convergenza e la velocità.

## Teorema
Sia $g : \mathbb{R}^n \to \mathbb{R}^n$ e $x^* \in \mathbb{R}^n$ tale che $g(x^*)=0$. Per un certo $\delta > 0$ si assuma che nella palla $B_\delta(x^*)$ $g \in C^1$ e lo Jacobiano $\nabla g(x)$ sia invertibile. Allora:
1. Esiste un $\delta > 0$ tale che se $x^0 \in S_\delta$, la sequenza $\{x^k\}$ generata dall'iterazione:
$$
x^{k+1} = x^k - [\nabla g(x^k)]^{-1}g(x^k)
$$
è ben definita, è contenuta in $S_\delta$, converge a $x^*$, e converge superlinearmente.
2. Se inoltre valgono i bound in ogni $x,y \in S_\delta$
$$
\Vert \nabla g(y)-\nabla g(x)\Vert \leq L \Vert y-x \Vert, \qquad L > 0
$$
$$
\Vert [\nabla g(x)]^{-1}\Vert \leq M, \qquad M > 0
$$
Allora, se $x^0 \in S_\delta$, abbiamo
$$
\Vert x^{k+1}-x^*\Vert \leq \frac{LM}{2}\Vert x^k-x^*\Vert^2
$$
quindi se $\frac{LM\delta}{2} < 1$ converge quadraticamente.
#### Dim 
Sia $\delta > 0$ tale che $\nabla g(x)^{-1}$ esista, sia $M>0$ tal che 
$$
\Vert \nabla g(x)^{-1}\Vert \leq M, \qquad \forall x \in S_\delta
$$
Sfruttiamo la relazione:
$$
\frac{d}{dt}g(tx^k + (1-t)x^*) = \nabla g(tx^k+(1-t)x^*)(x^k-x^*)
$$
quindi integrando rispetto a $t$:
$$
\int_0^1 \nabla g(tx^k+(1-t)x^*)(x^k-x^*)dt = g(x^k)-g(x^*)=g(x^k)
$$
usiamo questa equivalenza per stimare la differenza
$$
\Vert x^{k+1}-x^*\Vert = \Vert x^k - [\nabla g(x^k)]^{-1}g(x^k)\Vert = \left\Vert  [\nabla g(x^k)]^{-1}\left( \nabla g(x^k)(x^k-x^*) -g(x^k)\right)\right\Vert
$$
$$
= \left\Vert [\nabla g(x^k)]^{-1}\left( \nabla g(x^k)-\int_0^1 \nabla g(tx^k+(1-t)x^*)dt\right)(x^k-x^*) \right\Vert
$$
posso ora maggiorare
$$
\leq M  \int_0^1  \left\Vert\nabla g(x^k)- \nabla g(tx^k+(1-t)x^*)\right\Vert dt \Vert x^k - x^*\Vert
$$
dalla continuità di $\nabla g$, segue che possiamo prendere $\delta$ abbastanza piccola da rendere il termine nell'integrale piccolo a piacere, rendendolo minore di $\frac{1}{M}$ otteniamo la convergenza di $x^k \to x^*$ per induzione (anche la sua superlinearità).

Con l'ulteriore bound tramite $L$ possiamo maggiorare l'integrando ed ottenere:
$$
\leq M \int_0^1 Lt\Vert x^k-x^*\Vert dt \Vert x^k-x^*\Vert = \frac{ML}{2}\Vert x^k-x^*\Vert^2
$$
ottenendo la convergenza quadratica per $\delta$ abbastanza piccoli.

![[Pasted image 20220628220006.png]]

## Newton-like methods
Abbiamo dimostrato che se siamo abbastanza vicini alla soluzione, il metodo di Newton converge molto velocemente, ma in generale non sempre possiamo garantire che valgano le ipotesi. Vediamo una famiglia di metodi _ibridi_, ovvero che al limite tendono a Newton.

### Teorema 
Supponiamo che $f \in C^2$,  consideriamo la successione $x^{k+1}=x^k+\alpha^kd^k$, e supponiamo che:
$$
x^k \to x^*, \quad \nabla f(x^*)=0, \quad \nabla^2 f(x^*) \text{ def  positiva}, \quad \nabla f(x^k)\neq 0\; \forall k
$$
e che al limite valga:
$$
\lim_{k\to\infty} \frac{\Vert d^k+[\nabla^2 f(x^k)]^{-1}\nabla f(x^k) \Vert}{\Vert \nabla f(x^k)\Vert} = 0
$$
Allora se $\alpha^k$ è scelto con la [[Armijo rule]] con $s=1$ e $\sigma < 1/2$ si ha convergenza superlineare.
Inoltre per un $k$ abbastanza grande non si ha più riduzione di step, ovvero si passa a Newton puro.

### Dim 

