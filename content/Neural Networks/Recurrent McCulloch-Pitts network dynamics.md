# Dinamica 
Possiamo introdurre una dinamica discreta tra stati di una rete di [[McCulloch-Pitts neuron]] $S(t)$:
$$
S_i(t+\Delta t) = \Theta\left(  \sum_{j=1}^N J_{ij} S_j(t) + U_i^*\right) 
$$
Si può pensare a $\Delta t$ come un tempo refrattario dei neuroni biologici.

Ci sono due maniera di realizzare questa dinamica:
- _Dinamica parallela_ Gli stati evolvono tutti insiemi;
- _Dinamica sequenziale_ Si sceglie un neurone $i$ e si aggiorna solo quello.


## Noiseless recurrent networks
Studiamo la dinamica nel caso $T=0$ noiseless per i casi
![[Pasted image 20221017125210.png]]
![[Pasted image 20221017125224.png]]

### Parallel dynamics
**Es 1**
Caso banale: $J_{ij} = 0$ e $h_i \neq 0$. La regola di update è banale, non dipende dallo stato precedente, dopo una iterazione tutto il sistema va nello stato finale:
$$
\sigma_i = sign(h_i)
$$
Il bacino di attrazione per questo stato punto fisso è tutto il dominio $\mathcal{D} = \{-1,1\}^N$.
**Es 2**
Supponiamo ora $J_{ij} = \frac{J}{N}$ e $h_i = 0$, ovvero interazioni simmetriche e campo esterno nullo.
Otteniamo la regola di update:
![[Pasted image 20221017125717.png]]
Notiamo come compare un'osservabile macroscopica, la _magnetizzazzione media_ (spin medio):
$$
m(t) := \frac{1}{N}\sum_{i=1}^N \sigma_i(t)
$$
Possiamo ottenere una formula di update per questa osservabile macroscopica sommando:
$$
m(t+1)=\frac{1}{N}\sum_{i=1}^N \sigma_i(t+1) = \frac{sign(J)}{N} \sum_{i=1}^N sign(m(t)) = sign(J)\cdot sign(m(t))
$$
Se $J > 0$, abbiamo una dinamica _imitatoria_: i neuroni tendono a fare quello che fanno gli altri. Partizioniamo le configurazioni in:
$$
\mathcal{D}^+ := \{\sigma \in \{-1,1 \}^N \,:\, m(\sigma) > 0 \} \quad \mathcal{D}^- := \{\sigma \in \{-1,1 \}^N \,:\, m(\sigma) < 0 \}
$$
(supponiamo di avere un numero dispari di neuroni, così non abbiamo il caso patologico $m = 0$).

Abbiamo punti fissi $\{-1,-1,\dots\}^N$ e $\{+1,\dots,+1\}^N$ che corrispondono a $m = -1$ e $m=1$.

Se $J < 0$ abbiamo un ciclo limite di periodo due tra stati $m=1$ ed $m=-1$.

**Es 3**
Caso $J_{ij} = \frac{J}{N}$ e $h_i = h \neq 0$.
La regola di update della magnetizzazzione media è:
![[Pasted image 20221017130924.png]]

Se il campo esterno $h$ è troppo forte, ovvero $\vert h\vert >\vert J\vert$ otteniamo una dinamica banale, come nel caso senza interazioni. 

Con $J > 0$ otteniamo sempre due punti fissi, ma con bacini d'attrazione non uguali e che dipendono dal rapporto $\frac{h}{J}$.

Con $J < 0$ otteniamo sempre un ciclo di periodo due, $\frac{h}{J}$ controlla quanto ci metto a raggiungere il ciclo.

### Sequential dynamics
Studiamo gli stati  limite tramite [[Funzioni di Lyapunov]].

**Proposizione**
Se abbiamo interazioni simmetriche $J_{ij} = J_{ji}$, ed autointerazioni non negative $J_{ii} \geq 0$, un campo esterno $h_i$ e noisless ($T=0$), allora
$$
L(\sigma) := -\frac{1}{2} \sum_{i,j} J_{ij}\sigma_i\sigma_J -\sum_i h_i\sigma_i
$$
è una _funzione di Lyapunov_ della dinamica sequenziale:
![[Pasted image 20221017131903.png]]

