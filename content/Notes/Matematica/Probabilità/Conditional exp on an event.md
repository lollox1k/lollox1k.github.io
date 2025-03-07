# Definitions
## Conditioning on an event
Let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space. Given an event $A \in \mathcal{F}$ such that $\mathbb{P}(A) >0$, and a random variable $X$, we definte the _conditional expectation_:
$$
\mathbb{E}(X|A) := \frac{\mathbb{E}(X\mathbb{1}_A)}{\mathbb{P}(A)}
$$

Let's check if that makes sense, i.e. it's the same as using the coditional probability. First check the case $X$ is a discrete variable with values $S_X \subset \mathbb{R}$, which we can represent as a sum of indicators:
$$
X = \sum_{x \in S_X} x \mathbb{1}(X=x)
$$
$$
\frac{\mathbb{E}(X\mathbb{1}_A)}{\mathbb{P}(A)} = \frac{1}{\mathbb{P}(A)}
\sum_{x \in S_X} x\mathbb{E}(\mathbb{1}_{x \cap A})
=  \sum_{x \in S_X} x \frac{\mathbb{P}(X=x \cap A)}{\mathbb{P}(A)} = \sum_{x \in S_X} x \mathbb{P}(X=x|A)
$$

## Conditioning on a discrete random variable
Since we can represent a discrete random variable as a sum of indicators, it's natural to define
$$
\mathbb{E}(X|Y) := \sum_{y \in S_Y} \mathbb{1}(Y=y)\mathbb{E}(X|Y=y)= \sum_{y \in S_Y} \mathbb{1}(Y=y)\frac{\mathbb{E}(X\mathbb{1}(Y=y))}{\mathbb{P}(Y=y)}
$$
This is again a discrete random variable, and since it's a sum of indicators of  measurable sets $\sigma(Y)$, it's $\sigma(Y)$ measurable. If we fix $\hat y \in S_Y$, and compute
$$
\mathbb{E}[\mathbb{E}(X|Y)\mathbb{1}(Y=\hat y)] = 
\mathbb{E}\left[
\sum_{y \in S_Y} \mathbb{1}(Y=y)\mathbb{1}(Y=\hat y)\mathbb{E}(X|Y=y)
\right] = 
\mathbb{E}[
\mathbb{1}(Y=\hat y) \mathbb{E}(X|Y=y)
]


$$
but the expected value of $X$ conditioned to the event $Y=y$ is a number, hence we can pull it out
$$
\mathbb{E}[
\mathbb{1}(Y=\hat y)] \mathbb{E}(X|Y=y) = 
\mathbb{P}(Y=\hat y) \mathbb{E}(X|Y=y) = 
\mathbb{E}(X\mathbb{1}(Y=\hat y))
$$
since any measurable set in $\sigma(Y)$ can be represented as a sum of elements $y$, this generalizes to the identity:
$$
\mathbb{E}(\mathbb{E}(X|Y)\mathbb{1}_A) = \mathbb{E}(X\mathbb{1}_A) \qquad \forall A \in \sigma(Y)
$$
