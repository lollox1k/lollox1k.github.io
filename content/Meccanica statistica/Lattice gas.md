## Lattice Gas
Ipotesi: ogni sito può essere occupato o meno da una sola particella, quindi c'è l'ipotesi di _hard core_. Inoltre la forza è attrattiva, ed a coppia:

Chiamiamo $\Phi_2(i,j)$  con $K(i,j)$.
1. essendo **attrattiva** è negativa, la definiamo positiva: $-K(i,j) \leq 0$
2. a lungo raggio la forza decresce: $K(i,k) \to 0$ quando $\Vert i-j \Vert_\infty \to 0$.
3. **invariante per traslazioni**
$$
K(i,j) = K(i+a,j+a) \qquad \forall a \in \mathbb{Z}^d
$$
questo implica, traslando per l'opposto di uno dei due siti:
$$
K(i,j)=K(0,j-i) \implies K(i-j)
$$
ovvero che _è funzione della differenza_.

L'energia d'interazione totale è quindi:
$$
U = -\sum_{(i,j)\subset \Lambda} K(i,j)
$$
Costruiamo un tipico potenziale d'interazione.

Indichiamo il numero di occupazione della cella $i$ con $\eta_i$. Per l'ipotesi di prima, nel nostro modello sarà $\eta_i = 0,1$. E' _lo stato del sistema_.

L'energia del sistema sarà quella dovuta alle interazioni dei siti occupati:
$$
\mathcal{H}(\eta) := -\sum_{(i,j)\subset \Lambda} K(i,j)\eta_i\eta_j
$$

Aggiungiamo una richiesta sul potenziale d'interazione: che sia _sommabile_ che è equivalente a dire che l'interazione con una particella ed il resto del sistema è limitata:
$$
\sup_{i \in \mathbb{Z}^d} \left\{ \sum_{j\neq i} K(i,j)\right \} = \sum_{i \neq 0} K(0,i) = \kappa < \infty
$$
come conseguenza dell'invarianza per traslazioni. 
Il numero totale di particelle nella regione sarà:
$$
N(\Lambda) := \sum_{i \in \Lambda} \eta_i
$$
e la densità empirica
$$
\rho_\Lambda := \frac{N(\Lambda)}{|\Lambda|}
$$
Data l'Hamiltoniana, possiamo definire le distribuzioni Canonica e Gran canonica.

### Esistenza dell'energia libera 
Definiamo una sequenza di volumi finiti che converge a $\mathbb{Z}^d$.
Diciamo che $\Lambda_n \uparrow \mathbb{Z}^d$ se:
1. $\Lambda_n \subset \Lambda_{n+1}$
2. $\bigcup \Lambda_n = \mathbb{Z}^d$

Torna utile, per trascurare le condizioni di bordo, richiedere una cosa aggiuntiva:
$$
\lim_{n\to\infty} \frac{|\partial^{in} \Lambda_n|}{|\Lambda_n|}=0 \qquad \partial^{in}\Lambda := \{i \in \Lambda \,|\, \exists j \notin \Lambda \,\land\, i\sim j\}
$$
dove il bordo è alla solita maniera. Diciamo che $\Lambda_n \Uparrow \mathbb{Z}^d$ nel senso di _Van Hove_.

Una sequenza semplice che soddisfa tutti questi requisiti è quella dei cubi:
$$
B(n) = \{-n,\dots,n\}^d
$$

### Teorema
Sia $\Lambda_n \Uparrow \mathbb{Z}^d$ una sequenza nel senso di Van Hove. Sia $\rho \in [0,1]$ ed $N_n \in \mathbb{N}$ tale che $\frac{N_n}{|\Lambda_n|} \to \rho$.
Il limite
$$
\lim_{n\to\infty} f_{\Lambda_n;\beta}(\rho) = f_\beta(\rho)
$$
_esiste_, non dipende dalla scelta delle sequenza $\Lambda_n$ e $N_n$. Inoltre la convergenza è uniforme nei sottoinsiemi compatti di $(0,1)$ e $\rho \mapsto f_\beta(\rho)$ è convessa e continua.

