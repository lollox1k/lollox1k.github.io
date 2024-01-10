
Danno informazioni sul [[Limit of sets#Liminf limsup]] di insiemi misurabili.
# Lemma di Borel-Cantelli I
Sia $(A_n)_{n\geq 1}$ una successione di insiemi misurabili di uno spazio di misura $(\Omega,\mathcal{F},\mu)$. Se la serie $\sum_n \mu(A_n) < \infty$ è *sommabile* Allora 
$$
\mu(\limsup_n A_n) = 0
$$
**Proof** It follows from the definition of $\limsup$ of sets;
$$
\mu\left(\bigcap_{n\geq 1} \bigcup_{m \geq n} A_m\right)
$$
la successione $B_n := \cup_{m\geq n} A_m$ è non crecente in $n$, quindi per il teorema [[Continuity of mesure]]:
$$
\lim_{n\to\infty} \mu\left(\bigcup_{m\geq n}A_m\right) \leq \lim_{n\to\infty} \sum_{m=n}^\infty \mu(A_m) = 0
$$
per subadditività. Siccome è il resto di una serie convergente ottengo la tesi. $\square$

# Lemma di Borel-Cantelli II
Sia $(A_n)_{n\geq 1}$ una successione di _eventi indipendenti_ di uno spazio di probabilità $(\Omega, \mathcal{F},\mathbb{P})$. Se la serie $\sum_n \mathbb{P}(A_n) = \infty$ _diverge_ allora:
$$
\mathbb{P}(\limsup_n A_n) = 1
$$
> è l'opposto del primo lemma, ma serve la condizione in più dell'indipendenza!

**Proof** Dimostro che l'evento complementare ha probabilità $0$ (anche gli eventi $A_n^C$ sono indipendenti e misurabili):
$$
\mathbb{P}\left(\bigcap_{n\geq 1} \bigcup_{m\geq n} A_m\right)^C = \mathbb{P}\left(\bigcup_{n\geq 1} (\bigcup_{m\geq n} A_m)^C\right) = 
\mathbb{P}\left(\bigcup_{n\geq 1} \bigcap_{m\geq n} A_m^C\right) =
\lim_{n\to\infty}
\mathbb{P}(\bigcap_{m\geq n} A_m^C)
$$
per monotonia della successione non crecente in $n$.  Usando ancora una volta la monotonia e poi l'indipendenza:
$$
\mathbb{P}\left( \lim_{N\to\infty}\bigcap_{m=n}^N A_m^C\right) = \lim_{N\to\infty} \prod_{m=n}^N \mathbb{P}(A_m^C)
$$
siccome la successione è non crescente, lo scambio è lecito per [[Lemma di Fatou#Conseguenze]].
Usando la disuguaglianza $1-x \leq e^{-x}$ per $x \geq 0$:
$$
\lim_{N\to\infty} \prod_{m=n}^N \left(1-\mathbb{P}(A_m) \right) \leq \lim_{N\to\infty} e^{-\sum_m^N \mathbb{P}(A_m)} = 0
$$
per la non sommabilità. $\square$





