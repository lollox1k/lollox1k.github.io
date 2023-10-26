# Continuità della misura
Sia $(A_n)_{n\geq 1} \subset \mathcal{F}$ una successione monotona non decrescente di insiemi misurabili. Allora:
$$
\mu(\cup_n A_n) = \lim_{n\to\infty} \mu(A_n) 
$$
Sia $(A_n)_{n\geq 1} \subset \mathcal{F}$ una successione monotona non crescente di insiemi misurabili. Allora:
$$
\mu(\cap_n A_n) = \lim_{n\to\infty} \mu(A_n)
$$
#### Proof
Uso la $\sigma$-additività per insiemi disgiunti, definendo la successione:
$$
B_{n+1} := A_{n+1} \setminus A_{n} \quad B_1 = A_1
$$
Ovviamente $\cup B_n = \cup A_n$. Quindi:
$$
\mu (\cup_n A_n) = \mu( \cup_n B_n) = \sum_n \mu (B_n) = \mu(A_1) + \sum_{n=1} \mu(A_{n+1}\setminus A_n)
$$
siccome $A \subseteq B$ implica che $\mu(B\setminus A) = \mu(B)-\mu(A)$, otteniamo una serie telescopica:
$$
\mu(A_1) + \lim_{k\to\infty} \sum_{n=1}^k \mu(A_{n+1})-\mu(A_n) = \lim_{k\to\infty} \mu(A_k)
$$
Si ragiona in maniera analoga per una successione d'insiemi non crescente. $\square$

