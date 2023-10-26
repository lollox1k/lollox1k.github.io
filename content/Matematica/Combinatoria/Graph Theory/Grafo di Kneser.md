# Grafo di Kneser
I grafici di Kneser formano una famiglia infinita di grafici. 
Il grafo di Kneser $K_{n,k}$ con $n \geq k$ è un [[Grafo semplice]] i cui vertici corrispondono ai sottoinsieme di elementi $k$ di un insieme di $n$ elementi. Due vertici sono collegati se corrispondono a due sottoinsiemi disgiunti.

Il grafo $KG_{5,2}$ isomorfo al [[Grafo di Petersen]].
![[Pasted image 20221005171739.png]]

Il grado del grafo è quindi $\binom{n}{k}$ mentre la taglia è $\frac{1}{2}\binom{n}{k}\binom{n-k}{k}$, si vede facilmente usando il fatto che è un grafo regolare, quindi la somma dei gradi dei vertici è semplice, ed usando l'[[Handshake Lemma]] si arriva ad $\vert E \vert$.



