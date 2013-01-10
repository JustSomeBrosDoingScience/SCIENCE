Concept Learning
================

Induce a description of a concept from a set of specific examples.

Example: inferring a Boolean function from given inputs and outputs.

Notation and Terms
------------------

* $x$ - Instance Space (constraints).
* $c$ - Target Concept (to be learned).
* $<x, c(x)>$ - Training examples $D$.
* $H$ - Hypothesis space.
* $h$ - A single hypothesis where $h \in H$.
* $X: h:X \rightarrow \{0,1\}$

Learning goal is to find a $h$ to satisfy:

$$h(x) = c(x) for all in D$$

* $?$ indicates any value is acceptable (wildcard).
* $0$ indicates any value is unacceptable (garbage state).

$h$ is a conjunction of constaints.

For example:

$$h = {math=difficult, workload=hard, presentation=dull, application=?, references=?} \rightarrow 0$$

Concept learning can be defined as a search.

* Theoretical: $2^\{|H|\} - 1$
* Syntatian: $\prod_i x + 2$ (includes $?$ and $0$).
* Semantical: $1 + \prod_i x + 1$ (includes $?$ and $0$ as single states).

Ordering of H
-------------
$x$ satisfies $h$ iff $h(x)=1$.

$h_{i}$ generalised to $h_{j}$

$h_{j}$ specialised to $h_{i}$

Rote Learning
-------------
Rote learning is the a form of learning where you only give answers to instances which pre-exists in the training data. You cannot classify a completely an instance if there is no exact match in the data set.

FIND-S
------

```
init h to be the most specific in H
for each positive training instance in x:
  for each constaint a[i] in h:
    if a[i] satisfied x:
      do nothing
    else
      replace a[i] by next most specific example satisfied by x
return h
```

For example:

$$h_0 = <E, L, I, W, R>$$

$$x_1 = <M, L, I, W, R>$$

$$h_1 = <?, L, I, W, R>$$

$$x_2 = <E, H, I, N, R>$$

$$h_2 = <?, ?, I, ?, R>$$

Only works when:
* $f \in H$
* No errors in training data.
* $H$ are confunctions

Problems:
* May not converge on a correct $h$.
* Can't detect inconsistencies.
* Picks maximally specific $h$.
* There may be several $h$.


Candidate Elimination
---------------------
Finds all describable $h$ if $h$ is consistent with $D$ iff $h(x) = c(x)$ for $<x, c(x)> \in D$

$$
consistent(h,D) \equiv (\forall <x,c(x)> \in D) h(x) = c(x)
$$

Version space:

$$
VS_{H,D} \equiv \{h \in H | consistent(h,D)\}
$$

(Most) Specific $\rightarrow$ (Most) General are the only required $h$, others can be generated from these two.


List-then-Eliminate
-------------------

```
VS = H

for(<x, c(x)>):
  remove h if h(x) != c(x)

output VS
```

Guarentees all H consistent, required to enumerate all in H.


Induction Bias
--------------
$L$: Convept Learning als[sic?]

$X$: Instance space.

$c$: Target function.

$D_{L} = {<x,c(x)>}: Training data.

$$
D_{i}: (\forall x_{i} \in X)[(B \cap D_{i} \cap x_{i}) \vdash L(x_{i}, D_{i})]
$$

For reference:

$A \vdash B$: $A$ entails $B$.
