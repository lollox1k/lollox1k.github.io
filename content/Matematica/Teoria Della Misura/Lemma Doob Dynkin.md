# Lemma Doob Dynkin
Lo enuncio con solo uno spazio Borel misurabile.

Sia $(\Omega, \sigma(T))$ uno spazio misurabile, dove la sigma algebra è indotta da una funzione $T : \Omega \mapsto \mathbb{R}$. (lavoriamo con la sigma algebra di Borel). Allora per una funzione $X : \Omega \mapsto \mathbb{R}$ vale:
$$
X \quad\sigma(T)\text{-misurabile} \iff \quad X = f \circ T
$$
con $f : \mathbb{R}\mapsto \mathbb{R}$ Borel-misurabile.
### Dim 
1. ($\impliedby$) è banale, infatti composizione di funzioni misurabili è misurabile.

2. ($\implies$) Limitiamoci al caso $X$ funzione indicatrice. Quindi $X = \mathbb{1}_A(\omega)$, con $A \in \sigma(T)$ siccome stiamo supponendo $X$ $\sigma(T)$-misurabile. Ci basta scegliere $f = \mathbb{1}_{IM_T(A)}(x)$, ovvero la funzione caratteristica dell'immagine di $T$ dell'insieme $A$. Naturalmente $IM(A) \in Borel$.
3. Per linearità, si estende al caso di funzione semplice.
4. Per $X$ generica funzione misurabile, basta trovare una successione di funzioni semplici $f_n \uparrow f$:
$$
f_n = g_n \circ T \qquad f = g \circ T
$$
avendo definito $g = \limsup_n g_n$, che rimane ancora misurabile. $\square$

