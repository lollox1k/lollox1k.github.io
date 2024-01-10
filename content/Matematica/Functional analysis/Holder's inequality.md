**Theorem** (Holder's inequality) Suppose $(X,\mathcal{A}, \mu)$ is a measure space, $1 \leq p \leq +\infty$, and $u,v :X \to F$ are measurable. Then
$$
\Vert uv \Vert_1 \leq \Vert u \Vert_p \Vert v \Vert_{p'}.
$$
**Proof** The cases $p = 1, \infty$ are trivial. Suppose $1 < p < \infty$. Consider the special cases where $u$ and $v$ are normalized, $\Vert u \Vert_p = \Vert v \Vert_{p'}=1$, using [[Young's inequality]] on the absolute values
$$
| uv | \leq \frac {|u|^p} p + \frac{|v|^{p'}} {p'}
$$
integrating both sides
$$
\Vert uv \Vert_1 \leq \frac 1 p + \frac 1{p'} = 1 = \Vert u \Vert_p \Vert v \Vert_{p'}
$$
If one of the norms are zero or infinity the inequality works, so assume that $0 < \Vert u \Vert_p, \Vert v \Vert_{p'} < \infty$. 

We can normalize such funtions! Just apply the special case. $\square$
