>_It is a fundamental principle of mathematics to map a class of objects that are of interest into a class of objects where computations are easier. This map can be one to one, as with linear maps and matrices, or it may map only some properties uniquely, as with matrices and determinants._                                        
>                                                                                                                    -Klenke ch. 3

#### Probability generating functions that are designed for $\mathbb{N}_0$-valued random variables.
### Def
Sia $X$ una variabile aleatoria in $\mathbb{N}_0$. La funzione generatrice (p.g.f.) è la mappa $\psi : [0,1] \to [0,1]$ (con la convenzione $0^0 = 1$):
$$
\psi(z) = \sum_{n=0}^\infty P[X=n]z^n
$$
Seguono dalla teoria delle serie le proprietà:
1. Se $\psi$ è $C^0[0,1]$ e $C^\infty (0,1)$ allora vale:
$$
\lim_{z\to1} \psi^{(n)}(z) = \sum_{k=1}^\infty P[X=k]\cdot k(k+1)\dots(k+n-1)
$$
dove $\psi^{(n)}$ è la $n$-esima derivata (vale anche il caso $\infty=\infty$).
2. La distribuzione $P_X$ è unicamente determinata da $\psi$. 
3. $\psi$ è unicamente determinata da un insieme numebrabile di valori $\psi(x_i)$, $x_i \in [0,1]$, $i \in \mathbb{N}$. Se la serie che definisce $\psi$ converge per un qualche $z > 1$, allora:
$$
\lim_{z\to1} \psi^{(n)}(z) = \psi^{(n)}(1) < \infty \qquad \forall n \in \mathbb{N}
$$
In questo caso $\psi$ è univocamente determinata dalle derivate $\psi^{(n)}(1)$, $n \in \mathbb{N}$.

Una proprietà importante è la p.g.f di una variabile somma di variabili indipendenti è il prodotto delle rispettive p.g.f (somma $\implies$ convoluzione $\implies$ prodotto delle trasformate).

#### Teorema 
Se $X_1, \dots X_n$ sono variabili aleatorie indipendenti e a valori $\mathbb{N}_0$, allora:
$$
\psi_{X_1+\dots + X_n} = \prod_{i=1}^n \psi_{X_i}
$$
#### Dim
Scrivere il prodotto delle due p.g.f come [[Cauchy product]] e sfruttare l'indipendenza.
