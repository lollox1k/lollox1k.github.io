# Sistemi reticolari
Perchè ha senso studiare modelli semplificati, su un reticolo? 
1. la parte complicata da trattare ed interessante è solo quella dovuta al potenziale, le interazioni
2. possiamo ignorare i momenti!

Lavoriamo sui sitemi reticolari, ovvero in $\mathbb{Z}^d$.
Indichiamo un _volume finito_ con $\Lambda \Subset \mathbb{Z}^d$. 

L' insieme degli stati microscopici di un sistema nel volume $\Lambda$ non è altro che un elemento dell'insieme
$$
\omega \in \Omega_\Lambda, \qquad \Omega_\Lambda := \{-1,1\}^{|\Lambda|}
$$
e sarà quindi della forma $\omega = (\omega_i)_{i \in \Lambda}$.
Torna utile identificare un volume $\Lambda$ con le coppie di siti adiacenti, specialmente nel caso di interazioni nearest neighbour.
$$
\mathcal{E}_\Lambda := \{(i,j) \subset \Lambda \,\vert \,i \sim j\}
$$
Per ogni volume finito $\Lambda$, l'_energia della configurazione_ $\omega$ è determinata dall'hamiltoniana:
$$
\mathcal{H}_\Lambda : \omega \mapsto \mathbb{R}
$$
Come per i sistemi continui, si definisce un'energia potenziale $U$ tramite un insieme di interazioni $(\Phi_k(x))_{k\in 1,2,\dots}$, ovvero interazioni tra $k$ siti:
$$
U(\Omega) := \sum_{\xi \subset \Omega} \Phi_{|\xi|}(\xi)
$$
Diverse interazioni (diverse hamiltoniane) danno luogo a modelli diversi:
1. [[Lattice gas]]