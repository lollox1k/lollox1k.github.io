# Cambio di prospettiva
La procedura che abbiamo adottato fino ad ora è stata di definire distribuzioni di probabilità per sistemi definiti in un volume finito $\Lambda$, per poi effettuare il _limite termodinamico_ tendendo ad un sistema infinito. Vorremmo cambiare strategia, e partire direttamente da una distribuzione definita su tutto lo spazio.

A volume infinito (es. $\Lambda = \mathbb{Z}^d$) l'hamiltoniana, quindi la funzione di partizione non sono puù definite. Occorre l'uso di tecniche più sofisticate per ottenere l'oggetto che vogliamo: _distribuzioni di proabilità su spazi infiniti_.

# Eventi e misure di probabilità
Dato un insieme finito, è facile definire una misura di probabilità, assegnando un valore su ogni elemento dell'insieme delle parti di $\Omega_\Lambda$. L'insieme delle misure di probabilità di un insieme finito viene spesso indicato con $\mathcal{M}_1(\Omega_\Lambda)$.

Assumiamo che $\Omega = \mathbb{Z}^d$. Sia $S \subset \Omega$, la mappa di proiezione canonica $\Pi_S \Omega \mapsto S$ è definita naturalmente come la restrizione su $S$:
$$
\Pi_S(\omega) = \omega_S
$$
Fissiamo un sottoinsieme finito $\Lambda \Subset \Omega$ e consideriamo l'_insieme degli eventi locali che dipendono solo da cosa succede in $\Lambda$_:
$$
\mathcal{C}(\Lambda) := \{\Pi^{-1}\Lambda(A) \,\vert\, A \in \mathcal{P}(\Omega_\Lambda)\}
$$
Ogni evento $C \in \mathcal{C}(\Lambda)$ è detto _cilindro_ con base in $\Lambda$.

Consideriamo ora un insieme $S \subset \Omega$, quindi _anche infinito_. Definiamo la collezzione di tutti i cilindri con base finita contenuta in $S$:
$$
\mathcal{C}(S) := \bigcup_{\Lambda \Subset S} \mathcal{C}(\Lambda)
$$
questo insieme, è ancora a cardinalità numerabile!

Non ci resta che creare la sigma algebra generata da questo insieme:
$$
\mathcal{F}(S) := \sigma(\mathcal{C}(S))
$$
passando alla sigma algebra, ottengo anche _eventi non locali_, merito della chiusura per unione numerabile!.

> Il teorema di estensione di Kolmogorov non è utile qui, perchè servono i marginali.

### Lemma
Una funzione $f : \Omega \mapsto \mathbb{R}$ è $\mathcal{F}(S)$ misurabile se e solo se è locale, ovvero esiste un $\Lambda \Subset \mathbb{Z}^d$ tale che:
$$
f(\omega) = f(\omega') \qquad \text{ quando }\qquad \omega_\Lambda = \omega'_\Lambda 
$$
Una conseguenza è che dipendendo solo da un _numero finito_ di siti, ha anche un _numero finito di valori_, si potrà quindi esprimere come una combinazione lineare finita di funzioni indicatrici dei cilindri.


# Condizioni DLR
Osservazione chiave di Dobrushin, Lanford e Ruelle: 
> Dare condizioni di compatibilità sulle probabilità condizionali invece che sui marginali

**Intuizione**
Consideriamo gli insiemi: $\Delta \subset \Lambda \Subset \mathbb{Z}^d$ ed una condizione di bordo $\eta \in \Omega$.
Essendo finito, possiamo definire la misura $\mu_{\Lambda,\beta,h}^\eta$. Sia $f$ una funzione locale che dipende solo dai valori dei siti in $\Delta$. Quindi il valore atteso $\langle f \rangle_\mu$ può essere calcolato fissando prima gli spin dentro $\Lambda \setminus \Delta$. Quindi di fatto posso vedere come nuove condizioni di bordo sulla misura definita nel volume $\Delta$.
$$
\langle f \rangle_{\Lambda,\beta,h}^\eta = \sum_{\omega_{\Lambda\setminus \Delta}} \langle f \mathbb{1_{\omega_{\Lambda\setminus\Delta} }}\rangle_{\Lambda,\beta,h}^\eta = \sum_{\omega_{\Lambda\setminus \Delta}} \langle f \rangle_{\Delta,\beta,h}^{\omega_{\Lambda\setminus\Delta}} \mu_{\Lambda,\beta,h}^\eta(\omega_{\Lambda\setminus\Delta \text{ fuori } \Delta}) = \langle \langle f \rangle_\Delta\rangle_{\Lambda,\beta,h}^\eta 
$$
questo deve valere per ogni funzione locale, per ogni sottinsieme $\Delta$. Formulato precisamente:

### Lemma
Per tutti $\Delta \subset \Lambda \Subset \mathbb{Z}^d$ e tutte le funzioni limitate e misurabili $f : \Omega \mapsto \mathbb{R}$,
$$
\langle f \rangle_{\Lambda,\beta,h}^\eta = \langle \langle f \rangle_\Delta^*\rangle_{\Lambda,\beta,h}^\eta  \qquad \forall \eta \in \Omega
$$
il simbolo $*$ indichiamo sta per ricordare che stiamo mediando appunto sulle condizioni di bordo!

### Proof
Indichiamo con $\omega \in \Omega_\Lambda^\eta$ uno stato della forma: $\omega = \omega_\Lambda \eta_{\Lambda^c}$, ovvero fissate i siti di bordo. 
$$
\langle \langle f\rangle_\Delta^*\rangle_\Lambda^\eta = \sum_{\omega_\Lambda} \langle f \rangle_\Delta^{\omega} \frac{e^{-\mathcal{H}_\Lambda(\omega)}}
{Z_\Lambda^\eta}$$
allo stesso modo
$$
\langle f \rangle_\Delta^{\omega_\Lambda \eta_{\Lambda^c}} = \sum_{\omega_\Delta} f(\omega) \frac{e^{-\mathcal{H}_\Lambda(\omega)}}
{Z_\Delta^{\omega_\Lambda \eta_{\Lambda^c}}}
$$
ecc.

In maniera naturale, richiedo che per una misura infinito dimensionale debba valere:
$$
\langle f \rangle = \langle \langle f\rangle^*_{\Delta}\rangle \qquad \forall \Delta \Subset \mathbb{Z}^d
$$
per tutte le funzioni locali $f$.
