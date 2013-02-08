The Vienna Development Method
=============================

Early 1960's, IBM Vienna Laboratory, working on the formal definition PL/1 (in cooperation with IBM UK Labs. Hursley).

Metalanguage then known as VDL (Vienna Definition Language).

1974, Formal description of PL/1, notation used became known as *META-VI*.

Key developers:

* Dines Bjørner
* Cliff D Jones

The notation evolved with time, essential an "English School" and a "Danish School".

Later developments:

* STC VDM Reference Language
* Rigorous Approach to Industrial Software Engineering (RAISE) Specification Language (RSL)

Then standardised into:

* BSI VDM Specification Language (VSL)
* International Standards ISO/IEC 13817-1, December 1996: "Vienna Development Methods - Specification Language - Part I: Base Language"


VDM as a Development Method
---------------------------

Start with a (very) abstract specification and build an implementation from it.

Uses *data reification* and *program decomposition*, both of which are accompanied by *proof obligations*

Specification defines Abstract data types and are reifoicated to data structures in the implementation.

Specification also defines operations are decomposed to algorithms.


Specification in VDM
--------------------


### Functions

Uses implicit declaration.

Has:

* Signature, the name of the function
* Pre-condition, must be true on entering the function.
* Post-condition, must be true on exiting the function

Example:


$$ \text{max}(i:Z,j:Z)r:Z $$
$$ \text{pre } true $$
$$ \text{post } (r=i \cup r=j) \cap i \le r \cup j \le r $$

Can refer to pre- or post-condition out of context, we can use the notation: `pre-max` and `post-max`.

So a specification with the signature:

$$ f(p:Tp)r:Tr $$

Corresponds to a function

$$ f \rightarrow Tp, Tr $$


Advantages of Implicit Specification
------------------------------------

* Direct statement of multiple properties of interest to the user.
* Characterising a set of possible results by a post-condition.
* Explicit pre-condition.
* Less commitment to a specific algorithm.
* A direct naming of the result.


Example of implicit specification
---------------------------------

$$ \text{sqrt}(x:R)r:R $$
$$ \text{pre } x \ge 0 $$
$$ \text{post } abs(x-r^2) \lt 10^{-8} $$

Now, suppose we want to find the forth root function, we might try to use `sqrt` twice.

$$ y = \text{sqrt}(x) $$
$$ z = \text{sqrt}(y) $$

For this to work wee need

$$ \text{post-S1} \Rightarrow \text{pre-S2} $$

i.e.

$$ abs(x-y^2) \lt 10 ^ {-8} \Rightarrow y \ge 0 $$

Clearly, this is not true because a negative $y$ could satisfy the left-hand side of the implication, but not the right.


Formal Logic
------------

A **formal language** is:

* A set of symbols - the **alphabet** of the language, and
* A set of rules to specify how the symbols together - the **syntax**.

An acceptable string of symbols is a **well formed formular (wff)** of that language.

The **sematics** of a formal language is specified by attaching a meaning to each wff admitted by the syntax.

###Propositional Logic

Uses truth-valued quantities.
$$ A, B, ..., Z $$

Normal brackets $($ and $)$.

* $\neg$ negation (not), unary
* $\cap$ conjunction (and), binary
* $\cup$ disjunction (or), binary
* $\Rightarrow$ implication (implies), binary
* $\Leftarrow\Rightarrow$ equivalence (is equivalent to), binary

The syntax is simply:

```
proposition		::= letter
				 | ¬proposition
				 | proposition ∧ proposition
				 | ptopodiyion V proposition
				 | proposition -> proposition
				 | proposition <-> proposition
				 | (proposition)
```

Examples of valid wffs:

```
A,(A),¬A ∧ B
```
Precedence defined by the order. Note this is strict as no two operators have the same precedence. This allows us to get rid of brackets.

####Implication

$$A \Rightarrow B$$

Consider:

$$ i = 2 \Rightarrow i^2 = 4 $$

When $i = 2$, both sides will be true. Resolves to true.
When $i = -2$ the left hand side will evaluate to false, the other to true. Resolves to true.
When $i = 1$ both sides are false, which resolves the implication to true.

For the final entry, consider $i=1 \Rightarrow i^2 = 4 $$

When $i = 1$ the left-hand side is true, the other false. Resolves to false.


$$ A \Rightarrow B \equiv \neg A \cup B $$


