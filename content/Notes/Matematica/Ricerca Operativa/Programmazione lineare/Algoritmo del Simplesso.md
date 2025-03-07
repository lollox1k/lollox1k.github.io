In questo capitolo viene descritto un algoritmo per la soluzione di problemi di
programmazione lineare, Proposto nel 1947 da G.B.Dantzig.
Il metodo del simplesso è certamente l’algoritmo di ottimizzazione più famoso e più utilizzato nelle applicazioni.

Per il [[Problemi di PL#Teorema fondamentale della PL|teorema fondamentale della PL]] sappiamo che se il poliedro non contiene rette, e non il poliedro non ha una direzione di recessione che si comporta male, allora almeno una soluzione ottima si trova su un vertice. 
Il metodo del simplesso è una ricerca smart sui vertici del poliedro. 
_Problema:_ i vertici sono tanti, possono esplodere in numero esponenziale.

## Forma Standard
Il simplesso lavoro con problemi nella forma:
$$
\min c^Tx
$$
$$
Ax = b
$$
$$
x \geq 0
$$
detta _forma standard_. Una conseguenza è che essendo contenuto nella parte positiva, non contiene può contenere rette.
E' facile vedere come un qualunque problema di PL può essere trasformato in questa forma:
- $Ax\leq b = Ax + u = b$ con $u\geq 0$, variabili di Slack o surplus (nel caso $\geq$),
- $x = x_+ - x_-$ con $x_+,x_- \geq 0$, per il problema di $x$ negativi. 

Il vantaggio della forma standard è che consente una  caratterizzazione comoda dei vertici, fondamentali per il metodo del simplesso:
### Teorema caratterizzazione dei vertici in forma standard
Sia $P$ un poliedro non vuoto e $rank(A)=m$ (ovviamente $m\leq n$). 
Un punto $\overline x \in P$ è un vertice _se e solo se_ le colonne di $A$ relative alle _componenti positive_ di $\overline x$ sono _linearmente indipendenti_.
### Dim 
Riscriviamo il poliedro in forma standard come:
$$
Ax \geq b
$$
$$
-Ax \geq -b
$$
$$
x \geq 0
$$
siccome $\overline x$ è ammissibile, soddisfa le prime due serie di disequazioni con l'uguale. Supponiamo s.p.g. che le prime $r$ variabili siano strettamente positive, le restanti $n-r$ nulle.
Ricordando la definzione di [[Poliedri#Vertici|vertici]] come un punto con $n$ vincoli attivi l.i, se $\overline x$ è un vertice allora il rango di:
$$
rank\begin{pmatrix} A \\ -A \\ e_{r+1}^T \\ \dots \\ e_n^T 
\end{pmatrix} = n
$$
Matrice che posso riscrivere, essendo tutto il blocco $-A$ l.dip da $A$:
$$
rango
\begin{pmatrix}
A \\ 0_{(n-r)\times r} I_{(n-r)\times n-r}
\end{pmatrix}

= rango\begin{pmatrix}
a_i \dots a_r \quad a_{r+1} \dots a_n \\ 0_{(n-r)\times r} \quad I_{(n-r)\times n-r}
\end{pmatrix}
= n
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
Segue direttamente l'ultile colorrario che $x \in P$ è un vertice allora ha almeno $n-m$ componenti nulle.

