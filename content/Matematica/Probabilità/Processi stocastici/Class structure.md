It is possible to break a Markov Chain into smaller pieces, each of them easy to understand. The key idea is _communicating classes_.


**Def** We say that $i$ _leads to_ $j$ and write $i\to j$ if exists some $n\geq 0$ such that
$$
P_i(X_n = j) = P_{ij}^{(n)}> 0
$$
**Def** We say $i$ _communicates to_ $j$ and write $i\leftrightarrow j$  if both $i\to j$ and $j\to i$.

**Remark** It is clear that $\leftrightarrow$ is an equivalence relation on the state space $I$, so that we can partitions $I$ into _communicating classes_.

**Def** We say that $C$ is a _closed class_ if
$$
i \in C, \, i \to j \implies j \in C
$$
> a closed class is one from which there is _no escape_.

**Def** A state $i$ is called _absorbing_ if $\{i\}$ is a closed class.

**Def** A non closed class is called _open_. 


**Def** (Irreducibility) A Markov Chain is said to be _irreducible_ if $I$ is a single class. Just check that $\forall i,j$   $i \to j$.
