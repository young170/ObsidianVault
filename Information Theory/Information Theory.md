
## Introduction

I stumbled upon this topic by pure chance. It started with the paper, *'A Mathematical Theory of Communication' - C. E. Shannon*.
This collection of notes provides my understanding of the paper. I try to understand, study, experience, make examples, etc. with topics I really want to dive into. Although these notes may not cover the entire topic, I worked hard to write them in the simplest way possible. Have fun.

## Information and its Measurement

### What is information?

"How much information is in a message?" is the question that started the theory, and already its hard even to understand the question. More simply put, the question could be re-written, "How many questions are needed to understand the message?"

A simple example of this question would be:
Message1: "It is snowing on Mt. Everest."
Message2: "It is snowing in the Sahara."

Obviously, the first message doesn't need much questioning. However, for message 2, one could ask a number of questions. "Do you mean the Sahara in the continent Africa?" and so on. These questions basically boil up to the fundamental question, "Are you sure?". Which asks for **certainty**.

Now we know somehow (although we don't know how, yet) **information** (the message) is connected with **certainty** (or uncertainty).

After reading the example above again, one can conclude this:
* 'An event that has a **high probability** to occur provides **low information** content'
* 'An event that has a **low probability** to occur provides **high information** content'
Or, one could say the more likely an event is to occur, we can correctly guess the event.

Using mathematical words:
> **Information** $I(x)$ and **probability** $P(x)$ are inversely related

Visually, (known as the inverse $log$ graph)
![[inverse_proportion_solution.jpg]]
As the probability (x-axis) increases, information (y-axis) decreases.

Some properties we can learn from just this property are:
* If an event is certain to occur (100% probability), it yields no information.
	* $P(x) = 1 => I(x) = 0$
* An event never causes a loss of information.
	* $I(x) \ge 0$

### Mathematical Representation of Information

Now that we have a graph and some properties, we just need a mathematical statement that describes information in terms of probability. Lets simply plug in the variables we learned into the graph:
> $I(x) = - \log_b P(x) = \log _b (1/P(x))$

Wait a minute... what is the $b$? The $b$ is known as the base of the $log$, which determines the standard of the current $log$ function. Normally, this value would be $10$ (just like how we count numbers), but in this case it is going to be $2$. This is to represent bits. Bits are how computers count numbers.

### Information and Uncertainty

Now remember what we learned earlier...
> **information** (the message) is connected with **certainty** (or uncertainty).

We dealt with information, its time for uncertainty (the reason I chose uncertainty will be explained).

Before explaining uncertainty, lets give it a name. Just as the message was given a proper name of **information**, uncertainty is too general of a word. Here's an idea from John von Neumann...
> "...no one really knows what entropy really is, so in a debate you will always have the advantage" - John von Neumann

No one can really argue with him right? Lets re-write the title of this chapter.

### Information and ~~Uncertainty~~ Entropy

This time the mathematical expression is given first,
> $H(X) = \sum_{i=1}^n P(x_i) \cdot I(x_i)$

Here the entropy $H(X)$ is represented by the multiple of the probability $P(x)$ and information $I(X)$.
An example,
```
Events = [
	A: P(0.50), I(1)
	B: P(0.25), I(2)
	C: P(0.25), I(2)
]

Entropy = [
	A: 0.5
	B: 0.5
	C: 0.5
]
```

The sum of the entropy $H(X)$ would be 1.5. Then what does this mean? And why are they all constant?

## Information Systems

## [[General Communication System]]

Shannon also defined a simple yet effective system for communication.

##### Reference
[Foundations of information theory: Part 1, 2, 3)](https://mbernste.github.io/posts/self_info/)
[Mathematics of Information](http://www.ece.virginia.edu/~ffh8x/moi/index.html)
[Huffman Codes: An Information Theory Perspective](https://www.youtube.com/watch?v=B3y0RsVCyrw)
