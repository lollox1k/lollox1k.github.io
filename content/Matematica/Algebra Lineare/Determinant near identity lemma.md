**Lemma** Let $A$ be a $n\times n$ square matrix, then
$$
\det (I + \epsilon A) = 1 + \epsilon Tr(A) + o(\epsilon^2) 
$$
**Proof** Let $M = I + \epsilon A$.
$$
\det M = \sum_{\sigma} (-1)^\sigma \prod_{i=1}^n M_{i\sigma_i}
$$
Where $\sigma$ are the permutations of $[n]$. If $\sigma$ is the identity permutation, we get
$$
\prod_{i=1}^n M_{ii} = \prod_{i=1}^n (1+\epsilon A_{ii}) = 1 + \epsilon Tr(A) + o(\epsilon^2)
$$
for al the remaining permutation, at least one term of the product will be just $(\epsilon A_{ij})$, making only $o(\epsilon^2)$ contributions. $\square$
