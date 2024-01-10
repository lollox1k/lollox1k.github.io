# Legendre transform

Suppose $L : \mathbb{R}^n \to \mathbb{R}$ is a function such that:
- is _convex_;
- $\lim_{|v|\to \infty} \frac{L(v)}{|v|}=+\infty$
(Note that convexity implies continuity).

Then we can define
**Def** The _Legendre transform_ of $L$ is the function
$$
L^*(p) := \sup_{v \in \mathbb{R}^n} \Big\{ \langle p,\,v\rangle-L(v)\Big\}
$$

Our conditions ensures that there exists a point of maximum, call it $v^*$. 
Provided that $L(v)$ is differentiable at $v^*$, imposing stationarity one finds
$$
p = D_vL(v^*)
$$
so that this equation is solvable (perhaps not uniquely) for $v^* = h(p)$.
Then
$$
L^*(p) = h(p)p-L(h(p))
$$

### Duality of the Legendre transform

**Theorem** The new function $p \mapsto L^*(p)$ is 
- _convex_;
- $\lim_{|v|\to \infty} \frac{L^*(v)}{|v|}=+\infty$
- $L^{**} = L$ is _involutive_.

**Proof**  For each fixex $v$ the function $pv-L(v)$ is linear, so that the $\sup$ is convex:
$$
L^*(\alpha p_1+ (1-\alpha)p_2) = \sup_v \alpha p_1 v + (1-\alpha)p_2v - L(v) 
$$
$$
\leq \alpha\sup_v \{p_1v-L(v)\} + (1-\alpha)\sup_v\{p_2v-L(v)\} = \alpha L^*(p_1) + (1-\alpha)L^*(p_2) \square
$$



### From Velenik and Friedli

**Def** (Legendre-Fenchel transform) Let $f : I \to \mathbb{R} \cup \{+\infty\}$. The **Legendre transform** of $f$ is defined by:
$$
f(y)^* := \sup_{x \in I} \{yx - f(x)\}
$$
Geometrically: the maximum distance between the line $yx$ and the function graph.

**Proposition** The legendre transform of any function is convex.
**Proof** $\forall \alpha \in [0,1]$
$$
f^*(\alpha y_1 + (1-\alpha)y_2) = \sup_x \{  \alpha y_1x + y_2x -\alpha y_2 x -f(x)\}
$$
adding and subtracting $\alpha f(x)$ 
$$
\leq \alpha f^*(y_1) + f^*(y_2) -\alpha f^*(y_2) \quad \square
$$

**Oss** This implies that if $f$ is not convex, $(f^{*})^* \neq f$ i.e. that the Legendre Transform is not involutive.

**Def** (Supporting line) A supporting line at $x$ with slope $m$ for the function $f$ is a line such that:
$$
f(y) \geq f(x) + m(y-x)
$$
**Oss** A function is convex iff every point admits (at least one) supporting line.
**Oss** If a convex function is non differentiable at $x$, then it has infinite supporting line at this point with slopes in  $[\partial^- f(x), \partial^+f(x)]$.

**Proposition** (Duality of supporting lines slopes and points) If $f$ admits a supporting line with slope $k$ at point $x_0$, then $(k, f^*(k))$ admits a supporting line with slope $x_0$.
**Proof** 

$$
f^*(k) + x_0(z-k) = \sup_x \{ kx -f(x) +x_0z - x_0k\}
$$
since $f$ admits a supporting line at $x_0$ with slope $k$
$$
f(x) \geq f(x_0) + k(x-x_0) \implies -kx_0 \leq f(x)-f(x_0)-kx
$$
so that
$$
\leq \sup_x \{ kx - f(x) +x_0z +f(x) - f(x_0) -kx\} = x_0z - f(x_0) \leq f^*(z)
$$
so $f^*$ admits a supporting line at $k$ with slope $x_0$. $\square$

**Non differentiable points
![[Pasted image 20231103175616.png]]

**Proposition** Let $f$ be a convex function. Then:
1. If $f$ is not differentiable at $x$, $f^*$ is affine in the interval $[\partial^- f(x), \partial^+f(x)]$;
2. If $f$ is affine in some interval $[a,b]$ with slope $k$, then $f^*$ is not differentiable in $k$ and $\partial^- f^*(k) \geq b > a \geq \partial^-f^*(k)$.

**Proof** Since $f$ is convex, at the point $x$ it admits infinite supporting lines with slopes in $[\partial^- f(x), \partial^+f(x)]$. By the prevoious propositipon $f^*$ admits at al point $[\partial^- f(x), \partial^+f(x)]$ a supporting line with slope $x$. Since $f^*$ is convex, all the supporting line coincide, and $f^*$ is affine in this interval. $\square$






