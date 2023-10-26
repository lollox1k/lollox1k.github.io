### Weak
**Theorem** (Markov property) Let $(X_n)_{n\geq 0}$ be a $Markov(\lambda,P)$. Then, conditional on $X_m = i$, $(X_{m+n})_{n \geq 0}$ is $Markov(\delta_i, P)$ and is _indipendent_ of the random variables $X_0,\dots, X_m$.

**Proof** We need to show that if $A$ is an event determined by $X_0,\dots,X_m$ we have, then
$$
\mathbb{P}\left( \{X_m = i_m, X_{m+1}= i_{m+1},\dots, X_{m+n} = i_{m+n}\} \cap A \,\vert\, X_m = i\right)
$$
$$
= \delta_{i_m,i} \,p_{i_m i_{m+1}}\,p_{i_{m+1} i_{m+2}}\,\dots\, p_{i_{m+n-1} i_{m+n}} \mathbb{P}(A\,\vert X_m=i)
$$
Using [[Discrete time Markov chains|theorem 1.1.1]]
$$
= \mathbb{P}(Y_0 = i_m, \dots, Y_n = i_{m+n}) \mathbb{P}(A\,\vert\, X_m = i)
$$
So that $(Y_n)_{n \geq 0} \sim Markov(\delta_i,P)$.

To prove the first identity,  note that $A\in \sigma(X_0,\dots,X_m)$, the events $E = \{X_0 = i_0,\, X_1 = i_i,\dots,\, X_m = i_m\}$ form a partiton (look [[Sigma algebra from partiton]]), so that we can always write an event $A$ as a union (finite or countable) of events $A_k$. In our case the partition if the collection of paths of lenght $m$: $C_k = \{ X_0 = i_0, \dots X_m = i_m\}$ for all possible sequences of states.

It suffices to prove the identity for such events, applying the definition of conditional probability one gets
$$
\delta_{i,i_m} p_{i_m,i_{m+1}} \dots\, p_{i_{m+n-1}, i_{m+n}}\; \lambda_{i_0}p_{i_0,i_1}\dots\, p_{i_{m-1},i}\frac{1}{\mathbb{P}(X_m = i)} 
$$
we can see that the right part is precisley the definition of conditional probability of $A$ to the event $X_m = i$. $\square$

## Strong

**Theorem** (Strong Markov property) Let $(X_n)_{n\geq 0}$ be a $Markov(\lambda,P)$, and let $T$ be a [[Stopping times|stopping time]] of $(X_n)_{n\geq 0}$. Then, conditional on $T < \infty$ and $X_T = i$, $(X_{T+n})_{n \geq 0}$ is $Markov(\delta_i, P)$ and is _indipendent_ of the random variables $X_0,\dots, X_T$.

**Proof** Let $B \in \sigma(X_0,\dots,X_T)$ any event depending on $X_0,\dots,X_T$. Then,
$B \cap \{T=m\} \in\sigma(X_0,\dots, X_m)$.
Also, since we are conditioning w.r.t. $T < \infty$, the events $\{T=m\}$ partition the event space.
Let's use the notation $H_T^{T+n} = \bigcap_{k=T}^{T+n}\{X_k=i_k\}$ for the "history" from time $T$ to $T+n$.
We need to prove:
$$
P(H_T^{T+n} \cap B | T<\infty, X_T=i) 
$$
$$
= P_i(H_0^n)P(B| T<\infty, X_T=i)
$$
then the fact that $(X_{T+n})_{n \geq 0} \sim Markov(\delta_i, P)$ follows from the characterization [[catene di Markov|path probability]].
Using the definition of conditional probability, we can see that we just need to prove
$$
P(H_T^{T+n} , B , T<\infty, X_T=i) = P_i(H_0^n)P(B, T<\infty, X_T=i)
$$
now we use our previous observations (and the definition of conditional probability) to write the first event as
$$
\sum_{m\geq0} P(H_T^{T+n} | B \cap \{T=m\}, X_T=i)P(B \cap \{T=m\}, X_T=i)
$$
$$
= \sum_{m\geq0} P(H_m^{m+n} |  X_m=i)P(B \cap \{T=m\}, X_T=i)
$$
now using the weak markov property on the deterministic time $m$

$$
= \sum_{m\geq0} P_i(H_0^{n})P(B \cap \{T=m\}, X_T=i)
$$
$$
= P_i(H_0^n)P(B, T< \infty, X_T = i) \qquad \square
$$








**Proof 2** Let's use the notation $H_{T-1} = \bigcap_{n=0}^{T-1}\{X_n=j_n\}$ for the "history" up to time $T-1$ of our DTMC, pick two states $i,j \in I$. Then
$$
P(X_{T+1}=j | H_{T-1} \cap \{X_T=i\}) = \frac{P(X_{T+1} = j \cap H_{T-1} \cap \{X_T=i\})}{P(H_{T-1} \cap \{X_T=i\})}
$$
where we have used the definition of conditional probability. Since we are working with finite a.s. stopping time, using the law of total probability
$$
= \sum_{n \geq 0} \frac{P(X_{T+1} = j \cap H_{T-1} \cap \{X_T=i\} \cap \{T=n\})}{P(H_{T-1} \cap \{X_T=i\})}
$$
we can substitute $T$ with $n$, since we are taking the interection with the event $\{T=n\}$, and use the regular Markov property!
$$
= \sum_{n \geq 0} \frac{P(X_{n+1} = j \cap H_{n-1} \cap \{X_n=i\} \cap \{T=n\})}{P(H_{T-1} \cap \{X_T=i\})}
$$
now use the defintion of conditional probability again
$$
= \sum_{n \geq 0} \frac{P(X_{n+1} = j | H_{n-1} \cap \{X_n=i\} \cap \{T=n\})}{P(H_{T-1} \cap \{X_T=i\})} P( H_{n-1} \cap \{X_n=i\} \cap \{T=n\})
$$
$$
= \sum_{n \geq 0} p_{ij} \frac{P( H_{T-1} \cap \{X_n=i\} \cap \{T=n\})}{P(H_{T-1} \cap \{X_T=i\})}
$$
$$
= p_{ij}\sum_{n \geq 0} P(\{T=n\} | H_{T-1} \cap \{X_T=i\}) = p_{ij}
$$
where the sum is equal to one since $T$ is a stopping time, so it's compleatly determined by the history up to time $T$ (one term is $1$ and the others $0$). $\square$





