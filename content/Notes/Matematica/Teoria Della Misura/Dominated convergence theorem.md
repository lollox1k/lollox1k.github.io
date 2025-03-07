**Theorem** (Lebesgue) Let $f_n$ be a sequence of measurable functions in the measure space $(X, \Sigma, \mu)$ such that $f_n \to f$ (pointwise convergence) a.e. Then if there exists a measurable function $g$ such that  $|f_n| \leq g$ a.e. for all $n$, and $g$ is integrable,
$$
\lim_{n\to\infty} \int |f-f_n|d\mu = 0
$$
that is $f_n \xrightarrow{L^1} f$.
**Remark** Not that $L^1$ convergence also implies
$$
\lim_{n\to\infty}\int f_n d\mu = \int f d\mu
$$
i.e. we can exchange the limit with the integral. This follows from this simple inequality:
$$
\left| \int fd\mu - \int f_n d\mu\right| \leq \int |f-f_n| d\mu
$$


**Proof** We will use the reverse [[Lemma di Fatou|Fatou's lemma]] on the positive functions $|f-f_n|$ which are bounded by $2g$:
$$
\limsup_n \int |f-f_n|d\mu \leq \int \limsup_n |f-f_n| d\mu  = 0 \quad \square
$$



