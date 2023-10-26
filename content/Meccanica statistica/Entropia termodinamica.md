Nella [[Termodinamica assiomatica]] si postula l'esistenza di una funzione entropia associata ad ogni sistema macroscopico, grazie alla quale è possibile caratterizzare lo stato di equilibrio.

## Postulato  
Ad ogni sistema macroscopico $\Sigma$, descritto da un set di variabili di stato $X$, è associata una funzione differenziabile $S^\Sigma$ chiamata _entropia_, specifica del sistema. 
1. Questa funzione è additiva:
$$
S^\Sigma(X^1,X^2) = S^{\Sigma_1}(X^1) + S^{\Sigma_2}(X^2)
$$
una volta che i due sistemi sono messi in contatto (interagiscono), le variabili di stato del nuovo equilibrio $(\overline X^1, \overline X^2)$ sono quelle che massimizzano l'entropia $S^\Sigma$.

E' un _extremum principle_.

Let us emphasize that although _the thermodynamic properties of a system are entirely contained in its entropy function_ (or in any of the equations of state or thermodynamic potential derived later), _thermodynamics does not provide tools to determine what this function should be_ for a specific system (it can, of course, be measured empirically in a laboratory). As we will see, the determination of these functions for a particular system from first principles is a task that will be devolved to equilibrium statistical mechanics.

Vale quindi:
$$
\text{Sistema } \Sigma \iff \text{Entropia } S^\Sigma
$$
Come nella meccanica analitica 
$$
\text{Sistema } \Sigma \iff \text{Lagrangiana } \mathcal{L}^\Sigma
$$
Dall'entropia definiamo le [[Variabili coniugate]], quantità familiari come la _temperatura_, la _pressione_ ed il meno famoso _potenziale chimico_.

### Proprietà
1. Se un sistema è descritto dalle variabili estensive $(U,V,N)$ segue dall'additività che l'entropia è _omogenea di grado 1_ per tutte queste variabili:
$$
S(\lambda U,\lambda V, \lambda N) = \lambda S(U,V,N) \qquad \forall \lambda > 0
$$
#### Dim
Divertente, prima si dimostra per i naturali, poi razionali e per continuità per reali. 

2. E' una funzione _concava_ rispetto alla variabili.
#### Dim 
Banale segue direttamente dalla condizione di massimizazzione.

## Densità di entropia
Essendo omogenea, possiamo "portare fuori" il volume e definire un'entropia per unità di volume (una densità):
$$
S(U,V,N) = VS(\frac{U}{V},1,\frac{N}{V})
$$
definendo la densità di energia $u := \frac{U}{V}$ e la densità $\rho := \frac{N}{V}$ 
$$
s(u,\rho):= \frac{1}{V}S(uV,V,\rho V)
$$
## Entropia per particella
Possiamo fare la stessa cosa normalizzando per il numero di particelle $N$, definendo l'energia per particella $e:= \frac{U}{N}$ e il volume per particella $v := \frac{V}{N}$
$$
s(e,v):= \frac{1}{N} S(eN,vN,N)
$$



