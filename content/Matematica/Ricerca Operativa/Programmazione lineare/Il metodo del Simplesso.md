# Metodo del simplesso
Riscrive il problema di PL in una forma equivalente e _comoda_, in cui i vertici, che sono fondamentali come conseguenza del [[Problemi di PL#Teorema fondamentale della PL| Teorema fondamentale della PL]], assumono una forma semplice.

## Def 
**forma standard**
$$
\min c^Tx
$$
$$
Ax=b
$$
$$
x \geq 0, b \geq 0
$$
è evidente che aggiungendo opportune variabili e moltiplicando per $-1$, ogni problema di PL può essere riscritto in questa forma. Vediamo ora la proprietà fondamentale, la forma che assumono i veritici.

### Teorema caratterizzazione dei vertici in forma standard
Sia $\overline x$ un punto appartenente al poliedro $P$ definito in forma standard, e $rango(A)=m$ (ovviamente $m<n$).
Allora $\overline x$ è un vertice di $P$ se e solo se le colonne di $A$ relative alle
componenti positive (non nulle) di $\overline x$ sono linearmente indipendenti.
> le uniche variabili che contano sono quelle positive

### Dim 
per dimostrare questo fatto, trasformiamo la forma canonica del poliedro nella forma solita, ed imponiamo la definizione di vertice, ovvero il rango dei vincoli attivi deve essere uguale ad $n$.
$$
Ax=b \quad\rightarrow \quad Ax \leq b, -Ax\leq -b
$$
supponiamo che le prime $r$ variabili siano strettamente positive, le restanti $n-r$ nulle. Questo significa che $r$ vincoli di non negatività sono attivi. Quindi la definizione di vertice solita è:
$$
rank\begin{pmatrix} A\\-A\\e_{r+1}^T\\\dots\\e_n^T\end{pmatrix}=n
$$
ma le righe di $A$ ed $-A$ sono ovviamente linearmenti dipendenti, rimuovendole non abbasso il rango complessivo. Riscrivo i vincoli di non negatività in forma più comoda:
$$
rango \begin{pmatrix}A\\0_{(n-r)\times r} \quad I_{(n-r)\times (n-r)}\end{pmatrix}
$$
dalla definzione di indipendenza lineare, essendo $n$ colonne:
$$
\begin{pmatrix}
a_i \dots a_r \quad a_{r+1} \dots a_n \\ 0_{(n-r)\times r} \quad I_{(n-r)\times n-r}
\end{pmatrix} \begin{pmatrix} y \\ z\end{pmatrix} = \begin{pmatrix} 0 \\ 0\end{pmatrix}
$$
implica che $(y,z) = 0$. Ma la particolare forma della matrice ci sta dicendo che $z=0$, quindi rimaniamo con la condizione:
$$
(a_i,\dots a_r)y = 0 \qquad \text{implica } y=0
$$
ovvero l'indipendenza lineare delle colonne della matrice $A$ che corrispondono alle componenti positive di $\overline x$. $\square$

### Corollario
Segue direttamente l'ultile colorrario che $x \in P$ è un vertice allora ha almeno $n-m$ componenti nulle (potrebbe averne di più!).
#### Dim 
Se ne avesse meno di $n-m$, non avrebbe abbastanza colonne linermente indipendenti (meno di $n$),  quindi per il teorema precedente non sarebbe un vertice.


## Def SBA
Un po' di definizioni.

Chiamo una _matrice di base_ una sottomatrice non singolare $B$ della matrice $A$, avendo supposto $rank(A)=m$ $B$ è una matrice $m\times m$.

Chiamo _soluzione di base ammissibile_ (SBA) il punto $\overline x \in \mathbb{R}^n$ tale che:
$$
\overline x = \begin{pmatrix}x_B\\x_N\end{pmatrix} \qquad x_B = B^{-1}b \geq 0, \quad  x_N = 0_{n-m}
$$
Che ha le proprietà:
1. è un punto ammissibile, ovvero $\overline x \in P$ (si verifica direttamente).
2. è un vertice.
Infatti le componenti positive hanno colonne l.i (sono un sottoinsieme delle colonne di $B$ che è non singolare), (notiamo inoltre che rispetta il corollario precedente).
Inoltre ad ogni vertice corrisponde una SBA.
Ogni vertice ha una _soluzione di base associata_. La costruisco partendo dalle $r \leq m$ componenti del vertice positive, posso aggiungere altre per creare la matrice $B$. Poi basta verificare che è in $P$.

> Abbiamo ottenuto la seguente caratterizzazione fondamentale:
$$
Vertici \iff SBA
$$
## Criterio di ottimalità
Data la divisione $x = \begin{pmatrix}x_B\\x_N\end{pmatrix}$ , la funzione obbiettivo può essere riscritta come:
$$
c^Tx = c_B^Tx_B + c_N^Tx_N
$$
ed i vincoli:
$$
Bx_B + Nx_N = b \qquad
x_B,x_N \geq 0
$$
possiamo scrivere $x_b$ in funzione di $x_N$ e $b$, infatti essendo $B$ non singolare:
$$
x_B = B^{-1}b - B^{-1}Nx_N
$$
sostituendo nella funzione obbiettivo:
$$
c^Tx = c^T_B(B^{-1}b - B^{-1}Nx_N) + c_N^Tx_N = c_B^TB^{-1}b +(c_N^T - c_B^TB^{-1}N)x_N = c_B^TB^{-1}b + \gamma^Tx_N 
$$
dove abbiamo definito il vettore dei _coefficienti di costo ridotti_ $\gamma^T$.

## Teorema criterio di ottimalità
Sia $\overline x$ una SBA. Se il vettore dei _coefficienti di costo ridotti è non negativo_, allora è una soluzione ottima.
### Dim 
Lo dimostriamo facendo vedere che:
$$
c^T \overline{x} \leq c^T x
$$
dove $x$ è una qualunque punto ammissibile.

Calcolare il valore della funzione obbiettivo nella SBA è facile, $x_N = 0_{n-m}$:
$$
c^T\overline x = c_B^Tx_B = c_BB^{-1}b
$$
ma la funzione obbiettivo in un qualunque punto ammissibile può essere scritta come:
$$
c^Tx = c_B^TB^{-1}b + \gamma^Tx_N
$$
per ipotesi $\gamma \geq 0$, e siccome anche $x_N \geq 0$ si ha che:
$$
c^Tx = c_B^TB^{-1}b + \gamma^Tx_N \geq c^T_BB^{-1}b = c^T\overline x \quad \square
$$

### Criterio di Illimitatezza

Sia $x$ una SBA e $\gamma_i < 0$, e la relativa colonna $(B^{-1}N)_i \leq 0$ ovvero tutta non positiva. Allora il problema è _illimitato inferiormente_.

### Dim 
costruttiva, troviamo delle SBA in cui la funzione obbiettivo è arbitrariamente piccola.
Partiamo dalla SBA per cui si verifica l'ipotesi, e da lì scappiamo verso una direzione.
$$
x(\rho) =\begin{pmatrix}x_B(\rho)\\x_N(\rho)\end{pmatrix} 
$$

con $x_N(\rho)= \rho e_i$
Facciamo vedere che:
1. $x(\rho)$ è ammissibile per ogni $\rho \geq 0$:
	- $x_N(\rho) \geq 0$ banalmente;
	- $x_B(\rho) = B^{-1}b -B^{-1}Nx_N(\rho) = B^{-1}b - \rho \gamma_i \geq 0$, ma per ipotesi essendo una SBA $B^{-1}b \geq 0$, inoltre per i segni è sempre vera.
2. la funzione obbiettivo è arbitrariamente piccola:
	 $$
	 c^Tx(\rho)= c^Tx_B + \rho\gamma_i^T
  $$
  che per $\rho \to \infty$ diventa arbitrariamente piccola. $\square$


## Costruzione di una nuova SBA
Supponiamo di avere una SBA e che i test di ottimalità ed illimitatezza siano entrambi falliti. Come scegliamo un'altra SBA (un altro vertice) in maniera _intelligente_? 

Come prima caso, la nuova SBA dovrà necessariamente avere una delle variabili fuori base $x_N$ positiva, infatti se ha le stesse variabili poste a zero, anche la parte in base dovrà essere uguale a prima, non abbiamo quindi una nuova SBA.

Nel metodo del simplesso si costruisce una nuova SBA portando una delle variabili fuori base ad un numero positivo: $x_N' = e_h \rho$  con $\rho > 0$ (in questo caso la variabile $h$). Affinchè sia ammissibile $x_B'$ dovrà assumere la forma:
$$
x_B' = B^{-1}b-B^{-1}Nx_N' = B^{-1}b-\rho (B^{-1}N)_h
$$
e affinché sia ammissibile $x_B' \geq 0$:
$$
B^{-1}b \geq \rho(B^{-1}N)_h
$$
questo è un sistema di disequazioni. Siccome $B^{-1}b$ è ammissibile, è maggiore di zero, quindi se $(B^{-1}N)_{hi} \leq 0$ la disugualianza è valida per ogni $\rho$. Gli unici vincoli su $\rho$ sono quindi nel caso sia positivo, in questo caso per soddisfare l'intero sistema, basta scegliere $\rho$ come il minimo tra i rapporti:
$$
\rho = \min_{\substack{i=1,\dots,m;\\ (B^{-1}N)_{hi}>0}} \left\{ \frac{(B^{-1}b)_i}{(B^{-1}N)_{hi}} \right\} = \frac{(B^{-1}b)_k}{(B^{-1}N)_{hk}}
$$
chiamiamo $k$ l'indice della variabile in base che il rapporto minimo. Abbiamo quindi ottenuto una nuova SBA, sapendo $\rho$ possiamo vedere che forma ha:
$$
x_N' = \frac{(B^{-1}b)_k}{(B^{-1}N)_{hk}} e_h \qquad x_B'= B^{-1}b - \frac{(B^{-1}b)_k}{(B^{-1}N)_{hk}}(B^{-1}N)_h
$$
che succede alla compoente $k$ di $x_B'$? Il denomiatore si semplifica e quindi: $(x_B)_k = 0$
Ricordando la caratterizzazione $SBA \iff Vertice$, la nuova SBA deve avere le colonne corrispondenti alle variabili positive linearmente indipendenti. Questo insieme è appena cambiato, come abbiamo appena fatto.  Dobbiamo far vedere che la colonna $A_{m+h}$ è linearmente indipendente cone la colonne $A_{1,\dots,m}\setminus A_k$. Basta far vedere che $A_{m+h}$ è una combinazione lineare delle colonne di $B = A_{1,\dots,m}$ e che il coefficiente relativo alla colonna uscente $A_k$ sia diverso da zero. Ma è questo propriò il caso, infatti:
$$
A_{m+h} = N_h = B(B^{-1}N)_h
$$
mettendo in chiaro ($B = A_{1,\dots,m}$):
$$
A_{m+h}= \sum_{i=1}^m (B^{-1}N)_{hi}A_i
$$
con $(B^{-1}N)_{hk} > 0$. Quindi è davvero una nuova SBA! $\square$

### Come scelgo h?
Quale variabile fuori base faccio entrare? Siccome voglio minimizzare la funzione, conviene limitarci a SBA in cui la funzione obbiettivo non aumenta. Ma è facile vedere che basta far entrare variabili a cui corrispondono coefficienti di costo ridotto non positivo! Basta ricordare il testi di ottimalità, infatti:
$$
c^Tx = c_B^TB^{-1}b + \gamma^Tx_N = c_B^TB^{-1}b - \gamma^T_h\rho \leq c_B^TB^{-1}b = c^T\overline x
$$
### Altro
- basi degeneri
- sistema artificiale

