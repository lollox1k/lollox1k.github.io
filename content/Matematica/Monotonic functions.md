> [!definition]
> Let $I \subseteq \mathbb{R}$ be an interval. A function $f : I \to \mathbb{R}$ is called **monotonic non-decreasing** if $f(x)\leq f(y)$ for every $x,y \in I$ such that $x \leq y$. When the same holds with the reversed inequalities is called **monotonic non-increasing**.

# Properties 

Let $f : I \to \mathbb{R}$ be a monotonic function. Then
1. $f$ is _measurable_.
> [!proof]-
>  $f^{-1}((-\infty,a])$ is an interval, since $(-\infty, a]$ is a [[Pi-system]] that generates the Borel $\sigma$-algebra, $f$ is measurable. $\square$
1. For every $x \in \mathring I$ the _left and right limit exists_ (they are finite). 
> [!proof]-
> WLOG let $f$ be non-decreasing, let $\{x_n\}$ be a monotoinic sequence >such that $x_n \uparrow x$, then
>   $$
>	\lim_{y \uparrow x} f(y) = \lim_{n \to \infty} f(x_n)\leq f(x)
>	$$
	>exists and is finite, since the sequence $f(x_n)$ is non-decreasing and
	>bounded from above by $f(x)$. Similarly one gets the result for non
	>increasing and right limits. $\square$

> [!remark]
> If we don't restrict to point in the interior, we have existence but not necessarily finiteness (we can't bound the sequence), consider for example $I = (-\frac \pi 2, +\frac \pi 2)$ and the funtion $\tan(x)$.

3. Every discountinuity is of _jump_ type, and the number of discontinus points is at most _countable_.
> [!proof]-
> Let $[a,b] \subseteq I$ a finite interval. Call $S$ the set of >discontinuities of $f$ in $[a,b]$. This means that there exists an $n > 0$ >such that $|f_-(x)- f_+(x)| > \frac 1 n$ . Then we can write $S$ as >the union
	>$$
>	S = \bigcup_{n =1}^\infty \left\{x \in [a,b] \,:\, |f_-(x)- f_+(x)| > \frac 1 n\right\}
  >$$
	>since the interval is finite, each set in the union is finite, since has at >most $|f(b)-f(a)|n$ elements. Then $S$ is at most numerable. >Since $\mathbb{R}$ is can be writte has the countable union of finite
	>intervals, the number of discontinuities is still at most countable. $\square$


The last property implies that a monotonic function is _continuous almost everywhere_. It turns out that this also holds for its derivative.

> [!theorem]
> Every monotonic non-decreasing function $f: [a,b] \to \mathbb{R}$ admits a derivative a.e. Furthermore $f'$ satisfies the inequality:
> $$
> \int_a^b f'(t)dt \leq f(b)-f(a)
> $$
> > [!proof]-
> > First we prove that the set
> > $$
> > E := \{x \in (a,b)\,:\, \underline D^+f(x) < \alpha < \beta < \overline D_-f(x)\}
> > $$
> > has measure zero. 
> > \vdots \vdots \vdots
> > Define the familiy of functions $\{\Delta_h f\}_{h\geq 0}$ where
> > $$
> > \Delta_h f(x) := \frac{f(x+h)-f(x)}{h}
> > $$ 
> > (we do a continuous extention of $f$ outside $[a,b]$). Clearly $\Delta_h f \to f'$ a. e., using [[Lemma di Fatou|Fatou's lemma]]:
> > $$
> > \int_a^b f' dx \leq \liminf_{h\to 0} \int_a^b \Delta_h f dx
> > = \liminf_{h\to 0} \frac 1h\int_b^{b+h} f dx - \frac 1h\int_a^{a+h} f dx 
> > $$
> > $$
> > \leq \liminf_{h\to 0} \frac 1h \int_b^{b+h} f(b)dx -\frac 1h \int_a^{a+h} f(a)dx = f(b) - f(a) \quad \square
> > $$
> > 


> [!proposition]
> Every left-continuous monotonic function  $f$ can be written as the sum of a continuous monotonic function $\phi$ and a jump function $H$ (left-continuous). $f = \phi + H$ 
> This representation is unique.
> > [!proof]-
> > Let $\{x_n\}$ and $\{h_n\}$ be the set of discontinuities and jump values of $f$, define the [[Jump functions|jump function]] $H$ with these values. The function $\phi := f - H$ is continuos (easy to check) and monotonic.
> > Suppose WLOG that $f$ is non-decreasing, then for $x \leq y$ 
> > $$
> > \phi(y) - \phi(x) = f(y)-f(x) - [H(y)-H(x)] \geq 0
> > $$
> > since the sum of the jumps from $x$ to $y$ is not greater the the whole increment of the function. $\square$
> 

Clearly we can generalize this decomposition to monotonic function that have bot left and right continuous point, by summing two Jump functions.


