We have discussed the existence and uniqueness of a stationary distribution for a Markov Chain in [[Long run behavior of Markov Chains]]. We have also shown that in a _finite_ Markov Chain, if for some $i$ the limits
$$
(p^n)_{ij} \to \pi_j
$$
then the limiting distribution it's also stationary. We now investigate the conditions needed for the convergence to the (unique) stationary distribution.

First a brief summary:

If $P$ is _recurrent_ then there exists at least one invariant measure. 
If we add _irreducibility_, then using the lemma for invariant measure on irreducible chains, the invariant measure is unique up to a scaling factor. 

These results rely on the vector $\gamma^k$, which is normalizable if the chain is _positive recurrent_ for a state $k$, since $\sum_{i} \gamma_i^k = \mathbb{E}_k[\tau_k^+]$, also an irreducible chain is positive recurrent iff it admits an invariant distribution. (An invariant measure is not sufficient, the conterexample is the symmetric r.w. in Z with invariant measure $\lambda_i = 1$, the chain is null recurrent.)

**Theorem** Let $P$ be an _ergodic_ chain (irreducible, [[Aperiodic chains|aperiodic]] and positive recurrent), then for any starting distribution $\lambda$, for all $i,j$ 
$$
P(X_n = i) \xrightarrow{n\to\infty} \pi_i
$$

**Proof** The main idea is _coupling_ (by Doblin 1937). Let $(X_n)_{n\geq 0} \sim Markov(\lambda, P)$ and  $(Y_n)_{n\geq 0} \sim Markov(\pi, P)$

Fix a reference state $b \in I$, and define the stopping time 
$$
T := \inf \{n \geq 0\,:\, X_n = Y_n = b\}
$$
**Step 1** We show that $P(T < \infty) = 1$, for this we need both irreducibility (obvious) and also aperiodicity (less obvious). 
Consider the process $W_n := (X_n, Y_n)$ with state space $I \times I$, and transition probabilties
$$
\tilde p_{(i,j) (k,l)} = p_{ij}p_{kl}
$$
and initial distribution $\mu_{(ij)} = \lambda_i \pi_j$. Since $P$ is aperiodic, for all state $i,j,k,l$ we have
$$
(\tilde P^n)_{(i,j)(k,l)} = (P^n)_{ij}(P^n)_{kl} > 0
$$
this follows from the property of [[Hadamard's product]]: $(A\odot B)^n = A^n\odot B^n$
for $n$ large enough, so that $\tilde P$ is irreducibile. Also, one can check that $\tilde\pi_{(i,j)} := \pi_i\pi_j$ is an invariant distribution, so that $W_n$ is also positive recurrent.

We have a recurrent irreducibile markov chain, this means that for any initial distribution [[Recurrence and transience|every state is visited a.s.]], in particular the state $(b,b)$, so that
$$
P(T< \infty) = 1
$$
and the chains meet a.s.

Now the magick trick

$$
P(X_n = j) = P(X_n = j, n \geq T) + P(X_n = j, n < T)
$$
$$
= P(Y_n = j, n\geq T) + P(X_n = j, n < T) + P(Y_n = j, n < T) -P(Y_n = j, n < T)
$$
$$
= P(Y_n = j) + P(X_n = j, n < T)-P(Y_n = j, n < T)
$$
$$
= \pi_j + P(X_n = j, n < T)-P(Y_n = j, n < T)
$$
the last two terms tend to zero when $n\to\infty$, since $T$ is finite a.s:
$$
P(X_n = j, n < T) \leq P(n < T) \xrightarrow{n\to\infty}0
$$
so that
$$
P(X_n = j) \xrightarrow{n\to\infty} \pi_j \qquad \square
$$




