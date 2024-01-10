# GMRES

The method GMRES stants for _Generalized Minimum RESidual_, è un metodo di [[Krylov subspace methods|Krylov]] in quanto cerca la soluzione $x_k$ minimizzando la norma euclidea del residuo nel sottospazio affine $W_k$:
$$
x_k = argmin_{v \in W_k} \Vert b-Av\Vert_2. \qquad \Vert r_k\Vert_2 = \min_{v \in W_k} \Vert b-Av\Vert_2
$$
L'[[Arnoldi iteration]] ci da una base ortonormale del $k$-esimo sottospazio di Krylov, dunque il vettore ottimo $v \in W_k = x_0 + \mathcal{K}_k(A,r_0)$, $v = x_0 + V_ky$
$$
r_k = b-Ax_k = b-A(x_0 + V_ky)  = r_0 -AV_ky
$$
usando la proprietà delle matrici $V$ ed $H$ dell'iterazione di Arnoldi ottengo:
$$
r_k = r_0 - V_{k+1}\hat H_ky
$$
ma siccome $V$ è una base ortgonormale del sottopazio di Krylov $K(A,r_0)$, il residuo iniziale non è altro che la prima colonna della matrice $V$, riscalato:
$$
r_k = V_{k+1}(\Vert r_0 \Vert_2e_1-\hat H_ky)
$$
Siccome $V_{k+1}$ ha colonne ortonormali, trovare al passo $k$ una soluzione che minimizza il residuo, è equivalente a risolvere il problema di minimizzazzione:
$$
\min_{y \in \mathbb{R}^k} \Vert \Vert r_0\Vert_2 e_1- \hat H_{k}y \Vert_2 
$$
che è un [[Problema dei minimi quadrati]] in dimensione $k$ (inferiore ad $n$!).

Dato che $W_n = \mathbb{R}^n$, se non è avvenuto breakdown prima, GMRES termina in al più $n$ passi (in artimetica esatta).

### Breakdown
Nel caso di breakdown al passo $m < n$, sappiamo che $AV_m = V_m H_m$ 
dunque 
$$
r_m = V_m(\Vert r_0\Vert e_1 -H_my)
$$
