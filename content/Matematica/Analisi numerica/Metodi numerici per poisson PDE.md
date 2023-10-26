## L'equazione di Poisson

L'equazione di poisson è una PDE lineare del second'ordine
$$
\nabla^2y = f
$$
E' un _problema al contorno_, di tipo spaziale con condizioni di bordo del dominio sul quale è definita l'equazione differenziale, sono problemi _stazionari_.

Esistono due tipi di condizioni al contorno. Sia $D \subseteq \mathbb{R}^n$ il dominio sul quale è definita l'equazione differenziale:
- _Problema di Dirichlet_ $y = f$ su $\partial D$;
- _Problema di Neumann_ $\frac{\partial y}{\partial n} = g$ su $\partial D$ (derivata normale sul bordo),
- _Problema Robin_ condizioni miste.

## ODE

Consideriamo il caso unidimensionale con condizioni al contorno di Dirichlet omogenee:
$$
\begin{cases}
-y''(x) = f(x)\qquad x \in [0,1]\\
y(0)=0 \\
y(1)=0
\end{cases}
$$
Questo ODE ad esempio modellizza la forma d'equilibrio di una stringa elastica con estremi fissati all'altezza zero sottoposta ad un carico $f(x)$.

**Oss** Il caso non omogeno può essere ricondotto tramite l'introduzione di una funzione ausiliaria a quello omogeno, pertando studiamo questo s.p.g.

### Esistenza ed unicità
**Proposizione** Se il carico è continuo, $f(x) \in C^0([0,1])$, allora esiste unica $y(x) \in C^2([0,1])$:
$$
y(x) = \int_0^1 G(x,s)f(s)ds
$$
dove $G(x,s)$ è la funzione di green del Laplaciano $1D$:
$$
G(x,s) = 
\begin{cases}
s(1-x) \text{ se } s \in [0,x]\\
x(1-s) \text{ se } s \in [x,1]
\end{cases}
$$

### Proprietà della soluzione
Dalla forma intergrale della soluzione si vede che se $f \in C^m([0,1])$ allora $y \in C^{m+2}([0,1])$.

**Monotonia** Se $f \in C^0([0,1])$ è una funzione non negativa, allora $y$ è non negativa, siccome $G(x,s)\geq 0$ $\forall s \in [0,1]$.

**Principio del massimo** Se $f \in C^0([0,1])$ allora:
$$
\Vert y \Vert_\infty \leq \frac{1}{8} \Vert f \Vert_\infty
$$
**Dim** Dalla definizione di $y$, passo ai moduli ed uso le proprietrà dell'integrale del modulo. $\square$

### Soluzione numerica 1D

Usiamo un metodo delle [[Finite difference|differenze finite]], nel caso $1D$ semplicemente discretizziamo l'intervallo $[0,1]$ con $n+1$ nodi equidistanti, ottenendo $n$ intervalli di ampiezza $h = \frac{1}{n}$, dove $h$ è il _passo di discretizzazzione_.

Indicizziamo gli $n+1$ nodi con $x_j = jh$ con $j = 0:n$. 

Approssimiamo la derivata seconda con la formula delle differenze centrate.
Usando la formula di Taylor con resto di Lagrange:
$$
y(x_j + h) = y(x_j) + y'(x_j)h +\frac{1}{2}y''(x_j)h^2 + \frac{1}{6}y'''(x_j)h^3 +\frac{1}{24}y''''(\xi_j)h^4
$$
$$
y(x_j - h) = y(x_j) - y'(x_j)h +\frac{1}{2}y''(x_j)h^2 - \frac{1}{6}y'''(x_j)h^3 +\frac{1}{24}y''''(\eta_j)h^4
$$
Sommando:
$$
y(x_j+h) + y(x_j-h) = 2y(x_j) + y''(x_j)h^2 + \frac{h^4}{24}(y''''(\xi_j)+y''''(\eta_j))
$$
da cui
$$
y''(x_j) = \frac{y(x_j+h) -2y(x_j) + y(x_j-h)}{h^2} + o(h^2) 
$$
nel nostro caso il termine di resto può essere maggiorato con il carico:
$$
\frac{h^4}{24}\left|y''''(\xi_j)+y''''(\eta_j)\right| \leq \frac{h^4}{12} \Vert y'''' \Vert_\infty = \frac{h^4}{12}\Vert f'' \Vert_\infty
$$

