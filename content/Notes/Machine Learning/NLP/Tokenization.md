Transformer models cannot receive raw strings as input; instead, they assume the text has been tokenized and encoded as numerical vectors.

### Character Tokenization
The simplest tokenization scheme is to feed each character individually to the model.
``` 
text = "Tokenizing text is a core task of NLP."
tokenized_text = ['T', 'o', 'k', 'e', 'n', 'i', 'z', 'i', 'n', 'g', ' ', 't', 'e', 'x', 't', ' ', 'i', 's', ' ', 'a', ' ', 'c', 'o', 'r', 'e', ' ', 't', 'a', 's', 'k', ' ', 'o', 'f', ' ', 'N', 'L', 'P', '.']
```

The next step is _numericalization_, each char is encoded to an integer. For example creating a python dictionary:

``` 
toek2idx = {ch: idx for idx, ch in enumerate(sorted(set(tokenized_text)))}

input_ids = [token2idx[token] for token in tokenized_text]
input_ids = [5, 14, 12, 8, 13, 11, 19, 11, 13, 10, 0, 17, 8, 18, 17, 0, 11, 16, 0, 6, 0, 7, 14, 15, 8, 0, 17, 6, 16, 12, 0, 14, 9, 0, 3, 2, 4, 1]
```

The last step is to convert input_ids to a 2D tensor of _one-hot_ vectors, we can use `one_hot()` from pytorch:
``` 
import torch 
import torch.nn.functional as F 

# converto to torch.tensor
input_ids = torch.tensor(input_ids) 
# convert to one-hot
one_hot_encodings=F.one_hot(input_ids,num_classes=len(token2idx)) 
```

For each of the 38 input tokens we now have a one-hot vector with 20 dimensions, since our vocabulary consists of 20 unique characters.

**Drawbacks of char tokenization**
Character-level tokenization _ignores any structure in the text_ and treats the whole string as a stream of characters.
Although this helps deal with misspellings and rare words, the main drawback is that _linguistic structures such as words need to be learned from the data_. This requires significant compute, memory, and data. 
For this reason, character tokenization is rarely used in practice. 

### Word Tokenization
Instead of splitting the text into characters, we can split it into words and map each word to an integer. Using words from the outset enables the model to skip the step of learning words from characters, and thereby reduces the complexity of the training process.

One simple class of word tokenizers uses whitespace to tokenize the text. We can do this by applying Python’s `split()` 
```
tokenized_text = ['Tokenizing', 'text', 'is', 'a', 'core', 'task', 'of', 'NLP.']
```

Clearly there is a drawback: given that words can include declinations, conjugations, or misspellings, _the size of the vocabulary_ can easily grow into the millions!
Having a large vocabulary is a problem because it requires neural networks to have an enormous number of parameters.


### Subword Tokenization
The basic idea behind subword tokenization is to combine the best aspects of character and word tokenization. On the one hand, we want to split rare words into smaller units to allow the model to deal with complex words and misspellings. On the other hand, we want to keep frequent words as unique entities so that we can keep the length of our inputs to a manageable size. 
The main distinguishing feature of subword tokenization (as well as word tokenization) is that _it is learned from the pre‐training corpus_ using a mix of statistical rules and algorithms.

