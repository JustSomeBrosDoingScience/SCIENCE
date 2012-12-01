# Bayesian Learning

#Introduction

A couple of important probability maths things you need to know are:

$P(A \cap B) = P(A)P(B)$

$P(A | B) = \frac{P(B | A)P(A)}{P(B)}$


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


