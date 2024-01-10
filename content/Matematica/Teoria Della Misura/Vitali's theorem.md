
> [!definition]
> A family of functions $\{f_i\}_{i \in I} \subseteq L^1(X,\mu)$ is called **uniformly integrable** if for every $\epsilon > 0$ there exists a $\delta > 0$ such that for every small enough set $\mu(E) < \delta$ 
> $$
> \int_E |f_i|d\mu < \epsilon \quad \forall i \in I
> $$
> This is the same as
> $$
> \lim_{\mu(E)\to 0} \sup_{i \in I} \int_E |f_i|d\mu = 0
> $$

> [!definition]
>  A family of functions $\{f_i\}_{i \in I} \subseteq L^1(X,\mu)$ is called **tight** if for every $\epsilon > 0$ there exists a subset $E \subseteq X$ with $\mu(E) < \infty$ such that
>  $$
>  \int_{X\setminus E} |f_i|d\mu < \epsilon \qquad \forall i \in I  
>  $$

> [!proposition]
> Let $f \in L^1$, then for every $\epsilon > 0$ there exists a finite set $E$ such that
> $$
> \int_{X\setminus E} |f|d\mu < \epsilon
> $$ 
> > [!proof]-
> > Define sets $A_n := \{ x\,:\, |f(x)| \geq \frac 1n\}$. Then
> > $$
> > A := \bigcup_{n\geq 1} A_n = \{x\,:\, |f(x)| > 0\}
> > $$
> > so that
> > $$
> > \int_A |f|d\mu = \int_X |f| d\mu
> > $$
> > Define the sequence of functions $f_n := |f| \mathcal{A_n}$, since $A_n \subseteq A_{n+1}$ by the [[Monotone Convergence Theorem|]]
> > $$
> > \lim_{n\to \infty} \int_X |f|\mathcal{A_n}d\mu = \int_A |f| d\mu
> > $$
> > This means that for every $\epsilon > 0$ there exists $N \geq 1$ such that
> > $$
> > \int_X |f|d\mu - \int_{A_n} |f|d\mu < \epsilon, \quad \forall n \geq N \quad \square
> > $$
> > 

> [!theorem]
> Let $\{f_n\}$ be a sequence that is uniformly integrable and tight over $E$. If $f_n \to f$ pointwise a.e. on $E$, then 
> $$
> \lim_{n\to\infty}\int_E |f-f_n| d\mu = 0
> $$
> > [!proof]-
> > (Sketch) Fix $\epsilon > 0$, we work on the finite set $E$ using thighness assumption, now we can use [[Convergence of Measurable Functions|Egorov's theorem]], $f_n \rightrightarrows f$  on a set $E' \subseteq E$ with $\mu(E\setminus E') < \epsilon$. If we split the integral
> > $$
> > \int_X |f-f_n| d\mu = \int_{X\setminus E} |f-f_n| d\mu + \int_{E\setminus E'} |f-f_n| d\mu + \int_{E'} |f-f_n| d\mu
> > < 2\epsilon \int_{E'} |f-f_n| d\mu
> > $$
> > we can take the limit inside where there is uniform convergence, and since $\epsilon$ was arbitrary the theorem follows. $\square$ 


> [!theorem]
> Let $\{h_n\}$ be a sequence of non-negative functions on $E$ that converges pointwise a.e. to $0$. Then 
> $$
> \lim_{n\to\infty}\int_E h_n d\mu = 0
> $$
> if and only if $\{h_n\}$ is uniformly integrable and tight over $E$.






