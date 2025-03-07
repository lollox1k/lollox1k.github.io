Sia $\Phi$ un [[Metodi numerici|metodo numerico]] di integrazione. Il suo errore di _tronacamento_ nel punto (x,y) è definito come la differenza tra l'incremento approssimato con quello vero:
$$
T(x,y;h) := \frac{1}{h}[y_{n+1} - u(x+h)]
$$
dove $y_{n+1}$ è calcolato col metodo, $u(x+h)$ il valore analitico corretto, ovvero la funzione che risolve l'equazione differenziale con condizione iniziale $(x,y)$, quindi $u(x) = y$.
Possiamo riscrivere $y_{n+1}$ per metodi ad uno step:
$$
y_{n+1} = y + h\Phi(x,y;h)
$$
quindi l'errore di trocamento diventa:
$$
T(x,y;h) = \frac{u(x)}{h} + \Phi(x,y;h) -\frac{u(x+h)}{h} = \Phi(x,y;h) -\frac{1}{h}[u(x+h)-u(x)]
$$
che mostra chiaramente che è la differenza tra l'incremento per step approssimato con quello analitico.

