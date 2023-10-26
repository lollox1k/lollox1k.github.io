Una [[PDE]] non lineare (quasi-lineare), un suo caso semplice è un'esempio di come la non linearità può generare soluzioni non $C^\infty$ nonostante la condizione iniziale sia smooth.
Forma generale:
$$
\partial_t u + u\partial_x u - a\partial_x^2 u = 0
$$
la non linearità è data dal fattore $u$ davanti la derivata spaziale. Ponendo $a=0$ otteniamo un'equazione del trasporto dove la velocità delle caratteristiche dipende dal valore stesso della soluzione, si vede facilmente che può generare discontinuità a funzione gradino (onda d'urto). Spesso si indica nella forma equivalente:
$$
\partial_t u + \frac{1}{2}\partial_x u^2 = 0
$$
Prendiamo la condizione iniziale $u_0 = -sinx$, lavoriamo nell'intervallo $[-\pi/2,\pi/2]$. Si vede facilmente che per $x$ negative la velocità è positiva, quindi la condizione iniziale si sposta verso destra, succede l'opposto per la parte $x>0$. Quindi la condizione iniziale si _schiaccia_ sempre più tendendo ad una funzione gradino.