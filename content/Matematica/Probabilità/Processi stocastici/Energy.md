We assume that the network is finite, that is $V$ and $E$ are finite sets.
As usual We define the Hilbert space $l^2(V)$ of real functions on $V$ with inner product:
$$
(f,g) := \sum_{x \in V}f(x)g(x)
$$
We are interest in [[Electrical networks|flows]], so we extend the edge set $E$ to contain edges in both directrion, $e$ and $-e$, so that a flow is antisymmetric $\theta(-e) = -\theta(e)$. Thus we define $l_{-}^2(E)$ the hilbert space of antysimmetric functions on $E$ with inner product
$$
(\theta, \theta') := \frac{1}{2}\sum_{e\in E} \theta(e)\theta'(e)
$$
Given a voltage function we can build currents, so we define the **coboundary operator** $d: l^2(V)\to l_{-}^2(E)$ by
$$
(df)(e) := f(e^-) - f(e^+)
$$
note that it's linear.

Conversely, given an antisymetric function we can build an operator that computes the net our flow of a given vertex, the **boundary operator** $d^*: l_{-}^2(E) \to l^2(V)$ defined by
$$
(d^*\theta)(x) := \sum_{e \in E\,:\,e^-= x} \theta(e)
$$
which is also linear. 

**Oss** The boundary and coboundary operator are **adjoint** of each other.

**Proof** We need to check that $\forall f, \theta$ 
$$
(df, \theta) = (f,d^*\theta)
$$
from the definition of inner product
$$
\frac{1}{2}\sum_{e\in E} \left[f(e^-) - f(e^+)\right]\theta(e)
$$
$$
= \frac{1}{2} \sum_{e\in E} f(e^-)\theta(e) - \frac{1}{2}\sum_{e\in E} f(e^+)\theta(e)
$$

we can rearrange the first term by highlighting terms $f(x)$
$$
f(x)\left[ \sum_{e^-=x} \theta(e)\right]
$$
and summing. Similarly for the second term
$$
\frac{1}{2}\sum_{x \in V}f(x)\left[ \sum_{e^-=x} \theta(e)\right] - \frac{1}{2}\sum_{x \in V} f(x)\left[ \sum_{e^+=x} \theta(e)\right]
$$
but if $e^+ = x$, then $-e = e^-$ of $x$, so that
$$
= \sum_{x\in V} f(x)(d^*\theta)(x) = (f,d^*\theta) \quad \square
$$

With these definitions we can restate the [[Electrical networks|laws]]:
Let $i$ be a _current_, then

**Ohm's Law**:                   $dv = ir$, that is $\forall e \in E$ $(dv)(e) = i(e)r(e)$
**Kirchhoff's node law**:   $d^*i(x) = 0$ if $x \notin A \cup Z$.


We can think of a flow as a fuild flowing through a network of pipes. The scource are the vetices $a \in A$, the amount of fluid entering the network is just $\sum_{a \in A} d^*\theta(a)$, which is the same amount exiting the network in the sink $Z$.
We call the total amount of current entering the network 
**Def** The **Strenght of the flow** is defined as
$$
\text{Strenght}(\theta) := \sum_{a \in A} (d^*\theta)(a)
$$

**Lemma** (flow conservation) Let $G$ be a finite graph and $A$ and $Z$ be disjoint subsets of its vertices. If $\theta$ is a flow between $A$ and $Z$, then
$$
\sum_{a \in A} (d^*\theta)(a) = - \sum_{z \in Z} (d^*\theta)(z)
$$
**Proof** Since $\theta$ is a flow 
$$
\sum_{x \notin A \cup Z} (d^*\theta)(x) = 0
$$
so that
$$
\sum_{a \in A} (d^*\theta)(a) + \sum_{z \in Z} (d^*\theta)(z) +\sum_{x \notin A \cup Z} (d^*\theta)(x) = \sum_{x \in V}(d^*\theta)(x) 
$$
but this can be written as the inner product
$$
= (d^*\theta, 1) = (\theta, d1) = (\theta, 0) = 0 \quad \square
$$


**Lemma** Let $G$ be a finite graph and $A$ and $Z$ two disjoint subsets of its vertices, and $\theta$ a flow from $A$ to $Z$ and $f$ is constant on $A$ and $Z$ with values $\alpha$ and $\xi$, respectively, then
$$
(\theta, df) = \text{Strength}(\theta)(\alpha-\xi)
$$
**Proof** 
$$
(\theta, df) = (d^*\theta, f) = \sum_{x \in V} (d^*\theta)(x)f(x)
$$
$$
= \alpha\sum_{a \in A} (d^*\theta)(a) + \xi \sum_{z \in Z}(d^*\theta)(z) = \text{Strength}(\theta)(\alpha-\xi) \quad \square
$$

**Def** (Energy) For an antisymmetric function $\theta$, we define its **energy** to be
$$
\mathcal{E}(\theta) := \Vert \theta \Vert_r^2
$$
where we have introduced the norm induced by the inner product which scales each component by the resistence:
$$
(f,g)_r := (fr,g) = (f,gr)
$$

Now we are interested in the energy (dissipated) by a current, so that Kirchhoff's and Ohm's law hold:
$$
\mathcal{E}(i) = (i,i)_r = (ir,i) = (dv,i)
$$
now suppose that we are in the case of the previous lemma, with $f$ beeing a voltage function such taht $f(A)=v_a$ and $f(Z) = v_z$, then
$$
\mathcal{E}(i) = \text{Strength}(i)(v_a-v_z) 
$$
using the relation
$$
v_a-v_b = \text{Strength}(i)\mathcal{R}(A \leftrightarrow Z) 
$$
we can conclude that
$$
\mathcal{E}(i) = \text{Strength}(i)^2 \mathcal{R}(A \leftrightarrow Z) 
$$

### Star and loop decomposition of $l^2_-$

Let's introduce the signed characteristic function of an edge:
$$
\chi^e := \mathbb{1}_e -\mathbb{1}_{-e}
$$
clearly $(\chi^e, \theta)_r = r(e)\theta(e)$.

With this we can rewrite Kirchhoff's laws using the scalar procuct $(\cdot,\cdot)_r$
$$
\left(\sum_{e^-=x} \chi^ec(e), i\right)_r =0 \qquad \forall x \notin (A \cup Z)
$$
$$
\left(\sum_{i=1}^n \chi^{e_i}, i\right)_r = 0 \qquad \forall e_1,\dots, e_n=e_1
$$

Consider the subspaces $\star$ and $◊$, spanned by the functions in the left side of the inner products above:

**Claim 1** $\star \perp ◊$ 
**Proof** Easy for the base elements, make a drawing. $\square$

**Claim 2** We can decompose $l^2_-(E,r) = \star \oplus ◊$ 
**Proof** We show that if $\theta \perp \star$ and $\theta \perp ◊$ then $\theta = 0$.
Then $\theta$ satisfies Kirchhoff's two law, so that there exists a potential $v$ so that $\theta(e) = dv(e)c(e)$. Since $\theta \perp ◊$, $v$ is harmonic everywhere, this implies $v = cost.$ so that $\theta = 0$. $\square$

Now, since any current satisfies Kirchhoff's second law, $i \perp \lozenge$ so that $i \in \star$.
Now take any flow $\theta$ with the same source and sink of a current $i$. Then $\theta-i$ is a souce-less flow, and $\theta-i \perp \star$. We have just found our decomposition:
$$
\theta = i + (\theta -i)
$$

This implies that given the resistences, a current $i$ has the smallest norm (induced by the resistences) among any flow $\theta$ which shares the same soucres $A$ and sinks $Z$:
$$
\Vert \theta \Vert_r^2 = \Vert i \Vert_r^2 + \Vert \theta-i\Vert_r^2
$$
from this follows

**Theorem** (Thomson's Principle) Let $G$ be a finite network, $\theta$ a flow from $A$ to $Z$ and $i$ a current from $A$ to $Z$ such thatr $d^*i = d^*\theta$. 
Then $\mathcal{E}(\theta) > \mathcal{E}(i)$ unless $\theta = i$.
**Proof** Immediate consequence of the previous facts.


**Theorem** (The Nash-Williams inequality) If $a$ and $z$  are distinct vertices in a finite network that are separated by pairwise disjoint cutsets $\Pi_1,\dots,\Pi_n$, then
$$
\mathcal{R}(a \leftrightarrow z) \geq \sum_{k=1}^n \left(\sum_{e \in \Pi_k} c(e)\right)^{-1}
$$
**Proof** We use the equivalence of the energy of a unit current and effective resistence. Consider the unit flow from $a$ to $z$, we can induce a new unit flow in a reduce network: call $K$ the set of vertices still reachable from $a$, and call $Z\subseteq V \setminus K$  the boundary of $\Pi$, . It's easy to see using flow conservation that 
$$
\sum_{x \in Z} d^*i(z) = \sum_{e^+ \in Z} i(e) = 1
$$
this is a unit flow from $a$ to $Z$.  Then by the [[Cauchy-Schwarz inequality]]
$$
\sum_{e \in \Pi} i(e)^2 r(e) \sum_{e \in \Pi} c(e) \geq \left(\sum_{e \in Pi} |i(e)|r(e)^{1/2}c(e)^{1/2}\right)^2 = 
\left( \sum_{e \in \Pi} |i(e)|\right)^2 
$$
$$
\geq \left( \sum_{e^- \in Z} |i(e)|\right)^2 \geq 1
$$
so that
$$
\sum_{e \in \Pi} i(e)^2 r(e) \geq \left(\sum_{e \in \Pi} c(e)\right)^{-1}
$$
by summing over over $k$ we get our result. $\square$


Since enery is related to resistance, and resistance to infinity is realted to transience, we have the following usefull result.

**Theorem** (Rayleigh’s Monotonicity Principle) Let $G$ be a connected graph with two sets of non-negative weights $c$ and $c'$ such that $c \leq c'$.
1. If $G$ is finite and $A$ and $Z$ two disjoint subsets, then
$$
\mathcal{C}_c(A \leftrightarrow Z) \leq \mathcal{C}_{c'}(A \leftrightarrow Z)
$$
2. If $G$ is infinite then 
$$
\mathcal{C}_c(A \leftrightarrow \infty) \leq \mathcal{C}_{c'}(A \leftrightarrow \infty)
$$
in particular if $(G,c)$ is _transient_, then so is $(G,c')$.

**Proof** $2.$ follows simply by $1.$ and taking the limit for a sequnce $G_n$ that exaust $G$. 
To prove $1.$ consider a unit flow from $A$ to $Z$. We have proven that
$$
\mathcal{C}(A \leftrightarrow Z)^{-1} = \mathcal{E}(i)
$$
now
$$
\mathcal{E}_c(i_c) \geq \mathcal{E}_{c'}(i_c) \geq \mathcal{E}_{c'}(i_{c'})
$$
the first inequality follows from the definition of energy (if $r = \frac{1}{c} \geq r')$, the second from Thomson's principle. $\square$
