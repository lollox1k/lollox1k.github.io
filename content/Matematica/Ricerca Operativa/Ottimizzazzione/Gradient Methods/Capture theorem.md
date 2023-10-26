# Capture Theorem
![[Pasted image 20220630172907.png]]

Sia $f$ continuamente differenziabile, sia $\{x^k\}$ una sequenza generata da un metodo del gradiente, ovvero $x^{k+1}=x^k+\alpha^kd^k$, tale che $f(x^{k+1})\leq f(x^k)$ e che converga ad un punto stazionario.  Si assuma che esistano gli scalari $s,c > 0$ tale che per tutti i $k$ vale:
$$
\alpha^k \leq s, \qquad \Vert d^k \Vert \leq c \Vert \nabla f(x^k)\Vert
$$
Sia $x^*$ un minimo locale isolato di $f$ in un certo insieme aperto. _Allora_ esiste un insieme aperto $S$ che contiene $x^*$ tale che se $x^k \in S$ tutti i punti successivi sono in $S$, e $x^k \to x^*$, ovvero la sucessione viene catturata.

### Dim 
Sia $\rho > 0$ tale che $x^*$ sia il minimo della palla $B_\rho(x^*)$:
$$
f(x^*) < f(x) \qquad \forall x \in B_\rho(x^*)  
$$
definiamo una funzione $\phi(t)$ per $t \in [0,\rho]$:
$$
\phi(t) := \min_{ \{x \vert t \leq \Vert x-x^*|\leq \rho\}} f(x)-f(x^*)
$$
proprietà di questa funzione:
1. $\phi(t)> 0 \qquad \forall t \in (0,\rho]$
2. è monotona non decrescente

Fissato $\epsilon \in (0,\rho]$ sia $r>0$ tale che:
$$
\Vert x - x^*\Vert < r \implies \Vert x-x^*\Vert +sc\Vert \nabla f(x)\Vert < \epsilon
$$
questo insieme è ben definito, infatti $\Vert \nabla f(x)\Vert$ vale $0$ in $x^*$, e dalla continuità ne segue che questo termine può essere reso arbitrariamente piccolo stando abbastanza vicino a $x^*$.

L'insieme $S$ del teorema è:
$$
S :=\left\{  x \vert \, \Vert x-x^*\Vert < \epsilon, f(x) < f(x^*)+\phi(r) \right\}
$$
alcune osservazioni:
1. $S \subseteq B_\rho(x^*)$, ovvero è dentro la palla dove è l'unico minimo.
2. la seconda condizione non permette al metodo di "scappare"

Dimostriamo che se $x^k \in S$ allora $x^{k+1} \in S$, per induzione allora tutta la successione rimane in $S$.

Dalla definizione di $S$ vale:
$$
f(x^k)-f(x^*) < \phi(r)
$$
ora sfruttiamo la definizine di $\phi$, che è il minimo di tutti i vettori nella corona circolare $t\leq \Vert x-x^*\Vert \leq \rho$. Siamo certi che $x^k$ appartenga alla corona $\Vert x^k-x^*\Vert \leq \Vert x-x^*\Vert \leq \rho$, quindi:
$$
\phi(\Vert x^k-x^*\Vert) \leq f(x^k)-f(x^*)< \phi(r)
$$
siccome $\phi$ è monotona non decrescente, questo implica che:
$$
\Vert x^k-x^*\Vert  < r
$$
quindi rispetta
$$
\Vert x^k-x^*\Vert + sc\vert \nabla f(x^k)\Vert < \epsilon
$$
con un'altra semplice relazione otteniamo la tesi. Stimiamo
$$
\Vert x^{k+1}-x^*\Vert = \Vert x^k +\alpha^kd^k-x^*\Vert \leq \Vert x^k-x^*\Vert + \alpha^k \Vert d^k\Vert
$$
usiamo ancora le ipotesi che limitano lo step e la norma della direzione:
$$
\leq \Vert x^k-x^*\Vert + sc\Vert \nabla f(x^k)\Vert
$$
combinato con il risultato precedente:
$$
\Vert x^{k+1}-x^*\Vert < \epsilon
$$
siccome $f(x^{k+1}) < f(x^k)$, ne segue:
$$
f(x^{k+1})-f(x^*) < f(x^k)-f(x^*)< \phi(r)
$$
quindi anche $x^{k+1} \in S$. 
Siccome la chiusira si $S$ è compatta, la successione converge all'unico punto stazionario $x^*$. $\square$

### Oss
E' evidente come ogni per ogni $S' \subseteq S$ il teorema continua a valre, ovvero possiamo rendere piccolo a piacere l'insieme di cattura. 