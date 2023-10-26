# Similarity transformation

**Definition** For a nonsingular matrix $X$, the map $A \mapsto X^{-1}AX$ is called a _similarity transformation_ of $A$.

**Theorem** A similarity transformation preserves eigenvalues.
**Proof** We can show this by proving that $A$ and $X^{-1}AX$ share the same characteristic polynomial:
$$
p_{X^{-1}AX}(\lambda) = \det{(X^{-1}AX-\lambda I)} = \det{(X^{-1}(AX-\lambda XI))}
$$
we use [[Binet]] theorem and the fact that $XI = IX$ (the identity commutes with every matrix) to get:
$$
\det{X^{-1}} \det{(AX-\lambda IX)} = \det{X^{-1}} \det{(A-\lambda I)}\det{X} = \det{(A-\lambda I)}
$$
where we again used binet. The last term is the characteristic polynimial of $A$. $\square$
