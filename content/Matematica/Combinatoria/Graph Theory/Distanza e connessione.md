## Relazione di raggiungibilità
Se tra i vertici $x$ e $y$ esiste un cammino dico che sono raggiungibili:
$$
x \sim y \iff \exists \text{ una passeggiata da $x$ a $y$}
$$
**Oss** E' una relazione di equivalenza su $V$ (riflessiva, simmetrica e transitiva).

Le classi di equivalenza sono chiamate *componenti connesse*, sono i sottografi connessi massimali del grafo $G$:
$$
V(G)/_\sim = V_1 \cup V_2 \cup \dots V_n
$$
definisco $\lambda(G) = n$ il numero di componenti connesse di un grafo $G$.

**Prop** Se $x \sim y$ allora esiste un cammino semplice tra $x$ ed $y$.

**Dim** 
Costruisco il cammino semplice a partire dalla passeggiata da $x$ ad $y$, infatti se non è semplice significa che c'è una ripetizioni di archi, quindi di vertici, ovvero $\exists i < j$ tale che: $x_i = x_j =: z$

$$
\mathcal{C} = x,e_1, x_2, e_2, \dots x_i, e_i,\dots x_j,e_j,\dots y
$$
posso rimuovere il blocco compreso tra questo stesso vertice $z$, ottengo una nuova passeggiata senza che il vertice $z$ si ripetea. Faccio lo stesso per tutti i vertici ripetuti, per induzione arrivo ad un cammino senza ripetizioni di vertici, ovvero semplice. $\square$

## Metrica 
Definiamo una metrica sull'insieme dei vertici $V(G)$, ovvero $d: V(G)\times V(G) \mapsto \mathbb{N} \cup \{\infty\}$

$$
d_G(x,y) = 
\begin{cases}
+\infty \text{ se } x \nsim y \\
\min \{t : t \text{ lunghezza passeggiata da $x$ a $y$} \} 
\end{cases}
$$
quindi $(G, d_G)$ è uno spazio metrico.

**Oss** Sia $G'$ un sottografo di $G$, allora $d_{G'}(x,y) \geq d_G(x,y)$ 

**Oss** Se $d_G(x,y) = t$ allora esiste un cammino semplice lungo $t$ che li collega: se non è semplice posso accorciarlo, ma è il minimo per definizione!

**Def**  Sia $G$ un grafo connesso, si definisce _Eccentricità di un vertice_ $v \in V$:
$$
ecc(v) := \max_{x \in V} d(v,x)
$$

Da questa definizione seguono altre due.

**Def** Sia $G$ un grafo connesso, si definisce il _raggio del grafo_ il numero:
$$
rad(G) := \min_{x\in V} ecc(x)
$$
il raggio di un grafo è il valore minimo di eccentricità. I vertici del grafo di minima eccentricità vengono detti _centro del grafo_.
Analogamente 
**Def** Sia $G$ un grafo connesso, si definisce il _diametro del grafo_ il numero:
$$
rad(G) := \max_{x\in V} ecc(x)
$$

i vertici di massima eccentricità vengono detti _periferia del grafo_.

Vale la seguente disugualianza tra le quantità definite

**Proposizione** Sia $G$ un grafo connesso, allora vale:
$$
rad(G) \leq diam(G) \leq 2 rad(G)
$$
**Dim** La prima disuglianza è vera per definizione. 
Per dimostrare la seconda,siano $u,v \in V$ tali che $d(u,v) = diam(G)$. Scegliamo un vertice nel centro del grafo $c$, allora vale:
$$
d(u,v) \leq d(u,c) + d(c,v) \leq 2 ecc(c) = 2 rad(G) \qquad \square
$$

**Remark** Anche nel caso $G$ non connesso valgono queste disugualianze, ma ogni eccentricità risulta infinita...


