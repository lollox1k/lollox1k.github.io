The simplest of [[Monotonic functions]] are called _jump functions_, they are defined in the following way:
Let $I \subseteq \mathbb{R}$ be an interval, suppose we have a finite or countable collection of points $x_1,x_n, \dots$ in this interval, for each point we assign a value $h_n$ such that $\sum_n h_n < \infty$ and $h_n > 0$ for all $n$. 
$$
f(x) := \sum_{n \,:\, x_n < x} h_n
$$
where we define $f(x) = 0$ is the sum has zero terms.
This function is:
1. Monotonic non-decreasing
2. Left-continuous[^1], with jump discontinuities at every $x_n$ with corresponding jump value $h_n$, continuous at every other point.

> [!example]
> We can construct a Jump function that is has jumps in a dense set. Let $\{x_n\} = \mathbb{Q}$ (with a choosen denumeration) and $h_n$ be any positive sequence in $l^1$, for example  $h_n = \frac 1 {2^n}$.

[^1]: If we insted defined $f$ as 
	$$
	f(x) = \sum_{n \,:\, x_n \leq x} h_n
	$$
	then it would be right-continuous.
