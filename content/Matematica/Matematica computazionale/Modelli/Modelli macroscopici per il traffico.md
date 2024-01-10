Consideriamo una corsia unidimensionale, senza incroci. Essendo un [[Modelli macroscopici]][[Scale di osservazione]] le variabili indipendenti sono $(x,t)$.

Vogliamo derivare il modello macroscopico, quindi PDEs per il traffico partendo da prinicipi fisici. Sia $\rho(t,x)$ la densità. Il numero dei veicoli (massa) sarà:
$$
N(t)_{[x1,x2]} = \int_{x_1}^{x_2} \rho(x,t) dx
$$
Deve valere la conservazione della massa, i veicoli non scompaiono: la variazione della massa dipende da quanti entrano ed escono nei rispettivi bordi $x_1$ e $x_2$.
Il flusso è:
$$
q(t,x) = v(t,x)\rho(t,x)
$$
arriviamo ad un' equazione di continuità:
$$
\frac{\partial \rho(t,x)}{\partial t} + \frac{\partial \rho(x,t)v(x,t)}{\partial x} = 0
$$