Useremo questo schema centrato per trovare la soluzione sui nodi, che indicheremo col vettore $\{u_0,\dots,u_{n+1}\}$. Sappiamo già i valori di bordo dalle condizioni di Dirichlet. 

Discretizziamo anche la funzione di carico: $f_j = f(x_j)$ con $j = 1,\dots,n-1$.

Otteniamo $n-1$ equazioni lineari:
$$
\frac{1}{h^2}
\begin{pmatrix}
2 & -1 & 0 & 0 & \dots \\
-1 & 2 & -1 & 0 & \dots \\
0 & -1 & 2 & -1 & \dots \\
&&\dots
\end{pmatrix}
\begin{pmatrix}
u_1 \\ u_2 \\ u_3 \\ \dots
\end{pmatrix}
= \begin{pmatrix}
f_1 \\ f_2 \\ f_3 \\ \dots
\end{pmatrix}
$$
ricordiamo che $u_0 = u_n = 0$. La matrice viene chiamata $A_{fd}$.
**Osservazioni** E' una matrice:
1. Tridiagonale.
2. E' reale e simmetrica.
3. Diagonale dominante.
4. Tutti gli elementi diagonali positivi.
5. Sparsa.
6. Irriducibile.
7. Definita positiva.
8. Una $M$-matrice.

### Condizionamento

Studiamo il numero di [[Fondamenti dell'analisi numerica|condizionamento]] con la norma infinito della matrice $A_{fd}$. Si vede subito che  $\Vert A_{fd}\Vert_\infty = \frac{4}{h^4}$.
Per stimare $\Vert A_{fd}^{-1}\Vert_\infty$ sfruttiamo il fatto che l'inversa di una $M$-matrice ha elementi non negativi, e che la norma infinito non è altro che il massimo valore della somma dei moduli di ogni riga, che possiamo scrivere come:
$$
\Vert A_{fd}^{-1}\Vert_\infty = \max_{1\leq i \leq n-1} (A_{fd}^{-1}f)_i
$$ dove $f = (1,1,1,\dots)^T$. 
Ora il trucco seguente: siccome $f'=f''=0$ la soluzione numerica soddisfa lo schema, ovvero $u = A_{fd}^{-1} f$, passando alle norme si ottiene:
$$
\frac{1}{8} \Vert f \Vert_\infty \geq \Vert u \Vert_\infty = \max_{1\leq i \leq n-1} (A_{fd}^{-1}f)_i 
$$
Siccome $f=(1,1,1,1,\dots)^T$ la sua norma infinito vale uno, abbiamo una stima dal basso del condizionamento a norma infinito:
$$
K_\infty(A_{fd}) \geq \frac{1}{2h^2} = \Theta(n^2)
$$
dunque, $A_{fd}$ è _mal condizionata_.

### Caratteristiche della soluzione numerica

Dato che $A_{fd}$ è una $M$-matrice, abbiamo la _monotonia della soluzione numerica_.

Introducendo per le funzioni di griglia la norma discreta del massimo, abbiamo anche il _principio del massimo discreto_, basta usare la stima precedente sull'inversa.

**Stabilità** Il principio del massimo discreto ci assicura che la soluzione non si allontana troppo, è dunque stabile.

**Consistenza** L'errore di troncamento converge a zero quando $h\to0$. 
$$
\tau_j := \frac{1}{h^2}|-y(x_j+h)+2y(x_j)-y(x_j-h) - f_j|
$$
dove invece della soluzione numerica abbiamo usato $f_j$ siccome $A_{fd}u = f$.
Siccome il metodo è del secondo ordine sappiamo che:
$$
|\tau_j| \leq \frac{h^2}{12}\Vert f''\Vert_\infty \qquad \forall j = 1:n-1
$$
che va a zero come $h^2$.

Abbiamo dunque la _convergenza_.





