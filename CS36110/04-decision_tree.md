Decision Tree Learning
======================
Easiest and most powerful algorithms.

Nodes test an attribute, leaves are a classification, edges correspond to an attribute value.

Can use set notion to represent a decision tree.

$A \cap B$ -> Image here.

$A \cup B$ -> Image here.

Can represent any boolean function.

Top-Down Induciton
------------------
```
node = root
main loop:
  A <- 'best' decision attribute for next node.
  Assign A as decision attribute for node
  Sort E to leaf nodes
  if E perfectly classified or all attributes used:
    stop
  else
    iterate through leaf nodes
```

Problem is deciding the best decision for a node.

We apply Occam's Razor to this problem, that is the best solution is the best solution, in this case this means the best tree is the smallest possible to correctly classify elements.

The search we use to find a tree is a greedy hueristic where the main decision is for the next attributes.

We try to find the purest attribute to split on at the current point in the tree.

Example:

${(A=0, B=0), -}: 50$

${(A=0, B=1), -}: 0$

${(A=1, B=0), -}: 0$

${(A=1, B=1), +}: 100$

Splitting on $A$ in this example gives pure labels (I think I copied this down wrong). Splitting on $B$ doesn't.


Entropy
-------

$S$ -> Training data

$p_+$ -> Positive examples in $S$

$p_-$ -> Negative examples in $S$

$Entropy(S) = - p_+ log_2(p_+) - p_- log_2(p_-)$

Baring in mind that $p_- = 1 - p_+$

The least pure is $p_+ = 0$

More generally:

$Entropy(S) = \sum_i(-p_i log_2(p_i))$


Information Gain
----------------

$Gain(S,A)$ is the expected reduction of Entropy due to sorting on $A$.

$Gain(S,A) = Entropy(S) - \sum_{u \in Values(A)}\frac{|S_u|}{|S|}Entropy(S)$


ID3
---

```
create root node
if all labelled same return single node with an attribute
	A = best att for S
	root = A
```


Overfitting
-----------

$error_{train}(h) < error_{train}(h')$

$error_D(h) > error_D(h')$

Stop growing tree when split is not statistically significant.

Post-prune overfitting.

"Post" tree: $min(size(tree)+size(misclassifier(train)))$ (where min is the minimal description length [whatever the fuck that is])


Continuous Attributes
---------------------

Choose cut-off values (like in fuzzy?)


Attributes with many values
---------------------------

Use Gain Ratio:

$GainRatio(S,A) = \frac{Gain(A,S)}{SplitInfo(S,A)}$


Attributes with costs
---------------------

$\frac{Gain^2(S,A)}{Cost(A)}$

$\frac{2^{Gain(S,A)} - 1}{Cost(A) + 1}$


Attributes with missing values
------------------------------

Assign the most common, classify new examples in a similar fashion.


