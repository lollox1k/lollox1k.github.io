# Preliminari di Meccanica statistica classica
_Source:_ Short treatise G. Gallavotti (1999) 
- Obiettivo della MS classica;
- Idee chiave di Boltzmann: discretizzazione, ipotesi ergodica;
- Tempo di ricorrenza, osservabili macroscopiche;

## Introduzione 
Scopo della meccanica statistica classica: 
> Dedurre le proprietà macroscopiche della materia a partire dall'ipotesi atomica

$$
Micro \implies Macro
$$
Si vuole passare da una descrizione microscopica, ovvero un punto nello spazio delle fasi $6N$ dimensionale, a leggi per quantità macroscopiche medie.

### Descrizione a Grana Grossa
Per la meccanica classica posizione e momento sono numeri reali, lo stato assume _valori continui_. Per Boltzmann (molto prima della QM) tuttavia, il sistema doveva essere descritto _discretizzando lo spazio delle fasi_ in cellette di "piccola" dimensione. La giustificazione di ciò è operativa (dal sapore sperimentale): assumiamo di avere una precisione limitata nelle misurazioni, allora gli stati all'interno di una stessa celletta sono indistinguibili: _è una risoluzione massima_. La descrizione del continuo si recupera nel limite di precisione infinita.

Oggi sappiamo dal _principio di indeterminazione_ che questo limite di precisione è anche teorico:
$$
\delta p \delta q \geq h
$$
Descriviamo quindi lo stato del sistema con una celletta $\Delta$ di volume $h^{3N}$, e associamo a ciascuna celletta i momenti e posizioni che corrispondono al centro di essa.

### Come dipende la teoria da $h$?
In luce del principio di indeterminazione, è  naturale identificare $h$, il volume delle cellette $h^{3N}$, con la costante di Planck. Ma Boltzmann come ha potuto fissarla/studiarla?

Prima imponiamo delle richieste sulla nostra descrizione discreta in cellette.
### Dinamica microscopica discreta
Abbiamo discretizzato lo spazio delle fasi, discretizziamo anche la dinamica facendo lo stesso col tempo: introduciamo un intervallo temporale "piccolo" $\tau$. Come per la costante $h$, dobbiamo indagare che significa "piccolo".

Il sistema evolvendo passa da uno stato ad un altro, nel nostro caso da $\Delta \rightarrow \Delta'$. Ma se $\tau$ è troppo piccolo non riesce ad uscire dalla cella iniziale, se è troppo grande compie un salto.

Della dinamica microscopica classica sappiamo che:
1. è deterministica
2. invertibile
3. conservazione dell'energia

Quindi, sia $S$ una mappa che manda cellette in altre cellette (l'evoluzione temporale):
$$
S\Delta = \Delta'
$$
richiediamo che conservi l'energia meccanica e sia invertibile.
$$
E(\Delta) = K(\Delta) + \Phi(\Delta)
$$
dove
$$
K(\Delta) = \sum_i^N \frac{p_i^2}{2m_i}
$$

$$
\Phi(\Delta) = \sum_{i\leq j} \phi(q_i-q_j)
$$
ricordiamo che $\Delta \iff (q,p)$ sono i centri della celletta.

Risolvendo le equazioni di Hamilton otteniamo dopo un tempo $\tau$ un nuovo stato $(q',p')$, a cui facciamo corrispondere la celletta $\Delta'$.

_Questa discretizzazzione crea problemi_: non sempre vale l'unicità (il nuovo stato potrebbe capitare esattamente sul bordo di due celle) o due punti della stessa cella possono evolvere in cellette diverse, o l'inveritbilità: due punti in cellette diverse possono finire nella stessa cella:
$$
S\Delta_1 = S\Delta_2, \qquad \Delta_1 \neq \Delta_2
$$
Quello che possiamo fare è scegliere $\tau$ e $h$ in  maniera ottimale, rendendo questi eventi rari.

> Quando si fa integrazione numerica di equazioni differenziali si incorre negli stessi problemi!

Per avere l'unicità, richiediamo che il tempo sia "piccolo", ma non troppo da non muoversi. Nel limite al continuo $\lim_{h\to 0} \tau_{min} = 0$.

Imponiamo la distiguibilità. Approssimando l'eqazioni di Hamilton
$$
\delta q \geq \frac{\delta E}{\delta p} \tau \qquad h = \delta q \delta p \geq \max{\delta E} \tau
$$
la variazione deve essere più grande della celletta (Il max è su tutte le cellette).

Otteniamo la suggestiva:
$$
h = \delta t \delta E
$$
con $\delta t = \min{\tau}$ che soddisfa la condizione precente. 

Assumendo $\delta p = \overline p = \sqrt{3mk_BT}$ otteniamo:
$$
\tau \geq \frac{h}{k_BT}
$$
> Per temperature basse non funziona più, rompo la condizione di unicità e reversibilità.

Boltzmann fece le ipotesi:
$$
\delta p = \overline p = \sqrt{3mk_BT}
$$
$$
\delta q = (V/N)^{1/3}
$$
ottenendo un $h$ con ordine di grandezza comparabile alla costante di Planck.

>> Per basse temperature l'approssimazione non funziona più

## Ipotesi Ergodica
Per studiare l'evoluzione temporale di quantità che dipendono dallo stato microscopico, Boltzmann fece l'audace ipotesi che la mappa $S$ sia una _permutazione a un ciclo_ delle cellette compatibili con il vincolo di energia:
$$
S\Delta_k = \Delta_{k+1}, \qquad k = 1,2,\dots \mathcal{N}
$$
data un'appropriata enumerazione, e $\Delta_{\mathcal{N}+1} = \Delta_1$ (ciclo).

_Problema:_
E' palesemente falsa per molti sistemi! Infatti se esistono altre costanti del moto, non vale! Es. sistema in un contenitore sferico (le interazioni di bordo conservano il momento angolare totale). Oppure catena di oscillatori accoppiati.

Allora è naturale definire la nozione di _Distribuzione di probabilità ergodica_.
### Def 
Un *insieme di celle* dello spazio delle fasi è *ergodico* se è *chiuso rispetto la mappa $S$* e la sua azione è una permutazione ad un ciclo.

Quindi la versione non restrittiva dell'ipotesi ergodica diventa quella di studiare il moto dopo aver *fissato a priori tutte le quantità conservate*.

Questo è in generale un problema difficile, esistono infatti *quantità conservate non banali*(come il momento angolare totale), e ogni sistema va analizzato a se.

Nonostante ciò Boltzmann ritenne che questi sistemi sono l'eccezzione.

### Medie temporali
Sia $f(q,p)$ un'osservabile, è importante (praticamente l'unico dato accessibile) lo studio della sua media temporale:
$$
\overline f = \lim_{T\to\infty} \frac{1}{T} \int_0^T f(q(t),p(t))dt
$$
Nella nostra descrizione discreta a grana grossa:
$$
\overline f =  \lim_{T\to\infty} \frac{1}{T} \sum_{i=1}^{int(T/\tau)} f(S^i\Delta)\tau
$$
Assumendo l'ipotesi ergodica tutto diventa più semplice, essendo un ciclo scompare anche il limite:
$$
\overline f = \frac{1}{\mathcal{N}}\sum_{i=1}^{\mathcal{N}} f(S^i\Delta)
$$
_Media sullo spazio delle fasi_

