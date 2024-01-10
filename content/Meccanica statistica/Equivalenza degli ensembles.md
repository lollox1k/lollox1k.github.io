# Equivalenza degli ensemble
## Equivalenza microcanonico-canonico
Dimostriamo l'equivalenza della termodinamica ottenuta dall' [[Ensemble canonico]] e [[Ensemble microcanonico]].

Abbiamo visto che entrambi gli ensemble rispettano l'ortodicità, definiscono quindi una funzione entropia.  Ci aspettiamo quindi che nel limite termodinamico definiscono la stessa termodinamica, i.e. le stesse relazioni macroscopiche che legano le quantità $p,v,u,T,s$.

Dimostreremo che l'equivalenza vale "in generale" per ogni sistema, nel limite termodinamico a patto di scegliere lo stesso valore per la costante $k_B$ (che a priori non è uguale nei due ensemble!).

Lo stratagemma che usiamo è dovuto a Boltzmann e Gibbs. Definiamo:
$$
\Sigma(U,V)=\int_{\mathcal{H}(p,q)\leq U} \frac{dpdq}{N!h^{3N}}
$$
$$
Z(\beta,V)=\int e^{-\beta\mathcal{H}(p,q)}\frac{dpdq}{N!h^{3N}}
$$
le due funzioni di partizione sono legate, $Z$ è una sorta di trasformata di Laplace:
#### Claim
$$
Z(\beta,V)=\beta\int_{U_{min}}^\infty \Sigma(E,V)e^{-\beta E}dE
$$
#### Dim
Integro per parti:
$$
-\Sigma(E,V)e^{-\beta E}\vert_{U_{min}}^\infty +\int e^{-\beta E} \frac{\partial \Sigma}{\partial E}dE
$$
ma
$$
\frac{\partial \Sigma}{\partial E}= \Omega(E,V)
$$
si usa il fatto che la derivata della theta è la delta. 
$$
Z(\beta,V)= \Sigma(U_{min},V)e^{-\beta U_{min}} + \int e^{-\beta \mathcal{H}(p,q)}\frac{dpdq}{N!h^{3N}}
$$
il primo termine è trascurabile. $\square$

Da questa equivalenza segue che l'energia libera:
$$
F(\beta,V)=-\beta^{-1}\log Z(\beta,V)= -\beta^{-1}\log \beta-\beta^{-1}\log \int_{U_{min}}^\infty e^{-\beta E}\Sigma(E,V)dE
$$
Le quantità termodinamiche che si ricavano dall'enseble canonico sono:

- $f_c(\beta,v)=\lim_{N\to\infty}\frac{1}{N}F(\beta,V)$
- $u_c(\beta,v)=\frac{\partial f_c}{\partial \beta}$
- $T_c = \frac{1}{k_B\beta}$
- $p_c = \lim_{N\to\infty} P(\mu) = -\frac{\partial f_c}{\partial V}$
- $s_c = \frac{u_c-f_c}{T_c}$

>> Si assume senza problemi di scambiare i limiti con le derivate

Le stesse quantità  nel microcanonico sono:
- $f_m(u_m,v_m)=u_m-T_ms_m$
- $u_m = \frac{U}{N}$
- $T_m = \left( \frac{\partial s_m}{\partial u_m} \right)^{-1}$
- $p_m = T_m\frac{\partial s_m}{\partial v_m}$
- $s_m = \lim_{N\to\infty}\frac{k_B}{N}\log \Sigma(U,V)$

L'equivalenza di tutte queste quantità diventa:
Se stabiliamo una corrisponenda tra i parametri del canonico $\beta = 1/k_BT_c$, $v=v_c$ con quelli del microcanonico $u = u_m$, $v=v_m$, nella seguente maniera:
$$
T_c = \frac{1}{k_B\beta} = \left( \frac{\partial s_m}{\partial u_m} \right)^{-1}= T_m, \qquad v_c = v_m
$$
_Allora tutte le altre quantità coincidono_ (a patto di fissare $k_B$)
### Giustificazione euristica
Nel limite $N\to\infty$ possiamo usare l'approssimazione di di picco:
$$
Z(\beta,V)=\beta\int_{U_{min}}^\infty e^{S(E,V)}e^{-\beta E}dE \simeq CN^{1/2} \exp\left( N\max_{u} -\beta u + \frac{1}{k_B}s_m(u,v_m) \right)
$$
 supponendo che il massimo esista e sia unico in un dato valore $u_0$. Siccome la derivata è nulla segue che $u_0$ soddisfa:
$$
\beta = \frac{1}{k_B}\frac{\partial s_m}{\partial u}(u_0,v_m)
$$
inoltre:
$$
u_c = \frac{U(\mu)}{N}= \frac{\int e^{-\beta E} (E/N) \Sigma(E,V)dE }{\int e^{-\beta E}\Sigma(E,V)dE} \to u_0
$$
perchè nel limite $N\to\infty$ solo i valori $u\simeq u_0$ contano. Quindi $u_c = u_0$ nel limite termodinamico. Per far vedere come coincida con l'energia del microcanonico, sfruttiamo la relazione precedente e la definizione di temperatura nel microcanonico:
$$
\beta = \frac{1}{k_B}\frac{\partial s_m}{\partial u}(u_0,v_m)= \frac{1}{k_B}\frac{\partial s_m}{\partial u}(u_c,v_m)=\frac{1}{k_B}T_m(u_c,v_m)^{-1}
$$
quindi con l'identificazione $v_m = v_c$ otteniamo che $u_c = u_m$.

Rimane da far vedere $f_c = f_m$. Sfruttiamo sempre il ragionamento sul massimo:
$$
f_c(\beta,v_m)= -\beta^{-1} \max_{u}\left( -\beta u + s_m(u,v_m)/k_B \right)
$$
ma il massimo abbiamo supposto essere $u_0 = u_c = u_m$
$$
= u_m -\beta^{-1}s_m(u_m,v_m)/k_B = u_m -T_c s_m(u_m,v_m)
$$
usando l'identificazione $T_c = T_m$ ottengo il risultato voluto.
$$
f_c(\beta,v_c)= u_m - T_m s_m(u_m,v_m) = f_m(u_m,v_m)
$$
Ne consegue che anche le entropie (dunque la termodinamica) coincidono.

## Non equivalenza
La derivazione precedente fa un'assunzione importante: _l'energia libera ha un unico punto di massimo_. Per far vedere questa cosa si dimostra la stretta convessità dell'energia libera. Per fare ciò si richiedono _ipotesi aggiuntive di stabilità_. La cosa diventa delicata durante le _transizione di fase_.
