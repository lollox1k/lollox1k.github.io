Vediamo come costruire una misura, seguendo il procedimento di Caratheodory (il suo teorema di estensione).

#### Misura esterna a partire da una proto misura
Prendiamo una qualunque [[Proto misura]]  con dominio $\mathcal{D} \subseteq 2^E$ quindi una funzione a valori non negativi che manda l'insieme vuoto in zero. Definiamo una funzione $\mu^*$
$$
\mu^*(B) := inf\Big\{  \sum \mu(A_i) \quad \Big | A_i \in \mathcal{D},\quad B \subseteq \bigcup A_i  \Big\}
$$
Approssimiamo la misura di $B$ "da fuori" (per questo il nome misura esterna). Nel caso in cui 
Non esista tale successione, ovvero non esistono $C_i$ in grado di ricoprire $B$, poniamo per convenzione $inf\{ \emptyset \}=\infty$. 

#### Insiemi misurabili secondo Caratheodory
Data una misura esterna, definita quindi su tutto l'insieme delle parti, posso in maniera molto naturale definire una famiglia di insieme, detti misurabili (spoiler, sono una sigma algenbra, quindi induco una misura, anche completa).
L'insieme $A$ si dice misurabile secondo Caratheodory se vale la proprietà di _spezzamento_:
$\forall B \in 2^E$  deve valere:
$$
\mu^*(B) = \mu^*(B\cap A) + \mu^*(B \cap A^c)
$$
#### Unicità 
La procedura è quindi:
1. Definire una proto misura su un sottoinsieme dell'insieme delle parti, cosa estremamente facile;
2. Costruire la misura esterna con la definizione sopra;
3. Trovare la famiglia di insiemi misurabili, abbiamo quindi una misura completa.

Tuttavia non sappiamo se _l'estensione_ è unica, potrebbe accadere che esistano altre misure che sono in accordo sull'insieme di partenza $\mathcal{D}$ della proto misura, ma differiscono su qualche insieme misurabile secondo Caratheodory.