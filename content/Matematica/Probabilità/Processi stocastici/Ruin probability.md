
The aim of this note is to study the behaviour of the gambler's ruin, a finite state [[catene di Markov|Markov chain]] with absorting state at its ends.

**Def** Gambler's ruin chain. Let $(X_n)_{n\geq 0}$ be the MC with state space $S = \{0,1,\dots, N\}$ and transition probabilities $P(X_{n+1}=k+1|X_n=k) = p$ and $P(X_{n+1}=k-1|X_n=k) = q$, with the boundary conditions $P(X_{n+1}=0|X_n = 0) = P(X_{n+1}=N|X_n = N) = 1$.

The value $X_n$ is the fortune of the player, if it reaches the state $0$ he is ruined! 

The following are interesting questions:
1. What is the probability of ruin starting from $X_0 = i$.
2. What is the average lenght of the game?

Let's define the event _ruin_:
$$
R := \bigcup_{n\geq 0} \{X_n = 0\} 
$$
which is the same as $h_i := P(H^0 < \infty\vert X_0 = i)$ using the notation in [[Hitting probability and mean hitting times]].

Using [[Markov property]] we obtain the following system of equations:
$$
\begin{cases}
h_0 = 1\\
h_1 = qh_0 + ph_2\\
\dots\\
h_n = qh_{n-1} + ph_{n+1}\\
\dots\\
h_N = 0
\end{cases}
$$

## Solving RHEs via ansatz
we solve this systems of linear equations from an ansatz:
$$
h_k = Ca^k
$$
substituting we get
$$
Ca^n = qCa^{n-1} + pCa^{n+1}
$$
assuming $C \neq 0$ 
$$
a = q + p a^2 \qquad a^2 -\frac{1}{p}a + \frac{q}{p} = 0
$$
solving for $a$ 
$$
\frac{1}{2p} \pm \frac{1}{2}\sqrt{\frac{1}{p^2} -4\frac{q}{p}}
$$
$$
\frac{1}{2p}(1 \pm \sqrt{1-4qp})
$$

we get two values for $a = \{1, \frac{q}{p}\}$. Since we are solving linear equations the general solution has the form
$$
h_k = C_1a_1^k + C_2a_2^k = C_1 + C_2\left(\frac{q}{p}\right)^k
$$
let's find $C_1$ and $C_2$ using the boundary conditions
$$
\begin{cases}
h_0 = C_1 + C_2 = 1 \\
h_k = C_1 + C_2\left(\frac{q}{p}\right)^N = 0\\
\end{cases}
$$
$$
(1-C_2) + C_2\left(\frac{q}{p}\right)^N = 0
$$
$$
C_2 = \frac{1}{1-\left(\frac{q}{p}\right)^N} \qquad C_1 = 1-\frac{1}{1-\left(\frac{q}{p}\right)^N} = \frac{-\left(\frac{q}{p}\right)^N}{1-\left(\frac{q}{p}\right)^N}
$$
and the solution we were looking for is
$$
h_k = \frac{\left(\frac{q}{p}\right)^k-\left(\frac{q}{p}\right)^N}{1-\left(\frac{q}{p}\right)^N}
$$

**Remark** In the limit $N\to \infty$ the ruin probability is simply a geometric random variable.

For the symmetric case $p=q=1/2$ this is not enough, since we only get $a=1$. 
First note that in the symmetric case, our difference equations is a discretization of the laplace equation:
$$
h_n = \frac{h_{n+1}+h_{n-1}}{2}
$$
rearranging
$$
h_{n+1}-2h_n + h_{n-1} = 0
$$
which is the finite difference formula for the second derivative. Linear functions solve laplace equation in $1$d, so an ansatz is
$$
g(k) = C_2k
$$
and a general solution is
$$
h_k = C_1 + C_2k
$$
using the boundary conditions we get
$$
h_k = 1 - \frac{k}{N}
$$
