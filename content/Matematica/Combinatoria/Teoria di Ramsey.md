# Ramsey Theory

E' una generalizzazzione del [[Pigeonhole Principle]], introdotta nel $1928$ dal logico/matematico/filosofo Frank Ramsey.
Nel principio dei cassetti si devono distribuire $n$ oggetti in $m$ contenitori. In maniera equivalente, stiamo _assegnando $n$ colori ad $m$ oggeti_. Se $m >n$, almeno due oggetti avranno lo _stesso colore_.

L'idea è estendere la colorazione, non ai singoli oggetti, ma a _coppie_. Questa procedura può essere ben visualizzata _colorando archi_ di un _grafo completo_ $K_n$.

Definisco il numero minimo di oggetti $n$ che devo disporre per avere almeno un $m$

**Def** Dati $r,k,p$ interi positivi, il _numero di Ramsey_ $R(r,k,p)$ è definito come il minimo numero tale che comunque assegno un $r$ colori ai $k$-sottoinsiemi posso sempre trovare un $p$-sottoinsieme monocromatico.

*Remark 1*. Colorare un sottoinsieme non significa colorarne gli elementi, ma appunto l'insieme costituito da questi elementi, così come si fa nel aso di un grafo quando colorare una oppia $\{u, v\}$ significa colorare l'arco che cngiunge i vertici $u$ e $v$ e non i due vertici. 
Nel caso di colorare $k$-sottoinsiemi con con $k>2$, stiamo colorando _archi di ipergrafi_.

**Remark 2** l teorema di Ramsey si presenta ome una _profonda generalizzazione del principio dei cassetti_. Ad esso si può attribuire il seguente significato: 

>una struttura di una certa classe (ad esempio il grafo completo $K_n$ colorato con $r$ colori) ontiene sempre una sottostruttura appartenente alla stessa classe (il grafo ompleto $K_p$), di cardinalità elevata ($p$ assegnato grande a piacere), e on un grado di regolarità superiore a quello della struttura data ($K_p$ monocromatico).

In altri termini, vi sono _regolarità inevitabili_: un completo disordine è 
impossibile.

### Arrow notation

Esiste una notazione alternativa per indicare $R(r,k,p)$, detta _arrow notation_:
$$
R(r,k,p) = n 
$$
allora vale:
$$
n \rightarrow (p)_r^k
$$
l'idea è che sto dicendo che ogni $r$-colorazione dei $k$-sottoinsiemi dei vertici di un grafo completo $K_n$ contiene per forza (implica) l'esistenza di un sottografo di oprdine $p$ monocromatico.


## Classical 2-colors Ramsey theory

Concentriamoci sul caso a $2$ colori e colorando coppie di elementi, quindi $r=k=2$. Possiamo aggiungere la condizione di richiedere l'esistenza di almeno una sottotruttura di cardinalità fissata per ciascun colore, introducendo gli interi $p_1,\dots,p_r$. Nel nostro caso $r=2$ quindi il numero è univocamente identificato da $R(p,q)$.

**Def** Dati due interi positivi $p,q$, il numero di Ramsey $R(p,q)$ è il più piccolo intero $n$ tale che ogni $2$-colorazione degli archi di $K_2$ contiene un $K_p$ del primo colore (rosso) o $K_q$ del secondo (blu).

**Proposizione** Per tutti $p,q$ interi positivi, vale $R(p,q)=R(q,p)$.
**Dim** Naturale conseguenza della simmetria per scambio di colori: data una colorazione degli archi di un completo, ottengo una colorazione complementare ottenuta scambiando i colori.
Per definizione ogni $2$-colorazione degli archi di $K_{R(p,q)}$ dovrà contenere un $K_p$ rosso e $K_q$ blu. Analogamente ogni $2$-colorazione di $K_{R(q,p)}$ dovrà contenere un $K_q$ rosso ed un $K_p$ blu. Ma le colorazioni complementari sono ancora colorazioni. $\square$ 

### Esempi

Facciamo alcuni esempio semplici.
-  $R(1,k)$ 
Stiamo richiedendo che $K_n$ contenga sempre un $K_1$ rosso, ma $K_1$ è un singolo vertice senza archi (che colore assegno?), lo definiamo monocromatico. Quindi 
$$
R(1,k)=R(k,1)=1
$$

- $R(2,k)$
Se ho un $K_n$ con $n<k$, posso colorare tutti gli archi di blu, avendo zero archi rossi non ho $K_2$ rosso, e di certo non posso contenere un $K_k$ blu. quindi $R(2,k) \geq k$. Consideriamo ora $K_k$, di nuovo, se colo anche un solo vertice di rosso, soddisfo la condizione. Se al contrario non ne coloro nessuno, alla fine avrò un grafo completo tutto blu di ordine $k$, quindi
$$
R(2,k)=R(k,2)=k
$$


