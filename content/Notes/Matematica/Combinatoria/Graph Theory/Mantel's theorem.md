Mantel's theorem is a special case of [[Turan theorem]]. 

**Theorem** The maximum size of a graph of order $n$ that is triangle-free (it doesn't contain $K_3$) is 
$$
m \leq \frac{n^2}{4}
$$
**Proof** Pick any edge in $xy \in E$ (it can't be empty since it has maximum size). Since it is triangle-free, the neighbourhoods of $x$ and $y$ are disjoint
![[Pasted image 20230717201513.png]]
so that 
$$
d(x)-1 + d(y) -1
 \leq n-2 \implies d(x)+d(y) \leq n
$$
summing over all edges
$$
\sum_{xy \in E} d(x)+d(y) \leq n|E|
$$
every therm $d(x)$ in the sum appears $d(x)$ times, so
$$
\sum_{x\in V} d(x)^2 \leq n|E|
$$
we can use [[Cauchy-Schwarz inequality]] to lower boud the first term (or use the fact what the variance is always non-negative)
$$
\left(\sum_{x \in V} d(x)\right)^2 \leq n^2|E|
$$
using the [[Handshake Lemma]]
$$
4|E|\leq n^2 \implies |E|\leq \frac{n^2}{4} \quad \square
$$

 