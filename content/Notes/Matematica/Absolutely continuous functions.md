> [!definition]
> A function $f: [a,b] \to \mathbb{R}$ is called **absolutely continuous** if for every $\epsilon > 0$ there exists $\delta_\epsilon > 0$ such that every finite familiy of open disjoint intervals $(a_k,b_k)$ such that the sum of their lenghts is less than $\delta_\epsilon$
> $$
> \sum_{k=1}^n (b_k - a_k) < \delta_\epsilon
> $$ 
> the inequality
> $$
> \sum_{k=1}^n |f(b_k)-f(a_k)| < \epsilon
> $$
> is satisfied.


# Examples 

> [!example]
> The function $\sqrt{x} \in AC[0,1]$. Note that this function is not uniformly continuous, so that $UC \centernot\implies AC$.
> We use the fact that $0 \leq h \leq a < b$ 
> $$
> \sqrt{b}-\sqrt{a} \leq \sqrt{b-h}-\sqrt{a-h}
> $$
> we can then shift all intervals to the left, concatenating them to obtain a telescopic sum
> $$
> \sum_k (\sqrt{b_k}-\sqrt{a_k}) \leq \sqrt{c_n}
> $$
> where $c_1 =  0$ and $c_2 = b_1-a_1$, and so on.
> Then $c_n$ is the total lenght of the intervals, just choose $\delta = \epsilon^2$. 


# Properties
It's a _stronger condition than uniform continuity_, just take a family of one interval. It's not equivalent, since the [[Cantor-Vitali function]], which is continuous, hence in $[0,1]$ is uniformly continuous is not AC since we can always find a family $(a_k,b_k)$ such that
$$
\sum_{k=1}^n |c(b_k)-c(a_k)| = 1, \qquad \sum_{k=1}^n (b_k-a_k) < \delta
$$
the "rise" of the function is on a set of measure zero!

Clealry if $f$ is Lipschitz, then it's absolutely continuous, since
$$
\sum_{k=1}^n |f(b_k)-f(a_k)| \leq L\sum_{k=1}^n (b_k-a_k)
$$
just take $\delta = \frac \epsilon L$.

We introduce this definition in our quest to find the family of functions for which the fondamental theorem of calculus holds, hence it's not surprising that given any $f \in L^1(a,b)$, then the integral function
$$
F(x) := \int_a^x f\,dx
$$
it's absolutely continuous. This follows from the [[Lebesgue's integral|absolutely continuity of the Lebesgue integral]] (hence the name).

Let $(a_k, b_k)$ a famili of disjoint open intervals. Then
$$
\sum_k |F(b_k)-F(a_k)| = \sum_k \left| \int_{a_k}^{b_k} f\,dx\right|
\leq \sum_k \int_{a_k}^{b_k} |f|\,dx = \int_{\cup_k(a_k,b_k)}|f|\,dx < \epsilon
$$
if the measure of the set we are integraitng on is small enough:
$$
\mu\left(\bigcup_k (a_k,b_k)\right) = \sum_k (b_k-a_k) < \delta_\epsilon
$$
since the intervals are disjoint.

The following theorem makes clear that the family of function that satisfies the Fundamental Theorem of Calculus is precisley $AC$.

> [!lemma]
> Let $f \in C^0[a,b]$. $f$ is $AC[a,b]$ iff $\{\Delta_h f\}_h$ is uniformly-integrable.
> > [!proof]-
> > Suppose that $\{\Delta_h f\}_h$ is uniformly-integrable[^1], then every integral function shares the same continuity modulus $\delta_\epsilon$. Let $(a_k, b_k)$ be a family of disjoint interval with total length less than $\delta_\epsilon$
> > $$
> > \sum_{k=1}^n \left |  \frac 1h\int_{b_k}^{b_k+h} f dt -\frac 1h\int_{a_k}^{a_k+h} f dt\right| = \sum_{k=1}^n \left | \int_{a_k}^{b_k} \Delta_h f dt\right| < \epsilon
> > $$
> >Taking the limit $h\to 0$, and using continuity of $f$ we get that $f \in AC[a,b]$.
> >Now suppose $f \in AC[a,b]$, WLOG we can assume that $f$ is non-decreasing (the usual [[Bounded variation functions|Jordan decomposition]]), then $\Delta_h f \geq 0$. Let $A = \bigcup_k (a_k,b_k)$ the usual disjoint union of intervals. Then
> >$$
> >\int_A  \Delta_h f dt = \sum_k \int_{a_k}^{b_k} \Delta_h f dt = 
> >\frac 1h \sum_k \int_{b_k}^{b_k+h} f dt-\int_{a_k}^{a_k+h} f dt
> >$$
> >$$
> > = \frac 1h \int_0^h \sum_k f(b_k+t)-f(a_k+t) dt < \frac 1h \int_0^h \epsilon dt = \epsilon \quad \square
> >$$
> >

> [!theorem]
> Let $f \in AC([a,b])$. Then its derivative $f'$ exists a.e., furthermore $f' \in L^1(a,b)$ and satisfies: 
> $$
> \int_a^x f' dt = f(x)- f(a), \qquad \forall x \in [a,b]
> $$
> > [!proof]-
> > Since $AC \implies BV$, $f$ can be [[Bounded variation functions|decomposed]] as the difference of two monotonic functions, which have derivatives a.e. 
> > For the previous lemma, and the fact that $\Delta_h f \to f'$, using [[Vitali's theorem]]:
> > $$
> > \int_a^x f' dt = \lim_{h\to 0} \int_a^x \Delta_h f dt = \lim_{h\to 0} \frac 1h \left(\int_x^{x+h} fdt -\int_a^{a+h} f dt\right) = f(x)-f(a) \quad \square
> > $$
> 


[^1]: To solve the problem $b+h \notin [a,b]$ we use the continuous extention of $f$ in $\mathbb{R}$: just set $f(x) = f(b)$ if $x > b$ and $f(x)=f(a)$ if $x < a$.

