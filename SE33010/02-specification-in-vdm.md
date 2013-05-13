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
$$ \text{post } (r=i \lor r=j) \land i \le r \lor j \le r $$

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
* $\land$ conjunction (and), binary
* $\lor$ disjunction (or), binary
* $\Rightarrow$ implication (implies), binary
* $\Leftrightarrow$ equivalence (is equivalent to), binary

The syntax is simply:

```
proposition ::= letter
              | ¬proposition
              | proposition ∧ proposition
              | proposition V proposition
              | proposition -> proposition
              | proposition <-> proposition
              | (proposition)
```

Examples of valid wffs:

```
A,(A),¬A ∧ B
```

Precedence defined by the order. Note this is strict as no two operators have the same precedence.


####Implication

$$A \Rightarrow B$$

Consider:

$$ i = 2 \Rightarrow i^2 = 4 $$

When $i = 2$, both sides will be true. Resolves to true.

When $i = -2$ the left hand side will evaluate to false, the other to true. Resolves to true.

When $i = 1$ both sides are false, which resolves the implication to true.

For the final entry, consider $i=1 \Rightarrow i^2 = 4$

When $i = 1$ the left-hand side is true, the other false. Resolves to false.


$$ A \Rightarrow B \equiv \neg A \lor B $$


###Semantic Reasoning

Semantic reasoning leads to the idea of validity denoted by the double turnstile symbol $\models$

Let $P$ be a finite list of propositions - the *premises*. 

If, whenever all propositions of $P$ are true then the proposition $W$ is true, we say that $P$ provides the validity of $W$, written $P \models W$

If $P$ is empty then $\models W$ means that $W$ is always true and we say that $W$ is a tautology.

Propositions $P$ and $Q$ are logically equicalent if $\models P \Leftrightarrow Q$ (sometimes written $P \equiv Q$)


###Syntactic Reasoning/Formal Proof

In formal logic we are concerned with the syntatic derivations or **formal proofs**, rather than the meanings.

That is:

* We have a set of **axioms** - wffs which can be written without reference to any other wff in the language.
* A set of **inference rules** - rule which describe how wffs can be produces as *immediate consequences* of other wffs in the language.

A **derivation** or **formal proof** of the wff $W$ form a given set of wffs $P$ (the *premises*) is a finite sequence of wffs, each of which is either:

1. An axiom
2. A premise
3. An immediate consequence of one or more preceding wffs (as determined by the inference rules)

If there is such a derivation of $W$ from $P$ we write $P \vdash W$.

$\vdash$ is the single turnstyle, or syntactic turnstyle.

Applying formal proofs to propositional logic gives us the **propositional calculus**.

There are many choices of deductive system for the propositional calculus, the system outlined below is called a *Gentzen Natural Deductive System*.

####Some Inference Rules

$$\frac{A,B}{A \land B} \text{ and } \frac{A,B}{B \land A}\text{  }\land\text{-Introduction}$$

$$\frac{A \land B}{A} \text{ and } \frac{A \land B}{B} \text{  }\land\text{-Elimination}$$

$$\frac{A}{A \lor B} \text{ and } \frac{A}{B \lor A} \text{  }\lor\text{-Introduction}$$

etc.

####An Example

Show that $P \land Q \vdash P \lor Q$

Proof:


-  ----------  ------------------------
1  $P \land Q$  premise
2  $P$         1 by $\land$-Elimination
3  $P \lor Q$  2 by $\lor$-Introduction
-  ----------  ------------------------

Q.E.D.


####Another example

Show that $P,P \Rightarrow Q, Q\Leftrightarrow R \vdash Q \land R$


-  ---------------------------  -----------------------------------------
1  $P$                          premise
2  $P \Rightarrow Q$            premise
3  $Q \Leftrightarrow R$  premise
4  $Q$                          1,2 by $\Rightarrow$-Elimination
5  $Q \Rightarrow R$            3 by $\Leftrightarrow$-Elminiation
6  $R$                          4,5 by $\Rightarrow$-Elimination
7  $Q \land R$                   4,6 by $\land$-Introduction
-  ---------------------------  -----------------------------------------

Q.E.D.


Consistency and Completeness
----------------------------

The propositional calculus is boy **consistent** and **complete**.

**Consistency** If $P$ is any finite set of propositions and $W$ is a proposition such that $P \vdash W$ then $P \models W$

That is, anything which can be formally proved can be show... (*A: I give up see the slides*).


