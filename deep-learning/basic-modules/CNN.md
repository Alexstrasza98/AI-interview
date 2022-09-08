# Convolutional Neural Networks
## Basic of CNN
CNN is mostly consisted of four kinds of layers - convolution layer, activation layer, pooling layer and normalization layer. 
Fully connected layer is optional and always replaced by 1x1 conv.

### Convolution
Convolution layer is implemented by sliding a kernel over a local window of original input and computing the convolution (correlation actually) between them and generate a
scalar output. The core difference between convolution and correlation is if the kernel is flipped, and which leads to exchangeability. 
Since exchangeability is not useful in neural network and the weights of kernel are learnt, not specified. We always use correlation in real application.
The mathematical form is:

$$S(i,j) = (K*I)(i,j) = \sum_m \sum_n I(i+m, j+n)K(m,n)$$

- Advantage of Convolution over Fully connected layer
