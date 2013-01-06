Artificial Nueral Networks
==========================

Linear Classification
---------------------

$h(\vec{x}) = sign(x)$

Uses an absolute threshold (e.g. binary).


Linear Regression
-----------------

Apply a linear function.

$h(\vec{x}) = s$


Logistic Regression
-------------------

Apply a 'soft' threshold (like a sigmoid function).

$h(\vec{x}) = \theta s$


Perception
----------

A type of ANN.

$(x_0, x_1, ..., x_d) = \vec{x} \rightarrow inputs, \vec{w} \rightarrow weights$

$$
o(\vec{x}) = \left\{ 
  \begin{array}{l l}
    1 & \quad \text{if} \vec{w} \vec{x} > 0\\
    -1 & \quad \text{otherwise}
  \end{array} \right.
$$

$$
\sum^d_iw_ix_i = \vec{w}\vec{x}
$$

This can represent a logical function, e.g.: $x1 \&\& x2$

But can't represent some, e.g.: XOR.

$$
h(\vec{x}) = sign( \sum^d_i{w_i x_i} ) = sign(\vec{w}\vec{x})
$$

Each run pick a misclassified example:

$$
sign(\vec{w}\vec{x}^{(n)}) \neq y^{(n)}
$$

Update weight:

$$
\vec{w} \leftarrow \vec{w} + y^{(n)}\vec{x}^{(n)}
$$

```
until no misclassified results:
	pick misclassified result
	update weight
done
```

Modified

$$
\Delta\vec{w} = \eta(y-o)\vec{x}
$$

$o \rightarrow$ Perception output.

$\eta \rightarrow$ Small constant (learning weight).

Can be prooved to converge with a linearly seperable data set and learning rate which is sufficiently small.
