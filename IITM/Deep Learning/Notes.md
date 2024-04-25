# Deep Learning

## Week 1

### History of deep learning:

Deep learning is inspired by the biology of the brain i.e. the network of neurons. This is translated to perceptrons in computer science. 

Jordan network was a RNN that introduced context to NLP and video processing.

:)

---

## Week 2

Linearly separable is essentially when one straight line can't divide the solution plane into the required sets. 

<img title="" src="images/Notes/2024-03-06-21-00-19-Screenshot_20240306_205947.png" alt="" data-align="center" width="466">

See above for XOR. This is to say that one perceptron can only handle a linearly separable data. We have $2^{2^n}$ boolean functions for n inputs.

A few terms to remember:

* $w$ is weight. This applied to an input.

* $h$ is usually the output from a perceptron.

* $b$ or $bias$ is usually added in the end , just before evaluation of a function.

So formula is usually: $w_0*i_0 + ... + b <condition> <some\ value>$ so for example: $w_0*i_0 + ... + b \ge 0$ If that is true then we have some output else some other output.

Input layer is not a perceptron. Hidden and output layers are perceptrons.

Things like sigmoid function help with non boolean implementations. So there are smooth transition between True and False.

<img title="" src="images/Notes/2024-03-06-21-43-03-Screenshot_20240306_214255.png" alt="" data-align="center" width="466">

This is usually applied to the final output. 

Full formula here is 

$output = \frac{1}{1+r^{-(w_1x+b_1)}}$ 



### Error:

Error is used to guide the algorithm.

Taylor series is a way of approximating a continuously differential function.

<img src="images/Notes/2024-04-23-01-05-20-Screenshot_20240423_010504.png" title="" alt="" data-align="center">

The higher the order of the function we consider the higher the "accuracy" will be.

<img src="images/Notes/2024-04-23-01-07-56-Screenshot_20240423_010707.png" title="" alt="" data-align="center">

This is gradient descent formula

Gradient is the collection of the partial derivatives. Matrix thingy. In gradient descent we move opposite to the gradient because that is where the loss reduces the most.

<img src="images/Notes/2024-04-24-23-07-36-Screenshot_20240424_230728.png" title="" alt="" data-align="center">

Let's say this is loss function. $f(x)$ is the prediction.

Change in weights is partial derivation (w and then b) of this.

$w_1 = w_0-\eta(\frac{df}{dw})$

REVISE THE BASIC INTEGRATION AND DERIVATION RULES!!!

We can approximate any function with $x$ number of towers.

<img src="images/Notes/2024-04-25-22-06-00-Screenshot_20240425_220548.png" title="" alt="" data-align="center">

We only need 2 neurons to make a tower, in 2d. and only 1 $x$. To get a "closed tower in 3d we use 4 neurons. 

<img src="images/Notes/2024-04-25-22-09-27-Screenshot_20240425_220921.png" title="" alt="" data-align="center">

Now if we add this to another sigmoid and set it so the all output above one stays the we get, <img title="" src="images/Notes/2024-04-25-22-11-47-Screenshot_20240425_221113.png" alt="" width="167">.

![](images/Notes/2024-04-25-22-12-13-Screenshot_20240425_221208.png)

---

## Week 3

<img title="" src="images/Notes/2024-04-25-23-30-04-Screenshot_20240425_232957.png" alt="" data-align="center" width="650">

<img src="images/Notes/2024-04-25-23-30-22-Screenshot_20240425_233014.png" title="" alt="" data-align="center">

Softmax is

$\frac{e^{aL_j}}{\sum_{i=1}^k{e^{aL_j}}}$

\>:( Softmax bounds to 0-1.

Cross entropy loss is $L(\theta) = -\sum_{c=1}^k{y_clog\ \^{y_c}}$

Now since we use this for probability, the formula simplifies into $l(\theta)= -log\ \^{y_l}$ where $l$ is the True class.

<img title="" src="images/Notes/2024-04-25-23-40-37-Screenshot_20240425_234033.png" alt="" data-align="center" width="617">

a is value pre-activation function and h is value post-activation function.

<img src="images/Notes/2024-04-26-00-01-34-Screenshot_20240426_000127.png" title="" alt="" data-align="center">

---
