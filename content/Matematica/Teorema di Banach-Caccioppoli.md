Teorema del punto fisso per contrazioni in spazi metrici.

## Definizione
Sia $(X,d)$ uno [[Spazio metrico]], e $\phi : X \mapsto X$ una funzione viene detta _contrazione_ se esiste una costante $L \in [0,1)$ tale che $\forall x,y \in X$
$$
Ld(\phi(x), \phi(y)) \leq d(x,y)
$$
Quindi $\phi$ _contrae_ nel senso che accorcia le distanze.

## Teorema
Sia $(X,d)$ uno spazio metrico non vuoto, completo e $\phi$ una contrazione su di esso.
Definiamo la successione per ricorsione:
1. $y_0 = x$
2. $y_{n+1} = \phi(y_n)$
dove $x$ è un punto di $X$ arbitrario  (possiamo perchè è non vuoto).

Valgono i seguenti fatti:
1. la successione converge $\lim_{n\to\infty}y_n = y$
2. il limite è unico 
3. $y$ è un punto fisso della contrazione: $\phi(y) = y$

## Dim
Facciamo vedere che è una successione di Cauchy, pertanto dalla completezza dello spazio metrico converge ad un elemento dello spazio stesso. La distanza tra due elementi consecutivi della successione è:
$$
d(y_n, y_{n+1}) = d(\phi(y_{n-1}), \phi(y_{n-2})) \leq Ld(y_{n-1}, y_{n-2}) = \dots \leq L^nd(x_0,x_1)
$$
e dato che $L \in [0,1)$ la distanza va a zero nel limite. Ma dobbiamo far vedere che la serie è di Cauchy. Ma il nostro bound implica quello affinchè la seria sia di Cauchy, basta usare la disuguaglianza triangolare. 
Siano $m,n \in \mathbb{N}$ e $n<m$. 
$$
d(y_n,y_m) \leq d(y_n,y_{n+1}) + \dots d(y_{m-1}, y_m) 
$$
Possiamo maggiorare ogni termine con il risultato precedente.
$$
\leq d(x_0,x_1)\sum_{i=n}^m L^i = d(x_0,x_1)\sum_{i=0}^{m-n-1}L^{i+n} = d(x_0,x_i)L^n \sum_{i=0}^{m-n-1}L^i
$$
Qust'ultima è una serie geometrica e vale:
$$
\sum_{i=0}^{n-m-1}L^i = \frac{1-L^{n-m}}{1-L} \leq \frac{1}{1-L}
$$
quindi nel limite $n\to\infty$:
$$
\lim_{n\to\infty} d(x_0,x_i)\frac{L^n}{1-L} = 0
$$
quindi la serie è di Cauchy.

Facciamo vedere che $y$ è un punto fisso di $\phi$. Per continuità:
$$
\phi(y) = \lim_{n\to\infty} \phi(y_n) = \lim_{n\to\infty} y_n = y 
$$

Dimostriamo l'unicità per assurdo: siano $x,y \in X$ entrambi punti limite della sucessione. Calcoliamo la loro distanza, e sfruttiamo che sono entrambi punti fissi:
$$
d(x,y) = d(\phi(x), \phi(y)) \leq L d(x,y)
$$
Siccome $x\neq y$ $d(x,y) > 0$. Dividendo da entrambe le parti si ottiene l'assurdo:
$$
1 \leq L
$$
ma per ipotesi $L\in [0,1)$. $QED$