dove si estrae $i$ uniformemente in $[1,N]$.

Durante la dinamica la funzione evolve:
$$
\Delta L = L(\sigma(t+1))- L(\sigma(t)) = -2\left\vert \sum_{j=1}^N J_{ij}\sigma_j+h_i  \right\vert -2J_{ii} \leq 0
$$
Siccome $L(\sigma)$ è limitata inferiormente, ammette un minimo ed il sistema arriverà a queste configurazioni e si fermerà. (Richiediamo distanza di hamming $1$).

## Pattern retrival
Possiamo vedere questa abilità delle reti di "ricordare" informazioni $\sigma(\infty)$, dato un input iniziale $\sigma(0)$, sfruttando questa dinamica verso attrattori.

Basando sulla regola (principio) di Hebb:
> Neurons that fire together wire together 
> Neurons out of sync fail to link

Risulta ragionevole:
![[Pasted image 20221017134417.png]]
Si vede facilmente che possiamo memorizzare singoli pattern $\xi$ definendo le connessioni in accordo con la regola di Hebb. Aggiungere campo esterno complica le cose, valgono le stesse considerazioni fatte nella dinamica parallela caso $J$ simmetrico con campo esterno. Quindi la rete avrà punti fissi in $\xi$ e $-\xi$, a seconda di $\frac{h}{J}$.


Per più pattern, una scelta ragionevole è mediare:
![[Pasted image 20221017134756.png]]
Per semplificare la trattazzione assumiamo che i pattern siano ortogonali.

**Proposizione** La dinamica sequenziale applicata ad una rete con pesi dati dalla regola di Hebb e $h_1 = 0$, mostra $2K$ stati stazionari, che corrispondono ai pattern ed hai loro inversi.

**Dim** Scriviamo la funzione di Lyapunov:
$$
L(\sigma) = -\frac{1}{2}\sum_{ij} J_{ij} \sigma_i \sigma_j + -\sum_{i}\sigma_ih_i
$$
con la regola di Hebb e campi esterni nulli
$$
= \frac{1}{2N}\sum_{ij} (\delta_{ij}-1)\left[\sum_{\mu = 1}^K \xi_i^\mu\xi_j^\mu \right]\sigma_i \sigma_j 
$$
$$
= \frac{1}{2N}\sum_{ij}\left[\sum_{\mu = 1}^K \xi_i^\mu\xi_j^\mu \right]\sigma_i \sigma_j + \frac{1}{2}K
$$
notando che
$$
\left(\sum_{i=1}^N \xi_i^\mu \sigma_i\right)^2
= \sum_{ij} \xi_i^\mu\xi_j^\mu \sigma_i \sigma_j
$$
dunque
$$
L(\sigma) = -\frac{1}{2}\sum_{\mu=1}^K \left(\frac{1}{\sqrt{N}}\sum_{i=1}^N \xi_i^\mu \sigma_i\right)^2 + \frac{1}{2}K
$$

Il termine al quadrato non è altro che il prodotto scalare tra lo stato ed il pattern (normalizzato) $\xi_i$. Siccome abbiamo supposto per ipotesi che i pattern sono ortogonali, per massimizzare il prodotto scalare $\sigma$ deve avere la stessa direzione di $\xi$, ed in questo caso $\langle \xi, \sigma \rangle = \pm \Vert \sigma \Vert$ e zero per gli altri pattern, dunque:
$$
L(\sigma) \geq \frac{1}{2}K -\frac{1}{2}N
$$
ed il minimo si ottiene quando $\sigma = \pm \xi$.

**Osservazione** Non è vero che tutti i minimi sono pattern, esistono dei _minimi spuri_.
$$
\sigma_i = sgn(\xi_i^1 + \xi_i^2+ \dots)
$$

**Proposizione** Misture dispari dei pattern sono stati stazionari. Misture pari sono stati stazionario instabili. Sono minimi locali.

### Stocasticità
Introduciamo delle perturbazioni random sulla soglia di attivazione, sommando una variabile a media nulla:
$$
U_i^*(t) = U_i^* + \frac{1}{2}Tz_i(t)
$$
dove $\frac{1}{2}T$ è la deviazione standard, $z(t)$ una variabile a media nulla e varianza unitaria. Il parametro $T$ controlla dunque il grado di stocasticità (una temperatura).

