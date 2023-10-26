A _Monoid_ is a [[Semigroup]] with an identity element.

**Def** A set $S$ equipped with a binary operation is called a _Monide_ if:
1. (clousure) $\forall s_1,s_2 \in S$ $s_1s_2 \in S$
2. (associativity) $\forall s_1,s_2,s_3$ $s_1(s_2s_3) = (s_1s_2)s_3$
3. (identity element) $\exists e \in S$ such that for evert $s \in S$ $es = se = s$


**Oss** The identity element is unique: suppose $e$ and $e'$ are both identities, then $e = ee' = e'$.

**Oss** An element $m \in S$ is called _invertible_ if there exists another element $m^{-1} \in S$ such that 
$$
m^{-1}m = mm^{-1}= e
$$
where $m^{-1}$ is called _the inverse_ of $m$. 
The inverse is unique, since $n^{-1} = n^{-1}(mm^{-1}) = (n^{-1}m)m^{-1}=m^{-1}$.

**Oss** The set of invertbile elements of a monoid is a [[Group]].

Every [[Semigroup]] $S$ can be transformed into a monoid denoted $S^1$ by adding a new element (the identity), and defining the operation with it as desired.



**Examples**
- the integers equipped with the standard product $(\mathbb{Z}, \cdot)$ are a monoid.
- all the endofunctions of a set $X$ equipped with function composition $(End(X), \circ)$
- the set of square matrice of any field $M_n(\mathbb{F})$ equipped with the usual matrix prodcut.
