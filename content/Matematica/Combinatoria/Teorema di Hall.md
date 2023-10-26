# Insieme trasversale

Consideriamo un insieme finito, $[n] = \{1,2,\dots, n\}$, ed una famiglia $\mathcal{F}$ (un multinsieme) finita di elementi dell'insieme delle parti $2^{[n]}$ (posso avere copie degli stessi sottoinsiemi).

**Def** Un _insieme trasversale_ $T$, anche detto un  $SRD$ _insieme di rappresentanti distinti_ , di una famiglia di sottoinsiemi $\mathcal{F}$ è un insieme con la proprietà che $\forall A_i \in \mathcal{F} \quad \exists a_i \in T$ tale che $a_i \in A_i$, con $a_i$ rappresentante del sottoinsieme $A_i$, e $a_i \neq a_j$ quando $i\neq j$.

**Osservazione** è ovvio che in generale non tutte le famiglie ammettano un insieme di rappresentanti distinti, ad esempio banale $\mathcal{F} = (\{1\}, \{1\})$. 
Una condizione necessaria è che scelti $k$ elementi della famiglia, la loro unione debba contenere almeno $k$ elementi distinti, altrimenti è impossibile trovare dei rappresentanti biunivoci, dopo tutto voglio avere una funzione iniettiva, e per il principio dei cassetti non può esistere se la condizione precedente non vale.
La cosa meno ovvia, è che anche una condizione sufficiente.

## Il teorema di Hall

**Teorema** (Hall)
Sia data la famiglia $\mathcal{F} = \{A_1,\dots,A_m\}$. Se $\forall k = 1,\dots,m$ e $\forall i_1,\dots,i_k \subseteq [m]$ insieme di indici vale:
$$
\left|\bigcup_{j=1}^k A_{i_j}\right| \geq k 
$$
detta _condizione di Hall_, allora la famiglia ammette un insieme di rappresentanti distinti (trasversale).

Prima dimostriamo un lemma.
**Lemma** Sia $\mathcal{F}$ una famiglia che ammette un SDR. Sia $R = \{a_1,\dots,a_{\rho}\}$ l'intersezione di tutti i SDR di $\mathcal{F}$, allora vale:
$$
\left | \bigcup_{i=1}^\rho T_i\right|=\rho
$$
**Dim lemma** è chiaro che deve valere la condizione necessaria di Hall, quindi la cardinalità è maggiore uguale a $\rho$. Facciamo vedere che se fosse maggiore, si arriva ad un assurdo: esiste quindi un elemento $a \neq a_1,\dots,a_\rho$ che appartiene a qualche $T_i$ con $i=1,\dots,\rho$. Siccome $a \notin R$, esiste un SDR in cui non compare. Preso questo insieme trasversale, sostituendo $a_i \to a$ si ottiene un nuovo $SDR$, dove non compare $a_i$: assurdo, in quanto per ipotesi $a_i \in R$. $\square$
**Dim** Il teorema segue semplicemente dal lemma, per induzione:
- $m=1$, la condizione di Hall garantisce che l'unico sottoinsieme sia non vuoto, esiste quindi un elemento che può rappresentarlo.
- Passo induttivo, supponiamo che una famiglia di cardinalità $m-1$ ammetta un SDR, mostriamo che la condizione di Hall sulla famiglia $\mathcal{F}' := \mathcal{F} \cup \{T_m\}$ implica l'esistenza di un insieme trasversale. Se $T_m \not\subseteq R$, ovvero se non è contenuto nell'intersezione di tutti i SDR della famiglia $\mathcal{F}$, esisterà un insieme trasversale per $\mathcal{F}'$: basta prendere $a_m \in T_m$ tale che $a_m \notin R$. 
- Se $T_m \subseteq R$, allora:
$$
\left | \bigcup_{i=1}^\rho T_i \cup T_m\right|=\rho < \rho +1
$$
contro l'ipotesi di Hall. $\square$

