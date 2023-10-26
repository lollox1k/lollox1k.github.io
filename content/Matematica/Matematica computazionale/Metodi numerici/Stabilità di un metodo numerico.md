>If a problem in differential equations is well-posed, then, by definition, the solution u depends continuously on the data f. On the discrete level, this continuous dependence is called stability

 [[Metodi numerici]]
L'idea è che se perturbo la condizione iniziale, la soluzione numerica non si allontana troppo da quella iniziale, come fa la soluzione analitica, dipendendo con continuità dai valori iniziali. 

Dipende anche dal problema studiato: lo stesso metodo può risultare stabile o instabile per problemi diversi.

Vogliamo quantificare quanto si allontana la soluzione numerica rispetto alla perturbazione, in maniera molto naturale definiamo la _costante di stabilità_ come il rapporto di queste quantità:
$$
C(h)_{stab} = \frac{||\widetilde{y}-y||}{|\epsilon|}
$$
Per chiarire vediamo il problema di Cauchy:
$$
y' = \lambda y \qquad y(0)=y_0
$$
La soluzione analitica è $y(x) = y_oe^{\lambda x}$. Studiamo la stabilità di questo problema risolto numericamente con il metodo di Eulero:
$$
y_{n+1} = y_n + hf(x,y_n)
$$
nel nostro caso:
$$
y_{n+1} = y_n + h\lambda y_n = (1+h\lambda)y_n 
$$
è riscrevere il valore $n$-esimo in funzione della posizione iniziale:
$$
y_n = (1+h\lambda)^ny_0
$$
studiamo ora la stabilità calcolando la costante di stabilità, aggiungendo una perturbazione al dato iniziale $\widetilde{y}_0 = y_0 + \epsilon$:
$$
C(h)_{stab} = \frac{| \widetilde{y}_n - y_n|}{|\epsilon|} = (1+h\lambda)^n
$$
dipende dal parametro $\lambda$ del problema, dallo step $h$ del metodo, e dal passo $n$. E' facile vedere che $C$ è unbounded se:
$$
|1+h\lambda| > 1
$$
ovvero, in questo caso la differenza tra la soluzione iniziale e quella perturbata diverge. E' evidente che questo problema è invece stabile per $\lambda \leq 0$, indipendentemente da $h$.

Vediamo col metodo di Eulero-Cromer (eulero implicito):
$$
y_{n+1} = y_n + f(x+h,y_{n+1})
$$
per il nostro problema:
$$
y_{n+1} = y_n + h\lambda y_{n+1}
$$
$$
y_{n+1} = \frac{y_n}{1-h\lambda}
$$
calcoliamo il rapporto di prima:
$$
C(h)_{stab} = \frac{1}{|1-h\lambda|^n}
$$
ancora una volta per non far divergere $C$ dobbiamo avere la condizione:
$$
|1-h\lambda| \geq 1
$$
quindi anche con questo metodo il problema di Cauchy è instabile.