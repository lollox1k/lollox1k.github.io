

Let $f \in L_{loc}^1(\mathbb{R}^n)$, then for every $\varphi \in C_c^{\infty}(\mathbb{R}^n)$ it's well defined the action of $f$ on $\varphi$ by
$$
\langle f,  \varphi \rangle = T_f(\varphi) := \int_{\mathbb{R}^n} f\varphi \,dx
$$

Call $K = \text{supp } \varphi$ since using [[Holder's inequality]] 
$$
\Vert f \varphi \Vert_{L^1(\mathbb{R}^n)} = \Vert f \varphi \Vert_{L^1(K)} \leq \Vert f \Vert_{L^1(K)} \Vert \varphi \Vert_{L^\infty(K)}
$$


Let $\alpha = (\alpha_1,\dots,\alpha_n)$ with $\alpha_i \in \mathbb{N}$, $\alpha$ is known as a **multi-index** of order $|\alpha| := \sum_i \alpha_i$. 

Let $\varphi \in C^{\infty}(\Omega)$ with $\Omega \subseteq \mathbb{R}^n$ an open subset, we define 
$$
D^\alpha \varphi := \frac {\partial^{\alpha_1}}{\partial x_1^{\alpha_1}}\cdots \frac {\partial^{\alpha_n}}{\partial x_1^{\alpha_n}}\varphi
$$
# The space of test functions
> [!definition]
> The space of **test function** $\mathcal{D}(\Omega)$ it's the space $C_c^\infty(\Omega)$ together with the following convergence criterion: $\{\varphi_n\} \subset C_c^\infty(\Omega)$ converges to $\varphi \in C_c^\infty(\Omega)$ if:
> 1. there exists a compact set $K \subset \mathbb{R}^n$ such that $\text{supp }\varphi_n \subset K$ for all $n$;
> 2. for every multi-index $\alpha$ we have $D^\alpha \varphi_n \rightrightarrows D^\alpha\varphi$ on $\Omega$ (on $K$).
> 
> We use the notation $\varphi_n \xrightarrow{D} \varphi$.


Note that $\text{supp }\varphi \subseteq K$ is implied my uniform convergence.
The motivation for condition $1.$ is clear, we don't want limits with support wandering to infinity. The second rather strong conditions is usefull to make the continuous the linear functionals of the type:
$$
F[x] := \int_{\mathbb{R}^n} x(t) \varphi(t) dt
$$
since with uniform convergence we can carlessly exchange the limit with the integral.

This notion of convergence can be obtained as a LC-topology from a family of seminorms ($\mathcal{D}(\Omega)$ is a [[Topological vector space]]).

# Distributions
> [!definition]
> A linear map $T : \mathcal{D}(\mathbb{R}^n) \to \mathbb{R}$ (or $\mathbb{C}$) is called **distribution** if:
> 1. $T$ is _linear_: $T(\lambda \varphi + \psi) = \lambda T(\varphi) + T(\psi)$
> 2. $T$ is _continuous_: if $\varphi_n \xrightarrow{D} \varphi$ then $T(\varphi_n) \to T(\varphi)$
>
>Since this space is the topological dual we use the notation $\mathcal{D}'(\mathbb{R}^n)$.


>[!example]
> 1. Every $f \in L^1_{loc}(\mathbb{R}^n)$ induces a distribution 
> $$
> T_f(\varphi) := \int_{\mathbb{R}^n} f(t)\varphi(t)dt
> $$
> Distribution which can be represented by a local function are called **regular**.
> 1. The most famous not regular distribution is the **Dirac's delta**:
> $$
> \delta_x(\varphi) := \varphi(x)
> $$
> it's easy to see why is not regular. Suppose that there exists a function $f \in L^1_{loc}$ that represents the delta, then given any test function $\varphi$. By [[Lebesgue's integral|the absolute continuity]] of the Lebesgue integral we can find $E \subseteq \mathbb{R}^n$ such that
> $$ 
> \varphi(x)=\delta_x[\varphi] = \int_E f(t) \varphi(t)dt < \epsilon
> $$
> A clear contradiction if $\varphi(x) \neq 0$.


