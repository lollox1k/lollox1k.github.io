An Algorithm to compute a Orthonormal basis for a given [[Krylov subspace methods#Krylov subspace|Krylov subspace]], essentially using a Gramh-Smith procedure  


At a certain step $m \leq n$ **breakdown** wil happe, this means $w_m = 0$ and the process stops. 
At every step the orthonormal vectors $v_i$ $i=1,\dots,k+1$ can be stored in the matrix $V_{k+1} \in \mathbb{R}^{n\times (k+1)}$.

When $k < m$, before breakdown, holds:
$$
AV_k = V_{k+1}\hat H_k
$$
where $\hat H_k \in \mathbb{R}^{(k+1)\times k}$ is the matrix formed by the overlaps $h_{i,j}$. By construction, $\hat H_k$ is an _upper hessember matrix_. 

To prove the equality above, note that for every $j \leq k$, the following holds:
$$
Av_j = h_{1,j}v_1 + \dots + h_{j,j}v_j + h_{j+1,j} v_{j+1}
$$
For $k \leq m$ we have:
$$
V_k^TAV_k = H_k
$$
where $H_k \in \mathbb{R}^{k\times k}$ is the matrix $\hat H_k$ without the last row. 
To prove this, first consider the case $k=m$, i.e. breakdow has happened; we have $h_{m+1,m} = 0$, so that $AV_m = V_m H_m$. 
In general, when $k<m$ $V_k^T V_{k+1} = I_{k,k+1}$ (the $k$ identity matrix with an added coulumn of zeros). 
So in the end:
$$
V_k^T A V_k = V_k^TV_{k+1}\hat H_k = I_{k,k+1}\hat H_k = H_k
$$
> We can think of $H_k$ as the **projection** of $A$ onto the Krylov subspace using the base $V_k$.

## Arnoldi iteration to compute eigenvalues

We can emply arnoldi iteration to approximate eigenvalues of _big, sparse, non symmetric matrices_.

Let $A \in \mathbb{R}^{n\times n}$, consider the eigenvalue problem:
$$
Ax = \lambda x,
$$
Call the eigenvalues $\theta_i$ $i=1,\dots,k$ of the upper hessemberg matrix $H_k$, called _Ritz values_ of $A$. We can compute them using [[Fattorizzazione QR|QR method]], exploiting the fact that is upper hessember. The Ritz values are approximation of the eigenvalues of $A$.