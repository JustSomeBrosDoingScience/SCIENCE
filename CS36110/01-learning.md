Learning
========
Knowledge is gained through learning from experience. Normally to apply knowledge we have to makes some form of assumtions, we call this bias in IL. Therefore our knowledge is not always correct.

We can learn from both sucess and failure.

Learning is an abstract process, we cannot formalise how we as humans actually learn.


AI Systems
----------
TODO image here.

The advantages of this are as follows:

* This is often more accurate than humans.
* Humans are often incapable of expressing the result.
* Automatic method to search for the hypothesis explains the data.
* Cheap and flexible.

However the downsides are that:

* There is a need for a lot of labelled data.
* Error-prone and inheritantly imperfect.
* Difficult to discern what has actually been learnt.

One important tennant of IL is that data is cheap and abudant, but knowledge is rare and expensive. Thus learning from examples is the most common form of learning.

To have achived learning you must improve the performance of the system in some way.

The training data takes the form of an input:output mapping. The input is usually some form of vector and the output can take the form of a real, discrete or categorical value.

If 
$$output \in R$$
then the algorithm is ??? (I turned off here).

Learning is supervised is the output of the training data is known.


Definitions
-----------
We define this experience in the form

$$y = f(x)$$

Where: $y$ is the outcome and $x$ is the parameters. We use $f$ to map $x$ to $y$. $f$ is usually unknown as it is the aim for learning.

We guess $f$ using hypotheses $H$. Each hypothesis $h$ is an approximation of $f$ from the training data in various methods (e.g. Expectation Maximisation, Optimisation, etc.).

Give expereicence $<1:0>(i=1,2,...)$ we define a target $h:1 \rightarrow 0$. We then optimise the objective function:

$$\min\sum(O^^_i - O_i)$$

Where $O^^$ is the actual output and $O$ is the desired output.

TODO graph here.

In the above graph $h1$ accounts for noise. $h2$ is accurate if the training data is known not to be noisy. Both of these require some form of prior knowledge of the data set.


Performance
-----------
The error rate is defined as:

$$E = e \div p$$

Where $E$ is the error rate, $e$ is the errors and $p$ is the predictions.

The *Apparent error rate* is the error rate of all tested data.

The *Test sampe error rate* is the error rate when trained with a large fraction and tested with the remaining data.

The *True error rate* is the error rate when trained with all existing data and tested with new data.

True error is preferred out of all three, but is the most difficult to perform.