Every Radon measure induces a distribution in a natural way:
$$
T_\mu (\varphi) := \int \varphi \,d\mu
$$
in fact:
- it's well defined since $\forall \varphi \in C_c^\infty(\Omega)$ 
$$
\int_\Omega \varphi d\mu \leq \Vert \varphi \Vert_\infty \mu(\text{supp}(\varphi)) < \infty
$$
- it's linear and continuous by the properties of the [[Lebesgue's integral]]

> [!proposition]
> Let $\mu$ be a Radon measure, then $T_\mu$ is representable by an $L^1_{loc}$ function iff $\mu$ is absolutely continuous w.r.t. the Lebesgue measure.
> > [!proof]-
> > Let $\mu$ be a Radon measure, following [[Radon-Nikodym theorem|Lebesgue decomposition theorem]] we can decompose it as $\mu = \mu_{as} + \mu_s$. A measure defines a distribution via integration:
> > $$
> > T_\mu(\varphi) = \int \varphi \,d\mu = \int \varphi \,d \mu_{as} + \int \varphi \,d \mu_{s}
> > $$ 
> > Using the [[Radon-Nikodym theorem]] we can write the integral with the absolutely continuous measure as
> > $$
> > \int g \varphi\,d\lambda
> > $$
> > w.r.t. the Lebesgue measure. Since $\mu$ is Radon, it gives finite measure to every compact set, so $g \in L^1_{loc}$. 
> > Clearly equality holds iff $\mu_s \equiv 0$, i.e. $\mu$ is absolutely continuous w.r.t. the Lebesgue measure. $\square$

The following proposition is usefull to check if a given linear functional is a distribution.

> [!proposition]
> Let $T : \mathcal{D}(\mathbb{R}^n) \to \mathbb{R}$ (or $\mathbb{C}$) be linear. The following are equivalent:
> 1. $T$ is a distribution
> 2. $\forall K \subset \mathbb{R}^n$ compat $\exists m \in \mathbb{N}$ $\exists C > 0\, \forall \varphi \in \mathcal{D}(\mathbb{R}^n)$ $\text{supp }\varphi \subseteq K$  s.t.
> $$
> |T(\varphi)| \leq C \sum_{|\alpha| \leq m} \Vert D^\alpha \varphi\Vert_\infty
> $$
> 
> > [!proof]-
> > We only need to check that $T$ is continous.
> > $(\impliedby)$ Let $\varphi_n, \varphi \in \mathcal{D}(\mathbb{R}^n)$ with $\varphi_n \xrightarrow{D}\varphi$. Then by the definition of convergence there exists $K$ compact such that $\text{supp }\varphi_n \subseteq K$ and for all $\alpha \in \mathbb{N}$ we have $\Vert D^\alpha \varphi_n - D^\alpha \varphi\Vert_\infty \to 0$.
> > To prove that $T$ is continuous we need to check that
> > $$
> > |T(\varphi_n) - T(\varphi)| = |T(\varphi_n - \varphi)|
> > $$
> > goes to zero. We can use the bound $2.$
> > $$
> > \leq C \sum_{|\alpha| \leq m} \Vert D^\alpha \varphi_n - D^\alpha \varphi \Vert_\infty \xrightarrow{n\to\infty} 0
> > $$
> > since on the right we have a finite sum.
> >  $(\implies)$ We prove the contrapositive statement: if $2.$ doesn not hold, then $T$ is not continuous (hence not a distribution).
> >  $\exists K$ compact $\forall m \in \mathbb{N}$ and $\forall C >0$ s.t. $\forall \varphi \in \mathcal{D}$ with $\text{supp }\varphi \subseteq K$
> >  $$
> >  |T(\varphi)| > C \sum_{|\alpha| \leq m} \Vert D^\alpha \varphi \Vert_\infty
> > $$
> > Choose $C = m = k \in \mathbb{N}$, we can construct a sequence $\varphi_k \in \mathcal{D}$ with
> > $$
> > |T(\varphi_k)| > k \sum_{|\alpha| \leq k} \Vert D^\alpha \varphi_k \Vert_\infty
> > $$
> > The rescaled sequence $\psi_k := \frac{\varphi_k}{|T(\varphi_k)|}$ is well defined, also
> > $$
> > \psi_k \xrightarrow{D} 0
> > $$
> > since 
> > $$
> > |T(\varphi_k)| > k\Vert \varphi_k \Vert_\infty > k |\varphi_k(x)| \quad \implies \quad \frac {|\varphi_k(x)|}{|T(\varphi_k)|} < \frac 1k
> > $$
> > this works for any multi-index $\alpha$.
> > But if we compute 
> > $$
> > |T(\psi_k)| = \frac 1 {|\varphi_k|} |T(\varphi_k)| = 1 \neq 0
> > $$
> > hence $T$ is not continous. $\square$

