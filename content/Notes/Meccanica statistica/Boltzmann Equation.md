# Equazione di Boltzmann
Descrive l'evoluzione temporale della densità di probabilità degli stati di una particella, partendo da interazioni binarie istantanee (per il gas di Maxwell gli urti)
$$
\partial_t f(t,x,v) + v\cdot \nabla_x f(t,x,v) = Q[f](v)
$$
Il termine con la velocità è detto termine diffusivo: senza l'operatore collisionale $Q[f]$ l'equazione si riduce all' [[Equazione del trasporto]].

L'operatore collisionale è di forma integrale, nel caso di interazioni binarie è quadratico in $f$ (con interazioni con ostacoli fissi risulta lineare, caso [[Equazione di Lorenz]]). 
$$
Q[f](v)= \int_{\mathbb{R}^3}\int_{S^2} k(|v-w|,\omega)[f(v')f(w')-f(v)f(w)]d\omega\, dw
$$
Un integrale sulle velocità e sulle direzioni. Con l'apice sono indicate le velocità post collisione delle particelle che interagiscono.

Interpretazione: si può vedere come due parti:
1. quella di sinistra (a volte indicaga con $Q_+[f]$) essendo positiva rappresenta l'incremento della probabilità di avere delle particelle con velocità $v'$ e $w'$;
2. quello di destra col meno è la rispettiva perdita, abbiamo perso due particelle con $v$ e $w$.
3. il termine $k$ è detto _kernel d'interazione_, che può essere scomposto in una sezione d'urto differenziale per un fattore.

# Quantità conservate
Usiamo sempre l'ipotesi che:
$$
\lim_{|x|\to\infty}f(t,x,v) = 0
$$
Del tutto ragionevole visto che vogliamo considerare una distribuzione di probabilità, quindi in $L^1$.

Sia $\phi(v)$ una funzione, associamo ad essa il suo valore atteso, che sarà una funzione del tempo:
$$
q(t):= \mathbb{E}_f[\phi] = \int \phi(v)f(t,x,v)dvdx
$$
Stiamo integrando su $\mathbb{R}^3\times \mathbb{R}^3$.
viene detta _quantità conservata_ se è costante nel tempo.

Ma sappiamo calcolare la derivata grazie all'eq. di Boltzmann:
$$
q'(t)= \frac{d}{dt}\int \phi(v)f(t,x,v)dxdv = \int \phi(v)\partial_t f(t,x,v)dxdv
$$
$$
= \int \phi(v)[-v \cdot \nabla_x f(t,x,v)]dxdv + \int \phi(v) Q[f](v)dxdv
$$
valutiamo il primo addendo, è la somma di 3 termini:
$$
\int \phi(v) v_1 \partial_xf dxdv = \int \phi(v)v_1dv [f(t,x,v)]\vert_{-\infty}^{+\infty} = 0
$$
per l'ipotesi precedente.

Quindi _conta solo l'integrale con l'operatore collisionale_.

### Def invariante collisionale
Diciamo che la funzione $\phi(v)$ è un _invariante collisionale_ se:
$$
\int \phi(v)Q[f]dv = 0
$$
per ogni $f$ distribuzione di probabilità.

### Lemma
Se per ogni $v,w \in \mathbb{R}^3$ si ha (quasi ovunque):
$$
\phi(v)+\phi(w)=\phi(v')+\phi(w')
$$
allora $\phi(v)$ è un invariante collisionale.

> banalmente se si conserva dopo le collisioni, rimane costante.

### Dim 
Applico la definizione, qualche cambio di variabile e simmetria del kernel d'interazione.
$$
\int \phi(v)Q[f]dv = \int\int\int \phi(v) k(v\to v'|w')[f(v')f(w')-f(v)f(w)]dv\,dw\,dS
$$
effettuo un cambio di variabili: $v \to w$, $w \to v$ , ovviamente il modulo dello Jacobbiano è 1
$$
\iiint \phi(w)k(w\to v'|w')[f(v')f(w')-f(w)f(v)]dv\,dw\,dS
$$
Il kernel d'interazione è invariante per questo scambio! (per maxwell gas $k =\Vert v-w\Vert$ ), quindi ho la stessa espressione ma con $\phi(w)$.

