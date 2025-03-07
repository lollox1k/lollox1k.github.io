# Modello Curie-Weiss

E' la versione _mean-field_ del [[The Ising model]], che è risolvibile analiticamente solo per $d=1$ e $d=2$ con campo esterno $h=0$. L'approssimazione di campo medio fornisce risultati qualitativamente corretti per dimensioni abbastanza elevate (esatte per $d > 4$), nel caso $d=1$ sbaglia anche qualitativamente, mostrando una transizione di fase che nella soluzione esatta è assente.

## L'approssimazione mean-field

Partiamo dall'Hamiltoniana del modello di Ising in dimensione $d$, quindi un insieme di spin $\sigma = {-1,1}$ che vivono sul reticolo $\mathbb{Z}^d$. Ogni spin contribuisce all'energia totale del sistema interagendo con i suoi $2d$ primi vicini, con un termine:
$$
-\sum_{j \,:\,i \sim j} J\sigma_i\sigma_j = -2d\sigma_i \frac{1}{2d}\sum_{j \,:\,i \sim j} \sigma_j 
$$
dove abbiamo messo in evidenza lo spin $i$, e diviso e moltiplicato per il numero di vicini. Questa riscrittura mostra come lo spin $\sigma_i$ interagisca con un campo medio dei sui vicini, l'ipotesi (l'approssimazione) di campo medio consiste nel _sostituire a questa media sui vicini la media globale_:
$$
\frac{1}{2d} \sum_{j \,:\,i \sim j} \sigma_j \simeq \frac{1}{N} \sum_{j=1}^N \sigma_j =: m
$$
al crescere della dimensione, questa approssimazione diventa sempre migliore, nel limite infinito dimensionale è esatta. Possiamo immaginare gli spin posizionati su un grafo completo.
![[Pasted image 20221115132541.png]]

Con questa approssimazione abbiamo l'Hamiltoniana del modello di Curie-Weiss:
$$
\mathcal{H}^{CW}(\sigma) := -\frac{2dJ}{N}\sum_{i,j = 1}^N \sigma_i\sigma_j -h\sum_i \sigma_i
$$
rispetto al modello di Ising la sommatoria è su tutti le coppie $i,j$. 

## Misura di Gibbs

Sia $\Omega_N := \{-1,1\}^N$ lo spazio delle configurazioni. La misura di Gibbs su $\Omega_N$ è
$$
\mu^{CW}(\sigma) := \frac{e^{-\beta \mathcal{H}(\sigma)} }{Z^{CW} }
$$
Vogliamo mostrare come il modello sia paramagnetico ad alte temperaure e ferromagnetico a basse temperature.

## Campo esterno $h=0$

Il caso di campo esterno nullo $h=0$ rende _l'Hamiltoniana simmetrica_ per inversione $\sigma \mapsto -\sigma$. Questo implica che la densità di _magnetizzazione_ $m_N$ abbia una _distribuzione di probabilità simmetrica_, ovvero:
$$
\langle m \rangle^{CW} = 0
$$
ci aspettiamo che ad alte temperature gli spin siano praticamente indipendenti, e sotto una certa soglia critica allineati. 

### Teorema
Sia $h=0$, allora esiste una _temperatura critica_ $\beta_c := \frac{1}{2d}$ tale che:
1. Quando $\beta \leq \beta_c$ la magnetizzazione si concentra sullo zero: $\forall \epsilon > 0$ $\exists N$ tale che:
$$
\mu^{CW}(m_N \in (-\epsilon, \epsilon)) \geq 1-2e^{-cN}
$$
2. Quando $\beta > \beta_c$, la magnetizzazione è limitata dallo zero: esiste $m^*(\beta) > 0$ detta _magnetizzazione spontanea_, tale che per $\epsilon > 0$ abbastanza piccoli, esiste un $b(\epsilon, \beta) > 0$ tale che:
$$
\mu(m \in J) \geq 1-2e^{bN}
$$
dove $J$ è l'unione di due intervalli simmetrici centrati in $-m^*$ e $m^*$ di raggio $\epsilon$.

