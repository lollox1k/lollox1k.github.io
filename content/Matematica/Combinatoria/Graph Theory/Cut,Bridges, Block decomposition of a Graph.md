# Cuts

Vogliamo dire di più su quanto è [[Distanza e connessione|connesso]] un grafo. Intuitivamente, un grafo "molto connesso" ha più cammini possibili dati due vertici, un grafo conesso minimale ne ha solo uno (vedi [[alberi]]). 

Per analizzare la questione introduciamo alcune definizione.

**Def** (Cut) Un vertice $v$ di un grafo $G$ viene detto _punto di taglio_ se il grafo $G' = G\setminus v$ indotto ha più componenti connesse: $\lambda(G') > \lambda(G)$. 

Quindi rimuovendo un vertice di taglio, il grafo diventa più sconnesso. 
Vediamo una caratterizzazione dei punti di taglio.

**Teorema** Un vertice $v \in V(G)$ è un cut-vertex di $G$ se e solo se $\exists u,w \in V(G)$  diversi da $v$ tali che $v$ compare in ogni cammino $u-w$.

**Dim** Assuiamo che $G$ sia connesso, il caso generale si otteiene considerando ogni componente connessa. 
$(\implies)$ Sia $v \in V(G)$ un cut-vertex, allora per definizione $G \setminus v$ è disconnesso. Siano $u,w$ vertici in componenti connesse diverse di $G\setminus v$, quindi $\nexists$ cammini $u-w$ nel grafo ridotto, ma siccome $G$ era connesso, e questo cammino non esiste più, tutti i cammini passavano per $v$.
$(\impliedby)$ Supponiamo esistano due vertici $u,w$ tali che ogni cammino $u-w$ passa per un vertice $v$. Ma allora rimuovendolo, non esiste un cammino tra $u$ e $w$, quindi il grafo e disconnesso. $\square$ 

>Quanti punti di taglio può avere al massimo un grafo?

Ogni grafo completo $K_n$ ha zero punti di taglio. 
Il grafo cammino $P_n$ ha $n-2$ punti di taglio, tutti vertici interi.
Esiste un grafo connesso con più di $n-2$ punti di taglio? No.

**Teorema** Ogni grafo connesso non triviale ($n\geq 2$) contienene almeno due punti non di taglio.

**Dim** Supponiamo per assurdo esista un grafo non triviale $G$ con al massimo $1$ non cut-vertex (tutti i vertici sono di taglio tranne al massimo uno). Siano $u,v \in V(G)$ tali che $d(u,v)=diam(G)$. Almeno uno dei due (s.p.g. $v$) sarà un cut-vertex, quindi $G\setminus v$ sarà disconnesso. Prendiamo ora un vertice $w$ in una componente connessa diversa da quella dove compare $u$. Siccome $v$ è un punto di taglio di $G$, ogni cammino $u-w$ deve passare per $v$. Ma allora 
$d(u,w) > d(u,v) = diam(G)$, assurdo. $\square$

_Abbiamo mostrato di più_: ogni vertice che appartiene alla [[Distanza e connessione#Metrica|periferia]] non può essere un punti di taglio. La periferia infatti ha sempre almeno due vertici (la distanza è simmetrica!).


# Bridges

Analogamente:

**Def** (Bridge) Un arco $e$ di un grafo $G$ viene detto _ponte_ se la sua rimozione fa aumentare le componenti connesse.

**Osservazione** A differenza dei punti di taglio, rimuovere un ponte fa aumentare la componenti connesse di esattamente uno.

Vale una caratterizzazione identia a quella per i punti di taglio, tramite i cammini:

**Teorema** Un arco $e \in E(G)$ è un ponte di $G$ se e solo se $\exists u,w \in V(G)$ tali che $e$ compare in ogni cammino $u-w$.
**Dim** Identica a quella dei cut-vertex. $\square$

Inoltre, vale banalmente:
**Prop** Se $e$ è un ponte di $G$, allora i suoi vertici incidenti appartengo a diverse componenti connesse di $G\setminus e$.

Ne esiste anche un'altra in termini di cicli:
**Teorema** Un arco $e \in E(G)$ è un ponte di $G$ se e solo se non compare in nessun ciclo di $G$.
**Dim** Facciamo vedere che un arco non è un ponte se e solo se appare in un ciclo.
- $(\implies)$ Se $e$ compare in un ciclo, non è un ponte, infatti i suoi vertici incidenti ammettono ancora un cammino in $G\setminus e$, quindi appartengono alla stessa componente connessa.
- ($\implies$) Se $e$ non è un ponte, compare in un ciclo. Quindi $G \setminus e$ è ancora connesso, quindi esiste un cammino $C$ tra i vertici incidenti di $e$. Ma allora nel grafo $G$ c'è un ciclo formato dal cammino $C \cup {e}$. $\square$

> Che legame c'è tra ponti e punti di taglio? 

**Teorema** Se $e = \{u,v\}$ è un ponte di $G$, e $deg(u)\geq 2$ allora $u$ è un punto di taglio di $G$.

**Dim** Segue dalla caratterizzazione tramite cammini: infatti siccome $e$ è un ponte esistono vertici $u,v \in V$ tali che $e$ appare in ogni cammino, tuttavia se questi due veritici sono proprio gli incidenti di $e = \{u,v\}$, allora nessuno dei due è un punto di taglio, infatti per quella caratterizzazione serve che siano distinti. Questo abbiene appena uno dei due $u,v$ è diverso da quelli di $e$, quindi il vertice $u$ avrà almeno un altro vicino oltre a $v$. $\square$



# Block decomposition

**Def** Un grafo $G$ connesso, non banale (ha più di un verice), senza punti di taglio, si dice _non separabile_ o _2-connesso_.

Il secondo nome si può generalizzare a $k-$_connesso_, ovvero un grafo connesso a cui devo togliere almeno $k$ vertici per renderlo sconnesso. 

Ogni grafo può essere decomposto in sottografi massimali con questa proprietà.

**Def** (Blocco) Un _blocco_ di $G$ è un sottografo di $G$ massimale non separabile.

**Prop** Ogni arco di $G$ appare in uno e un solo blocco. Quindi i blocchi formano una partizione degli archi. 
**Dim**  Ancora una volta supponiamo per assurdo $e \in B_1,B_2$. Allora anche i suoi vertici incidenti $\{u,v\}$ appartengono a tutti e due i blocchi. 
Per ogni coppia vertici $x \in B_1$ e $y \in B_2$, siccome per ipotesi $B_1,B_2$ sono non separabili, esistono dei cammini $x-v$ in $B_1$ ed cammino $y-v$ in $B_2$ che non passano per $u$, altrimenti $u$ sarebbe stato un punto di taglio in sia in $B_1$ che $B_2$.
E' chiaro quindi che in $B_1\cup B_2$ non esiste una coppia di vertici tali che tutti i loro cammini passano per un vertice, ovvero non esistono punti di taglio, e $B_1 \cup B_2$ è ancora non separabile, contro la massimalità. $\square$

**Prop** Ogni vertice non di taglio appare in uno e un solo blocco. 
**Dim**  Supponiamo per assurdo che $v \in B_1,B_2$. Allora $B_1 \cup B_2$ è ancora non separabile, contro la massimalità di $B_1$ e $B_2$. $\square$ 

**Block graph** Il grafo dei blocchi di $G$ $B(G)$ è definito come:
- $V(B(G)) = \{B | B \text{ è un blocco di } G\}$
- $\{B_i,B_j\} \in E(B(G))$ $\iff$ $B_i \cap B_j \neq \emptyset$ 
