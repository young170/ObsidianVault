
## Introduction

I stumbled upon this topic by pure chance.
This collection of notes provides my understanding of the paper.

## Information

Information theory can be said to be derived from the data compression problem.
Starting with the question, "how much can we compress?"
This logically led to, "how much **information** is in the message?"
Which raised the basis of information theory, "how do we measure **information**?"

It started with the paper, *'A Mathematical Theory of Communication' - C. E. Shannon*.

Before diving into what information is, Shannon describes a [[General Communication System]].

## Measuring Information

### Key properties

1. **Information** $I(x)$ and **probability** $P(x)$ are inversely related
	1. [[Uncertainty & Information]]
2. $I(x) \ge 0$, observing event $x$ never causes a loss of information
	1. Information is non-negative
3. $P(x) = 1 => I(x) = 0$ 
	1. If an event is certain to occur, it yields no information
4. $P(x \cap y) = P(x) \cdot P(y) => I(x \cap y) = I(x) + I(y)$
	1. If $x$ and $y$ are independent events, then the total information is the sum of each information

### Self Information

$I(x) = \log _b (1/P(x)) = - \log_b P(x)$

* Measures the information after observing event $x$ with probability $P(x)$
* Satisfies the key properties
* The base of the $\log$ is usually 2, which represents bits

## Information Entropy

> "...no one really knows what entropy really is, so in a debate you will always have the advantage"
> - John von Neumann

$H(X) = \sum_{i=1}^n P(x_i) \cdot I(x_i)$

As a message's length approaches $\infty$, the average length per symbol $L$ never gets lower than the entropy value $H(X)$

##### Reference
[Foundations of information theory: Part 1, 2, 3)](https://mbernste.github.io/posts/self_info/)
[Mathematics of Information](http://www.ece.virginia.edu/~ffh8x/moi/index.html)
[Huffman Codes: An Information Theory Perspective](https://www.youtube.com/watch?v=B3y0RsVCyrw)
