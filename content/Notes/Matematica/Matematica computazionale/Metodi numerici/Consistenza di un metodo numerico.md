# Consistenza di un metodo numerico
Un [[Metodi numerici|metodo numerico]] $\Phi$ si dice _consistente_ se:
$$
\lim_{h\to 0} T(x,y;h) = 0
$$
ovvero il [[Truncation error]] converge uniformemente a zero quando lo step tende a zero.

Per un problema di Cauchy al prim'ordine:
$$
\frac{dy}{dx} = f(x,y) \qquad y(0) = y_0
$$
segue dalla definizione di errore di troncamento che un metodo è consistente se e solo se:
$$
\lim_{h\to 0} \Phi(x,y;h) = u'(x) = f(x,y)
$$
dove $u(x)=y$ è la soluzione analitica con  condizioni iniziali pari allo stato attuale dell'integrazione numerica. 
