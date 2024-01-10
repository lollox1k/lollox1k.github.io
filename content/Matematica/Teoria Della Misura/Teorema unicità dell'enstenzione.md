## Teorema unicità dell'enstenzione
Sia $\mathcal{I}$ un $\pi$-sistema su $S$. Sia $\Sigma = \sigma(\mathcal{I})$ la sigma algebra generata dal sistema, e $\mu,\nu$ due misure finite sullo spazio misurabile $(S,\sigma(\mathcal{I}))$ che concordano sul $\pi$-sistema e sulla misura di $S$             ($\mu(S) = \nu(S) < \infty$).  Allora:
$$
\mu = \nu \quad \text{su } \Sigma 
$$
**Dim** 
Sia $\mathcal{D} := \{ F \in \Sigma \,:\, \mu(F) = \nu(F)\}$. Facciamo vedere che è un $d$-sistema su $S$. 
Siccome per ipotesi $\mathcal{I} \subseteq \mathcal{D}$, ed è un $\pi$ sistema, per i lemma di Dynkin:
$$
\sigma(\mathcal{I}) = d(\mathcal{I}) \subseteq \mathcal{D}
$$
- $S \in \mathcal{D}$ per ipotesi. 
- Siano $A,B \in \mathcal{D}$ con $A \subseteq B$. Allora siccome sono misure finite:
$$
\mu(B\setminus A)  =  \mu(B) - \mu(A) = \nu(B)-\nu(A) = \nu(B\setminus A)
$$
quindi $(B\setminus A) \in \mathcal{D}$.
- Consideriamo una successione monotona crescente $F_n \to F$ in $\mathcal{D}$, allora:
$$
\mu(F) = \mu(\cup_n F_n)= \lim_{n\to\infty}\mu(F_n) = \lim_{n\to\infty} \nu(F_n) = \nu(F)
$$
per  [[Limit of sets]] e [[Continuity of mesure]]. $\square$


**Corollario**
Se ho due misure di probabilità che concordano su un $\pi$-sistema, allora concordano su tutta la sigma algebra generata dal sistema.

Il caso più frequente è il $\pi$ sistema che generea la sigma algebra di Borel:
$$
\mathcal{B} = \sigma(\pi(\mathbb{R})) \qquad\pi(\mathbb{R}) := \{(-\infty, x] \vert\, x \in \mathbb{R}\}
$$
Quindi se due misure di probabilità concordadno sugli intervalli della forma $(-\infty, x]$ sono equivalenti su tutta la sigma algebra di $Borel$ (su tutto $\mathbb{R}$ fanno $1$ per definizione, quindi concordano).
