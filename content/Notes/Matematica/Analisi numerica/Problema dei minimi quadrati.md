# Least square problem

Assumiamo $A \in \mathbb{C}^{m\times n}$ di rango massimo ($n$) con $m\geq n$. 
Il sistema $Ax=b$ è pertanto _sovradeterminato_, ed in generale non esiste una soluzione $x \in \mathbb{C}^n$. Il meglio che si può fare è minimizzare la norma del residuo:
$$
x^* = \text{argmin}_{x \in \mathbb{C}^n}||b-Ax||_2 \qquad \gamma = ||b-Ax^*||_2
$$
Ciò significa trovare la soluzione nell'immagine $range(A)$ più vicino a $b$.

Decomponiamo il termine noto $b =b_1 + b_2$ con $b_1 \in range(A)$ e $b_2 \in range(A)^{\perp}$.  Se $b \notin range(A)$ necessariamente $b_2 \neq 0$. Per l'ortogonalitèà tra $b_1, Ax$ e $b_2$ 
$$
||b_1 + b_2 -Ax||_2^2 = ||b_1 - Ax||_2^2 + ||b_2||_2^2
$$
è chiaro che minimizzare questa quantità significa risolvere il sistema $Ax=b_1$. Si ha $\gamma = ||b_2||_2$.

## Equazioni normali

**Proposizione** $range(A)^\perp = \ker(A^H)$.
**Dim** $z \in range(A)^\perp$ significa che $0 = (Ax)^Hz = x^H A^H z \quad\forall x$. Questo implica che $A^Hz = 0$, ovvero $z \in \ker(A^H)$. $\square$

Con questa caratterizzazione, stiamo richiedendo che il residuo sia nel ker di $A^H$ ovvero:
$$
A^H(b-Ax)=0
$$
Questo sistema definisce le cosidette _equazioni normali_:
$$
A^HAx = A^Hb 
$$
$$
x = (A^HA)^{-1}A^Hb
$$
$$
x = A^+b
$$
dove abbiamo introdottoa la _pseudo inversa di Moore-Penrose_ $A^+$.
**Osservazione** La matrice $A^HA \in \mathbb{C}^{n\times n}$ è invertible siccome abbiamo supposto $A$ di rango massimo.

**Osservazione** La pseudo inversa è un'inversa sinistra:
$$
A^+A = (A^HA)^{-1}A^HA = I_n
$$
> Risolvere usando le equazioni normali è pericoloso infatti $\mathcal{K}(A^HA) = \mathcal{K}(A)^2$.

## Soluzione tramite fattorizzazione QR

Usiamo la [[Fattorizzazione QR]] per riscrevere le equazioni normali:
$$
A^H(b-Ax) = R^HQ^H(b-QRx) = R^H(Q^Hb-Rx) = 0
$$
e risolvere il sistema triangolare con le matrici della fattorizzazione ridotta:
$$
R_nx = Q_n^Hb = c_1
$$
Infatti le prime $n$ colonne di $Q$ sono una base ortonormale di $range(A)$, mentre le restanti $m-n$ del suo ortononale. Dunque:
$$
Q^Hb = 
\begin{pmatrix}
c_1 \\ c_2
\end{pmatrix}
\qquad R = 
\begin{pmatrix}
R_n \\ 0
\end{pmatrix}
$$
Partendo invece dalla norma del residuo
$$
x^* = argmin_{x \in \mathbb{C}^n} ||b-QRx|| = argmin_{x \in \mathbb{C}^n} ||Q^Hb-Rx||
$$
siccome $Q^H$ è unitaria non cambia la norma $2$. Se decomponiamo $b$ ottiemo:
$$
\gamma = ||Q^Hb - Rx^*|| = ||c_2||
$$
quindi se calcoliamo la fattorizzazione completa sappiamo anche calcolare $\gamma$ direttamente.

