# Gas perfetto
E' il più semplice sistema studiato dalla meccanica statistica:
$N$ particelle identiche di massa $m$, che non interagiscono, in assenza di forze esterne.
L'Hamiltoniana è dunque l'energia cinetica:
$$
\mathcal{H} = \sum_{i=1}^N \frac{p_i^2}{2m}
$$
Questo modello spiega bene i _gas rarefatti_, ovvero quando le interazioni tra molecole sono trascurabili.

# Legge dei gas perfetti
$$
PV = k_BNT \qquad PV=nRT
$$
Originariamente è una legge empirica, uno dei meriti della meccanica statistica classica è proprio saperla ricavare.

## Dall'enseble microcanonico
Ricaviamola usando l'[[Ensemble microcanonico]].
$$
\Omega(U,V)= \iint_{q \in V^N\, p \in \mathbb{R}^{3N}} \frac{dqdp}{N!h^{3N}}\,  \delta\left( \sum_{i=1}^N \frac{p_i^2}{2m} - U\right) 
$$
L'integrale sulle posizioni restituisce il volume del sistema $V^N$. Per valutare la parte con la delta, la superficie ad energia fissata $U$, notiamo che geometricamente è una sfera $3N$ dimensionale di raggio $\sqrt{2mU}$, usando la formula [[Volume della palla n dimensionale]] si ottiene:
$$
\Omega(U,V)= \frac{V^N}{N!h^{3N}}\,\frac{(2\pi)^{3N/2}}{\Gamma(3N/2)}(2mU)^{(3N-1)/2}
$$
Usiamo la [[Formula di Stirling]] per approssimare la funzione Gamma e il fattoriale:
$$
\Gamma(3N/2) \sim (3N/2-1)^{(3N/2-1)}e^{-(3N/2-1)}\sqrt{2\pi (3N/2-1)}
$$
In realtà non ci serve il fattore $O(\sqrt{N})$, che scompare nel limite termodinamico $s = \frac{S}{N}$ con $N\to\infty$.

Per arrivare all'equazione di stato, basta calcolare l'entropia prendendo il logaritmo della funzione di partizione:
$$
S(U,V)= k_B \log \Omega(U,V)
$$
$$
= k_B\left( N\log V + \frac{3N}{2}\log 2\pi + \frac{3N-1}{2}\log 2mU -\left(\frac{3N}{2}-1\right)\log\left(\frac{3N}{2}-1\right) + \left( \frac{3N}{2}-1\right)\right)
$$
sempre perchè siamo interessati al limite $N\to\infty$ possiamo togliere i $-1$ di troppo.
$$
S(U,V) = Nk_B\left( \log  \frac{V}{N}\left(\frac{U}{N}\right)^{\frac{3}{2}}   + \frac{5}{2} + \frac{3}{2}\log \frac{6m\pi}{h^2}\right)
$$
la pressione è dunque:
$$
p = \frac{\partial S}{\partial V}T = Nk_B\frac{1}{V}T
$$
ovvero:
$$
pV = Nk_BT \qquad \square
$$
## Dall'ensemble canonico
$$
Z(\beta,V)= \int\frac{dpdq}{N!h^{3N}}\, e^{-\beta\sum_i^N \frac{p_i^2}{2m}} = \frac{V^N}{N!} \left(  \frac{2\pi \,m\,k_BT}{h^2}\right)^{3N/2}
$$
il fattore dovuto ai momenti, risultato di integrali gaussiani indipendenti, viene spesso riscritto definendo una quantità con le dimensioni di una lunghezza:
$$
\lambda := \sqrt{\frac{h^2}{2\pi \,m\,k_B T}}
$$
detta _lunghezza d'onda termica di de Broglie_ (scala per capire se si deve passare alla MS quantistica).

La funzione di partizione diventa:
$$
Z(\beta,V) = \frac{1}{N!} \left(\frac{V}{\lambda^3}\right)^N
$$
Ancora una volta approssimo il fattoriale con Stirling, e passo al logaritmo per trovare l'energia libera:
$$
F(\beta,V) = -Tk_B\log Z(\beta,V) = -Tk_BN\left( \log \frac{V}{\lambda^3} -\log N +1 \right)
$$
per ricavare l'equazione di stato calcolo la pressione:
$$
p = -\frac{\partial F}{\partial V} = Tk_BN\frac{1}{V} \implies pV = Nk_BT \quad \square
$$

### Commenti 
Notiamo che, come doveva essere, la termodinamica ricavata a partire dai due enseble coincide, almeno per il caso del gas perfetto (imponendo che si usi lo stesso valore per la costante di Boltzmann).

