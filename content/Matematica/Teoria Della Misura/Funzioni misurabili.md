# Mesurable functions
Una funzione $f : E \to F$ si dice misurabile se la preimmagine di un insieme misurabile è misurabile (ispirata da funzione continue in topologia). 
Ovvero: Sia $\mathcal{E} \subseteq 2^E$  e $\mathcal{F} \subseteq 2^F$  [[Sigma algebra]] dei rispettivi insiemi, $f$ è misurabile se $\forall A \in \mathcal{F}$  allora $f^{-1}(A) \in \mathcal{E}$ , rimaniamo nella sigma algebra del dominio (gli insiemi misurabili dove è definita una certa misura [[Misura]]). 

Questa definizione sarà utile per le capire quali funzioni sono Lebesgue integrabili [[Integrale di Lebesgue]] (spoiler devono essere misurabili).

## Osservazioni elementali
1. La preimmagine $f^{-1}$ _preserva le operazioni insiemistiche_. Segue dalle definzioni, estremamente utile.
2. Se una funzione è misurabile su un sottoinsieme della sigma algebra che la genera tutta, allora è misurabile, ovvero: sia $h : E \mapsto F$ e $\mathcal{C} \subseteq \mathcal{E}$ ed inoltre $\sigma(\mathcal{C}) = \mathcal{E}$. Allora se $\forall c \in \mathcal{C}$ vale $h^{-1}(c) \in \mathcal{F}$, segue che $h$ è $\mathcal{E}$-misurabile.
**Proof** considero l'insieme degli elementi dove è misurabile: $\mathcal{B} := \{ B \in \mathcal{E} \, : \, h^{-1}(B) \in \mathcal{F}\}$. Per ipotesi $\mathcal{C} \subseteq \mathcal{B}$. Mostrando che $\mathcal{B}$  è una sigma algebra (lo è perchè $h^{-1}$ preserva le operazioni insiemistiche), segue che:
$$
\sigma(\mathcal{C}) = \mathcal{E} \subseteq \sigma(\mathcal B) = \mathcal B
$$
quindi l'insieme dove è misurabile è proprio la sigma algebra di partenza. $\square$
**Esempio** Con funzioni $f : S \mapsto \mathbb R$ con la sigma algebra $\Sigma$ per $S$ e di Borel $\mathcal B$  per i reali, e il sottoinsieme base:
$$
\Pi := \{(-\infty,x] \, : \, x \in \mathbb{R}\} \qquad \mathcal B = \sigma(\Pi)
$$
quindi basta far vedere che gli insiemi sono misurabili:
$$
\{h \leq c\} :=\{ s \in S \, : \, h(s) \leq c\} \in \Sigma \qquad \forall c \in \mathbb R
$$
per concludere che $h$ è $\Sigma$-misurabile.

## Successione monotna di funzioni semplici
Sia $f$ una funzione misurabile non negativa, allora esiste una successioni di funzioni semplici $h_n$ tale che $h_n \uparrow f$.
### Dim 
Sfrutto le _funzioni scala_, definite:
$$
h_n(x) := 
\begin{cases}
n \text{ se } f(x) \geq n \\
\frac{k}{2^n} \text{ se } \frac{k}{2^n} \leq f(x) \leq \frac{k+1}{2^n}\\
\end{cases} 
\qquad 0 \leq k \leq n2^n -1
$$
è una funzione semplice, possiamo rappresentarla come:
$$
h_n(x) = \sum_{k=0}^{n2^n-1} \frac{k}{2^n} \mathbb{1}_{\frac{k}{2^n}\leq f(x) \leq \frac{k+1}{2^n}}(x) + n \mathbb{1}_{f(x) \geq n}(x)
$$
Gli insiemi delle funzioni caratteristiche sono misurabili, segue dalla misurabilità di $f$.

