# The Sherrington-Kirkpatrick model

Is a simple mean-field [[Disordered systems]] with gaussian coupings. 
The hamiltonian is
$$
\mathcal{H}^{SK} = \frac{1}{2\sqrt{N}} \sum_{(i,j)} J_{ij} \sigma_i \sigma_j \qquad J_{ij} \sim N(0,1)
$$
with $J_{ij}$ i.i.d.
We can add an external field $h$, this doesn't complicates the study, since it factorazies.

### Computing the annealed free energy

**Proposition** The annealed free energy of the SK model is
$$
f^A = -\frac{1}{\beta} \ln 2\cosh \beta h -\frac{\beta}{4}
$$
**Proof** Since the couplings are i.i.d, the partizion function is the product of $\binom{N}{2}$ identical partion function.
$$
Z = \sum_\sigma \prod_{1 \leq i < j \leq N} \exp \left( \frac{\beta}{\sqrt{N}}J_{ij} \sigma_i \sigma_j\right)\exp{ \left(\beta h \sum_k \sigma_k\right)}
$$
we can compute the gaussian average
$$
\mathbb{E}\exp \left( \frac{\beta}{\sqrt{N}}J_{ij} \sigma_i \sigma_j\right)
$$
sice $\sigma_i\sigma_j = \pm 1$  $J_{ij} \sigma_i \sigma_j \sim N(0,1)$, from a simple calculation we find
$$
= \exp \left( \frac{\beta^2}{2N} \right)
$$
since we have $\binom{N}{2} = N(N-1)/2$ terms in the product we get
$$
\mathbb{E}Z = \sum_{\sigma}  \exp \left[ \frac{\beta^2}{2N} \cdot \frac{N(N-1)}{2}\right] \exp{ \left(\beta h \sum_k \sigma_k\right)}
$$
per sommare il termine dipendente dagli spin, lo fattorizziamo
$$
\prod_k 2\cosh(\beta h) = 2^N\cosh^N(\beta h)
$$
otteniamo:
$$
Z_N =2^N\cosh^N(\beta h)\exp(\frac{\beta^2}{4}(N-1))  
$$
quindi l'energia libera nel TDL è
$$
f^A = \lim_{N\to\infty}\frac{-1}{\beta N} \ln \mathbb{E}Z
$$
$$
=  -\frac{1}{\beta}\ln 2\cosh(\beta h) -\frac{\beta}{4}
$$
**Remark** se si calcola l'entropia si trova che è negativa per $\beta$ abbastanza grandi, questo non ha senso fisico, di conseguenza l'energia libera annealed non è quella corretta.


### The square root normalization

In the [[Modello di Curie-Weiss]] the normalization for the interacions $J$ was $\frac{1}{N}$, while here in the SK model we have $1/\sqrt{N}$. 

The intuition: sum of $n$ gaussian variables is again a gaussian with standard deviation of $\sqrt{n}$.

Si può far vedere analiticamete usando il [[Isserlis-Wick theorem]].

Let's compute the average energy:
$$
\langle \mathcal{H}\rangle = \mathbb{E} \frac{\sum_\sigma \mathcal{H}(\sigma) e^{-\beta \mathcal{H}}}{Z}
$$
$$
= -\frac{1}{2\sqrt N} \sum_{i,j} \mathbb{E}J_{ij} 
\frac{\sum_\sigma\sigma_i\sigma_j e^{-\beta \mathcal{H}}}{Z}
$$
we now use the theorem $\mathbb{E}[gF(g)] = \nu^2 \mathbb{E}[F'(g)]$
$$
= -\frac{1}{2\sqrt N} \sum_{i,j} \mathbb{E}\partial_{J_{ij}} \frac{\sum_\sigma\sigma_i\sigma_j e^{-\beta \mathcal{H}}}{Z}
$$
let's compute the partial deriviative
$$
-\frac{\beta}{2\sqrt N}\frac{1}{Z^2}\left[ \left(\sum_\sigma \sigma_i^2\sigma_j^2 e^{-\beta H}\right)Z - \left( \sum_{\sigma^a} \sigma_i^a\sigma_j^a e^{-\beta H}\right)\left( \sum_{\sigma^b} \sigma_i^b\sigma_j^b e^{-\beta H}\right) \right]
$$
$$
=-\frac{\beta}{2\sqrt N}\left( 1- \Omega(\sigma_i^a\sigma_j^a)\Omega(\sigma_i^b\sigma_j^b)\right)
$$
dove con $\Omega$ abbiamo indicato la media rispetto alla misura di Boltzmann.
Quindi alla fine 
$$
\langle \mathcal{H}\rangle = -\frac{\beta}{4 N}\sum_{i,j} 1- \mathbb{E}[\Omega(\sigma_i^a\sigma_j^a)\Omega(\sigma_i^b\sigma_j^b)]
$$
$$
= -\frac{\beta N}{4}(1-\langle q^2_{ab}\rangle)
$$
che come voluto è di ordine $O(N)$.
