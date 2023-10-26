A simple solution to the proble of [[Vanishing and exploding gradient|vanishing gradient]], since the problem is that chaining a lot of function leads to a a gradient of lots of factors, we use that differentiation is linear:
$$
g(x) :=x + f(x), \qquad g'(x) = 1 + f'(x)
$$
![[Pasted image 20231015175614.png]]

It's called *residual* since the layers now learns the residual, the difference beetween the input and the (desired) output.

