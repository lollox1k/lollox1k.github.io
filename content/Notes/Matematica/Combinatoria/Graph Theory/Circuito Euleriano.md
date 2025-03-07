# Circuito Euleriano

Un [[Grafo semplice#Passeggiate Cammini Circuiti Cicli|circuito]] è detto *Euleriano* se visita tutti i vertici del grafo.

Un grafo viene detto euleriano se ammette un circuito euleriano, ovvero esiste:
$$
\mathcal{C} = x_1, e_1, \dots e_t, x_1 \qquad t = \vert E(G)\vert
$$
> la lunghezza del circuito è la taglia del sottografo.
> "Si può disegnare senza staccare la penna e ripassare sopra"

**Teorema** (Eulero)
Sia $G$ un grafo senza punti isolati, Allora:
$$
G \text{ euleriano} \iff G \text{ connesso e vertici di grado pari} 
$$
**Dim** (Machì)
($\implies$) 
Sia $\mathcal{E}$ il cammino euleriano del grafo $G$ privo di punti isolati.
L'esistenza di un cammino che contiene tutti gli archi (quindi anche tutti i vertici dato che non esistono vertici isolati) implica che il grafo è _connesso_.
Ogni vertice ha sicuramente un arco in entrata ed uno in uscita distinti, quindi ogni volta che il vertice compare nel cammino euleriano il *grado aumenta di due*, ed è quindi pari (siccome ogni arco compare nel cammino).

($\impliedby$)
Costruiamo un circuito euleriano come sottografo: 
siccome ogni vertice ha grado pari, ed il grafo è connesso esiste un [[Grafo semplice#Passeggiate, Cammini, Circuiti, Cicli|ciclo]], chiamiamolo $\mathcal{C}$. Non è detto che sia euleriano (potrebbe mancare qualche arco), quindi $\mathcal{C} \subseteq \mathcal{E}$.
Facciamo vedere che se $G$ contiene un circuito, ne contiene uno massimale, che sarà proprio quello euleriano.

Consideriamo il sottografo $G'$ creato rimuovendo tutti gli archi che compaiono in $\mathcal{C}$. 
$G'$ potrebbe non essere più connesso, ma ogni vertice ha ancora grado pari (abbiamo rimosso un numero pari di archi da ogni vertice).

Per induzione sulle componenti connesse di $G'$ possiamo ottenere il cammino euleriano, infatti rimuovo tutti gli archi dei circuiti, non posso arrivare ad un sottografo vuoto, sennò il cicuito era euleriano!

## Teorema di Eulero 2
Una caratterizzazione leggermente diversa
Sia $G$ un grafo connesso, allora le seguenti sono equivalenti:
1. $G$ è _euleriano_.
2. ogni vertice di $G$ ha _grado pari_.
3. Gli archi di $G$ possono essere partizionati in cicli disgiunti per archi.

**Dim**
$(1 \implies 2)$ Sia $\mathcal{E}$ il circuito euleriano. Sia $v \in V$, ogni volta che $\mathcal{E}$ entra in $v$, deve uscire in $v$ da un arco diverso. Siccome $\mathcal{E}$ non ripete mai un arco, il numero di archi incidenti a $v$ deve essere pari.

$(2 \implies 3)$ Supponiamo che ogni vertice di $V$ sia di grado pari. Facciamo induzione sui cicli di $G$. Siccome $G$ è connesso ed ogni vertice ha grado pari, $d(G)\geq 2$, dunque esiste un ciclo $\mathcal{C}$. Se contiene un solo ciclo, allora il ciclo stesso è la partizione cercata. Per ipotesi induttiva, supponiamo valga quando $G$ contiene $k$ cicli. 
Se $G$ contiene $k+1$ cicli, posso ottenere un sottografo $G'$ indotto rimuovendo gli archi che compaiono in uno dei cicli. Continua a valere l'ipotesi sui gradi, infatti ho tolto da ogni vertici due archi (se compariva nel ciclo) o zero (se non compariva). Inoltre $G'$ ha componenti connesse (può essere disconnesso) che contengono non più di $k$ cicli. Quindi ogni componente connessa per ipotesi induttiva può essere partizionata in cicli disgiunti per archi. Insieme al ciclo rimosso, formano una partizione del grafo $G$. 

$(3 \implies 1)$  Supponiamo di avere una partizione degli archi di $G$ in cicli $S_1, S_2, \dots, S_k$. Sia $C$ un circuito massimale di $G$, tale che l'insieme degli archi di $C$ è esattamente:
$$
E(S_{j_1}) \,\cup\, E(S_{j_2}) \, \cup \,\dots\, \cup\, E(S_{j_m})
$$
Supponiamo ora che $e \in E(G)$ non appartenga al circuito $C$, ma che $e$ incida su vertice $v \in C$ (per la connessione di $G$ posso trovarlo). Sia $e \in S_i$, necessariamente anche $v \in S_i$.

Sia $C'$ un circuito ottenuto concatenando $S_i$ a $C$ nel vertice $v$, ottengo un circuito più grande che contiene $C$ contro la massimalità. Questo significa che non esiste tale arco $e$, quindi $C$ è euleriano. $\square$

## Cammino euleriano

E' un cammino (posso ripetere i veritici) dove compaiono tutti gli archi. Vale il seguente corollario

**Corollario** Un grafo connesso $G$ ammette un _cammino euleriano_ se e solo se esistono al massimo due vertici di grado dispari.

**Remark** il numero di vertici di grado dispari deve essere pari, quini ne esistono almeno due, mai uno solo.

**Dim**
$(\impliedby)$ Siano $u,v$ i vertici di grado dispari. Se $uv \notin E(G)$ creo un nuovo grafo $G'$ aggiungendo quest'arco. $G'$ continua ad essere connesso, ed ora ha tutti i gradi pari: esiste quindi un circuito euleriano. Togliendo l'arco aggiunto primo al circuito, ottengo un cammino euleriano.
Se $uv \in E(G)$, creo un nuovo grafo $G'$ rimuovendo l'arco. Potrei perdere la conessione, ma al massimo ottengo due componenti connesse, con gradi tutti pari: posso quindi trovare due cicli euleriani, che posso poi unire con l'arco rimosso.
$(\implies)$ Sia $\mathcal{T}$ il cammino (trail) euleriano. Per i vertici all'interno valgono le considerazioni fatte per il circuito euleriano, avranno necessariamente grado pari. Mentre per gli estremi, ho sicuramente il primo/ultimo arco, ed all'interno entrate ed uscite, quindi un numero dispari. $\square$


