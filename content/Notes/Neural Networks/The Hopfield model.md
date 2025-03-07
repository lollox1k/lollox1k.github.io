# The Hopfield model

### Mattis model (1977)

Abbiamo studiato il comportamento termodinamico del [[Modello di Curie-Weiss]]. In particolare, sotto una certa temperatura critica, il modello arrivava ad uno stato di equilibrio con magnetizzazzione media $\pm 1$ (caso di campo esterno nullo). Di fatto il sistema  (visto come rete di neuroni McCulloch-Pitts con rumore) sta "ricordando" uno dei due stati a magnetizzazzione unitaria. E' facile riadattare le interazioni affinchè la rete converga ad un pattern arbitrario: 
sia $\xi$ un pattern, l'Hamiltoniana di Mattis
$$
\mathcal{H}^M(\sigma) := -\frac{1}{2N} \sum_{ij}^N \xi_i\xi_j \sigma_i \sigma_j = -\frac{N}{2}\hat m^2
$$
dove abbiamo introdotto la _magnetizzazzione di Mattis_ 
$$
\hat m := \sum_{i=1}^N \xi_i \sigma_i
$$
A livello matematico il modello è identico a quello di Curie-Weiss, ed al di sotto della temperatura critica il sistema ha come configurazione di equilibrio gli stati con $\hat m = \pm 1$, ovvero $\pm\xi$.

Notiamo che abbiamo usato la _regola di Hebb_ per definire le interazioni. 

### Low load
Studiamo il caso di numero di pattern finito, detto _basso carico_. Le interazioni sono definite in accordo con la regola di Hebb
$$
J_{ij} = \frac{1}{N}\sum_{\mu=1}^P \xi_i^\mu \xi_j^\mu
$$
e con pattern _Rademacher_.

L'hamiltoniana del sistema è
$$
\mathcal{H}(\sigma) = -\frac{1}{N} \sum_{i < j} \sum_\mu \xi_i^\mu\xi_j^\mu \sigma_i \sigma_j = -\frac{1}{2N} \sum_{ij} \sum_\mu \xi_i^\mu\xi_j^\mu \sigma_i \sigma_j + \frac{1}{2N}\sum_{i}\sum_\mu (\xi_i^\mu)^2\sigma_i^2
$$
$$
= -\frac{N}{2}\sum_\mu\hat m_\mu^2 + \frac{P}{2}
$$
ovviamente il termine costante è ininfluente nel limite termodinamico.
Calcoliamo la funzione di partizione dipendente da una specifica realizzazzione dei $P$ pattern rademacher.
$$
Z_{N,\beta, \xi} = \sum_\sigma \exp{\left(\frac{\beta}{2N} \sum_{i,j,\mu} \xi_j^\mu\xi_i^\mu \sigma_i\sigma_j\right)}
$$
un trucco per svolgere questo conto è introdurre una _densità degli stati_ continua
$$
Z = \int_{-\infty}^{+\infty} z(m)dm
$$
ovviamente siccome le magnetizzazzioni di mattis $m_\mu$ hanno solo alcuni valori razionali tra $-1$ ed $1$, dovremmo intrdurre delle delta, che rappresenteremo come la loro trasformata
$$
\delta(x-y) = \frac{1}{2\pi}\int e^{iz(x-y)}dz
$$
quindi
$$
Z_{N,\beta, \xi} = 
\sum_\sigma \int \left[ \Pi_{\mu=1}^P dm_\mu \delta(m_\mu - \frac{1}{N}\sum_i \xi_i^\mu \sigma_i) \right] \exp{\left(\frac{\beta N}{2}\sum_\mu m_\mu^2\right)}
$$
$$
= \frac{1}{2\pi}\sum_\sigma \iint \left[ \Pi_{\mu=1}^P dm_\mu d\hat m_\mu\exp{i\hat m_\mu(m_\mu - \frac{1}{N}\sum_i \xi_i^\mu \sigma_i)} \right] \exp{\left(\frac{\beta N}{2}\sum_\mu m_\mu^2\right)}
$$
$$
= \frac{1}{2\pi}\sum_\sigma \iint \left[ \Pi_{\mu=1}^P dm_\mu d\hat m_\mu \right]\exp{ \left[] \sum_\mu i\hat m_\mu(m_\mu - \frac{1}{N}\sum_i \xi_i^\mu \sigma_i) + \frac{\beta N}{2}\sum_\mu m_\mu^2 \right]}
$$
usando l'integrale di picco prima per l'integrale sulle $d\hat m_\mu$ e dopo sulle $dm_\mu$ i termini di ordine $N$ che sopravvivono dell'energia libera intensiva del limite termodinamico sono
$$
\langle f \rangle^Q = \min_m \left\{\frac{1}{2}\sum_\mu m_\mu^2 - \frac{1}{\beta}\mathbb{E} \log 2\cosh (\beta\sum_\mu m_\mu \xi_i^\mu) \right\}
$$
dove le magnetizzazzioni di mattis soddisfano l'equazione di autoconsistenza
$$
m_\mu = \mathbb{E} \sum_i\xi_i^\mu \tanh (\beta \sum_\nu m_\nu \xi^\nu)
$$
il valore atteso è su $\xi^\mu$ Rademacher.

