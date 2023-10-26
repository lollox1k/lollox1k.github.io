### Definitions
Let $(X_n)_{n\geq 0}$ be a [[Discrete time Markov chains|Markov chain]] with transition matrix $P$. Define
$$
H_i = \inf\{n \geq 0\,:\, X_n = i\} \quad \text{hitting time on } i
$$
$$
T_i = \inf\{n \geq 1\,:\, X_n = i\} \quad \text{first passage time to } i
$$
using the convention $\inf{\emptyset} = \infty$.
**Remark** They are different only if $X_0 = i$.

We can definte the $r$-th passage time to $i$, setting $T_i^{(0)}=0$ and for $r \geq 1$
$$
T_i^{(1)} = T_i \qquad T_i^{(r+1)} := \inf \{n > T_i^{(r)}\,:\, X_n = i\}
$$
and the excursion time beetween visits
$$
S_i^{(r)} := 
\begin{cases}
T_i^{(r)} - T_i^{(r-1)} \quad\text{ if } \quad T_i^{(r-1)} < \infty\\
0 \qquad \qquad \qquad\text{ otherwise }
\end{cases}
$$
this explain our choice for $T_i^{(0)}$.

The following lemma should be obvious.
**Lemma** For $r = 2,3,\dots$ the random variable $S_i^{(r)}$ is independent of $H_{T_i^{(r-1)}}$ and for all $n\geq 0$ 
$$
P_i(S_i^{(r)} = n\,|\, T_i^{(r-1)}< \infty) = P_i(S_i^{1}=n) = P_i(T_i = n)
$$
**Proof** Since $T_i^{r-1}$ is a [[Stopping times|stopping time]], by the [[Markov property|strong Markov property]] 
$$
\tilde X_n := X_{T_i^{(r-1)}+n} \quad Markov(\delta_i,P) 
$$
$$
\tilde T_i = \inf \{n \geq 1 \,:\, \tilde X_n = i\}
$$
using the definition of the excurtion time
$$
\{S_i^{(r)} = n\} = \{T_i^{(r)} - T_i^{(r-1)}=n \,,\, T_i^{(r-1)} < \infty\}
$$
$$
= \{\tilde T_i = n, T_i^{(r-1)} < \infty\}
$$
so the probability
$$
P_i(\{\tilde T_i = n\} \,|\, T_i^{(r-1)} < \infty) = P_i(T_i = n) = P_i(S_i^{(1)} = n) \quad\square
$$

Other useful definitions are:
$$
V_i = \sum_{n=0}^\infty \mathbb{1}_{X_n=i} \quad \text{number of visits to } i
$$
$$
f_i = P_i(T_i < \infty) \text{ return probability to }i
$$
$$
m_i = \mathbb{E}[T_i] \text{ mean return time to }i
$$
**Def** (Recurrent state) We say that the state $i$ is _recurrent_ if 
$$
i \text{ recurrent} \iff P_i(V_i = \infty) = 1
$$
a non-recurrent state is called _transient_.

There is a link beetween recurrent and and return probability.

**Lemma** For all $r \geq 0$, $P_i(V_i > r) = f_i^r$.
**Proof** By induction. The base case $r=0$ is true (with the convention $0^0 = 1$). Assume it holds for $r$. 
$$
P_i(V_i > r+1) = P_i(T_i^{(r+1)} < \infty) = P_i(T_i^{(r+1)}< \infty,\, T_i^{(r)}< \infty)
$$
or equivalently using the excurtion time
$$
= P_i(S_i^{(r+1)}< \infty, \, T_i^{(r)}< \infty)
$$
using the definition of conditional probability
$$
= P_i(S_i^{(r+1)}< \infty \,|\, T_i^{(r)}< \infty)P_i(T_i^{(r)}< \infty)
$$
$$
= \sum_{n\geq 0}  P_i(S_i^{(r+1)} = n \,|\, T_i^{(r)}< \infty)P_i(T_i^{(r)}< \infty)
$$
using the strong Markov property
$$
= \sum_{n \geq 0} P_i(T_i=n)P_i(T_i^{(r)}< \infty)
$$
$$
= P_i(T_i < \infty)P_i(T_i^{(r)}< \infty) = f_i\,f_i^r = f_i^{r+1} \quad \square
$$
since $T_i^{(r)} < \infty$ is the same event as $V_i > r$.


### Characterization 
**Theorem** We have the dichotomy:
1. se $P_i(T_i < \infty) = 1$, allora $i$ è _ricorrente_ e 
$$
\sum_{n=0}^\infty p_{ii}^{(n)} = \infty
$$
2. se $P_i(T_i < \infty) < 1$, allora $i$ è _transiente_ e
$$
\sum_{n=0}^\infty p_{ii}^{(n)} < \infty
$$

