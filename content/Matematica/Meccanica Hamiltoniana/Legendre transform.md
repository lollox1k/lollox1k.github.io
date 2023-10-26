# Legendre transform

Suppose $L : \mathbb{R}^n \to \mathbb{R}$ is a function such that:
- is _convex_;
- $\lim_{|v|\to \infty} \frac{L(v)}{|v|}=+\infty$
(Note that convexity implies continuity).

Then we can define
**Def** The _Legendre transform_ of $L$ is the function
$$
L^*(p) := \sup_{v \in \mathbb{R}^n} \Big\{p\,v-L(v)\Big\}
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