> - Quando $N$ è  grande, per ogni temperatura maggio uguale a quella critica $m_N \simeq 0$ con alta probabilità
> - Quando $N$ è grande, per ogni temperatura strettamente minore di quella critica $m_N \simeq \pm m^*(\beta)$ con probabilità vicina a $1/2$.

![[Pasted image 20221115134618.png]]

Nel limite $N\to\infty$ ho delle delta di Dirac.

In assenza di campo esterno, l'Hamiltoniana può essere riscritta in termini della magnetizzazzione media $M_N$ anzichè gli spin:
$$
M_N^2 = \left( \sum_{i=1}^N \sigma_i \right)^2 = \sum_{i,j=1}^N \sigma_i\sigma_j = N^2 m_N^2
$$

$$
\mathcal{H}^{CW} = -\frac{2dJ}{N}\sum_{i,j = 1}^N \sigma_i\sigma_j = -\frac{2dJ}{N}M_N^2 = -2dJNm_N^2
$$
Con un abuso di notazione ridefiniamo la costa di accoppiamento:
$$
J = 2dJ
$$
quindi abbiamo:
$$
\mathcal{H}^{CW}(m_N) = -JN m_N^2
$$
con $m_N \in [-1,1]$ e razionale del tipo $m = \frac{2k}{N}$ con $k = -\frac N2,\dots,\frac N2$.

Abbiamo quindi un [[Two state system]], con entropia per particella:
$$
s(m) = -\frac{\left(1-m\right)}{2}\ln\left(\frac{\left(1-m\right)}{2}\right) -\frac{\left(1+m\right)}{2}\ln\left(\frac{\left(1+m\right)}{2}\right)
$$

Calcoliamo la probabilità di osservare una magnetizzazione media $m$, con la misura di Gibbs:
$$
\mu^{CW}(m_N = m) = \frac{\binom{N}{N(m+1)/2} e^{\beta JNm_N^2 }}{Z^{CW}} 
$$
dove il coefficiente binomiale è un fattore di degenerazione, conta quante configurazione hanno una magnetizzazione media $m_N$.

Per la funzione di partizione $Z^{CW}$, siccome siamo interessati all'andamento asintotico $N\to\infty$, possiamo stimarla con il termine massimo della somma:
$$
\max_m\binom{N}{N\frac{m+1}{2}} e^{\beta JNm_N^2 }\leq Z^{CW} \leq (N+1) \max_m\binom{N}{N\frac{m+1}{2}} e^{\beta JNm_N^2 }
$$
l'esponenziale tende a far crescere $m$, mentre il coefficiente binomiale è massimo per $m=0$. Dobbiamo capire come si bilanciano i due contributi nell'ottimo. Possiamo usare la [[Formula di Stirling]] per approssimare il coefficiente binomiale, esattamente per come abbiamo fatto nel [[Two state system]], quindi asintoticamente si comporta come $e^{Ns(m)}$. 
$$
Z^{CW} \leq (N+1) e^{N \max_m\{ s(m) + \beta J m_N^2 \}}
$$
osservare che $e(m) = -J m_N^2$, riconosco l'energia libera:
$$
\beta f(m) := \beta e(m) -s(m)
$$
massimizzare l'esponente equivale a minimizzare l'energia libera. Il fattore $(N+1)$ che ho nell'upperbound è ininfluente quando passo al logaritmo e al limite termodiamico:
$$
\lim_{N\to\infty} \frac{-1}{\beta N}\log Z^{CW} = \min_m f(m)
$$
Quindi la probabilità di avere una magnetizzazione media $m$ sarà:
$$
\lim_{N\to\infty}-\frac{1}{\beta N}\log\mu^{CW}(m_N = m) = f(m)-\min_m f(m)
$$
e la probabilità che $m \in J \subseteq [-1,1]$ 
$$
\lim_{N\to\infty}-\frac{1}{\beta N}\log\mu^{CW}(m_N \in J) = \min_{m \in J} f(m)-\min_\hat m f(\hat m) = \min_{m \in J} I(m)
$$
possiamo risolvere il problema di minimizzazione derivando (la funzione è smooth)
$$
\frac{\partial I}{\partial m} = (-2 \beta J m + \frac{1}{2}\log(1 - m) - \frac{1}{2}\log(1 + m)) = 0
$$

