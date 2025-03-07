Normalize to zero mean and one variance each feature across the batch.
It's a method of _adaptive reparametrization_.

The normalzation operations are considered in the computational graph of the network!
for each feature $x_i$ in the of size $m$:
$$
\mu_i = \frac{1}{m} \sum_{i=1}^m x_i^{(m)}, \quad \sigma_i = \sqrt{\delta + \sum_{i=1}^m (x_i^{(m)}-\mu_i)^2}
$$
$\delta$ is a small value (e.g. $10^{-8}$) added for numerical stability (at zero $\sqrt{x}$ is non differentiable).
So the rescaled features are
$$
\hat x_i = \frac{x_i - \mu_i}{\sigma_i}
$$


During inference time, the mean and variance may be replaced by the values obtained one the whole training dataset.