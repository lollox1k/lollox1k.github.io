# Minimization rule
## Unlimited
Scelgo lo step size $\alpha^k$ in maniera da minimizzare il valore della funzione lungo la semiretta:
$$
x^{k+1} = x^k + \alpha^k d^k \qquad \alpha^k = \min_{\alpha \in [0,\infty)} f(x^k + \alpha d^k)
$$
Si deve quindi risolvere un problema di minimizzazzione su un insieme illimitato! Numericamente è più fattibile implementare la versione limitata
## Limited
Si introduce una costante positiva $s$, ci si limita ad $\alpha \in [0,s]$.