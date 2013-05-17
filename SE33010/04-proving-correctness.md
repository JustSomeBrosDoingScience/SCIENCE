Proving Correctness
===================

* *Validation* - Implementation which does the right thing.
* *Verification* - Implementation meets the specification.


Correctness Proof
-----------------

A correctness proof is the predicate calculus used in computing for the specification of computer programs and then reasoning about these specifications. The introduction of a formal language for the specification helps to make this more rigorous and may help to point out potential ambiguities in a system.

By using a formal (mathematical) notation the results can be **proved** about the specification.

If a formal proof is used correctly throughout the development process (including the use of a formally defined programming language) then it is possible to produce a formally proved implementation. That is, an implementation which is proved to meet its specification.

The predicate language can be used as a functional specification language, done by providing two formulae:

* Pre-condition,
* Post-condition.

As the name suggests, the pre-condition specifies the input restrictions and the post-condition specifies how the result should be related to the input.

If $S$ is the section of code to be specified this is written as:

$$\{\mathcal{I}\}\mathit{S}\{\mathcal{O}\}$$

###Example

$\{a \ne 0 \land b^2 > 4ac\}$

```
    double : d, x1, x2;
    d = Math.sqrt(b * b - 4 * a * c);
    x1 = (-b + d) / (2 * a);
    x2 = (-b - d) / (2 * a);
```

$\{x1 \ne x2 \land a(x1)^2 + b(x1) + c = 0 \land a(x2)^2 + b(x2) + c = 0\}$

The proof is as follows:

* $b^2 > 4ac$ ensures $d$ is defined and $d \ne 0$.
* $a \ne 0$ ensures $x1$ and $x2$ are both defined.
* $d \ne 0$ implies $x1 \ne x2$.
* To check $x1, x2$ satisfy $ax^2 + bx + c = 0$ is a matter of routine algebra.

This is a bad example as the mathematical verification relies on real numbers, clearly an implementation will only use an approximation to real number (floating point problems).

A mismatch between mathematical arithmetic and machine arithmetic is a problem within formal methods which does not seem to have been fully addressed. There are fewer problems with integer arithmetic, where the machine arithmetic is exact, but the limited range of machine integers and integer overflow may still cause problems.

There are formally defined (IEEE) standards for machine arithmetic but formal methods continue to use mathematical arithmetic.

The formula $\{\mathcal{I}\}S\{\mathcal{O}\}$ means that $\mathcal{I}$ is satisfied immediately prior to the execution of $S$ and $\mathcal{O}$ must be immediately satisfied by $S$, assuming $S$ halts.

Proving this result is called **partial verification**; $S$ is **partially correct** with respect to $\mathcal{I}$ and $\mathcal{O}$.

If it can be proved that $\mathcal{I}$ implies that $S$ will always halt, then this is called **total verification**; $S$ is **totally correct** with respect to $\mathcal{I}$ and $\mathcal{O}$.

*This is important when $S$ involves iteration or recursion.*


###Theorem 1

1. If $\vdash \mathcal{I} \Rightarrow \mathcal{J}$ and $\{\mathcal{J}\}S\{\mathcal{O}\}$ is partially verified, then $\{\mathcal{I}\}S\{\mathcal{O}\}$ is partially verified.
2. If $\{\mathcal{I}\}S\{\mathcal{J}\}$ is partially verified and $\vdash \mathcal{J} \Rightarrow \mathcal{O}$, then $\{\mathcal{I}\}S\{\mathcal{O}\}$ is partially verified.

This can be abbreviated to:

$$\frac{ \mathcal{I} \Rightarrow \mathcal{J} , \{\mathcal{J}\}S\{\mathcal{O}\} }{ \{\mathcal{I}\}S\{\mathcal{O}\} }$$

and

$$\frac{ \{\mathcal{I}\}S\{\mathcal{J}\}, \mathcal{J} \Rightarrow \mathcal{O} }{ \{\mathcal{I}\}S\{\mathcal{O}\} }$$

##Assignment
The notation $S(b/a)$ means the same sentence as $S$ but with all instances of $a$ replaced by $b$.

$$\frac{ \mathcal{I} \Rightarrow \mathcal{O}(t/x) }{ \{\mathcal{I}\}\mathtt{x=t;}\{\mathcal{O}\} }$$

###Example

$$\{a > 0\} \mathtt{x = a - 1;} \{ x = a - 1 \land x \ge 0\}$$

$$\mathcal{O} = \{x = a - 1 \land x \ge 0\}$$

$$\mathcal{O}(a-1/x) = \{a - 1 = a - 1 \land a - 1 \ge 0\}$$

$$ a > 0 \Rightarrow a - 1 = a - 1 \land a - 1 \ge 0$$

$$\therefore \; a > 0 \Rightarrow \mathcal{O}(a-1/x)$$


##Statement Sequences
For a sequence of statements $S_1;S_2;\dots;S_n$, there is the rule:

$$\frac{ \{\mathcal{I}\}S_1\{\mathcal{J}_1\}, \{\mathcal{J}_1\}S_2\{\mathcal{J}_2\},\dots,\{\mathcal{J}_n\}S_n\{\mathcal{O}\} }{ \{\mathcal{I}\}S_1;S_2;\dots;S_n\{\mathcal{O}\} }$$


##Conditional Statements

$$\frac{ \{\mathcal{I} \land B\}S_1\{\mathcal{O}\}, \{\mathcal{I} \land \neg B\}S_2\{\mathcal{O}\} }{ \{\mathcal{I} \mathtt{ if(B) } S_1 \mathtt{ else } S_2 \{\mathcal{O}\} }$$

Under the assumption $B$ has no side effects.

If there is no `else` statement then:


$$\frac{ \{\mathcal{I} \land B\}S\{\mathcal{O}\}, \mathcal{I} \land \neg B \Rightarrow \mathcal{O} }{ \{\mathcal{I} \mathtt{ if(B) } S \{\mathcal{O}\} }$$

Again assuming $B$ has no side effects.


##Iterations

The while loop can be specified as follows:

$$\frac{ \{\mathcal{I} \land B\} S \{\mathcal{I}\} }{ \{\mathcal{I}\} \mathtt{ while(B) } S(\mathcal{I} \land \neg B) }$$

Assuming $B$ has no side effects.

It is useful to introduce the idea of a **loop invariant**; a formula ($\mathcal{L}$) that remains true after each iteration of the loop, leading to the following rule:

$$\frac{ \mathcal{I} \Rightarrow \mathcal{L}, \{\mathcal{L} \land  B\}S\{\mathcal{L}\}, \mathcal{L} \land \neg B \Rightarrow \mathcal{O} }{ \{\mathcal{I}\}\texttt{ while(B) } S \{\mathcal{O}\} }$$
