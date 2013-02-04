CS Seminar - The Watchmaker may be blind but he's not stupid
============================================================

Links between cognition and evolution.

Main claim - Natural selection takes place in your mind and gives you good ideas.

Natural selection makes mistakes but is intelligent and can get more so.


Natural Selection
-----------------

Auto-catalytic (exponential) growth with variation (differences within a generation) and heredity (correlation between generations) and variability (differences between generations).

Natural selection is just an algorithm, we know it within our system (life), but you can get natural selection without life (machines).


Natural Selection makes mistakes, Saturn doesn't
------------------------------------------------

Some variants in natural selection are better (or worse) than others.


Blind but not stupid
--------------------

Natural selection is intelligent in that it gets better at performing a task over time (knowledge-based search).

Imagine that we have two identical tables (equal fitness). Each table has two babies, one table is defined by the width and height, the other by rectangular blocks (same phenotypes, different genotypes). Obviously the width/height parent can produce fitter offspring.

Evolution gains knowledge in terms of it's previous knowledge.

> "How many moves do you look ahead in chess?" "One, the right one."


How evolution by natural selection improves
-------------------------------------------

Non-trivial neutrality.

The question is: can genotype and phenotype maps vary and evolve themselves. Yes.

Evolution of evolvability: if there's variation within variability you can evolve them too (lineage evolution).

The point is natural selection *can* get better over time.

Sex is adaptation for search.


Bayes and Darwin
----------------

Bayesian school of though: Animal learning is optimal in a mathematical sense.

Bayes Inference: 

$$ P(H|D) = \frac{P(D|H)P(H)}{\sum^{H}_{h}P(D|H)P(H) $$_

Can use Bayes to update hypothesis using MCMC (Markov something)

Can also use natural selection and it turns out Bayes rule is isomorphic with natural selection.

$$ frequency(T)_{t+1} = fitness \times frequency(T)_{t} $$

Approximate Bayesian inference is a computation, Natural selection is an algorithm.

Natural selection is good for open-endedness. It is also good for doing search in a symbolic space.

Productivity just means you can comprehend unlimited ideas.

Language, for example, has systematisation composition (you don't rote learn sentences, you learn words and rules for how those words can be put together).


How does Natural Selection compare?
-----------------------------------

* Solitary Search: (Stochastic) hill climbing.
* Parallel Search: Independent hill climbers.
* Parallel Search with competition (price): Competitive Learning, Reinforcement Learning, Synaptic Selectionism, Neural Darwinism (Edelmanism).
* Parallel Search with Competition and Information Transmission (JMS): Genetic Natural Selection, Adaptive Immune System, Genetic Algorithms, Didactic receptive fields, Neuronal Replicators.

**Competitive Learning:** Give more resources to fitter agents.

A better algorithm might that fitter agents "recruit" other agents (replication). Agents here act like alleles. This is the core of natural selection.

Just a reminder that copying is not replication. Replication involves copying the probability of being copied. Establish co-variance of replication(?).

**Adaptive Immune Systems** have this property where T-cells have the probability of replication.

**Genetic Algorithms** obviously have this property and so do (possibly) **Neuronal Replicators** there is certainly copying here, but unsure if it's replication.

Limited Heredity: In the physical capacity of where it exists it is possible to generate all possible values. It is limited because you could not generate all possible variants because of the combinatorial complexity.

It might be better to recruit rather than restart.


Surely nothing replicates in my brain!
--------------------------------------

Neurons don't, but is there any plausible ways in which information (a pattern) could replicate from one part of the brain to another?

Imagine you have a neural network and is characterised by it's pattern of connectivity. How can you replicate this?

Spike Time Dependent Plasticity. Helps determine that at pre caused the post. This can cause false positives. STDP does not allow for complete copying, but can be modified to do this with high-fidelity.

There's other ways of doing it that get weirder (***A:** I'm going to give up here*). Talk to Borris for me :)

Neural co-evolution:

Actors: do things.
Tasks: Things you do.

Fitness of actor: $f(t1), f(t2)$

Fitness of a task: $Var(f(actors))$

Tasks evolve that make your actors have a better fitness.