Application
-----------

Propositional logic can be applied to model the behaviour of digital electronic circuits. Used to reason about the behaviour of circuits, the decidability theorem implies that finite algorithms can be used to create the circuit.


Predicate Logic
---------------

We want to use logic to reason about the correctness of computer programs. To do this we need a language which is more powerful than the propositional logic. We introduce truth valued functions: *predicates*:

$$positive(counter)$$

Can have more than one argument:

$$bigger\_than(counter,total)$$

More conveniently, we write this in *infix* form as:

$$counter \lt total$$

The alphabet of the predicate is that for propositional logic, extended by lower case letters, the symbols $\forall$ $\exists$ $\bullet$, and arbitary strings of letters (upper or lower case).

$\forall x$ is read "for all $x$"

$\exists x$ is read "there exists $x$"


VDM
===

###Built in Sets

**B** = booleans

**N** = Unsigned integers starting at 0

$\text{N}_1$ = Unsigned integers starting at 1

**Z** = Signed integers

###Some example notation

$$ \_ + \_ : Z \times Z \rightarrow Z $$

$$ \_ mod \_ : N \times N_1 \rightarrow B $$


Proof Obligation for Functions
------------------------------

Suppose we have an implicit specification:

$$f(p:T_p)r:T_r$$

`pre pre-f(p)`

`post post-f(p,r)`

$$ f:T_P \rightarrow T_r$$



Suppose we have to define multiplication:

$$ multp(i,j)  $$

```
  if   i = 0
  then 0
  else if   is-even(i)
    then 2 * multp(i/2, j)
    else j + multp(i-1, j)
```

Then the proof obligation becomes:

$$ \forall i,j \in \text{N} \bullet multp(i,j) \in \text{N} \land multp(i,j) = i \times j $$


Partial Functions
-----------------

Consider:

$$ subp(i:\text{N}, j:\text{N})r:\text{N} $$

```
pre j <= i
post r + j = i
```

An explicit definition of $subp$ will generate the following proof obligation:

$$ \forall i,j:\text{N} \bullet \text{pre} - subp (i,j) \Rightarrow subp(i,j) \in \text{N} \land \text{post} - subp(i,j) $$

i.e.

$$ \forall i,j:\text{N} \bullet j \le i \Rightarrow subp(i,j) \in \text{N} \land subp(i,j) + i = j$$

Can't complete this evaluation; when $j$ is bigger than $i$ this equation is undefined.

However, using **Logic of Partial Functions** (LPF):

1. If $j \le i$ the implication becomes $\text{T} \Rightarrow \text{T} \land \text{T}$ which evaluates to **T**.
2. If $j \gt i$ the implication becomes $\text{F} \Rightarrow \text{* } \land \text{ *}$ which evaluates to **T**.

The "Law of the Excluded Middle" ($\vdash P \lor \neg P$) clearly does not hold in LPF.

This is, in fact, a virtue with partially defined functions, for example, there is no reason for:

$$ \frac{2}{0} = 1 \lor \frac{2}{0} \ne 1 $$

However, we do get useful results like:

$$\forall n \bullet n \in \text{Z} \Rightarrow n = 0 \lor \frac{n}{n} = 1 $$

Another rule which doesn't hold in LPF is $\vdash P \Rightarrow P$.


Domain of Interest
------------------

The domain of interest can now be defined rigorously by specifigying over which set the bound variables range.

For example

$$ \exists x \bullet x \gt 4$$

Can be more precisely specifed by

$$ \exists x \bullet x \in \text{N} \land x \gt 4 $$

The expression still has meaning when $x \gt 4$ is undefined.

So, in future, we will always quantify over some set and we introduce an avvreviated notation:

$$ \forall x \in S \bullet P(x) \text{for} \forall x \bullet \in S \Rightarrow P(x) $$


States and Operations
---------------------

Functions may not have side effects, instead we have **states** and **operations** on the states.

Example:

```
state Register as
    reg: N
end

LOAD(i:n)
ext wr reg:N
post reg = i
```

The exterior clause (`ext`) specifies which parts of the state can be accessed by the operation.

* `rd` means read access
* `wr` means write access (implies read access)

Operation labels landitalised by convention.

Hooked variables denote the value of that variable prior to the execution of the operation.

Returning works like:

```
SHOW()r:N
ext rd reg:N
post r = reg
```

Can also have `pre-OP` and `post-OP`.


Data Types
----------

