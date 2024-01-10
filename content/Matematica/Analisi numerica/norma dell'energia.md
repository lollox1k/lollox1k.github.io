# Norma dell'energia

Sia $A \in \mathbb{C}^{n\times n}$ una matrice _hermitiana defnita positiva_. Allora esiste unica la matrice $A^{\frac{1}{2}}$ soluzione del problema $X^2=A$. Una matrice hermitiana defnita positiva induce un prodotto scalere (non degenere), dunque anche una norma:
$$
\Vert x \Vert_A := \sqrt{\langle x, x \rangle_A} = \sqrt{x^HAx} = \Vert A^{\frac{1}{2}}x\Vert_2
$$
che viene detta _norma dell'energia_ o ($A$-norma), indotta dal $A$-prodotto scalare. 
Per la norma matriciale indotta dalla norma dell'energia vale il seguente risultato.
**Proposizione** Sia $M\in \mathbb{C}^{n\times n}$, si ha
$$
\Vert M \Vert_A = \Vert A^{\frac{1}{2}}MA^{-\frac{1}{2}}\Vert_2
$$
**Dim** Per definizione
$$
\Vert M \Vert_A = \max_{x, \Vert x \Vert_A=1} \Vert Mx \Vert_A
$$
usando la definizione della norma dell'energia:
$$
\max_{\Vert A^{1/2}x\Vert_2 = 1} \Vert A^{1/2}Mx\Vert_2 = \max_{\Vert y\Vert_2=1} \Vert A^{1/2}M A^{-1/2}y\Vert_2 = \Vert A^{1/2}MA^{-1/2}\Vert_2 \quad \square
$$

**Proposizione** Da questo fatto segue che se $AM$ è ancora hermitiana, si ha
$$
\Vert M \Vert_A = \rho(M)
$$
inoltre, se $M$ è normale, $\Vert M \Vert_A=\Vert M \Vert_2$.
**Dim** La cosa da notare è che $A^{1/2} = A^{-1/2}A$, dunque possiamo scrivere:
$$
\Vert M \Vert_A = \Vert A^{-1/2}AMA^{-1/2}\Vert_2
$$
siccome è $AM$ è hermitiana, tutto lo è, dunque
$$
= \rho(A^{-1/2}AMA^{1/2}) = \rho(A^{1/2}MA^{-1/2}) = \rho(M)
$$
siccome sono simili. Inotre se $M$ è normale, so che $\Vert M \Vert_2 = \rho(M)$. $\square$

Segue un'interessante disuguaglianza sul [[Numero di condizionamento di una matrice|numero di condizionamento]]:
**Osservazione** Sia $AM$ e $AM^{-1}$ hermitiane. Allora vale
$$
\mathcal{K}_A(M) \leq \mathcal{K}_2(M)
$$
**Dim** Dalla proposizione precedente sappiamno che $\Vert M \Vert_A = \rho(M) \leq \Vert M \Vert _2$, stessa cosa per $M^{-1}$. Facendo il prodotto si ottiene la tesi. $\square$

