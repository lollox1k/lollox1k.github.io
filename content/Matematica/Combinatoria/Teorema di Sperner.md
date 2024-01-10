# Teorema di Sperner

Detto $M(n) := \{\vert \mathcal{F} \vert \;:\; \mathcal{F} \subseteq 2^{[n]} \}$ che ha la proprietà di Sperner, (ovvero nessun insieme è contenuto nell'altro). Allora $M(n) = \binom{n}{\lfloor \frac{n}{2}\rfloor}$.

**Oss** Se $\mathcal{F}$ ha la proprietà di Sperner, è un'anticatena in $(2^{[n]}, \subseteq)$.

### Lemma (LYM inequality)

Se $\mathcal{F}$ è una famiglia di Sperner di $[n]$ allora 
$$
\sum_{E \in \mathcal{F}} \binom{n}{\vert E \vert}^{-1} \leq 1
$$
**Dimostrazione**
Idea della _catena satura_ di lunghezza massima di $(2^{[n]}, \subseteq)$, una successione: $D_0 = \emptyset \subset D_1 \subset D_2 \dots \subset D_n = [n]$. Se voglio massimizzare la lunghezza, è ovvio che aggiungo ad ogni passo solo un elemento $a_i$.
1. Quante sono le catene sature da $\emptyset$ a $[n]$? Ovviamente corrispondono alle permutazioni di $n$ elementi, e sono $n!$
2. Quante sono le catene $\emptyset \subset \dots \subset E \subset \dots \subset [n]$ che passano per il sottoinsieme $E \subseteq [n]$ con $\vert E\vert$ elementi? Ho $\vert E \vert !$ modi per arrivare da $\emptyset$ ad $E$, e dopo $(n-\vert E \vert )!$ per terminare la catena, quindi ho $|E|!(n-|E|)!$ 

Chiamo le catene sature che passano per l'insieme $E$ $\mathcal{D}_E$ che avrà cardinalità come detto sopra.
3. $\mathcal{F}$ è una famiglia di sperner. Se $E,E' \in \mathcal{F}$, $E'\neq E$, allora $\mathcal{D}_E \cap \mathcal{D}_F = \emptyset$.
Infatti se esistesse una catena che compare in entrambe le famiglie, supponiamo s.p.g che $E$ compaia prima di $F$ nella catena: $\emptyset \subset \dots \subset E \dots \subset F \dots \subset [n]$. Ma allora $E \subset F$ contro l'ipotesi di famiglia di sperner.
Essendo disgiunte è facile calcolare la cardinalità dell'unione, che deve essere più piccola della cardinalità di tutte le catene:
$$
\left\vert \bigcup_{E\in \mathcal{F}} \mathcal{D}_E \right\vert = \sum_{E \in \mathcal{F}} \vert \mathcal{D}_E \vert = \sum_{E \in \mathcal{F}} |E|!(n-|E|)! \leq n!
$$
dividendo per $n!$ ottengo la tesi. $\square$

**Dimostrazione** (Sperner)

1. $M(n) \geq \binom{n}{\lfloor \frac{n}{2}\rfloor}$

Sia $\mathcal{F}_k = \binom{[n]}{k}$ la famiglia uniforme.  Soddisfa la proprietà di Sperner, infatti avendo tutti la stessa cardinalità, per valere $A \subseteq B$ si deve avere $A=B$. Ovviamente vale:
$$
\vert \mathcal{F}_k \vert = \binom{n}{k}
$$
Basta prendere $\mathcal{F}_{\lfloor \frac{n}{2}\rfloor}$ per concludere che $M(n)$ deve essere maggiore o uguale.
2. Sia $\mathcal{F}$ qualunque con la proprietà di Sperner, facciamo vedere che $\vert \mathcal{F} \vert \leq \binom{n}{\lfloor \frac{n}{2}\rfloor}$.
**Osservazione** La successione dei coffefficienti binomiali è bimodale (la binomiale):
$$
\binom{n}{\lfloor \frac{n}{2}\rfloor} = \binom{n}{\lceil \frac{n}{2}\rceil}
$$
e qui assume il valore massimo. Ho finito, uso il lemma LYM:
$$
1 \geq \sum_{E \in \mathcal{F}} \binom{n}{|E|}^{-1} \geq \sum_{E \in \mathcal{F}} \binom{n}{\lfloor \frac{n}{2}\rfloor }^{-1} = \binom{n}{\lfloor \frac{n}{2}\rfloor }^{-1} \vert \mathcal{F} \vert
$$
$\square$
