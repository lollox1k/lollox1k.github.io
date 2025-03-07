Supponiamo di avere una variabile dipendente $w$ dimensionale che può assumere valori in $[w_m, w_M]$. Dipende dalla fisica del sistema (es temperatura di un materiale).
Adimensionalizzare significa trovare $\overline w$ tale che i nuovi valori che può assumere sono ad esempio $[0,1]$ oppure $[-1,+1]$ . Banalmente riscalo $w$:
$$
\overline w = \frac{w-w_m}{w_M - w_m} \implies \overline w \in [0,1]
$$
Approccio simile per le variavili indipendenti:
Se abbiamo variabili spaziali $x,y,z$, possiamo adimensionalizzare in modo simile tenendo conto dello spazio fisico del sistema, quindi $x_m,x_M$ ecc.
Possiamo però adimensionalizzare anche rispetto al massimo tra $x_M,y_M,z_M$, preservando le proporzioni spaziali del sistema. 

Per la variabile indipendente temporale allo stesso modo:
$$
\overline t = \frac{t-t_0}{T-t_0} \implies \overline t \in [0,1]
$$
$t_0$ tempo iniziale, tipicamente posto a zero, $T$ grande è il tempo di osservazione del fenomeno fisico. 

### Esempio modello traffico
Flusso in una dimensione, una corsia. Sia $l$ la lunghezza del tratto di strada considerato, la nostra _lunghezza caratteristica_. Dobbiamo determinare un _tempo caratteristico_ $T$, abbiamo una densità massima $\rho_M$ ed una velocità massima $v_M$.
Il tempo caratteristico sarà $T = \frac{l}{v_M}$.
Le variabili adimensionali indipendenti sono:
- il tempo $\overline t = \frac{t}{T}$
- la posizione $\overline x = \frac{x}{l}$
Le variabili adimensionali dipendenti sono:
- la densità $\overline \rho = \frac{\rho}{\rho_M}$
- la velocità $\overline V = \frac{V}{V_M}$
- la velocità media $\overline v = \frac{v}{v_M}$
- il flusso di veicoli $q$

Queste variabili hanno diverse caratterizzazioni, in base alla scala di osservazione:
- scala microscopica: lo stato è $x_i(t), v_i(t)$ con $t$ var indipendente
- scala mesoscopica: lo stato è ancora inviduato da $x,v$, ma in modo probabilistico:
$$
f(t,x,v)
$$
densità di probabilità. Quindi le var indipendeti sono $t,x,v$.
- scala macroscopica: lo stato è descritto da quantità medie:
$$
\rho(t,x) \qquad v(t,x) \qquad q(t,x)
$$
$(t,x)$ sono le variabili indipendenti.