Ora effettuo lo scambio $v \to v'$, $w \to w'$, qui richiedo che sia Jacobbiano unitario, nel caso di Maxwell e Lorentz si fa vedere facilmente che è così.
$$
\iiint \phi(v)k(v\to v'|w')[f(w')f(v')-f(v)f(w)]dv'\,dw'\,dS
$$
ora dobbiamo esprimere $v,w$ in funzione di $v',w'$.  Segue dalla simmetria delle interazioni che rinominando le varibli di integrazioni, si ottiene:
$$
-\iiint \phi(v')k(v\to v'|w')[f(v')f(w')-f(v)f(w)]dv\,dw\,dS
$$
da questa cambio $v\to w$, quindi $v'\to w'$ ed ottengo:
$$
-\iiint \phi(w')k(v \to v'|w')[f(v')f(w')-f(v)f(w)]dv\,dw\,dS
$$
(il modulo dello Jacobbiano è sempre uno).

Sommo le 4 espressioni quivalenti e divido per 4, raccolgo:
$$
\iiint \left[ \phi(v)+\phi(w) - \phi(v')-\phi(w') \right]\left[ f(v')f(w')-f(v)f(w)\right] dv\,dw\,dS
$$
$\square$

### Corollario
Se consideriamo sfere dure, allora ogni invariante collisionale continuo è della forma:
$$
\phi(v) = a + b\cdot v + c\Vert v \Vert^2, \qquad a,b,c \in \mathbb{R} 
$$
### Dim 
Siccome valgono conservazione del momento e dell'energia, la somma $\phi(v) + \phi(w)$ deve dipendere solo dalle quantità conservate:
$$
\phi(v)+\phi(w)= \Phi(v+w, v^2+w^2)
$$
ora introduciamo nuove funzioni:
$$
\phi_{\pm}(v) = \phi(v) \pm \phi(-v) 
$$
notiamo come sia una funzione pari!
e analogamente:
$$
\Phi_{\pm}(v+w, v^2+w^2) = \Phi(v+w, v^2+w^2) \pm \Phi(-v-w, v^2+w^2)
$$

giocherellando si ottiene:
$$
\phi_{\pm}(v) + \phi_{\pm}(w) = \Phi_{\pm}(v+w, v^2+w^2)
$$
sfruttando la parià di $\phi_{\pm}$ si ottiene:
$$
2\phi_+(v)=\Phi_+(2v^2,0)
$$
_è funzione solo del quadrato_. Quindi anche $\phi_+$ è solo funzione del quadrato!
Riscrivendo:
$$
\psi(v^2)+\psi(v^2)= \Phi_+(v^2+w^2)= \psi(v^2+w^2)+\psi(0)
$$
quindi è lineare, richiedendo la continuità è della forma:
$$
\psi(v)= cv^2+a
$$
Consideriamo due vettori ortogonali, allora la per la parte negativa:
$$
\phi_-(v)+\phi_-(w)= \Phi_-(v+w,0)= \phi_-(v+w)
$$
l'ultima segue da $\phi_-(0)=0$

Dati due vettori arbitrari, sia $\rho$ ortogonale ad tutti e due, allora se applica l'eq precedente...

Si conclude con $\phi(v)= (\phi_+ \phi_-)/2$       $\square$


# Equilibrio
Una distribuzione $f$ è detta di _equilibrio_ se:
$$
Q[f,f]dv=0
$$
### Proposizione
Una distribuzione è di equilibrio se è l'esponenziale di un invariante collisionale della forma $\phi(v)+\phi(w)= \phi(v')+\phi(w')$

### Dim 
Dalla definzione di operatore collisionale, se $f(v)f(w)=f(v')f(w')$ allora è un equilibrio.
Passando ai logaritmi:
$$
\log f(v) + \log f(w) = \log f(v')+\log f(w')
$$
ovvero se $\log{f}$ è un'invariante collisionale della forma espressa sopra. $\square$ 

### Oss
Ovviamente vale per combinazioni lineari di invarianti collisionali.

## La Maxwelliana
$$
f(v)= \mathcal{M}_{\rho,u,T}(v)=\frac{\rho}{(2\pi T)^{3/2}}e^{-\frac{\Vert v-u\Vert^2}{2T}}
$$

# Teorema H
Sia $f(t,v,x)$ una funzione sufficientemente smooth e zero all'infinito, ed una soluzione dell'equazione di Boltzmann. Allora la quantita:
$$
H(t) := \int f\log{f} dvdt
$$
detta _Entropia_ (c'è il segno menoooo) decande in tempo ed è zero se e solo se $f$ è una maxwelliana.

### Oss
$\log{f}$ è un invariante collisionale quando $f=\mathcal{M}$, quindi $\mathcal{M}$ è un equilibrio. (E' exp di combinazione lin di invarianti....).

## Dim
Uso le stesse simmetrie/anti simmetrie usate per dimostrare il teorema degli invarianti collisionali, Ottengo:
$$
\int \log{f}Q[f,f]dv = \frac{1}{4}\iiint k \left[ f(v')f(w')-f(v)f(w) \right] \left[ \log{f(v)} + \log{f(w)}  -\log{f(v')}  -\log{f(w')} \right]dv\,dw\,dS
$$
raccogliendo $f(v')f(w')$ ed usando le proprietà dei logaritmi ottengo:
$$
\iiint k f(v')f(w')\left( 1-z \right)\left( \log{z}\right)dv\,dw\,dS
$$
dove $z = \frac{f(v)f(w)}{f(v')f(w')}$. La funzione integranda è non positiva. $\square$

# Equazioni di Eulero, limite idrodinamico
Per ottenere equazioni macroscopiche, passo al valore atteso degli invarianti, considerando la Maxwelliana come equilibrio.

$$
\partial_t \int \phi(v)fdv + \int \phi(v)v\cdot \nabla_x fdv = \int \phi(v)Q[f,f]dv = 0
$$
con $\phi(v)=1$ otteniamo la conservazione di massa, ovvero l'equazione di continuità:
$$
\partial_t \rho + \nabla_x\cdot (u\rho) = 0
$$

con $\phi(v)=v$ otteniamo
$$
\partial_t(u\rho) + \partial_x\left(\int v^2fdv\right)=0
$$
con $f=\mathcal{M}$ si ottiene:
$$
\partial_t(u\rho)+\partial_x(u^2\rho + P)=0
$$
con l'energia:
$$
0 + \nabla_x \cdot u = 0 
$$

