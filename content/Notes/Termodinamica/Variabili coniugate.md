Vediamo come ricavare a partire dalla funzione entropia le altre quantità con cui si lavora in termodinamica classica. Per ipotesi la funzione entropia è differenziabile. 

Le variabili macroscopiche con cui solitamente si descrive un sistema isolato (in maniera molto generali) sono:
$$
X = (U,V,N)
$$
l'energia, il volume ed il numero di particelle.

Dalla termodinamica classica sappiamo che due sistemi all'equilibrio devono avere:
1. stessa temperatura $T_1 = T_2$
2. stessa pressione $P_1 = P_2$
3. stesso potenziale chimico $\mu_1 = \mu_2$
Applicando il principio di massima entropia tra due sistemi, richiediamo che l'entropia totale sia stazionaria, troviamo per ogni variabile:
$$
\frac{\partial S}{\partial U_1}(U_1)+ \frac{\partial S}{\partial U_1}(U-U_1) = 0
$$
ovvero:
$$
\frac{\partial S}{\partial U }(\overline U_1) = \frac{\partial S} {\partial U}(\overline U_2) 
$$
in maniera analoga per le altre derivate:
$$
\frac{\partial S}{\partial V}(\overline V_1) = \frac{\partial S}{\partial V}(\overline V_2) \qquad \frac{\partial S}{\partial N}(\overline N_1) = \frac{\partial S}{\partial N}(\overline N_2)
$$
Questo ci porta alla naturale indentificazione delle derivate dell'entropia con le quantità termodinamiche sopra citate.

### Temperatura assoluta
$$
\frac{1}{T} := \Big (\frac{\partial S}{\partial U}\Big)_{V,N}
$$
in meccanica statistica si definisce $\beta = 1/T$. Essendo $T>0$, _l'entropia è funzione strettamente crescente della temperatura_ (è invertibile).

### Pressione
$$
P:= T\Big( \frac{\partial S}{\partial V}\Big)_{U,N}
$$
### Potenziale chimico
$$
\mu:= -T\Big( \frac{\partial S}{\partial N}\Big)_{U,V}
$$
Il segno ed i fattori $T$ servono per essere in accordo col primo e secondo principio della termodinamica!

## Le variabili coniugate sono intensive
Segue direttamente dalla definzione:
$$
f_i = \frac{\partial S(\lambda x_i)}{\partial (\lambda x_i)} = \frac{\lambda S(x_i)}{\lambda \partial x_i} = \frac{\partial S(x_i)}{\partial x_i}
$$
quindi $\forall \lambda > 0$:
$$
T(\lambda U, \lambda V, \lambda N) = T(U,V,N)
$$
$$
P(\lambda U, \lambda V, \lambda N) = P(U,V,N)
$$
$$
\mu(\lambda U, \lambda V, \lambda N) = \mu(U,V,N)
$$
sono _omogenee di grado 0_.

Derivando per $\lambda$ e dopo ponendo $\lambda = 1$ otteniamo la relazione di Eulero:
$$
S(U,V,N) = \frac{U}{T} + \frac{P}{T}V - \frac{\mu}{T}N
$$
che ci permette di ricostruire la funzione entropia dalla conoscenza della dipendenda funzionale delle variabili intensive da quelle estensive, ovvero le _equazioni di stato_.

Siccome non sono indipendneti, ne bastano solo due delle tre per determinare l'entropia.
Es. Gas perfetto:
$$
P = \frac{NRT}{V} \qquad U = cRNT
$$
da qui si arriva all'entropia per il gas perfetto. Partendo dal differenziale dell'entropia per particella (ed usando l'omogeneità delle variabili intensive):
$$
ds(e,v) = \frac{\partial s}{\partial e}de+ \frac{\partial s}{\partial v}dv = \frac{1}{T}de + \frac{P}{T}dv 
$$
usando le due equazioni di stato:
$$
\frac{1}{T}=cR\frac{N}{U} =\frac{cR}{e} \qquad \frac{P}{T}=R\frac{N}{V}=\frac{R}{v} 
$$
integrando si ottiene a meno di una costante la funzione entropia per particella
$$
s(e,v)=cR\log(e/e_0) - R\log(v/v_0) + s_0
$$
moltiplicando per $N$ 
$$
S(U,V,N) = Ns_0 + NR\log[(U/U_0)^c (V/V_0)(N/N_0)^{-(c+1)}]
$$
