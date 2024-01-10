
The most popular and used activation function:
$$
ReLu(x) := \max(0,x)
$$

**Pros**:
- Computationally less expensive compared to other activation functions
- Fewer neauron beeing activated, leading to network sparsity and thus computational efficency
- Avoida vaniscing gradient: since its derivative is always $1$ (in the positive input range) gradiens flow well on active paths of neurons.
**Cons** 
- The *dying ReLu*: if too many values are negative, most of the network is inactive and the network is unable to learn further

Possible causes of the dying ReLu:
- _High learning rate_: the update will push weights into negative numbers, thus overall negative scalar product.
- _Large negative bias_ obvious. 