Uno _spazio metrico_ $(X,d)$ è un insieme $X$ ed una distanza $d : X\times X \mapsto [0,\infty)$. 
Vediamo le condizioni che una distanza deve rispettare:
### Definizione 
Una funzione  $d : X\times X \mapsto [0,\infty)$ si dice _distanza_ se $\forall x,\forall y,\forall z \in X$:
1. $d(x,y) = d(y,x)$ _simmetrica_
2. $d(x,y) = 0$ se e solo se $x=y$
3. $d(x,z) \leq d(x,y) + d(y,z)$ _disugualianza triangolare_

## Esempi di metriche
La _metrica euclidea_ in $\mathbb{R}^n$:
$$
d(x,y) = \sqrt{  \sum_i^n (x_i-y_i)^2  }
$$
che per $\mathbb{R}$ è semplicemente il modulo.

Data una biezione tra due insiemi, uno eredita la metrica dell'altro. Ed esempio metrica finita per $\mathbb{R}$, parto dal dominio della tangente $[-\pi/2,\pi/2]$ con metrica euclidea. Quindi per tutti i reali ottengo una _distanza finita_:
$$
d(x,y) = |\arctan(x)-\arctan(y)|
$$
$diam(\mathbb{R}) = \pi$ con questa distanza!


### Spazio metrico completo
Uno spazio metrico si dice _completo_ se tutte le [[successioni di Cauchy]] convergono ad un elemento dello spazio.