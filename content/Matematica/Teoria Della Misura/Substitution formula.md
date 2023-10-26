# Substitution formula

**Theorem** Let $(X,\mathcal{F})$ and $(Y, \mathcal{E})$ be two measurable spaces, and a [[Funzioni misurabili|measurable map]] $h : X \to Y$, and a measurable function $g : Y \to \mathbb{R}$ (assuming the Borél $\sigma$-algebra). Then, if any of the two following integral exists, they are equal:
$$
\int_Y g\,d(h_*\mu) = \int_X g\circ h \,d\mu
$$
**Proof** Use the _standard machinery_.
Assume $g = \mathbb{1}_C$ with $C \in \mathcal{E}$ a measurable set. By definition of the [[Integrale di Lebesgue|lebesgue integral]] of a simple function
$$
\int_Y \mathbb{1}_C\,d(h_*\mu) = h_*\mu(C) = \mu(h^{-1}(C))
$$
by definition of the [[Pushforward measure]]. 
Now for the left side, using an integration variable $x$ for clarity
$$
\int_X  \mathbb{1}_C(h(x))\,d\mu(x)
$$
the integrand function is
$$
\mathbb{1}_c(h(x))=
\begin{cases}
1 \text{ se } h(x) \in C \\
0 \text{ se } h(x) \notin C
\end{cases}
$$
this is the same as $\mathbb{1}_{h^{-1}(C)}$  the characteristic function of the set $h^{-1}(C)$. This is again a simple function, so
$$
= \mu(h^{-1}(C))
$$
so the theorem is proved for characteristic functions of measurable set. 
By linearity, it follows easily for simple function $g = \sum_{i=1}^n k_i \mathbb{1}_{C_i}$.

Using [[Monotone Convergence Theorem]] we can extend the result to non-negative measruable functions, choose a sequence of simple functions such that $\phi_n \uparrow g$.
$$
\int_Y g \,d(h_*\mu) = \lim_{n\to\infty} \int_Y \phi_n d(h_*\mu) = \lim_{n\to\infty} \int_X \phi_n(h(x))dx = \int_X g\circ h \,d\mu
$$
using the fact that $\phi_n\circ h$ are simple functions and
$$
\phi_n\circ h \,\uparrow\, g \circ h
$$
Extending the result to not non-negative function is done as usual, splitting the function in the positive and negative part. $\square$ 

**Variant using the Lebasgue definition**
Suppose now that $g$ is non-negative $g : Y \to [0,\infty)$, using the definition of the Lebasgue integral
$$
\int_Y g\, d(h_*\mu) = \sup \left\{ \int_Y \tilde S\, d(h_*\mu) \Big\vert \tilde S \leq g, \tilde S \text{ simple function} \right\}
$$
the inequality in the definition is $\forall y \in Y \tilde S(y) \leq g(y)$. But we are working with the pushforward measure, so we can resctrict this inequality only in the image of $X$ under $h$:
$$
\forall y \in h(X) \quad\tilde S(y) \leq g(y)
$$
this is equivalent to
$$
\forall x \in X \quad \tilde S(h(x)) \leq g(h(x)) 
$$
the inequality can be rewritten to
$$
\tilde S \circ h \leq g \circ h
$$
Let's get back to the definition of the integral above, and use the fact that we proved the substitution formula for the integral of simple functions
$$
\sup \left\{ \int_X \tilde S\circ h\, d\mu \,\Big\vert \tilde S \circ h \leq g\circ h, \tilde S\circ h \text{ simple function} \right\}
$$
where $\tilde S : Y \to [0,\infty)$. Also the composition $\tilde S \circ h$ is a simple function but from $X \to [0,\infty)$. Just call $S := \tilde S \circ h$
$$
\sup \left\{ \int_X S\, d\mu \,\Big\vert S \leq g\circ h, S \text{ simple function} \right\} = \int_X g \circ h \, d\mu
$$
note that we are ignoring the restriction to simple function of the form $\tilde S \circ h$, removing this constraint doesn't change the supremum.

Extending the result to not non-negative function is done as usual, splitting the function in the positive and negative part. $\square$

