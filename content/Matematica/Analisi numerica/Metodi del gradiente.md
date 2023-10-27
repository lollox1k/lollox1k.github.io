# Metodi del gradiente per sistemi lineari

Vediamo ora come utilizzare i [[Gradient Methods]] per risolvere sistemi lineari con matrici simmetriche definite positive, associando ad essi una forma quadratica da minimizzare. 

Assumiamo che il sistema da risolvere $Ax=b$ sia *reale*.
## Forma quadratica associata
Consideriamo la funzione quadratica $\Phi : \mathbb{R}^n \mapsto \mathbb{R}$:
$$
\Phi(x) = \frac{1}{2}x^TAx -x^Tb
$$
dove $A \in \mathbb{R}^{n\times n}$ è una matrice _simmetrica_ e _definita positiva_.
Scelta in maniera tale che il suo gradiente:
$$
\nabla \Phi(x) = Ax-b = -r(x)
$$
dove $r(x)$ è il residuo del sistema assegnato. L'ipotesi sulla matrice $A$ garantiscono il punto $x^* \in \mathbb{R}^n$ tale che $\nabla \Phi(x^*)=0$ risulta essere un minimo globale di $\Phi$, infatti:
$$
\Phi(y) = \Phi(x+(y-x)) = \frac{1}{2}x^TAx + \frac{1}{2}(y-x)^TA(y-x) +\frac{1}{2}x^TA(y-x) + \frac{1}{2}(y-x)^TAx -x^Tb -(y-x)^Tb
$$
$$
= \frac{1}{2}x^TAx + \frac{1}{2}(y-x)^TA(y-x) \geq \frac{1}{2}x^TAx
$$
se la matrice $A$ è definita positiva.

