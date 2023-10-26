### AdaGrad
Individually adapts the learning rate for each parameter.

**Input** gloabl learning rate $\eta$, initial guess for params $\theta$, small constant $\delta$ for num. stability
grad. acc. $r = 0$
**while** not stop criterion:
	compute gradient estimate $\hat g = \frac{1}{B} \sum_i \nabla_\theta L(f_\theta(x_i), y_i)$
	accumulate squared gradient $r = r + g*g$ 
	compute update $\Delta \theta = -\frac{\eta}{\delta + \sqrt{r}}* g$ 
	apply update $\theta = \theta + \Delta\theta$

With $*$ we mean element-wise.

### RMSProp
The same as AdaGrad but introduces a new decay parameter parameter $\rho \in [0,1]$ to exponentially forget the previous gradients:
$$
r = \rho\,r + (1-\rho)g*g
$$
### Adaptive Moments: Adam
 Is a 2014 update to RMSProp combining it with the main feature of the [[Stochastic gradient descent SGD|Momentum]] method. In this optimization algorithm, running averages with exponential forgetting of both the gradients and the second moments of the gradients are used.

**Input** gloabl learning rate $\eta$, initial guess for params $\theta$, small constant $\delta$ for num. stability, forgetting rates $\rho_1$, $\rho_2$, initial velocity $v$.
grad. acc. $r = 0$
**while** not stop criterion:
	compute gradient estimate $g = \frac{1}{B} \sum_i \nabla_\theta L(f_\theta(x_i), y_i)$
	accumulate squared gradient $r = \rho_1\,r + (1-\rho_1)g*g$ 
	update velocty $v = \rho_2\,v + (1-\rho_2)\eta g$ 
	correct bias: $r = \frac{r}{1-\rho_1^t}$
	correct bias: $v = \frac{v}{1-\rho_2^t}$
	compute update $\Delta \theta = -\eta\frac{v}{\delta + \sqrt{r}}$
	apply update $\theta = \theta + \Delta\theta$
	