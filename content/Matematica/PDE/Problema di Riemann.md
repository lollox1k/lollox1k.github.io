Problema di cauchy di una legge di conservazione con condizione iniziale costante a tratti con una discontinuità.
![[Pasted image 20220406155724.png]]
Interessante perchè compaiono fenomini come onde di shock e rarefazione.

Studiamo come si comporta [[linear advection]] con questa condizione iniziale. Ci aspettiamo come al solito che la soluzione sia la condizione iniziale che viaggia con velocità costante, spostando la discontinuità. Ma la condizione iniziale non è derivabile in un punto! _Non soddisfa la forma differenziale della legge di conservazine, ma quella integrale_:
$$
\frac{d}{dt}\int_0^L \rho(t,x)dx + a[\rho(t,L) - \rho(t,0)] = 0 
$$
testiamo la soluzione $\rho_0(x-at)$ . Assumiamo che la discontinuità si trovi in $0<x_0<L$ al tempo zero. Supponiamo inoltre che $at<L$.
$$
\frac{d}{dt}((x_0+ta)\rho_L + (L-x_0-at)\rho_R) + a[\rho_0(L-at)-\rho_0(-at)]
$$
$$
a[\rho_L -\rho_R] + a[\rho_R - \rho_L] = 0
$$
$QED$

# Modello LWR
Studiamo il modello macroscopico del traffico [[Modelli macroscopici per il traffico|LWR]] con la chiusura di Green-Shield. Il problema di Riemann associato può essere cisto come la partenza dopo un semaforo rosso: a sinistra densità costante massima, a destra nulla.
## Rarefazione
Approssiamo la condizione iniziale con una funzione per cui possiamo calcolare le caratteristiche (questo approccio fallisce con la condizione di riemann perchè abbiamo una regione vuota, non raggiunta da una caratteristica), in maniera tale che $\lim_{\epsilon \to 0} g_{\epsilon} = \rho_0$ . scegliamo:
$$
g_{\epsilon}(x) = \begin{cases} \rho_M \quad x \geq 0 \\ \rho_M(1-\frac{x}{\epsilon}) \quad 0<x<\epsilon \\ 0 \quad x \geq \epsilon\end{cases}
$$
![[Pasted image 20220406162537.png]]

Ricordiamo che la velocità con la chiusura di GS è:
$$
q'(\rho) = v_m \Big(1-\frac{2\rho}{\rho_M}\Big)
$$
Si vede che con la condizione discontinua si hanno due velocità costanti per le caratteristiche: $-v_m$ e $v_m$ per le due regioni, creando una zona non raggiunta:
![[Pasted image 20220406163119.png]]
Con la nuova condizione iniziale invece abbiamo nella zona vuota un ventaglio di caratteristiche detto _rarefaction fan_
![[Pasted image 20220406163357.png]]

## Shock
Il caso in cui la condizione iniziale è maggiore a destra (formazione di una cosa di traffico), osserviamo come la discontinuità invece si smussarsi in un'onda di rarefazione, si propaga all'indietro: abbiamo uno _shock_, che rispetta la condizione di  [[Shock and Rankine-Hugoniot theorem| Rankine-Hugoniot]].

Infatti con questa condizione iniziale le caratteristiche si intersecano, e la soluzione va intesa in senso [[Weak solutions of continuity equations|debole]]. 