Effettuiamo anche in cambio da $S_i = \{0,1\}$ a spin $\sigma_i = \{1,-1\}$.  La regola di update diventa:
$$
\sigma_i(t+\Delta t) = sign\left[ \varphi_i(t) + Tz_i(t) \right] \qquad \varphi_i(t) = \sum_{j=1}^N J_{ij}\sigma_j(t)+h_i 
$$
da qui si capisce il fattore $1/2$ aggiunto al rumore. La quantità $\varphi(t)$ viene detto _campo locale_.

La probabilità di trovare un neurone nello stato $\sigma_i = 1,-1$ al tempo $t+\Delta t$ è dunque una variabile aleatoria che dipende dalle v.a. $z_i(t)$ e dallo stato della rete $\sigma(t)$. Se supponiamo sia _simmetrico_:
$$
\mathbb{P}[\sigma_i(t+\Delta t)=1] = \mathbb{P}[\varphi_i(t) > -Tz_i(t)] = \int_{\varphi_i(t)/T}^\infty \mathbb{P}[z_i(t) = z]dz
$$
$$
\mathbb{P}[\sigma_i(t+\Delta t)= -1] = \mathbb{P}[\varphi_i(t) < -Tz_i(t)] = \int_{-\infty}^{-\varphi_i(t)/T} \mathbb{P}[z_i(t) = z]dz
$$
esprimento il tutto in funzione della cumulativa $g(x)$
$$
\mathbb{P}[\sigma_i(t+1)= \pm 1] = g(\pm \varphi_i(t)/T)
$$
Con $z_i(t) \sim N(0,1)$ la cumulativa è $erf(x)$; un'altra scelta simile è la tangente iperbolica:
$$
g(x) = \frac{1}{2}\left( 1+\tanh(x) \right) 
$$
a cui corrisponde un rumore distribuito come:
$$
\mathbb{P}[z_i(t)=x] = \frac{1}{2}\left( 1-\tanh^2(x) \right)  
$$

Per la dinamica parallela, supponendo le variabili indipendenti, la probabilità fattorizza e si ottiene:
$$
\mathbb{P}(\sigma(t+1)) = \prod_{i=1}^N \mathbb{P}(\sigma_i(t+1) = \pm 1) = \prod_{i=1}^N g(\sigma_i(t+1)\varphi_i(t)/T)
$$
### Noisy dynamics
Vogliamo studiare il comportamento della rete quando aggiungiamo del rumore nelle soglie di attivazione, come abbiamo precedentemente mostrato. A causa del rumore random, potremmo solo fare considerazioni di carattere probabilistico sul comportamento della rete. Siamo sempre interessati al comportamento limite $\sigma(\infty)$. 
E' chiaro che possiamo studiare lo stato limite tramite le [[catene di Markov]]. Sotto opportune ipotesi sulle interazioni, riusciamo a calcolare la distribuzione di equilibrio.

### Matrice di transizione della dinamica sequenziale

