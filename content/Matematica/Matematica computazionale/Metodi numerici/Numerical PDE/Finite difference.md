Un approccio [[Numerical PDE| numerico]] per le PDE molto semplice: discretizzare il domnio spaziale e temporale, approssimare le derivate con rapporti di differenze finite.

### FD linear advection
Vediamo questo approccio per l'equazione parabolica al prim'ordine [[linear advection]], in $1D+1D$. Il primo passo è discretizzare il tempo e lo spazio in $N$ punti:
![[Pasted image 20220330170738.png]]
indichiamo con $u_i^n$ il valore della funzione nel punto spaziale $i = 1,\dots,N$ al tempo $n = 0,\dots,T$, fissando una risoluzione spaziale $\Delta x$ e temporale $\Delta t$.
Discretizzando l'equazione otteniamo:
$$
\frac{u_i^{n+1}-u_i^n}{\Delta t} = -a\frac{u_{i+1}^n-u_{i-1}^n}{2\Delta x}
$$
Abbiamo stimato la derivata temporale con Eulero (ordine 1), la derivata spaziale con Verlet (ordine 2 [[Ordine di un metodo numerico|vedi qui]]). 

Esplicitando per il valore al tempo $n+1$ otteniamo:
$$
u_i^{n+1} = u_i^n -\frac{1}{2}\frac{a\Delta t}{\Delta x}(u_{i+1}^n-u_{i-1}^n) 
$$
Il termine costante $C := \frac{a\Delta t}{\Delta x}$ viene detto $CFL$ number, Courant-Friedrichs-Lewy.

#### Osservazione 2
quando calcoliamo il valore nel punto 1, "caschiamo fuori", infatti ci serve il valore nel punto 0: si risolve il problema aggiungendo manualmente dei punti "_ghost points_" (stesso problema per l'ultimo punto n).
Oppure _condizioni di bordo periodiche_.

#### Osservazione 2
Il metodo è instabile!
Usiamo la [[fourier mode analysis]] per farlo vedere: l'equazione è lineare, quindi ogni modo di fourier non si influenza. Vediamo che succede all'ampiezza di un particolare modo:
$$
a_i^n = A^n e^{j\theta i}
$$
Abbiamo usato $j$ come unità immaginaria:
Calcoliamo il rapporto delle ampiezze per tempi succesivi (usando lo schema numerico):
$$
\Big|\frac{A^{n+1}}{A^n}\Big| = |e^{j\theta i}-\frac{C}{2}e^{j\theta i}(e^\theta - e^{-\theta}) = |1-jC\sin\theta|
$$
Il modulo quadro è:
$$
\Big| \frac{A^{n+1}}{A^n}\Big|^2 = 1 + C^2\sin^2\theta \geq 1
$$
quindi instabile indipendentemente dal valore della costante $C$.
