# Regola di armijo
L'idea è ridurre lo step size abbastanza da far diminuire la funzione (sappiamo che per un $\alpha$ abbastanza piccolo la funzione decresce), senza però perdere troppo sulla velocità di convergenza. 
Definiamo la seguente regola:
Fissiamo 3 parametri scalari $s > 0$, $0<\sigma < 1$ e $0<\beta < 1$. 
$s$ è lo step iniziale, $\beta$ controlla quanto accorcio lo step dopo ogni tentativo, $\sigma$ richiede che la funzione diminuisca di almeno una certa soglia. 
Per decidere lo step al passo $k$ facciamo dei tentivi, indicizzati con $m$:
$$
\alpha^k = \beta^{m_k}s
$$
dove $m_k$ è il primo intero non negativo per cui vale la condizione:
$$
f(x^k) - f(x^k + \beta^ms d^k) \geq -\sigma \beta^m s\nabla f(x^k)^T d^k
$$
quindi si riduce lo step aumentando la potenza di $\beta$ in maniera da ottenere una diminuzione abbastanza grande.

Fintanto che $\nabla f(x^k) \cdot d < 0$ il metodo è ben definito, in un numero finiti di tentativi trova lo step size.

Uso Taylor a sinistra e divido per $\beta^ms$:
$$
\frac{o(\beta^m)\Vert d^k\Vert}{\beta^m} \geq (1-\sigma)\nabla f(x^k)^Td^k
$$
quindi per $m\to \infty$ si ha $\beta^m\to 0$, ed essendo il membro a destra minore di zero otteniamo mostra come esiste l'intero $m_k$. $\square$
## Convergenza
Dimostriamo come converga a punti stazionari per la procedura di Armijo e direzione [[Gradient Methods#Gradient related | gradient related]].
### Dim
Per assurdo sia $x^k \to \overline x$ e $\nabla f(\overline x) \neq 0$. Siccome $f(x^k)$ è una sequenza monotona non crescente, o diverge a $-\infty$ o converge. Per continuità $f(x^k)\to f(\overline x)$, Quindi:
$$
f(x^k) - f(x^{k+1}) \to 0
$$
Dalla regola di Armijo sappiamo che:
$$
f(x^k) - f(x^{k+1}) \leq -\sigma \alpha^k \nabla f(x^k)^T d^k
$$
ne deduciamo che:
$$
\alpha^k \nabla f(x^k)^T d^k \to 0
$$
siccome è _gradient related_, presa una sottosuccessione che converge a $\overline x$ vale la condizione:
$$
\limsup_{j\to\infty} \nabla f(x^{k_j})^T d^{k_j} < 0
$$

quindi $\alpha^k \to 0$. Ma dalla regola di Armijo, questo significa che da un certo step in poi deve avvenire almeno una riduzione del passo, ovvero:
$$
f(x^k)-f(x^k+\frac{\alpha^k}{\beta} d^k) < -\frac{\alpha^k}{\beta}\sigma \nabla f(x^k)^Td^k \qquad \forall k \geq \overline k
$$
dove $\alpha^k = \beta^{m_k}s$.
Introduciamo alcune variabili: 
$$p^k := \frac{d^k}{\Vert d^k \Vert}$$ovvero le direzioni normalizzate, e un passo riscalato: 
$$\overline \alpha^k := \frac{\alpha^k\Vert d^k \Vert}{\beta}
$$
notiamo una cosa sulle due nuove successioni introdotte:
1. siccome $d^k$ è limitata, $\overline \alpha^k \to 0$;
2. $\Vert p^k \Vert = 1$, quindi è contenuta in un compatto: esiste una sottosuccessione convergente:
$$
\lim_{k\to \infty,\, k \in K} p^k = \overline p
$$
Riscriviamo la disequazione precedente:
$$
f(x^k)-f(x^k+\overline \alpha^k p^k)< -\overline \alpha^k \sigma \nabla f(x^k)^T p^k
$$
Utilizziamo il teorema di Lagrange:
$$
-\nabla f(\xi^k)^Tp^k < -\sigma \nabla f(x^k)^Tp^k \qquad \xi^k \in [x^k,x^k+\overline \alpha^kp^k] 
$$
ora passiamo al limite, sempre la sottosuccessione $K$:
$$
-\nabla f(x^k)^T\overline p \leq -\sigma \nabla f(x^k)^T\overline p
$$
$$
0 \leq (1-\sigma)\nabla f(x^k)^T\overline p
$$
siccome $\sigma \in (0,1)$ 
$$
0 \leq \nabla f(x^k)^T\overline p
$$
Siamo giunti all'assurdo, infatti $d^k$ è per ipotesi Gradient Related, il che implica:
$$
\lim_{k\to\infty,\, k \in K} \frac{\nabla f(x^k)^Td^k}{\Vert d^k \Vert} \leq \frac{\limsup_{k\to\infty,\,k\in K} \nabla f(x^k)^Td^k}{\limsup_{k\to\infty,\,k\in K} \Vert d^k \Vert} < 0
$$
giungendo all'assurdo. $\square$

