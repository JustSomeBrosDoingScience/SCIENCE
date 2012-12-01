# Bayesian Learning

#Introduction

Most Machine Learning techniques try to learn one hypothesis function for all
of the given data. However, this is not always the best approach - especially
when there are several reasonably likely hypotheses for a problem. Take the
following example from Russell \& Norvig:

> Our favourite surprise candy comes in two flavours: cherry(yum) and
> lime(ugh). The candy manufacturer has a peculiar sense of humour and wraps
> each piece of candy in the same opaque wrapper, regardless of flavour. The
> candy is sold in very large bags, of which there are known to be five kinds -
> again, indistinguishable from the outside:

* $h_1: 100\% cherry$
* $h_2: 75\% cherry + 25\% lime$
* $h_3: 50\% cherry + 50\% lime$
* $h_4: 25\% cherry + 75\% lime$
* $h_5: 100\% lime$

We denote the type of bag as $H$ and it's possible values range from $h1$ to
$h5$. $H$ is unobservable to us. However, as each sweet is opened and tasted,
we can initialise $D_1, D_2, D_3... D_N$ where each $D_i$ is a random
variable is cherry or lime. We want to use the agent to try and predict the next
piece of candy.

Bayesian Learning incrementally calculates the probability of each hypothesis,
making predictions based on *all* hypotheses, weighted by their probabilities
rather than using a single best hypothesis. This means learning comes down to
probabalistic inference.

We can use Bayes' rule to work out the probability of a hypothesis ($h_i$)
given a flavour($d$). This is shown as

$p(h_i|d) = \frac{p(d|h_i)p(h)}{p(d)}$

if we know $d$ because we observed it, then $p(d)=1$ and our equation
becomes:

$p(h_i|d) = p(d|h_i)p(h)$

## Naivity is key

In Naive Bayesian learning, we always assume that each feature of the data set
$F_i$ is independent of every other feature $F_j$ for $i \ne j$ such that "the
probability of 
$p(F_i|C,F_j) = p(F_i|C)$ 


## MAP - Maximum Aposteriori Hypothesis

This allows us to extract the most probable hypothesis given the training data
set $D$. Finding the MAP is less computationally demanding and can also be used
to reduce the risk of Overfitting - it is a natural embodiment of *Ockham's
Razor.* 


