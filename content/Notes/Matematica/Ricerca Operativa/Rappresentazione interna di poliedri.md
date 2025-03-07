L'obbiettivo è il _teorema di Wyel_, rappresentare un poliedro in forma interna, ovvero come una combinazione particolare di un insieme finito di oggetti, rispetto alla definizione esterna tramite sistema di disequazioni [[Poliedri#Def]].

### Def cono 
Un insieme non vuoto $C \subseteq \mathbb{R}^n$ è detto _cono_ se $\forall x \in C$ $\lambda x \in C$ per tutti $\lambda \geq 0$.
Geometricamente, dato un punti diverso dall'origine, contiene tutta la semiretta in quella direzione.

### Def cono convesso
Un insieme $C \subseteq \mathbb{R}^n$ è detto _cono convesso_ se presi qualunque due punti $x,y \in C$ la loro 
 [[combinazione conica]] appartiene a $C$. 

#### Oss 
Ovviamente questa definizione è equivalente a quella di insieme convesso e cono allo stesso tempo.

## Teorema di Weyl
Dati due insieme di punti in $\mathbb{R}^n$, $V = \{v 1 , . . . , v_k\}$ e $D = \{d_1 , . . . , d_q\}$ l’insieme $conv(V) + cone(D)$ è un poliedro.

#### Dim 
L'idea è vedere il tutto come un insieme di disequazioni e vincoli, quindi un poliedro. Basta eliminare le variabili $\lambda$ e $\mu$ con una proiezione, ed ottenere così la rappresentazione esterna (implicita) del poliedro.
Se $V = ∅$ abbiamo che $conv(V ) = ∅$ e quindi anche $conv(V ) + cone(D)$ è l’insieme vuoto, che è un poliedro. 
Se invece $V$ non è vuoto abbiamo che i punti $x$ di $conv(V ) + cone(D)$ sono del tipo $x = w + z$ con $w ∈ conv(V)$ e $z ∈ cone(D)$. 
Ricordando la definizione di involucro convesso e quello di involucro conico abbiamo quindi che $x$ appartiene a $conv(V ) + cone(D)$ se e solo se esistono $λ ∈ \mathbb{R}^k$ e $µ ∈ \mathbb{R}^q$ tali che:
$$
x = z + w = \sum_{i=1}^k \lambda_i v_i + \sum_{j=1}^q \mu_j d_j
$$
dove per i coefficienti devono valere:
$$
\sum_i \lambda_i = 1, \qquad \lambda_i \geq 0 \quad\forall i
$$
$$
\mu_j \geq 0 \quad \forall j
$$
ricordando che ogni vincolo di uguaglianza può essere "spezzato" in due vincoli di disuguaglianza, otteniamo il tutto come un sistema di disequazioni. In altre parole, $conv(V ) + cone(D)$ è la [[Eliminazione di Fourier-Motzkin|proiezione]] su $\mathbb{R}^n$ del poliedro $Q$ definito dal sistema precedente, ed è quindi un poliedro.

