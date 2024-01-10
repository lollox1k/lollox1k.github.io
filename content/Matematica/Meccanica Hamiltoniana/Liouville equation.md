## Dispense
Consider a generic initial probability distribution $f_0$ (w.r.t. Lebesque measure). Let $f(t,x)$ be the probability density at time $t$. For every subset of the phase space $A$ should hold the following
$$
\int_A dx \, f_0(x) = \int_{A_t} dx \, f(t,x)
$$
that is, _probability is conserved_. From this identity, we can solve for $f(t,x)$: just make a change of variable $x = \Phi^{t,0}(y)$ (this makes appear the Jacobian of the flux) [[EDO e flussi|flow of an EDO]]:
$$
\int_A dx \, f_0(x) = \int_{A_t} dx \, f(t,x) = \int_A dx\, f(t,\Phi^{t,0}(x))J(x,t,0)
$$
(where we renamed the new variable $x$). Since this must hold for all $A$ measurable sets, the integrands must be equal a.s:
$$
f_0(x) = f(t,\Phi^{t,0}(x))J(x,t,0)
$$
We are using a simple lemma 
**Lemma** Let $g(x)$ be a locally integrable function, if for every measurable set $A$ 
$$
\int_A g(x) =0
$$
then $g(x)$ is zero a.s.
**Proof** Let's call $A^+ \subseteq A$ the subset of $A$ where $g(x)>0$. Since $g$ is measurable, $A^+$ is measurable. Then, this set must have zero measure. The same is true for $A^-$. So $g(x)=0$ a.s. $\square$

The equation we have found is just the _local conservation of probability_, the Jacobian $J$ tells us how each volume $dx$ need to change to preserve probability.
$$
f_0(x) dx= f(t,\Phi^{t,0}(x))\,J(x,t,0)dx
$$
One can find that this holds also for a non-zero initial time $s$.
We can find a PDE that $f(t,x)$ solves by taking the derivative w.r.t. 
$$
\partial_t [f(t, \Phi^{t,0}(x))]J + f\partial_tJ = 0
$$
the first term is
$$
(\partial_t f + u\cdot\nabla f)\vert_{t, \Phi^{t,0}(x)}
$$
we already computed the time derivative of the Jacobian in the second term [[EDO e flussi|jacobian of the flux]]
$$
(f \,\nabla \cdot u \,J )\vert_{t,\Phi^{t,0}(x)}
$$
putting all togheter
$$
(\partial_t f + u \cdot \nabla f)J + f \text{ div}\,uJ = 0
$$
$J$ starts as $1$ (the jacobian of the flux is the identity at time $0$), and since it solves a linear edo, it can't be zero in finite time.
>> THINK

Hence we can cancel $J$. The first term is a _transport_ term of $f$, the second is the infinitesimal volume variation. With a bit of algebra we can obain the _Liouville equation_:
$$
\partial_t f + \text{ div }uf = 0
$$
In sostanza 
>> L'equazione di Lioville è una legge di conservazione locale della probabilità, con la solita interpretazione del cambio di probabilità totale in $A$ è dovuto ad un flusso $u f$di probabilità attraverso il bordo dell'insieme $\partial A$.

## Arnold

**Theorem (Liouville)** Let be given a system of ODEs $\dot x = f(x)$ with $x = (x_1,\dots,x_n)$ such that solutions are defined for all times. Then we can define the associated [[EDO e flussi|flow]] $g^t$. Let $D_0$ be a region in the phase space, call $v_0$ its volume. For all times:
$$
D(t) = g^t D_0, \quad v(t) = \text{volume } D(t).
$$
Then 
$$
\frac{dv}{dt}\vert_{t=0} = \int_{D_0} \text{div }f dx
$$
**Proof**
$$
v(t) = \int_{D(t)}dx = \int_{D_0} \det{\frac{\partial g^tx}{\partial x}}dx
$$
we did a change of variable, so the determinat of the Jacobian appears.
From the definition of flow
$$
g^t(x) = x + f(x)t + o(t^2) 
$$
so its Jacobian is
$$
\frac{\partial g^tx}{\partial x} = I + \frac{\partial f}{\partial x}t + o(t^2)
$$
using the [[Determinant near identity lemma]], we get
$$
v(t) = \int_{D_0} [1 + t\,\text{div }f + o(t^2)]\,dx
$$
applying the definition of derivative we obtain the result. $\square$


**Corollary** Hamiltonian systems preserves volumes.
**Proof** Just compute the divergence:
$$
\text{ div }f = \partial_q (\partial_p H) + \partial_p(-\partial_qH) = 0
$$
so by Liouville's theorem volumes in the phase space are preserved under time evolution. $\square$






