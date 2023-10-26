# Grafo complementare

## Def 
Sia $G$ un grafo semplice, il grafo $\overline G$, detto *complementare di $G$* è un grafo con lo stesso insiemi di vertici $V(\overline G)=V(G)$ e con insieme di archi:
$$
xy \in E(\overline G) \iff xy \notin E(G)
$$

## Proprietà
### Taglia
Segue dalla definizione che gli insieme degli archi di $G$ e $\overline G$ sono disgiunti, in effetti sono una bipartizione di tutti gli archi possibili, infatti $G \cup \overline G = K_n$ dove $n = |V(G)|$. 
Da qui segue la relazione sulla taglia di un grafo complementare:
$$
|E(G)|+|E(\overline G)| = |E(K_n)| = \binom{n}{2}
$$
### Connessione
**Domanda** Se $G$ è un grafo connesso, il suo complementare $\overline G$ è disconnesso? No
Controesempio: $P_4$.

Vale invece il verso opposto.

**Proposizione** Se $G$ è disconnesso, il suo complementare $\overline G^c$ è connesso.
**Dim**
Dimostriamolo costruendo un cammino tra due vertici arbitrari $x,y \in V(\overline G^c)$.
Se $x,y$ appartenevano a diverse componenti connessi di $G$ (ne ha almeno due essendo sconnesso, in particolare ha almeno due vertici distinti), ho fatto, infatti $xy \in E(\overline G^c)$. Supponiamo ora che $x,y$ appartengano alla stessa componente connessa, i casi sono due:
1. $xy \notin E(G)$, e allora ho finito perchè $xy \in E(\overline G)$;
2. $xy \in E(G)$, in questo caso non ho un arco che li collega direttamente nel complementare, dobbiamo costruire un cammino più lungo:
Prendiamo un vertice $z$ appartenente ad un'altra componente connessa del grafo di partenza $G$, deve esistere perchè per ipotesi il grafo è sconnesso ma $xy \in E(G)$. Ma allora sia $x$ che $y$ sono collegati a $z$, quindi esiste il cammino $xzy$, dunque $x\sim y$. $\square$



