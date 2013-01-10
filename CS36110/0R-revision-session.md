Revision Session
================

Support Vector Machines
-----------------------

> "Understand principal of SVMs, but not the maths."

Concepts important. Formulas are not that important - show figures and show understanding - hyperplanes. Training examples - support vectors are just examples with a special hyperplane. One degree of freedom of SVMs.

Linear classifier. Maximise the margin between examples.

SVMs essential try to achive two ideas: maximise the margin, minimise the error. Different from other learning algorithms.

Suppose given kind of hyperplane: $ax + by + cy + d = 0$: What is the margin, remember formula, apply formula.

In this case: $m = \frac{2}{||W||}$

Distance if $(x,y,z)$ is: $D = \frac{ax + by + cy + d}{\sqrt{a^2+b^2+c^2}}$

We can change so that $ax + by+cz +D = \pm1$ easily as the norm doesn't change.

Each question probably contains 3 parts:

* Basic Concepts
* Theories, concepts
* Application

For all other mathematical formulas we aren't expected to know every single detail. SVM are special because there are some simple maths.

Choose **3** from **4** questions.


Non-linear SVM
--------------

> "We're not touching on non-linear SVMs?"

No, it was removed from the sylabus. It's much simpler but the principals are similar.

**Draw figures, write explanations.**


Past Papers Model Answer
------------------------

> "Past exam question 1 (monkey and bannana is learning?), what's a model answer for this?"

Something discussed in the slides. The learning process - monkey learns process to achieve goal.

Younghai is quite flexible, so long as the answer is reasonable and well justified then it will get marks :).


FIND-S
------

> "You have some attributes, $a,b,c$, and some examples. Start with the most specific (non are acceptible). $a$ is then acceptible in the first example, $b$ is then acceptable in the second. How do you write this down without including $c$?"

You'll just have to generalise from $a$ to $?$. In practice you can introduce some other notiations. You have to make a trade off between the simplicity or the compututional complexity, etc.

Concept learning is, of course, very basic.


Maths of ANN
------------

> "Know weights are adjusted every time, not sure how it happens."

Use some diagram or graph to help. Nodes in all layers, initialise all weights. Given the inputs, you can always calculate the outputs. Compare output against real output. In this case you can just change the direction of a network.

First go from input to output, then propergate the error back to the inputs.

Input and output is not linear $\rightarrow$ first order derivative of the sigmoid function.

Seems complicated, once you know the ideas, it's actually quite easy to work out formulas.

Nice property:

$$
\frac{\partial \text{damnit he moved on to quic}}{...} = (\sigma(?))(1-\sigma(?))
$$

For an output node the error is:

$$
\delta = O(1-O)(T-O)
$$

For a hidden node the error is:

$$
\delta = O(1-O)Error-contribution
$$

Where $Error-contribution$ is the weighted sum of errors of the nodes to which it is connected in the next layer.

Small random initialisation values are very small (depends on the applicaton). Normally around 0.


Past Paper Party Question
-------------------------


Wanted to see something about the constraints. Something like **when**, **purpose**, **where**, etc. How to describe such situations using some attributes or features.



Cross Validation
----------------

> "How do you go about performing cross-validation?"

Split the data set. Training and testing set.


Golden Standard
---------------

> "What is the golden standard?"

Usually 2 thirds for training, 1 third for testing. Depends on situation.


Confusion Matrix
----------------

> "What is a confusion matrix?"

True positive, false positive, false negative, true negative.


Topics of the exam
------------------

> "What's on the exam?"

* Introduction, concept learning
* SVM (concepts and computations) and a little on Reinforcement Learning (emphasis ideas, difference to other learning techniques).
* ??
* ??

IID: Identically, Inderpendetly, Distributed. In this case, one example should not be affected by another. All examples follow some sort of single distribution.

Collect evidence showing understanding. Encoraged to write as much as possible, even if you're not sure which is the right answer. **WRITE SOMETHING**. Read questions carefully ;).

Getting part a wrong does not imply part b.

If you know the formulas, write it down and explain it. If you don't, use words to describe the process.

Average mark is around 50% from last year. Normal is around 55%. Hopefully better this year :).


Concept Learning again
----------------------

> "How do you work out symatically different hypotheses?"

Constraints: $a: a_1, a_2, a_3$, $b: b_1, b_2$, $c: c_1, c_2$ and special cases: $?, \emptyset$.

$a: 5, b:4, c:4$

Possibilities not including special cases.

$$
3 \times 2 \timez 2 = 12
$$


Syntatically.

$$
5 \times 4 \times 4 = 80
$$ 

However as soon as $\emptyset$ is included, it is always negative.

$\therefore$ Symatically:

$$
4 \times 3 \times 3 + 1 = 37
$$

Ideal hypotesis space:

$$
2^n \text{ where } n = a_n \times b_n \times c_n
$$


Bayesian Learning
-----------------

> "Difference between MAP and ML?"

ML assume all different hypothesis are equally likely, for MAP not all equally likely.

Naive Bayes classifier -> Estimated probabilities. Encoraged to work these out from given training examples.
