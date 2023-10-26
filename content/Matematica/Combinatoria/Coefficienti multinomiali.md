# Coefficienti multinomiali
Generalizza in maniera naturale il [[Coefficiente binomiale]]:
Consideriamo la potenza $n$-esima del polinomio:
$$
(x_1 + x_2 + \dots + x_k)^n = \sum z_1z_2\dots z_n \quad z_i \in \{x_1,\dots, x_k\}
$$
è una somma di tutte le stringhe lunghe $n$ di elementi scelti tra le $x_i$.  Se una data stringa $z = z_1\dots z_n$ ha $r_i$ occorrenze di $x_i$, la somma $\sum_i r_i = n$. Se le variabili commuatano, allora la stringa si può scrivere come:
$$
z = x_1^{r_1}x_2^{r_2}\dots x_k^{r_k}
$$
il coefficiente multinomiale $\binom{n}{r_1 \, \dots r_k}$ sarà il numero di occorrenze di queste stringhe.
$$
(x_1 + x_2 + \dots + x_k)^n = \sum_{r_1,\dots r_k \; \sum r_i = n} \binom{n}{r_1\,\dots \, r_k} x_1^{r_1}x_2^{r_2}\dots x_k^{r_k}
$$
**Osservazione**
Una $k$-partizione ordinata di $[n]$ è una tupla di insiemi $(A_1,\dots, A_k)$ disgiunti che uniti danno $[n]$. Se fisso le cardinalità degli insiemi $|A_i| = r_i$, è chiaro che c'è una corrispondenza biunivoca tra le $k$-partizioni con cardinalità $r_1,\dots r_k$ e le stringhe sopra menzionate.

> un'altra caratterizzazione del coefficiente multinomiale è il numero di partizioni di $[n]$  in $k$ sottoinsiemi (ordinati) con cardinalità fissata $r_1, \dots, r_k$  

Vediamo concretamente:

_alfabeto_ $= \{1,2,3,4\}$ $k = 4$ 
_stringhe_ $z = 114432$   $n=6$

voglio trovare una biiezione tra $z \mapsto (A_1,A_2,A_3,A_4)$
il carattere $1$ ha due occorrenze, $4$ ne ha due, $3$ e $2$ ne hanno una. Il carattere $1$ corrisponde all'insieme $A_1$, e le posizioni in cui compare $1$ sono gli elementi di $[n]$ che appartengono ad $A_1$. Nel nostro caso:
$$
114432 \mapsto (\{1,2\}, \,\{6\}, \,\{5\}, \,\{3,4\})
$$
è chiaro che è una biiezione.

Se consideriamo una funzione $f  : [n] \mapsto [k]$, con $k \leq n$, è chiaro che le preimmagini formano una partizione, e ugualmente ogni $k$-partizione induce una funzione $g : [n] \mapsto [k]$, se $x \in A_i$ allora $g(x) = i$.

Quindi il coefficiente  multinomiale è il numero di funzioni da $[n]$ in $[k]$ con fibre $f^{-1}(i)$ di cardinalità fissata $r_1,\dots ,r_k$.

Come per il coefficente binomiale il ruolo delle $r_i$ è  simmetrico.

## Relazione di ricorrenza

Prima di dimostrarla algebricamente, esiste una semplice regola di addizione, una relazione di ricorrenza. Supponiamo di avere $m$ scatole ed $n$ oggetti da distribuire. Sia $\alpha \in [n]$ un particolare oggetto. Se lo mettiamo nella prima scatola, per i rimanenti oggetti abbiamo:
$$
\binom{n-1}{r_1-1, r_2,\dots, r_m}
$$
in maniera simili, se mettiamo $\alpha$ nella seconda scatola dovremmo diminuire $r_2$ di uno. Siccome possiamo partizionare tutti i possibili assegnamenti in base a dove contengono l'elemento $\alpha$, la cardinalità di tutti gli assegnamenti sarà la somma. $\square$

Algebricamente:

$$
(x_1 + x_2 + \dots + x_k)^n = (x_1 + x_2 + \dots + x_k)^{n-1}(x_1 + x_2 + \dots + x_k)
$$
$$
= \left(  \sum_{(s_1,\dots s_k) \; \sum s_i = n-1} \binom{n-1}{s_1\dots\, s_k} x_1^{s_1}\dots x_k^{s_k}\right)(x_1+x_2\dots + x_k)
$$
$$
= \sum_{j=1}^k \left( \sum_{(s_1,\dots s_k) \; \sum s_i = n-1} \binom{n-1}{s_1\dots\, s_k} x_1^{s_1}\dots x_j^{s_j+1}\dots x_k^{s_k} \right)
$$
adesso se $i\neq j$ poniamo $r_i := s_i$ mentre se $i=j$ $r_i := s_i + 1$. (quindi la somma $\sum r_i = n$)
$$
=   \sum_{(r_1,\dots r_k) \; \sum r_i = n} \sum_{j=1}^k\binom{n-1}{r_1\dots\ r_j -1 \dots r_k} x_1^{r_1}\dots x_j^{r_j}\dots x_k^{r_k} 
$$
confrontando otteniamo la seguente relazione:
$$
\binom{n}{r_1 \dots r_k} = \sum_{j=1}^k \binom{n-1}{r_i \, \dots r_j-1 \, \dots r_k}
$$
## Forma algebrica
Dati  interi non negativi $r_1, \dots r_k$ tali che $\sum_i r_i = n$, abbiamo:
$$
\binom{n}{r_1\, \dots r_k} = \frac{n!}{r_1!\dots r_k!}
$$
### Dim
Ricostruiamola a partire dal coefficiente binomiale, per cui abbiamo una forma algebrica. Usiamo la caratterizzazione come funzioni con cardinalità delle fibre fissate. Possiamo scegliere la controimmagine di $1$ in $\binom{n}{r_1}$ modi diversi. Poi restano $n-r_1$ elementi per scegliere la preimmagine di $2$, quindi $\binom{n-r_1}{r_2}$ e così via. In totale:
$$
\binom{n}{r_1}\binom{n-r_1}{r_2}\dots \binom{r_k}{r_k}
$$
sostituendo la formula algebrica del binomiale:
$$
\frac{n!}{r_1!(n-r_1)!} \frac{(n-r_1)!}{r_2!(n-r_1-r_2)!} \dots
$$
dopo le cancellazzioni:
$$
\frac{n!}{r_1!r_2!\dots\, r_k!}
$$
$\square$

