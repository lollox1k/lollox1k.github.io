# Teoremi sulla convergenza uniforme
Assumiamo che la successioni di funzioni $f_n \to f$ converga puntualmente.
In quali casi riesco a dimostrare la convergenza uniforme $f_n \rightrightarrows f$ ?

### Lipshitz continuità

Sia $f_n \to f$.  Inoltre, siano $f_n$ _lipshitz continute_ su un _compatto_ $I$:
$$
	\forall x,y \in I \qquad \vert f_n(y)-f_n(x)\vert \leq C \vert y-x \vert
$$
per ogni $n$, con $C > 0$.

Allora $f_n \rightrightarrows f$ su $I$.
### Dim
Consideriamo un ricoprimento finito del compatto $I$. Partendo dall'unione di tutte le palle di un certo raggio $\delta$, prendiamo un sottoricoprimento finito Quindi $I = \cup_i^M B_\delta(x_i)$. Siccome abbiamo convergenza puntuale, per ogni punto $x_i$ centri delle palle, vale:
$$
	\vert f_n(x_i)-f_m(x_i)\vert < \epsilon \qquad \forall n,m \geq N_i
$$
Siccome è un _insieme finito_ è sicuramente ben definito il massimo:
$$
N := \max_{i \in [1,\dots,M]} \{N_1,\dots,N_M\}
$$
quindi
$$
\vert f_n(x)-f_m(x)\vert \leq \vert f_n(x) -f_n(x_i)\vert + \vert f_n(x_i)-f_m(x_i) \vert + \vert  f_m(x_i) - f_m(x) \vert < 3\epsilon
$$
infatti per la lipshitz continuità:
$$
\vert f_n(x) -f_n(x_i)\vert \leq C \vert x-x_i\vert
$$
basta scegliere il raggio delle palle iniziali 
$$
\delta = \frac{\epsilon}{C}
$$
il secondo pezzo segue per la convergenza puntuale quando $n,m \geq N$.
Quindi è una successione di Cauchy, ed essendo lo spazio delle funzioni continue $C[a,b]$ completo, esiste il limite ed è continuo, e la convergenza è uniforme. $\square$
