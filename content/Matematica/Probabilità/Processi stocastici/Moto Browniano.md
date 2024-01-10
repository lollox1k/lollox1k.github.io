Il moto Browniano è un processo stocatisco a tempo continuo $(B_t)_{t \geq 0}$ è un elemento di $C[0,1]$ distribuito secondo la [[Wiener measure]].
Then $B_t \sim N(0,t)$ and
$$
Cov(B_s,B_t) = s \land t
$$
assume w.l.o.g. $s < t$ then
$$
\mathbb{E}[B_sB_t] = \mathbb{E}[(B_t-B_s)B_s] + \mathbb{E}[B_s^2]
$$
$$
= \mathbb{E}[B_t-B_s]\mathbb{E}[B_s] + s = s
$$
since $(B_t-B_s)$ is indipendent of $B_s-B_0 = B_s$.

We can compute the law of the increments via the characteristic function:
$$
\mathbb{E}[e^{iuB_t}] = \mathbb{E}[e^{iu(B_t-B_s)}]\mathbb{E}[e^{iuB_s}]
$$
$$
\phi(B_t-B_s) = \frac{\mathbb{E}[e^{iuB_t}]}{\mathbb{E}[e^{iuB_s}]} = e^{-(t-s)u^2/2}
$$
dunque $B_t-B_s \sim N(0,t-s)$. 
Thus _increments are stationary_, meaning their distribution doesn't depend on time.

From the indipendence of the increments we can compute the probability of cylinder sets:
$$
\mathbb{P}(B_{t_1} \in I_1, B_{t_2} \in I_2, \dots) =
\mathbb{P}(B_{t_1} \in I_1, (B_{t_2}-B_{t_1})+B_{t_1} \in I_2, \dots)
$$
and the fact that given $X,Y$ indipendent random variables:
$$
f_{X,X+Y}(x,y) = f_X f_Y(y-x)
$$
so from the properties of the Wiener measure, its value is deterined on all cylinder sets, which form a [[Pi-system]]: so the measure is uniquley determined on all measurable sets. 




