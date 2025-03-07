#### Misura 
Aggiungiamo ad una [[Misura esterna]] la cosa fondamentale, ovvero la richiesta intuitiva che la misura deve essere uguale alla misura delle parti (anche numebrabili), la sigma additività. Purtroppo ciò causa oggetti patologici nell'insieme delle parti di $\mathbb{R}$ [[Insieme di Vitali]], ci limitamo a definirla su una sigma algebra [[Sigma algebra]].

**Def** (measure) Una funzione $m : S \to [0, +\infty]$ dove $S \subseteq 2^E$ è una $\sigma$-algebra. 
1. $m(\emptyset) = 0$
2. $\sigma$-additività:
$$
A = \bigcup_{n\in\mathbb{N}} A_n \quad A_n \bigcap A_m = \emptyset \quad \forall n\neq m \implies m(A) = \sum_{n=0}^\infty m(A_n) 
$$
