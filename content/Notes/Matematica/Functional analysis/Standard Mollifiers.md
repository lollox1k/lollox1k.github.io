> [!definition]
> Consider the function
> $$
> \rho(x) = 
> \begin{cases}
> e^-{\frac{1}{1-\Vert x \Vert^2}} \text{ if } \Vert x \Vert < 1 \\
> 0 \text{ otherwise }
> \end{cases}
> $$
> The **standard mollifiers** are the family of functions $\{\rho_\epsilon\}_{\epsilon > 0}$
> $$
> \rho_\epsilon(x) := c_\epsilon \rho(\epsilon x)
> $$ 
> where $c_\epsilon$ is a normalization factor.

The standard Mollifiers are an example of [[Distributions|Test functions]] with the following nice (usefull) properties:
- $\Vert \rho_\epsilon \Vert_{L^1} = 1$ by definition.
- $\rho_\epsilon \in C_c^\infty$ 
- $\lim_{\epsilon \to 0} \rho_\epsilon(x) = \delta_0$ in the sense of [[Distributions]].
- Smoothing property: given any distribution $T$, the family of convolutions
$$
T_{\epsilon} = T * \rho_\epsilon
$$
are smooth functions. 

![[Pasted image 20231121213013.png]]

A nice smooth bump! 👌