# Algoritmo di Householder

L'algoritmo genera una matrice $H$ unitariamente simile ad $A$ in forma di Hessemberg superiore.

Come per la [[Fattorizzazione QR]] si fa uso dei [[Riflettore di Householder|riflettori di Householder]].

La novità rispetto a QR è applicare i riflettori sia a _sinistra_ che a _destra_.
$$
H = U^HAU \qquad U = U_1\dots U_{n-2}
$$
in $n-2$ step, in quanto sono le colonne in cui dobbiamo far comparire degli zeri.

Quindi al passo $k$ costruisco il riflettore elementare che annulla le componenti $k+2,\dots,n$ della $k$-esima colonna di $A$, e lascia invariate le prima $k$ righe:
$$
U_k = \begin{pmatrix}
I_k & 0 \\
0 & U_{n-k}
\end{pmatrix}
$$
viene poi moltiplicato anche a destra, lasciando invariate le prima $k$-colonne, creando una nuova matrice simile a quella del passo precedente.

Il costo computazionale è di $\frac{10}{3}n^3 + O(n^2)$ operazioni.

Nel caso di $A$ _hermitiana_, quando si applica il riflettore a destra si annullano gli elementi $k+2,\dots, n$ della $k$-riga, ottenendo una matrice _tridiagonale_, e il costo computazionale si riduce a $\frac{4}{3}n^3 + O(n^2)$.