## Teorema di Ramsey

Resta da provare che la definzione sia corretta, ovvero che per ogni intero positivo $r,k,p$ esiste un $m$ tale che $R(r,k,p)=m$. Dimostriamo prima il caso $r=2$. Usando la notazione introdotta sopral equivale a dire che:

Per dimostrare questo teorema (finito), useremo argomenti infiniti.

**Teorema 1** Sia $G$ un grafo completo infinito con vertici numerabili. Data ogni $2$-colorazione degli archi, conterrà sempre un completo infinito monocromatici, in arrow notation:
$$
\omega \rightarrow (\omega)_2^2
$$
**Dim** Costruiamo una sottosequenza infinita di vertici $\{w_i \,|\, i \in \mathbb{N}\}$ di $V(G)$ applicando ripetutamente il [[Pigeonhole Principle]]. 
Sia $w_0 = v_0$. Per ogni $i \geq 1$ il vertice $v_0v_i$ è blu o rosso. Consideriamo la funzione $f : V\setminus \{v_0\} \mapsto \{blue,\, red\}$ che manda un vertice nel colore del suo arco $v_0v$. Quindi esisterà almeno uno dei due colori che ha come preimmagine un insieme infinito di vertici: $f^{-1}(c) = V_0$ con $c=blue,\,red$.
Per costruire la sequenza, scelgo $w_1$ come il vertice in $V_0$ con l'etichetta più bassa (li ho enumerati). Faccio lo stesso scegliendo $w_2$ come il vertice in $V_1$, (insieme costruito analogamente a $V_0$). e che non compare già nella sequenza (non posso avere $w_2 = w_0$). 
Questa sequenza ha una proprietà interessante. Se $i<j<k$ allora $w_j,w_k \in V_i$, quindi gli archi $v_iv_j,\, v_iv_k$ hanno lo stesso colore! Quindi ogni $w_i$ manda $j>i$ in un colore, o rosso o blu. Sto colorando di due colori una sequenza infinita, quindi sempre per il pigeonhole principle esiste una sottosuccessione dello stesso colore.  Questa induce un sottografo completo monocromatico infinito. $\square$

**Teorema 2** Per ogni $n \in \mathbb{N}$ esiste un $m \in \mathbb{N}$ tale che $R(n,n)=m$.
**Dim** Supponiamo per contraddizione che esista un $n$ tale che per ogni $m$ esiste una $2$-colorazione degli archi di $K_m$ per cui non contiene un $K_n$ monocromatico.
Sia $G$ un grafo completo (infinito) con vertici numerabili $V(G)=\{v_i\,|\, i \in \mathbb{N}\}$, consieriamo $E = \{e_i \,|\, i \in \mathbb{N}\}$ una enumerazione degli archi di $G$.
Costruiamo un albero $T$ delle colorazioni parziali degli archi di $G$ nella maniera seguente: la radice dell'albero è la colorazione vuota. Ogni livello $L_i$ corrisponde ad un arco $e_i$, e contiene $r=2^i$ vertici: ad ogni livello sto scegliendo come colorare l'arco $e_i$. 

Dobbiamo togliere tutte le colorazioni (che sono cammini) tali che il sottografo di $G$ indotto da $e_0,e_1,\dots,e_k$ contiene una componente monocromatica $K_n$.

>E' come l'albero degli assegnamenti parziali per una teoria infintia di formule proposizionali!

L'albero di tutte le colorazioni parziali di $G$ è ovviamente infinito con livelli finiti. Una volta rimossi i cammini che contengno componenti monocromatiche $K_n$, siccome per ipotesi ne esistono sempre colorazioni che non lo contengno, ho ancora un albero infinito. Dunque per il [[Koning's lemma|lemma di Konig]] esiste un cammino infinito. Questo cammino fornisce una $2$-colorazione di $G$ che non contiene un completo $K_n$ monocromatico, di conseguenza $G$ non può contenere un completo monocromatico infinito, contro il **teorema  1**,contraddizione. $\square$

Il teorema può essere generalizzato per induzione ad ogni numero di colori finiti:

**Teorema 3** (Ramsey infinito) Per ogni $n \in \mathbb{N}$ e $c \in \mathbb{N}$ vale:
$$
\omega \rightarrow (\omega)_c^n
$$
**Teorema 4** (Ramsey finito) Per ogni $k,n,c \in \mathbb{N}$ esiste un $m \in \mathbb{N}$ tale che:
$$
m \rightarrow (k)_c^n
$$
**Dim** Segue dal precedente, si usa il principio dei cassetti finito. $\square$







