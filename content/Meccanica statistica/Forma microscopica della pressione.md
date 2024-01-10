# Pressione
>> Intuitivamente: Forza per unità di superficie

Pressione di un gas? Con l'ipotesi atomica immagino che le molecole del gas urtino la pareti del contenitore, trasferendo quantità di moto. Forte pressione corrisponde microscopicamente a molti urti, ovvero frequenti e ad alta velocità (dipende dalla velocità meida quindi  dalla temperatura).

## Definizione termodinamica
Dal primo principio e secondo principio:
$$
dU = TdS - pdV \implies p = -\frac{\partial U}{\partial V} 
$$
## Definizione microscopica
Parte dallo spazio delle fasi (microstato). Deve essere in accordo con quella termodinamica, Ortodicità degli ensemble.

Definiamo $n(Q,v)dv$ il numero di particelle contenute in un cubo $Q$ adiacente al bordo del contenitore del sistema con velocità normale alla parete negativa compresa tra $[-v,-(v+dv)]$ $v >0$ (affinchè avvenga l'urto) diviso il volume di $Q$.
Assumendo un urto elastico, ogni particella trasferisce quantità di moto pari a $2mv$.

Definiamo l'osservabile sullo spazio delle fasi del sistema:
$$
P(\Delta) := \sum_Q \int_{v>0} dv n(Q,v)(2mv)\frac{vs}{S}
$$
dove $\cup Q = \partial V$, $s$ è la superficie di una faccia dei cubi $Q$ ed $S$ la superficie del sistema.

_E' la quantità di moto trasferita, per unità di tempo e superficie, sulla parete_

Infatti il numero di collisioni per unità di tempo su una faccia $s$ dei cubetti $Q$ è $n(Q,v)vsdv$, infatti il numero di particelle nel cubo con una data velocità è:
$$
n(Q,v)dv(\delta l)^3
$$
dove $\delta l$ è il lato dei cubi $Q$. Il tempo per ottenere un urto è dell'ordine:
$$
\delta t \sim \frac{\delta l}{v}
$$
il rate, ovvero la frequenza degli urti è l'inverso, che moltiplicato all'espressione precedente da la quantità cercata:
$$
n(Q,v)dv (\delta l)^2 v = n(Q,v)vs dv \qquad \square
$$
### Claim 
>> Questa definzione microscopica corrisponde a quella macroscopica termodinamica

Infatti vale la relazione:
$$
p = -\frac{\partial U}{\partial V} =\frac{\partial F}{\partial V} = \beta^{-1}\frac{\partial}{\partial V}\log Z(\beta,V)
$$
### Dim 
$$
p = P(\mu)= \sum_Q\frac{1}{Z(\beta,V)}\iint dpdq \,e^{-\beta E(p,q)} \int_{v>0} dv\,n(Q,v)(2mv)\frac{vs}{S} 
$$
