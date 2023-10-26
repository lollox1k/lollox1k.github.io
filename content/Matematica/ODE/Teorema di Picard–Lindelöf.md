Utile teorema che mostra esistenza ed unicità della soluzione di un problema di Cauchy, con ipotesi ragionevoli.

## Teorema
Sia dato il problema di Cauchy
$$
\begin{cases} y' = f(t,y) \\ y(t_0) = y_0\end{cases}
$$
Se la funzione $f(t,y)$ è continua in $t$ e Lipshitz continua in $y$, allora esiste un insieme $[t_0-a, t_0+a]\times[y_0-b, y_0+b] \subset \mathbb{R}^n$ dove la soluzione esiste ed è unica.

### Dim 
Idea chiave: costruire una successione che converge alla soluzione. Questa successione è ottenuta tramite l'applicazione ripetuta di un funzionale integrale che è una  contrazione nello spazio metrico delle funzioni continue in un certo intorno, per il [[Teorema di Banach-Caccioppoli]] converge ed è unica la funzione limite.
### Serie di Picard
Successione di funzioni definita per ricorrenza:
$$
\begin{cases}
y_0 = y(t_0) \\
y_{n+1} = \int_{t_0}^t f(s,y_n)ds + y(t_0) 
\end{cases}
$$

#### Osservazioni 
Posso vedere la definizione come un _funzionale integrale_ $T : y_n \mapsto y_{n+1}$. 
> il punto fisso di questo funzionale è la soluzione della ODE

Infatti integrando il problema di Cauchy tra $t$ e $t_0$:
$$
y(t)-y(t_0) = \int_{t_0}^t f(t,y(y))dt
$$
Facciamo vedere che il funzionale $T$ è una contrazione nello spazio metrico delle funzioni continue in un interno del "punto iniziale" $(t_0,y_0)$, sotto opportune ipotesi.

Fissiamo il nostro spazio metrico:
1. scegliamo le funzioni continue da un intorno del tempo iniziale $I_a = [t_0-a, t_0+a]$ e dei valori iniziali $B_b = [y_0-b, y_0+b]$.
2. la metrica indotta dalla norma del sup: 
$$
||\phi||_{\infty} = \sup_{t \in I} |\phi(t)|
$$
Facciamo vedere che il funzionale è ben definito: deve mappare le funzioni continue nella palla di raggio $b$ centrata in $y_0$ in se stesso. 
- La continuità è ovvia, essendo un funzionale integrale.
- Lo spazio metrico non è vuoto, infatti $y_0 \in B$.
Consideriamo una funzione $\phi \in B_b(y_0)$, applichiamo il funzionale e calcoliamo la distanza con il centro della palla $y_0$:
$$
||T(\phi)-y_0||_{\infty} = \sup_{t \in I}\Big|\int_{t_0}^t f(t,\phi(t))dt \Big| \leq \sup_{t\in I} \int_{t_0}^t | f(t,\phi)dt| \leq M | t-t_0| = Ma
$$
Abbiamo maggiorato $|f(t,\phi)$| con $M = \sup_{(t,\phi)\in I\times B} |f(t,\phi)|$ con il sup. 
_Abbiamo richiesto che $f(t,\phi)$ sia limitata nel rettangolo $I_a\times B_b$ _.

Quindi $T$ è una contrazione se $Ma \leq b$ ovvero:
$$
a \leq \frac{b}{M}
$$
Dimostriamo che è una contrazione, ovvero $\forall \phi_1,\phi_2 \in B$:
$$
|| T\phi_1 - T\phi_2||\leq k||\phi_1-\phi_2|| 
$$
con $k \in [0,1)$.

$$
||\int_{t_0}^t f(s,\phi_1) - f(s,\phi_2) ds || \leq \int_{t_0}^{t'} |f(s,\phi_1)-f(s,\phi_2)|ds \leq L \int_{t_0}^{t'} ||\phi_1-\phi_2||ds \leq La||\phi_1-\phi_2||
$$
$t'$ è il tempo che massimizza il primo membro. Abbiamo assunto che esista la maggiorazione:
$$
\sup_{t \in I}|f(t,\phi_1(t))-f(t,\phi_2(t))| \leq L ||\phi_1-\phi_2||
$$
ovvero che _f sia Lipschitz rispetto alla $\phi$_ con costante $L$ con la norma del sup (è praticamente un upper bound uniforme per ogni tempo!).

Affinché sia una contrazione $La \in [0,1)$ quindi:
$$
a < \frac{1}{L}
$$
### Recap
Abbiamo visto che il funzionale $T$ è ben definito se $a \leq \frac{b}{M}$, dove $b$ è il raggio della palla nel dominio delle soluzioni, centrato nel valore iniziale, ed $M$ il sup della funzione $f$.

Inoltre, affinché $T$ sia una contrazione $a < \frac{1}{L}$ dove $L$ è la costante di $Lipshitz$ della $f$ rispetto alla $y$.

Quindi scegliendo $a = \min\{\frac{b}{M}, \frac{1}{L}\}$ possiamo applicare il teorema delle contrazioni, e avere:
- esistenza
- unicità
della soluzione/punto fisso! $QED$.

### Unicità globale 
Il teorema ci assicura che finchè siamo nel rettanglo $I_a \times B_b$ con $a$ scelto di consguenza, la solzione è esiste ed è unica. Fuori che succede? Se continua ad esistere è possibile perdere l'unicità? E' possibile che la soluzione nel rettangolo si divida in più soluzioni fuori?

Supponiamo di avere due funzioni soluzioni $\phi$ e $\phi'$, siccome risolvono lo stesso problema di Cauchy, entrambe sono punti fissi del funzionale integrale. Calcoliamo il modulo della loro differenza:

$$
|\phi(t)-\phi'(t)| = |\int_{t_0}^t f(s,\phi)-f(s,\phi')ds | \leq \int_{t_0}^t | f(s,\phi)-f(s,\phi')| ds \leq L\int_{t_0}^t |\phi(s)-\phi'(s)|ds
$$
dove abbiamo usato la Lipshitzianità di $f$ rispetto alla seconda variabile. 
Possiamo applicare il [[Lemma di Gronwall]], con la costante $c=0$. Ma questo implica:
$$
|\phi(t)-\phi'(t)| \leq 0 \qquad \forall t \leq t_0
$$
quindi anche per $t>a$ all'esterno dell'intervallo $I_a$. 

