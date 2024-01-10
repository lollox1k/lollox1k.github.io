**Def** A Markov chain $(X_n)_{n\geq0}$ is said to admit a _limiting distribution_ if the following conditions are satisfied:
1. the limits
$$
\pi_j := \lim_{n\to\infty} P(X_n=j \vert X_0=i) 
$$
exists for all $i,j \in I$, and
2. they form a probability distribution on $I$, i.e.
$$
\sum_{j \in I} \lim_{n\to\infty} P_i(X_n=j) = 1, \quad \forall i \in I
$$
**Remark** If condition $1$ is satisfied and the state space $I$ is finite, then condition $2$ is always satisfied (in this case we can exchange the limit with the summation.)

**Example** We can compute the limiting distribution of the two state MC with transition matrix
$$
P =
\begin{pmatrix}
1-a & a \\
b & 1-b 
\end{pmatrix}
$$
we need to compute $\lim_{n\to\infty} P^n$, to do so we can diagonalize it and get
$$
P^n =
\frac{1}{a+b}
\begin{pmatrix}
b + a(1-a-b)^n & a(1-(1-a-b)^n)\\
b(1-(1-a-b)^n) & a+b(1-a-b)^n \\
\end{pmatrix}
$$
if $a=b=0$ then $P=I$, we have a trivial MC. With the hypotesis $(1-a-b) <1$ the limit exists 
$$
\lim_{n\to\infty} P^n = 
\frac{1}{a+b}
\begin{pmatrix}
b  & a \\
b & a \\
\end{pmatrix}
= 
\begin{pmatrix}
\frac{b}{a+b}  & \frac{a}{a+b} \\
\frac{b}{a+b}  & \frac{a}{a+b} \\
\end{pmatrix}
$$
which also show that the limiting probability distribution doesn't care about the starting state $X_0$.


