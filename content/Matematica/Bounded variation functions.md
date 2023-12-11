

> [!definition] 
> Let $I \subseteq \mathbb{R}$ be an interval and $P = \{x_1,\dots,x_n\} \subset I$ a partition. We define the **variation** of a funtion $f: I \to \mathbb{R}$ w.r.t. partition $P$ as
>$$
> V(f,P) := \sum_{i=1}^{n-1} |f(x_{i+1}) - f(x_i)|
> $$
> and the **total variation** of $f$ as the supremum on all partitions
>$$
>Var(f,I) := \sup_{P \text{ part. of}\, I} V(f,P)
>$$
>If this quantity is finite, we say that $f$ has **bounded variation** and we denote the set of all bounded variation functions on $I$ as $BV(I)$.
>If $I = [a,b]$ then we write $V_a^b[f]$ (notation from Kolmogorov-Fomin).


> [!example] 
> 1. The function $f(x) = x \sin{\frac 1x}$ is continuous on $[0,1]$ but $V_0^1[f] = +\infty$.
> 2. The function $f(x) = \sqrt{x}$ has $V_0^1[f] = 1$.


# Properties
The set $BV(I)$ forms a linear space (with sum and scalar multiplication defined in the obbious way), since
1. $Var(\alpha f, I) = |\alpha|Var(f,I)$ 
2. $Var(f+g, I) \leq Var(f,I) + Var(g,I)$ since $\sup(A+B) \leq \sup(A) + \sup(B)$.

Since $Var(f,I) = 0$ iff $f$ is a constant function, $Var(\cdot,I)$ is a _seminorm_ on this linear space. To get a norm one could define $\Vert\cdot \Vert := |f(a)| + Var(f,I)$ where $a \in I$. 

Let $f : [a,b] \to \mathbb{R}$.
1. If $f$ is monotone, then $f \in BV([a,b])$ and $V_a^b[f] = |f(b)-f(a)|$, since if w.l.o.g. $f$ is non-decreasing we can drop the absolute values and get a telescopic sum
$$
V(f,P) = \sum_{i=1}^{n-1} f(x_{i+1}) -f(x_i) = f(x_n) -f(x_i) \leq f(b) - f(a)
$$
2. If $f$ is [[Lipschitz]] with constant $L$ then $V_a^b[f] \leq L(b-a)$, since
$$
V(f,P) \leq L \sum_{i=1}^{n-1}|x_{i+1}-x_i| \leq L(b-a)
$$
3. If $f \in C^1[a,b]$ then 
$$
V_a^b[f] = \int_a^b |f'(x)|dx
$$
if we use the [[Teorema di Lagrange|mean value theorem]] 
$$
Var(f,P) = \sum_{i=1}^{n-1} |f'(\xi_i)|(x_{i+1}-x_i)
$$
but the supremum on all partitions of $[a,b]$ is the definition of the Riemann-Darboux intergral of $|f'|$. 

4. Let $a < b < c$, then
$$
V_a^b[f] + V_b^c[f] = V_a^c[f]
$$
since 
$$
Var(f,P) = \sum_{i=1}^r |f(x_{i+1}) -f(x_i)| + \sum_{i=r+1}^{n-1} |f(x_{i+1}) -f(x_i)| \leq V_a^b[f] + V_b^c[f]
$$
where we have split the sum such that $\{x_1,\dots x_{r+1}\} \subset [a,b]$ and $\{x_{r+1}, \dots x_n\} \subset [b,c]$.

Let $P_1$ and $P_2$ be two partitions of the intervals $[a,b]$ and $[b,c]$ such that $\forall \epsilon > 0$
$Var(f, P_1) > V_a^b[f] - \epsilon$ and $Var(f, P_2) > V_b^c[f] - \epsilon$. Since $P_1 \cup P_2$ is a partition for $[a,c]$ 
$$
V_a^c[f] \geq Var(f,P_1 \cup P_2) > V_a^b[f] + V_b^c[f] -2\epsilon
$$
since $\epsilon$ was arbitrary the claim follows.

This implies, since the total variation is a non-negative quantity, that the function $v : [a,b] \to [0,\infty]$ defined as
$$
x \mapsto V_a^x[f]
$$
is _monotonic non-decreasing_. 
From this follows a cool decomposition theorem.

> [!theorem] 
> **Jordan's decomposition** 
> Every bounded variation function in an interval $f \in BV([a,b])$ can be written as the difference of two [[Monotonic functions|monotonic non-decreasing functions]].
> > [!proof]- 
> > Consider the function $\phi = v-f$, where $v(x) = V_a^x[f]$. Let $x \leq y$, then
> > $$
> > \phi(y)-\phi(x) = V_x^y[f]-[f(y)-f(x)] \geq 0
> > $$
> > we see that $\phi$ is also monotonic non-decreasing, so $f$ can be written as
> > $$
> > f = v - \phi
> > $$
> > which is the decomposition we were looking for. $\square$

> [!remark]
> Clearly the decomposition is not unique, since we can add a constant. To obtain a unique decomposition one can fix the value of the first function to zero at point $a$ for example.

> [!tip]
We can extend the theorem to unbounded intervals taking the $\inf$ or $\sup$, of course we need to restrict to bounded monotonic functions. 


A consequence of this decomposition is that any bounded variation function has a well defined derivative a.e.



# Decomposition of BV functions
Let's recap what we know about bounded variation functions.
Let $g \in BV$, since in general $g \notin AC$ 
$$
g \neq \int_a^x g'dt -g(a)
$$
define a new function as this difference
$$
\chi := g - \int_a^x g'dt+g(a)
$$
Note that $\chi' = 0$ almost everywhere. Then we can decompose $g$ as
$$
g = \chi + \phi, \qquad \phi:= \int_a^x g' dt -g(a)
$$
where $\phi$ is an [[Absolutely continuous functions|absolutely continuous function]]. Then $\chi$ is still a bounded variation function that we can represent using the Jordan decomposition:
$$
\chi = u-v
$$
where $u,v$ are monotonic non-decreasing functions. We can further decompose $u$ and $v$ using [[Jump functions]]:
$$
u = H_u + \varphi_u, \qquad v = H_v + \varphi_v
$$
where $\varphi_u, \varphi_v$ are continuous functions. 
Putting all piecies togheter we get:
$$
g = H + C + \phi
$$
where $H := H_u + H_v$ is called the **Jump part** of $g$; $C := \varphi_u + \varphi_v$ is a continuous function known as the **cantorian part** of $g$, and $\phi$ is the **absolutely continuous part** of $g$.

For example the [[Cantor-Vitali function]] coincides with its cantorian part (this is the reason for its name).

> [!tip] Moral of the story
> Since $(C+H)' =0$ a.e., the only part we can get back from integrating the derivative $g'$ is the absolutely continuous one.





