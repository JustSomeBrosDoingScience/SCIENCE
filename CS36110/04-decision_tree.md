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

We try to find the purest attribute to split on at the current point in the [TBC...]