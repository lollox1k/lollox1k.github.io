# Step costante
La regola più semplice, passo costante:
$$
x^{k+1} = x^k + \alpha^k d^k \qquad \alpha^k = s
$$
## Convergenza 
Intuitivamente, se il passo $s$ è troppo grande, il metodo diverge, se è troppo piccolo sarà lento. Troviamo una condizione, legata alla $L$-continuità della funzione, che ci assicura convergenza.

Applicando il [[Descent Lemma]] per stimare la differenza della funzione in due passi $x^k$ e $x^{k+1}$ otteniamo:
$$
f(x^{k+1})-f(x^k) \leq \nabla f(x^k)(x^{k+1}-x^k) + \frac{L}{2}\Vert x^{k+1}-x^k\Vert^2
$$
ma $x^{k+1}-x^k = \alpha^kd^k$ 
$$
f(x^{k+1})-f(x^k)\leq \alpha^k\nabla f(x^k)d^k + \frac{L\alpha_k^2}{2}\Vert d^k \Vert^2 
$$
richiediamo che il passo $\alpha^k$ sia compreso tra:
$$
\epsilon \leq \alpha^k \leq (2-\epsilon)\frac{\vert \nabla f(x^k)^Td^k\vert}{L\Vert d^k \Vert^2}
$$
con $\epsilon > 0$.

nel caso più semplice di _steepest descent_, ovvero $d^k = -\nabla f(x^k)$ e otteniamo:
$$
\epsilon \leq\alpha^k \leq \frac{2-\epsilon}{L}
$$

Facciamo vedere come con questi limiti $x^k$ converge ad un punto stazionario. Riscrivendo il lato destro della disuguaglianza ottenuta tramite il Desceng Lemma:
$$
f(x^k)-f(x^{k+1})\leq \alpha^k\left[ \frac{\alpha^kL}{2}\Vert d^k\Vert -\vert \nabla f(x^k)^Td^k \vert  \right]
$$
ma l'upper bound di $\alpha^k$ impliche che:
$$
\frac{\alpha^kL}{2}\Vert d^k\Vert -\vert \nabla f(x^k)^Td^k \vert  \leq -\frac{\epsilon}{2}\vert\nabla f(x^k)^Td^k\vert
$$
ed usando $\alpha^k \geq \epsilon$ otteniamo:
$$
f(x^{k+1})-f(x^k)\geq \frac{\epsilon^2}{2}\vert \nabla f(x^k)^Td^k\vert \geq 0
$$
prendendo una sottosuccessione che converge ad un punto non stazionario $\overline x$, si ottiene:
$$
\vert \nabla f(x^k)^Td^k| \to 0
$$
che va contro l'ipotesi di gradient related. $\square$