$$
m = \tanh J\beta m \qquad J = 2dJ
$$
studiando graficamente le soluzioni di questa equazione noto transizioni di fase sotto una certa temperatura critica, che dipenderà anche dalla dimensione $d$.

## Campo esterno $h\neq 0$

Il campo esterno non complica le cose, infatti fattorizza nel calcolo della funzione di partizione. Cambia il punto di massimo, infatti dovrò ottimizzare:
$$
\max_m\{N[s(m)- \beta e(m) + hm]  \}
$$
che in termini dell'energia libera:
$$
\max_m\{N[-\beta f(m) + hm]  \} = -\beta N\min_m \{ f(m) - Thm\}
$$
la funzione potenziale sarà:
$$
\lim_{N\to\infty} \frac{-1}{\beta N}\log Z^{CW}_{h\neq 0} = \min_m \{f(m) - Thm\} =: \Psi(h)
$$
che non è altro che la _trasformata di Legendre dell'energia libera_ rispetto alla magnetizzazzione media, la _pressione_.

Studiamo il comportamento della magnetizzazzione media in funzione del campo esterno
Possiamo trovare il massimo di $hm-f(m)$ derivando, essendo una funzione smooth (analitica), ottenendo una nuova equazione di autoconsistenza
$$
m = \tanh[\beta Jm + h]
$$
che come prima ammette sempre almeno una soluzione. 
Nel caso $\beta > \beta_c$ i imiti destro e sinistro della magnetizzazzione $m(h)$ non coincidono, siamo nella fase _ferromagnetica_. Se invece $\beta \leq \beta_c$ entrambi i limiti fanno zero, siamo nella fase _paramagnetica_.

Studiamo ora la pressione, scrivendola con la magnetizzazzione in cui si ottiene il massimo, diventa
$$
\Psi(h) = hm^* -f(m^*)
$$
dove con $m^*$ abbiamo indicato la magnetizzazzione che massimizza l'argomento della trasformata di legender (dipenderà sia dal campo esterno che dalla temperatura). Derivando
$$
\frac{\partial \Psi(h)}{\partial h} = m^*
$$
i ragionamento di prima sulla magnetizzazzione media $m^*$ si ripetono qui con i limiti destro e sinistro della deriata della pressione, che diventa dunque non derivabile in $h=0$ quando $\beta > \beta_c$.

### Caratterizzazzione della transizione di fase

Studiando le soluzioni $m^*$ dell'equazione di autoconsistenza otteniamo i punti stazionari dell'energia libera. Gli stati di equilibrio saranno i minimi.

![[Pasted image 20230216190714.png]]

Osserviamo come l'energia libera sia simmetrica in assenza di campo esterno $h$. Sotto la temperatura critica appaiono due minimi (simmetrici), al di sopra l'unico minimo è quello di magnetizzazzione nulla.


La soglia critica $\beta_c$ si ottengono quando la derivata della tangente iperbolica diventa maggiore di uno:
$$
\beta 2dJ \geq 1 \implies \beta_c = \frac{1}{2dJ} 
$$
dipende quindi dalla dimensione del sistema $d$.

usando l'identità $|\tanh z| \leq |z|$ si vede facilmente che
$$
|m| \leq \beta J |m|
$$
quindi nel caso $\beta J < 1$ l'unica soluzione possibile è $m = 0$, ovvero _fase paramagnetica_.
