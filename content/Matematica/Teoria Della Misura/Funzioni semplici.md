Classe di partenza per defnire l' [[Lebesgue's integral]], in letteratura si trovano definizioni un po' diverse. Banalmente, una funzione semplice (unidimensionale) è una funzione $\phi : E \to [0,\infty]$  che assume un numero finito di valori non negativi(è costante a tratti). 
$$
C = \{ f(a) \quad | \quad a \in E\} \qquad |C| < \infty 
$$
Si può dunque rappresentare come combinazione lineare finita di funzioni caratteristiche di insiemi misurabili:
$$
\phi(x) = \sum_{n=1}^M c_n \chi_{E_n}(x)
$$
Richiedendo che le $c_n$ siano tutte distinte e gli insiemi $E_n$ disgiunti, la rappresentazione è unica. $E_n$ sono insiemi misurabili, infatti considerando le preimmagini dei valori che assume, (che sono misurabili per ipotesi), si ottiene la rappresentazione desiderata detta _canonica_:
$$
F_k := \{\omega \,| \,\phi(\omega)=c_k \} \qquad \phi(x) = \sum_{k=1}^N c_k \chi_{F_k}(x)
$$


Definisco in maniera ovvia l'integrale di una funzione semplice rispetto ad una misura $\mu$:
$$
\int_E \phi d\mu := \sum_{n=1}^M c_n \mu(E_n)
$$
Bisogna stare attendi, se la misura $\mu$ non è finita. Adottiamo la solita convenzione $0\cdot \infty = 0$. Oppure si può definire le funzioni semplici su un dominio finito per la misura, e poi generalizzare, come fanno Kolmogrov e Fomin.

Notiamo che la funzione di Dirichlet è una funzione semplice, se uso la misura di Lebesgue l'integrale è nullo:
$$
\int_{[0,1]} D(x) d\mu(x) = 0\cdot \mu([0,1]\setminus \mathbb{Q}) + 1\cdot \mu(\mathbb{Q}\cap [0,1]) = 0
$$
## Oss
L'integrale è indipendente dalla rappresentazione. Se consentiamo ai coefficienti $c_n$ di essere uguali, e gli insiemi non disgiunti, possiamo comunque dimostrare l'indipendenza del valore dell'integrale, mostrando che è uguale a quello calcolato con la rappresentazione canonica.
