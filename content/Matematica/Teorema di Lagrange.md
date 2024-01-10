### Versione 1-dim
Sia $f : [a,b] \to \mathbb{R}$ una funzione continua e derivabile in $(a,b)$. Vale:
$$
f(b)-f(a) = f'(c)(b-a)\quad c \in (a,b)
$$
per un qualche $c$. 

#### Dim 
Si applica il teorema di Rolle ad una funzione ausiliaria $g$(faccio in modo che $g(a) = g(b)$), basta sottrarre una retta appropriata.

#### Versione n-dim
Sia $f: A \subseteq \mathbb{R}^n \to \mathbb{R}$ una funzione differenziabile. Scelti due punti $x_1,x_2 \in A$ allora:
$$
f(x_2) - f(x_1) = \nabla f(c)\cdot(x_2-x_1)
$$
Per un appropriato $c$ nel _segmento_ tra $x_1$ e $x_2$: $c = \lambda x_1 + (1-\lambda)x_2$ per qualche $\lambda \in [0,1]$. 
#### Dim 
ci riconduciamo al caso unidimensionale, sfruttando la parametruzazzione del segmento già data nella defunuzione: vediamo la funzione $f(\lambda)$, che è unidimensionale, fissando gli estremi $x_1,x_2$ prima. Applicando Lagrange 1-dim:
$$
f(1) - f(0) = f'(\overline\lambda)(1-0)
$$
quando $\lambda = 0$ siamo su $x_2$, $\lambda = 1$ su $x_1$. $f'(\overline{\lambda})$ è la derivata nella direzione ($x_2-x_1$), essendo $f$ differenziabile si può esprimere con il gradiente, ottenendo l'asserto del teorema $QED$.

## Corollario interessante 
Sia $g$ una funzione $C^2$, applichiamo Lagrange alla sua derivata $g'$:
$$
g'(y)-g'(x) = g''(z)(y-x) \qquad z \in [x,y]
$$
ora integriamo in $y$ da $x$ a $y$, usando il teorema fondamentale del calcolo integrale:
$$
g(y)-g(x) -g'(x)(y-x) = \frac{1}{2}g''(z)(y-x)^2
$$
che possiamo riscrivere come:
$$
g(y) = g(x) + g'(x)(y-x) + \frac{1}{2}g''(z)(y-x)^2
$$
Una versione al _secondo ordine_ di Lagrange.

Si estende ugualmente a più dimensioni, considerando la funzione $g(\lambda) := f(\lambda y + (1-\lambda)x)$ compare l'Hessiano:
$$
f(y) = f(x) + \nabla f(x)(y-x) + \frac{1}{2}(y-x)^T H(z)(y-x)
$$

con $z$ nel segmento tra $y$ e $x$ come per Lagrange n-Dim.

Non è altro che una generalizzazione di Lagrange ad ogni ordine, è il _resto di Lagrange_ della serie di Taylor.
