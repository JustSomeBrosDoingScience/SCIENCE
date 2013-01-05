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


