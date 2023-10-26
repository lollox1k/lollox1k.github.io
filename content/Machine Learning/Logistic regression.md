
Suppose that we want to learn a function $f : \mathbb{R}^n \to \{0,1\}$. A simple hypotesis would be a step function:
$$
h_w(x) = \theta(w^Tx)
$$
 but this is non differentiable! 
 Another simple choice that is smooth is the _logistic function_:
$$
logistic(x) = \frac{1}{1+e^{-x}}
$$
so that ourmodel is defined as
$$
P(y=1\mid x) = logistic(w^Tx)
$$


- **Input**: $x \in \mathbb{R}^n$
- **output**: $y \in \{0,1\}$
- **hypotesis**: $\frac{P(y=1 \mid x)}{P(y=0\mid x)} = e^{w^Tx}$

Since $P(y=1 \mid x) + P(y=0 \mid x) = 1$, we find that

$$
q_w(y=1| x) = P(y=1\mid x) = \frac{1}{1-e^{-w^Tx}}
$$
We call $p$ the 'true' probability. Our goal is to make $q$ as similar as possible to $p$, to do so we introduce 
- **Performance metric**: Binary crossentropy
$$
H(p,q) = -p(y = 1)\log\frac{p(y=1)}{q(y=1)} - (1-p(y=1))\log\frac{1-p(y=1)}{1-q(y=1)}
$$
we minimze the average binary cross-entropy on the $m$ training examples

$$
\frac{1}{m} \sum_{i=1}^mH(p,q) = -\frac{1}{m} \sum_{i=1}^m y_i\log q_w(y=1) + (1-y_i)log(1-q_w(y=1))
$$
note that
$$
\log q_w = \log \frac{1}{1+e^{-w^Tx}} = -\log (1+e^{-w^Tx})
$$
$$
\log (1-q_w) = \log\left( 1 - \frac{1}{1+e^{-w^Tx}}\right) = \log\left( \frac{e^{-w^Tx}}{1+e^{-w^Tx}}\right)  = -w^Tx - \log(1+e^{-w^Tx})
$$


let's compute the gradient!
$$
-\frac{1}{m} \sum_{i=1}^m y_i\left(\frac{x e^{-w^Tx}}{1+ e^{-w^Tx}}\right) + (1-y_i)\left( -x + \frac{x e^{-w^Tx}}{1+ e^{-w^Tx}}\right)
$$
$$
-\frac{1}{m} \sum_{i=1}^m y_ix + \left(\frac{x e^{-w^Tx}}{1+ e^{-w^Tx}}\right) 
$$
$$
-\frac{1}{m} \sum_{i=1}^m x_i \left( y_i + \frac{e^{-w^Tx_i}}{1+e^{-w^Tx_i}}\right)
$$
$$
-\frac{1}{m} \sum_{i=1}^m x_i(y_i + 1-q_w(x_i))
$$
(c'è un +1 che non dovrebbe esserci, alla fine è molto clearn)
imposing it equals to zero
$$
\sum_{i=1}^m x_i(y_i - q_w(x_i)) = 0
$$
which is
$$
\sum_{i=1}^m x_i(y_i - \hat y_i) = 0
$$

this is not analitically tractable! 
We need to use numeric techincs like [[Gradient Methods]].