Facciamo vedere che $h_n \uparrow f$.
1. Se $f(x) = \infty$, $h_n(x) = n$, quindi $h_n(x) \uparrow f(x)$.
2. Se $f(x) < \infty$, allora esiste $n_0 \in \mathbb{N}$ tale che $f(x) < n_0$, consideriamo $n \geq n_0$,
per tutte le funzioni $h_n$ vale nel punto $x$:
$$
k \leq 2^n f(x) \leq k+1 \qquad 0 \leq k \leq n2^n-1
$$
ovvero $k = \lfloor 2^nf(x)\rfloor$, la parte intera, quindi
$$
h_n(x) = \frac{\lfloor 2^n f(x)\rfloor}{2^n}
$$
**remark** questa riscrittura della funzione scala è quella da ricordare!
ma vale per la parte intera di un numero reale $\lfloor x \rfloor \leq x < \lfloor x \rfloor +1$,  ovvero $\lfloor x \rfloor > x-1$,che nel nostro caso fornisce
$$
h_n(x) \leq f(x) \qquad h_n(x) > \frac{2^nf(x)-1}{2^n} = f(x)-\frac{1}{2^n} 
$$

quindi:
$$
h_n(x) \leq f(x) < h_n(x) + \frac{1}{2^n} \qquad f(x) < n
$$
che implica che $h_n(x) \to f(x)$. Facciamo vedere la monotonia, (per il caso $f(x)=\infty$ è già stato dimostrato).

1. Caso che $n  \leq n+1 \leq f(x)$, allora $h_n(x) = n < h_{n+1}(x) = n+1$.
2.  Caso $n \leq f(x) \leq n+1$, allora $h_n(x)=n$ e $h_{n+1}(x) = \frac{\lfloor 2^{n+1}f(x)\rfloor}{2^{n+1}}$
$$
h_{n+1}(x) = \frac{\lfloor 2^{n+1}f(x)\rfloor}{2^{n+1}} \geq \frac{\lfloor 2^{n+1}n\rfloor}{2^{n+1}} = n = h_n(x)
$$
3. Caso $f(x) \leq n < n+1$:
$$
h_{n+1}(x) = \frac{\lfloor 2^{n+1}f(x)\rfloor}{2^{n+1}} \geq \frac{\lfloor 2^{n+1}f(x)\rfloor}{2^{n+1}}
$$
Segue dalla proprietà $n\lfloor x \rfloor \leq \lfloor nx \rfloor$ con $n \in \mathbb{N}$.
$$
x = \lfloor x \rfloor + r \qquad 0 \leq r < 1
$$
$$
\lfloor nx \rfloor = n \lfloor x \rfloor + \lfloor nr \rfloor \geq n \lfloor x \rfloor  
$$
quindi:
$$
h_{n+1}(x) - h_n(x) = \frac{\lfloor 2^{n+1}f(x)\rfloor - 2\lfloor 2^n f(x) \rfloor}{2^{n+1}} \geq 0
$$
provando che $h_n \uparrow f$. $\square$

### Lemma di unicità dell'integrale
Indipendenza della successione. Siano $h_n \uparrow f$ e $g_n \uparrow f$. Allora:
$$
\lim_n I(h_n) = \lim_n I(g_h) = I(f)
$$
### Dim
Prima dimostriamo che se $g \leq \lim_n h_n = f$ con $g$ semplice, allora $I(g) \leq \lim_n I(h_n) = I(f)$.

1. Supponiamo $g = c\mathbb{1}_E(x)$, con $E$ misurabile.
Se $c=0$, vale banalmente dal fatto che $h_n$ sono non negative, quindi $I(g) =0 \leq \lim_n I(h_n)$.
Assumiamo $c > 0$.

Definiamo una nuova funzione semplice:
$$
\mathbb{1}_E(x) \cdot h_n(x) \leq h_n(x)
$$
continua a valere $g \leq \lim_n \mathbb{1}_E(x)h_n(x)$.

Possiamo rappresentare la nuova funzione semplice come:
$$
\sum_{i=1}^N a_i \mathbb{1}_{A_i \cap E}(x)
$$
(prodotto di indicatrici è l'indicatrice dell'intersezione).

