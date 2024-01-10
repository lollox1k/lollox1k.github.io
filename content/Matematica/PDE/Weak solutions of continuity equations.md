Consideriamo l'equazione di continuità
$$
u_t + q(u)_x = 0
$$
supponiamo $q$ funzione smooth. 

Vediamo in che senso esistono soluzioni deboli di questa equazione, scaricando le derivate da $u$ ad una funzione test [[Weak deriative]].

Integriamo le due derivate con un funzione test $\psi \in C^{\infty}_{cpt}([0,\infty)\times \mathbb{R})$ , sciagliamo come domain temporale $(0,\infty)$ e spaziale tutta la retta $\mathbb{R}$.
$$
\int_0^\infty u_t \psi dt = -u\psi(0,x)-\int_0^\infty u \psi_t dt
$$
Avendo scelto il tempo iniziale $t=0$ è comparso un termine di bordo.
Per la parte spaziale:
$$
\int_{-\infty}^\infty q_x\psi dx = -\int_{-\infty}^\infty q \psi_x dx
$$
Abbiamo i pezzi per ricostruire l'equazione di continuità, integriamo la parte spaziale per il tempo e viceversa, sommiamo:
$$
\int_0^\infty \int_{-\infty}^\infty \Big[ u_t + q_x\Big]\psi dxdt = -\int_0^\infty \int_{-\infty}^\infty \Big[ u\psi_t + q\psi_x \Big]dxdt - \int_{-\infty}^\infty u\psi(0,x)dx
$$
Quindi: Se $u$ è soluzione classica dell'equazione, allora deve valere:
$$
\int_0^\infty \int_{-\infty}^\infty \Big[ u\psi_t + q\psi_x \Big]dxdt + \int_{-\infty}^\infty u\psi(0,x)dx = 0
$$
Ma in questa equazione non compaiono derivate di $u$. E' naturale _definire soluzioni deboli come le $u \in L^1_{loc}$ che soddisfano questa equazione per ogni funzione test $\psi$_.

Si può verificare come le soluzioni discontinue sia soluzioni deboli.

