# $\lambda$-sistema
Chiamato anche $d$-sistema (da differenza). Una famiglia di insiemi $\mathcal{D} \subseteq 2^S$ è un $d$-sistema sull'insieme $S$ se e valgono le seguenti proprietà:
- $S \in \mathcal{D}$
- Se $A,B \in \mathcal{D}$ e $A \subseteq B$ allora $B\setminus A \in \mathcal{D}$
- Se $(A_n)_{n\geq 1} \subseteq \mathcal{D}$ e $A_n \uparrow A$ allora $A \in \mathcal{D}$ 
> un $\lambda$ sistema è quasi una sigma algebra, gli manca la chiusura per unione però! grazie alla chiusura per intersezione del $\pi$ sistema il gap si colma.

**Osservazione 1**
Una $\sigma$-algebra è sia un $\pi$ che $\lambda$ sistema. Ma vale anche il contrario:
$$
\pi, \lambda \iff \sigma 
$$
Supponiamo che $\Sigma$ sia un $\pi$ e $\lambda$ sistema:
- Siccome è un $\lambda$ sistema contiene tutto l'insieme $S$.
- Il $\lambda$ sistema grazie alla chiusura per differenza, e che contiene $S$ garantisce la chiusura per complementare, infatti:
$$
A^c = S \setminus A
$$
- proviamo prima la chiusura per unione finita, siano $E,F \in \Sigma$, allora:
$$
E \bigcup F = S \setminus (E^c \cap F^c ) \in \Sigma
$$
(segue dalle leggi di de Morgan). Qui è cruciale che sia anche un $\pi$ sistema. (si usa solo qui).
La chiusura per unione numerabile segue subito, infatti la successione unione  è monotona:
$$
G_n := E_1 \cup E_2 \cup \dots \cup E_n \uparrow G 
$$
siccome quindi $\bigcup E_n = G \in \Sigma$ per la chiusura per successioni monotone crescenti del $\lambda$ sistema. $\square$

**Osservazione 2**
Ovviamente $d(A) \subseteq \sigma(A)$, perchè ogni sigma algebra è un $\lambda$ sistema, quindi si ha meno scelta, ed il più piccolo è maggiore. _Il min è su un insieme più piccolo_.