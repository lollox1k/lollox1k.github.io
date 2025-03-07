# Limite di successioni subadditive
Una successione si dice _subadditiva_ se:
$$
a_{n+m} \leq a_n + a_m
$$
Vale il seguente teorema:
### Teorema
$$
\lim_{n\to\infty} \frac{a_n}{n} = \inf_n \frac{a_n}{n}
$$
quindi, _il limite esiste sempre_.

### Proof
Sia $\alpha = \inf_n \frac{a_n}{n}$, prendiamo un valore leggermente superiore: fissato $\epsilon > 0$ esiste un $l$ tale che
$$
 \frac{a_l}{l} \leq \alpha + \epsilon
$$
ogni naturale $n$ può essere scritto nella forma $n = kl + j$ con $k = 0,1,\dots$ e $0 \leq j < l$.
Dalla definzione di $\alpha$ segue:
$$
\alpha n \leq a_n = a_{kl+j} \leq a_{kl} + a_j \leq k a_l + a_j
$$
dividiamo per $n$ e passiamo al limite
$$
\alpha \leq \lim_{n\to\infty} \frac{a_n}{n}\leq \frac{a_l}{l} \leq \alpha + \epsilon
$$
per l'arbitrarietà di $\epsilon$ questo conclude la dimostrazione. $\square$

## Estensione sul reticolo
Si può estendere a successioni di parallelepipedi in $\mathbb{Z}^d$. In questo caso la subadditività è di una funzione $a : \mathcal{R} \mapsto \mathbb{R}$:
$$
a(R_1 \cup R_2) \leq a(R_1) + a(R_2) \quad R_1 \cap R_2 = \emptyset
$$
Un esempio è la successione di parallelepipedi semplice:
$$
B(n) = \{-n,\dots,n\}^d
$$
Vale il seguente teorema:
### Lemma Fekete
Sia $a : \mathcal{R} \mapsto \mathbb{R}$ _subadditiva_ e _invariante per traslazioni_ e una sequenza di parallelepipedi $|\Lambda_n| \to \infty$. Allora:
$$
\lim_{n\to\infty} \frac{a(\Lambda_n))}{|\Lambda_n|} = \inf_{\Lambda \in \mathcal{R}} \frac{a(\Lambda)}{|\Lambda|}
$$
### Proof
Come prima, sia $\alpha := \inf_{\Lambda} \frac{a(\Lambda)}{|\Lambda|}$, sia $\Delta$ un elemento della successione tale che $\frac{a(\Delta)}{|\Delta|} \leq \alpha + \epsilon$. 
Ogni cubo $\Lambda_n$ può essere scomposto in un'unione di  $N_n$ traslati di $\Delta$ ed un resto. Supponendo di scegliere $n$ grande a piacere, 
$$
\lim_{n\to \infty} \frac{|\Lambda_n|}{N_n|\Delta|} = 1
$$
applicando la subadditività e l'invarianza per traslazioni:
$$
a(\Lambda_n) \leq N_n a(\Delta) + (|\Lambda_n|-N_n|\Delta|)a(\{0\}^d)
$$
dove il secondo addendo è il termine di resto.
Quindi:
$$
\alpha \leq \liminf_{n\to\infty} \frac{a(\Lambda_n)}{|\Lambda_n|} \leq \limsup_{n\to\infty} \frac{N_n a(\Delta)}{N_n|\Delta|} \leq \alpha + \epsilon
$$
per l'arbitrarietà di $\epsilon$ questo conclude la dimostrazione. $\square$
