# Teorema di Erdos (1947)
In generale vale il lower bound per il [[Graph coloring|numero cromatico]]
$$
\omega(G) \leq \chi(G)
$$
**Oss** Per i cicli dispari vale $\omega(C_{2k+1}) < \chi(C_{2k+1})$.

**Domanda** Quando può essere grande il divario tra il numero di clique e il numero cromatico?
**Risposta** Può essere esponenzialmente più grande del numeri di clique.

Più precisamente:
**Teorema**
Per $k \geq 4$, esiste un grafo $G$ con:
1. $\vert V(G)\vert \geq 2^{k/2}$;
2. $\alpha(G) < k$;
3. $\omega(G) < k$

**Corollario**
Segue dal teorema e dal [[Graph coloring#Relazioni con gli altri invarianti| lower bound]]:
$$
\frac{\vert V(G) \vert}{\alpha(G)} \leq \chi(G)
$$
come il numero cromatico posso essere esponenzialmente più grande di quello di clique.

**Dim** La dimostrazione è non costruttiva, mostriamo solo che un grafo con quelle proprietà deve esistere.

Sia $n = 2^{k/2}$, e $[n] = \{1,2,\dots, 2^{k/2}\}$.
Sia $\mathcal{G}_n := \{ G \;:\; V(G) = [n]\}$ l'insieme dei grafi etichettati su $[n]$.
Ovviamente $|\mathcal{G}_n| = 2^\binom{n}{2}$, l'insieme delle parti di tutti gli archi possibili.  

Dati due grafi $G,G'$ su $[n]$ distinti, devono avere archi distinti, ovvero $E(G)\neq E(G')$.

Definiamo due sottoinsiemi di $\mathcal{G}_n$:
 $$
 \begin{aligned}
 \mathcal{A}_n := \{G \in \mathcal{G}_n \,:\, \alpha(G) \geq k\} \\
  \Omega_n := \{G \in \mathcal{G}_n \,:\, \omega(G) \geq k\} \\
 \end{aligned}
$$
E' chiaro che il nostro grafo cercato, sarà nell'intersezione dei complementari di questi due sottoinsiemi:
$$
\mathcal{G}_n \setminus(\mathcal{A}_n \cup \Omega_n)
$$
Se riusciamo a mostrare che quest'insieme è non vuoto, allora il teorema è dimostrato.

**Claim 1** $|\mathcal{A}_n| = |\Omega_n|$. Infatti c'è una biiezione tra i due insiemi, il passaggio al grafo complementare.

**Claim 2** La proprietà di un grafo di essere una clique è ereditaria, ovvero è chiusa per inclusione: se $C$ è una clique, allora $C' \subseteq C$ è ancora una clique.

In particolare, se $G \in \Omega_n$, per definizione $\omega(G) \geq k$, quindi esiste certamente una clique $K$ di ordine  $k$ come sottografo di $G$. 
Sfruttiamo le clique di ordine $k$ per costruire un ricoprimento dell'insieme $\Omega_n$, fissando clique con etichette diverse:
$$
\Omega_n = \bigcup_{K \subseteq [n], |K|=k} \Omega_n(K)
$$

dove $\Omega_n(K) := \{G \in \mathcal{G}_n \,:\, K \text{ è clique di } G\}$.
L'inclusione $\supseteq$ è banale, essendo unione di sottoinsiemi.
Per far vedere il verso $\subseteq$, sia $G \in \Omega_n$. Per definizione $\omega(G) =t \geq k$. Quindi $\exists C$ clique di ordine $t$ contenuta in $G$, e siccome la proprietà di essere clique è ereditaria, esiste anche una clique $K \subseteq C$ di ordine esattamente $k$ (ne esisteranno più di una se $t > k$, questo mostra che non è una partizione), quindi esiste $K$ tale che $G \in \Omega_n(K)$.

Sfruttiamo la cover per ottenere un upperbound sulla cardinalità di $\Omega_n$. Dobbiamo calcolare $|\Omega_n(K)|$ per una $k$-clique ad eichette fissate. Ma questo significa che ho degli archi obbligati, quelli che appaiono nella clique, che sono $\binom{k}{n}$. Di conseguenza la carindalità è:
$$
|\Omega_n(K)| = 2^{\binom{n}{2}-\binom{k}{2}}
$$
Mettendo tutto insieme;
$$
|\Omega_n| \leq \sum_{K \in \binom{[k]}{2}} |\Omega_n(K)| = \binom{n}{k} 2^{\binom{n}{2}-\binom{k}{2}} 
$$
usando un [[Coefficiente binomiale#Upper bound|upper bound]] sul primo coefficiente binomiale per semplificare, otteniamo:
$$
\binom{n}{k} \leq \frac{n^k}{k!}
$$
inotre per $k\geq 4$ vale
$$
\frac{1}{k!} < \frac{1}{2^k}
$$
| k  | 1/k!          | 1/2^k      |
|----|---------------|------------|
| 0  | 1             | 1          |
| 1  | 1/1! = 1      | 1/2 = 0.5  |
| 2  | 1/2! = 1/2    | 1/4 = 0.25 |
| 3  | 1/3! = 1/6    | 1/8 = 0.125|
| 4  | 1/4! = 1/24   | 1/16 = 0.0625 |
| 5  | 1/5! = 1/120  | 1/32 = 0.03125 |
| 6  | 1/6! = 1/720  | 1/64 = 0.015625 |
| 7  | 1/7! = 1/5040 | 1/128 = 0.0078125 |
| 8  | 1/8! = 1/40320| 1/256 = 0.00390625 |

questo fatto insieme alla scelta intelligente di $n=2^{\frac{k}{2}}$
$$
|\Omega_n| < 2^{\binom{n}{2}-\binom{k}{2}+k(\frac{k}{2}-1)}
$$
per semplificare ancora le cose, notiamo che per $k \geq 2$ vale:
$$
k\left(\frac{k}{2}-1\right) < \binom{k}{2}-1 = \frac{k(k-1)}{2} -1
$$
Dunque vale strettamente per $k \geq 4$.

Ritorniamo al teorema, per far vedere che un insieme è non vuoto basta far vedere che la sua cardinalità non è nulla:
$$
|\mathcal{G}_n\setminus(\mathcal{A}_n \cup \Omega_n)| = |\mathcal{G}_n| - |\mathcal{A}_n \cup \Omega_n|
$$
siccome sono sottoinsiemi. Non sono disgiunti, ma posso stimare dall'alto con al somma:
$$
|\mathcal{G}_n\setminus(\mathcal{A}_n \cup \Omega_n)| \geq |\mathcal{G}_n|- 2|\Omega_n| > 2^{\binom{n}{2}} -2\cdot 2^{\binom{n}{2}-\binom{k}{2}+k(k/2-1)}
$$
usando l'ultimo upperbound (stretto) discusso:
$$
> 2^{\binom{n}{2}} -2^{\binom{n}{2}} = 0
$$
Quindi l'insieme è non vuoto. $\square$ 

