# Condizioni duali
Si ottengono esprimendo il [[Cono Tangente]] con il [[Cono linearizzato]], come abbiamo visto questo non è sempre vero, quando è possibile questa condizione viene detta _condizione di Abadie_: $T_C(\overline x) = L_C(\overline x)$.

Si usa poi uno dei teoremi dell'alternativa in particolare una variante del [[Lemma di Farkas#Corollario]].

## Teorema 
Sia dato il problema di ottimizzazzione $MIN(C,f)$ dove l'insieme $C$ è definito da un sistema di disequazioni ed equazioni $g_i(x)\leq 0$ e $h_j(x)=0$, e $f,g,h$ funzioni differenziabili. 
Supponiamo che valgano le condizioni di Abadie, allora una condizione necessaria affinché $\overline x \in C$ sia un minimo locale è data da:
$$
\nabla f(\overline x) + \nabla g_i(\overline x)^T \lambda + \nabla h_j(\overline x)^T \mu = 0
$$
con $\lambda \geq 0$ e $i \in I_0(\overline x)$.
### Dim 
L'insieme di disuguaglianze che definiscono il cono linearizzato e la [[Condizioni di Ottimalità Primali]]
$$
\begin{cases}
\nabla g_i^Td \leq 0 \\
\nabla h_j^Td = 0 \\
\nabla f^Td \geq 0
\end{cases}
$$
nego il sistema passando alla complementare dell'ultima e moltiplico per meno uno:
$$
\begin{cases}
\nabla g_i^Td \leq 0 \\
\nabla h_j^Td = 0 \\
-\nabla f^Td > 0
\end{cases}
$$
Passo al sistema alternativo per ottengere
$$
\nabla f + \nabla g_i^T\lambda + \nabla h_j^T \mu = 0, \qquad \lambda \geq 0
$$
con $i \in I_0(\overline x)$. Ovviamente dobbiamo ricordarci che $\overline x \in C$ quindi devono valere anche:
$$
g_i(\overline x)\leq 0, \qquad h_j(\overline x)=0
$$
$\square$

> Sono una generalizzazio dei moltiplicatori di Lagrange.