**Dim 2**
Per induzione sulla cardinalità della famiglia $m$.
Base $m=1$, la condizione di Hall ci assicura che l'unico insieme sia non vuoto, quindi esiste un SDR.
Sia $m > 1$, considero una famiglai $\mathcal{F} = (A_1,\dots,A_m)$.
Dividiamo il ragionamento in due casi:
1. _Caso abbondante_: $\forall k < m$, scelti $k$ insiemi da $\mathcal{F}$ ho che:
$$
\left|\bigcup A_i\right| \geq k+1
$$
Sia $x \in A_1$, per l'ipotesi abbondante $|A_1| \geq 2$. Consideriamo la famiglia:
$$
\mathcal{F}' = (A_2',\dots, A_m') \qquad A_i' = A_i \setminus \{x\}
$$
La famiglia $\mathcal{F}'$ ha $m-1$ elementi, vale l'ipotesi induttiva e dunque esiste un $SRD$. Posso estenderlo con l'elemento $x$ ad un $SRD$ di $\mathcal{F}$.
2. _Caso magro_: Esiste un $k<m$ ed un insieme di $k$ indici per cui:
$$
\left|\bigcup A_i\right| = k
$$
s.p.g, chiamiamo questi insiemi $A_1,\dots,A_k$. Siccome $k<m$, per ipotesi induttiva esiste un $SRD$ per questi insiemi: $T = \{a_1,\dots,a_k\}$, e deve valere per quanto detto $\cup_{i=1}^k A_i = T$.
Costruiamo una nuova famiglia rimuovendo gli elementi di $T$ agli insiemi rimanenti:
$$
\mathcal{F}' = (B_{k+1},\dots, B_m) \qquad B_i:= A_i \setminus T \qquad k+1\leq i \leq m 
$$
supponiamo che esista un $SRD$ per $\mathcal{F}'$, è evidente che estendendolo con $T$ ottengo un $SRD$ per la famiglia di partenza. Resta da fare vedere che $\mathcal{F}'$ ammette un $SRD$, siccome abbiamo solo $m-k$ insiemi, se vale la condizione di Hall possiamo usare l'ipotesi induttiva.

Consideriamo un insieme di $h$ indici, allora vale:
$$
\left|\bigcup_{i=1}^k A_i \;\cup\; B_j{_1}\cup B_{j_2} \cup \dots \cup B_{j_h}\right| = k + |B_j{_1}\cup B_{j_2} \cup \dots \cup B_{j_h}|
$$
essendo disgiunti. Inoltre l'unione è uguale all'unione di degli insiemi originali:
$$
 \left|\bigcup_{i=1}^k A_i \;\cup\; B_j{_1}\cup B_{j_2} \cup \dots \cup B_{j_h}\right| \geq k+h
$$
siccome per ipotesi soddisfano la condizione di Hall. Ma questo implica:
$$
|B_j{_1}\cup B_{j_2} \cup \dots \cup B_{j_h}| \geq h
$$
quindi la famiglia $\mathcal{F}'$ per ipotesi ammette $SRD$. $\square$

## Altre forme 

Il teorema può essere riformulato in termini di [[Grafi bipartiti]] e [[Matchings|matching completi]], infatti un matching completo è un insieme trasversale. 

**Teorema** (Hall per grafi bipartiti) Un grafo bipartito $V = V_1 \dot\cup V_2$ ammette un matching completo se e solo se vale la condizione di Hall, $\forall S \subseteq V_1$ vale $|\Gamma(S)| \geq |S|$.

Ad ogni grafo posso associare la sua matrice di adiacenza, quindi il teorema può essere riformulato anche in termini di matrici.

Un insieme trasversale per una matrice $0$-$1$ è una scelta di "$1s$" per ogni riga che non siano sulle stesse colonne.   


**Teorema** (Hall forma matriciale) Una matrice $0$-$1$ ammette un insieme trasversale se e solo se $\forall k$, gli "$1$s" su $k$ righe sono un almeno $k$ colonne diverse.

## Ipotesi aggiuntive

La condizione di Hall seppur semplice concettualmente, non è semplice da verificare, infatti ho un numero esponenziale di casi da controllare.
Aggiungendo ipotesi sulla famiglia ottengo condizioni meno stringenti.

**Proposizione** Sia $A$ un insieme finito $|A|=n$, ed $\mathcal{F} = (A_1,\dots,A_m)$ una famiglia _uniforme_ di sottoinsiemi di $A$, ovvero hanno tutti la stessa cardinalità $r \leq n$. Allora, se $\forall x \in A$  appare nello stesso numero $d$ di sottoinsiemi, ed $m \leq n$, esiste un insieme trasversale.

**Dim** Rappresentiamo la famiglia in forma matriciale, i sottoinsiemi sulle righe e gli elementi sulle colonne. Siccome ogni $A_i$ ha cardinalità $r$ ogni riga contiene esattamente $r$ uni. Siccome ogni elemento appare esattamente in $d$ insieme, ogni colonna ha $d$ uni. 
Ho due modi di contare tutti gli uni della matrice:
- Per righe: $m\cdot r$ 
- Per colonne $d\cdot n$
Siccome $m \leq n$ $\implies$ $r \geq d$ 
Supponiamo per assurdo non valga la condizione di Hall, allora esistono $k$ sottoinsiemi $A_{i_1},\dots,A_{i_k}$ tali che:
$$
U := A_{i_1} \cup \dots \cup A_{i_k}\qquad| U| < k
$$
Ripeto il doppio conteggio nella matrice di incidenza dell $k$ righe:
$$
k\cdot r = \sum_{j = 1}^k |A_{i_j}|= \sum_{x \in U} d_x \leq d |U| < k\cdot d
$$
dove con $d_x$ indichiamo quante volte compare l'elemento $x$ negli insiemi $A_{i_1},\dots$ $\square$ 

