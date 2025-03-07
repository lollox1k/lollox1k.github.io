Sono [[Modelli microscopici]]  [[Scale di osservazione]], lo stato del sistema è l'insieme delle posizioni e velocita dei veicoli.
$$
x_i(0) = x_i^0, \qquad v_i(0)= v_i^0, \qquad i=1,\dots,N
$$
"car-following models"

Ipotesi standard: un ordinamento iniziale che si preserva:
$$
x_1^0 < x_2^0 < \dots < x_N^0
$$
Una corsia, non stiamo considerando sorpassi in questo modello.

Focus sul veicolo $i$, il suo _leader_ è il veicolo $i+1$, il suo _follower_ $i-1$.

Sono modelli di tipo forza, ovvero definisco la forza sul veicolo $i$ in base allo stato microscopico, in questo caso da se stesso e l'interazione con il leader:
$$
\begin{cases}
\dot{x}_i = v_i\\
\dot{v}_i = F(t, x_i(t), v_i(t), x_{i+1}(t), v_{i+1}(t))
\end{cases}
$$
### Modello follow-the-leader
Pipes 1953, Gazis 1961
Vediamo come è definita $F$:
$$
F = \alpha \frac{v_{i+1}(t)-v_i(t)}{[x_{i+1}(t)-x_i(t)]^\gamma} + \beta \frac{v_d-v_i{t}}{\tau}
$$
Notiamo due termini: 
- il primo è d'interazione: l'accellerazione diventa positiva se il leader è più veloce, negativa se sono più veloce. Il denominatore ha l'effetto che se sono molto lontano dal leader, subisco poco la sua influenza.
- il secondo termine è detto di _rilassamento_, il parametro $v_d$ è una velocità desiderata, $\tau$ il tempo di rilassamento (tempo di reazione): è la tendenza a raggiungere la velocità desiderata, indipendentemente dal leader. Nel primo della fila c'è solo questo termine! (Nel caso di condizioni al bordo periodiche sì, es. rotonde).

### Optimal velocity model, modello di Bando
Bando, Hasebe et al. 1995
$$
F = \frac{1}{\tau}\Big[ V_d(x_{i+1}(t)-x_i(t))-v_i(t)\Big]
$$
Il termine d'interazione è "inglobato" nel termine di rilassamento. Si deve definire una funzione $V_d$ (funzione della distanza dal leader), sperimentalmente determinata (es tipo sigmoide):
![[Pasted image 20220309123931.png]]
In questo modello la velocità desiderata è dipendente dallo stato del sistema.

Si possono combinare i due modelli, mettendo il termine del modello di Bando al postom del termine di rilassamento nel modello FTL, modello chiamato FTL-OVM, FTL-Bando.

### Domande di ricerca
- Come scegliere $V_d$? come questa scelta influenza la stabilità nel traffico?
Utile per auto a guida autonoma.
- modelli con interazioni non locali
- studiare effetti di ritardo
- studiare modelli multi-lane, multi-classe