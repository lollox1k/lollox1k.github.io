# Line graph

Studiato negli anni $'60$, è una naturale "dualità" tra nozione di adiacenza ed incidenta.

**Def** Viene detto _line graph_ del grafo $G$ il grafo $\mathcal{L}(G)$ che ha come vertici gli archi di $G$, ed archi se i corrisponenti archi incidono su uno stesso vertice.

**Oss 1** Se $G$ è [[Circuito Euleriano|euleriano]], allora $\mathcal{L}(G)$ è [[Ciclo hamiltoniano|hamiltoniano]].

**Oss 2** Non tutti i grafi hamiltoniano hanno un corrispondente grafo euleriano $\mathcal{L}^{-1}(G)$.

**Teorema** (Baudy-Chvàtal 1972)
$$
G \text{ hamiltoniano } \iff \text{ chisura di } G \; cl(G) \text{ hamiltoniana}
$$
**Def** Dato $G$, la _chiusura_ di $G$, $cl(G)$ è il grafo che si ottiene ricorsivamente aggiungendo archi:
1. se $\{u,v\} \notin E(G)$
2. se $d(u) + d(v) \geq n$ 

**Osservazione** Sia $e = \{u,v\} \in E(G)$. Allora il grado di $e$ in $\mathcal{L}(G)$ sarà:
$$
d_{\mathcal{L}(G)}(e) = d_G(u) + d_G(v) - 2
$$
E' naturale chiedersi che legame ha l'ordine $p_L$ e la taglia $q_L$ di $\mathcal{L}(G)$ rispetto a quelle di $G$ $p,q$. 

**Proposizione** Vale $p_L = q$ e $q_L = -q +\frac{1}{2}\sum_{i=1}^p d_i^2$.
**Dim** L'ordine è banale, segue dalla definizione. Per la taglia si può usare l'[[Handshake Lemma]] con la precedente osservazione:
$$
|E(\mathcal{L}(G))| = \frac{1}{2}\sum_{i=1}^q {d_L}_i
$$
$$
= \frac{1}{2}\sum_{i=1}^q (d_G(u)+d_G(v)-2)= -q + \frac{1}{2}\sum_{i=1}^q d_G(u)+d_G(v)
$$
resta da provare
$$
\sum_{i=1}^q d_G(u)+d_G(v) = \sum_{i=1}^p d_i^2
$$
La somma di sinsitra è per ogni arco di $G$, quindi un vertice $v$ apparirà nella somma esattamente $d(v)$ volte, così che sommando sui vertici devo introdurre un fattore moltiplicativo $d_i$. $\square$ 

E' naturale definire una nozione di _line graph iterato_ $\mathcal{L}^n(G)$ con $n \geq 1$

Altra domanda interessante, quand'è che $G \cong \mathcal{L}(G)$ ? Notiamo che questo vale per i cicli $C_n$. Infatti una cosa che deve valere è taglia = ordine. In effetti questo è l'unico caso.

**Teorema** Sia $G$ connesso. Allora  $G \cong \mathcal{L}(G)$ se e solo se $G$ è un ciclo $C_n$.
**Dim** 
- ($\impliedby$) Si verifica banalmente che ogni ciclo è isomorfo al suo line graph.
- ($\implies$) Siccome è isomorfo, sicuramente $|V(G)|=|E(G)| =: n$. Usiamo il legame che conosciamo tra l'ordine e la taglia di un grafo e il suo line graph per ottenere la relazione:
$$
\sum_{i=1}^n d_i^2 = 4n  
$$
che insieme al classico handshake lemma mi permette di calcolare la varianza:
$$
Var[d] = \mathbb{E}[d^2]-\mathbb{E}[d]^2 = \frac{\sum_i d_i^2}{n} - \left(\frac{\sum_i d_i}{n}\right)^2 = 4-4=0
$$
quindi il grafo è _uniforme_ di grado $d$, sostituendo arriviamo all'unica solizione $d=2$, e sappiamo un grafo è uniforme di grado due e connesso se e solo se è un [[Grafo semplice|ciclo]]. $\square$

In generale, se i linegraph sono isomorfi, i grafi di partenza lo sono? Non sempre, controesempio: $K_3$ e $K_{1,3}$ la _forchetta_, che tra l'altro si dismotra non essere il linegraph di nessun grafo. Infatti chiaramente $K_3 \ncong K_{1,3}$ ma $\mathcal{L}(K_3) = \mathcal{L}(K_{1,3}) = K_3$. 

**Teorema** Siano $G,G'$ connessi e tali che $\mathcal{L}(G) \cong \mathcal{L}(G')$. Allora $G \cong G'$, a meno che $G \cong K_3$ e $G' \cong K_{1,3}$.
 
**Def** Un grafo $G$ è detto _line graph_ se è il linegraph di un qualche grafo, ovvero $\exists H$ tale che $\mathcal{L}(H)=G$.

Come detto prima, $K_{1,3}$ la forchetta è un esempio di un non line graph.

Il seguente teorema è una caratterizzazione dei line graph dovuto ad Krausz (1942).

**Teorema** (caratterizzazione dei linegraph)
Le seguenti sono equivalenti:
1. $G$ è un linegraph.
2. Gli archi di $G$ si possono partizionare in sottografi completi in modo che nessun vertice stia in più di due completi.
3. $G$ non contiene $K_{1,3}$ come sottografo indotto, e se qualora due triangoli hanno un alto in comune, allora il sottografo ridotto dei $4$ vertici è un $K_4$ 
4. Nessuno di nove sottografi mostri è un sottografo indotto di $G$. (configurazione proibite).

Vediamo una caratterizzazione ristretta agli [[Alberi]].
**Teorema** (Chartrand) Un grafo è il linegraph di un albero se e solo se è il grafo dei blocchi $B(G)$ di $G$, in cui ogni cutpoint sta in esattamente due blocchi.



