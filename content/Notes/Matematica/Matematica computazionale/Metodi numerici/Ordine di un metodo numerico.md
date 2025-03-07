Un [[Metodi numerici|metodo numerico]] $\Phi$ si dice di _ordine p_, se per una qualche norma vettoriale vale:
$$
||T(x,y;h)|| \leq Ch^p
$$
uniformemente nell'intervallo di definizione d'interesse, con $C$ costante indipendente da $x,y$ e $h$.
Ovvero $||T|| = O(h^p)$. Da notare che $p >0$ implica la [[Consistenza di un metodo numerico]]. 

### Esempi
Vediamo qualche esempio:
$$
f'(x)=u(x)
$$
Usiamo Eulero:
$$
\tilde u_h(x) = \frac{f(x+h)-f(x)}{h}
$$
L'errore di troncamento è la differenza con la soluzione analitica:
$$
T = |\tilde u_h(x)-u(x)| = \Big|\frac{f(x+h)-f(x)}{h}-f'(x)\Big|
$$
L'idea che si sfrutta sempre è espandere con Taylor $u$ attorno ad $x$, ed esprimere il resto in forma di Lagrange, bisogna capire dove fermarsi, proviamo con l'ordine due:
$$
T = \frac{1}{h}\Big [ f(x) + hf'(x)+\frac{h^2}{2}f''(\xi) - f(x)\Big]-f'(x)
$$
$$
T = \frac{h}{2}f''(\xi) = Ch
$$
quindi è di ordine 1. 

Vediamo un altro metodo stesso problema, approssimare la derivata di una funzione, al secondo ordine: "leap-frog", praticamente Verlet:
$$
\tilde u_h(x) = \frac{f(x+h)-f(x-h)}{2h}
$$
Spoiler: è del secondo ordine