Abbiamo visto che una scelta sensata per la distribuzione del rumore, è quella con funzione di partizione
$$
g(x) = \frac{1}{2}\left( 1+\tanh(x) \right) \qquad
\mathbb{P}[\sigma_i(t+1)= \pm 1] = g(\pm \varphi_i(t)/T)
$$
essendo molto simile al rumore gaussiano, senza l'impiccio della $erf(x)$.
Vogliamo trovare la matrice di transizione $W$ di dimensione $2^N \times 2^N$.
Se assumiamo di scegliere in maniera uniforme lo spin $\sigma_i$ da aggiornare, affinchè due pattern $\sigma$ e $\sigma'$ abbiamo probabilità positiva devono essere necessariamente a distanza di Hamming uno:
$$
W(\sigma;\sigma') = \frac{1}{N} \sum_{i=1}^N 
\left[
\frac{1}{2}(1+\sigma_i\tanh{\beta \varphi_i(\sigma'))}\delta_{\sigma,\sigma'} +
\frac{1}{2}(1-\sigma_i\tanh{\beta \varphi_i(\sigma'))}\delta_{F_i\sigma,\sigma'}
\right]
$$
dove il primo termine della sommatoria considera il caso in cui il pattern rimane lo stesso, il secondo nel caso in cui lo spin $i$ cambia segno. 
Con $F_i\sigma$ intendiamo lo stato $\sigma'_j = \sigma_j$ quando $j\neq i$ e $\sigma'_i = -\sigma_i$.

Il processo di Markov associato a questa matrice di transizione è _ergodico_, ovvero indipendnetemente della distribuzione iniziale $p_0(\sigma)$ esiste un tempo finito $\tau$ tale che:
$$
p_t(\sigma) >0 \quad \forall t \geq \tau
$$
in maniera equivalente
$$
W^t(\sigma; \sigma') > 0 \quad \forall t \geq \tau
$$
è chiaro che nel nostro caso sequenziale $\tau = N$.

**Teorema** Processi di Markov ergodici hanno un'unica distribuzione stazionario $p_\infty$ alla quale convergono indipendentemente dalla distribuzione iniziale.
$$
p_\infty(\sigma) = \sum_{\sigma'}W(\sigma;\sigma')p_\infty(\sigma')
$$
Per calcolare esplicitamente la distribuzione stazionaria, aggiungiamo l'ipotesi di _dettaglio bilanciato_:
$$
W(\sigma;\sigma') p_\infty(\sigma') = W(\sigma';\sigma)p_\infty(\sigma) \quad \forall \sigma,\sigma'
$$

**Teorema** La dinamica sequenziale _senza autointerazioni_, e con _interazione simmetriche_ implica il dettaglio bilanciato. La distribuzione stazionaria di equilibrio è data da:
$$
p_\infty(\sigma) \propto e^{-\beta\mathcal{H}(\sigma)}
$$
$$
\mathcal{H}(\sigma) = -\frac{1}{2}\sum_{ij}^N J_{ij}\sigma_i\sigma_j - \sum_{i=1}^N h_i\sigma_i 
$$
che è proprio la [[Finite volume Gibbs distributions|distribuzione di Boltzmann-Gibbs]].

**Remark** L'hamiltoniana è proprio la funzione di Lyapunov del caso noisless, infatti nel limite $T\to 0$ la distribuzione stazionaria si picca intorno ai minimi di $\mathcal{H}$.

**Proof*** Siamo nelle ipotesi senza autointerazioni ed interazioni simmetriche:
$$
J_{ii} = 0  \qquad J_{ij} = J_{ji} \quad\forall ij
$$
facciamo vedere che questo vale se e solo se vale il bilancio dettagliato
$$
W(\sigma;\sigma') p_\infty(\sigma') = W(\sigma';\sigma)p_\infty(\sigma) \quad \forall \sigma,\sigma'
$$
Il caso $\sigma = \sigma'$ è triviale.
Resta il caso $F_i\sigma = \sigma'$. La condizione di DB diventa
$$
\frac{e^{-\beta F_i\sigma_i \varphi(F_i \sigma)}}{\cosh{\beta\varphi_i(F_i\sigma)}}p_\infty(F_i \sigma) = 
\frac{e^{-\beta \sigma_i \varphi(\sigma)}}{\cosh{\beta\varphi_i(\sigma)}}p_\infty(\sigma)
$$
Siccome siamo nell'ipotesi di no autointerazioni i campi locali:
$$
\varphi_i(F_i \sigma) = \varphi_i(\sigma)
$$
sono indipendenti dal valore di $\sigma_i$!

Resta da far vedere che
$$
e^{-\beta F_i\sigma_i\varphi_i(F_i\sigma)} p_\infty(F_i\sigma) = e^{-\beta \sigma_i\varphi_i(\sigma)}p_\infty(\sigma)
$$
Sfruttiamo il fatto che $\forall \sigma$ 
$$
p_\infty(\sigma) = \exp{ \beta\left( \sum_k h_k \sigma_k + \sum_{k\neq l} J_{kl}\sigma_k\sigma_l + K(\sigma) \right) }
$$
studiando all'esponente solo i termini che dipendono da $\sigma_i$ 
$$
\frac{1}{2}\sum_{k\neq i} \sigma_i(J_{ki}-J_{ik})\sigma_k + K(\sigma)
$$
DB vale se e solo se
$$
K(F_i\sigma) - K(\sigma) = \sigma_i \sum_{k\neq i} (J_{ki}-J_{ik})\sigma_k \qquad \forall \sigma,i
$$

