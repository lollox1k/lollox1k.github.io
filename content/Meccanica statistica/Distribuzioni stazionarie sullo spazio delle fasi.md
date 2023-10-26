# Ensebles
Le [[Preliminari di Meccanica statistica classica|ipotesi di Boltzmann]], permettono di calcolare il valore  medio di osservabili _dimenticando_ la dinamica miscroscopica sottostante, effettuando una media sulla regione dello spazio delle fasi con energia compatibile.

In generale, senza assumere l'[[Preliminari di Meccanica statistica classica#Ipotesi Ergodica| ipotesi ergotica]], il valore medio di un'osservabile esiste e sarà uguale al valore medio sul ciclo che contiene lo stato inziale.

Per una descrizione quantitativa, introduciamo la definizione di _distribuzione stazionaria_.
### Def 
Una misura di probabilità $\mu$ è detta _distribuzione stazionaria_  rispetto alla mappa $S$ se è invariante:
$$
\mu(\Delta) = \mu(S\Delta)
$$
da qui segue che $\mu(\Delta) = \mu(S^k \Delta)$, ovvero è una "costante del moto".  Tuttavia questa costante _dipende dalla celletta iniziale_. Possiamo immaginare di dividere lo spazio delle cellette in diversi cicli $\mathcal{C}_i$. 
Se $S$ è ergodica, si ha un solo ciclo che copre tutte le cellette ad energia fissata,segue che $\mu = 1/N$ con $N$ numero delle cellette. Definiamo in maniera naturale una _misura ergodica._
### Def
Una misura di probabilità stazionaria $\mu$ sulle cellette è detta _ergodica_ se la mappa $S$ agisce come una permutazione ad un ciclo sulle cellette dove vale $\mu(\Delta) > 0$.

Possiamo "scomporre" ogni misura stazionaria in componenti ergodiche, una per ogni ciclo:
$$
\mu(\Delta) = \sum_i p_i\mu_i(\Delta) \qquad \sum_i p_i = 1
$$
con $p_i \geq 0$ e  le misura ergodiche $\mu_i$ sono definite:
$$
\mu_i(\Delta) = 
\begin{cases}
1/N_i \text{  se  } \Delta \in C_i \\
0 \text{ altrimenti }
\end{cases}
$$
i coefficienti $p_i$ sono interpretati come la _probabilità del ciclo i_.

Boltzmann fece l'ipotesi che:
>> Stati di equilibrio macroscopici $\iff$ distribuzioni stazionarie $\mu$

Boltzmann chiamo questi distribuzioni _monoedes_, il termine moderno è _Ensembles_, douto a Gibbs.

Il valore medio di un'osservabile data una distribuzione stazionaria, quindi uno stato di equilibrio è:
$$
\overline f = \sum_{\Delta} \mu(\Delta)f(\Delta)
$$
l'interpretazione è che $\mu(\Delta)$ è la _probabilità  che il sistema all'equilibrio sia nello stato microscopico_ $\Delta$, osservandolo "fotografandolo" ad un tempo random.

# Ortodicità
Sia $\mathcal{E}$ l'insieme di tutte le distribuzioni stazionarie sullo spazio delle cellette. Quali vanno bene per descrivere il mondo? Ovvero:
>> Quali distribuzioni stazionarie sono in accordo con il secondo principio della termodinamica?

Questo è noto come il _problema dell'ortodicità_.

Data $\mu \in \mathcal{E}$ si definiscono le quantità medie macroscopiche:
- $T(\mu) := \sum_{\Delta} \mu(\Delta) K(\Delta)$
- $\Phi(\mu) := \sum_{\Delta} \mu(\Delta) \Phi(\Delta)$
- $U(\mu) := T(\mu) + \Phi(\mu)$
- $P(\mu) := \sum_{\Delta} \mu(\Delta) P(\Delta)$
- $V := \int dq$
- $\rho(\mu)  = \frac{N}{V}$

Con $V$ il volume del sistema e $N$ il numero di particelle.

#### Domanda
Quando $\mu$ cambia in maniera infinitesima all'interno di $\mathcal{E}$, la variazione infinitesiama corrispondente delle quantità medie sopra definite $dU$, $dV$, soddisfano la relazione:
$$
\frac{dU + PdV}{T_{emp}} = \text{diff. esatto}
$$
dove è stata definita la temperatura come l'energia cinetica media:
$$
T_{emp} := \frac{T(\mu)}{N}
$$
tale relazione deve valere _almeno nel limite termodinamico_ $N$,$V$,$U$ $\to \infty$.

In sostanza il primo più secondo principio della termodinamica. 

Da qui si può integrare il differenziale esatto e definire l'entropia $S(\mu)$.

Se l'ipotesi precedente _distrib. stazionarie_ $\iff$ _stati di eq._ è corretta, tutte le distribuzioni ortodiche devono dare luogo alla stessa fisica macroscopica.

### Ensebles studiati
- [[Ensemble microcanonico]]
- [[Ensemble canonico]]
- [[Ensemble gran canonico]]