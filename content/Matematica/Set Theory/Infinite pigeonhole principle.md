**Theorem** (Infinite Pigeonhol Principle) Suppose the set $P$ is _infinite_, $H$ is _finite_, and $f : P \mapsto H$. Then there is an element $h \in H$ such that the preimage set $P_h := \{p \in P \,|\, f(p)=h\}$ is infinite.

**Proof** By contradiction, suppose that every such preimage set is finite. The set $P$ can be written as:
$$
P = \bigcup_{h \in H} P_n
$$
but a finite union of finite set is finite. $\square$


