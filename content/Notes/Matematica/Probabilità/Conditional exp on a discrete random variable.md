Since we can represent a discrete random variable as a sum of indicators, it's natural to define
$$
\mathbb{E}(X|Y) := \sum_{y \in S_Y} \mathbb{1}(Y=y)\frac{\mathbb{E}(X\mathbb{1}(Y=y))}{\mathbb{P}(Y=y)}
$$
