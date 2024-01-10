**Teorema** (Erod-Ko-Rado)  Sia $I(n,k)$ definito come:
$$
I(n,k) := \max\left\{ |\mathcal{F}| \, :\, \mathcal{F} \subseteq \binom{[n]}{k}, \text { intersecante}\right\}
$$
Allora 
$$
I(n,k) = 
\begin{cases}
\binom{n}{k} \text{ se } k > \frac{n}{2}, \\
\binom{n-1}{k-1} \text{ se } k \leq \frac{n}{2}.
\end{cases}
$$
E' possibile rappresentare sottoinsiemi uniformi come vertici, e collegari se e solo se la loro intersezione è nulla. Questo grafo viene detto [[Grafo di Kneser]] ed è indicato con $Kne(n,k)$. E' evidente che _una famiglia intersecante forma uno stabile_, quindi la cardinalità di una famiglia estremale è il numero di stabilità $\alpha(Kne(n,k))$.

**Dim 1** Dimostriamo il caso $k > \frac{n}{2}$. 
Facciamo vedere che è una famiglia intersecante, è banale infatti se per assurdo avessero intersezione nulla, la cardinalità dell'unione è uguale alla somma delle cardinalità:
$$
n \geq |A \cup B| = |A| + |B| = 2k > n
$$
### Lemma del sondaggio

Sia $\mathcal{U}$ un insieme detto universo, consideiramo una famiglia $\Sigma \subseteq 2^\mathcal{U}$ di suoi sottoinsiemi, ed un insieme fissato $\mathcal{C} \in 2^{\mathcal{U}}$, di elementi con una certa caratteristica. Vogliamo la seguente proprietà:
$\forall S \in \Sigma$
$$
\frac{|S \cap \mathcal{C}|}{|S|} \leq \lambda \implies \frac{|\mathcal{C}|}{|\mathcal{U}|} \leq \lambda
$$
ovvero _la densità locale_ su ogni $S$ è minore uguale a quella _globale_.
La proprietà cercata è la seguente:

**Def** Una famiglia $\Sigma \subseteq 2^{\mathcal{U}}$ è detta _famiglia di sonaggio_ per $\mathcal{U}$ se $\forall x \in \mathcal{U}$, $x$ sta nello stesso numero di sottoinsiemi di $\Sigma$:
$$
c(x):= |\{S \in \Sigma \,:\, x \in S\}| \implies c(x)=c \;\forall  x
$$
**Proposizione** Sia $\Sigma$ una famiglia di sottoinsiemi di $\mathcal{U}$ famiglia di sondaggio per $\mathcal{U}$, $\lambda \in \mathbb{R}^+$, allora
$$
\frac{|S \cap \mathcal{C}|}{|S|} \leq \lambda \;\forall S\implies \frac{|\mathcal{C}|}{|\mathcal{U}|} \leq \lambda
$$
**Dim** Per ipotesi, siccome ogni elemento $x \in \mathcal{U}$ compare lo stesso numero di volte $c$ negli insiemi di $\Sigma$, deve valere:
$$
c|\mathcal{U}| = \sum_{S \in \Sigma} |S|
$$
ho un overlap esatto di $c$ volte. Se $c > 0$ la famiglia $\Sigma$ è un ricoprimento. Analogamente per l'insieme $\mathcal{C}$ vale:
$$
c|\mathcal{C}| = \sum_{S\in\Sigma} |S \cap \mathcal{C}|
$$
riscrivo la tesi, come somma ed uso l'ipotesi per maggiorare ogni addendo al numeratore:
$$
\frac{|\mathcal{C}|}{|\mathcal{U}|} = \frac{\sum_{S\in\Sigma} |S \cap \mathcal{C}|}{\sum_{S \in \Sigma} |S|} \leq \lambda \frac{\sum_{S\in\Sigma} |S |}{\sum_{S \in \Sigma} |S|} = \lambda \quad \square
$$
**Dim 2** Dimostriamo ora il caso $k \leq \frac{n}{2}$.
Considero la famiglia 
$$
\mathcal{F}_0 := \left\{A \cup \{n\} \,:\, A \in \binom{[n-1]}{k-1}\right\}
$$
questa famiglia è intersecante, infatti tutti i sottoinsiemi contengono l'elemento $n$, dunque $I(n,k) \geq \binom{n-1}{k-1}$. 
Costruiamo una famiglia di sondaggio:
$$
\mathcal{U} = \binom{[n]}{k} \quad \mathcal{C} = \mathcal{F} 
$$
Per costruire la famiglia del sondaggio $\Sigma$, introduciamo le _configurazioni cicliche_ di $[n]$.
Fissato $\pi \in \Pi$, un $A$ è un _intervallo ciclico_ di $\pi$ se i suoi elementi si trovano consecutivamente in $\pi$, ovvero se esiste un $l \in [n]$ tale che:
$$
A=\{l,\pi(l),\pi^2(l),\dots, \pi^{k-1}(l)\}
$$
$$
S(\pi) := \{A \,:\, A \text{ è un intervallo ciclico di $\pi$ di card. } k\}
$$
definiamo l'insieme delle famiglie di intervalli ciclici:
$$
\Sigma := \{S(\pi) \,:\, \pi \in \Pi\}
$$
che è chiaramente una famiglia di sondaggio, siccome ogni $k$-intervallo appare lo stesso numero di volte con le $S(\pi)$, se $x \in \mathcal{U}$, allora $x$ deve apparire nella configurazione ciclica $\pi$, le configurazioni cicliche che contengono $x$ sono $(n-k)!$, indipendentemente da $x$. 

Non ci resta che mostrare che questo vale per ogni densità locale, ovvero $\forall \pi \in \Pi$ 
$$
\frac{|\mathcal{F}\cap S(\pi)|}{|S(\pi)|} \leq \frac{k}{n}
$$
siccome $|S(\pi)| = n$ basta provare che il numeratre è $\leq k$.
Se le intersezioni sono nulle $c=0$ allora è dimostrato.
Supponiamo ora che $|\mathcal{F} \cap S(\pi)| \neq \emptyset$, allora esiste un $A \in S(\pi)$ $A \in \mathcal{F}$. Chiaramente al massimo può intersecarsi con altri $k$ intervalli ciclici.
Usando la proprietà di una famiglia di sondaggio:
$$
\frac{|\mathcal{F}|}{|\mathcal{U}|} \leq\frac{k}{n}
$$
$$
|\mathcal{F}| \leq \frac{k}{n}\binom{n}{k} = \binom{n-1}{k-1}
$$

