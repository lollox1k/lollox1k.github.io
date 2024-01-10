

**Def** A Markov Chain $(X_n)_{n\geq 0}$ is said to admin a **limiting probability distribution** if the following conditions are satisfied:
1. the limits
$$
\lim_{n\to\infty} P_i(X_n=j)
$$
exists for all states $i,j \in I$ and are indipendent from the starting state $i$, and
2. 
$$
\sum_{j \in I} \lim_{n\to\infty} P_i(X_n=j) = 1
$$
for all $i \in I$.

**Remark** Condition $2.$ is always satisfied in the case of a finite state space $I$, provided that the limits exists (codition $1.$) since we can exchange then limit and then (finite) summation.

For intuition, think of a finite Markov Chain with its transition matrix being an $n\times n$ stochastic matrix. What happens if we start from any vector $v_0$, and reapply the right matrix multiplication $v_{n+1} = v_n P$? in the limit $n\to \infty$ we expect $v_n$ to be in the eigenspace corresponding to the eigenvalue of greatest absulute value. But using [[Gershgorin cicle theorem]] it's easy to see that the spectrum of a stochastic matrix is limited to value $1$, and such eigenvalue exists since in any stochastic matrix the vector $(1,1,1\dots)^T$ has eigenvalue $1$ (every row sums to one and $\sigma(P)=\sigma(P^T)$).

Then it's natural to define the following:

**Def** (Stationary measure) We say that a measure $\lambda = (\lambda_i\,:\, i \in I)$ is an **invariant measure** of the Markov Chain with transition matrix $P$ if it solved the LHE:
$$
\lambda = \lambda P
$$
if $\sum_i \lambda_i = 1$ it's called an **invariant probability distribution**.

We now show that if a _finite_ Markov Chain admits a limiting probability distribution (even if it depends on the starting state $i$), then the limiting distribution is also _stationary_.

**Theorem** Let $I$ be _finite_. Suppose that for some $i \in I$ the following limits exists
$$
P_i(X_n = j) = p_{ij}^{(n)} \to \pi_j \qquad \forall j \in I
$$
then $\pi = (\pi_i \,:\, i \in I)$ is an invariant distribution.
**Proof** First we check that it's normalized
$$
\sum_{j\in I} \pi_j = \sum_{j\in I} \lim_{n\to\infty} p_{ij}^{(n)} = \lim_{n\to\infty} \sum_{j\in I}  p_{ij}^{(n)} = 1
$$
and
$$
\pi_j = \lim_{n\to\infty} p_{ij}^{(n)} = \lim_{n\to\infty}\sum_{k \in I} p_{ik}^{(n-1)}p_{kj}= \sum_{k \in I} p_{kj}\lim_{n\to\infty}p_{ik}^{(n-1)} = \sum_{k\in I}p_{kj}\pi_j
$$
where the exchanges are justified by the finiteness of the summation. $\square$

So in general if the state space is infinite, the limiting distribution are not stationary distribution. Consider the symmetric random walk in $\mathbb{Z}$, the limiting distribution are $p_{ij}^{(n)} \to 0$, which is stationary, but not a probability measure!

Other possibilities are:

- Stationary distribution may not be unique if the Markov chain is not irreducible, since any _convex combination_ of each class is a new valid stationary distribution. Trivial example is $P = Id$ (any distribution is invariant). Another counterexample is if the chain is irreducible but _transient_: consider the one dimensional RW with transition probabilities $p\neq q$, then we have two stationary measures: $\lambda_i = 1$ and $\mu_i = (p/q)^i$. 
- Stationary distribution may not exist, (es. symmetric walk in $\mathbb{Z}$)
- Limiting distribution do not exist if the Markov chain is periodic, a trivial example is the MC with transition matrix
$$
P=
\begin{pmatrix}
0 & 1 \\
1 & 0
\end{pmatrix}
$$

