It relates linear functionals on spaces of continuous functions on a locally compact space to [[Real or complex measures]].

Let $X$ be a locally compact Hausdorff space and $C_c(X)$ be the set of all continuous functions $f : X \to \mathbb{R}$ with compact support. 

A positive functional is one that if $f \geq 0$ then $I(f) \geq 0$.
An example of positive linear functional is the integral w.r.t. a Radon measure:
$$
I(f) = \int_X f d\mu
$$
we will show that this is the only possibility.

> [!proposition]
> If $I$ is a positive linear functional on $C_c(X)$, for each compact $K \subset X$ there is a constant $C_K$ such that
> $$
> |I(f)| \leq C_K\Vert f \Vert_\infty \qquad \forall f \in C_c(X) \text{ s.t. } \text{supp }f \subseteq K
> $$
> > [!proof]-
> > Consider real functionals (by the triangle inequality the complex case follows). Since $X$ is LCH, it's also locally [[normal space|normal]], since we are working in a compact subset $K$ we can use [[Urysohn’s lemma]] and build a continuous function $\phi \in C_c(X;[0,1])$ such that $\phi = 1$ on $K$.
> > $$
> > |f| \leq \Vert f \Vert_\infty \phi
> > $$
> > or equivalently
> > $$
> > \Vert f \Vert_\infty \phi - f \geq 0, \qquad \Vert f \Vert_\infty \phi + f \geq 0
> > $$
> > Since $I$ is a positive linear functional:
> > $$
> > I(\Vert f \Vert_\infty \phi - f) \geq 0, \qquad I(\Vert f \Vert_\infty \phi + f )\geq 0
> > $$
> > thus
> > $$
> > |I(f)| \leq  I(\phi)\Vert f \Vert_\infty \qquad \square
> > $$


> [!theorem]
> If $I$ is a positive linear functional on $C_c(X)$, then there is a **unique Radon measure** $\mu$ on $X$ such that 
> $$
> I(f) = \int_X f \,d\mu, \qquad \forall f \in C_c(X)
> $$
> Moreover,
> $$
> \mu(U) = \sup\{I(f) \mid f \in C_c(X), \, f \prec U\}
> $$
> for all open sets $U$ and
> $$
> \mu(K) = \inf\{ I(f) \mid f \in C_c(X), \, f \geq \mathbb{1}_K\}
> $$
> for all compact sets $K$.
> > [!proof]-
> > **Existence** Define for all $U$ open sets:
> > $$
> > \mu(U) := \sup \{I(f)\mid f \prec U,\, f \in C_c(X)\}
> > $$
> > where by $f \prec U$ we mean $0 \leq f \leq \mathbb{1}_U$.
> > We can define an [[Misura esterna|outer measure]] by:
> > $$
> > \mu^*(E) := \inf \{ \mu(U) \mid E \subseteq U, U \text{ open }\}
> > $$
> > If we restrict it on the Borel set we get a measure.
> > $\dots$