Studiamo il caso di pattern puro, ovvero $m_1 \neq 0$ mentre tutte le altre magnetizzazzioni di mattis sono nulle. L'equazione di autoconsistenza diventa semplice da analizzare, infatti 
$$
m_1 =\tanh \beta m_1
$$
dove abbiamo soppresso $\xi$ date che la tangente iperbolica è dispari. Abbiamo ottenuto proprio l'equazione di autoconsistenza del [[Modello di Curie-Weiss]].

L'analisi della stabilità suegue direttamente da Curie-Weiss, avremo quindi una regione di _retrivial_ (fase ferromagnetifca) ed una caotica (paramagnetica).

Osservando che la derivata è proprio $\beta$, sappiamo che il valore critico $\beta_c = 1$. 

Si possono poi studiare gli stati detti _misture simmetriche_, ovvero il vettore delle magnetizzazzioni di mattis è $\mathbf{m} = m_n (1,1,1,\dots,0,0,\dots)$ non nullo per $n$ pattern, e con stesso valore di overlap.

Scrivendo in forma vettoriale le equazioni di autoconsistenza
$$
\mathbf{m} = \mathbb{E} \mathbf{\xi} \tanh( \beta \,\mathbf{\xi \cdot m})
$$
per ogni termine
$$
m_n = \frac{1}{n}\mathbb{E} \sum_{\mu=1}^n \xi^\mu \tanh (\beta m_n \sum_{\mu=1}^n \xi^\mu)
$$
definendo le somme parziali $z_n := \sum_{\mu=1}^n \xi^\mu$ 

Possiamo studiare analiticamente il caso noiseless $\beta \to \infty$ (la tangente iperbolica vale uno)
$$
m_n = \frac{1}{n}\mathbb{E} [|z_n|]
$$

