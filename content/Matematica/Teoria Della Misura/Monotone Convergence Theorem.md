# Monotone Convergence Theorem
Sia $(f_n)_{n\geq 1}$ una successione di funzioni misurabili non negative $f \in m\Sigma^+$ (spazio misurabile $(S,\Sigma)$), tali che $f_n \uparrow f$. Allora:
$$
\mu(f_n) \uparrow \mu(f) \leq \infty
$$
ovvero
$$
\int_S f_n(x) d\mu(s) \uparrow \int_S f(x)d\mu(x)
$$
## Proof (Landim)
L'idea è trovare una successione di funzioni semplici che converga ad $f$, scegliendo funzioni semplici dalle $g_{nm}\uparrow f_n$. Dalla monotonia dell'integrale segue la tesi.

Per ipotesi, $f_n$ sono misurabili, dunque esistono delle successioni di funzioni semplici che convergono monotonamente ad esse:
$$
\begin{align}
& g_{11}, \,g_{12}, \,g_{13},\,\dots f_1 \\
& g_{21}, \,g_{22},\, g_{23}, \,\dots f_2 \\
& g_{31}, \, g_{32},\, g_{33},\, \dots f_3 \\
\end{align}
$$
definisco la successione $g_k := \max_{i \leq k} g_{ik}$. _Fisso la $k$ colonna, scelgo il max_
Facciamo vedere le seguenti proprietà:
1. Sono funzioni semplici. Ovvio dalla definizione. 
2. $g_k$ è monotona non descrescente: banale dalla definizione, infatti ogni volta prendo il max su funzioni che sono più grandi o uguali a quelle dove ho preso il max la volta prima.
3. $g_k \uparrow f$. L'osservazione cruciale è che $g_k \leq f_k$, ma questo è facile e segue direttamente dalla definizione e dal fatto che anche $f_k$ è una sequenza monotona non decrescente. Quindi:
$$
g_{ik} \leq g_k \leq f_k \leq f
$$
prendendo il limite per $i \to \infty$ ottengo:
$$
f_k \leq g_k \leq f_k \leq f
$$
e prendendo il limite per $k \to \infty$ ottengo che $g_k \uparrow f$.
Quindi, dalla definizione dell'[[Integrale di Lebesgue]]:
$$
\int f d\mu = \lim_n \int g_n d\mu
$$
Per dimostrare la tesi, prima osserviamo che un verso segue banalmente dalla monotonia dell'integrale di Lebesgue, infatti $f_n \leq f$ implica
$$
\int f_n d\mu \leq \int f d\mu \qquad \forall n
$$
quindi anche per il limsup:
$$
\limsup_n \int f_n d\mu\leq \int f d \mu
$$
Per l'altro verso sfruttiamo l'osservazione che $g_k \leq f_k$, ancora una volta dalla monotonia:
$$
\int f d\mu = \lim_n \int g_n d\mu \leq \liminf_n \int f_n d \mu 
$$
questo dimostra la tesi. $\square$

### Osservazione
Posso estendere il teorema anche se la sequenza $f_n$ è limitata inferiormente da una funzione misurabile $g$. Basta applicare il teorema alla sequenza non negativa $f_n - g \geq 0$.



### Proof (Williams)
Prima necessitiamo di qualche lemma.

### Lemma 1
Limite di successioni doppiamente monotone. 
Sia $(y_n^r)_{n,r \geq 1}$ una sequenza di numeri in $[0,\infty]$ doppiamente monotona, ovvero fissando $r$ monotona in $n$, e viceversa.

Allora il limite doppio esiste ed è indipendente dall'ordine:
$$
y^r := \lim_n y_n^r \qquad y_n := \lim_r y_n^r
$$
i limiti esistono per monotonia, il risultato è:
$$
y_\infty := \lim_n y^r = \lim_r y_n
$$
### Proof
Siccome lavoriamo nella semiretta realte estesa, è ben definito il sup:
$$
y^* := \sup_{r,n} y_n^r, \quad y^* \in [0,\infty]
$$
Scegliamo $\epsilon > 0$, allora $\exists \overline r, \overline n$ tali che $\forall r \geq \overline r, \, n \geq \overline n$ si ha:
$$
y^* - \epsilon \leq y_n^r \leq y^* + \epsilon
$$
che è la definizione di limite due dimensionale, quindi:
$$
\lim_{n,r} y_n^r = y^*
$$
Questo implica che i due limite coincidano. Fissiamo $r$, per la monotonia esiste il limite
$$
\lim_n y_n^r =: y^r
$$
Facciamo vedere che:
$$
\lim_r y^r = y^*
$$
sia $\epsilon > 0$, se scelgo il $N := max(\overline r, \overline n)$  allora ho per $n,r \geq N$
$$
\vert y_n^r - y^* \vert \leq \epsilon
$$
allo stesso modo esiste un $M$ tale che $\forall n \geq M$
$$
\vert y_n^r - y^r \vert \leq \epsilon
$$
mettendo insieme i pezzi, scegliendo il massimo tra $N,M$:
$$
\vert y^r - y^* \vert \leq \vert y^r - y_n^r \vert + \vert y_n^r - y^* \vert \leq 2\epsilon
$$
in maniera analoga per il limite di $y_n$. $\square$

### Lemma 2
Sia $A \in \Sigma$, e la successione di funzioni semplici non negative $h_n \in SF^+$ tale che $h_n \uparrow I_A$.
Allora $\mu(h_n) \uparrow \mu(A)$. 
### Proof
Dalla monotonia segue che $\mu(h_n) \leq \mu(A)$. Facciamo vedere che:
$$
\liminf_n \mu(h_n) \geq \mu(A) 
$$
che implica l'uguaglianza.
Definiamo gli insiemi (misurabili) 
$$
A_n := \{s \in A \,:\, h_n(s) > 1- \epsilon\}
$$
è evidente che $A_n \uparrow A$. Quindi per [[Continuity of mesure]]:
$$
\lim_n \mu(A_n) = \mu(A)
$$
per costruzione degli $A_n$ vale:
$$
(1-\epsilon)I_{A_n} \leq h_n
$$
quindi:
$$
(1-\epsilon)\mu(A_n) \leq \mu(h_n)
$$
quindi anche per il $\liminf$. $\square$



Costruiamo un successioni di funzioni semplici che converge monotonamente $f_r \uparrow f$. 
Definiamo la r-esima funzione scala:
$$
\alpha_r(x) := 
\begin{cases}
0 \text{ if } x=0\\
(i-1)2^{-r} \text{ if } (i-1)2^{-r} < x \leq i2^{-r} \quad (i \in \mathbb{N})\\
r \text{ if } x > r\\
\end{cases}
$$
Sia $f_n^{(r)} := \alpha_r(f_n)$, e $f^{(r)} := \alpha_r(f)$. Siccome $\alpha_r$ è continua da sinistra, $f_n^{(r)} \uparrow f^{(r)}$. Siccome $\alpha_r(x) \uparrow x$ $\forall x$, $f_n^{(r)} \uparrow f_n$ quando $r \to \infty$.