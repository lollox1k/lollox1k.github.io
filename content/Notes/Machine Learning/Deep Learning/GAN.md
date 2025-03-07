_Generative Adversarial Networks_:
- generative model
- instead of MLE it uses an adversarial training model
- networks: deep learning

![[Pasted image 20231016203119.png]]


First we train the discriminator, we freeze the generator (so that the generated images are basically random noise) and gradient descent to update the discriminator weights.

Then we train the generator by fixing the discriminator.

The word adversarial should be clear. Using the standard notation we can view the Loss as negative the reward, then
$$
\min_G \max_D R(D,G)
$$
this is a min max game.
The [[Nash Equilibrium]] for this game is achieved at:
$$
P_{data}(x) = P_{gen}(x) \quad \forall x, \qquad D(x)=\frac{1}{2} \quad \forall x
$$

### Mode collapse
- The generator settles for just one (or cycles few) generated examples that fool the discriminator: the model is almost indipendent from the noise $z$.
- cat and mouse game: the generator produces a single mode. The discriminator quickly overfits to label as generated. The generator quickly finds a new mode. Repeat...