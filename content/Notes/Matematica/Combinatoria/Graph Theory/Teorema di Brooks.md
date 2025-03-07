
# Teorema di Brooks

Abbiamo visto come si puù costruire un [[Graph coloring#Algoritmo greedy e upper bound|algoritmo greedy]] che trova una colorazione con al più $d(G)+1$ colori.

**Question** Sotto quali ipotesi posso invece avere $\chi(G) \leq d(G)$?

**Teorema** (Brooks 1941)
Sia $G$ un grafo con $d(G) = d$. Se $G$ soddisfa le condizioni:
1. non contiene un grafo completo $K_{d+1}$;
2. se $d>2$ ($G$ non è un ciclo)

Allora $\chi(G) \leq d(G) = d$.

**Dim** Ragioniamo per assurdo. Supponiamo esista un grafo G che rispetta **1** e **2**, e inoltre la negazione del teorema, ovvero $\chi(G) > d$, che unito al teorema precedentemenente dimostrato ci da $\chi(G) = d + 1$. Chiamiamo questa proprietà **3**. Facciamo vedere come un grafo che soffisfi **1**, **2** e **3** non esista.

Per prima costa, se $G$ soddisfa queste proprietà, allora esiste un sottografo $G' \subseteq G$ che le soddisfa. Consideriamo un tale **sottografo minimale**. 

**Claim 1** $\forall x \in V(G)$ si ha che $\chi(G\setminus \{x\}) < \chi(G)$.  Consideriamo due casi:
1. $d(G \setminus \{x\}) < d(G)$. E' facile vedere che vale anche per il numero cromatico:
$$
\chi(G \setminus \{x\}) \leq d(G\setminus \{x\}) +1 < d(G) +1= \chi(G) 
$$
2. $d(G \setminus \{x\}) = d(G)$. Se non valesse il claim, ovvero:
$$
\chi(G \setminus \{x\}) = \chi(G) = d(G) + 1 = d(G \setminus \{x\}) +1
$$
ma questo va contro l'ipotesi di mininalità rispetto alle proprietà **1** **2** e **3**.

**Strategia** Prendo in $G$ un vertice $x$ di grado massimo $d$.  Vedremo come $\Gamma(x) \cup \{x\}$ induce un completo di ordine $d+1$ contro la condizione **1**.

Il claim $1$ mostra come il numero cromatico debba scendere rimuovendo qualunque vertice, quindi in particolare un vertice $x$ di grado massimo $d$.
Posso definire una colorazione ottimale, colorando i vicini $\Gamma(x)$ con $d$ colori e $x$ con il colore $d+1$.

Quindi $x$ sarà l'unico vertice di colore $d+1$, infatti per il claim $1$ $\chi(G \setminus \{x\}) < d + 1$ . Quindi posso costruire una $d$ colorazione del grafo senza $x$. 

Chiamiamo questa colorazione $x-$ottimale.

**Claim 2** Nel sottografo indotto dai vertici $\Gamma(x) \cup \{x\}$ sono presenti tutti i $d+1$ colori (condizione necessaria affinchè sia un completo). Questo è ovvio, altrimenti se mancasse un colore, potrei usare quello per colorare $x$, ottenendo una colorazione migliore $\chi(G) = d$ ma contro l'ipotesi **3**.

**Claim 3** Mostriamo come ogni vicino di $x$ sia connesso da un cammino semplice, $x_i \sim x_j$ $\forall x_i, \,x_j \in \Gamma(x)$.

Chiamo $H_{ij}$ il sottografo bicromatico indotto dai colori $i$ e $j$, con $i \neq j$  a valori in $[d]$.

Facciamo vedere come $x_i$ e $x_j$ appartengono alla stessa componente connessa, ovvero esiste un cammino bicromatico che li collega. Chiamiamo la componente connessa dove compare $x_i$ $H \subseteq H_{ij}$. Se per assurdo $x_j \notin H$, riusciamo a costruire nuova colorazione $f^{'}$  $x-$ottimale:
$$
y \mapsto f^{'}(y) := \begin{cases} 
f(y) \text{ se } y \notin H \\
i \text{ se } f(y) = j, \; y \in H \\
j \text{ se } f(y) = i, \; y \in H
\end{cases} 
$$
> Ho scambiato il colore $i$ con $j$ nella componente connessa $H$ dove compare $x_i$, ($f(x_i) = i$). 

E' ancora una colorazione, infatti ho supposto che $x_i$ ed $x_j$ non fossero collegati, quindi lo scambio non crea problemi. Ma ora ho due vertici con il colore $j$, quindi posso definire una nuova colorazione con solo $d$ colori, ponendo $f(x)=i$, assurdo contro il claim 2.

**Claim 4** La componente connessa $H_{ij}$ che contiene $x_i$ e $x_j$ è un cammino semplice.
Costruiamo un cammino $C_{ij}$ da $x_i$ a $x_j$, mostrando che ad ogni passo non c'è una biforcazione:
1. Primo passo: da $x_i$ non c'è una biforcazione, ovvero $d_{H_{ij}}(x_1) = 1$. Se ci fosse:
$$
\vert \Gamma_G(x_i) \cup \{x_i\}\vert < d+1 = \chi(G)
$$
ovvero in questo sottografo manca un colore, chiamiamolo $c$. Se definisco una nuova colorazione, che lascia invariati tutti i vertici tranne $x_i$, tale che $f^{'}(x_i) = c$, ottengo una  nuova colorazione $x-$ottimale, ma il colore $i$ manca nel sottografo indotto dei vicini di $x$, contro il claim 2.
2. Secondo passo: neanche dopo $x_i$ ci sono biforcazioni. Supponiamo che esistano biforcazioni, sia $y$ il primo vertice dove ho una biforcazione. Considero il sottografo indotto da $y$ e dai suoi vicini in $H$, $S := \Gamma_H(y) \cup \{y\}$. Siccome è una biforcazione, contiene almeno $4$ vertici.  Sia $f(y)=k$, con $k \in \{i,j\}$, si avrà che $f(\Gamma(y)) = \overline k$ il colore rimanente. Che succede se rimuovo dal grafo iniziale?
$$
\vert \Gamma_G(y) \cup \{y\} \vert \leq d + 1
$$
$$
\vert \Gamma_G(y) \cup \{y\} \setminus S \vert \leq d + 1 - 4 = d - 3
$$
siccome $S \subseteq \Gamma_G(y) \cup \{y\}$.
I colori che compaiono per colorare l'intorno di $y$, togliendo $y$ e i suoi vicini di colore $i,j$ sono al massimo $d-2$.

Se ho una biforcazione, ho almeno $3$ vicini con lo stesso colore, quindi ho sicuramente un colore $c \neq i,j$ tra i primi $d$ che non ho usato. Ridefinisco una nuova colorazione tale che $f(y)= c$ e lascia il resto invariato. E' ancora una colorazione $x-$ottimale, ma ho scollegato $x_i$ da $x_j$, contro il claim $3$.

**Claim 5** Siano $i,j,k$ tre vertici distinti, $f$ una colorazione $x-$ottimale, $C_{ij}$ un cammino semplice tra $x_i$ ed $x_j$, $C_{jk}$ tra $x_j$ e $x_k$. Allora $V(C_{ij}) \cap V(C_{jk}) = \{x_j\}$.

Supponiamo per assurdo $y \in V(C_{ij}) \cap V(C_{jk})$ ma $y \neq x_j$. Essendo un'intersezione tra due cammini bicromatici, quando si intersecatno creano una stella a $5$ vertici $S$, con in mezzo il vertice $y$ del colore in comune ($f(y)=j$). Quindi:
$$
\vert \Gamma_G(y) \cup \{y\} \setminus S\vert \leq d + 1 - 5 = d-4
$$
manca un colore $c \neq i,j,k$, definisco una nuova colorazione tale che $f^{'}(y)=c$ e lascia il resto invariato. E' ancora $x-$ottimale, ma ho sconnesso $x_i$ ed $x_j$, contro il claim 3.

**Claim 6** Il cammino semplice $C_{ij}$ è lungo $1$ (è un arco). 
Supponiamo per assurdo $\{x_i,x_j\} \notin E(G)$. Poichè $d(G)>2$, esiste in $\Gamma(x)$ almeno un altro vertice $x_j$, ovvero $\vert \Gamma(x) \cup \{x\}\vert \geq 4$, quindi posso trovare $x_i,x_j,x_k \in \Gamma(x)$ distinti.
Sia $f$ una colorazione $x-$ottimale in cui scambio i colori $i$ e $k$ solo sul cammino $C_{ik}$.
E' ancora una colorazione $x-$ottimale, ma crea un assurdo col claim precedente: Infatti, i nuovi cammini indotti da questa nuova colorazione vanno contro il claim precedente:
Prendiamo un $y \in C_{ij}$, collegato ad $x_i$ ed $x_j$. Possiamo farlo, perchè per ipotesi $x_i$ ed $x_j$ non sono collegati, quindi esiste almeno un vertice tra di loro. Si avrà $f(y) = j$. Consideriamo ora l'intersezione dei vertici $V(C_{ij}) \cap V(C_{jk})$. L'assurdo si ha perchè $y \in V(C_{jk})$, quindi appartiene all'intersezione contro il claim 5.

In Conlusione, abbiamo fatto vedere che $\Gamma_G(x) \cup \{x\}$ è un completo di $d+1$ vertici, questo è assurdo perchè per ipotesi doveva valere la proprietà **1**, non contenere $K_{d+1}$. $\square$