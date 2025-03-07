# Teorema di Konig-Egervary

Se la condizione di Hall non è soddisfatta, non posso trovare un [[Teorema di Hall|insieme di rappresentanti distinti]], o di uni indipendenti per ogni riga. Qual è il numero massimo di uni che posso ottenere? A questo risponde il teorema di Konig-Egervary.

E' un risultato di tipo _minmax_, dove il massimo di una quantità è uguale al minimo di un'altra. Abbiamo visto due formulazioni per il teorema di Hall, per famiglie di insieme e grafi bipartiti. Dunque anche il teorema di Konig-Egervay avrà due forme analoghe.

## Per matrici $0$-$1$

**Teorema** (Konig-Egervary 1931) In una matrice $0$-$1$ rettangolare, il minimo numero $m$ di linee che nell'insieme contengono tutti gli $1$ è uguale al massimo numero $M$ di $1$ indipendenti.

**Dim** Se vi è un numero $M$ di $1$ indipendenti, poichè due di questi stanno su linee diverse, sono necessarie almeno $M$ linee per comprenmdere tutti gli $1$, quindi $m \geq M$.
Per dimostrare l'altro verso $M \geq m$ facciamo vedere che possiamo trovare almeno $m$ $1$ indipendenti. Supponiamo che la nostra matrice sia $p \times q$, e le linee che contengono tutti gli uni siano $m = r+s$ dove $r$ sono le righe ed $s$ le colonne. Possiamo permutare righe e colonne in modo tale che siano le prime $r$ righe e le prime $s$ colonne. Posso dividere in blocchi la matrice, le matrici "diagonali" sono piene di zero, le antidiagonali conengono uni e soddisfano la condizione di Hall. Essendo in blocchi diversi le matrici non contengono elementi in comune, ho quindi $r+s = m$ uni indipendenti. $\square$

## Per grafi bipartiti

**Teorema** In un grafo bipartito $G$, $V=V_1\cup V_2$, il massimo numero di archi in un mathing in $G$ è uguale al minimo numero di vertici in un edge-cover di $G$.

**Dim** Segue dal teorema in forma matriciale, consideriamo la matrice di adiacenza di $G$, sulle righe i vertici di $V_1$ e sulle colonne quelli di $V_2$. Ogni uno rappresenta un arco, quindi il minimo numero di linee che contiene tutti gli uni è un edge-cover che contiene meno vertici possibili. Per il teorema precedente sappiamo che questo è uguale al massimo numero di uni indipendenti, e questo è un matching massimo del grafo $G$ in $V_1$ (massimo numero di righe con uni indipendenti). $\square$

