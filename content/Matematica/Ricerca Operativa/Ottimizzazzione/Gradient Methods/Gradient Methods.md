# Core idea
Una famiglia di metodi di ottimizzazzione non lineare numerici. 
L'idea alla base è una successione di punti definita per ricorrenza:
$$
x^{k+1}= x^k + \alpha^k d^k
$$
dove la _direzione_ $d^k$ dipende dal gradiente.
Inoltre lo _step size_ $\alpha^k$ può variare, secondo varie regole. 

# Convergenza
Si possono trovare condizioni che garantiscono la _convergenza_ di questi metodi in _punti stazionari_, ache la _velocità di convergenza_. 
Un importante risultato è il [[Capture theorem]], se la sequenza arriva abbastanza vicino ad un minimo locale, il  metodo converge lì.

## Direzione 
Intuitivamente, se vogliamo minimizzare la funzione dobbiamo richiedere che:
$$
\nabla f(x^k) \cdot d^k < 0 \qquad \forall k
$$
tuttavia, non vogliamo nemmeno che la successione di direzioni converga ad una direzione ortogonale al gradiente (_asintoticamente ortogonali_), ovvero:
$$
\frac{\nabla f(x^k)\cdot d^k}{||\nabla f(x^k)||\,||d^k||} \to 0
$$
Una condizione che possiamo imporre affinché ciò non accada è la seguente:
### Eigenvalue bond
$$
d^k = -D^k \nabla f(x^k)
$$
dove $D^k$ è una matrice simmetrica definita positiva, con autovalori positivi e limitati, ovvero esistono due costanti positive $c_1,c_2$ tale che:
$$
c_1 ||v||^2\leq v^t D^k v \leq c_2 ||v||^2 \qquad \forall v \in \mathbb{R}^n
$$
Infatti:
$$
|\nabla f(x^k)\cdot d^k| = |\nabla f(x^k)^TD^k \nabla f(x^k)| \geq c_1 ||\nabla f(x^k)||^2
$$
$$
||d^k||^2 = [D^k \nabla f(x^k)]^T D^k \nabla f(x^k) = ||D^k \nabla f(x^k)||^2 = ||D||^2 ||\nabla f(x^k)||^2 \leq c_2^2 ||\nabla f(x^k)||^2
$$
siccome $c_2$ è maggiore uguale di ogni autovalore di $D$, upper bound sulla norma matriciale. Quindi:
$$
\frac{|\nabla f(x^k)\cdot d^k|}{||\nabla f(x^k)||\,||d^k||} \geq \frac{c_1 ||\nabla f(x^k)||^2}{c_2||\nabla f(x^k)||^2  }= \frac{c_1}{c_2} \qquad \square
$$
Un'altra condizione più generale è la seguente:
### Gradient related
supponiamo di poter determinare $d^k$ da $x^k$, diciamo che la sequenza di direzioni è _gradient related_ se per ogni sottosuccessione $\{x^k\}_j$ che converge ad un punto _non stazionario_ vale:
$$
\limsup_{j\to\infty} \nabla f(x^{k_j})^T d^{k_j} < 0 
$$

## Step size selection rules
I nome dei metodi seguono dalla regola di scelta dello step. Da notare come in questi metodi valga sempre la condizione sulla direzione precedemente enunciata.
1. [[Minimization rule]]
2. [[Armijo rule]]
3. [[Costand step size]]
4. [[Diminiscing step size]]