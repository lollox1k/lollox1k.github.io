
**Def** A [[catene di Markov|Markov chain]] is called **reversible** if there exists a _positive valued function_ $\pi$ such that for all states $x,y$ holds
$$
\pi(x)p(x,y) = \pi(y)p(y,x)
$$
This equation is known as the **Detailed balance equation** (DB).

**Claim** This function on the state space is a stationary measure.
**Proof** We need to check that $\pi P = \pi$ holds. 
$$
\sum_y \pi(y)p(y,x) = \sum_y \pi(x)p(x,y) = \pi(x)
$$
since $\sum_y\pi(x,y) = 1$. $\square$

If $\sum_x \pi(x) = C < \infty$ then $\pi(x)/C$ is a stationary distribution.


**Proposition** (Kolmogorov's loop criterion) An _irreducibile_ Markov chain is reversible if and only if for every closed walk $x_0,x_1,\dots x_n=x_0$ 
$$
\prod_{i=0}^n p(x_i,x_{i+1}) = \prod_{i=0}^n p(x_{i+1},x_{i}), \qquad (x_{n+1}=x_0)
$$
i.e. the probability of a given closed walk is the same in each direction.
**Proof** Assume the markov chain is reversibile, we can use DB to reverse the probabilities:
$$
p(x,y) = \frac{\pi(y)}{\pi(x)}p(y,x) 
$$
using this identity in the product the $\pi$  terms cancels out (you can show this by induction).

(_low confidence_) Fix a state $w$, and define for every state $x \in I$ 
$$
\rho(x):= p(w,x_1)\dots p(x_n,x) > 0
$$
where $wx_1,\dots x_n \,x$ is any path from $w$ to $x$ (this exists and has positive probability since the chain is irreducible). (To better define this function you can use the shortes path with shortes probability).

Given another neighbouring state $y \in I$, we can build a closed walk $w \to x$, $x \to y$, $y \to w$
which has the same probability of its reversed 
$$
\rho(x)p(x,y)\hat\rho(y) = \rho(y)p(y,x)\hat\rho(x)
$$
so that our chain is reversibile with respect to the function
$$
\pi(x) := \frac{\rho(x)}{\hat\rho(x)} \qquad \square
$$


**Oss** $P$ is reversibile iff $P = \tilde P$, as defined in [[Time reversal]].
