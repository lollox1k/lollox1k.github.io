For Markov Chains, the past and the future are indipendent, given the present. This suggests looking at the Markov Chain with time running backwards. On the other end, [[Convergence to equilibrium for ergodic chains]] is an irreversible process. So we must start at equilibrium.

**Theorem** Let $P$ be irreducible and have an invariant distribution $\pi$. Suppose that $(X_n)_{n\geq 0} \sim Markov(\pi,P)$ define the reverse chain
$Y_n = X_{N-n}$. Then $(Y_n)_{0\leq n \leq N}$ is $Markov(\pi, \tilde P)$, where the new transition matrix is given by
$$
(\tilde P)_{ji} = \frac{\pi_i}{\pi_j}(P)_{ij} 
$$
and $\tilde P$ is also irreducible with invariant distribution $\pi$.

**Proof** First we check that $\tilde P$ is a stochastic matrix:
$$
\sum_i (\tilde P)_{ji} = \sum_i\frac{\pi_i}{\pi_j}(P)_{ij} = \frac{1}{\pi_j} \pi_j = 1 
$$
next we check that $\pi$ is invariant for $\tilde P$:
$$
\sum_j \pi_j (\tilde P)_{ji} = \sum_j \pi_j \frac{\pi_i}{\pi_j}(P)_{ij} = \pi_i
$$

To prove that $Y_n$ is $Markov(\pi,\tilde P)$ we use this [[Discrete time Markov chains|characterization]] of Markov Chains:
$$
P(Y_0 = i_0, \dots Y_N = i_N) = P(X_N = i_0, \dots X_0 = i_N)
$$
$$
= \pi_{i_N}p_{i_N, i_{N-1}}\dots p_{i_1, i_0}
$$
using the definition of $\tilde P$, $p_{i_1,i_0} = \frac{\pi_{i_0}}{\pi_{i_1}} \tilde p_{i_0,i_1}$
$$
= \pi_{i_N} \frac{\pi_{i_{N-1}}}{\pi_{N}} \tilde p_{i_{N-1},i_N} \dots = \pi_{i_0} \tilde p_{i_0,i_1}\dots \tilde p_{i_{N-1}, i_N}
$$
so that $Y \sim Markov(\pi, \tilde P)$. 
Irreducibility follows from reversing a given path. $\square$

