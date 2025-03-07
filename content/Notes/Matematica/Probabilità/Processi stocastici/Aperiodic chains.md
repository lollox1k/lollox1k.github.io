
Consider the irreducible two-state chain with stochastic matrix
$$
P = 
\begin{pmatrix}
0 & 1 \\
1 & 0 \\
\end{pmatrix}
$$
it's clear that the limits $(p^n)_{ij}$ don't exists. This chain has a period of two.

**Def** A state $i \in I$ is called _aperiodic_ if $(P^n)_{ii} > 0$ for all $n$ sufficienlty large. 

This is the same as $P$ is a regular matrix.

An equivalent definition, more easy to check, is the following:

**Proposition** If there exists $n_1,\dots, n_k > 0$ such that $p^{n_j}_{ii}> 0$ for all $j \in 1,\dots,k$, and 
$$
1 = \gcd \{n_1,\dots, n_k\}
$$
then the state $i$ is aperiodic.

**Proof** This follows from the fact that, provided $n$ is big enough, we can always find $a_1,\dots, a_k \in \mathbb{N}$ such that ([[Bezou's lemma]])
$$
n = a_1n_1 + \dots a_kn_k
$$
so that, using Chapman-Kolmogorov
$$
(p^n)_{ii} \geq (p^{a_1n_1})_{ii}\dots (p^{a_kn_k})_{ii} > 0, \quad \square
$$
Also, the period of a state is a [[Class structure|class property]]:

**Proposition** If $i \leftrightarrow j$ then $i$ and $j$ have the same period.
**Proof** Call the period of state $d_i$ and $d_j$ respectivly. There exists $r,s \geq 0$ such that $(P^r)_{ij}, (P^s)_{ji} > 0$. 
We know that
$$
(P^{r + s})_{ii} \geq (P^r)_{ij}(P^s)_{ji} >0
$$
so that $d_i | r+s$. Suppose $d_j | k$, then
$$
(P^{k+r+s})_{ii} \geq (P^r)_{ij}(P^k)_{jj}(P^s)_{ji} > 0
$$
so that $d_i | k+r+s$ but since it divides also $r+s$, this means that
$$
d_j | k \implies d_i |k
$$
so that $d_i \leq d_j$. By swapping $i$ and $j$ we get our result. $\square$


Another useful thing is that if $i$ is an aperiodic in an irreducibile chain, then for evert $j,k \in I$ $(P^n)_{ij} >0$ for $n$ large enough (The matrix $P^n$ has all positive entries, i.e. it's regular).
**Proof** 
$$
(P^{n+r+s})_{jk} \geq (P^r)_{ji}(P^n)_{ii}(P^s)_{ik} > 0 \quad \square
$$

