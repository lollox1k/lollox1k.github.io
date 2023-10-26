# Misure prodotto
L'obbiettivo è arrivare al [[teorema di Fubini]] per lo scambio dell'ordine di integrazione. Prima dobbiamo definire il prodotto si spazio misurabili.

## Def Prodotto di Spazi misurabili
Sia $(S_1,\Sigma_1)$ e $(S_2,\Sigma_2)$ due spazi misurabili, chiamiamo $S$ il loro prodotto cartesiano $S:= S_1 \times S_2$. Vogliamo costruire una $\sigma$-algebra prodotto, per farlo in maniera elegante definiamo l'opratore di proiezione:
$$
\rho_i (s_1,s_2) = s_i \qquad i=1,2
$$
il gioco è fatto:
$$
\Sigma := \sigma(\rho_1,\rho_2)
$$
chiediamo che tipo si insiemi generano questa sigma algebra, per come abbiamo definito gli opertaori di proiezione, è facile, infatti $\rho_1$ se ne frega degli insiemi in $\Sigma_2$:
$$
\Sigma = \{\rho_1^{-1}(B_1), \rho_2^{-1}(B_2) \quad \forall B_1,B_2 \in \Sigma_1,\Sigma_2 \}
$$
ma le preimmgini hanno la semplice forma:
$$
\rho_1^{-1}(B_1)= B_1 \times S_2
$$
$$
\rho_2^{-1}(B_2) = S_1 \times B_2
$$
nel caso di un numero finito di prodotti cartesiani vale:
$$
(B_1 \times S_2) \bigcap (S_1 \times B_2) = (B_1 \times B_2)
$$
la sigma algebra dovrà contenere questi insiemi. E' facile vedere come formino un [[Pi-system]].
**Osservazione**
In generale non è vero che prodotto cartesiano di $\sigma$-algebra, controesempio facile in $(\mathbb{R}^2, \mathcal{B} \times \mathcal{B} )$:
$$
[0,1]\times [0,1] \bigcup [1,2]\times [1,2] \notin \mathcal{B}\times \mathcal{B}
$$
## Funzioni misurabili
Cominciamo con una caratterizzazione delle funzioni misurabili limitate sullo spazio prodotto.

Sia $\mathcal{H}$ la classe delle funzioni $f : S \mapsto \mathbb{R}$ _limitate_ e $\Sigma$ misurabili, tali che:
1. $\forall s_1 \in S_1$ fissato, la funzione $f_{s_1} : S_2 \mapsto \mathbb{R}$ con $f_{s_1}(s_2) := f(s_1,s_2)$ è $\Sigma_2$ misurabile.
2. .$\forall s_2 \in S_2$ fissato, la funzione $f_{s_2} : S_1 \mapsto \mathbb{R}$ con $f_{s_2}(s_1) := f(s_1,s_2)$ è $\Sigma_1$ misurabile.

Allora $\mathcal{H} = b\Sigma$, ovvero tutte le funzioni misurabili e limitate godono di queste due proprietà.
