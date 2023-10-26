# Discrete time Markov chains


### Definition and basic properties

Let $I$ be a _countable_ set. Each $i \in I$ is called a _state_ and $I$ is called the _state-space_.

We say that $\lambda = \{\lambda_i \,:\, i \in I\}$ is a _measure_ on $I$ if $0 \leq \lambda_i < \infty$ for all $i \in I$. If the _total mass_ $\sum_{i\in I} \lambda_i$ equals $1$, then we call $\lambda$ a _distribution_.

We will work with a [[Probability spaces|probability space]] $(\Omega, \mathcal{F}, \mathbb{P} )$. A [[Random variables|random variable]] taking values in $I$ is a measurable function $X : \Omega \to I$. 

Suppose we set
$$
\lambda_i = \mathbb{P}(X=i) = \mathbb{P}(\{\omega \in \Omega \,:\, X(\omega) = i\})
$$
this defines the _distribution_ of $X$. We think of $X$ as modelling a random state which takes value $i$ with probability $\lambda_i$.

It's natural to define a matrix $P = (p_{ij}\,:\, i,j \in I)$ which entries correspont to the probability to get from state $i$ to state $j$. It follows that each row shoud be a distribution, i.e. $\sum_J p_{ij} = 0$. Such matrices are called _stochastic_.

**Def** A stochastic process $(X_n)_{n \geq 0}$ is a _Markov Chain_ with _initial distribution_ $\lambda$ and a _transition matrix_ $P$ if
1. $X_0$ has a distribution $\lambda$;
2. for $n\geq 0$, conditional $X_n = i$, $X_{n+1}$ has distribution $(p_{ij}\,:\, j \in I)$ and is independent of $X_0,\dots, X_{n-1}$.

Written explicitly, these condition are
1. $\mathbb{P}(X_0=i) = \lambda_i$;
2. $\mathbb{P}(X_{n+1} = i\,|\, X_0 = i_0, \dots, X_{n-1} = i_{n-1}, X_{n}=j) = p_{ji}$

We say that $(X_n)_{n\geq 0}$ is $Markov(\lambda, P)$ for short.

## DUBBIO ???
>> Il professore aggiunge che gli stati $i_0,\dots, i_n$ devono avere probabilità positiva???
$$
\mathbb{P}(X_0=i_0, \, X_1 = i_i,\dots) > 0
$$
>> _My answer:_ non vuole condizionare su eventi di probabilità nulla!

>> _Meaning:_ Markov chains are discrete time stochastic processes with "no memory". The r.v. $X_n$ is the state at time $n$.


We can give a more comprehensive description of Markov Chains, i.e. an equivalent characterization.

**Theorem 1.1.1** A Discrete time random process $(X_n)_{0 \leq n \leq N}$ is  $Markov(\lambda,P)$ is and only if for all $i_0,\dots,i_N \in I$ 
$$
\mathbb{P}(X_0=i_0,X_1=i_1,\dots X_N=i_N) = \lambda_{i_0} p_{i_0i_1}p_{i_1i_2}\dots p_{i_{N-1}i_N}
$$
**Proof** 
$(\implies)$ Suppose $X$ is $Markov(\lambda,P)$, then
$$
\mathbb{P}(X_0=i_0,\dots X_N=i_N)
$$
$$
= \mathbb{P}(X_N = i_N \vert X_0=i_0,\dots X_{N-1}=i_{N-1})\mathbb{P}(X_0=i_0,\dots X_{N-1}=i_{N-1})
$$
which follows from the definition of conditional probability.
The first term is, by property $2$ equal to $p_{i_{N-1}i_N}$. By iterating $N$ times we get our thesis.

$(\impliedby)$ 
It's clear by induction that for each $0 \leq n \leq N$
$$
\mathbb{P}(X_0 = i_0, \dots, X_n=i_n) = \sum_{i_{n+1},\dots,i_N \in I} \mathbb{P}(X_0=i_0,X_1=i_1,\dots X_N=i_N) = \lambda_0 p_{i_1} \dots p_{i_n}
$$
in particular this implies
$$
\mathbb{P}(X_0=i_0) = \lambda_0
$$
By computing the conditional probability
$$
\mathbb{P}(X_{n+1} = i_{n+1} \,\vert\, X_0=i_0,X_1=i_1,\dots) = \frac{\mathbb{P}(X_0 = i_0, \dots, X_{n+1}=i_{n+1})}{\mathbb{P}(X_0 = i_0, \dots, X_n=i_n)} = p_{i_ni_{n+1}}
$$
this is Markov property $2$. $\square$




