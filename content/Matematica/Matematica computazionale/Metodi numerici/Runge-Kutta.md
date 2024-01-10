Una famiglia di [[Metodi numerici]] ad $s$-step. 

I metodi espliciti sono esprimibili come:
1. $y_{n+1} = y_n + h\sum_i^s b_ik_i$
2. $k_s = f(t_n+c_sh, y_n + h(a_{s1}k_1 + a_{s2}k_2 + \dots + a_{s,s-1}k_{s-1}))$  

Tutti questi coefficienti $a,b,c$ che definiscono i metodi vengono raccolti in dei tableaux:
![[Pasted image 20220308222112.png]]
Si dimostra che il metodo è consistente ([[Consistenza di un metodo numerico]]) se e solo se:
$$
\sum_i^s b_i = 1
$$
Infatti dalla seconda definizione di consistenza:
$$
\lim_{h\to 0} \Phi(x,y;h) = \sum_i^s b_i f(x,y) = f(x,y)
$$
avendo sfruttato il fatto che per $h\to 0$ tutte le $k_i \to f(x,y)$. 

Cosa fanno i metodi Runge-Kutta: sostanzialmente l'incremento numerico è una comabinazione pesata (i pesi sono le $b_i$) della funzione $f$ del problema di Cauchy calcolata in vari punti: le costanti $c_i$ ci dicono in quali punti dell'intervallo della variabile indipendente ($x$ o $t$), le $a_{is}$ in quali punti per la $y$, da notare che è una matrice: dipende anche dallo step corrente $s$, come ha senso che sia: i valori di $y$ vanno calcolati!

Alcuni metodi RK famosi:
- RK4
![[Pasted image 20220308223431.png]]
- Eulero
 ![[Pasted image 20220308223520.png]]
 - RK2 o punto di mezzo
 ![[Pasted image 20220308223546.png]]