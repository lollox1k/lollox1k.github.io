# Matching

**Def** Un _matching_ $M$ è un insieme indipendente di archi $M \subseteq E(G)$, ovvero archi che non hanno estremi in comune.

**Def** Dato un matching $M$ in un grafo $G$, l'insieme dei _vertici che incidono su un arco del matching_ vengono chiamati _saturati_ dal matching, o $M$-saturati. I restanti _non saturati_.

**Def** Un matching che satura tutti i vertici di un grafo viene detto _perfetto_.

Analogamente posso definire matching massimali e massimi.

**Def** Dato un grafo $G$ ed un suo matching $M$, un _cammino alternante_ è un cammino in $G$ dove gli archi si alternano in archi del matching e non.

**Def** Un _cammino aumentante_ è un cammino alternante dove il primo e l'ultimo vertice sono non saturati dal matching.

Il motivo di questo nome diviene chiaro col seguente teorema.

**Teorema** (Berge) Un matching $M$ è massimo se e solo se $G$ non contiene cammini aumentanti.

**Dim** 
- ($\implies$) Assumiamo che $M$ sia un matching massimo, e supponiamo che esista un $P = v_1,v_2,\dots,v_k$ cammino aumentante.  Siccome è aumentante, $k$ deve essere pari, e gli archi $v_2v_3,v_4v_5, \dots, v_{k-2}v_{k-1}$ sono nel matching, mentre gli altri no. Ma allora posso definire un matching migliore che contiene un arco in più:
$$
M' = (M\setminus \{v_2v_3,v_4v_5, \dots, v_{k-2}v_{k-1}\}) \cup \{v_1v_2,\dots,v_{k-1}v_k\}
$$
contraddizione.
- ($\impliedby$) Assumiamo che $G$ non abbia $M$-cammini aumentanti, supponiamo che $M'$ sia una matching migliore di $M$. Definiamo il sottografo $H\subseteq G$ nel seguente modo:
$$
V(H)=V(G) \qquad e \in E(H) \iff e \in M\Delta M'
$$
Studiamo qualche proprietà del sottografo. Siccome tutti i vertici di $H$ hanno al massimo un arco di $M'$ e uno di $M$, $d(H)\leq 2$. Questo significa che ogni componente connessa di $H$ è un punto isolato, un cammino, o un ciclo. Se è un ciclo, deve essere pari, infatti non posso avere due archi adiacienti dello stesso matching. Siccome $|M'| > |M|$, deve esistere almeno un arco fuori da un ciclo, quindi un cammino con più archi di $M'$, quindi deve iniziare e finire con archi in $M'$. Ma allora questo cammino è un $M$-cammino aumentante, contraddizione. Quindi non può esistere tale matching migliore $M'$, $M$ è un matching massimo. $\square$

