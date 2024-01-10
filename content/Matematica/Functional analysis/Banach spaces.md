**Proposition** (Every absolutely convergent series is convergent) Let $(X, \Vert\cdot\Vert)$ be a Banach space, and $\sum_k x_k$ a series such that series of norms $\sum_k \Vert x_k \Vert < \infty$ conveges. Then also the series conveges.

**Proof** The norm series is a series of real numbers. Since it converges, it's also a [[successioni di Cauchy|Cauchy sequence]], so that $\forall \epsilon > 0$ there exists $N \geq 0$ such that for all $m > n \geq N$
$$
\left| \sum_k^m \Vert x_k\Vert - \sum_k^n \Vert x_k\Vert\right| = \sum_{k=n+1}^m \Vert x_k\Vert < \epsilon
$$
using the [[Minkowsky's inequality]] 
$$
\left\Vert \sum_k^m  x_k - \sum_k^n  x_k\right\Vert \leq \sum_{k=n+1}^m \Vert x_k \Vert < \epsilon
$$
so that also the series is Cauchy. Since $X$ is a Banach space, the series converges. $\square$ 
