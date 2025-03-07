

Vediamo [[Numerical PDE|metodo numerico]] ai volumi finiti: discretizziamo lo spazio in cellette, invece che punti studiamo l'evoluzione temporale dei valori medi di cella. Alla fine si arriva ad un metodo equivalente a quello delle differenze finito al prim'ordine. Vedremo due scelte, upwind e downwind per la derivata.

Definiamo la media spaziale di ogni cella
$$
<u_i(t)> := \frac{1}{\Delta x} \int_{x_i-\Delta x/2}^{x_i + \Delta x/2} u(t,x)dx
$$
derivo per il tempo ed uso la relazione tra le derivate di [[linear advection]].

$$
\frac{d}{dt}<u_i(t)> = -\frac{a}{\Delta x}[u(t,x_i+\Delta x/2)-u(t,x_i - \Delta x/2)]
$$
Fin qui nessuna approssimazione. Supponiamo ora che il valore ai bordi delle celle, quello che compare a destra, sia ben approssimabile dalla media di cella, la domanda ora è da quale delle due celle? posso fare due scelte, _upwind_ e _downwind_. Una delle due è stabile! Bel rabionamento fisico sulla propagazione delle informazioni, la scelta dipende dalla _direzione della velocità_. Siamo fortnuati, in linear advection è una costante.

- diffusione numerica
- CLF
- energia per stabilità
- Rusanov Flux?
