Let $D$ be a vocabulary of words, and let $w_i \in D$ be a word.
A _Language Model_ (LM) is a probability distribution over the sequences of words, i.e. $P(w_1,w_2,\dots, w_n)$.

The task of a language model is to compute the probability of a given sentence.


### Types of LM
- **Unigram** basic (false) assumption that the probability of each word is indipendent, so that
$$
P(w_1,w_2,\dots, w_n) = P(w_1)P(w_2)\cdots P(w_n)
$$
- **N-gram** dependence up to context size $N$:
$$
P(w_1,w_2,\dots, w_n) = \prod P(w_i \mid w_{i-n+1}, \dots, w_{i-1})
$$
- **Neural** 
$$
P(w_1,w_2,\dots, w_n) = \prod P(w_i \mid \text{ context}(w_i))
$$
