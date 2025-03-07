#### Combinazione conica
Praticamente una combinazione lineare con coefficienti non negativi. La combinazione conica di un insieme di vettori viene indicata come:
$$
Q = cone(v_1,v_2,\dots, v_n) 
$$
Alcunche proprietà:
1. è un insieme non vuoto, infatti $0 \in Q$ 
2. è un _insieme convesso_:
facciamo vedere che $\lambda x_1 + (1-\lambda)x_2 \in Q$ $\forall x_1,x_2 \in Q$ $\lambda \in [0,1]$. Siccome $x_1,x_2 \in Q$ possono essere scritto come combinazione conica dei vettori generatori $v$:
$$
x_1 = \alpha^Tv \qquad x_2 = \beta^Tv \qquad \alpha,\beta \geq 0
$$
Per far vedere che anche combinazioni convesse sono in $Q$, basta far vedere che può essere scritto come combinazione conica dei vettori generatori. Usiamo la notazione classica dei prodotti scalari: $v^tu = \langle v,u \rangle$ 
$$
\lambda \langle \alpha, v \rangle + (1-\lambda)\langle \beta, v \rangle
$$
$$
\langle \lambda \alpha, v \rangle + \langle (1-\lambda)\beta, v \rangle = \langle \lambda \alpha + (1-\lambda)\beta, v\rangle
$$
ovviamente $\lambda \alpha + (1-\lambda)\beta \geq 0$. $QED$

## Teorema
La definizione di combinazione conica può essere interpretata come un poliedro, con $\lambda$ come variabili. Vale la rappresentazione:
$$
cone(v_1,\dots,v_n)= \{x \in \mathbb{R}^n \vert Ax \leq 0\}
$$
per una certa matrice $A$. 
### Dim
è abbastanza naturale, si procede con l'[[Eliminazione di Fourier-Motzkin]] e si arriva ad un sistema di disequazioni omogeneo in $\lambda$. Le $x$ (che fanno il ruole delle $b$ costanti) si cancellano, dovendo trasformare le equazioni in due disequazioni con segno opposto:
$$
\lambda^Tv = x \quad
\begin{cases}
\lambda^T \leq x \\
-\lambda^Tx \leq -x
\end{cases}
$$





