
A computer program is said to learn from _experience_ $\mathcal{E}$ with respect to some class of _tasks_ $\mathcal{T}$  and performance measure $\mathcal{P}$, if its performance at tasks $\mathcal{T}$, as measured by $\mathcal{P}$, improves with experience $\mathcal{E}$.

### Classification task
The objective of the model is to learn the mapping function $\mathcal{T} : X \to Y$
that maps inputs $X$ to a set of labels $Y$. 
The expirience here is a collection of data, namly the pairs $\mathcal{E}= \{(x_i,y_i)\}_{i=1,\dots,M}$.
A performance measure is some kind of distance $\mathcal{P}=dist(\hat y,y)$.

## The classical statistical perspective

The main assumption is that our data follows a (true) probability distribution. Let's imagine a family of statistical models, where each member is specified by a set of real parameters $\Lambda \subseteq \mathbb{R}^p$
$$
\{P_\lambda \,:\, \lambda \in \Lambda\}
$$
Our assumption is that our data is i.i.d like
$$
D = \{(x_i,y_i)\} \sim P_{\lambda_0}, \quad \lambda_0 \in \Lambda
$$
our task is then to find the (true) $\lambda_0$, that is find the correct set of parameters. To do this, we define an _estimator_ $\hat \lambda$ based on the data
$$
\hat\lambda (D)
$$
given a distribution with parameters $\lambda$, we can of course compute the expected value conditioned on $x$ (imagine $x$ is a picture, $y$ a label)
$$
f_\lambda(x) := \mathbb{E}[y |x]
$$
then we can define an _empirical cost_ to measure the performance of our model
$$
\hat R_M(\lambda) := \frac{1}{M} \sum_{i=1}^M dist(y_i, f_\lambda(x_i))
$$
so we the average distance (averaging on all our dataset of $M$ samples) a choice of distance. It's clear that using the true parameters $\lambda_0$, this empirical cost would tend to zero in the limi $M\to \infty$.

It makes sense to choose as our best guess for the parametes 
$$
\hat \lambda = argmin_\lambda \hat R_M(\lambda)
$$

**Technical difficulties of this approach**
1. Family of model not known!
2. The minimization task is usually hard ($\hat R_M$ non convex)
3. We need $M$ big enough to be in the SLLN, i.e empirical cost need to be close to the (true) population cost.