Predefined sets: **B**, **N**, **N**1, **Z**, **Q**, **R**.

For a set *X*, *X-set* is the set of all finite subsets of *X*.

e.g.: **B**-set = {{},{true},{false},{true,false}}

A useful abbreviation for sets of integers is:

$$\{i,...,j\}=\{ k \in Z \ldots$$

VDM-SL admits a lot of useful set operations.

Type of `To Be Defined` is allowed and just means the type is defined somewhere else.

**Just a note:** no concurrency in VDM so you don't have to worry about locking.

###Composite Type

The general form of a composite type definition is:

```
Name ::
  s1 : T1
  s2 : T2
  .
  .
  .
  sn : Tn
```

This type has associated with it the constructor:

```
mk-Nam : T1 x T2 x ... x Tn -> Name
```

And selector functions:

```
s1 : Name -> T1
s2 : Name -> T2
.
.
.
sn : Name -> Tn
```

Example:

```
Date ::
  day : {1,...,366}
  year : {1901,...,2099}
```

Automatically gives us these functions:

```
mk-Date({1,...,366} x {1901,...,2099} -> Date
day : Date -> {1,.366}
year : Date -> {1901, 2099}
```

For example: `mk-date{45,2003}`

There is the problem of leap years in this example. So we might want a function `valid-Date : Date -> B` to determine whether a date is actually valid.

```
valid-Date(dt) ? is-leapyear(year(dt)) V day(dt) <= 365

is-leapyear(i) ? i mod 4 = 0
```

Alternatively:

```
valid-Date(dt) ?
  let mk-Date(d,y) = dt
  in is-leapyear(y) V d <= 365
```

**Note:** Because of the restricted year range our definition of leap year works.

Data type **invariants** can be added to composite types using the construction:

```
Date ::
  day : {1,...,366}
  year : {1901,...,2099}
where
  inv-Date(mk-Date(d,y)) ? is-leapyear(y) V d <= 365
```

Now only valid dates will be allowed on the constructor.

####Optional Fields

Optional fields are allowed in composite types, denoted by `[...]`, and an omitted field is denoted by `nil`:

```
Record ::
  day : {1,...,366}
  year : {1901,...,2099}
  valid : [ERROR]
```

Useful for recursive data types.

###Recursive Data Definitions

```
List = [Listelt]
Listelt ::
  hd : N
  tl : List

nil in List
mk-Listelt(3,nil) in List
mk-Listelt(1,mk-Listelt(2,mk-Listelt(3,nil))) in List

lsum : List -> N
lsum(l) ?
  cases l:
    nil -> 0
    mk-Listelt(hd,tl) -> hd + lsum(tl)
  end
```

####Binary Search Tree Example

```
Tree = [Node]
Node ::
  left : Tree
  value : N
  right : Tree
where
  inv-Node(mk-Node(left,value,right)) ?
    (forall(lv) in values(left) assert lv < value) and (forall(rv) in values(right) assert value < rv)
values : Tree -> N-set
values(t) ?
  cases t of
    nil -> {}
    mk-Node(left,value,right) -> values(left) union {value} union values(right)
```


Maps
----

A **map** is similar to a function defined on a finite set, except that the argument:result pairs are given explicitly.

e.g.: $\left\{{a_1 \mapsto r_1, a_2 \mapsto r_2,\ldots ,a_n \mapsto r_n}\right\}$

$$\left\{{x \mapsto f(x)|P(x)}\right\}$$

Denoted by

$$ X \rightarrow^{m} Y $$

###Map Overriding

$$m_1 \dagger m_2$$

$m_2$ overrides elements in $m_1$. If an element in exists in both $m_1$ and $m_2$ then the return from $m_2$ is used, otherwise it's just the union of the two maps.


Sequences
---------

Given a type $X$, we can have *sequences* of elements of $X$.

The types of such sequences is denoted by $X*$

Sequences are denoted by:

$$\left[ a,b,c \right]$$

Where:

$$ a,b,c, \in X $$


###Operations

------------------------ ----------------------------- --------------------
$hd\_$                   $X* \rightarrow X$            head (first element)
$tl\_$                   $X* \rightarrow X*$           tail
$len\_$                  $X* \rightarrow N$            length
$elems\_$                $X* \rightarrow X\text{-set}$ set of elements
$\_(\_)$                 $X \times N_1 \rightarrow X$  element selection
$\_ \curvearrowright \_$ 
------------------------ ----------------------------- --------------------


