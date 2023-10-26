# Diminiscing step size
Si fanno due richieste ragionevoli:
$$
\alpha^k \to 0 \qquad \sum_k \alpha^k = +\infty
$$
quindi una successione infinitesima non sommabile, ad esempio $\frac1k$, l'idea è di consentire al metodo di arrivare ovunque. Infatti la seconda condizione garantisce che non converge ad un punto non stazionario:
Sia $x^k \to \overline x$, allora scelti $m>n$ abbastanza grandi:
$$
|x^m-\overline x| < \epsilon \qquad |x^n-\overline x| < \epsilon
$$
il che implica
$$
|x^n - x^m| < 2\epsilon
$$
ma la distanza è pari a:
$$
|x^m-x^n| = \Big\vert \sum_{k=n}^{m-1} \alpha^k (-\nabla f(x^k))\Big\vert \approx \sum_{k=n}^{m-1} \alpha^k (-\nabla f(\overline x)) \quad \square
$$
che diverge se il gradiente non si annulla.


## Convergenza
Richiediamo che il gradiente di $f$ sia L-continuo, ed inoltre due limiti per la direzione:
$$
c_1\Vert \nabla f(x^k)\Vert^2 \leq -\nabla f(x^k)^Td^k
$$
$$
\Vert d^k \Vert^2 \leq c_2 \Vert\nabla f(x^k)\Vert^2
$$
con $c_1,c_2>0$, sia $x^k \to \overline x$. Allora $\nabla f(\overline x) = 0$. 
### Dim 
Usiamo il [[Descent Lemma]], otteniamo:
$$
f(x^k)-f(x^{k+1})\leq \alpha^k\nabla f(x^k)^Td^k +\frac{L{\alpha^k}^2}{2}\Vert d^k\Vert^2
$$
usando i bound sulla direzione otteniamo:
$$
f(x^k)-f(x^{k+1})\leq \alpha^k\left[ \frac{L}{2}c_2\Vert \nabla f(x^k)\Vert-c_1\Vert \nabla f(x^k)\Vert^2 \right]
$$
siccome $\alpha^k \to 0$, il termine quadratico diventa trascurabile per $k$ abbastanza grande:
$$
f(x^k)-f(x^{k+1})\leq -\alpha^kc_1\Vert\nabla f(x^k)\Vert^2 \qquad \forall k \geq \overline k
$$
sommando queste disequazioni a partire da $\overline k$ ottengo (si cancellano i termini in mezzo):
$$
c_1\sum_{k=\overline k}^\infty\alpha^k\Vert \nabla f(x^k)\Vert^2 \leq \lim_{k\to\infty}f(x^k)-f(x^{\overline k})
$$
siccome la disuguaglianza precedente ci assicura che la successione è definitivamente monotona, o diverge a $-\infty$ o ad un punto $\overline x$. In questo caso il termine di destra è limitato, di conseguenza la serie a sinistra è convergente:
$$
\sum_{k=\overline k}^\infty \alpha^k \Vert \nabla f(x^k)\Vert^2 < +\infty
$$
ma questo implica $\Vert \nabla f(x^k)\Vert \to 0$, siccome $\sum_k \alpha^k = +\infty$. $\square$

