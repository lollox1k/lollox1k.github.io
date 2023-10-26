Mathematically an eletrical network is just a non negative weighted graph. We call this edge weights _conductances_, their reciprocals _resistences_. 
The reason for this terminology is that physics can aid our intuition.


**Def** A Network is a tuple $(V,E,c)$ where $c : E \to [0,\infty]$ is a non negative weight function on the edges of the graph (possibly with loops).

In a natural way we can define transition probabilities between state $i,j \in V$:
$$
p(i,j) := \frac{c(ij)}{\sum_{v \in \Gamma(i)} c(iv)}
$$
**Claim** The transition matrix $P$ such defined is reversibile:
**Proof** We show that $c(i) := \sum_{j \in \Gamma(i) c(ij)}$ is an invariant measure, since it satisfies [[Reversibile Markov Chains|detailed balance]]:
$$
c(i)p(i,j) = c(ij) = c(j)p(j,i), \qquad \square
$$

The converse is also true: evert reversible markov chain can be turned into a network (we can find the right conductances) by using the function $\lambda$ that satisfies D.B:
$$
c(ij) := P(i,j)\lambda(i)
$$
We now show that this works. Note that reversibility is necessary, since $c(ij)=c(ji)$. Also we have the desired transition probabilities, since
$$
c(i) = \sum_{j \in \Gamma(i)} c(ij) = \sum_j P(i,j)\lambda(i) = \lambda(i)
$$
so that the transition probabilities are
$$
\frac{c(ij)}{c(i)} = \frac{P(i,j)}{\lambda(i)}\lambda(i) = P(i,j) \quad \square
$$

**Def** (_Voltage_) Given two disjoint subsets $A$ and $Z$ of vertices of a network, a _voltage_ is a function on the vertices of the network such that is [[Harmonic functions|harmonic]] on all $x \notin A \cup Z$. Usually the voltage is specified to be $1$ on $A$ and $0$ on $Z$.

**Def** (_Current_) Given a voltage on a network the current is a function $i : V \times V \to \mathbb{R}$ defined as:
$$
i(x,y) := c(x,y)[v(x)-v(y)]
$$
**Remarks** From the definition we see that $i$ is antisymmetric
$$
i(x,y)=-i(y,x)
$$
Also if $v$ is harmonic at $x$ (that is $x \notin A \cup Z$) we can se that
$$
\sum_{y\sim x} i(x,y) = v(x)\sum_{y \sim x}c(x,y)- \sum_{y \sim x}v(y)c(x,y) = 0
$$
A function that satisfies these two properties is called a **flow** from source $A$ to sink $Z$.

This definition and remarks can be stated as the familiar Ohm's and Kirchhoff's laws:

- **Ohm's law** 
$$
v(x)-v(y) = i(x,y)r(x,y)
$$
- **Kirchhoff's node law** The current is a flow from $A$ to $Z$.

- **Kirchhoff's cycle law**  If $x_1\,x_2\,\dots\, x_n=x_1$ is a cycle, then
$$
\sum_{i=1}^n r(x_i,x_{i+1})i(x_i, x_{i+1}) = 0
$$
The cycle law can be proven by summing Ohm's law.


A more general statement can be proven:

**Claim** Given an antisymmetric function $j$ on the edges of a connected network that satiesfies Kirchhoff node and cycle law, show that we can construct a voltage function up to an additive function such that $j$ is its associeted current.
**Proof** Choose a vertex $\overline x \in V$, and fix the value $v(\overline x) = K$.
Define the voltage $v$ for every other vertex $x \in V$ as:
$$
v(x):= \sum_\mathcal{P} i(x_i,x_{i+1})r(x_i,x_{i+1}) + K
$$
where $\mathcal{P}$ is any path from $x$ to $\overline x$. 
This function is well defined, since at least one such paths exists (the network is connected), and the value of $v(x)$ doesn't depend on the path choosen: suppose $\mathcal{P}$ and $\mathcal{P}'$ are two different path from $x$ to $\overline x$, joining them (one in reverse order) we get a cycle, using Kirchhoff cycle law their difference is zero:
$$
\sum_\mathcal{P} j(x_i,x_{i+1})r(x_i,x_{i+1}) - \sum_{\mathcal{P}'} j(x_i,x_{i+1})r(x_i,x_{i+1}) = 
$$
$$
\sum_\mathcal{P} j(x_i,x_{i+1})r(x_i,x_{i+1}) + \sum_{\mathcal{P}'} j(x_{i+1},x_i)r(x_{i+1},x_i) = 0
$$
where we have used the antisymmetri of the flow and the symmetry of the resistences.

It remains to show that $v$ is harmonic. Let $y$ be a neighbour of $x$, then
$$
v(x) = r(x,y)j(x,y) + v(y)
$$
rearrenging this identity and summing over all neighbours $y$ we get
$$
v(x)\sum_{y\sim x}c(x,y) = \sum_{y\sim x}j(x,y) + \sum_{y\sim x}v(y)c(x,y) 
$$
the first term on the right is zero since $j$ is a flow. We are left with the definition of an harmonic function at $x$. $\square$

