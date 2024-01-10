# Teorema della convergenza dominata
Sia $f_n,f$ funzioni misurabili tali che $f_n \to f$ puntualmente in un insieme $S$, e la successione sia dominata da una funzione integrabile (finito) $g$ non negativa:
$$
\vert f_n(s) \vert \leq g(s) \qquad \forall s \in S, \forall n \in \mathbb{N}
$$
allora $f_n \to f$ in $\mathcal{L}^1$, ovvero $\mu(\vert f_n -f \vert) \to 0$, quindi $I(f_n) \to I(f)$.

### Dim 
Segue dal [[Lemma di Fatou#Lemma di Fatou per integrali| lemma di Fatou per integrali inverso]], per applicarlo ho bisogno di una successione di funzioni non negative e limitata superiormente da una funzione integrabile (in $\mathcal{L}^1$).
Applico Fatou alla successione non negativa $\vert f_n -f\vert \leq 2g$:
$$
\lim_n \mu(\vert f_n-f \vert) \leq\limsup_n \mu(\vert f_n-f\vert) \leq \mu(\limsup_n \vert f_n-f\vert) = \mu(0)=0
$$
siccome $f_n \to f$.  Inoltre:
$$
\mu(|f_n-f|) \geq |\mu(f_n-f)| = |\mu(f_n)-\mu(f)|
$$
quindi $\mu(f_n) \to \mu(f)$. $\square$

