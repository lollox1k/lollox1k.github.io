# RBM

### Architecture
Is a neural network architecture on a complete bipartite graph. 
The two layer are called _visible_ and _hiddent_, in total we have
$$
N = N_v + N_h
$$
total neurons. Indichiamo lo stato dei neuroni visibili con $v \in \{-1,1\}$ e $h \in \{-1,1\}$ for the hidden neurons.

The hamiltonian is the usual of neural networks models
$$
\mathcal{H}^{RBM} = -\sum_{ij} J_{ij} s_is_j -\sum_i \theta_is_i
$$
### Supervised learning

The goal is to learn the joint distribution $q(x,y)$ where $x$ is the input and $y$ the label.

The idea is to use the visible neurons $v$ to encode $x$, and the hidden to encode the label (class). 

We need to find parameters $J,\theta$ such that the equilibrium distribution of the network is as close as possible to the data
$$
P_{J,\theta}(v,h) \sim q(v,h) 
$$
Then we can use the network to predict the correct label of unseen data, the best guess 
$$
h^* = \mathbb{E}[h\,|\, v = v^*]
$$
### Unsupervides learning

Input: some data $D = \{x_i\}$.
Task: learn the data distribution $q(x)$.

Again we encode our data $x$ in the visible layer neurons $v$.
So we need to find the best parameters $J,\theta$ such that
$$
P_{J,\theta}(v) \sim q(v)
$$
Once the network is trained, it can be used to generate new data, denoise, and to reconstruct.

### Learning

The task is to learn a distribution. The obvious choice is to define a metric (loss) beetween the network distribution and the goal and try to minimize that using gradient descent.

We will use the KL-divergence $D(q\Vert P_{J,\theta})$.
Using gradient descent we obtain update rules for the parameters:
$$
\Delta J_{ij} = -\eta \partial_{J_{ij}} D(q\Vert P_{J,\theta})
$$
$$
\Delta \theta_i = -\eta \partial_{\theta_i} D(q\Vert P_{J,\theta})
$$
thus we need to compute this derivatives. 
Let's consider the RBM in the unsupervised learning setting.
$$
P_{J,\theta}(v) = \frac{\sum_h \exp [ -\beta \mathcal{H}(v,h)]}{Z} = \frac{Z(v)}{Z}
$$
since we only care about visibile neurons, we had to marginalize.
$$
\partial_\lambda D(q \Vert P_{\lambda}) = -\sum_v q(v)\partial_\lambda[ \ln q(v)-\ln P_\lambda(q) ]
$$
$$
= -\sum_v q(v)\partial_\lambda[ -\ln Z(q)+\ln Z ]
$$
$$
= \sum_v q(v)\left[  \frac{\partial_\lambda Z(v)}{Z(v)} - \frac{\partial_\lambda Z}{Z} \right]
$$
calcoliamo le derivate che compaiono al numeratore
$$
\partial_\lambda Z(v) = -\beta\sum_h \partial_\lambda H(v,h)e^{-\beta H}
$$
$$
\partial_\lambda Z = -\beta\sum_{v,h} \partial_\lambda H(v,h)e^{-\beta H}
$$
rimettendo insieme...
$$
\Delta J_{ij} = -\frac{\eta\beta}{\ln2}\left[ \langle s_is_j\rangle_{free} - \langle s_is_j\rangle_{clamped}\right]
$$
$$
\Delta \theta_i = -\frac{\eta\beta}{\ln2}\left[ \langle s_i\rangle_{free} - \langle s_i\rangle_{clamped}\right]
$$
per la procedura di training devo far termalizzare la rete... Computazionalmente non trattabile per reti non miniuscole. 

**Teniche per approssimare**:
- MCMC Monte Carlo Markov Chain, più passi faccio meglio è (empiricamente ne basta anche uno solo!)
- Approssimazione mean field usando le equazioni di autoconsistenza.

