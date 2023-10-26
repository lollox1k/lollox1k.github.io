
Networks used usually for computer vision, they use _convolutional layers_ that exploit the visual domain traslation invariance (for a motivation[[Convolutions from first principles]]), and hierarchical structer of the visual world by stacking layers and lateyers, with the idea that each layer learing more complex feature.

They also implement **pooling**, a way to reduce the input size.

The typical architercure is stacking conv. layerse and then pooling to reduce the size, in the end a flatten and a dense network to output classes.

### The convolution layer
The layer learns the weights for a filter (or conv. **kernel**). You need to set the **size** of this windows, the **stride**, **padding** for boundary conditions, and the **number of kernels** (the idea is that you want to extract different features simultaneously.)



## Examples

#### LetNet-5 for MNIST
![[Pasted image 20231016140858.png]]

- $4$ convolutional layers, num_filters = $32, 32, 64, 64$
- $3$ dense layers $1024, 1024, 10$
- average pool


#### AlexNet
![[Pasted image 20231016141521.png]]

- much bigger input size, ImageNet competition $2012$
- $5$ conv. layers
- max pooling


#### VGG-16
![[Pasted image 20231016141833.png]]


#### GoogleLeNet
![[Pasted image 20231016142343.png]]

- very deep: $22$ layers
- adding two more outputs, their loss in added weighted by $0.3$, ignored at inference.


#### ResNet
![[Pasted image 20231016142446.png]]
- deep
- added residuals!