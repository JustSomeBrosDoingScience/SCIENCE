Regression
==========

Bias and Variance 
-----------------

Bias $\approx$ Systematic Error

Variance $\approx$ Error due to the varaiability of the model.

Bias $\rightarrow$ Underfitting $\rightarrow$ Hypothesis insufficient (in hypothesis space).

Variance $\rightarrow$ Overfitting $\rightarrow$ Hypothesis inacurate for unseen data (large hypothesis space).


Linear Regression
-----------------

$h(x) = w_0 + w_1x$

$min(\sum_i(y_i - h(x_i))^2)$

Effectively minimize the squared errors.


Bias - Variance Analysis
------------------------

Given new data $x^*$

Expected predicted error is $E_D((y^*-h(x^*))^2)$

Decompose into bins variance and noise.

$E_D((h(x^*) - \bar{h}(x^*))^2)$ $\rightarrow$ Variance

Where $\bar{h}(x^*) = E_D(h(x^*))$

$(\bar{h}(x) - f(x^*))^2$ $\rightarrow$ Bias

Where $f(x^*)$ is the true target.

$E_D((y^* - f(x^*))^2)$

Expected prediction error $=$ Variance $+$ Bias $+$ Noise


###Formal Definitions

$Variance = E_{x,D}((h(x) - \bar{h}(x))^2)$

$Bias = E_X((\bar{h}(x) - f(x))^2)$

$Noise = E{\epsilon, x}((y-f(x))^2) = E(\epsilon^2) = \sigma^2$


Hypothesis Space
----------------

Decreasing bias increases the hypothesis space (and therefore variance)

Increasing bias decreases variance.

You should match modle complexity to data resouces.

Decision trees have a high variance in general due to thei hueristic nature.

**Note:** Bias is not Inductive Bias. They are, however, linked.


Ensemble Models
---------------

Ensemble models involves combining the preditions of several models to improve overall performance.

### Intuitions

Combining diverse, inderpendant opinions.

Protective mechanism.

Majority vote.

### Boosting

Grow models sequentially, make misclassified examples important.

Decreases bias mainly.

### Bagging

Use different samples.

Decreases variance mainly.


Bagging - Bootstrap Aggrigation
-------------------------------

More robust to noise.


Random Forest
-------------

Applying Bagging to the decision tree and attributes.
