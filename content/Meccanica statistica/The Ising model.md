


### Finite volume pressure

### Infinite volume pressure
**Proposition** In the thermodynamic limit the **pressure** 
$$
\psi(\beta, h) := \lim_{\Lambda_n \uparrow \mathbb{Z}^d} \frac{1}{|\Lambda_n|} \log Z_{\Lambda_n}^\#(\beta,h)   
$$
is well defined, indipendent of the sequence $\Lambda_n$ and the boundary conditions. Moreover $\psi$ is convex in $\mathbb{R}_{\geq 0} \times \mathbb{R}$ and symmetric in $h$ (like the finite volume pressure). 

**Proof** 
1. **A new Hamiltonian $\mathcal{\overline H}$**
First a trick to ensure that the interaction energy across boudaries is always positive:
writing $(\omega_i\omega_j -1)+1$ in the Hamiltonian one can write
$$
\mathcal{H}_{\Lambda, \beta,h}^\#(\omega) = \mathcal{\overline H}_{\Lambda, \beta,h}^\#(\omega) -\beta| E_\Lambda|
$$
Let $\Lambda_1 \cap \Lambda_2 = \emptyset$, then 
$$
\mathcal{\overline H}_{\Lambda_1 \cup \Lambda_2}(\omega) = \mathcal{\overline H}_{\Lambda_1}(\omega) + \mathcal{\overline H}_{\Lambda_2}(\omega) + R
$$
where the interaction energy $R$ is
$$
R = -\beta \sum_{i\sim j \,\,\, i\in\Lambda_1\,\,\, j \in \Lambda_2} (\omega_i\omega_j -1) \geq 0
$$
so that 
$$
\mathcal{\overline H}_{\Lambda_1 \cup \Lambda_2}(\omega) \geq \mathcal{\overline H}_{\Lambda_1}(\omega) + \mathcal{\overline H}_{\Lambda_2}(\omega)
$$
but this implies that the partition function is submultiplicative (it's also translation invariant by definition):
$$
\overline Z_{\Lambda_1 \cup \Lambda_2} \leq \overline Z_{\Lambda_1}\overline Z_{\Lambda_2}
$$
2. **Existence of the limit for sequences of boxes $\mathcal{R}$** 
so that the pressure is subadditive. Using [[Limite di successioni subadditive#Lemma Fekete|Fekete's lemma]] we know that the following limit exists:
$$
\lim_{n\to\infty} \frac{1}{|\Lambda_n|} \log \overline Z_{\Lambda_n, \beta, h} = \inf_n \frac{1}{|\Lambda_n|} \log \overline Z_{\Lambda_n, \beta, h}
$$
also since $\mathcal{\overline H} \leq -\beta(-2|E_\Lambda|) +|h||\Lambda|$ we can bound from below the partition function
$$
\overline Z_{\Lambda, \beta, h} \geq e^{\ln2 |\Lambda| +2\beta|E_\Lambda| + |h||\Lambda|}
$$
and the pressure
$$
\frac{1}{|\Lambda_n|} \log \overline Z_{\Lambda_n, \beta, h} \geq \ln 2 + |h| + 2\beta \frac{|E_{\Lambda_n}|}{|\Lambda_n|} \geq Const.
$$
note that the number of edges is bounded for example by $d|\Lambda|$ (view the lattice a a graph and use the [[Handshake Lemma]]).
So the $\inf$ is a finite number, and the limit exists.

Now the existence of this limit implies the existence of the pressure, since they differ by a term
$$
\lim_{n\to\infty}\frac{1}{|\Lambda_n|} \log Z_{\Lambda_n, \beta, h} = \lim_{n\to\infty}\frac{1}{|\Lambda_n|} \log \overline Z_{\Lambda_n, \beta, h}  - \beta\frac{|E_{\Lambda_n}|}{|\Lambda_n|}
$$

the last term (which also has a limit since we can apply Feket's lemma) can be computed and is equal to
$$
\lim_{n\to\infty} \frac{|E_{\Lambda_n}|}{|\Lambda_n|} = d
$$
So we have proven the existence of the pressure for any sequences of rectangles that converges to $\mathbb{Z}^d$. 

3. **estenzione a sequenze di volumi nel senso di Van Hove**
To extend this result to any sequence $\Lambda_n \uparrow \mathbb{Z}^d$ in the sense of Van Hove, the idea it to approximate any volumes by rectangles, the Van Hove condition ensures that in the limit the difference goes to zero.

![[Pasted image 20220909170512.png]]

Consider the simple sequence of cubes $B_n = \{-n,\dots,n\}^d$.  Since this is a sequence of rectangles such that $B_n \uparrow \mathbb{Z}^d$, we now that the limit
$$
\lim_{n\to\infty} \frac{1}{|B_n|} \log Z_{B_n,\beta,h} = \psi(\beta,h)
$$
We now decompose a generic volume $\Lambda_n$ in disjoint translates of boxes $B_k$, for a given $k$ such that $\Lambda_n \subset [\Lambda_n] := \cup D_k$

We need to show that in the limit the difference of the pressure goes to zero, i.e. we want to exstimate:
$$
\vert \psi_{\Lambda_n}  - \psi\vert \leq \vert \psi_{\Lambda_n} - \psi_{[\Lambda_n]}\vert + \vert \psi_{[\Lambda_n]}-\psi_{B_k}\vert + \vert \psi_{B_k}-\psi\vert
$$
Given ant $\epsilon > 0$, for any $k \geq k_1$ we now that the last term is less than $\epsilon$ since $\psi_{B_k} \to \psi$.

Let's compute $\mathcal{H}_{[\Lambda_n]}$:
$$
 \mathcal{H}_{[\Lambda_n]} = \sum_j  \mathcal{H}_{B_k^{(j)}} + W_n
$$
Where the term $W_n$ is the energy due to the interaction between the regions $B_k$. The interaction can be bounded by
$$
|W_n| \leq 2d\beta  \frac{| [\Lambda_n]|}{|B_k|}(2k+1)^{d-1} = 2d\beta |[\Lambda_n]|(2k+1)^{-1}
$$
so that 
$$
\frac{|[\Lambda_n]|}{|B_k|} \mathcal{H}_{B_k} - 2d\beta |[\Lambda_n]|(2k+1)^{-1}\leq\mathcal{H}_{[\Lambda_n]} \leq \frac{|[\Lambda_n]|}{|B_k|} \mathcal{H}_{B_k} + 2d\beta |[\Lambda_n]|(2k+1)^{-1}
$$
$$
\left| \mathcal{H}_{[\Lambda_n]} - \frac{|[\Lambda_n]|}{|B_k|} \mathcal{H}_{B_k} \right| \leq 2d\beta |[\Lambda_n]|(2k+1)^{-1}
$$
from this follows that the partition function is bounded by
$$
e^{-2d\beta |[\Lambda_n]|(2k+1)^{-1}} Z_{B_k}^{\frac{|[\Lambda_n]|}{|B_k|}} \leq Z_{[\Lambda_n]} \leq e^{+2d\beta |[\Lambda_n]|(2k+1)^{-1}} Z_{B_k}^{\frac{|[\Lambda_n]|}{|B_k|}}
$$
so that the pressure
$$
|\psi_{[\Lambda_n]} - \psi_{B_k}| \leq 2d\beta(2k+1)^{-1} < \epsilon
$$
for $k$ big enough, say $\forall k \geq k_2$.

Let us write $\Delta_n := [\Lambda_n] \setminus \Lambda_n$, then it's easy to see that 
$$
|\mathcal{H}_{[\Lambda_n]}(\omega) - \mathcal{H}_{\Lambda_n}(\omega|_{\Lambda_n})| \leq (2d\beta + |h|)|\Delta_n|
$$
so that for the partition function
$$
Z_{[\Lambda_n]} = \sum_{\omega \in \Omega_{[\Lambda_n]} } e^{-\mathcal{H}_{[\Lambda_n]}(\omega)} \leq \sum_{\omega \in \Omega_{[\Lambda_n]} } e^{-\mathcal{H}_{\Lambda_n}(\omega|_\Lambda) + (2d\beta + |h|)|\Delta_n|}
$$
$$
= 2^{|\Delta_n|} Z_{\Lambda_n}e^{(2d\beta + |h|)|\Delta_n|}
$$
the same can be down for a lower bound. This yields
$$
|\log Z_{\Lambda_n} - \log Z_{[\Lambda_n]}| \leq (2d\beta + |h|)|\Delta_n|
$$

we now use the Van Hove condition, since we can bound the number of spins in $\Delta_n$ by
$$
|\Delta_n| \leq |B_k||\partial^{in}\Lambda_n|
$$
from this
$$
\left|\psi_{\Lambda_n} - \frac{1}{|\Lambda_n|}\log Z_{[\Lambda_n]}\right| \leq (2d\beta + |h|)|B_k|\frac{|\partial^{in}\Lambda_n|}{|\Lambda_n|}
$$
for $n$ big enough, the right side is smaller than $\epsilon$. Also the term inside the absolute values approches the pressure $\psi_{[\Lambda_n]}$ since
$$
1 \leq \frac{|[\Lambda_n]|}{|\Lambda_n|} = 1 + \frac{|\Delta_n|}{|\Lambda_n|} \leq 1 + |B_k| \frac{|\partial^{in}\Lambda_n|}{|\Lambda_n|} \to 1 
$$

4. **Indipendence of boundary condition

This follows from the fact that
$$
| \mathcal{H}^\eta_\Lambda(\omega) - \mathcal{H}_\Lambda(\omega)| \leq (2d\beta + |h|)|\partial^{in}\Lambda|
$$
so the finite volume pressures differ by a $O(|\partial^{in} \Lambda| / |\Lambda|$) which vanishes in the termodinamic limit thanks to the Van Hove condition. $\square$




### Magnetization

A natural macroscopic variable is the *average magnetic moment*, or the *magnetization density*:
$$
m_\Lambda := \frac 1{|\Lambda|} \sum_{i \in \Lambda} \sigma_i
$$

By direct computation 
$$
m^\#_\Lambda(\beta, h) = \frac{\partial \psi^\#_\Lambda(\beta,h)}{\partial h}
$$

An interesting question is wether it holds in thermodynamic limit
$$
m(\beta, h) = \lim_{\Lambda_n \uparrow \mathbb{Z}^d}\frac{\partial \psi^\#_\Lambda(\beta,h)}{\partial h} \stackrel{?}{=} \frac \partial {\partial h}\lim_{\Lambda_n \uparrow \mathbb{Z}^d} \psi_\Lambda^\#(\beta,h) = \frac {\partial \psi(\beta,h)}{\partial h}
$$

This depends on the differentiability of $\psi$ w.r.t $h$. Since it's convex, we know that the left and right derivatives always [[Funzioni convesse#Proprietà|exists]], and that $\psi$ is not differentiable in a set of measure zero. 

Moreover, when $\psi$ is differentiable the limit exchange [[Funzioni convesse#Proprietà|holds]]. 
This fact, that the magnetization density is discontinuos when $\psi$ is non differentiable, leads us to a first definition of phase transition:

**Def** (First order phase transition) The pressure $\psi$ exhibits a **first order phase transition** at $(\beta,h)$ is it fails to be differentiable w.r.t $h$ in this point. 

Nota that since $\psi$ in _indipendent from the boudary conditions_, if $\psi(h,\beta)$ is differentiable, the magnetization density in indipendent from the boundary condition, e.s. $+$ or $-$.  This means that we don't see a _macroscopic instability_. On the other hand, if $\psi$ fails to be differentiable, (hence we have a first order phase transition), the value of $m = \lim_{n\to\infty} m^\#_{\Lambda_n}$ _depends on the boundary conditions_: we have sensibility form b.c.: macroscopic instability.  


### One-Dimensional Ising Model

The 1D Ising model is exactly solvable, we can compute the pressure. This was Ising doctorate thesis main result. The trick is to a _trasnfer matrix_, and writing the partition function as the trace of power of this matrix.

For simplicity consider the periodic b.c. (we know that the pressure is insensitive to b.c.)
$$
Z_{\Lambda_n, \beta, h} = \sum_{\omega \in \Omega_\Lambda} e^{-\mathcal{H}_{\Lambda_n,\beta,h}(\omega)}
$$
$$
\sum_{\omega_0 = \pm 1}\sum_{\omega_1 = \pm 1}\cdots \prod_{i=0}^{n-1} e^{\beta\omega_i\omega_{i+1} +h\omega_i}
$$
We can define a $2\times 2$ matrix $A$ 
$$
A = \begin{pmatrix}
e^{\beta +h} & e^{-\beta + h}\\
e^{-\beta -h} & e^{\beta -h}
\end{pmatrix}
$$
if we compute $A^2$ 
$$
A^2 = 
\begin{pmatrix}
e^{\beta +h}e^{\beta +h} + e^{-\beta +h}e^{-\beta -h} & e^{\beta+h}e^{-\beta+h} + e^{-\beta+h}e^{\beta-h}\\
e^{-\beta -h}e^{\beta +h} +  e^{\beta-h}e^{}& e^{-\beta -h}e^{-\beta +h} + e^{\beta-h}e^{\beta-h} 
\end{pmatrix}
$$
The trace is precisely $Z$ with two particles. In general
$$
Z = Tr(A^N) = \lambda_1^N + \lambda_2^N
$$
thus the pressure is (since $|\Lambda_n |= N$)
$$
\psi(\beta,h) = \lim_{n\to\infty} \frac{1}{|\Lambda_n|} \log Z = \lim_{N\to\infty} \frac{1}{N}\log \lambda_1^N\left(1 + \frac{\lambda_2^N}{\lambda_1^N}\right) = \log\lambda_1
$$
where $\lambda_1$ is the maximum modulus eigenvalue so that 
$$
\left(\frac{\lambda_2}{\lambda_1}\right)^N \rightarrow 0
$$

the eigenvalues of $A$ are:
$$
\lambda_{1,2} = e^{\beta\cosh(h)} \pm \sqrt{e^{2\beta}\cosh^2(h)-2\sinh(2\beta)}
$$
this shows that the pressure is _analytic_ and differentiables for every value $(\beta,h)$. We can conclude that _there isn't a first order phase transition_.

One can compute the magnetization $m$ and show that it's continuos, in particular the spontaneus magnetization
$$
m^*(\beta) := \lim_{h\downarrow 0} m(\beta,h) = m(\beta,0) = 0 \quad \forall \beta \geq 0
$$



### Infinite volume Gibbs state

Here we define an infinite volume Gibbs state, as a linear functional on local functions. The link of this section with [[Misure di Gibbs a volume infinito|Infinite-volume Gibbs measures]] is given by the [[Riesz represebtation theorem]].

**Def** An **Infinite-volume Gibbs state** is a functional mapping a local function $f$ to a real number $\langle f \rangle$ satisfying:
1. Normalization $\langle 1 \rangle = 1$
2. Positivity $\langle f \rangle \geq0$ when $f\geq 0$
3. linearity $\langle f + \alpha g \rangle = \langle f \rangle + \alpha\langle g \rangle$ for all $\alpha \in \mathbb{R}$
The number $\langle f \rangle$ is called the **average of $f$ in the state $\langle \cdot\rangle$**.

It's natural to define convergence of finite volume Gibbs distribution to infinite volume state, if for any local function $f$ 
$$
\mu_{\Lambda_n,\beta,h}^{\#_n} (f) \to \langle f \rangle
$$
This is precisley the notion of [[Weak convergence of probability mesures on metric spaces|weak convergence of probability measure]], where the average of $f$ as
$$
\langle f \rangle = \int f\,d\mu
$$


Can we construct infinite volume Gibbs state as a limit of finite volume Gibbs distribution, in the sense of the previous limit? We study the case of two simple boundary conditions, which will be central in the analysis of the general case.

**Theorem** Let $\beta \geq 0$ and $h \in \mathbb{R}$. Given any sequence $\Lambda_n \uparrow \mathbb{Z}^d$, the finite volume Gibbs distribution with $+$ or $-$ boundary conditions converge to infinite volume Gibbs state:
$$
\langle \cdot \rangle_{\beta,h}^+ = \lim_{n\to\infty} \langle\cdot \rangle_{\Lambda_n, \beta,h}^+ \qquad \langle \cdot \rangle_{\beta,h}^- = \lim_{n\to\infty} \langle\cdot \rangle_{\Lambda_n, \beta,h}^-
$$
and the state obtained do not depend on the sequence $\Lambda_n$ and are both _translation invariant_.

**Remark** Not that in general $\langle \cdot \rangle_{\beta,h}^+ \neq \langle \cdot \rangle_{\beta,h}^-$. This is the case when at $(\beta,h)$ there is a first order phase transition.

**Proof** We use a representation of a local function as sums of occupation numbers
$$
f(\omega) = \sum_{A \subset supp(f)} \hat f_A n_A(\omega)
$$
then by linearity the result is valid for all local functions, if we prove it for $n_A$ functions. Since $n_A$ are non-decreasing, we can use a consequence of the FKG inequality:
$$
\langle n_A \rangle^+_{\Lambda_n} \geq \langle n_A \rangle^+_{\Lambda_{n+1}}
$$
thus this sequence is non-increasing, and since it's non-negative it converges. Thus by linearity for each local function
$$
\lim_{n\to\infty} \langle f\rangle^+_{\Lambda_n} = \langle f \rangle^+
$$
is well defined. It' linear, positive and normalized, so it's a Gibbs state. 
To show volume sequence independence, let $\Lambda^1_n, \Lambda^2_n \uparrow \mathbb{Z}^d$ we build a new sequence $\Delta_k \uparrow \mathbb{Z}^d$ in the following way:
$$
\Delta_{2k-1} = \text{ some } \Lambda_n^1 \qquad \Delta_{2k} = \text{ some } \Lambda_n^2 \text{ s.t.} \Delta_{2k-1}\subset \Delta_{2k}
$$
in words: we choose for odd numbers a set in $\Lambda^2$ and for even numbers a set in $\Lambda^2$, such that the sequence in increasing (we can always do that). Now the limit 
$$
\langle f \rangle^+_{\Delta_k} \to \langle f \rangle^+
$$
exists, but by construct $\Delta_k$ is a subsequence of both $\Lambda_1$ and $\Lambda_2$ hence their limit is the same.

Translation invariance follows from this, since we can cancel the effect of a translation of states by the inverse translation on the volumes, but we have just shown that the limit is indipendent from the sequence of volumes!
$$
\lim_{n\to \infty} \langle f \circ\theta_i\rangle^+_{\Lambda_n} = \lim_{n\to \infty} \langle f \circ\theta_i \rangle^+_{\theta_{-i}\Lambda_n}
= \lim_{n\to \infty} \langle f \rangle^+_{\Lambda_n} = \langle f \rangle^+ \qquad \square
$$


### Criteria for uniqueness

States prepared with $+$ and $-$ boundary conditions are usefull to study the question of uniquess of Gibbs states.

**Theorem** let $(\beta,h) \in \mathbb{R}_{\geq0} \times \mathbb{R}$. The following are equivalent:
1. There is a unique Gibbs state at $(\beta,h)$
2. $\langle \cdot \rangle^-_{\beta,h} = \langle \cdot \rangle^+_{\beta,h}$
3. $\langle \sigma_0 \rangle^-_{\beta,h} = \langle \sigma_0 \rangle^+_{\beta,h}$

**Proof** $1 \implies 2 \implies 3$ are trivial. 
$2 \implies 1$ follows from the inequality we have proven:
$$
\langle n_A \rangle^- \leq \langle n_A\rangle\leq \langle n_A\rangle^+
$$
but any local function can be written as linear combination of $n_A$.
$3 \implies 2$ The function $\sum_{i \in A} n_i - n_A$ is non-decreasing, so that
$$
\langle \sum_{i \in A} n_i - n_A \rangle^- \leq \langle \sum_{i \in A} n_i - n_A \rangle^+
$$
using linearity and rearrenging
$$
\sum_{i \in A}( \langle n_i\rangle^+ + \langle n_i\rangle^- ) \geq  \langle n_A \rangle^+-\langle n_A\rangle^-
$$
but in the limit, using translation invariance the left hand side vanishes. So for any local function $f$ the averages coincide. $\square$ 

### Correlation inequalities

**Theorem** (GKS inequality) Let $j_{ij}$ and $h_i$ be collections of non-negative real numbers. Then, for all $A,B \subset \Lambda$,
$$
\langle \sigma_A\rangle^+_{\Lambda,J,h} \geq 0\qquad
\langle \sigma_A\sigma_B\rangle^+_{\Lambda,J,h} \geq \langle \sigma_A\rangle^+_{\Lambda,J,h}\langle \sigma_B\rangle^+_{\Lambda,J,h}
$$

**Theorem** (FKG inequality) Let $f$ and $g$ be non-decreasing function, $J_{ij}$ be a collection of non-negative real numbers, $h$ a collection of real numbers (we allow negative values), $\#$ any boundary condition, then
$$
\langle fg\rangle^\#_{\Lambda,J,h} \geq \langle f\rangle^\#_{\Lambda,J,h}\langle g\rangle^\#_{\Lambda,J,h}
$$

From FKG inequality follows an intuitive inequality if we consider non-decreasing function $f$ and two volumes $\Lambda_1 \subset \Lambda_2$:
$$
\langle f \rangle^+_{\Lambda_1, \beta, h} \geq  \langle f \rangle^+_{\Lambda_2, \beta, h}
$$
since the indicator function $\mathbb{1}(\sigma_i = 1\, \forall i \in \Lambda_2\setminus\Lambda_1)$ is non-decreasing.
$$
\langle f \rangle^+_{\Lambda_1, \beta, h} = \frac{\langle f \mathbb{1}(\sigma_i = 1\, \forall i \in \Lambda_2\setminus\Lambda_1)\rangle^+_{\Lambda_2, \beta, h}}{\langle \mathbb{1}(\sigma_i = 1\, \forall i \in \Lambda_2\setminus\Lambda_1)\rangle_{\Lambda_2,\beta,h}} \geq \langle f \rangle^+_{\Lambda_2, \beta, h}
$$

Non-decreasing functions are functions that "like" $+1$ spins. In this sense it's intuitive to think of the boudnary conditions $-$ and $+$ as extremal.

**Lemma** Let $f$ be a non-decreasing function. Then for any boundary condition $\eta$, and $\beta \geq 0$, $h \in \mathbb{R}$, $\Lambda \Subset \mathbb{Z}^d$
$$
\langle f \rangle^-_{\Lambda,\beta,h} \leq \langle f \rangle^\eta_{\Lambda,\beta,h} \leq \langle f \rangle^+_{\Lambda,\beta,h}
$$
**Proof** Let $I(\omega) :=  e^{\beta\sum_{i\sim j\quad i\in\Lambda,\,j\notin\Lambda} \omega_i(1-\eta_j)}$ and note that
$$
\sum_{\omega \in \Omega^+_\Lambda} e^{-\mathcal{H}(\omega)} = \sum_{\omega \in \Omega^\eta_\Lambda} e^{-\mathcal{H}(\omega)}I(\omega)
$$
$$
\sum_{i\sim j\quad i,j \in \Lambda} \omega_i\omega_j + \sum_{i\sim j\quad i\in\Lambda,j \notin \Lambda} \omega_i\omega_j + \sum_{i\sim j\quad i\in\Lambda,j \notin \Lambda} \omega_i(1-\eta_j)
$$
but $j\notin\Lambda$ so $\omega_j = \eta_j$.
$$
\sum_{i\sim j\quad i\in\Lambda,j \notin \Lambda} \omega_i1
$$
these are the $+$ boundary conditions. 
Then
$$
\sum_{\omega \in \Omega^+_\Lambda} e^{-\mathcal{H}(\omega)}f(\omega) \geq \sum_{\omega \in \Omega^\eta_\Lambda} e^{-\mathcal{H}(\omega)}I(\omega)f(\omega)
$$
using FKG inequality, since $I$ is non-decreasing also
$$
\langle f \rangle^+_\Lambda  \geq \frac{\sum_{\omega \in \Omega^+_\Lambda} e^{-\mathcal{H}(\omega)}f(\omega)}{\sum_{\omega \in \Omega^+_\Lambda} e^{-\mathcal{H}(\omega)}} \geq \frac{\sum_{\omega \in \Omega^\eta_\Lambda} e^{-\mathcal{H}(\omega)}I(\omega)f(\omega)}{\sum_{\omega \in \Omega^\eta_\Lambda} e^{-\mathcal{H}(\omega)}I(\omega)} = \frac{\langle f I\rangle^\eta_\Lambda}{\langle I\rangle^\eta_{\Lambda}} \geq \langle f \rangle^\eta_\Lambda
$$


### Spontaneus symmetry breaking at low temperatures

Characterization of uniqueness so far:
$$
 \frac{\partial \psi(\beta,h)}{\partial h} \text{ exists }  \iff m^-(\beta,h) = m^+(\beta,h) \iff \langle \sigma_0\rangle^-_{\beta,h} =\langle \sigma_0\rangle^+_{\beta,h}
$$


Our goal is to prove that $\beta_c(d) < \infty$ for all $d\geq 2$. To do so it's sufficient to show that
$$
\mu_{\Lambda,\beta,0}^+(\sigma_0 = -1) \leq \delta(\beta)
$$
where $\delta(\beta) \to 0$ when $\beta\to\infty$.

This follows form
$$
\langle \sigma_0\rangle^+_{\Lambda,\beta,0} = \mu_{\Lambda,\beta,0}^+(\sigma_0 = +1) -\mu_{\Lambda,\beta,0}^+(\sigma_0 = -1)
$$
$$
= 1-2\mu_{\Lambda,\beta,0}^+(\sigma_0 = -1)
$$
so that for $\beta$ large enough  $\langle \sigma_0\rangle^+_{\Lambda,\beta,0} > 0$ 
but this implies, since we have symmetry by spin reverse ($h=0$)
$$
\langle \sigma_0\rangle^-_{\Lambda,\beta,0}=-\langle \sigma_0\rangle^+_{\Lambda,\beta,0}
$$
so we can conclude that 
$$
\langle \sigma_0\rangle^-_{\Lambda,\beta,0} \neq\langle \sigma_0\rangle^+_{\Lambda,\beta,0}
$$

since
$$
m^*(\beta) := \lim_{h\downarrow 0} m(\beta,h) = \lim_{h\downarrow 0} m^+(\beta,h) = m^+(\beta,0) = \langle \sigma_0\rangle_{\beta,0}^+
$$

we define the critical temperature as 
$$
\beta_c(d) := \inf\{ \beta \geq 0\,:\, m^*(\beta) > 0\}
$$

### Peierls' argument

First a simple revrite of the Hamiltonian
$$
\mathcal{H}_{\Lambda,\beta,0} = -\beta\sum_{(i,j)\in E_\Lambda} \sigma_i\sigma_j = -\beta|E_\Lambda| +\beta\sum_{(i,j) \in E_\Lambda}(1-\sigma_i\sigma_j)
$$

**Dual lattice** $\mathbb{Z}^d_* := \mathbb{Z}^d + (\frac12,\frac12)$
We are surronding each spin $i$ with a unit squared $Q_i$ centered at the spin. Our goal is to build "island" of negative spins (in a sea of positive ones):
$$
M(\omega) := \bigcup_{i\in \Lambda\,:\, \sigma_i = -1} Q_i
$$
the the boundary of this set $\partial M(\omega)$ is composed of edges in the dual lattice: each edge separates two opposite sign spins, thus we can rewrite the Hamiltonian as
$$
 -\beta|E_\Lambda| +2\beta |\partial M(\omega)|
$$
we now decompose $\partial M(\omega)$ in disjoint sets (islands), by introducing a _deformation rule_ to take care of possibile intersection of the form $+$. Now $\partial M$ is a union of closed curves
$$
\partial M(\omega) = \gamma_i \cup \gamma_2 \cup\cdots\cup \gamma_n
$$
each curve is called a _contour path_ of $\omega$, we denote their lenght with $|\gamma|$.
We again rewrite the hamiltonian as
$$
-\beta|E_\Lambda| + 2\beta \sum_{\gamma \in \Gamma(\omega)} |\gamma|
$$
thus the partition function is
$$
Z^+_{\Lambda,\beta,0} = \sum_{\omega \in \Omega^+_\Lambda} e^{\beta|E_\Lambda| - 2\beta \sum_{\gamma \in \Gamma(\omega)} |\gamma|}
$$
the constant term $\beta|E_\Lambda|$ doesn't change probabilities, since it cancels out:
$$
\mu(\omega)_{\lambda,\beta,0}^+ = \frac{e^{- 2\beta \sum_{\gamma \in \Gamma(\omega)} |\gamma|}}{\sum_{\omega \in \Omega^+_\Lambda} e^{- 2\beta \sum_{\gamma \in \Gamma(\omega)} |\gamma|}}
$$

Notice that if $\sigma_0 = -1$, then there exists a contour curve $\gamma$ such that $0 \in Int(\gamma)$. We can bound the probability:
$$
\mu(\sigma_0 = -1)^+_{B(n), \beta,0} \leq \mu(
\exists \gamma\,:\, 0 \in Int(\gamma))^+_{B(n), \beta,0}
$$
$$
\leq \sum_{\gamma :\, Int(\gamma) \ni 0} \mu(\gamma \in \Gamma)^+_{B(n), \beta,0}
$$

**Claim** For all $\beta > 0$ and any contour $\gamma$:
$$
\mu(\gamma \in \Gamma)^+_{B(n), \beta,0} \leq e^{-2\beta|\gamma|}
$$
**Proof** 
$$
\mu(\gamma \in \Gamma)^+_{B(n), \beta,0} = \sum_{\omega: \gamma\in \Gamma(\omega)} \mu(\omega)_{B(n),\beta,0}^+
$$
$$
= e^{-2\beta|\gamma|}\frac{\sum_{\omega: \gamma \in \Gamma(\omega)} \prod_{\Gamma \setminus \gamma} e^{- 2\beta  |\gamma'|}}{\sum_{\omega \in \Omega^+_\Lambda} \prod_{\Gamma}e^{- 2\beta |\gamma'|}}
$$
we need to show that the big fraction is bounded above by $1$. Indeed the sum in the denominator is the same as the denominator, with an additional constraint. Indeed a given configuration such that $\Gamma(\omega) \ni \gamma$, can be transformed into one that doesn't contain $\gamma$, simply by flipping all the spins inside $Int(\gamma)$. The new state has contour sets precisley $\Gamma(\omega)\setminus \{\gamma\}$ 
Call $C(\gamma)$ the set of configurations that can be obtained by removing $\gamma$, clearly $C(\gamma) \subseteq \Omega^+_{B(n)}$ so that
$$
\sum_{\omega: \gamma \in \Gamma(\omega)} \prod_{\Gamma \setminus \gamma} e^{- 2\beta  |\gamma'|} = 
\sum_{\omega' \in C(\gamma)}\prod_{\gamma' \in\Gamma} e^{-2\beta |\gamma'|}
$$
We have reached 
$$
\mu(\sigma_0 = -1)^+_{B(n),\beta, 0} \leq \sum_{\gamma :\, 0 \in Int(\gamma)} e^{-2\beta|\gamma|}
$$
we now divide these curves that enclose the origin by thei lenght, and asking how many exists of a fixed length. Clearly the shorter one has length $4$.
$$
\mu(\sigma_0 = -1)^+_{B(n),\beta, 0} \leq \sum_{k\geq4} e^{-2\beta k}\#\{\gamma:\, 0 \in Int(\gamma)\quad |\gamma| = k\}
$$
we can easly bound the number of contour paths of fixed lenght: at the first step i have $4$ choices, the  only $3$ (we cant go back) so the number of paths of length $k$ is $4\cdot 3^{k-1}$. For every curve we can assign a given spin it crosses, since the most a contour of length $k$ can travel is $\lfloor \frac k2 \rfloor$ there are at most $k^2$ curves that contain the origin. In the end
$$
\mu(\sigma_0=-1)^+_{B(n),\beta,0} \leq \frac 43\sum_{k\geq 4} k^2 3^ke^{-2\beta k} =: \delta(\beta)
$$
which converges if $2\log k/k + \log 3 -2\beta  < 1$ and goes to zero when $\beta \to \infty$. This proves that $\beta_c(2) < \infty$.