La precedente relazione si può esprimre in termini della [[norma dell'energia]]:
$$
\frac{1}{2}\Vert y-x\Vert_A^2 = \Phi(y) - \Phi(x)
$$

## Scelta ottimale del passo

In generale usare [[Minimization rule]] non è fattible, in quanto si deve risolvere un altro problema di minimizzazzione unidimensionale. Tuttavia, ora siamo nel caso particolare di funzione obbiettivo quadratica, il che consente di calcolare analiticamente l'$\alpha_k$ ottimale.

**Proposizione** Al $k-$passo di un metodo del gradiente, applicato ad una funzione quadratica definita positiva, il passo ottimale, ovvero che soddisfa la minimization rule:
$$
\alpha_k = argmin_\alpha \Phi(x^k+\alpha p^k)
$$
è dato da:
$$
\alpha_k = \frac{{r^k}^Tp^k }{{p^k}^T A p^k }
$$
inoltre, se $p^k$ è una _direzione di decrescita_, ovvero ${p^k}^T \nabla \Phi(x^k) <0$, si ha che $\alpha_k > 0$.

**Dimostrazione** Risolviamo il problema di ottimizzazzione unidimensionale lungo la retta $y(\alpha)=x^k +\alpha P^k$:
$$
\frac{\partial\Phi(y(\alpha))}{\partial\alpha} = \sum_{i=1}^n \frac{\partial\Phi}{\partial y_i} \frac{dy_i}{d\alpha} = \nabla\Phi(y(\alpha))^Ty'(\alpha) = (Ay(\alpha)-b)^Tp^k 
$$
$$
x^TA^Tp^k+\alpha p^TA^Tp^k -b^Tp^k = 0
$$
$$
\alpha = \frac{b^Tp^k-x^TA^Tp^k }{p^TA^Tp^k } = \frac{(b^T-x^TA)p^k }{{p^k}^TAp^k } = \frac{{r^k}^Tp^k }{{p^k}^TAp^k }
$$
dove abbiamo usato la simmetria di $A$ nell'ultimo uguaglianza. 
Se $p^k$ è direzione di discesa,Il numeratore è positivo, anche il denomitatore essendo  $A$ definita positiva, dunque $\alpha_k>0$. $\square$

Vale la seguente caratterizzazione legata alla norma dell'energia.

**Proposizione** Minimizzare la funzione energia $\Phi$ lungo la retta $y(\alpha)=x^k+\alpha p^k$ equivale a minimizzare la norma dell'energia dell'errore $e^{k+1}=x-x^{k+1}$, dove $x$ è la solizione del sistema.

**Dimostrazione** scriviamo esplicitamente cosa stiamo minimizzando:
$$
\Phi(y(\alpha)) = \frac{1}{2}y(\alpha)^TAy(\alpha) + y(\alpha)^TAx
$$
dove ho usato il fatto che $b=Ax$. Scriviamo esplicitamente la norma dell'energia dell'errore:
$$
\Vert e^{k+1}\Vert_A^2 = (x-x^{k+1})^TA(x-x^{k+1}) 
$$
$$
(x-y(\alpha))^TA(x-y(\alpha)) = x^TAx -x^TAy(\alpha) -y(\alpha)Ax +y(\alpha^T)Ay(\alpha) = x^TAx -2y(\alpha)^TAx + y(\alpha)^TAy(\alpha)
$$
dove abbiamo usato il fatto che $A$ è hermitiana essendo simmetrica.
Apparte il primo termine, il resto si può riscrivere come:
$$
\Vert e^{k+1}\Vert_A^2 = x^TAx +2\Phi(y(\alpha))
$$
apparte il primo termine costante, noto che minimizzare $\Phi(y(\alpha))$ è equivalente a minimizzare la norma dell'energia dell'errore. $\square$

**Lemma di ortogonalità** Vale il seguente risultato di ortogonalità tra i residui: ${r^{k+1}}^Tp^k = 0$, ovvero il residuo al passo $k+1$ di un metodo del gradiente è ortogonale alla direzione $p^k$.

**Dimostrazione** 
$$
{r^{(k+1)}}^T p^k = (b-Ax^{k+1})^Tp^k = (b-A(x^k+\alpha_kp^k))^Tp^k = b^Tp^k -xA^Tp^k -\alpha_k{p^k}^TA^Tp^k
$$
usando $\alpha_k$ ottimale:
$$
b^Tp^k -xA^Tp^k -\left(\frac{{r^k}^Tp^k }{{p^k}^T A p^k }\right){p^k}^TA^Tp^k = 0
$$
$\square$.

## Steepest descent (SD)

La scelta più ovvia per la direzione di discesa è proprio il residuo $r^k$, che è proprio meno il gradiente:
$$
p^k=r^k
$$
da cui il passo ottimo:
$$
\alpha_k = \frac{{r^k}^Tr^k }{{r^k}^TAr^k }
$$
si tratta dunque di un _metodo di Richardson non stazionario e non precondizionato_. 
Ovviamente continua a valere il lemma di ortogonalità, in questo caso le direzioni sono tutte ortogonali tra loro.

### Errore 

Si può effettuare un bound sull'errore ad ogni passo, in termini del numero di condizionamento di $A$:
$$
\Vert e^{(k+1)}\Vert_A \leq \frac{K_2(A)-1}{K_2(A)+1}\Vert e^k \Vert \leq \left(\frac{K_2(A)-1}{K_2(A)+1}\right)^{k+1}\Vert e^0 \Vert  
$$


**Dimostrazione**
Sia $x^k$ la soluzione generata al passo $k$ dal metodo del gradiente e ${x_R}^{k+1}$ il vettore generato da un passo del [[Metodo di Richardson stazionario]] non precondizionato (pongo $P=I$) a parametro ottimale, ovvero ${x_R}^{k+1} = x^k +\alpha_{opt} r^k$. Ma per definizione abbiamo scelto un $\alpha_k$ che minimizza la $A$-norma dell'energia al passo $k$, dunque:
$$
\Vert e^{k+1}\Vert_A \leq \Vert e^{k+1}_R\Vert_A
$$
e la tesi segue. $\square$


