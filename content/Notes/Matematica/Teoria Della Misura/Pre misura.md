Essenzialmente una misura definita su un [[Semianello]]. Stranamente richiedo la $\sigma$-additività, con la condizione che l'elemento unione numerabile deve appartenere al semianello, dato che un semianello è solo chiuso per intersezione finita, e _quasi_ chiuso per differenza.

#### Def 
Una funzione a valori non negativi definita su un semianello $\mu_p : \mathcal{A} \to [0,\infty]$ con le proprietà:
1. $\mu_p(\emptyset)=0$
2. $\sigma$-additiva, $A = \bigcup_{i=1}^\infty A_i$, $A_i \cap A_j = \emptyset$, $i\neq j$,    $  $A, A_i \in \mathcal{A}$ vale:
$$
\mu_p(A) = \sum_{i=1}^\infty \mu_p(A_i)
$$
Abbiamo dovuto richiedere che l'unione numerabile appartenga al semianello!

La misura banale delle box in $\mathbb{R^d}$ è una pre misura, dalla quale si arriva con il teorema di estensione di Carateodory alla misura di Lebesgue [[Costruzione di una misura, metodo Caratheodory]].