La conclusione è che stati misti simmetrici dispari sono stabili (minimi dell'eneregia libera), mentre gli stati pari sono instabili (punti di sella).

![[Pasted image 20230218202654.png]]

Se la temperatura è abbastanza alta (ma sempre nella regione di retrival) gli stati misti diventano instabili (nice!) ma il recupero degli stati puri perde qualità ;(.

## Signal-to-noise analysis

Analisi euristica per stimare la stabilità dei pattern, vale sia per il caso a basso carico che alto.

Se vogliamo che uno dato pattern sia stabile (nella dinamica deterministica) deve valere
$$
\sigma_i(t+1) = sign(\varphi_i(\sigma(t))) = \sigma_i(t)
$$
Esplicitiamo il campo locale quando $\sigma = \xi^1$ 
$$
\xi_i^1\varphi_i(\xi^1) = \frac{1}{N} \sum_{j\neq i} \sum_\mu \xi_i^1\xi_i^\mu\xi_j^\mu \xi_j^1 > 0
$$
se devono avere lo stesso segno il prodotto deve essere maggiore di zero.
separando il termine $\mu =1$ 
$$
\xi_i^1\varphi_i(\xi^1) = \frac{N-1}{N}+\frac{1}{N} \sum_{j\neq i} \sum_{\mu=2}^P \xi_i^1\xi_i^\mu\xi_j^\mu \xi_j^1
$$
Nel limite termodinamico $N\to\infty$ il primo termine tende ad uno, e viene detto _termine di segnale_. Il restante è detto _termine di rumore_.
$$
\xi_i^1\varphi_i(\xi^1) = 1 + R
$$
assumendo indipendenti le $\xi$, il termine di rumore è composto da $\simeq N\times P$ termini $\pm 1$. Sempre per $N$ grandi sarà distribuito come una gaussiana di varianza $\sqrt{NP}$, dunque alla fine
$$
R \approx \sqrt{\frac{P}{N}}
$$
questa analisi rudimentale ci dice che se il numero di pattern cresce più lentamente rispetto ad $N$, tutti i pattern sono stabili (anche il rumore tende a zero).

Consideriamo una $3$-mistura simmetrica. $\sigma_i := sgn(\xi_i^1+ \xi_i^2 + \xi_i^3)$. Se calcoliamo la magnetizzazzione di mattis di uno dei tre stati con questa mistura
$$
m_\nu^{(3)} = \frac{1}{N} \sum_i^N sgn(\xi_i^1+ \xi_i^2 + \xi_i^3)\xi_i^\nu
$$
La media empirica ($N >>1$) converge al valore atteso
$$
= \mathbb{E}[sgn(\xi_i^1+ \xi_i^2 + \xi_i^3)\xi_i^\nu] = 0.5 \qquad \nu = 1,2,3
$$

mentre è nulla per $\nu >3$.

Controlliamo la stabilità
$$
\sigma_i^{(3)} \varphi_i(\sigma^{(3)}) = S + R
$$
$$
S = \sigma_i^{(3)}\sum_{\mu=1}^3 m_\nu^{(3)}\xi_i^\mu = 0.5sgn(\xi_i^1+\xi_i^2+\xi_i^3)(\xi_i^1+\xi_i^2+\xi_i^3) = 0.5 |\xi_i^1+\xi_i^2+\xi_i^3|
$$
$$
R = \frac{1}{N} \sum_{j=1}^N\sum_{\mu=4}^P \sigma_i^{(3)}\xi_i^\mu\xi_j^\mu \sigma_j^{(3)}
$$
per il termine di rumore vale la stessa analisi del caso puro, ho una somma di circa $NP$ termini $\pm 1$, dunque il termine di rumore è del tipo
$$
R\approx \sqrt{\frac{P}{N}}
$$

Analizziamo la stabilità dei pattern puri nel caso ad alto carico. E' chiaro che se $P = \alpha N$, il termine di rumore nel limite $N\to\infty$ converge ad una gaussiana non varianza non nulla:
$$
R \to N(0,\alpha)
$$
Quindi la probabilità che un sito sia stabile è la probabilità che
$$
\mathbb{P}(R > -1) 
$$
probabilità esprimibile in termine della cumulativa, ovvero la $erf(x)$.  Se assumiamo $\alpha <<1$ possiamo usare l'espressione approssimata ed ottenere
$$
\mathbb{P}(R > -1)  \approx 1- \sqrt{\frac{\alpha}{2\pi}}e^{-\frac{1}{2\alpha}}
$$
Affinchè lo stato sia stabile, tutti gli $N$ siti lo dovranno essere. Assumendo indipendenza la proabilità che uno stato puro sia stabile diventa
$$
\mathbb{P}(\xi \text{ stabile }) = \left(1- \sqrt{\frac{\alpha}{2\pi}}e^{-\frac{1}{2\alpha}}\right)^N \approx 1-N\sqrt{\frac{\alpha}{2\pi}}e^{-\frac{1}{2\alpha}} 
$$

l'evento complentare è la probabilità di avere degli errori, quindi il valore atteso di errori $N_{err}$ sarà
$$
N_{err} = N\sqrt{\frac{\alpha}{2\pi}}e^{-\frac{1}{2\alpha}} << 1
$$
vogliamo siano molto minori di uno. Possiamo risolvere per $\alpha$ ed ottenere
$$
P_c = \frac{N}{2\log N}
$$
se richiediamo la stabilità di tutti i pattern ($PN$ siti)
$$
P_c = \frac{N}{4\log N}
$$
notiamo che questi casi sono sempre in _basso carico_, ovvero $P/N \to 0$. 

## High load

