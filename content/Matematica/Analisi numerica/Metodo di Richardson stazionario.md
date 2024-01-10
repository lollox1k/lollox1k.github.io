# Metodo di Richardson stazionario

Sono metodi iterativi della forma:
$$
x^{k+1} = x^k + \alpha P^{-1}r^k \qquad r^k := b - Ax^k, \quad \alpha > 0
$$
quindi metodi lineari stazionari del prim'ordine.
Il parametro reale $\alpha$ viene detto _parametro di accelerazione_, e la matrice $P \in \mathbb{C}^{n\times n}$ non singolare è detta _precondiziontore_.

Esplicitando il resto, il metodo assume la forma:
$$
x^{k+1} = (I-\alpha P^{-1}A)x^k + \alpha P^{-1}b
$$

## Analisi di convergenza

**Teorema** Se $P$ è una matrice non singolare, il metodo di Richardson stazionario è convergente se e solo se:
$$
\frac{2\Re{\lambda_i}}{\alpha|\lambda_i|^2}> 1 \quad \forall i = 1,\dots,n
$$
dove $\lambda_i$ sono gli autovalori di $P^{-1}A$.

**Dimostrazione**  Applichiamo il teorema sulla [[Metodi iterativi#Condizioni per la convergenza| convergenza dei metodi iterativi]] alla matrice di iterazione $R_\alpha = I-\alpha P^{-1}A$. La condizione diventa $|1-\alpha \lambda_i|<1$ per ogni $i$ diventa:
$$
(1 -\alpha \Re{\lambda_i})^2 + \alpha^2(\Im{\lambda_i})^2 < 1
$$
rimaneggiando, segue la tesi. $\square$

**Osservazione** Notiamo che se il segno della parte reale degli autovalori $\lambda_i$ non è costante, non esiste un $\alpha$ che permette la convergenza, dunque il metodo stazionario non può funzionare.

Possiamo ottenere risultati più specifici facendo opportune ipotesi sullo spettro di $P^{-1}A$.

**Teorema** Sia $P$ non singolare, e $P^{-1}A$ abbia autovalori reali positivi, ordinati in modo che $\lambda_1,\lambda_2,\dots,\lambda_n > 0$. Allora il metodo di Richardson stazionario converge se e solo se $0<\alpha < \frac{2}{\lambda_1}$. 
Inoltre, posto:
$$
\alpha_{opt} = \frac{2}{\lambda_1+\lambda_n}
$$
minimizzo il raggio spettrale $\rho(R_\alpha)$, quindi ho una convergenza più veloce:
$$
\min_\alpha \rho(R_\alpha)= \frac{\lambda_1-\lambda_n}{\lambda_1+\lambda_n}
$$

## Velocità di convergenza

Mettiamo nel caso in cui la matrice $A$ e $P$ siano _hermitiane definite positive_. Questo garantisce che lo spettro sia reale e maggiore strettamente di zero:
$$
\lambda_1 \geq \lambda_2 \geq \dots > 0
$$
Possiamo usare la [[norma dell'energia]] o $A$-norma per simare la velocità di convergenza, vale il seguente teorema:
**Teorema** Sia $A$, $P$ e $P^{-1}A$ hermitiane definite positive. Il metodo di Richardson stazionario con parametro $\alpha$ ottimale ha una velocità di convergenza:
$$
\Vert e^{k+1}\Vert_A \leq \rho(B_\alpha) \Vert e^k\Vert_A
$$
con
$$
\rho(B_\alpha) = \frac{\lambda_1-\lambda_n}{\lambda_1+\lambda_n} = \frac{\mathcal{K}_2(P^{-1}A)-1}{\mathcal{K}_2(P^{-1}A)+1}
$$
**Dim** Vale
$$
\Vert e^{k+1}\Vert_A \leq \Vert B_\alpha\Vert_A \Vert e^k\Vert_A
$$
Dove $B_\alpha = (I-\alpha P^{-1}A)$. Si può verificare che $AB_\alpha$ è hermitana positiva, dunque la sua norma dell'energia è uguale al raggio spettrale:
$$
\Vert e^{k+1}\Vert_A \leq \rho(B_\alpha) \Vert e^k\Vert_A
$$
Sfruttiamo il fatto che $P^{-1}A$ sia hermitiana e con spettro positivo, in maniera tale che $\Vert P^{-1}A\Vert_2 = \rho(P^{-1}A) = \lambda_1$,  (analogamente per il modulo dell'inversa) per scrivere $\mathcal{K}_2(P^{-1}A) = \frac{\lambda_1}{\lambda_n}$. $\square$

In realtà possiamo non richiedere il fatto che che $P^{-1}A$ sia hermitiana definita positiva, infatti se $P$ ed $A$ lo sono, segue che anche $P^{-1}A$ lo sia (studiare la matrice $P^{-1/2}AP^{-1/2}$). Quindi il teorema può essere enunciato come:
**Teorema** 
Sia $A$ e $P$ hermitiane definite positive. Il metodo di Richardson stazionario con parametro $\alpha$ ottimale ha una velocità di convergenza:
$$
\Vert e^{k+1}\Vert_A \leq \frac{\mathcal{K}_A(P^{-1}A)-1}{\mathcal{K}_A(P^{-1}A)+1} \Vert e^k\Vert_A
$$
**Dim** Dalle osservazioni precedenti, e dal fatto che $AP^{-1}A$ è hermitiana, dunque la sua norma dell'energia è uguale al raggio spettrale, che ci permette di introdurre il numero di condizionamento in $A$-norma. La disuguaglianza precedente, con il condizionamento spettrale segue dal fatto che $\mathcal{K}_A(P^{-1}A) \leq \mathcal{K}_2(P^{-1}A)$. $\square$





