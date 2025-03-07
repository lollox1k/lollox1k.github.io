**Theorem** Let $g$ be a gaussian random variable with variance $\nu^2$, $g \sim N(0,\nu^2)$. Let $F : \mathbb{R}\to \mathbb{R}$ be a differentiable function, and
$$
\lim_{x \to \pm \infty} F(x)P(x)=0
$$
where $P(x)$ is the density or $g$.
Then,
$$
\mathbb{E}[gF(g)] = \mathbb{E}(g^2) \mathbb{E}[F'(g)] = \nu^2 \mathbb{E}[F'(g)]
$$
**Proof** Use integration by parts. $\square$


**Remark** It can be generalized to gaussian vectors:

**Theorem** Let $g$ be gaussian vectors and $F : \mathbb{R}^n \to \mathbb{R}$ a differentiables function, then
$$
\mathbb{E}[g_1F(g)] = \sum_{l \leq n} \mathbb{E}[g_1g_l]\mathbb{E}\left[\frac{\partial F(g)}{\partial g_j}\right]
$$