>What are the conditions such that the limiting distribution exists? When it's unique?
>When does a stationary distribution exists? When it's unique?

The best we can hope is that the limiting distribution exists, and it converges to the unique stationary distribution.

For a fixed state $k$, we define for each $i$ the expected time spent in $i$ between visits to $k$:
$$
\gamma_i^k := \mathbb{E}_k\left[ \sum_{n=1}^\infty \mathbb{1}(X_n=i, n \leq \tau_k^+)\right]
$$
**Oss** Observe that
$$
\sum_{i \in I}\gamma_i^k = 1 + \sum_{i \in I\,:\, i \neq k} \mathbb{E}_k[\text{ \# of visits to i before returning to }k]
$$
$$
= 1 + \mathbb{E}_k[T_k-1] = \mathbb{E}_k[T_k]
$$

**Theorem** (Existence of an invariant measure) Let $P$ be _irreducible_ and _recurrent_. Then
1. $\gamma_k^k = 1$
2. $\gamma^k = (\gamma_i^k \,:\, i \in I)$ is invariant (i.e. satisfies $\gamma^k = \gamma^kP$)
3. $0 < \gamma_i^k < \infty$ for all $i \in I$.

**Proof** $1.$  It follows from the definition. 
$2.$ Exchanging the expectetion value (the exchange is justified by MON) we get:
$$
\gamma_i^k = \sum_{n=1}^\infty P_k(X_n=i, n \leq \tau_k^+)
$$
Let's check that $\gamma^k$ is invariant:
$$
\sum_{i \in I} \gamma_i^kp_{ij} = \sum_{i\in I} \sum_{n=1}^\infty P_k(X_n=i, n \leq \tau_k^+)p_{ij}
$$
now the event $\{n \leq \tau_k^+\}$ depends only on information up to time $n-1$, since:
$$
\{n \leq \tau_k^+\} = \{X_1 \neq k, X_2 \neq k, \dots, X_{n-1} \neq k\}
$$
thus, using the [[Markov property]] 
$$
P_k(X_{n+1}=j\vert X_n=i,\, n \leq \tau_k^+) = P_k(X_{n+1}=j\vert X_n=i) = p_{ij}
$$
using this identity
$$
= \sum_{i\in I} \sum_{n=1}^\infty P_k[\mathbb{1}(X_n=i, n \leq \tau_k^+)]P_k(X_{n+1}=j\vert X_n=i,\, n \leq \tau_k^+)
$$
$$
= \sum_{i\in I} \sum_{n=1}^\infty P_k(X_{n+1}=j, X_n=i,\, n \leq \tau_k^+)
$$
$$
=  \sum_{n=1}^\infty P_k(X_{n+1}=j,\, n \leq \tau_k^+)
$$
$$
=  \sum_{n=1}^\infty P_k(X_{n+1}=j,\, n +1\leq \tau_k^+) +   \sum_{n=1}^\infty P_k(X_{n+1}=j,\, n = \tau_k^+)
$$
$$
= \gamma_j^k - P_k(X_1 = j, 1 \leq \tau_k^+) = \gamma_j^k - p_{kj}
$$
the other term is
$$
\sum_{n=1}^\infty P_k(X_{n+1}=j\vert\, n = \tau_k^+)P_k(n = \tau_k^+)
= p_{kj}\sum_{n=1}^\infty P_k(n = \tau_k^+) = p_{kj}
$$
where $\sum_{n=1}^\infty P_k(n = \tau_k^+) = P_k(\tau_k^+ < \infty) = 1$ since the chain is recurrent.

$3.$ Since the chain is irreducible, for each state $i$ there exists $n,m > 0$ such that $p_{ik}^{(n)}, p_{ki}^{(m)} > 0$, then $\gamma^k = \gamma^k P^{(n)}$ and $\gamma^k = \gamma^k P^{(m)}$
$$
\gamma_i^k = \sum_{j\in I} \gamma_j^k p_{ji}^{(m)} \geq \gamma_k^kp_{ki}^{(m)} = p_{ki}^{(m)} > 0
$$
$$
1 = \gamma_k^k = \sum_{j \in I} \gamma_j^kp_{jk}^{(n)} \geq \gamma_i^k p_{ik}^{(n)}, \qquad \gamma_i^k \leq \frac{1}{p_{ik}^{(n)}} < \infty
$$
And our theorem is proven. $\square$

Clearly if we scale by a positive costant we get a new invariant mesure. 
If this invariant measure is normalizable, then we can find an invariant probability distribution. This is possibile if the chain is _positive recurrent_.

Let $P$ be _irreducible_. Then the following conditions are equivalent:
1. All states are positive recurrent.
2. Some state is positive recurrent.
3. There exists an invariant distribution $\pi$.
Moreover, when $3.$ holds we have $\pi_i = \frac{1}{\mathbb{E}_i[\tau_i^+]}$

**Proof** $1. \implies 2.$ is obvious. (we include this to show that positive recurrence is also a class property!).
$2. \implies 3.$ Call $k$ a recurrent state. Since a this state is recurrent and the chain irreducible, then the vector $\gamma^k$ is an invariant measure, and since $k$ is positive recurrent it's also normalizalble, so that 
$$
\pi_i := \frac{\gamma_i^k}{\mathbb{E}_k[\tau_k^+]}
$$
is an invariant distribution.
$3. \implies 1.$ Since $\pi$ is an invariant distribution
$$
\sum_i \pi_i = 1
$$
so that there must exists at least one $\pi_k > 0$. But since the chain i irreducibile this implies that $0 < \pi_i < \infty$ for all $i \in I$. Choose any $k$ and set $\lambda_i := \frac{\pi_i}{\pi_k}$, this is an invariant measure of an irreducible chain, so that
$$
\lambda_i \geq \gamma_i^k, \qquad\text{ for all }i
$$
but then
$$
\mathbb{E}_k[\tau_k^+] = \sum_i \gamma_i^k \leq \sum_i \lambda_i = \sum_i \frac{\pi_i}{\pi_k} = \frac{1}{\pi_k} < \infty \quad \square
$$



**Theorem** (Uniqueness of an invariant measure). Let $P$ be _irreducible_ and let $\lambda$ be an invariant measure for $P$ with $\lambda_k = 1$. Then $\lambda_i\geq \gamma_i^k$ for all $i \in I$. If $P$ is _recurrent_ then $\lambda = \gamma^k$, so that the invariant measure is unique up to a positive constat facor (we set $\lambda_k=1$).

**Proof** For each $i \in I$ we have
$$
\lambda_i = \sum_j \lambda_j p_{ji} = p_{ki} + \sum_{j \neq k}\lambda_j p_{ji}
$$
we use the same strategy in the proofs of [[Hitting probability and mean hitting times]], repeated substitution:
$$
= p_{ki} + \sum_{j \neq k}\left(p_{kj} + \sum_{z \neq k}\lambda_z p_{zj}\right) p_{ji}
$$
$$
= p_{ki} + \sum_{j\neq k} p_{kj}p_{ji} + R
$$
where $R \geq 0$ is a positive quantity. By repeating this substitution one gets:
$$
\geq P_k(X_1 = i) + P_k(X_2 = i, n \leq \tau_k^+) + \dots
$$
taking the limit, and exchanging expected value and sum by (MON) on gets the definition of $\gamma_i^k$.

If in addition $P$ is also recurrent, then $\gamma^k$ is also stationary, we can define a new stationary measure
$$
\mu := \lambda - \gamma^k 
$$
(we can do this since $\lambda \geq \gamma^k$), but since they agree on state $k$ $\mu_k = 0$, so by our previou theorem point $3.$ $\mu_i = 0$ for all $i \in I$, so that $\lambda = \gamma^k$. $\square$

