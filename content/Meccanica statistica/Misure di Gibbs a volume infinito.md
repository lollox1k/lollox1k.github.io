# Cambio di prospettiva
La procedura che abbiamo adottato fino ad ora è stata di definire distribuzioni di probabilità per sistemi definiti in un volume finito $\Lambda$, per poi effettuare il _limite termodinamico_ tendendo ad un sistema infinito. Vorremmo cambiare strategia, e partire direttamente da una distribuzione definita su tutto lo spazio.

A volume infinito (es. $\Lambda = \mathbb{Z}^d$) l'hamiltoniana, quindi la funzione di partizione non sono più definite. Occorre l'uso di tecniche più sofisticate per ottenere l'oggetto che vogliamo.

# Eventi e misure di probabilità
Dato un insieme finito, è facile definire una misura di probabilità, assegnando un valore su ogni elemento dell'insieme delle parti di $\Omega_\Lambda$. L'insieme delle misure di probabilità di un insieme finito viene spesso indicato con $\mathcal{M}_1(\Omega_\Lambda)$.

Assumiamo che $\Omega = \mathbb{Z}^d$. Sia $S \subset \Omega$, la mappa di proiezione canonica $\Pi_S \Omega \mapsto S$ è definita naturalmente come la restrizione su $S$:
$$
\Pi_S(\omega) = \omega_S
$$
Fissiamo un sottoinsieme finito $\Lambda \Subset \Omega$ e consideriamo l'_insieme degli eventi locali che dipendono solo da cosa succede in $\Lambda$_:
$$
\mathcal{C}(\Lambda) := \{\Pi^{-1}\Lambda(A) \,\vert\, A \in \mathcal{P}(\Omega_\Lambda)\}
$$
Ogni evento $C \in \mathcal{C}(\Lambda)$ è detto _cilindro_ con base in $\Lambda$.

Consideriamo ora un insieme $S \subset \Omega$, quindi _anche infinito_. Definiamo la collezzione di tutti i cilindri con base finita contenuta in $S$:
$$
\mathcal{C}(S) := \bigcup_{\Lambda \Subset S} \mathcal{C}(\Lambda)
$$
questo insieme, è ancora a cardinalità numerabile!

Non ci resta che creare la sigma algebra generata da questo insieme:
$$
\mathcal{F}(S) := \sigma(\mathcal{C}(S))
$$
passando alla sigma algebra, ottengo anche _eventi non locali_, merito della chiusura per unione numerabile!.

> Il teorema di estensione di Kolmogorov non è utile qui, perchè servono le distribuzioni marginali.

