$$
D = Tk_B \mu
$$
Il coefficiente di diffusione ([[Diffusione Fick's Law]]) è legato alla _mobilità_ $\mu$, ovvero il rapporto tra la forza agente e la velocità terminale e la temperatura.

#### Dim 
All'equilibrio la somma tra le densità di corrente di diffusione e di drift (dovuto ad una forza) è nulla:
$$
\vec J_{diff} + \vec J_{drift} = \vec 0
$$
La corrente di drift, come è solito essendo una densità di corrente $\vec J \simeq \rho \vec v$, ma sappiamo che la velocità dipende linearmente dalla forza esterna tramite la mobilità:
$$
\vec J_{drift} = \rho \mu \vec F 
$$
Per la diffusione sappiamo dalla [[Diffusione Fick's Law]] che:
$$
\vec J_{diff} = -D \nabla \rho
$$
quindi l'equazione è:
$$
-D\nabla \rho + \mu \vec F\rho = 0
$$
Serve esplicitamente la forza $\vec F(x)$ per trovare $\rho$, tuttavia se la forza è conservativa $F = -\nabla U$, e sapendo dalla [[statistica maxwell-boltzmann]] che la densità dipende solo dal potenziale:

$$
D\nabla \rho + \mu \nabla U\rho = 0
$$
$\rho(U)$ quindi:
$$
\nabla \rho = \frac{\partial \rho}{\partial U} \nabla U
$$
quindi l'equazione vettoriale 
$$
D \frac{\partial \rho}{\partial U} \nabla U + \mu \rho\nabla U  = 0
$$
impone l'equazione scalare (eliminando le componenti del gradiente di $U$):
$$
D \frac{\partial \rho}{\partial U} + \mu \rho = 0
$$
Sempre dalla statistica di MB sappiamo la forma di $\rho$:
$$
\rho(x) = \frac{1}{Z_q} e^{-\beta U(x)}
$$
(la normalizzazione $Z_q$ non è rilevante). Quindi calcolando la derivata e sostituendo:
$$
D = \frac{\mu}{\beta} = k_B T \mu \qquad \square
$$
