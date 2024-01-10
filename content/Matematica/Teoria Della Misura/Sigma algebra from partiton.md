**Proposition** Let $\mathcal{P} = \{E_1,E_2,\dots\}$ be a countable partition of a set $E$, that is
$$
\bigcup_k E_k = E, \qquad E_i \cap E_j = \emptyset \text{ if } i \neq j
$$
Then $\sigma(\mathcal{P}) = \mathcal{E} := \{ \cup_{i \in I} E_i \,|\, I \subseteq \mathbb{N}\}$, i.e. the [[Sigma algebra]] is simply all the possible unions (even contables) of the base sets.

**Proof**  First we show that $\{ \cup_{i \in I} E_i \,|\, I \subseteq \mathbb{N}\}$ is a $\sigma$-algebra.
By definition is closed under countalbe unions, and contains the empty set (the union of zero sets), and it's closed under complement, since 
$$
A = \bigcup_{i \in I_A} E_i
$$
then 
$$
A^c = \bigcap_{i \in I_A} E_i^c = \bigcap_{i \in I_A} \bigcup_{j \neq i} E_j = \bigcup_{i \notin I_A} E_i
$$
so indeed $\mathcal{E}$ is a $\sigma$-algebra.
Clearly $\mathcal{P} \subset \mathcal{E}$, so $\sigma(\mathcal{P}) \subseteq \sigma(\mathcal{E}) = \mathcal{E}$
But $\mathcal{E} \subseteq \sigma(\mathcal{P})$, since the sigma algebra that contains $\mathcal{P}$ also need to contain every countable union of its elements, so that
$$
\sigma(\mathcal{P}) = \mathcal{E} \qquad\qquad \square
$$