### Lemma
Una funzione $f : \Omega \mapsto \mathbb{R}$ è $\mathcal{F}(S)$ misurabile se e solo se è locale, ovvero esiste un $\Lambda \Subset \mathbb{Z}^d$ tale che:
$$
f(\omega) = f(\omega') \qquad \text{ quando }\qquad \omega_\Lambda = \omega'_\Lambda 
$$
Una conseguenza è che dipendendo solo da un _numero finito_ di siti, ha anche un _numero finito di valori_, si potrà quindi esprimere come una combinazione lineare finita di funzioni indicatrici dei cilindri.


# Condizioni DLR
Osservazione chiave di Dobrushin, Lanford e Ruelle: 
> Dare condizioni di compatibilità sulle probabilità condizionali invece che sulle marginali

**Intuizione**
Consideriamo gli insiemi: $\Delta \subset \Lambda \Subset \mathbb{Z}^d$ ed una condizione di bordo $\eta \in \Omega$.
Essendo finito, possiamo definire la misura a volume finito $\mu_{\Lambda,\beta,h}^\eta$. Sia $f$ una funzione locale che dipende solo dai valori dei siti in $\Delta$. Quindi il valore atteso $\langle f \rangle_\mu$ può essere calcolato fissando prima gli spin dentro $\Lambda \setminus \Delta$. Quindi di fatto posso vedere come nuove condizioni di bordo sulla misura definita nel volume $\Delta$.
$$
\langle f \rangle_{\Lambda,\beta,h}^\eta  = \sum_{\omega_{\Lambda\setminus \Delta}} \langle f \rangle_{\Delta,\beta,h}^{\omega_{\Lambda\setminus\Delta}} \mu_{\Lambda,\beta,h}^\eta(\omega_{\Lambda\setminus\Delta \text{ fuori } \Delta}) = \langle \langle f \rangle_\Delta^\cdot\rangle_{\Lambda,\beta,h}^\eta 
$$
questo deve valere per ogni funzione locale, per ogni sottoinsieme $\Delta$. Formulato precisamente:

### Lemma
Per tutti $\Delta \subset \Lambda \Subset \mathbb{Z}^d$ e tutte le funzioni limitate e misurabili $f : \Omega \mapsto \mathbb{R}$,
$$
\langle f \rangle_{\Lambda,\beta,h}^\eta = \langle \langle f \rangle_\Delta^\cdot\rangle_{\Lambda,\beta,h}^\eta  \qquad \forall \eta \in \Omega
$$
il simbolo $\cdot$ sta per ricordare che stiamo mediando appunto sulle condizioni di bordo!

### Proof
Indichiamo con $\omega \in \Omega_\Lambda^\eta$ uno stato della forma: $\omega = \omega_\Lambda \eta_{\Lambda^c}$, ovvero fissate le condizioni di bordo. 
$$
\langle \langle f\rangle_\Delta^\cdot\rangle_\Lambda^\eta = \sum_{\omega_\Lambda} \langle f \rangle_\Delta^{\omega_\Lambda \eta_{\Lambda^c}} \frac{e^{-\mathcal{H}_\Lambda(\omega_\Lambda \eta_{\Lambda^c})}}
{Z_\Lambda^\eta}$$
allo stesso modo
$$
\langle f \rangle_\Delta^{\omega_\Lambda \eta_{\Lambda^c}} = \sum_{\omega'_\Delta} f(\omega'_\Delta \omega_{\Lambda\setminus \Delta}\eta_{\Lambda^c}) \frac{e^{-\mathcal{H}_\Lambda(\omega'_\Delta \omega_{\Lambda\setminus \Delta}\eta_{\Lambda^c})}}
{Z_\Delta^{\omega_\Lambda \eta_{\Lambda^c}}}
$$

substituting, with the observation that 
$$
\mathcal{H}_\Lambda(\omega_\Delta \omega_{\Lambda\setminus \Delta}\eta_{\Lambda^c}) -\mathcal{H}_\Delta(\omega_\Delta \omega_{\Lambda\setminus \Delta}\eta_{\Lambda^c}) = \mathcal{H}_\Lambda(\omega'_\Delta \omega_{\Lambda\setminus \Delta}\eta_{\Lambda^c}) -\mathcal{H}_\Delta(\omega'_\Delta \omega_{\Lambda\setminus \Delta}\eta_{\Lambda^c})
$$
since they are the interaction between spins in $\Lambda\setminus\Delta$ with $\eta_\Lambda^c$ they don't care about spins in $\Delta$.

Rearranging the claim follows. $\square$

We can see the previous equation as a consistency relation for measure on the whole lattice:
$$
\langle f \rangle = \langle \langle f\rangle_\Delta^\cdot\rangle
$$

Rephrasing this with the probability measure obtained from the [[Riesz represebtation theorem]], for all local event $A \in \mathcal{F}$ 
$$
\mu(A) = \int \mu_\Delta^\omega(A) \mu(d\omega)
$$

This approach can be generalized (we explicitly used the [[The Ising model]], in particular a property of its hamiltonian), to do this we introduce the notion of **specifications** and **probability kernels**.


**Def**(Probability kernel) Let $\Lambda \Subset \mathbb{Z}^d$. A probability kernel from $\mathcal{F}_{\Lambda^c}$ to $\mathcal{F}$ is a map $\pi_\Lambda : \mathcal{F} \times \Omega \to [0,1]$ with the following properties:
1. For each $\omega \in \Omega$, $\pi_\Lambda(\cdot\mid \omega)$ is a probability measure on $(\Omega, \mathcal{F})$.
2. For each $A \in \mathcal{F}$, $\pi_\Lambda(A,\cdot)$ is $\mathcal{F}_{\Lambda^c}$-measurable.

Moreover, if for all $\omega \in \Omega$ 
$$
\pi_\Lambda(B\mid \omega) = \mathbb{1}_B(\omega), \qquad \forall B \in \mathcal{F}_{\Lambda^c}
$$
then is said to be **proper**.

**Oss** If $\pi_\Lambda$ is a proper probability kernel, then the probability measure $\pi_\Lambda(\cdot\mid\omega)$ is concentrated in the set $\Omega_\Lambda^\omega$:
$$
\pi_\Lambda(\Omega_\Lambda^\omega\mid\omega) = 1
$$
thus we see that $\omega$ plays the role of a boundary condition.

**Oss** We can integrate a bounded measurable function with respect to each measure, and study the dependence on $\omega$:
$$
(\pi_\Lambda f)(\omega) := \int f(\eta) \, \pi_\Lambda(d\eta\mid \omega)
$$
**Remark** Since we are working with $\Lambda \Subset \mathbb{Z}^d$, a _finite set_, a proper probability kernel is uniqueley defined by the values on the set $\Lambda$. Also each integral of the previous type is actually a finite sum. 

**Remark** For a proper proability kernel we can write the probability of any event $A \in \mathcal{F}$ with the sum 
$$
\pi_\Lambda(A\mid\omega) = \sum_{\eta_\Lambda \in \Omega_\Lambda} \pi_\Lambda(\eta_\Lambda\omega_{\Lambda^c}\mid \omega) \mathbb{1}_A(\eta_\Lambda\omega_{\Lambda^c}\mid \omega)
$$
also, the integral becomes
$$
(\pi_\Lambda f)(\omega) = \sum_{\eta_\Lambda \in \Omega_\Lambda} f(\eta_\Lambda \omega_{\Lambda^c}) \pi_\Lambda(\eta_\Lambda\omega_{\Lambda^c}\mid \omega) 
$$

To describe a infinite system we need  a _famility_ probability kernels $\{\pi_\Lambda\}_{\Lambda \Subset \mathbb{Z}^d}$ for all finite subset. The consistency realtions can be written with the composition of probability kernels:
$$
\pi_\Lambda \pi_\Delta(A \mid \eta) := \int \pi_\Delta(A\mid\omega)\pi_\Lambda(d\omega\mid \eta)
$$
**Def** (Specification) A familiy of proper probability kernels $\pi = \{\pi_\Lambda\}$ that satisfies the following consistency condition is called a **specification**:
$$
\pi_\Lambda \pi_\Delta = \pi_\Lambda, \qquad \forall \Delta \subset \Lambda \Subset \mathbb{Z}^d
$$

Similarly with a given measure $\mu$ 
$$
\mu \pi_\Lambda(A) := \int \pi_\Lambda(A\mid\omega)\mu(d\omega)
$$

**Def** (compatible measure) Given a familiy of probability kernels $\pi = \{\pi_\Lambda\}$ we say that a measure $\mu$ is **compatible with $\pi$**  if
$$
\mu = \mu \pi_\Lambda, \qquad \forall \Lambda \Subset \mathbb{Z}^d
$$
the set of measures comatible with $\pi$ is denoted by $\mathcal{G}(\pi)$.

The following questions aries:
1. _Existence_
2. _Uniqueness_
3. _Comparison with the limit approach_


### Gibbs specification

To recover the previous work, we define specifications starting from the Hamiltonian, in a bit more general setting.

**Def** (Potential) If for all $B \Subset \mathbb{Z}^d$ the functions $\Phi_B : \Omega \to \mathbb{R}$ are $\mathcal{F}_B$-measurable, then the collection $\Phi = \{\Phi_B\}_{B \Subset \mathbb{Z}^d}$ is called a **potential**.

**Def** (Hamiltonian) Given a potential $\Phi$, the Hamiltonian in the volume $\Lambda \Subset \mathbb{Z}^d$ is defined as
$$
\mathcal{H}_{\Lambda, \Phi}(\omega) := \sum_{B \Subset \mathbb{Z}^d\quad B\cap\Lambda \neq \emptyset} \Phi_B(\omega)
$$
**Remark** The above sum can contain infinite terms, we need to ensure convergence, for example with condition on the _range_:
$$
r(\Phi) := \inf \{R > 0\,:\, \Phi_B=0\text{ if } diam(B) > R\}
$$
clearly if $r(\Phi) < \infty$ the potential has finite range, and the hamiltonian is well defined. If $r(\Phi) = \infty$ we can impose that $\Phi$ is _absolutely summable_:
$$
\sum_{B \Subset \mathbb{Z}^d \quad B \ni i} \Vert \Phi_B \Vert_\infty < \infty, \qquad \forall i \in \mathbb{Z}^d
$$
which ensures that the interaction of a single spin $i$ with the rest of the system is finite. 


**Def** (Gibbsian specification) Given an absolutely summable potential $\Phi$, the probability kernel familiy defined as
$$
\pi^\Phi_\Lambda(\tau_\Lambda\mid \omega) := \frac{1}{Z^\omega_{\Lambda,\Phi}} e^{-\mathcal{H}^\Phi_\Lambda(\tau_\Lambda \omega_{\Lambda^c})}
$$
is called a gibbsian specification.

**Lemma** It's well defined: it's proper, and it's consistent.
**Proof** Since it's defined by the values in the finite set $\Lambda$ it's proper. The consistency follows from the same considerations used for the Ising hamiltonian.


**Def** (Infinite-volume Gibbs measure) A probability measure $\mu$ compatible with a Gibbsian specification $\pi^\Phi$ is said to be an **Infinite-volume Gibbs measure**.

It's custumary to write $\mathcal{G}(\pi^\Phi)$ as simply $\mathcal{G}(\Phi)$, or by the parameters of the potential like $\mathcal{G}(\beta, h)$ as in the case of the Ising model.

Following the definition of [[The Ising model|phase transition]] for the Ising mode, it's natural to define in this framework

**Def** If $\mathcal{G}(\Phi)$ contains at least two distinct Gibbs measures, $|\mathcal{G}(\Phi)| > 1$, we say that there exists a **first-order phase transition** for the potential $\Phi$.



## Existence
We are interest in the question of existence, which conditions on the potential $\Phi$ we must impose such that there exists a compatibile measure?

The idea is to study del limit of probability measures for a fixed boundary $\omega$ and a sequence of volume $\uparrow \mathbb{Z}^d$
$$
\mu_n(\cdot) := \pi_{B(n)}(\cdot \mid \omega)
$$
with the right topological notions on the set of measure on $(\Omega, \mathcal{F})$ we can prove that our sequents admits a converging subsequence, hence $\mathcal{G}(\Phi)$ is non-empty.

**Def** A sequence of states $\omega^n$ **converges** to a limit state $\omega$ if
$$
\lim_{n\to\infty} \omega^n_i = \omega_i, \qquad \forall i \in \mathbb{Z}^d
$$
we write $\omega^n \to \omega$.

**Oss** Since $\omega_i$ is a finite set, this can be states in a more geometrically appealing way: $\omega^n \to \omega$ iff for all $N\geq 0$ there exists an $n_0$ such that
$$
\omega^n_{B(N)} = \omega_{B(N)}, \qquad \forall n \geq n_0
$$
i.e. they coincide on arbitrary large sets (take the max of all $n_0$ for each of the finite sites inside $B(N)$ ).


**Proposition** With the above notion of convergence, $\Omega$ is _sequentially compact_: every sequence admits a converging subsequence.

**Proof** Standard diagonalization argument. Choose any enumeration of $\mathbb{Z}^d$. Since each spin space is compact, for each spin we can find a converging subsequence:
$$
\omega_1^{n_{1k}} \to \omega_1
$$
we then consider the sequence $\omega_2^{n_{1k}}$ , and again find a subsequence (of the previous subsequence) such that 
$$
\omega_2^{n_{2k}} \to \omega_2
$$
do this till $k$, clearly
$$
\lim_{k\to\infty} \omega^{n_{ik}}_i = \omega_i 
$$
the diagonal subsequence $\omega^{n_{kk}} \to \omega$ converges to this element. $\square$

We can now define a notion of continuiti:

**Def** A function $f : \Omega \to \mathbb{R}$ is **continuos** if given any $\omega^n \to \omega$ 
$$
f(\omega^n) \to f(\omega)
$$

**Oss** Clealry all local function are continuos.


We now define the notion of convergence in the space of measures on $(\Omega, \mathcal{F})$.

**Def** (convergence of measures) A sequence $(\mu_n)_{n\geq 1}$ of measure on $(\Omega, \mathcal{F})$ converges to a measure $\mu$ if
$$
\lim_{n\to\infty} \mu_n(C) = \mu(C), \qquad \forall C \in \mathcal{C}
$$
(for all cylinder sets). We write $\mu_n \Rightarrow \mu$. 

**Proposition** With this convergence to space of measure on $(\Omega, \mathcal{F})$ is sequentially compact.

**Lemma** Let $\mu,\nu$ be measures on $(\Omega, \mathcal{F})$. The following are equivalent:
1. $\mu = \nu$
2. $\mu(C) = \nu(C)$ for all $C \in \mathcal{C}$
3. $\mu(g) = \nu(g)$ for all local functions
4. $\mu(f) = \nu(f)$ for all continuos functions.
**Proof** $1 \implies 2$ Is trivial. $2 \implies 3$ follows simple by writing a local function as a linear combination of cylinder sets, plus an infinite set. $2 \impliedby 3$ since $\mathbb{1}_C$ is a local function. $3 \implies 4$ since $g$ are dense in $f$: let $g_ \to f$, then
$$
|\mu(f) - \mu(g_n)| \leq \Vert f-g_n\Vert_\infty \to 0
$$
so that $\mu(g_n) \to \mu(f)$. Similarly $\nu(g_n) \to \nu(f)$, and
$$
\mu(f) = \lim_{n\to\infty} \mu(g_n) = \lim_{n_\to\infty} \nu(g_n) = \nu(f)
$$
$3 \impliedby 4$ trivial since local functions are continuos. $\square$ 

### Quasilocality

**Def** (Quasilocal specification) A specification $\pi = \{\pi_\Lambda\}$ is **quasilocal** if each kernel $\pi_\Lambda$ is continuos w.r.t. its boundary condition. That is, for all $C \in \mathcal{C}$, $\omega \mapsto \pi_\Lambda(C\mid \omega) \in C(\Omega)$.

This is saying that this probability measure depends weakly on the "far" values of $\omega$. 


**Theorem** (Existence) If $\pi = \{\pi_\Lambda\}$ is quasilocal then $\mathcal{G}(\pi) \neq \emptyset$.
**Proof** Fix any $\omega \in \Omega$ and let 
$$
\mu_n(\cdot) := \pi_{B(n)}(\cdot\mid \omega)
$$

since the kernel are consistent, once $n$ is large enough $\Lambda \subset B(n)$, we can apply the consistency relation:
$$
\mu_n \pi_\Lambda = \pi_{B(n)}\pi_{\Lambda} = \pi_{B(n)} = \mu_n
$$
we know that there exists a subsequence converging to an element $\mu_{n_k} \Rightarrow \mu$. We prove that $\mu \in \mathcal{G}(\pi)$.  Pick a continuos function $f \in C(\Omega)$. 
$$
\mu \pi_\Lambda(f) = \mu(\pi_\Lambda f)
$$
but $\pi_\Lambda f \in C(\Omega)$ since $\pi$ is quasi-local, by [[Weak convergence of probability mesures on metric spaces#Theoream (Portmanteau)|Portmanteau's theorem]] 
$$
= \lim_{k\to\infty} \mu_{n_k}(\pi_\Lambda f) = \lim_{k\to\infty} \mu_{n_k}\pi_\Lambda(f) = \lim_{k\to\infty} \mu_{n_k}(f) = \mu(f)
$$

By the previous lemma $\mu\pi_\Lambda = \mu$, so that $\mu \in \mathcal{G}(\pi)$. $\square$ 

**Remark** The infinite-volume Gibbs measure obtained depends on the choosen $\omega$, which can be interpreted as the boundary condition, thus one shoulds wirte $\mu^\omega$, the Gibbs measure prepared with the boundary condition $\omega$.

**Lemma** Let $\pi$ be a quasilocal specification, then $\mathcal{G}(\pi)$ is closed. 
**Proof** By the previous proof $\mathcal{G}(\pi)$ contains every limit point of any convergenet sequences, i.e. it's sequentially compact. Since the space is Hausdorff it's also closed.


Luckly the Gibbsian specifiactions of an absolutely summable potential are quasilocal.

**Theorem** Let $\Phi$ be an absolutely summable potential, then the Gibbsian specification $\pi^\Phi$ is quasilocal. 
**Proof** Fix $\Lambda \Subset \mathbb{Z}^d$, fix $\omega$ and $\omega'$ such that they coincide on a set $\Delta \supset \Lambda$, pick any $\tau_\Lambda \in \Omega_\Lambda$. We show that when $\Delta$ gets bigger, the difference
$$
|\pi_\Lambda(\tau_\Lambda \mid \omega)-\pi_\Lambda(\tau_\Lambda \mid \omega')|
$$
is small. Trick: using the FTC 
$$
= \left| \int_0^1 \frac{d}{dt} \frac{e^{-h_t}}{z_t} \,dt\right|
$$
where $h_t := t\mathcal{H}_\Lambda(\tau_\Lambda \omega_{\Lambda^c}) + (1-t)\mathcal{H}_\Lambda(\tau_\Lambda \omega'_{\Lambda^c})$ and $z_t := \sum_{\tau_\Lambda} e^{-h_t}$. 

$$
= \left|\frac{d}{dt} \frac{e^{-h_t}}{z_t}\right|  
$$
$$
=\left|\frac{(\mathcal{H}^{\omega'}(\tau_\Lambda)-\mathcal{H}^\omega(\tau_\Lambda))e^{-h_t(\tau_\Lambda)}z_t-e^{-h_t(\tau_\Lambda)}\sum_{\eta_\Lambda} (\mathcal{H}^{\omega'}(\tau_\Lambda)-\mathcal{H}^\omega(\tau_\Lambda))e^{-h_t(\eta_\lambda)}}{z_t^2}\right| 
$$
defining $M := \max_{\tau_\Lambda \in \Omega_\Lambda} |(\mathcal{H}^{\omega'}(\tau_\Lambda)-\mathcal{H}^\omega(\tau_\Lambda)|$ we find
$$
\leq \frac{2Me^{-h_t(\tau_\Lambda)}}{z_t}\leq 2M
$$
this difference is the interaction between the spins in $\Lambda$ and those outiside $\Delta$, so this quantity can be bounded by
$$
M \leq |\Lambda|\sum_{B\Subset \mathbb{Z}^d, \quad B \ni i \in \Lambda,  diam(B) \geq D} \Vert \Phi_B \Vert_\infty
$$
where $i$ is a fixed spin in $\Lambda$, and $D$ is the minimum distance between $\Lambda$ and $\Delta^c$. Since the $\Phi$ is summable, when $D\to\infty$  ($\omega \to \omega'$) 
$$
|\pi_\Lambda(\tau_\Lambda \mid \omega)-\pi_\Lambda(\tau_\Lambda \mid \omega')| \rightarrow 0 \quad \text{ as } D\to\infty
$$
Any cylinder set $C$ can be written as a finite union of states $\tau_\Lambda$, so $\pi_\Lambda$ is continuos, hence it's quasilocal. $\square$ 


>> We have a procedure to construct Infinite-volume Gibbs measures: 
1. Start with an _absolutely summable potential_ $\Phi$
2. Define the Gibbsian specification $\pi^\Phi$
3. Choose a boundary $\omega$ and take the limit $\mu_n = \pi_{B(n)}(\cdot\mid \omega)$, we know that 
$$
\mu_n \Rightarrow \mu \in \mathcal{G}(\Phi)
$$


