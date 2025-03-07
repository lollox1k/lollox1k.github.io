# Poliedri
I poliedri sono particolari insiemi convessi che rivestono un ruolo importante
nei problemi di ottimizzazione per la frequenza con la quale si incontrano. E'
possibile dare risultati molto approfonditi ed eleganti sui poliedri, e lo studio dei
poliedri costituisce un importante capitolo dell’[[Ottimizzazione di funzioni convesse|ottimizzazione convessa]].

## Def
Un _poliedro_ in $\mathbb{R}^n$  è l’insieme delle soluzioni di un numero
finito di equazioni e disequazioni (non strette) lineari.

Con questa definizione un poliedro è sempre un insieme _chiuso_ e _convesso_ (si veda [[Insieme convesso#Teorema Intersezioni|Intersezione di convessi]]).

_Geometricamente_ le soluzioni di un’equazione lineare rapp-
resentano un iperpiano, mentre le soluzioni di una disequazione (non stretta) rappresenta un semispazio chiuso. 
Vediamo quindi che, con terminologia più geometrica, possiamo affermare che _un poliedro è l’ intersezione di un numero finito di semispazi chiusi_.

## Vertici
Geometricamente è chiaro cosa siano. Algebricamente? Esprimiamo un poliedro come:
$$
Ax \leq b
$$
senza perdità di generalità. I vertici sono i punti dove sono "attivi" un numero massimo di vincoli.
### Def vincoli attivi
Se un vettore $\overline x \in \mathbb{R}^n$ soddisfa $a_i^T x = b_i$ per un qualche $i \in \{1,\dots,m\}$ (le righe di $A$) si dice che il corrispondente vincolo è attivo in $\overline x$. Indichiamo l'insieme dei vincoli attivi in un generico punto come $I(x)\subseteq \{1,\dots,m\}$.

La cosa da notare è che in un vertice sono attivi esattamente $n$ vincoli, ma bisogna stare attenti a possibili vincoli ritondanti: _infatti in un vertice sono attivisi $n$ vincoli linearmente indipendenti_ (intendiamo che i vettori $a_i$ sono l.i.).

Possiamo caratterizzare i vertici di un poliedro in maniera equivalente:
$\overline x \in \mathbb{R}^n$ è un vertice del poliedro $Ax\leq b$ sse:
1. Esistono $n$ righe $a_i^T$  della matrice $A$ con $i \in I(\overline x)$ che sono linearmente indipendenti;
2. $\overline x$ è soluzione unica del sistema $a_i^T \overline x = b_i$ $\forall i \in I(\overline x)$.
L'equivalenza è una conseguenza del [[Teorema di  Rouché-Capelli]].

Per verificare se un punto è un vertice di un poliedro dato basta quindi prima di tutto verificare l’ammissibilità e, qualora questa risulti soddisfatta, basta verificare qual è il rango 
dei vincoli attivi.

#### Corollario 1
Se la matrica $A\in \mathbb{R}^{m\times n}$ ha un numero di righe l.i. minore di $n$, allora _il poliedro non ha vertici_.
Questo si verifica ad esempio se $m<n$.
#### Corollario 2
Il numero di vertici è finito. Date $m$ righe della matrice $A$, certamente $n\leq m$ righe l.i. sono minori di tutte le possibile scelte di $n$ righe da $m$, ovvero:
$$
\text{ \# vertici} \leq \binom{m}{n} \leq m^n \qquad \square
$$
Possono essere tanti, ma sono finiti!. 

# Esistenza dei veritci

## Quando un poliedro ha almeno un vertice?
Non tutti i poliedri hanno vertici, basta considerare il poliedro definito da una singola disequazione, che genera un semispazio (privo di vertici), oppure nel caso del _corollario 1_.

In generale, se la matrice $A$ ha un _numero massimo di righe lineramenti indipenenti_  $k<n$, è ovvio che non avrà un vertice. Facciamo vedere come questa condizione oltre ad essere sufficiente affinchè non abbia vertici, è anche necessaria.

Questa condizione è equivalente al fatto che il poliedro _non contenga rette_. Per dimostrare questa equivalenza, dimostriamo un lemma:
### Lemma
Dato un poliedro non vuoto $P = \{x \in \mathbb{R}^n \; | \; Ax \leq b\}$ e un suo punto $\overline x \in P$, se questo non è un vertice e $P$ non contiene rette, allora esiste una direzione $d$ tale che:
1. Esiste un punto $y\in P$ che appartiene alla retta $R(\overline x, d)$ tale che in $y$ sono attivi tutti i vincoli di $\overline x$ e almeno un altro vincolo;
2. esiste un $\overline \lambda > 0$ abbastanza piccolo tale che tutti i punti sulla retta  del tipo $\overline x + \lambda d$ con $\lambda \in [-\overline \lambda, + \overline \lambda]$ appartengono a $P$.

Geometricamente è chiaro cosa stiamo dicendo: partendo da $\overline x$ traccio una retta nel sottospazio dove sono attivi i vincoli di $\overline x$, questa prima o poi deve "sbattere da qualche parte", ovvero in un bordo del poliedro dove sono attivi altri vincoli.
#### Dim
Per ipotesi, essendo $\overline x$ non un vertice in esso saranno attivi un numero di vincoli $k< n$. Allora il sistema omogeneo ha infinite soluzioni:
$$
a_i^T d = 0 \qquad \forall i \in I(\overline x)
$$
scegliamo una soluzione non banale, ovvero $d\neq 0$, consideriamo la retta $R(\overline x, d)$, è facile vedere che lungo la retta i vincoli che erano attivi in $\overline x$ rimangono attivi:
$$
a_i^T(\overline x + \lambda d)= a_i^T\overline x+ \lambda a_i^Td = b_i
$$
Se invece guardiamo i vincoli non attivi, sappiamo che vale:
$$
a_i^T\overline x < b_i
$$
per continuità, siccome le disequazioni sono strette e definiscono semispazi aperti, posso trovare un aperto sulla retta abbastanza piccolo da continuare a rispettare anche le disugualgianze relative ai vincoli attivi, scegliendo $\overline \lambda$ abbastanza piccolo: quindi sono ancora dentro al poliedro, dimostrando il punto **2**.
Per dimostrare il primo punto, siccome il poliedro non contiene rette, ciò significa che per un certo $\lambda$, si esce, ovvero qualche vincolo non viene più soddisfatto. Tale vincolo non soddisfatto è necessariamente uno di quelli non attivi in $\overline x$, perchè lungo la retta questi sono sempre soddisfatti con uguaglianza.
In maniera precisa:
un punto della retta appartiene al poliedro se:
$$
a_i^T(\overline x + \lambda d) \leq b_i, \qquad \forall i \notin I(\overline x)
$$
non controlliamo i vincoli attivi, che sono sempre soddisfatti.
Per ogni vincolo $i$ ho 3 casi:
1. $a_i^T d= 0$ , in questo caso il vincolo è soddisfatto per ogni $\lambda$;
2. $a_i^T d > 0$, in questo caso $a_i^T(\overline x + \lambda d) \leq b_i$ solo quando $\lambda$ è:
$$
\lambda \leq \lambda_i = \frac{b_i-a_i^T\overline x}{a_i^T d} > 0
$$
3. $a_i^T d < 0$, in questo caso $\lambda$ deve essere:
$$
\lambda \geq \lambda_i = \frac{b_i-a_i^T\overline x}{a_i^T d} < 0
$$
Siccome la retta non è contenuta in $P$, per almeno un vincolo $i$ si è nel caso **2** o **3**. Supponiamo di essere nel caso **2**, sia $j$ l'indice che corrisponde il più piccolo $\lambda_i$. E' chiaro allora che il punto $y = \overline x + d\lambda_j$ appartiene a $P$, e sono attivi tutti i vincoli di $\overline x$ ed il vincolo $j$.
Per il caso **3**, tutto analogo ma $\lambda_j$ è il più grande $\lambda_i$. $\square$

Possiamo enunciare il teorema.

# Teorema
Sia $P$ un poliedro non vuoto. Le seguenti affermazioni sono equivalenti:
1. Il rango di $A$ è minore di $n$;
2. $P$ non ha vertici;
3. $P$ contiene una retta.
### Dim
**1** $\implies$ **2**
Un vertice è un punto dove sono attivi $n$ vincoli l.i, ma i vincoli attivi sono un sottoinsieme dei vincoli che definiscono il  poliedro, quind hanno rango sempre minore. $\square$
**2** $\implies$ **3**
Supponiamo che $P$ non abbia vertici, facciamo vedere che deve contenere una retta. Si giunge ad un assurdo, applicando il lemma precedente. Se infatti supponiamo che non contenga rette, possiamo applicare il lemma, e di volta in volta trovare punti in cui sono attivi sempre più vincoli una volta finiti i vincoli si arriva all'assurdo di avere più vincoli attivi dei vincoli totali del poliedro. $\square$
**3** $\implies$ **1**
Supponiamo che $P$ contenga una retta, ovvero un punto $\overline x \in P$ ed una direzione tale che la retta $R(\overline x, d) \in P$, quindi i punti della retta soddisfano:
$$
a_i^T(\overline x + \lambda d) \leq b_i, \qquad \forall \lambda
$$
$$
a_i^T\overline x + \lambda a_i^T d \leq b_i
$$
Se $(Ad)_i > 0$ mando $\lambda \to \infty$ ed esco dal poliedro, analogamente se $(Ad)_i < 0$ mando $\lambda \to -\infty$.  Segue che $Ad = 0$, ma se il sistema omogeno ha una soluzione non banale $d$, allora il rango della matrice $A$ è minore di $n$. $\square$