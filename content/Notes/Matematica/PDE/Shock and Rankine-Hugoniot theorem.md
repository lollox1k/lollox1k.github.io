Nel caso dell'equazione del trasporto non lineare, le curve caratteristiche possono intersecarsi: si formano delle discontinuità, e la soluzione va assunta in [[Weak solutions of continuity equations|senso debole]].

I punti di intersezione venogno detti di _shock_. 

### Teorema Rankine-Hugoniot
Utile per trovare la curva dello shock, come si evolve.

Sia $u$ una soluzione debole di:
$$
u_t + q(u)_x = 0
$$
della forma:
$$
u(t,x) = \begin{cases} u_-(t,x) x < \sigma(t) \\ u_+(t,x) x > \sigma(t) \end{cases}
$$
con $u_-$ e $u_+$ soluzioni classiche. Sia la curva $C$ parametrizzata da  $\sigma \in C^1([0,\infty)])$. 
_Allora_ lungo la curva $C$ vale la seguente relazione: 
$$
q(u_+) - q(u_-) = (u_+ - u_-)\sigma'
$$
ci dice come si raccordano le due soluzioni classiche, il salto.

### Dim 
parto dall'equazione integrale che risolve una soluzione debole, divido l'integrale nelle due soluzioni classiche e torno indietro (posso calcolare le derivate classiche).