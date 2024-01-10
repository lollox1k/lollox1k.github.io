# Flow

>> Given an ODE, we can define a _flow_ in its state space. Each starting conditon moves guided by this flow.

**Def** (flow) A _flow_ on a set $X$ is a group action of the additive group of real numbers $(\mathbb{R},+)$. More explicitly
$$
\Phi : X \times \mathbb{R} \to X
$$
such that, for all $x \in X$ and $s,t \in \mathbb{R}$ the flow has the property
$$
\Phi^0(x) = x \quad \Phi^s \circ \Phi^t (x) = \Phi^{s+t}(x)
$$
From the defnition follows that $\Phi^t : X \to X$ is a bijection with inverse $\Phi^{-t} : X \to X$. 

Usually we require the flow to be compatible with some properties of $X$, for example if $X$ is equipped with a differentiable structure, then $\Phi$ is _required to be differentiable_. In this case the flow forms a _one-parameter group_ of diffeomorphism (differentiable with differentiable inverse).

### Flow of an ODE

Given the ODE
$$
\dot x = u(t,x)
$$
we can define the flow $\Phi^{t,s}(x)$ which solves the ode, given any initial condition $x(s) = x$ (abuse of notation here). Note that we have $2$ real parameters, in the usual definition of flow is assumed $s=0$ (initial time).
That is, the flow satisfies
$$
\frac{d}{dt} \Phi^{t,s}(x) = u(t, \Phi^{t,s}(x))
$$
with initial condition
$$
\Phi^{s,s}(x)=x
$$
We suppose that all the conditions that ensure global existence and uniquness are satisfied [[Teorema di Picard–Lindelöf]].

From the definition of flow of an ODE, follows the property:
$$
\Phi^{t+\epsilon,s}(x) = x + u(x,t)\epsilon + o(\epsilon^2)
$$


The advantage of working with a flow, is that we can ask and answer new question, consider the evolution of a region of initial condition all at once.
For example, suppose (as in reality) that the initial conditions are not known exaclty, we can model this uncertainty with a region of inital condition, equipped with a probability distribution. How far apart does the solutions evolve? 

Suppose the initial state is uniformly distribuited in a set $B$, then its distributio  is
$$
f_0(x) = \frac{1}{|B|} \mathbb{1}_{x \in B}
$$
where $|B|$ is the measure of the set $B$. What can be said about the evolution of such system? Clearly, if we define the evolution of the set $B$ as a whole, (with a slight abuse of notation)
$$
B_t = \Phi^{t,0}(B) = \{\Phi^{t,0}(x) \,\vert\, x \in B)\}
$$
the probability that the system at time $t$ is in $B_t$ is one (solutions don't disappear!), but there's no reason to belive that the distribution is still uniform. How does $f$ evolve? To answer this question, we need to develop some properties of the flow.

**Prop** Let $\Phi^{t,s}$ the flow of the field $u(t,x)$ and $J(x,t,s) = \det\frac{\partial \Phi^{t,s}}{\partial x}$ the determinant of the jacobian of the flux. Then the jacobian satisfies the following linear equation with non-constant coefficients
$$
\frac{d}{dt} \partial_x \Phi^{t,s}(x) = \partial_x u\vert_{t,\Phi^{t,s}(x)}\partial_x \Phi^{t,s}(s)
$$

and $J$ 
$$
\frac{d}{dt}J(x,t,s) = \nabla \cdot u\vert_{t,\Phi^{t,s}(x)} J(x,t,s)
$$
**Proof** The first equation is straight forward, just exchange the derivatives.
To prove the second, we need the following lemma

**Lemma 1** 
$$
\frac{d}{d\epsilon} \det \partial_x \Phi^{t+\epsilon,t}(x) = \nabla \cdot u(t,x)
$$
the use of $\epsilon$ is necessaty, since we want to differentiate $\Phi^{t,t}$ only for the first $t$.

To prove this, we need the [[Determinant near identity lemma]].
With this lemma the proof of lemma $1$ is straightforward. $\square$






