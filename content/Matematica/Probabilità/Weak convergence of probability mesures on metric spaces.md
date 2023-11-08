# Weak convergence of probability mesures on metric spaces

We discuss the weak convergence of probability mesures on metric spaces $(S,\mathcal{S})$ equipped with the borel $\sigma-$algbra from the metric induced topology.
Since the objective is to prove the exintence of the [[Weiner mesure]], you should keep in mind $S=C[0,1]$ with the supremum norm, or $S = \mathbb{R}^d$. 

## Def (weak convergence)

For $(\mu_n)_{n \geq 1}$ and $\mu$ probability mesures on the mesurable space  $(S,\mathcal{S})$, we say $\mu_n$ converges weakly to $\mu$ , $\mu_n \Rightarrow \mu$ if
$$
\mu_n(f)\to \mu(f) \qquad n\to\infty \qquad \forall f \in C_b(S,\mathbb{R})
$$
>ovvero l'integrale su $S$ rispetto alla successione delle misure converge nei reali all'integrale rispetto alla misura $\mu$, per ogni funzione continua e limitata.

## Def (convergence in distribution)
Let $(X^n)_{n\geq 1}$, and $X$ random variables taking values in $S$, with distribution $X^n \sim \mu_n$ and $X \sim \mu$ respectivley. We say that $X^n$ converges in distribution to $X$, $X^n \Rightarrow X$, if
$$
\mathbb{E}[f(X^n)] \to \mathbb{E}[f(X)] \qquad n\to\infty \qquad \forall f \in C_b(S,\mathbb{R})
$$
> $X^n \Rightarrow X$ se e solo se $\mu_n \Rightarrow \mu$.


### Remark
It would be tempting to conclude that id $\mu_n \Rightarrow \mu$, then $\mu_n(A) \to \mu(A)$ for all $A$ Borel. This is in general false:
$$
\mu_n := \delta_{\frac{1}{n}} \qquad \mu = \delta_0
$$
it is clear that $\mu_n \Rightarrow \mu$. But any set $A$ such that the origin on the boundary like $A = (0,1]$ has always mesure $\mu_n(A)=1 \;\forall n$, but $\mu(A)=0$.

The following theorem characterizes weak convergence.
## Theorem (Portmanteau)
Let $(\mu_n)_{n\geq 1}$, $\mu$ be probability mesures on $(S,\mathcal{S})$. The following are equivalent:
1. $\mu_n \Rightarrow \mu$ as $n\to\infty$,
2. $\mu_n(f) \to \mu(f)$ for all $f:S\mapsto \mathbb{R}$ _bounded uniformly continuos_.
3. $\limsup_n \mu_n(C) \leq \mu(C)$ for all $C \in \mathcal{S}$ _chiusi_.
4. $\liminf_n \mu_n(A) \geq \mu(A)$ for all $A \in \mathcal{S}$ _aperti_.
5. $\lim_n \mu_n(A) = \mu(A)$ for all $A \in \mathcal{S}$ such that $\mu(\partial A)=0$.

**Proof**
$(1 \implies 2)$ obvious since uniform continuity implies continuity. 
$(2 \implies 3)$  We can't use the characteristic function of $C$, since it's discountinuos. We can approximate with a uniform continuos function with a parameter $\epsilon$. Then using **2**:
$$
\mathbb{1}_C \leq f_\epsilon \leq \mathbb{1}_{C_\epsilon}
$$
which shows that as $\epsilon \to 0$ $\mu(f_\epsilon) \to \mu(C)$.
$$
\limsup_n \mu_n(C) \leq \limsup_n \mu_n(f_\epsilon) = \mu(f_\epsilon) \leq \mu(C_\epsilon)
$$
$(3 \iff 4)$ It follows from taking complements.
$(4 \iff 5)$ We start from the mesure of the border:
$$
\mu(\partial A) = \mu(\overline A) - \mu(\mathring{A}) \geq \limsup_n \mu_n(A) - \liminf_n \mu_n(A)
$$
if $\mu(\partial A)=0$, $\liminf$ and $\limsup$ are equal, i.e. the definition of $\lim_n \mu_n(A)=\mu(A)$.

> Perchè c'è la doppia implicazione? quello che mi sembra sia dimostrato è $5\implies 4$!!!!

$(5 \implies 1)$ W.l.o.g assume $f \geq 0$, since $f$ is bounded.
$$
\mu(f)= \int_S f d\mu = \int_S \int_0^M \mathbb{1}(f(x) \geq t)dt d\mu(x) = \int_0^M \mu(\{ f(x)\geq t\})dt
$$
where $M:= \sup_S \vert f \vert$. The same holds for $\mu_n(f)$.  To prove **1**, we need to prove only that $\mu_n(\{f \geq t\}) \to \mu(\{f \geq t\})$ for almost all $t \in [0,\infty)$. 

We use **5**: for the sets $A_t := \{f\geq t\}$ we know that $\mu_n(A_t)\to \mu(A_t)$ provided that $\mu(\partial A_t) = 0$, where $\partial A_t = \{f=t\}$.

We need only to prove that $\mu(\partial A_t) >0$ only for a mesure zero set of $t$:
$$
\{t\geq 0 \,:\, \mu(\partial A_t) > 0\} = \bigcup_{n\geq 1} \left\{t \geq 0\,:\, \mu(\partial A_t) \geq \frac{1}{n}\right\}
$$
it is clear that $A_t \cap A_s = \emptyset$ when $t \neq s$. Then the mesure of the union is simply the sum: since $\mu(S)=1$, each term has at most $n$ elements, proving that the set is denumerable, hence has mesure zero. 
We are almost done:
$$
\vert \mu_n(f)-\mu(f)\vert \leq \int \vert \mu_n(A_t)-\mu(A_t)\vert
 dt \to 0$$
the exchange of limits is legit since we can apply [[Teorema convegenza dominata]] (probability mesures are bounded!). $\square$

**Proposition**
If $(\mu_n)_{n\geq 1}$ are probability mesures on $(\mathbb{R}, \mathcal{B})$, to check weak convergence, we need only to check if:
$$
\mu_n((-\infty, x]) \to \mu((-\infty, x]) \qquad \forall x \in \mathbb{R} \;:\; \mu(\{x\})=0
$$
i.e. to check convergence in a [[Pi-system]]. 

In the language of probability, this means that:
$$
X^n \Rightarrow X \iff F_{X^n}(x)\to F_X(x)
$$
for all $x$ where $F_X$ is continuos.




