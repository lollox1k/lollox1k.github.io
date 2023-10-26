# Metodi iterativi

Un metodo iterativo per risolvere equazioni lineari, consiste in un algoritmo che parte da una guess iniziale $x^0$, e via via genera soluzioni approssimate sempre migliori. Definisce quindi una successione, il cui limite è la soluzione esatta del sistema. 
$$
Ax = b \qquad x^k \to x
$$

Consideriamo prima un metodi iterativi della forma:
$$
x^{k+1} = Bx^k + f 
$$
quindi che generano una nuova soluzione approssimata come combinazione lineare della precedente, più un vettore costante.

Definendo il residuo al passo $k$ come $e^k := x- x^k$, la convergenza alla soluzione è equivalente a dire $e^k \to 0$ (equivalentemente se esiste una norma per cui $\Vert e^k \Vert \to 0$).

## Condizioni per la convergenza
Che condizioni deve avere affinchè converga alla soluzione esatta? 
L'idea è che vogliamo usare il teorema delle contrazioni.

**1** La soluzione esatta deve essere un punto fisso del metodo (condizione di consistenza).
Nel nostro caso, per il metodo da noi analizzato, una volta fissata $B$ ciò equivale a:
$$
x = Bx + f
$$
$$
(B^{-1} - I)A^{-1}b = f
$$
**2** Affinchè sia una contrazione, rispetto ad una qualunque norma matriciale si deve avere:
$$
\Vert Bx-By \Vert \leq \Vert B \Vert \Vert x-y\Vert
$$
ovvero $\Vert B \Vert < 1$.

Usando il [[Teorema di Banach-Caccioppoli]], sappiamo che $x^k \to x$.

**Teorema** Un metodo $x^{k+1} = Bx^k + f$ _consistente_, è convergente per ogni approssimazione iniziale $x^0$ se e solo se vale $\rho(B)<1$.
**Dim** Per la consistenza del metodo posso scrivere esplicitamente come evolve il residuo:
$$
e^{k+1} = x-x^{k+1} = Bx + f - Bx^k -f = B(x-x^k) = Be^k
$$
dove abbiamo usato la consistenza del metodo per la terza uguaglianza. Da qui segue:
$$
e^k = B^k e^0 \qquad \forall k \geq 0
$$
Segue dalla Gelfand's formula che $\lim_k\Vert B^k \Vert = \lim_k\rho(B)^k = 0$. 
($\impliedby$)  Sia $\rho(B) < 1$, facciamo vedere che il residuo va a zero per ogni $e^0$ iniziale.
Sia $\epsilon >0$ tale che $\rho(B) < 1-\epsilon$. Ricordiamo che vale $\rho(A) = \inf_{\Vert\cdot\Vert} \Vert A\Vert$ sull'insieme delle norme naturali:
$$
\exists \;\Vert\cdot\Vert\;:\; \Vert B \Vert \leq \rho(B)+\epsilon < 1
$$
Dato che $\Vert B^k\Vert \leq \Vert B \Vert^k$ per submoltiplicatività, si ha $\lim_k \Vert B^k \Vert = 0$. Considero la norma vettoriale che induce $\Vert\cdot\Vert$, si ha che 
$$
\lim_k \Vert e^k \Vert = \lim_k \Vert B^k e^0\Vert \leq \Vert e^0\Vert \lim_k \Vert B^k \Vert = 0 \quad \forall e^0
$$
quindi il metodo converge, indipendetemente dalla scelta di $x^0$.

$(\implies)$ Sia $\lim_k \Vert e^k\Vert = 0$ per ogni $e^0$, supponiamo per assurdo che $\rho(B)\geq 1$. Allora esiste un autovalore di $B$ $|\lambda| \geq 1$. Scegliamo $e^0$ come autovettore corrispondente all'autovalore $\lambda$, ovvero:
$$
Be^0 = \lambda e^0
$$
da questo segue che:
$$
\Vert e^k\Vert = \Vert B^k e^0 \Vert = |\lambda|^k \Vert e^0 \Vert
$$
che è assurdo, infatti il limite non tende a zero, ma diverge ( rimane costante)! $\square$

## Criterio di arresto

Nel mondo reale non possiamo raggiungere il limite della successioni, ci dobbiamo accontentare di una soluzione approssimata, entro una tolleranza richiesta. Idealmente, questa tolleranza va calcolata rispetto alla soluzione esatta:
$$
\frac{\Vert x-x^k\Vert}{\Vert x\Vert} = \frac{\Vert e^k\Vert}{\Vert x \Vert} < \text{tol}
$$
tuttavia per questo criterio di arresto deve essere nota la soluzione esatta... Non possiamo calcolare il residuo $e^k$ senza sapere la soluzione esatta, ma possiamo calcolare esattamente il residuo $r^k := Ae^k = b - Ax^k$.

Quindi il criterio diventa:
$$
\frac{\Vert r^k\Vert}{\Vert b\Vert} < \text{tol}
$$
Come è legato al residuo?
$$
\frac{\Vert e^k\Vert}{\Vert x\Vert} = \frac{\Vert A^{-1}r^k\Vert}{\Vert x\Vert} \leq \frac{\Vert A^{-1}\Vert \Vert r^k\Vert}{\Vert x \Vert} = \mathcal{K}(A) \frac{\Vert r^k\Vert}{\Vert A \Vert \Vert x \Vert} \leq \mathcal{K}(A) \frac{\Vert r^k\Vert}{\Vert b\Vert}
$$
> il criterio di arresto è tanto meno attendibile quanto più $\mathcal{K}(A)$ è grande





