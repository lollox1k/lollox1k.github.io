Consideriamo l'equazione
$$
u_t + f(u)_x = 0
$$
con $f(u)$ non lineare.
### Caso lineare
Abbiamo studiato il caso di [[linear advection]] in cui $f(u) = au$. Per questo caso gli schemi alle differenze centrate sono incondizionamente instabili [[Finite difference]] (derivata approssimata al secondo ordine), abbiamo pertanto usato il metodo upwind [[Finite volumes]], afflitto però da diffusione numerica ;(.
#### Problema del caso non lineare
Per equazioni non lineari, non è possibile a priori scegliere il verso (upwind/downwind), perchè la velocità non è costante! _La velocità cambia segno nello spazio_.

Ripercorrendo le idee in [[Finite volumes]], definiamo la media di cella, regolata dalla ODE:
$$
\frac{d}{dt}<u_i(t)> = -\frac{1}{\Delta x} [f(u(t,x_i+\Delta x/2))-f(t,u_i - \Delta x/2)]
$$
Ed approssiamo il valore della funzione nei bordi della cella con la media di cella. Per il caso lineare scelgo quale celle in base al segno della velocità. _Come faccio per il caso non lineare?_

Definiamo un flusso numerico:
$$
F_{i+\Delta x/2}(t) = f(u(t,x_i + \Delta x/2))
$$
Ad ogni interfaccia sto risolvendo un [[Problema di Riemann]]!

Risolvo esattamente i problemi di Riemann per capire quale flusso numerico considerare.
