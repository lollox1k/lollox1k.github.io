#### Misura esterna 
Aggiungiamo due condizioni ragionevoli ad una [[Proto misura]], la subadditività e la monotonia (è sempre deifnita su tutto l'insieme delle parti). E' una protomisura $\mu^* : 2^E \to [0, +\infty]$ con le seguenti proprietà: 
1. monotonia: 
$$
A \subseteq B \implies \mu^*(A) \leq \mu^*(B)
$$
2. $\sigma$-subadditività:
$$
A = \bigcup_{n\in\mathbb{N}} A_n \implies \mu^*(A) \leq \sum_{n=1}^\infty \mu^*(A_n)
$$
La subadditività da sola non basta a garantire che $\mu^*(\emptyset) = 0$, serve come al solito che almeno un insieme sia a misura finita.
