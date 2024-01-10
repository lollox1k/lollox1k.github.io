
In [[Misure di Gibbs a volume infinito]] we have studied the question wheter given a potential $\Phi$ the space of Infinite-volume Gibbs measures is non-empty. 

Following ideas from [[The Ising model]], we defined a notion of first order phase transition based on non-uniqueness of Gibbs measures.

At the start of the proof of existence, which needs that the specification $\pi$ is quasilocal (continuous), we fixed a boundary condition $\omega \in \mathbb{Z}^d$. It tunrs out that uniqueness of Gibbs measure is the same as indipendence from boundary conditions: all the limiting measures are the same.

**Lemma** The following are equivalent:
1. Uniqueness holds: $\mathcal{G}(\pi) = \{\mu\}$
2. For any $\omega$, and all $\Lambda_n \uparrow \mathbb{Z}^d$ and all local function
$$
\pi_{\Lambda_n}(f\mid \omega) \to \mu(f)
$$
**Proof** $(1 \implies 2)$ is trivial, if there exists only one Gibbs measure then regardless of the boundary condition every converging subsequence converges to $\mu$, so that the original sequence also converges to $\mu$. 
$(2 \implies 1)$ Take any $\mu, \nu \in \mathbb{G}(\pi)$ and a local function $f$.
$$
|\mu(f)-\nu(f)| = |\mu\pi_\Lambda(f)-\nu\pi_\Lambda(f)|=\left| \int \pi_\Lambda(f\mid\omega)\mu(d\omega) -  \int \pi_\Lambda(f\mid\eta)\mu(d\eta)\right|
$$
$$
\leq \int |\pi_\Lambda(f\mid\omega)-\pi_\Lambda(f\mid\eta)|\mu(d\omega)\nu(d\eta)
$$
Since local functions are bounded, the integrand is dominanted by $2\Vert f\Vert_\infty$ and we can apply the [[Dominated convergence theorem]] to take out the limit
$$
\leq \lim_{n\to\infty} \int |\pi_{\Lambda_n}(f\mid\omega)-\pi_{\Lambda_n}(f\mid\eta)|\mu(d\omega)\nu(d\eta) = 0
$$
Since $\mu(f)=\nu(f)$ for all bounded function, $\mu=\nu$. $\square$


To state Dobrushin's uniqueness theorem, we need to define some notions.

As usual, a distance between probability measures is the _total variation_. Here we compare spin distribution given two boundary conditions:
$$
\Vert \pi_i(\cdot\mid \omega) - \pi_i(\cdot\mid \omega')\Vert_{TV} := \sum_{\omega_i = \pm 1} |\pi_i(\omega_i\mid\omega) - \pi_i(\omega_i\mid\omega')|
$$

We can introduce the sup of total variation between measures in $i$ that differ only on a single spin $j$ 
$$
C_{ij}(\pi) := \sup_{\omega,\omega'\quad \omega_k=\omega_k'\quad k\neq j}  \Vert \pi_i(\cdot\mid \omega) - \pi_i(\cdot\mid \omega')\Vert 
$$
and a global property
$$
C(\pi) := \sup_{i\in\mathbb{Z}^d} \sum_{j \in\mathbb{Z}^d} C_{ij}(\pi)
$$
**Def** Let $f:\Omega \to \mathbb{R}$. We define the **oscillation** of $f$ at spin $i \in \mathbb{Z}^d$ as:
$$
\delta_i(f) := \sup_{\omega,\eta \quad \omega_k=\eta_k\quad k\neq i} |f(\omega) - f(\eta)|
$$
and the **total oscillation** of $f$ as
$$
\Delta(f) := \sum_{i \in \mathbb{Z}^d} \delta_i(f)
$$

The intuition is that the total oscillation tells us how "far" $f$ is from beeing a constant (which have total oscillation zero).

**Lemma** Let $f$ be continuous and with finite total oscillation. Then $\Delta f \geq \sup f - \inf f$.
**Proof** Let $\omega_s^n$ and $\omega_i^n$ be two sequences that converge to the sup and inf respectively, such that $\omega_s^n = \omega_i^n$ outside a volume $\Lambda^c$. Then a $n$ large enough
$$
\sup f - \inf f \leq f(\omega_s^n) - f(\omega_i^n) + \epsilon
$$
since $\omega_s^n = \omega_i^n$ are different only inside a finite volume $\Lambda$, we can bound the difference using local oscillation:
$$
f(\omega_s^n) - f(\omega_i^n) \leq \sum_{i \in \Lambda} \delta_i(f)
$$
thus
$$
\leq \Delta(f) + \epsilon \qquad \square
$$

**Theorem** (Dobrushin's uniqueness theorem) Let $\pi$ be a specification satisfying the condition:
$$
C(\pi) < 1
$$
called the **Dobrushin's condition of weak dependence**. Then $|\mathcal{G}(\pi)| = 1$

**Proof** Let $\mu,\nu \in \mathcal{G}(\pi)$ and let $f$ be a local function.