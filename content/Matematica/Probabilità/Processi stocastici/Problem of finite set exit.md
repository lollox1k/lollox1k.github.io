**Theorem** Let $J \subset I$ a finite subset of the state space of an irreducible [[Discrete time Markov chains|Markov chain]] $(X_n)_{n\geq 0}$. Define the the [[Stopping times|stopping time]]
$$
\tau := \inf\{n \geq0\,:\, X_n \notin J\}
$$
Then there exists constant $c_1,c_2 \in (0,\infty)$ such that 
$$
P_i(\tau > r) \leq c_1 e^{-c_2r}, \qquad \forall r \in \mathbb{N}
$$
in particular $P_i(\tau < \infty)=1$ and $\mathbb{E}_i[\tau] < \infty$.

**Proof** Let $T$ such that $\forall i \in J$ $\exists n \leq T$ so that there is a path $i=i_0, i_1, \dotsm i_{n-1}, i_n$ with just $i_n \notin J$ and positive probability:
$$
p_{i_0,i_1}\dots p_{i_{n-1}, i_n} > 0
$$
For all $i \in J$ let
$$
q_i := P_i(\tau \leq T) \geq P_i(X_0=i_0, \dots X_n=i_n) = p_{i_0,i_1}\dots p_{i_{n-1}, i_n} > 0
$$
Let 
$$
q := \min \{q_i: i \in J\}
$$
$$
P_i(\tau > n) = \sum_{j \in I} P_i(\tau > n, X_{n-T}=j)
$$
$$
\{\tau >n\} = \{\tau > n-T\} \cap \{\forall t \in [n-T,n], X_t \in J\}
$$
call the last event $B$.
Then
$$
P_i(\tau > n) = \sum_{j \in J} P_i(\tau > n-T, B,X_{n-T}=j)
$$
$$
= \sum_{j \in J} P_i(B\,|\, \tau > n-T, X_{n-T}=j)P_i(\tau > n-T, X_{n-T}=j)
$$
$$
= \sum_{j \in J} P_i(B\,|\, X_{n-T}=j)P_i(\tau > n-T, X_{n-T}=j)
$$
using the [[Markov property]]
$$
= \sum_{j \in J} P_j(\forall t \in [0,T], X_t \in J)P_i(\tau > n-T, X_{n-T}=j)
$$
$$
= \sum_{j \in J}P_j(\tau > T)P_i(\tau > n-T, X_{n-T}=j)
$$
$$
\leq \sum_{j \in J} (1-q)P_i(\tau >n-T, X_{n-T}=j)
$$
$$
= (1-q)P_i(\tau > n-T)
$$
repeating this with now $n = n-T$, we get
$$
P_i(\tau > n) \leq (1-q)^2 P_i(\tau > n-2T) \leq (1-q)^3 P_i(\tau > n-3T)
$$
$$
\leq (1-q)^{\lfloor\frac{n}{T}\rfloor} P_i(\tau > n -\left\lfloor\frac{n}{T}\right\rfloor T)
$$
$$
\leq (1-q)^{\frac{n}{T}-1} = \frac{1}{1-q} \left[(1-q)^\frac{1}{T}\right]^n = c_1 e^{-c_2 n}
$$
where
$$
c_1 = \frac{1}{1-q} \qquad c_2 = -\frac{1}{T}\log(1-q) > 0
$$


**Counterexample** If $J$ is not finite, there are counterexamples.
Consider the state space $\{1,2,\dots\} \cup \{\omega\}$, let $J = \{1,2,\dots\}$.
The transition probabilty are defined as follows:
$$
p_{i,\omega} = \frac{1}{(i+1)^2} \quad p_{i,i+1} = 1- p_{i,\omega}
$$
this chain, if started in $J$ tends towards $-\infty$, however every vertex in $J$ is connected to $\omega$, this measn that $T=1$. But the $min$ of the $q_i$ is note defined, their $\inf$ is zero. 

Clearly. starting from any $i \in J$, the probability of never reaching $\omega$ is the same as always going down:
$$
P_i(\tau = \infty) = \prod_{n=i}^\infty \left(1-\frac{1}{(n+1)^2}\right) > 0
$$
since 
$$
\prod_{n=i}^\infty \left(1-\frac{1}{(n+1)^2}\right) = \frac{i}{i+1} > 0
$$
in particular $P_1(\tau = \infty) = 1/2$.