Il prossimo passo, congetturato da Boltzmann ed utilizzato per i calcoli in meccanica statistica classica è che essendo $h$ piccolo, posso approssimare le somme con integrali:
$$
\overline f = \int_{J_E} f(q,p)dqdp \Big/ \int_{J_E} dqdp
$$
dove $J_E$ è una regione con energia $E \in [E, E-DE]$ con $DE << E$ incertezza macroscopica, ma più grande di quella microscopica $\delta E$.

> L'ipotesi ergodica ci ha "liberato" dalla dinamica microscopica 

## Oltre l'ipotesi ergodica
All'atto pratico è utile sapere quanto velocemente il limite della media temporale converge (non abbiamo tempo infinito).

Possiamo costruire mappe $S$ ed osservabili patologiche che oscillano fortemente ad ogni passo, pertando la media temporale converge molto lentamente, _dopo aver visitato tutto lo spazio_. Questo tempo, il _tempo di ricorrenza_ è tipicamente enorme.

Stimiamolo:
$$
t_R = \mathcal{N}\tau
$$
per $\tau$ scegliamo il limite inferiore calcolato prima:
$$
\tau = \frac{h}{k_B T}
$$
per stimare il numero di cellette con energia nell'intervallo $[E,E+\delta E]$ (chiamo $J$ la regione corrispondente dello spazio delle fasi) celle di dimensione $h$.
$$
\mathcal{N} = \frac{Vol(J)}{h^{3N}}
$$
$$
Vol(J) = V^N Vol(J_p) 
$$
Dove $J_p$ è un guscio sferico. Lo calcoliamo usando al formula per il [[Volume della palla n dimensionale]] (sto barando, ma il volume del guscio è praticamente uguale a quello della palla visto che $N >> 1$)
$$
Vol(J_p)=\frac{(2\pi)^{N/2}}{\Gamma(N/2+1)}\left(2mE\right)^{N/2}
$$
Siccome $N$ è grande possiamo usare [[Formula di Stirling]] per approssimare la funzione Gamma:
$$
\Gamma(N/2) \sim (N/2)^{(N/2)}e^{-(N/2)} (2\pi N/2)^{1/2}
$$



$$
t_R = \mathcal{N}\tau \simeq  \mathcal{N} \frac{h}{k_B T} \simeq \frac{h}{Nk_BT} \left( \frac{2\pi e^{5/3}}{3} \right)^{3N/2}
$$
Per una mole di idrogeno in condizioni standard risulta $10^{-14}\cdot 10^{10^{19}}$, per confronto l'età dell'universo è $\simeq 10^{17}$ secondi.

>> Il nostro lavoro e l'ipotesi ergodica sono da buttare?

Per riconciliare il tutto Boltzmann fece l'ulteriore ipotesi che per *osservabili interessanti*, quelle *macroscopiche*, sono praticamente costanti sulla superficie ad energia fissata ad eccezioni di una piccolissima frazione $\epsilon$ di cellette.

>> Le osservabili macroscopiche si comportano bene

Esempi di osserabili macro:
- Energia media
- Energia cinetica media
- Energia potenziale media
- Pressione
- Densità locale