
A loss function used in  classification. 
In general the **cross entropy** beetween discrete probability distribution is defined as
$$
H(p,q) := -\mathbb{E}_p[\log q]
$$

Recallin the deifnition of [[Kullback-Leibler divergence]], one finds that 
$$
H(p,q) = D_{KL}(p \mid\mid q) + H(p)
$$
where $H(p)$ is the entropy of $p$.


For the simple case where the suppor of $p$ and $q$ is a two values set $\{x_1,x_2\}$, we get

$$
H(p,q) = -p(x_1)\log q(x_1) - (1-p(x_1))\log(1-q(x_1))
$$
