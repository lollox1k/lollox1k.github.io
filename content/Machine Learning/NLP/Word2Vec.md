A simple algorithm for word embedding, i.e. from a simple one-hot representation we get a semantic vector of choosen size. 

This is a _bag of words_ model, it doesn't care about word order.
The idea is to choose a fixed context windows $C$, and then train a shallow model to predict the words in the context around a given word. The hidden layer is new given word embedding.

![[Pasted image 20231016162519.png]]

The loss is computed by summing all the $2C$ predicted vectors, so as we said it doesn't care about the order.


**Huge drawback**
- doesn't care about context, homonyms have the same embedding!