Given a distribution, the $m$ above is called its **order**. 
For example any regular distribution has order $m=0$, since:
$$
|T_f(\varphi)| \leq \int|f(t)\varphi(t)|dt \leq C \Vert \varphi \Vert_\infty
$$
where $C$ is just the integral (which is finite since $f \in L^1_{loc}$).
In general any Radon measure induces a distribution of order zero:
$$
|T_\mu(\varphi)| \leq \mu(\text{supp }\varphi)\Vert \varphi \Vert_\infty
$$
The converse is also true by the [[Riesz representation theorem]]:
Let $T$ be an order zero distributuion, then there exists $4$ unique Radon measures such that
$$
T(\varphi) = \int \varphi \,d\mu_1 -\int \varphi \,d\mu_2 +i\int \varphi \,d\mu_2 -i\int \varphi \,d\mu_4
$$
In general for a distribution of order $m$ there exists a set of Radon measures for any multi-index of oder $\leq m$$: $\mu_\alpha$, $\alpha \in \mathbb{N}^n$, $|\alpha| \leq m$ such that
$$
T(\varphi) = \sum_{|\alpha| \leq m} \int D^\alpha \varphi \,d\mu_\alpha
$$
> [!tip] 
> We can think of a distribution of order $m$ to depend only on derivatives of order less or equal to $m$

# Distributional derivatives
Since $C^1(\mathbb{R}^n) \subset L^1_{loc}(\mathbb{R}^n)$ it makes sense to define $T_f$ for any differentiable function $f$. In $n=1$ we would like:
$$
T'_f = T_{f'}
$$
so our notion of derivatives of distribution needs to be compatible with the equality above. If we apply $T_{f'}$ on a test function and use integration by parts
$$
T_{f'}(\varphi) = \int f'(t) \varphi(t) dt = -\int f(t) \varphi'(t)dt = -T_f(\varphi')
$$
(boundary terms are zero) the formula on the right makes sense for any distribution $T$, and ca be generalized for all partial derivatives (note that it also holds more generally for [[Absolutely continuous functions]]).

> [!definition]
> Let $T \in \mathcal{D}'(\mathbb{R}^n)$. The (distributional) **partial derivative** of $T$ w.r.t. $x_i$ is the distribution $\partial_{x_i} \varphi \in \mathcal{D}'(\mathbb{R}^n)$ defined as:
> $$
> \langle \partial_{x_i}T, \varphi \rangle = - \langle T, \partial_{x_i}\varphi \rangle, \qquad \forall \varphi \in \mathcal{D}(\mathbb{R}^n)
> $$

Using induction see that for any multi-index $\alpha$ 
$$
\langle D^\alpha T, \varphi \rangle = (-1)^{|\alpha|}\langle T, D^\alpha\varphi \rangle, \qquad \forall \varphi \in \mathcal{D}(\mathbb{R}^n)
$$

> [!example]
> In general for differentiable a.e. functions the distributional derivatives doesn't match the a.e. derivative.
> Consider the Haveside function $H(x) = \mathbb{1}_{[0,+\infty)}(x)$ (a [[Jump functions|jump function]]) which has derivative $0$ a.e, but it's distributional derivative is:
> $$
> T'_H(\varphi) = -T_H(\varphi') = -\int_{[0,+\infty)} \varphi'(t) dt = \varphi(0) = \delta_0(\varphi)
> $$

