E' un teorema/metodo di elimninazione per risolvere sistemi lineari di disequazioni:
$$
\begin{cases}
x_1 + 2x_2 + \dots + x_N \leq b_1\\
2x_1 - 4x_2 + \dots + x_N \leq b_2\\
\dots
\end{cases}
$$
In notazione compatta matriciale:
$$
Ax \leq b
$$
L'idea è eliminare una variabile alla volta fino ad arrivare ad un caso banale. Si eliminano le variabili effettuando _combinazioni coniche_ che generando un sistema di disequazioni implicate. 
#### Qualche definizione 
#### Poliedro 
l'insieme $P(A,b) \subseteq \mathbb{R}^n$ che risolve un sistema di disequazioni $Ax\leq b$ 
#### Disuguaglianze implicate 
La disequazioni $\alpha x \leq \beta$ è detta _implicata_ dal sistema di disequazioni $Ax\leq b$ se ogni $x \in P(A,b)$ soddisfa anche questa disequazione.  

Un sistema di disequazioni è detto _minimale_ se non contiene disuguaglianze implicate.

#### Combinazione conica
Combinazione lineare con coefficienti non negativi.
#### Teorema 
ogni disugualianza ottenuta come combinazione conica delle disugagliuanze in $Ax\leq b$ è una disuguaglianza implicata.
### Dim
banale, la cosa chiave è che una combinazione conica non "ribalta" il $\leq$, quindi posso sommarle.

#### Poliedro proiezione
Sia $P(A,b) \subseteq \mathbb{R}^n$. Il poliedro $P(A',b')\subseteq \mathbb{R}^{n-1}$ si dice _proiezione_ di $P(A,b)$ se $\forall x \in P'$ allora $\exists z$ tale che $(z,x) \in P$. Ovvero posso _estendere la soluzione_. Geometricamente $P'$ deve essere nella proiezione di $P$, tolta la dimensione di $z$.

### Teorema di Fourier-Motzkin
Partiamo da un poliedro $P$, scegliamo una variabile da eliminare $x_i$ con $i = 1,2\dots, n$. Generiamo un nuovo poliedro $P'$. Dividiamo le disequazioni di $P$ in 3 sottoinsiemi:
$$
Z = \{ i | a_{ir} = 0\} \quad P = \{i | a_{ir} > 0\} \quad N = \{i | a_{ir} < 0 \}
$$
E genero il nuvo sistema/poliedro aggiungendo:
- tutte le disequazioni in Z (dove non compare la variabile $x_r$)
- una disequazione per ogni elmeneto dell'insieme $P\times N$ (prodotto cartesiano)
Noto: tutte le disequazioni sono combinazioni coniche: è un poliedro implicato.
Ripeto fino ad arrivare all'insieme vuoto, oppure zero variabili, 


L'algoritmo è semplice, ma il numero di disequazione diventa molto grande, non è pratico da implementare per sistemi grandi. Assumiamo di avere $n$ variabili e $m$ disequazioni, e che gli insiemi $N$ e $P$ siano di cardinalità circa $m/2$. Allora dopo ogni step avremo un numero di disequazioni pari alla cardinalità del prodotto cartesiano $N\times P$ ovvero $\simeq m^2$ . Dovendo fare $n$ eliminazioni per ciascuna variabile alla fine otteniamo circa $m^{2n}$ disequazioni: cresce esponenzialmente (no buono).   

## Teorema 
Il sistema $A'x\leq b'$ definito come:
$$
\sum_{j=2}^n \left( \frac{a_{ij}}{a_{j1}}+\frac{a_{kj}}{|a_{k1}|} \right)x_j \leq  \frac{b_i}{a_{j1}}+\frac{b_k}{|a_{k1}|}, \quad \forall i \in P, \; \forall k \in N
$$
$$
\sum_{j=2}^n a_{ij}x_j \leq b_i \qquad \forall i \in Z
$$
è una proiezione del sistema $Ax\leq b$ dopo aver eliminato la variabile $x_1$.

### Dim 
Dobbiamo far vedere che $A'x\leq b'$ allora $\exists z$ tale che $A(x,z)\leq b$. 
Il primo verso è ovvio, infatti tutte le disequazioni nel nuovo sistema sono ottenute come conbinazione conica di quelle originarie, quindi è un sistema implicato.

Per dimostrare l'altro verso, scambiamo due termini:
$$
\sum_{j=2}^n \frac{a_{kj}}{|a_{k1}|}x_j - \frac{b_k}{|a_{k1}|} \leq \frac{b_i}{a_{j1}} -  \sum_{j=2}^n\frac{a_{ij}}{a_{j1}}x_j \qquad \forall i \in P, \; \forall k \in N
$$
quindi in particolare vale per massimi a sinistra e il minomo a destra, esiste quindi un elemento $x_1$ che si trova in mezzo, un _elemento separatore_. Questo elemento risolve il sistema originario, infatti:
$$
x_1 \leq \sum_{j=2}^n \frac{b_i}{a_{j1}} - \sum_{j=2}^n\frac{a_{ij}}{a_{j1}}x_j \qquad \forall i \in P
$$
$$
x_1 \geq \sum_{j=2}^n \frac{a_{kj}}{|a_{k1}|}x_j - \frac{b_k}{|a_{k1}|} \qquad \forall k \in N
$$
moltiplicando per il valore positivo $a_{1j}$ le disequazioni del gruppo $P$ si ottiene:
$$
a_{1j}x_1 + \sum_{j=2}^n a_{ij}x_j \leq b_i \qquad \forall i \in P
$$
moltiplicando per il valore positivo  $|a_{k1}|$ il gruppo $N$ si ottiene:
$$
a_{k1}x_1 + \sum_{j=2}^n a_{kj}x_j \leq b_k \qquad \forall k \in N
$$
quelle del gruppo $Z$ sono ovviamente soddisfatte, quindi $A(x_1,x)\leq b$. $\square$

> il sistema con meno variabili ha più equazioni, questo consente di essere una proiezione di quello di partenza!