Vogliamo ora dimostrare il contrario, meno banale, ovvero che ogni poliedro si può scrivere in quella forma. Cominciamo con poliedri limitati.
## Teorema 
Sia $P$ un poliedro non vuoto e limitato. Allora detto $V$ l'insieme dei suoi vertici, possiamo scrivere:
$$
P = conv(V) = conv(V) + cone(0)
$$
#### Dim 
Se $x\in P$ è un vertice, allora è banalmente vero. Supponiamo ora che $x \notin V$. Dato che non è un vertice, e $P$ è limitato, non contiene rette, quindi possiamo applicare [[Poliedri#Lemma]], e trovare due punti $x_1,x_2 \in P$ su una retta tali che in questi punti sono attivi tutti i vincoli di $x$ più almeno un altro, ed inoltre posso esprimere $x = \alpha x_1 + (1-\alpha)x_2$ con $\alpha \in (0,1)$ (notiamo che $x_1 \neq x_2 \neq x$). Se $x_1$ e $x_2$ sono vertici, ho fatto, altrimenti reitero il processo, sono sicuro che in un numero finito di passi arrivo a dei vertici. $\square$

Abbiamo usato la limitatezza, che ci permette di trovare due punti dove la retta "sbatte". Nel caso di poliedri non limitati, ma che comunque non contengono rette, in generale potrò trovare solo un punto di collisione. Vediamo come trattare questo caso tramite le _direzioni di recessione_.

## Def direzione di recessione
Sia dato un poliedro non vuoto $P$ e un suo punto $x$. Un vettore $d ∈ \mathbb{R}^n$ è detto direzione di recessione se $x + λd$ appartiene a $P$ per ogni $λ$ non negegativo. In altre parole se _la semiretta di origine $x$ e direzione $d$ è tutta contenuta in P_.

### Oss
Le direzioni di recfessione (che, come vedremo subito, non dipendono dal punto $x$ rappresentano quindi le direzioni in cui ci si può “muovere all’infinito” rimanendo dentro l’insieme $P$.

## Teorema 
Estendiamo il teorema precedente, ovvero la rappresentazione interna di poliedri non vuoti e finiti al caso non limitato, ma sempre senza rette: è possibile che una semiretta sia contenuta nel poliedro, questo fa cadere una parte della dimostrazione del teorema precedente. 

Mostriamo il seguente fatto:
$$
P = conv(v_1,\dots,v_p) + rec(P)
$$
### Dim 
Siccome $P$ è non vuoto, prendiamo $x\in P$. Se è un vertice ho finito, supponiamo non lo sia. Sempre per il lemma precedente, posso considerare una retta dove tutti i vincoli attivi rimangono tali, e siccome per ipotesi $P$ non contiene rette, almeno da uno dei due versi la rette deve "sbattere", ovvero attivare altri vincoli. Se trovo sempre due punti di collisione, reitero fino a giungere a dei vertici. Nel caso di un lato illimitato, posso espremire $x$ come:
$$
x = x_1 + \lambda d, \qquad \lambda \geq 0
$$
dove $x_1$ è il punto di collisione:
$$
x_1 = x -\overline \lambda d
$$
Quindi posso esprimere $x$ come un punto $x_1$ dove sono attivi tutti i vincoli di $x$ più almeno un altro ed una direzione di recessione, o come combinazione convessa di due punti $x_1$ e $x_2$ dove sono attivi più vincoli. Reitero fino ad avere solo vertici!. $\square$

Vogliamo far vedere come caratterizzare l'insieme delle direzioni di recessioni come una combinazione conica di un insieme finito di elementi $rec(P)=cone(d_1,\dots,d_k)$.

### Teo caratterizzazione algebrica delle dir. di recessione
1. Tutte le direzioni di recessione di un poliedro $P = \{x \; \vert \; Ax\leq b\}$ sono tutte e sole le soluzioni del sistema di disequazioni omogeno associato:
$$
Ad \leq 0
$$
2. Le $d$ non dipendono dal punto scelto $x$.

#### Dim
Supponiamo che la retta $x + \lambda d$ sia tutta contenuta in $P$ per ogni $\lambda \geq 0$. Allora vale:
$$
A(x+\lambda d) = Ax + \lambda Ad \leq b
$$
Siccome per ipotesi $x\in P$, vale $Ax \leq b$, il che implica banalmente $\lambda Ad \leq 0$ $\forall \lambda$, quindi:
$$
Ad \leq 0
$$
Viceversa, se vale la precedente cosa, segue che:
$$
A(x+\lambda d) = Ax +\lambda Ad \leq b
$$
per i segni, quindi **1** è dimostrato. Il punto **2** segue banalmente, notando che $x$ scompare dalla caratterizzazione.

### Oss
L'insieme delle direzioni di recessioni $rec(P)$ è quindi un _cono poliedrale_. Facciamo vedere come un cono poliedrale si possa rappresentare come combinazione conica di un insieme finito di elementi.

## Teorema 
Sia $C = \{x \in \mathbb{R}^n \vert Ax \leq 0\}$ un _cono poliedrale_, allora vale la rappresentazione:
$$
C = cone(d_1,\dots,d_n) \qquad d_i \in C
$$
si può esprimere come _combinazione conica_ di un _numero finito_ di suoi elementi, analogamente per i poliedri limitati e i veritici.
#### Dim 
Consideriamo la combinazione conica delle righe della matrice $A$:
$$
cone(a_1, \dots a_n) = \{x \in \mathbb{R}^n \vert Dx \leq 0\}
$$
dove abbiamo usato il [[Combinazione conica#Teorema|teorema]] che ci consente di rappresentare una combinazione conica come un cono poliedrale. 
Consideriamo le righe della nuova matrice $d_i$. Siccome $a_i \in cone(a_1,\dots,a_n)$ deve valere:
$$
d_j^Ta_i = a_i^Td_j \leq 0 \quad \forall j
$$
quindi i vettori $d_i$ soddisfano il sistema $Ax\leq 0$, sono contenuti in $C$, ovviamente anche la loro combinazione conica, quindi:
$$
cone(d_i) \subseteq C
$$
Mostriamo ora l'altro verso, per ottenere l'equivalenza degli insiemi. Sfruttiamo ancora il teorema di rappresentazione della combinazione convessa, stavolta dei vettori $d_i$:
$$
cone(d_i) = \{x \in \mathbb{R}^n \vert Gx \leq 0\}
$$
per una certa matrice $G$. Siccome $d_i \in cone(d_i)$, deve valere:
$$
g_j^T d_i = d_i^T g_j \leq 0
$$
quindi i vettori $g_j$ soddisfano il sistema $Dx\leq 0$, che era proprio $cone(a_i)$. Ogni punto di $C$ soddisfa anche le disequazioni implicate da $A$ che sono proprio quelle di $G$, quindi:
$$
C \subseteq cone(d_i) \qquad \square
$$

### Conclusione
$$
P = conv(v_1,\dots,v_k)+rec(P)= conv(v_1,\dots,v_k) + cone(d_1,\dots,d_p)
$$
$\square$