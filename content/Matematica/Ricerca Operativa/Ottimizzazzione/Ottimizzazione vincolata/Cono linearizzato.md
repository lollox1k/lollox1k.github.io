# Il cono linearizzato
Abbiamo visto come il [[Cono Tangente]] sia un'approssimazione locale dell'insieme ammissibile. E se invece tentassimo di approssimare le funzioni vincolo tramite i loro gradienti? 
## Def
Sia $C \subseteq \mathbb{R}^n$ definito tramite una serie di disuguaglianze ed uguaglianze di funzioni differenziabili:
$$
C := \left\{  x \in \mathbb{R}^n \vert g_i(x)\ \leq 0,\, h_j(x)=0  \right\}
$$
con $i=1,\dots,m$ e $j = 1,\dots,p$.

Si dice _cono linearizzato_ dell'insieme $C$ nel punto $\overline x$ l'insieme:
$$
L_C(\overline x) := \left \{  x \in \mathbb{R}^n \vert \nabla g_i(x)\leq 0,\, \nabla h_j(x)=0  \right\}
$$
con $i \in I_0(\overline x)$.

Che _legame_ c'è tra questo ed il cono tangente? 

$$
T_C(\overline x) \subseteq L_C(\overline x)
$$
> in generale il cono linearizzato è più grande.

### Dim 
Facciamo vedere che se $d \in T_C(\overline x)$ allora $d \in L_C(\overline x)$.

essendo $d$ nel cono tangente, esiste la successione di punti ammissibili $x^k \to \overline x$, essendo ammissibili deve valore:
$$
g_i(x^k) \leq 0 \qquad \forall i
$$
$$
h_j(x^k) = 0 \qquad \forall j
$$
essendo differenziabili, espandiamole attorno al punto $\overline x$, anch'esso ammissibile:
$$
g_i(\overline x) + \nabla g(\overline x)^T(x^k-\overline x) + o(\Vert x^k-\overline x \Vert) \leq 0
$$
$$
h_j(\overline x) + \nabla h_j(\overline x)^T(x^k-\overline x) o(\Vert x^k-\overline x \Vert) = 0
$$
ma $x^k-\overline x = \tau^k d^k$. Consideriamo il caso di vincoli attivi
$$
\begin{cases}
\nabla g_i(\overline x)d^k + o(\Vert d^k\tau^k\Vert) \leq 0 \\

\nabla h_j(\overline x)d^k + o(\Vert d^k\tau^k\Vert) = 0 
\end{cases}
$$
dividendo per $\tau^k$ e passando al limite ottengo le disequazioni del cono linearizzato! $\square$

## Teorema
Se le funzioni $g_i,h_j$ sono affini, allora $T_C(\overline x) = L_C(\overline x)$.
### Dim
Si passa per le direzioni ammissibili, si fa vedere che se $d \in L_C(\overline x)$ allora $d$ è anche ammissibile e quindi è in $T_C(\overline x)$, dimostrando che $L_C(\overline x) \subseteq T_C(\overline x)$.

$$
\begin{cases}
g_i^T(\overline x + \lambda d)=g_i^T\overline x+ \lambda g_i^Td \leq b \quad i \in I_0(\overline x)\\
g_i^T(\overline x + \lambda d)=g_i^T\overline x+ \lambda g_i^Td \leq b \quad i \notin\\
h_j^T(\overline x + \lambda d)= h_j^T\overline x+ \lambda h_j^Td = b

\end{cases}
$$
se $d \in L_C(\overline x)$ allora  $d$ rispetta queste tre, per $\lambda \in [0,\overline \lambda]$, infatti la prima e terza sono sempre vere, l'unica che pone vincoli è la due, ma per lambda abbasatanza piccoli viene rispettata. $\square$