# Definizione
Per definire la [[Weak deriative|derivata debole]], abbiamo integrato una funzione localmente integrabile $f \in L^1_{loc}(\mathbb{R}^n)$ con una funzione test $\psi \in C^{\infty}_{c}(\Omega)$. Possiamo interpetare questa procedura come una funzionale definito dalla $f$ che manda $C^{\infty}_{cpt} \to \mathbb{R}$
$$
\psi \mapsto \int_\Omega f \psi d^nx
$$
Una _distribuzione_ su $\Omega \subset \mathbb{R}^n$ è un funzionale generale, non necessariamente rappresentabile in forma integrale, es. _[[Dirac's delta]]_ $\delta_x$ :
$$
\delta_x[\psi] = \psi(x)
$$
ovviamente non vogliamo tutti i funzionali, ma quelli _lineari_, per avere uno spazio vettoriale e _continui_.
Lo spazio delle distribuzioni è quindi il _duale delle funzioni test_, con somma e prodotto per scalare definiti nella maniera ovvia, Swartz indicava $C^{\infty}_{cpt}$ con il simbolo $\mathcal{D}$ , quindi il suo duale:
$$
\mathcal{D}'(\Omega)
$$
Siccome ogni funzione localmente integrabile definisce la relativa distribuzione mediante l'integrale, è evidente che vale l'inclusione:
$$
L^1_{loc}(\Omega) \subset \mathcal{D}'(\Omega)
$$
dove abbiamo commesso un abuso di notazione (le funzioni ed i rispettivi funzionali integrali). In generale _ad ogni funzione in $L^p$ si può associare una distribuzione_ (integrale).

### Convergenza e continutà
Prima dobbiamo definire la convergenza nello spazio di partenza, le funzioni test. Siano $\psi \in C^{\infty}_{cpt}(\Omega)$ , $\{\psi_k\}_{k \in \mathbb{N} }\subset C^{\infty}_{cpt}(\Omega)$, diciamo che la successione converge  
$$
\psi_k \to \psi 
$$
se e solo se il supporto di tutte le $\psi_k$ è contenuto in un insieme compatto $K\subset \Omega$ e le funzioni e tutte le derivate parziali convergono uniformemente in $K$.

Definiamo quindi la continuità come al solito. La distribuzione $u$ è continua se data una successione tale che $\psi_k \to \psi$, vale:
$$
\lim_{k\to\infty}(u,\psi_k) = (u,\psi)
$$
abbiamo introdotto la notazione comune $(u,\psi) := u[\psi]$.

### Derivate distribuzionali
Definiamo in maniera praticamente uguale alle [[Weak deriative|derivate deboli]]l e derivate di una distribuzione:
$$
(D^\alpha u,\psi) := (-1)^{|\alpha|}(u,D^\alpha \psi)
$$
ben definito perchè è una mappa lineare e continua.

##### Osservazioni
Le derivate deboli non sempre esistono, mentre quelle distribuzionali esistono sempre, $\psi$ sono $C^\infty$!!!.
Data la somiglianza spesso i termini derivata debole e distribuzionale vengono usati come sinonimi, ma sono cose diverse! (spazi diversi), infatti la derivata debole (quando esiste) è rappresentata da una funzione localmente integrabile, cosa non sempre vera per le distibuzioni.



