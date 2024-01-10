### MAX CNF-SAT
_Input_: $CNF$ boolean formula (clause lenght not fixed)
_Goal:_ find assignment that maximises # of sat clauses

### Random assignment algoritm for fixed k
1. set $x_i = 0,1$ with prob. $1/2$ $\forall i$
note: works best with long clauses $P(C_i is UNSAT)) = 1/2^k$ ($k$ number of literals)

2. divide and conquer, finds at leeast $1-1/2^k$ SAT clauses.

## LP-relaxation + Randomized Rounding
1. variabili:
$$
\forall i \quad x_i \in \{0,1\} \qquad \forall C \quad z_c \in \{0,1\}
$$
2. funzione obj: 
$$
\max\sum_C w_c z_C
$$
where $w_C$ is a weight, (for max CNFSAT $w_c=1$ ), we get something for free.
3. creare i vincoli:
$$
\forall C \qquad \sum_{i\in C^+} x_i + \sum_{i\in C^-}(1-x_i) \geq z_c
$$
where $C^+$ and $C^-$ are the set of variables and negated variables of clause $C$ respectivly.
4. rilasso, _passo al continuo_
$$
\forall i \quad x_i^* \in [0,1] \qquad \forall C \quad z_c^* \in [0,1]
$$
We get a linear programming problem, solvable in P time. Since the serch space of the lineare problem is bigger, the solution is better than the discrete one:
$$
LP \geq OPT
$$
5. rounding. We do it probabilistically:
$$
x_i = \begin{cases} 1 \text{ with prob } x_i^* \\ 0 \text{ otherwise } \end{cases}
$$
$$
\beta_k := (1-1/2^k) 
$$
expected number of SAT clauese:
$$
E[X] = \sum_C w_i E[C_i] = \sum_C w_c E[C_i] ) \sum_C w_c P[C_i \text{ is SAT}]
$$
where $C_i = 1,0$ if is SAT or not. (we used linearity and expted of bernoullui random variable).

Pick a clause $C$ with $|C| = k$ literals.
$$
P(C \text{ is SAT}) \geq \beta_k z_c^*
$$
in fact:
$$
P(C \text{ is SAT}) = 1- \Pi_{i\in C}(1-x_i^*)
$$
