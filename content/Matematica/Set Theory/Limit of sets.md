# Limit of sets
## Liminf & limsup
Sia $(A_n)_{n\geq 1}$ una sequenza di sottoinsiemi di un insieme di partenza $X$.

Diciamo che $\lim_{n\to\infty} A_n = A$, ovvero la sequenza converge all'insieme limite $A$ se i seguenti insiemi coincidono (e fanno $A$):
$$
\liminf_n A_n := \bigcup_{n\geq 1} \bigcap_{m \geq n} A_m  \qquad \limsup_n A_n := \bigcap _{n\geq 1} \bigcup_{m\geq n} A_m
$$
**intuizione dietro alle definizioni**:
We sometimes write $\{A_n \text{ infinitely often} \}$ as an alternative for $\limsup A_n$, because $ω \in  \limsup A_n$ if and only if $\omega \in A_n$ for infinitely many $n$. Similarly, we write $\{A_n \text{ eventually }\}$ for $\liminf A_n$. The abbreviations i.o. and ev. are often used.

In maniera equivalente, si può definire tramite limite di funzioni caratteristiche dell'insieme, quindi passare ad $\mathbb{R}$ ed usare la nozione di liminf e limsup qui:
$$
\limsup_n A_n := \{x \in X \,\vert\, \limsup_n \mathbb{1}_{A_n}(x) = 1\}
$$
$$
\liminf_n A_n := \{x \in X \,\vert\, \liminf_n \mathbb{1}_{A_n}(x) = 1\}
$$
To put it another way, the limit infimum consists of elements that "eventually stay forever" (are in _each set_ after  _some_ n), while the limit supremum consists of elements that "never leave forever" (are in _some_ set after _each_ <math>n</math>). Or more formally:
$$
\lim_{n\to\infty}A_n = A \quad \iff
$$
$$
\forall x \in A\, \exists N \,\vert\, \forall n \geq N\, x \in A_n
$$

$$
\forall y \notin \,A \exists N \,\vert\, \forall n \geq N\, y \notin A_n
$$
### Equivalenza delle definizioni
 $\liminf_n \mathbb{1}_{A_n}(x) = 1$ se e solo se la successione $A_n(x)$ vale $0$ un numero _finito_ di volte:
$$
\exists N \,\vert\, \forall m \geq N \quad A_m(x) = 1
$$
In maniera equivalente:
$$
x \in \cup_n \cap_{m\geq n} A_n \iff \exists N \,\vert\, x \in A_m \forall m \geq N 
$$
che è quivalente a dire $x \notin A_n$ per un numero _finito_ di insiemi.

Quindi $x \in \liminf_n A_n$ se e solo se $x \in A_n$ a meno di un numero finito di insiemi.

In maniera analoga, $\limsup_n A_n = 0$ se e solo se la successione $A_n(x)$ vale $1$ un numero finito di volta, che è quivalente a dire:

$$
\exists N \,\vert\, \forall m \geq N \quad A_m(x) = 0
$$
In maniera equivalente:
$$
x \in \cap_n \cup_{m\geq n} A_n \iff \forall n \exists m \geq n \,\vert\, x \in A_m
$$
negando:
$$
x \notin \cap_n \cup_{m\geq n} A_n \iff  \exists N \,\vert\, \forall m \geq N x \notin A_m
$$
che è quivalente alla condizione data con la funzione caratteristica.

# Sequenze monotone
Come per sequenze reali, se le successioni sono _monotone_, il limite esiste.
Sia la sequenza $(A_n)_{n\geq 1}$ non descrescente: $A_n\subseteq A_{n+1}$ per ogni $n$, allora:
$$
\limsup_n A_n = \bigcup_{n\geq 1} \bigcap_{m \geq n} A_m
$$
usando la non decrescenza:
$$
\bigcap_{m\geq n} A_m = A_n
$$
quindi:
$$
\limsup_n A_n = \bigcup_n A_n
$$
Analogamente per il liminf:
$$
\liminf_n A_n = \bigcap _{n\geq 1} \bigcup_{m\geq n} A_m
$$
usando la non descrescenza:
$$
\bigcup_{m\geq n} A_m = \bigcup_{m\geq 1} A_m
$$
si ottiene quindi:
$$
\limsup_n A_n = \bigcup_{n\geq 1} A_n = \liminf_n A_n
$$
_quindi_ il limite esiste. Si ragiona analogamente per sequenze non crescenti. $\square$
