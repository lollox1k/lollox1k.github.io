**Proposition** (Minkowsky inequality) Let $u,v : E \to \mathbb{C}$ two measurable functions, and $p \in [1,+\infty]$, then
$$
\Vert u + v \Vert_p \leq \Vert u \Vert_p + \Vert v \Vert_p
$$

**Proof** Assume $1 \leq p < \infty$, since the case $p=\infty$ is trivial. Suppose $h \in L^{p'}$ and $\Vert h \Vert_{p'} \leq 1$. Then
$$
\left|\int (u+v)hd\mu\right| \leq \int| uh|d\mu + \int |vh|d\mu 
$$
$$
\Vert uh \Vert_1 + \Vert vh \Vert_1 \leq \Vert u \Vert_p + \Vert v \Vert_p
$$
where the second inequality is true by [[Holder inequality]]. Taking the supremum and using the lemma below we get the result. $\square$



**Lemma** (Formula for $\Vert u \Vert_p$) Suppose $(X, \mathcal{A}, \mu)$ is a measure space, $1 \leq p < \infty$ and $u \in L^p(\mu)$. Then
$$
\Vert u \Vert_p = \sup \left\{ \left|\int uh \,d\mu \right| \,:\, h \in L^{p'} \, \text{ and }\, \Vert h \Vert_{p'}\leq 1 \right\}
$$
**Proof** using [[Holder inequality]] 
$$
\left|\int uh \,d\mu \right| \leq \Vert uh \Vert_1 \leq \Vert u \Vert_p
$$
To prove the other way, consider the function
$$
h(x) = \frac{\overline u(x) |u(x)|^{p-2}}{\Vert u\Vert_p^{p/p'}}
$$
(set $h(x) = 0$ if $f(x) = 0$).
then
$$
\left|\int uh \,d\mu \right| = \frac{1}{\Vert u\Vert_p^{p/p'}} \left| \int |u|^p d\mu\right| = \Vert u\Vert_p 
$$
and $\Vert h \Vert_{p'} = 1$. $\square$ 


**Remark** The case $p=\infty$ fails, this is a counter example. Let $X = \{b\}$ a set with one element, and $\mu(\{b\}) = \infty$. Then the functions in $L^1(\mu)$ are the functions that are identically zero, $h(b)=0$ (with the usual convention $0\cdot \infty = 0$) so that $\Vert h \Vert_1 = 0$. But the functions in $L^\infty(\mu)$ are the ones with bounded values on $b$, just take $f(b) = 1$, so that $\Vert b \Vert_\infty = 1$. Clearly the above indentity cannot hold.

If $X$ is $\sigma$-finite, then the case $p= \infty$ also holds.