Fissiamo $0 < \epsilon < c$, definiamo una successioni di insiemi:
$$
C_n := \{ x \in E \,:\, h_n(x) \geq c-\epsilon\}
$$
siccome $h_n(x)$ è crescente, lo sono anche gli insiemi $A_n \subseteq A_{n+1}$.
Inoltre $\cup_n A_n \subseteq E$, dalla definizione. Ma vale anche l'inclusione inversa, infatti se $x \in E$,
$g(x) = c$ e per ipotesi $g \leq \lim_n h_n$ quindi $x \in C_n$ per tutti gli $n$ maggiori di un certo $M$. 
Banalmente vale $A_n \subseteq E$. quindi:
$$
I(h_n) \geq I(\mathbb{1}_E h_n) \geq I(\mathbb{1}_{A_n} h_n) \geq (c-\epsilon) \mu(A_n)
$$
passando al limite in $n$, sfruttando la [[Continuity of mesure]] per successioni monotone, si ha:
$$
c\mu(E) -\epsilon \mu(E) \leq \lim_n I(h_n) = I(f)
$$
ma $I(g) = c\mu(E)$. quindi:
$$
I(g) \leq \lim_n I(h_n) = I(f)
$$
2. estendiamo ora a $g$ funzione semplice generica, uso la linearità per funzioni semplici:
$$
I(g) = \sum_{i=1}^N c_i \mu(E_i) \leq \sum_{i=1}^N \lim_n I(\mathbb{1}_{E_i} h_n)
$$
la somma è finita, posso scambiare:
$$
 \lim_n \sum_{i=1}^N I(\mathbb{1}_{E_i} h_n) = \lim_n I\left(\sum_{i=1}^N \mathbb{1}_{E_i}h_n \right) = \lim_nI(h_n)
$$
Segue l'indipendenza dell'integrale dalla particolare successione di funzioni semplici:
$$
I(g_k) \leq \lim_n I(h_n) = I(f)
$$
quindi vale anche per il limite in $k \to \infty$, ovvero:
$$
I(f) = \lim_k I(g_k) \leq \lim_n I(h_n) = I(f)
$$
# Proprietà
1. **Linearità dell'integrale di Lebesgue**

_Per funzioni semplici_
Siano $f,g \in SF^+$, funzioni semplici non negative:
$$
I(f+g) = I(f)+I(g)
$$
#### Dim 
$$
f = \sum_{i=1}^N a_i \mathbb{1}_{A_i}(x) \qquad g = \sum_{i=1}^M b_i \mathbb{1}_{B_i}(x)
$$
siccome $A_i$ e $B_i$ partizionano $\Omega$, ottengo un'altra rapprestazione valida:
$$
A_i' := \bigcup_{j=1}^M A_i \cap B_i \qquad B_i' := \bigcup_{j=1}^N B_i \cap A_j
$$
$$
f = \sum_{i=1}^N \sum_{j=1}^M a_i \mathbb{1}_{A_i \cap B_j} \qquad g = \sum_{i=1}^M \sum_{j=1}^N b_i \mathbb{1}_{B_i \cap A_j}
$$
Grazie a questo trick la somma si scrive in modo comodo:
$$
f+g = \sum_{i=1}^N \sum_{j=1}^M (a_i+b_j) \mathbb{1}_{A_i \cap B_j}
$$
e l'integrale vale per definizione:
$$
I(f+g) = \sum_{i=1}^N \sum_{j=1}^M (a_i+b_j) \mu(A_i \cap B_j)
$$
$$
= \sum_{i=1}^N a_i \sum_{j=1}^M \mu(A_i \cap B_j) + \sum_{j=1}^M b_j \sum_{i=1}^N \mu(A_i \cap B_j)
$$
siccome sono partizioni di $\Omega$, le sommatorie interne diventano semplicemente la misura dell'insieme fissato dalla prima sommatoria:
$$
= \sum_{i=1}^N a_i \mu(A_i) + \sum_{j=1}^M b_j \mu(B_j) = I(f)+I(g)
$$
L'omogeneità segue banalmente, porto fuori dalla sommatoria la costante. $\square$

_Per funzioni misurabili non negative_

Prendiamo $f_n \uparrow f$ e $g_n \uparrow g$ successioni di funzioni semplici che convergno a due funzioni misurabili non negative. Sappiamo che $I(g_n + f_n) = I(g_n) + I(f_n)$. Inoltre è evitente che 
$(g_n+f_n) \uparrow (g+f)$. Quindi:
$$
I(f+g) = \lim_n I(g_n + f_n) = \lim_n I(g_n) + \lim_n I(f_n) = I(g) + I(f) \quad \square
$$





