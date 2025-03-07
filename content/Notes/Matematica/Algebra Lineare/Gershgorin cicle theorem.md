# Gershgorin cicle theorem

It's possibile to gain some information about eigenvalues locations easly using Gershgorin's theorem.

Let $D(c,r)$ denote the closed disk centered at $c \in \mathbb{C}$ of radius $r\in \mathbb{R}$.  

**Theorem** Let $A \in \mathbb{C}^{n\times n}$, then the eigenvalues of $A$ are all contained in the union of the _Gershgorin disks_:
$$
\bigcup _{i=1}^n D(a_{ii}, R_i) \quad R_i = \sum_{j=1, \, j \neq i} |a_{ij}|
$$
The disks are centered at the diagonal elements of $A$, and their radius is the sum of the modulus of the row elements, exept the diagonal one. 

**Remark** Since the spectrum of $A^h$ is the same, one can comput the gershgorin disks of $A^h$ and take the intersection with the disks of $A$ to improve the location exstimate.

**Proof** Consider an eigenvalue $\lambda$ and its corresponding norm $1$ eigevector $v$, so that $Av = \lambda v$. 
Let $v_i$, $i = 1,\dots,n$ be the biggest (in modulus) cordinate of $v$, then
$$
\sum_{j=1}^n a_{ij} v_j = \lambda v_i
$$
we now separate from the sum the diagonal term $a_{ii}v_i$ and rearrenge:
$$
\lambda v_i - a_{ii}v_i = \sum_{j=1\, j\neq i}^n a_{ij}v_j 
$$
we now use the fact that $v_i \geq v_j$, we divide and get:
$$
\lambda-a_{ii} \leq \sum_{j=1\, j\neq i}^n a_{ij} 
$$
now we take norms and use the triangle inequality:
$$
|\lambda -a_{ii}| \leq \sum_{j=1\, j\neq i}^n |a_{ij} | = R_i
$$
this is the definition of a closed disk centerd at $a_{ii}$ of radius $R_i$. $\square$

## Corollary

From this theorem follows easly that a _striclty diagonal dominant matrix_ is invertible, since all its eigenvalues are non-zero.

Also, an hermitian and diagonal dominant matrix is positive semidefinite.
