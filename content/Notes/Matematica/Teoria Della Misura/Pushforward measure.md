# Pushforward measure
AkA image measure.

Let $(X,\mathcal{F})$ and $(Y, \mathcal{E})$ be two measurable spaces, and a [[Funzioni misurabili|measurable map]] $h : X \to Y$.

Suppose we have a [[Misura|measure]] $\mu : \mathcal{F} \to [0,\infty]$ on the first set, we can define a new measure $\lambda : \mathcal{E} \to [0,\infty]$ for $Y$ using the function $h$, in the following manner:
$$
\lambda(E) := \mu(h^{-1}(E)), \qquad E \in \mathcal{E}
$$
this is well defined, since $h$ is measurable, so that $h^{-1}(E) \in \mathcal{F}$, and $\lambda$ is a measure since the preimage $h^{-1}$ behaves "well" w.r.t. set operations.

Other notations used are:
$$
h_*\mu \qquad \mu \circ h^{-1} \qquad h\#\mu
$$

