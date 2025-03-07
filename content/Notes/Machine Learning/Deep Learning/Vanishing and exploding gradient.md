
In deep learning, since we stack a _considerable amount of layers_, the gradient depends on more and more factor. So a natural problem arises: the gradient can _tendo to zero or infinity exponetially fast_.


Consider for example the _sigmoid_ activation function. For values with big $|x|$ the function is almost flat, so the gradient is almost zero (it's always a value in $[0,1]$). If we stack a lot of layers, the gradient becomes very small, it _vanishes_, therefore the network is hard to train.
