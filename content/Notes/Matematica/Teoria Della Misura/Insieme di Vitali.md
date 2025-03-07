# Insieme di Vitali
insieme non lebegue misurabile. Vediamo la costruzione.
#### Claim 
_Sia $\mu$ una misura su $P(\mathbb{R})$ tale che che:
- $\mu((0,1])) < +\infty$
- invariante per traslazioni: $\mu(F+t) = \mu(F) \forall t \in \mathbb{R}, \forall F \in P(\mathbb{R}$
Allora è la funzione identicamente  nulla $\mu = 0$.

In altre parole non esiste una misura bella ed utile su tutto l'insieme delle parti della retta reale.

#### Dim
Sia $I := (0,1]$ con la relazione di equivalenza:
$$
x \sim y \iff x-y \in \mathbb{Q}
$$
che definisce gli insieme quozienti:
$$
[x] := \{x+r \quad | \quad r \in \mathbb{Q}, \quad x+r \in I\}
$$

Costruiamo un insieme $A \subseteq I$ con le proprietà:
- per ogni classe di equivalenza $[x]$ esiste un elemento $a \in A$  con $a \in [x]$
- per ogni $a,b \in A$ t.c. $a,b \in [x]$ $\implies a = b$
Ovvero scegliamo un solo rappresentante per ogni classe. Ciò è possibile grazie all'assioma della scelta [[Axioms of set theory]].

Definiamo ora una famiglia numebrabile di insieme $A_n$:
$$
A_n := r_n + A
$$
dove $r_n$ è una enumerazione dei razionali nell'intervallo $(-1,1]$.

Gli insiemi di questa famiglia sono disgiunti:
$$
A_n \cap A_m = \emptyset \qquad n \neq m
$$
#### Dim
si procede per assurdo. Sia $x \in A_n \cap A_m$, dalla definizione degli insieme:
$$
x = r_n + a_n, \qquad a_n \in A
$$
$$
x = r_m + a_m, \qquad a_m \in A
$$
quindi
$$
r_n + a_n = r_m + a_m
$$
$$
a_n - a_m = r_m - r_n \in \mathbb{Q}
$$
ma allora
$$
a_n \sim a_m \implies a_n, a_m \in [a_m]
$$
e per la definizione di $A$ $a_n = a_m$. Segue che 
$$
r_n - r_m = 0 \qquad r_n = r_m
$$
in conclusione $n = m$ (l'enumerazione è ovviamente biunivoca).

Consideriamo ora l'unione numerabile $\cup A_n$. Si vede facilmente che valgono le inclusioni:
$$
(0,1] \subseteq \bigcup_{n\in\mathbb{N}}A_n \subseteq (-1,2]
$$
Ora usiamo le proprietà della nostra misura. Segue dalla monotonia e dalla sigma additività:
$$
\mu((0,1]) \leq \mu(\bigcup_{n\in\mathbb{N}}A_n) \leq \mu((-1,2])
$$
E' facile vedere l'assurdo. Sia $\mu((0,1]) = C \in \mathbb{R}$. Siccome possiamo costruire l'intervallo $(-1,2]$ traslando ed unendo 3 copie disgiunte dell'intervallo $(0,1]$ concludiamo che $\mu((-1,2]) = 3C$.
$$
C \leq \sum_{n=1}^\infty \mu(A_n) \leq 3C \qquad 
$$
Segue dall'invarianza per traslazioni della misura che ogni insieme $A_n$ ha la stessa misura. 
E' facile vedere come l'unico valore che soddisfa le disuguaglianze sia la misura sempre nulla in modo che $C=\mu(A_n)=0$. Qualunque altro valore farebbe divergere la serie, che deve però essere finita e minore di 3C. 
