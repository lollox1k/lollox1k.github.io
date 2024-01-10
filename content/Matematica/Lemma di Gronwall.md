## Lemma di Gronwall
Sia $\phi(t)$ una funzione continua tale che:
$$
|\phi(t)| \leq c + L\int_{t_0}^t |\phi(s)|ds \qquad \forall t \geq t_0
$$
con le costanti $c,L \in [0,\infty)$. Allora vale la stima:
$$
|\phi(t)| \leq ce^{L(t-t_0)} \qquad \forall t \geq t_0
$$
#### Dim
definiamo la funzione integrale:
$$
\Phi(t) := \int_{t_0}^t |\phi(s)|ds
$$
essendo $\phi$ continua, $\Phi$ è derivabile e per ipotesi la sua derivata è maggiorata da:
$$
\Phi'(t) = |\phi(t)| \leq c + L \Phi(t)
$$
moltiplicando per $e^{-L(t-t_0)}$:
$$
\Phi'(t)e^{-L(t-t_0)} - L\Phi(t)e^{-L(t-t_0)} \leq c e^{-L(t-t_0)}
$$
si risconosce a sinistra la derivata del prodotto:
$$
(\Phi(t)e^{-L(t-t_0)})' \leq ce^{-L(t-t_0)}
$$
Integrando tra $[t_0,t]$ si ottiene un upper bound per $\Phi(t)$:
$$
\Phi(t)e^{-L(t-t_0)} \leq \frac{c}{L}(1-e^{-L(t-t_0)})
$$
dove abbiamo usato il fatto che $\Phi(t_0) = 0$. Dividiamo per il fattore esponenziale ed otteniamo:
$$
\Phi(t) \leq \frac{c}{L}(e^{L(t-t_0)-1})
$$
ora usiamo questa stima nella disuguaglianza di ipotesi:
$$
|\phi(t)| \leq c + L\Phi(t) \leq c + c(e^{L(t-t_0)}-1) = ce^{L(t-t_0)}  
$$
$QED$


### Usi della disuguaglianza
1. Ad esempio _stimare la differenza di due soluzioni di un Problema di Cauchy date due condizioni iniziali_, infatti:
$$
|u(t)-v(t)|= \Big| u_0-v_0 + \int_{t_0}^t f(s,u)-f(s,v) ds\Big| \leq |u_0-v_0| + \Big | \int_{t_0}^t f(s,u)-f(s,v) ds \Big |
$$
sia $L$ la costante di Lipshitz della $f$:
$$
|u(t)-v(t)|\leq |u_0-v_0| + L\int_{t_0}^t |u(s)-v(s)|ds
$$
usando il lemma di Gronwall:
$$
|u(t)-v(t)| \leq |u_0-v_0|e^{L(t-t_0)}
$$
più passa il tempo più la stima sulla differenza aumenta (come ci si aspettava). Dipende linearmente dalla condizione iniziale, esponenzialmente dal tempo e dalla costante di $L$.

2. _unicità globale delle soluzioni di un problema di Cauchy_ [[Teorema di Picard–Lindelöf]]