#### Lemma convessità
Siano $\Lambda_1, \Lambda_2$ due sottoinsiemi disgiunti $\Lambda_1,\Lambda_2 \Subset \mathbb{Z}^d$. Se $N_1 \leq |\Lambda_1|$ e $N_2 \leq |\Lambda_2|$ Allora 
$$
Z_{\Lambda_1 \cup \Lambda_2;\, \beta;\, N_1+N_2} \geq Z_{\Lambda_1;\, \beta;\, N_1} + Z_{\Lambda_2;\, \beta;\, N_2}
$$
#### Proof
$$
\sum_{\eta} e^{\beta \sum_{(i,j) \subset \Lambda}K(i,j) }\frac{1}{N!}
$$
dove l'insieme delle configurazioni è della forma $\eta \in \{0,1\}^{\Lambda}$ con la condizione che $N = \sum \eta_i$.

E' evidente che limitandoci alle configurazioni $\eta'$ tali che hanno $N_1$ particelle in $\Lambda_1$ e $N_2$ in $\Lambda_2$. Ottengo una quantità inferiore (sto sommando su meno stati, sempre quantità positive).
Il fattore combinatorio diventa $\frac{N!}{N_1!N_2!}$.

Separiamo la somma nell'esponente:
$$
\sum_{\eta'}  e^{\beta \sum_{(i,j) \subset \Lambda_1}K(i,j) + \beta\sum_{(i,j) \subset \Lambda_2}K(i,j) + \sum_{i \in \Lambda_1\, j \in \Lambda_2} \beta K(i,j)}\frac{1}{N_1!N_2!}
$$
Essendo $K(i,j)\geq 0$ possiamo trascuare il termine di interazione tra le regioni e fattorizzare per ottenere il risultato. $\square$

#### Lemma "continuità"
Una sorta di continuità della funzione di partizione rispetto al numero di particelle (i.e. incrementando le particelle di uno la funzione non cambia troppo).

Sia $\Lambda \Subset \mathbb{Z}^d$ e $N \in \{0,1,\dots, |\Lambda|-1\}$. Allora:
$$
\frac{|\Lambda|-N}{N+1} Z_{\Lambda;\,\beta;\,N}\leq Z_{\Lambda;\,\beta;\, N+1} \leq e^{\beta\kappa} \frac{|\Lambda|-N}{N+1}Z_{\Lambda;\,\beta;\,N}
$$
#### Proof
Possiamo vedere le configurazioni con $N+1$ particelle come tutte quelle da $N$ particelle a cui poi aggiuniamo un'altra in un sito libero. 
$$
\frac{1}{(N+1)!} \sum_{\eta \in \{0,1\}^{\Lambda};\, N(\eta)=N+1} e^{-\beta \mathcal{H}_K(\eta)} = \frac{1}{N+1} \frac{1}{N!}\sum_{\eta \in \{0,1\}^{\Lambda};\, N(\eta)=N} \sum_{\eta' \geq \eta;\, N(\eta')=N+1}e^{-\beta \mathcal{H}_K(\eta')}
$$
è chiaro che $\mathcal{H}(\eta') \leq \mathcal{H}(\eta)$, inoltre vale:
$$
\mathcal{H}(\eta') = \mathcal{H}(\eta) - k
$$
dove $k$ è l'energia dovuta alla nuova particella con quelle già presenti in $\eta$.  Sicuramente vale $k \leq \kappa$, quindi
$$
\mathcal{H}(\eta') \geq \mathcal{H}(\eta) - \kappa
$$
Con queste disuguaglianze, e condiserando che ci sono $|\Lambda| - N$ termini nelle somma otteniamo il lemma. $\square$ 

## Proof del limite
1. **esistenza del limite per sequenze particolari di particelle**
Consideriamo la sequenza $N_n = \lceil\rho |\Lambda_n|\rceil$ (il ceil).
I casi limite $\rho = 0$ e $\rho = 1$ possono essere calcolati esplicitamente:
$$
f_\beta(0)=0 \qquad f_\beta(1)= -\frac{\kappa}{2}
$$
per i valori intermedi, scriviamo il lemma della continuità come:
$$
c^{-1} Z_{\Lambda;\, N} \leq Z_{\Lambda;\, N+1} \leq c Z_{\Lambda;\, N}
$$
per un qualche $c > 1$.
Sia $\rho \in (0,1)$. Per tutti i $\Lambda_1,\Lambda_2$ disgiunti e con $\Lambda_1 \cup \Lambda_2 = \Lambda$ abbiamo che $\lceil\rho |\Lambda|\rceil \geq \rho |\Lambda_1| + \rho|\Lambda_2| \geq\lceil\rho |\Lambda_1|\rceil + \lceil\rho | \Lambda_2|\rceil -2$, ovvero $N \geq N_1 + N_2 -2$.
Usando due volte verso il basso la precedente disequazione otteniamo:
$$
Z_{\Lambda;\,  \lceil \rho |\Lambda| \rceil } \geq c^{-2} Z_{\Lambda;\,  \lceil \rho |\Lambda| \rceil -2}
$$
adesso consideriamo due volumi disgiunti $\Lambda_1, \Lambda_2$ con un relativo numero di particelle $N_1 = \lceil\rho|\Lambda_1|\rceil$  e $N_2 = \lceil\rho|\Lambda_2|\rceil$.  Vale quindi:
$$
Z_{\Lambda;\, N } \geq c^{-2} Z_{\Lambda_1;\, N_1} Z_{\Lambda_2;\, N_2}
$$
di conseguenza, passando al logaritmo abbiamo una proprietà di subadditività della funzione:
$$
a(\Lambda) := -\log (c^{-2} Z_{\Lambda;\, \lceil \rho|\Lambda|\rceil})
$$
Inoltre, come conseguenza dell'invarianza per traslazione del potenziale di interazione $K$, è anche invariante per traslazione. Possiamo quindi applicare il teorema [[Limite di successioni subadditive]]:
$$
\lim_{n\to\infty} \frac{a(\Lambda_n)}{|\Lambda_n|} = \inf_n \frac{a(\Lambda_n)}{|\Lambda_n|} 
$$
quindi esiste l'energia libera, almeno per successioni di $N_n = \lceil\rho |\Lambda_n|\rceil$, e con $\Lambda_n$ parallelepipedi.

Una conseguenza dell'esistenza, è anche il seguente upper-bound, che segue dal fatto che il limite è pari all'inf:
$$
Z_{\Lambda,\lceil \rho |\Lambda| \rceil} \leq c^2 e^{-\beta f(\rho)|\Lambda|}
$$
2. **esistenza del limite per sequenze generiche di particelle**
Assumiamo ora di avere una generica sequenza $N_n$ tale che $\frac{N_n}{|\Lambda_n|} \to \rho$.
Facciamo vedere che l'errore che si commette è trascurabile nel limite. Applicando la disuguaglianza un numero necessario di volte $\vert N_n - \lceil \rho |\Lambda| \rceil \vert$:
$$
c^{-\vert N_n - \lceil \rho |\Lambda| \rceil \vert}Z_{\Lambda, \lceil \rho |\Lambda| \rceil} \leq Z_{\Lambda;\, N_n} \leq c^{\vert N_n - \lceil \rho |\Lambda| \rceil \vert} Z_{\Lambda, \lceil \rho |\Lambda| \rceil}
$$
siccome $N_n - \lceil \rho |\Lambda_n| \rceil \to 0$, il limite coincide con quello del caso precedente, questo conclude la dimostrazione. $\square$
3. **convergenza uniforme sui compatti di $(0,1)$**
Per dimostrare la convergenza uniforme sui compatti di $(0,1)$, sia  $I = [a,b] \subset (0,1)$ usiamo la disuguaglianza di continuità con densità in $I$
$$
\left\vert f_{\Lambda\,\beta} \left(\frac{N+1}{|\Lambda|}\right) - f_{\Lambda\,\beta} \left(\frac{N}{|\Lambda|}\right) \right\vert \leq \frac{1}{|\Lambda|} \sup_{\rho \in I}\left\{ \kappa + \beta \log\left(\frac{1-\rho}{\rho}\right)\right\}
$$
quindi possiamo effettuare un bound uniforme, che con la convergenza puntuale implica la convergenza uniforme, quindi continuità della funzione limite (vedi [[Teoremi sulla convergenza uniforme#Lipshitz continuità]]) .  $\square$

La convessità segue dalla quasi convessità e della continuità della funzione limite.  $\square$

## Ensemble Gran Canonico
Ora consentiamo al numero di paticelle $N$ di variare, la distribuzione di probabilità diventa:
$$
\nu_{\Lambda,\beta,\mu}(\eta) := \frac{\exp{-\beta[\mathcal{H}(\eta) - \mu N(\eta)]}}{\Theta_{\Lambda,\beta,\mu}}
$$
la funzione di partizione gran canonica:
$$
\Theta_{\Lambda,\beta,\mu} := \sum_{\eta \in \{0,1\}^{\Lambda}} \exp{-\beta[\mathcal{H}(\eta) - \mu N(\eta)]}
$$
fattorizzando e sommando su tutte le configurazioni $\eta$ con $N$ particelle otteniamo la seguente relazione con la funzione di partizione canonica:
$$
\Theta_{\Lambda,\beta,\mu} = \sum_{N=0}^{|\Lambda|} e^{\beta\mu N} Z_{\Lambda,\beta,N}
$$
Il relativo potenziale termodinamico (intensivo) è la _pressione_. A volume finito assume la forma:
$$
p_{\Lambda,\beta}(\mu) := \frac{1}{\beta |\Lambda|} \log \Theta_{\Lambda,\beta,\mu} \qquad  \mu \in \mathbb{R}
$$
Dalla definizione segue che:
$$
\frac{\partial p}{\partial \mu} = \frac{\langle N \rangle}{|\Lambda|}
$$
ovvero la densità media. Quindi il potenziale chimico ci permette di controllare il numero di particelle: valori negativi corrispondono ad una fase diluita, positivi grandi ad una fase liquida.

## Esistenza della pressione a volume infinito
### Teorema
Sia $\Lambda_n \Uparrow \mathbb{Z}^d$ una sequenza nel senso di Van Hove. Per ogni $\mu \in \mathbb{R}$  il limite
$$
\lim_{n\to\infty} p_{\Lambda_n,\,\beta}(\mu) = p_\beta(\mu)
$$
_esiste_ e non dipende dalla scelta delle sequenza $\Lambda_n$. $p(\mu)$ è convessa e continua.

### Osservazioni
- Siccome $p_\beta(\mu)$ è convessa, la sua derivata:
$$
\rho_\beta(\mu) := \frac{\partial p}{\partial\mu}
$$
ovvero la densità media, _esiste quasi ovunque_.  Le derivate destre e sinistre $\rho^+$ e $\rho^-$ sono sempre ben definite. Questo permette di scambiare i limite per concludere che se esiste:
$$
\rho_\beta(\mu) = \lim_{n\to\infty} \frac{\langle N_{\Lambda_n} \rangle}{|\Lambda_n|}
$$
- $p(\mu)$ è _strettamente convessa_, ovvero un aumendo di $\mu$ provoca sempre un aumento di densità, infatti derivando:
$$
\frac{\partial^2 p}{\partial \mu^2} = \frac{\beta}{|\Lambda|}Var(N)
$$
Si può dimostrare che $Var(N) > 0$, il che implica la stretta convessità.

Per dimostrare l'esistenza del limite, passiamo per l'_equivalenza degli ensemble_: La pressione è la trasformata di Legendre dell'energia libera, $\mu$ è la variabile coniugata di $N$.

## Equivalenza degli ensemble
Equivalence of ensembles at the level of potentials holds for the general lattice gas. That is, the free energy and pressure are each other’s Legendre transform:
$$
f_\beta(\rho) = \sup_{\mu \in \mathbb{R}} \{\mu\rho - p_\beta(\mu)\} \qquad \forall \rho \in [0,1]
$$
$$
p_\beta(\mu) = \sup_{\rho \in [0,1]} \{ \rho\mu - f_\beta(\rho)\} \qquad \forall \mu \in \mathbb{R}
$$
### Dim 
Siccome i termini della somma che definiscono il gran potenziale sono non negativi:
$$
\max_N \{e^{\beta\mu N}Z_{\Lambda_n,\beta,N}  \} \leq \sum_{N=0}^{|\Lambda_n|} e^{\beta\mu N}Z_{\Lambda_n,\beta,N} \leq (|\Lambda_n| +1) \max_N \{e^{\beta\mu N}Z_{\Lambda_n,\beta,N}
$$
Possiamo usare l'upper bound calcolato per l'esisteza dell'energia libera:
$$
Z_{\Lambda,\lceil \rho |\Lambda| \rceil} \leq c^2 e^{-\beta f(\rho)|\Lambda|}
$$
$$
Z_{\Lambda_n,\beta,N} \leq c^2 \exp\{ -\beta[f(\rho)|\Lambda_n| + \mu N] \} \leq \sup_\rho c^2 \exp\{ -\beta[f(\rho) + \mu \rho]|\Lambda_n| \}
$$
quindi per il $\limsup$ vale:
$$
\limsup_{n\to\infty} \frac{1}{\beta|\Lambda_n|} \log \Theta \leq \frac{1}{\beta|\Lambda_n|} \left(\log c^2 -\beta \sup_\rho \{ f(\rho)-\mu\rho\}|\Lambda_n|\right) 
$$


# Gas di sfere dure
Poniamoci nel semplice caso $K(i,j) = 0$, ovvero manteniamo solo la parte hard-core del gas.
In questo semplice modello i potenziali termodinamici possono essere calcoalti esplicitamente.

The canonical partition function becomes a _purely combinatorial quantity_, counting the configurations $\eta$ con $N_\Lambda(\eta) = N$:
$$
Z_{\Lambda,\beta,N} = \binom{|\Lambda|}{N} 
$$
l'**energia libera** a volume infinito può essere calacolata approssimando con stirling i fattoriali:
$$
f_\beta(\rho) = \frac{1}{\beta}\left( \rho \log \rho + (1-\rho)\log(1-\rho) \right)
$$
![[Pasted image 20220912125146.png]]

La **pressione** si può ricavare dalla definizione usando il binomio di Newton:
$$
\Theta = \sum_{N=0}^{|\Lambda|} e^{\beta\mu N} \binom{|\Lambda|}{N} = (1+e^{\beta\mu })^{|\Lambda|} 
$$
quindi:
$$
p(\mu) = \frac{1}{\beta} \log (1+e^{\beta \mu})
$$


da qui derivando posso calcolare la densità media:
$$
\rho(\mu) = \frac{e^{\beta\mu}}{1+e^{\beta\mu}} \implies \mu = \frac{1}{\beta}\log\frac{p}{1-p}
$$
Questa espressione è invertivile, quindi posso scrivere il potenziale chimico in funzione della densità per ottenere un'equazione di stato:

$$
p = \frac{1}{\beta} \log (1 + \frac{p}{1-p}) = \frac{1}{\beta} \log (\frac{1}{1-p}) =- \frac{1}{\beta} \log(1-p) 
$$
a basse densità $\log (1-\rho) \simeq -\rho$
$$
p = \frac{\rho}{\beta} \implies p = k_B T \rho \implies pv = k_B T
$$
con $v = \rho^{-1} = V/N$. Ovvero l'equazione di stato dei gas perfetti.



