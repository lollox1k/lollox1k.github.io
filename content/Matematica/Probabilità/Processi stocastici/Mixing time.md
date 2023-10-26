Suppose the assumptions to guarantee that our [[Discrete time Markov chains|Markov chain]] converges to its [[Convergence to equilibrium for ergodic chains|invariant distribution]]. We now ask 
>
>How fast does it converges?


To formalize this we need a notion of distance, we use the _total variation_:

$$
\Vert \mu-\nu \Vert_{TV} := \sup_{A \subseteq I} |\mu(A)-\nu(A)| = \frac{1}{2}\sum_{x \in I}|\mu(i)-\nu(i)|
$$

For a finite markov chain there exists $c_1,c_2 \in (0, \infty)$ such that
$$
\Vert \lambda P^n - \pi \Vert \leq c_1 e^{-c_2n}
$$
where the constants depend on the second largest eigenvector of the transition matrix (think of the [[Power method]]).

This could depend on the starting distribution, so we define (finite markov chains)
$$
d(t) := \max_{x \in I}\Vert \delta_x P^t - \pi \Vert
$$
the distance at time $t$. With this we define
$$
t_{mix}(\epsilon) := \min\{t \geq 0\,:\, d(t) < \epsilon\}
$$

The following lemma is usefull for establishing bounds on the mix time

**Lemma**  Let $(X_n)_{n\geq 0} \sim Markov(\mu, P)$ and $(Y_n)_{n\geq 0} \sim Markov(\nu, P)$ and let $Z_n = (X_n,Y_n)$ be a coupling of the markov chains. 
Then
$$
d_{TV}(\mu_n, \nu_n) \leq P_Z(X_n \neq Y_n)
$$
**Proof** Given any $A \subseteq I$ we have
$$
\mu_n(A)- \nu_n(A) = P_z(X_n \in A) - P_z(Y_n \in A)
$$
$$
= P_z(X_n \in A, Y_n \notin A) - P_z(Y_n \in A, X_n \notin A)
$$
$$
\leq P_z(X_n \in A, Y_n \notin A)
$$
$$
\leq P_z(X_n \neq Y_n) \qquad \square
$$

We can use this when $Y_n$ has initial distribution $\pi$ (stationary) to bound the mixing time.

**Lemma** (_coupling lemma_) Let $Z_n$ be a coupling, if for any $x \in I$ there exists $T\geq 0$ such that
$$
P_z(X_T \neq Y_T\,|\, X_0 = x, \, Y_0 = \pi) \leq \epsilon
$$
then $t_{mix}(\epsilon) \leq T$.

**Proof** We use the previous lemma and the definition of $t_{mix}$:
$$
t_{mix}(\epsilon) \leq T
$$
since $d(T) = \max_{x \in I} d_{TV}(p_x^n, \pi) \leq \epsilon$. $\square$


Card shuffling, r.w. lazy on hypercube

$$
t_{mix}(\epsilon) \leq n\ln\left(\frac{n}{\epsilon}\right)
$$

