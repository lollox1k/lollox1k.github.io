## Classificazione delle PDE
- _ordine_: il grado della derivata maggiore
$$
\partial_{xx}u + \partial_t u = 0 \qquad \text{grado 2}
$$
- _lineari_: combinazione lineare delle derivate (e funzione stessa)
$$
\alpha\partial_x u + \beta \partial_t u = 0
$$
- _semi-lineari_: i coefficienti della combinazione lineare sono funzioni delle variabili indipendenti (non della soluzione stessa)
$$
f(t,x)\partial_t u(t,x) + g(t,x)\partial_x u = 0
$$
- _quasi -lineari_: se le derivate di grado maggiore hanno coefficienti che possono dipendere dalla funzione stessa $u$ e dalle derivate di grado inferiore
$$
\partial_t u + f(t,x,u)\partial_x u = 0
$$
- _non-lineari_: RUN 
- _omogenea_: se non compaiono termini indipendenti da $u$ (termini di sorgente)