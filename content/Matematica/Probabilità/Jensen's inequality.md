## Jensen's inequality
Sia $f$ una funzione convessa, $\lambda_i \in [0,1]$ t.c. $\sum_i \lambda_i = 1$, allora:
$$
f(\sum_i \lambda_ix_i) \leq \sum_i\lambda_if(x_i)
$$
**Conseguenze**
- $f(E[X])  \leq E[f(X)]$
- media aritmetica $\geq$ media geometrica

**Dim**
per induzione. Il caso $n=2$ segue dalla definizione di [[Funzioni convesse| funzione convessa]].
Supponiamo sia vera per $n$. Motriamo che vale per $n+1$:
$$
f(\sum_i^{n+1}\lambda_i x_i) = f(\sum_i^n \lambda_i x_i + \lambda_{n+1}x_{n+1})
$$
ora che abbiamo separato in due elementi, vorremmo applicare la convessità per due punti, abbiamo bisogno di un coefficiente che moltiplici il primo addendo tale che sommato con $\lambda_{n+1}$ faccia $1$. Basta dividere e dividere per $1-\lambda_{n+1}$. Supponiamo infatti che valga $\lambda_{n+1} \neq 1$, infatti se vale uno la disuguaglianza vale banalmente (è un'uguaglianza). Possiamo applicare la definzinizione di funzione convessa:
$$
f((1-\lambda_{n+1})\sum_i^n \frac{\lambda_i}{1-\lambda_{n+1}} x_i + \lambda_{n+1}x_{n+1}) \leq (1-\lambda_{n+1})f(\sum_i^n \frac{\lambda_i}{1-\lambda_{n+1}} x_i) + \lambda_{n+1}f(x_{n+1})
$$
Possiamo usare  l'ipotesi induttiva, infatti vale:
$$
\sum_i^n \frac{\lambda_i}{1-\lambda_{n+1}} = 1
$$e maggiorare il tutto con:
$$
\leq (1-\lambda_{n+1}) \sum_i^n\frac{\lambda_i}{(1-\lambda_{n+1})}f(x_i) + \lambda_{n+1}f(x_{n+1}) = \sum_i^{n+1} \lambda_i f(x_i)
$$
e raccogliere. $QED$
