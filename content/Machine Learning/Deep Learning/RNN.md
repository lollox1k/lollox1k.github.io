### Modelling Sequence Data


Some task where the input is of sequential nature:
- speech recognition
- machine translation
- language modeling
- sentiment analysis
- video data

How should we choose our model?
Again, FCN are  [[Cybenko universal approximation theorem|universal]], but the size of the model can grow too much.

If our sequence is long $x_1,\dots, x_T$ the FCN would become prohibitively large:
**Idea** input one $x_i$ at a time, re-use the same weights!
With this idea we don't care about the sequence length $T$.

To memorize prviously information, we employ a **recurrent** mechanism.
$$
h^t = f_W(h^{t-1}, x^t), \quad h^{-1} \text{ given }
$$
we can _unfold_ this formula $t-1$ times.

A simple RNN model:
$$
h^t = \tanh(W_{hh}h^{t-1} + W_{xh}x^t), \quad o^t = softmax(W_{ho}h^t)
$$

### Training an RNN
It's like we arte backpropagating through time.
Just unfold the network! The loss is just the sum:
$$
L = \sum_{i=1}^T L(o^i, y^i)
$$
for simplicity let's assume that there is no bias and that the activation function is the identity. Then
$$
h^i = W_{hh}h^{i-1} + W_{xh}x^i
$$
$$
o^i = W_{ho}h^i
$$
Let $s \leq t$, then
$$
\frac{\partial L^t}{\partial h^s} = \frac{\partial L^t}{\partial h^t} \prod_{s < k \leq t} \frac{\partial h^k}{\partial h^{k+1}}
$$
but in our simple case 
$$
\frac{\partial h^k}{\partial h^{k+1}} = W_{hh}
$$
so that
$$
= \frac{\partial L^t}{\partial h^t} W_{hh}^l
$$
things could get ugly if $l$ is big: if the greatest eigenvalue norm is greater than $1$ we get [[Vanishing and exploding gradient|exploding gradient]], if it's less than $1$ vanishing gradient.


### LSTM

_Long-Short-Term-Memory_  
Past input contribute less and less to the loss. We need to add memory!

**Main ideas**
- a new hidden state $c^t$ called _cell state_, with the ability to _store long-term information_.
- LSTM can _read, write and erase_ information from a cell.
- _Gates_ are defined to get the ability to select information, they are also vector of length $n$.
- At each time step $t$ the gates can be _open_ (1) or _close_ (0), or somewhere in between.
![[Pasted image 20231016154737.png]]

#### Forget Gate
Controls what is kept vs forgotten from previous cell state.
$$
f^t = \sigma(W_f h^{t-1} + U_f x^t + b_f)
$$
#### Input Gate
Controls what parts of the new input are written to the cell.
$$
i^t = \sigma(W_i h^{t-1} + U_i x^t + b_i)
$$
#### Output Gate
Controls what parts of the cell state is trasnfered to the hidden state.
$$
o^t = \sigma(W_o h^{t-1} + U_o x^t + b_o)
$$

#### New Cell content
We update the content of the cell and the hidden state usins the gates
$$
\tilde c^t = \tanh (W_c h^{t-1} + U_c x^t + b_c)
$$
forget and write 
$$
c^t = f^t \odot c^{t-1} + i^t \odot \tilde c^t
$$
the new hidden state uses the output gate
$$
h^t = o^t \odot \tanh c^t
$$


### GRU

_Gated Recurrent Units_ It doesn't use a cell state, but it has gates!

#### Reset Gate
controls what parts of previous hidden state are used to compute new content
$$
r^t = \sigma(W_r h^{t-1} + U_r x^{t} + b_r)
$$
#### Update Gate
controls what parts of previous hidden state are used to compute new content
$$
u^t = \sigma(W_u h^{t-1} + U_u x^{t} + b_u)
$$

We use the gates very similarly to create a new hidden state:
$$
\tilde h^t = \tanh (W_h (r^t \odot h^{t-1}) + U_h x^t + b_h)
$$
$$
h^t = (1-u^t) \odot h^{t-1} + u^t \odot \tilde h^t 
$$
