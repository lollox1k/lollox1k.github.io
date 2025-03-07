
>> Just approx the gradient of the loss function on the whole dataset with a mean on just a subset (batch)
>

**Input** lr $\eta$, initial guess for params $\theta$
**while** not stop criterion:
	compute gradient estimate $\hat g = \frac{1}{B} \sum_i \nabla_\theta L(f_\theta(x_i), y_i)$
	apply update $\theta = \theta - \eta \hat g$


### Momentum
Inspired by physics, the update also depends on the previous "velocity".

**Input** lr $\eta$, initial guess for params $\theta$, momentum factor $\alpha$, initial velocity $v$
**while** not stop criterion:
	compute gradient estimate $\hat g = \frac{1}{B} \sum_i \nabla_\theta L(f_\theta(x_i), y_i)$
	update velocity $v = \alpha v - \eta \hat g$
	apply update   $\theta = \theta + v$

There is a variant called _Nesterov Momentum_, it's like implicit euler method, we compute the gradient with the position updated by the previos velocity:

**Input** lr $\eta$, initial guess for params $\theta$, momentum factor $\alpha$, initial velocity $v$
**while** not stop criterion:
	compute approx next $\hat\theta = \theta + v$
	compute gradient estimate $\hat g = \frac{1}{B} \sum_i \nabla_{\hat\theta} L(f_{\hat\theta}(x_i), y_i)$
	update velocity $v = \alpha v - \eta \hat g$
	apply update   $\theta = \theta + v$
	