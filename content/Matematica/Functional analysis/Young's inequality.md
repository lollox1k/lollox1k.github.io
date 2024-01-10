**Theorem** (Young's inequality) Suppose $1 < p < \infty$, then for all $a,b \geq 0$
$$
ab \leq \frac{a^p} p + \frac{b^{p'}}{p'}  
$$
where $\frac 1p + \frac1{p'} = 1$.

**Proof** If either $a$ or $b$ equals zero then the inquality is trivial. Suppose that neither are zero, fix $b > 0$ and define the real function:
$$
f(a) = \frac{a^p} p + \frac{b^{p'}}{p'} -ab 
$$
its derivative is $f'(a) = a^{p-1} -b$ so that $f$ is decrising in the inverval 
$(0, b^{1/p-1})$ and increasing in $(b^{1/p-1}, \infty)$ so that it achieves a global minimum in $a = b^{1/p-1}$ with value $0$, so that
$$
\frac{a^p} p + \frac{b^{p'}}{p'} -ab  \geq 0 \qquad \square
$$