**Proof** The probability that the state $i$ is recurrent, i.e. the number $V_i$ of visits is infinite is
$$
P_i(V_i = \infty) = P_i\left(\bigcap_{r\geq 0}\{V_i > r\} \right) = \lim_{r\to\infty} P(V_i > r) = \lim_{r\to\infty} f_i^r = 1
$$
where we have used [[Continuity of mesure]] and the previous lemma.
Since $P_i(V_i=\infty) = 1$, we also know that
$$
\infty = \mathbb{E}_i[V_i] = \mathbb{E}_i\left[\sum_{n\geq 0} \mathbb{1}(X_n=i)\right] = \sum_{n\geq 0} P_i(X_n=i) = \sum_{n\geq 0} p_{ii}^{(n)}
$$
where we have used [[teorema di Fubini|Fubini's theorem]].

Doing the same computation for a state such that $P_i(T_i < \infty) < 1$ we get
$$
P_i(V_i = \infty) = \lim_{r\to\infty} f_i^r = 0
$$
computing the expected value we get
$$
\mathbb{E}_i[V_i] = \sum_{r\geq 0} P_i(V_i > r) = \sum_{r\geq 0} f_i^r = \frac{1}{1-f_i} < \infty
$$
but also
$$
\mathbb{E}_i[V_i] = \sum_{n\geq 0} p_{ii}^{(n)}
$$
and the theorem is proven. $\square$

**Corollary** Every state is either transient of recurrent.


### Class property

We can show that being recurrent or transient is a [[Class structure|class]] property.

**Theorem** Let $C \subseteq I$ be a communicating class. Then either all state in $C$ are transient or all are recurrent.

**Proof** Take any pair $i,j \in C$ and suppose $i$ is transient, let's show that $j$ is also transient. Since $i \leftrightarrow j$ then $\exists n,m \geq 0$ such that
$$
P_{ij}^{(n)} > 0 \quad \text{and} \quad P_{ji}^{(m)} > 0
$$
for all $r \geq 0$
$$
P_{ii}^{n+r+m} = (P^nP^rP^m)_{ii} = \sum_{l,k \in I} P^{(n)}_{il}P^{(r)}_{lk}P^{(m)}_{ki} \geq P^{(n)}_{ij}P^{(r)}_{jj}P^{(m)}_{ji}
$$
then
$$
\sum_{r\geq 0} P_{jj}^{(r)} \leq \frac{1}{P^{(n)}_{ij}P^{(m)}_{ji}} \sum_{r \geq 0}P_{ii}^{n+r+m} < \infty
$$
where we have used the fact that $i$ is transient, and the dichotomy. This proves that also $j$ is transient. $\square$ 

We have proven that if a state $i \in C$ is transient, then the whole class is transient. This means either state are all recurrent, or all transient. $\square$

**Theorem** Every recurrent class is closed.

**Proof** Let's show that if $C$ is open, then it's transient. 
Since $C$ is open, then $\exists i \in C$ and $\exists j \notin C$ such that $i \to j$ (but not $j\to i$ since $j \notin C$. This means there exist $n \geq 0$ such that $(P^n)_{ij} > 0$

$$
P_i(V_i > n| \exists m )
$$

**Theorem** Let $P$ be an irreducible recurrent markov chain. Then for every initial distribution $\mu$ every state is visited a.s:
$$
P(T_i < \infty) = 1
$$
**Proof** Using the w.m.p
$$
P(T_i < \infty) = \sum_{j \in I} P(T_i < \infty| X_0 = j)\mu_j
$$
$$
= \sum_{j \in I} P_j(T_i < \infty)\mu_j
$$
since $\sum_j \mu_j = 1$, if we prove that $P_j(T_i < \infty) = 1$ for all $j$ we have done.
We now use the recurrence hypotesis
$$
1 = P_j(V_j =\infty) 
$$
$$
= P_j(\sum_{n=0}^\infty \mathbb{1}(X_n = j) =\infty) 
$$
choose an arbitrary time $m \geq 0$
$$
= P_j(\sum_{n=0}^{m-1} \mathbb{1}(X_n = j) + \sum_{n = m}^\infty \mathbb{1}(X_n = j)=\infty) 
$$
since the first sum is less or equal to $m-1$ (a finite number)
$$
= P_j(\sum_{n = m}^\infty \mathbb{1}(X_n = j)=\infty)
$$
$$
\geq P_j(X_n = j, \exists n \geq m)
$$
$$
= \sum_{i \in I} P_j(X_n=j, \exists n\geq m|X_m =i)P_j(X_m=i)
$$
$$
= \sum_{i \in I}P_i(T_j < \infty)P_j(X_m=i)
$$
since the second terms add to one, this implies that
$$
P_i(T_j < \infty) = 1 \qquad \square
$$