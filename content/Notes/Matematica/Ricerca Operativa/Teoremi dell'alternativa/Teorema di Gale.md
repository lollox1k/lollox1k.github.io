Dall'[[Eliminazione di Fourier-Motzkin]], segue che un poliedro $P$ definito come al solito:
$$
P := \left\{x \in \mathbb{R}^n \vert Ax\leq b\right\}
$$
è _ammissibile_, ovvero non vuoto se e solo se una volta che ho eliminato tutte le variabili arrivo ad una disequazione implicata non falsa della forma:
$$
a \leq b, \qquad a,b\in\mathbb{R}^n
$$
se questa è falsa, ovvero $a > b$, posso tramite combinazioni coniche giungere ad una qualunque contradizzione, prendiamo ad esempio:
$$
0_n \leq -1
$$
Quindi il poliedro $P$ è ammissibile se e solo se il sistema:
$$
\lambda^T(A,b)=(0_n,-1), \qquad \lambda \geq 0
$$
non ammette soluzioni. Questo sistema non è altro che quanto detto precedentemente: si arriva ad una disequazione implicata tramite combinazione convessa ($\lambda \geq 0$), ed ad una contraddizione.

Questo fatto può essere riscritto in un'altra forma, nota come teorema di Gale.

# Teorema di Gale
Il sistema:
$$
Ax \leq b
$$
è ammissibile se e solo se il sistema
$$
y^TA=0 \qquad y^Tb < 0 \qquad y \geq 0
$$
non è ammissibile.

### Dim 
è solo una riscrittura di quanto detto prima, con la piccola modifica che:
$$
y^TA = 0, \quad y^Tb =-1 \iff y^TA = 0, \quad y^Tb < 0 
$$
Un verso è banale, per l'altro basta notare che possiamo riscalare liberamente il vettore $y^T$ per una costante positiva, la prima condizione continua a valere ed ottenere $-1$. $\square$
