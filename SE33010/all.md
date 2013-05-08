SE33010 - Formal Methods in Software Engineering
================================================

Fred Long (fwl). 

The use of mathematical formal methods in software specification and techniques for producing reliable software.

**Reminder:** Fred has a good lecturing style :)

You will need to put effort in to succeed. Not all mathematics (but there is a fair amount).

Links on blackboard to books (both out of print).


Assessment
----------

* 80% Exam
* 10% Written Assignment
* 10% Written Assignment

Also $\approx 3$ un-assessed worksheets in workshops.


Why do we need formal methods?
------------------------------

Bugs are common in software.

Legal requirement to report vulnerabilities (vulnerabilities are a special class of bug).

> "If debugging is the process of taking out bugs, programming must be the process of putting them in."

Cannot prove the absence of bugs by testing software. Need to be able to prove there are no bugs in the software $\rightarrow$ prove the software is correct. Mathematical techniques can begin to do this.

Few example of where this has been done successfully:

* Metro lines in Paris (14) Oct. 1998 has an automatic train control system was developed on time, in budget and was proved to be 100% correct using formal proof.
* A real time air-traffic control system used VDM, developed for London airports. Productivity of developers: 13 lines per person per day compared to 7. Wasn't proved to be correct - 35% reduction in defects. Industry standard: 1 defect per 1000 lines of code.
* BMW/Rolls Royce test facility used Z notation for certification testing of the electronic control system.
* NASA international space system fault detection system, irregularities discovered early in development using formal methods.
* IEEE reporting on experience from a student group project. Two classes of groups of students, one using formal development, one using traditional development (small groups, 2 students per group). 45.5% of traditional groups passed testing, 100% of formal groups passed testing.


<h1 id="se33010---formal-methods-in-software-engineering">SE33010 - Formal Methods in Software Engineering</h1>
<p>Fred Long (fwl).</p>
<p>The use of mathematical formal methods in software specification and techniques for producing reliable software.</p>
<p><strong>Reminder:</strong> Fred has a good lecturing style :)</p>
<p>You will need to put effort in to succeed. Not all mathematics (but there is a fair amount).</p>
<p>Links on blackboard to books (both out of print).</p>
<h2 id="assessment">Assessment</h2>
<ul>
<li>80% Exam</li>
<li>10% Written Assignment</li>
<li>10% Written Assignment</li>
</ul>
<p>Also <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Capprox%203" alt="\approx 3" title="\approx 3" /> un-assessed worksheets in workshops.</p>
<h2 id="why-do-we-need-formal-methods">Why do we need formal methods?</h2>
<p>Bugs are common in software.</p>
<p>Legal requirement to report vulnerabilities (vulnerabilities are a special class of bug).</p>
<blockquote>
<p>&quot;If debugging is the process of taking out bugs, programming must be the process of putting them in.&quot;</p>
</blockquote>
<p>Cannot prove the absence of bugs by testing software. Need to be able to prove there are no bugs in the software <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Crightarrow" alt="\rightarrow" title="\rightarrow" /> prove the software is correct. Mathematical techniques can begin to do this.</p>
<p>Few example of where this has been done successfully:</p>
<ul>
<li>Metro lines in Paris (14) Oct. 1998 has an automatic train control system was developed on time, in budget and was proved to be 100% correct using formal proof.</li>
<li>A real time air-traffic control system used VDM, developed for London airports. Productivity of developers: 13 lines per person per day compared to 7. Wasn't proved to be correct - 35% reduction in defects. Industry standard: 1 defect per 1000 lines of code.</li>
<li>BMW/Rolls Royce test facility used Z notation for certification testing of the electronic control system.</li>
<li>NASA international space system fault detection system, irregularities discovered early in development using formal methods.</li>
<li>IEEE reporting on experience from a student group project. Two classes of groups of students, one using formal development, one using traditional development (small groups, 2 students per group). 45.5% of traditional groups passed testing, 100% of formal groups passed testing.</li>
</ul>
Introduction to Logic
=====================

Formalisation of Software Development
-------------------------------------

1. User's ideas
2. Requirements Specification
3. System specification
4. Programs
5. Executable Machine Code

Last step is often automated. Idea of formal methods is to move the automation up (use tools to automatically generate code).

To do this the specification must be amenable to processing (cannot be a natural language).

Need to use a "formal" specification language.

There is some research into introducing formal notations for requirement specification, but of course (accept in very few examples) you're never going to be able to completely automate this process.

Ideas are very difficult to formalise.

This module focuses on a formal definition for a system specification.

Compilers can be completely automated from requirements.


Specification
-------------

A specification should be:

* Concise
* Complete
* Consistent

May go through several stages and may come in a number of pieces.

It is important to maintain consistency between stages of specification, traditional methods of software development make this difficult. This is because of the large, natural language nature of the traditional specification (relies on humans to ensure consistency).

Mathematical methods of specification can help with this. This definitely addresses the issue of being concise (downside on people not being familiar with the notion). Big advantage is the use of software tools to analyse the specification for consistency, may be able to have a check for completeness. Some chance of being able to check for missing elements of the specification.



Advantages of Formal Specification
----------------------------------

* Makes you think. Natural languages allow for "sloppiness". Constrained about things like integer values, etc. This is surprisingly important and is often overlooked.
* Unambiguous language. Natural language is very context sensitive.
* May be autonomous. From formal specification it may be possible to generate code, for example. Can lead to inefficient code, this might be used as a prototype rather than end product.
* Automated test data. Very likely to pick up boundary cases where software is likely to go wrong.
* Can be proved to be correct rather than tested. Testing is still important and does a different job. This might make unit testing redundant.
* Errors detected earlier.
* Adapt to changing requirements more reliably. Can also introduce metrics of how it will affect the system.
* Very good for rapid prototyping.

Disadvantages of Formal Specification
-------------------------------------

* Specification difficult to communicate to users. Difficult to get "sign-off".
* Highly specialised workforce.
* May sacrifice efficiency if used blindly. If applied properly it should be just as efficient.
* May need sophisticated (*read: expensive*) tools.
* May need additional computing facilities (theorem provers ran on specialised hardware). Lately this is less of a problem, but most tools are very resource intensive.


###Note on terminology

Sometimes "formal methods" may be via the use of documentation and/or coding standards. In this course we are talking about a Mathematically formal specification.


Approaches to a Formal Specification
------------------------------------

Two approaches

* Algebraic (axiomatic)
* Model-based (operational)

An algebraic specification defines a mathematical object in terms of relations among the operations defined over the object. In many ways this is more abstract

A model-based approach is an explicit system model constructed from abstract or concrete primitives (think of this as another programming language).

Focus on model-based specifications, particularly VDN.


###Example of Algebraic Specification

Example of a boolean type.

```
INITIAL
		boolean

SORT
		bool

CONSTANTS
		true		: bool
		false		: bool

OPERATIONS
		not _		: bool -> bool
		_ or _		: bool, bool -> bool
		_ and _		: bool, bool -> bool
		_ impl _	: bool, bool -> bool
		_equiv _	: bool, bool -> bool

EQUATIONS
		not(not(A))	= A
		A or (B or C)	= (A or B) or C
		A or B		= B or A
		A or true	= true
		A or false	= A
		A and B		= not(not(A) or not(b))
		A impl B	= not(A) or B
		A equiv B	= (A impl B) and (B impl A)
END
```

`INITIAL` means that there are no values or relations other than those which can be deduced from the given ones, for example one can deduce that `A and B = B and A`, buy not `true = false`.

The mathematical branch of *category theory* is needed to reason about such specifications.


```
INITIAL
		lists (elem with {_ eq _ : elem,elem -> bool; undef : -> elem})

USES
		boolean

SORT
		list

CONSTANTS
		empty	: list
		undef	: list

OPERATIONS
		_ . _			: elem,list -> list
		first _			: list -> elem
		rest _			: list -> list
		is-undef _		: list -> bool
		_ is-member-of _	: elem,list -> bool
		_ eq _ 			: list,list -> bool
		at-end _		: list -> bool

EQUATIONS
		first(empty)		= undef
		first(undef)		= undef
		first(A.B)		= A
		rest(empty)		= undef
		rest(undef)		= undef
		rest(A.B)		= B
		is-undef(empty)		= false
		is-undef(undef)		= true
		is-undef(A.B)		= false
		E is-member-of undef	= false
		E is-member-of empty	= false
		E is-member-of (A.B)	= (E eq A) or (E is-member-of B)
		(A.B) eq (C.D)		= (A eq C) and (B eq D)
		empty eq empty		= true
		(A.B) eq empty		= false
		A eq B			= B eq A
		at-end(empty)		= true
		at-end(undef)		= false
		at-end(A.B)		= false
END
```


<h1 id="introduction-to-logic">Introduction to Logic</h1>
<h2 id="formalisation-of-software-development">Formalisation of Software Development</h2>
<ol style="list-style-type: decimal">
<li>User's ideas</li>
<li>Requirements Specification</li>
<li>System specification</li>
<li>Programs</li>
<li>Executable Machine Code</li>
</ol>
<p>Last step is often automated. Idea of formal methods is to move the automation up (use tools to automatically generate code).</p>
<p>To do this the specification must be amenable to processing (cannot be a natural language).</p>
<p>Need to use a &quot;formal&quot; specification language.</p>
<p>There is some research into introducing formal notations for requirement specification, but of course (accept in very few examples) you're never going to be able to completely automate this process.</p>
<p>Ideas are very difficult to formalise.</p>
<p>This module focuses on a formal definition for a system specification.</p>
<p>Compilers can be completely automated from requirements.</p>
<h2 id="specification">Specification</h2>
<p>A specification should be:</p>
<ul>
<li>Concise</li>
<li>Complete</li>
<li>Consistent</li>
</ul>
<p>May go through several stages and may come in a number of pieces.</p>
<p>It is important to maintain consistency between stages of specification, traditional methods of software development make this difficult. This is because of the large, natural language nature of the traditional specification (relies on humans to ensure consistency).</p>
<p>Mathematical methods of specification can help with this. This definitely addresses the issue of being concise (downside on people not being familiar with the notion). Big advantage is the use of software tools to analyse the specification for consistency, may be able to have a check for completeness. Some chance of being able to check for missing elements of the specification.</p>
<h2 id="advantages-of-formal-specification">Advantages of Formal Specification</h2>
<ul>
<li>Makes you think. Natural languages allow for &quot;sloppiness&quot;. Constrained about things like integer values, etc. This is surprisingly important and is often overlooked.</li>
<li>Unambiguous language. Natural language is very context sensitive.</li>
<li>May be autonomous. From formal specification it may be possible to generate code, for example. Can lead to inefficient code, this might be used as a prototype rather than end product.</li>
<li>Automated test data. Very likely to pick up boundary cases where software is likely to go wrong.</li>
<li>Can be proved to be correct rather than tested. Testing is still important and does a different job. This might make unit testing redundant.</li>
<li>Errors detected earlier.</li>
<li>Adapt to changing requirements more reliably. Can also introduce metrics of how it will affect the system.</li>
<li>Very good for rapid prototyping.</li>
</ul>
<h2 id="disadvantages-of-formal-specification">Disadvantages of Formal Specification</h2>
<ul>
<li>Specification difficult to communicate to users. Difficult to get &quot;sign-off&quot;.</li>
<li>Highly specialised workforce.</li>
<li>May sacrifice efficiency if used blindly. If applied properly it should be just as efficient.</li>
<li>May need sophisticated (<em>read: expensive</em>) tools.</li>
<li>May need additional computing facilities (theorem provers ran on specialised hardware). Lately this is less of a problem, but most tools are very resource intensive.</li>
</ul>
<h3 id="note-on-terminology">Note on terminology</h3>
<p>Sometimes &quot;formal methods&quot; may be via the use of documentation and/or coding standards. In this course we are talking about a Mathematically formal specification.</p>
<h2 id="approaches-to-a-formal-specification">Approaches to a Formal Specification</h2>
<p>Two approaches</p>
<ul>
<li>Algebraic (axiomatic)</li>
<li>Model-based (operational)</li>
</ul>
<p>An algebraic specification defines a mathematical object in terms of relations among the operations defined over the object. In many ways this is more abstract</p>
<p>A model-based approach is an explicit system model constructed from abstract or concrete primitives (think of this as another programming language).</p>
<p>Focus on model-based specifications, particularly VDN.</p>
<h3 id="example-of-algebraic-specification">Example of Algebraic Specification</h3>
<p>Example of a boolean type.</p>
<pre><code>INITIAL
        boolean

SORT
        bool

CONSTANTS
        true        : bool
        false       : bool

OPERATIONS
        not _       : bool -&gt; bool
        _ or _      : bool, bool -&gt; bool
        _ and _     : bool, bool -&gt; bool
        _ impl _    : bool, bool -&gt; bool
        _equiv _    : bool, bool -&gt; bool

EQUATIONS
        not(not(A)) = A
        A or (B or C)   = (A or B) or C
        A or B      = B or A
        A or true   = true
        A or false  = A
        A and B     = not(not(A) or not(b))
        A impl B    = not(A) or B
        A equiv B   = (A impl B) and (B impl A)
END</code></pre>
<p><code>INITIAL</code> means that there are no values or relations other than those which can be deduced from the given ones, for example one can deduce that <code>A and B = B and A</code>, buy not <code>true = false</code>.</p>
<p>The mathematical branch of <em>category theory</em> is needed to reason about such specifications.</p>
<pre><code>INITIAL
        lists (elem with {_ eq _ : elem,elem -&gt; bool; undef : -&gt; elem})

USES
        boolean

SORT
        list

CONSTANTS
        empty   : list
        undef   : list

OPERATIONS
        _ . _           : elem,list -&gt; list
        first _         : list -&gt; elem
        rest _          : list -&gt; list
        is-undef _      : list -&gt; bool
        _ is-member-of _    : elem,list -&gt; bool
        _ eq _          : list,list -&gt; bool
        at-end _        : list -&gt; bool

EQUATIONS
        first(empty)        = undef
        first(undef)        = undef
        first(A.B)      = A
        rest(empty)     = undef
        rest(undef)     = undef
        rest(A.B)       = B
        is-undef(empty)     = false
        is-undef(undef)     = true
        is-undef(A.B)       = false
        E is-member-of undef    = false
        E is-member-of empty    = false
        E is-member-of (A.B)    = (E eq A) or (E is-member-of B)
        (A.B) eq (C.D)      = (A eq C) and (B eq D)
        empty eq empty      = true
        (A.B) eq empty      = false
        A eq B          = B eq A
        at-end(empty)       = true
        at-end(undef)       = false
        at-end(A.B)     = false
END</code></pre>
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


<h1 id="the-vienna-development-method">The Vienna Development Method</h1>
<p>Early 1960's, IBM Vienna Laboratory, working on the formal definition PL/1 (in cooperation with IBM UK Labs. Hursley).</p>
<p>Metalanguage then known as VDL (Vienna Definition Language).</p>
<p>1974, Formal description of PL/1, notation used became known as <em>META-VI</em>.</p>
<p>Key developers:</p>
<ul>
<li>Dines Bjørner</li>
<li>Cliff D Jones</li>
</ul>
<p>The notation evolved with time, essential an &quot;English School&quot; and a &quot;Danish School&quot;.</p>
<p>Later developments:</p>
<ul>
<li>STC VDM Reference Language</li>
<li>Rigorous Approach to Industrial Software Engineering (RAISE) Specification Language (RSL)</li>
</ul>
<p>Then standardised into:</p>
<ul>
<li>BSI VDM Specification Language (VSL)</li>
<li>International Standards ISO/IEC 13817-1, December 1996: &quot;Vienna Development Methods - Specification Language - Part I: Base Language&quot;</li>
</ul>
<h2 id="vdm-as-a-development-method">VDM as a Development Method</h2>
<p>Start with a (very) abstract specification and build an implementation from it.</p>
<p>Uses <em>data reification</em> and <em>program decomposition</em>, both of which are accompanied by <em>proof obligations</em></p>
<p>Specification defines Abstract data types and are reifoicated to data structures in the implementation.</p>
<p>Specification also defines operations are decomposed to algorithms.</p>
<h2 id="specification-in-vdm">Specification in VDM</h2>
<h3 id="functions">Functions</h3>
<p>Uses implicit declaration.</p>
<p>Has:</p>
<ul>
<li>Signature, the name of the function</li>
<li>Pre-condition, must be true on entering the function.</li>
<li>Post-condition, must be true on exiting the function</li>
</ul>
<p>Example:</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20%5Ctext%7Bmax%7D%28i%3AZ%2Cj%3AZ%29r%3AZ%20" alt=" \text{max}(i:Z,j:Z)r:Z " title=" \text{max}(i:Z,j:Z)r:Z " /><br /> <br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20%5Ctext%7Bpre%20%7D%20true%20" alt=" \text{pre } true " title=" \text{pre } true " /><br /> <br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20%5Ctext%7Bpost%20%7D%20%28r%3Di%20%5Clor%20r%3Dj%29%20%5Cland%20i%20%5Cle%20r%20%5Clor%20j%20%5Cle%20r%20" alt=" \text{post } (r=i \lor r=j) \land i \le r \lor j \le r " title=" \text{post } (r=i \lor r=j) \land i \le r \lor j \le r " /><br /></p>
<p>Can refer to pre- or post-condition out of context, we can use the notation: <code>pre-max</code> and <code>post-max</code>.</p>
<p>So a specification with the signature:</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20f%28p%3ATp%29r%3ATr%20" alt=" f(p:Tp)r:Tr " title=" f(p:Tp)r:Tr " /><br /></p>
<p>Corresponds to a function</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20f%20%5Crightarrow%20Tp%2C%20Tr%20" alt=" f \rightarrow Tp, Tr " title=" f \rightarrow Tp, Tr " /><br /></p>
<h2 id="advantages-of-implicit-specification">Advantages of Implicit Specification</h2>
<ul>
<li>Direct statement of multiple properties of interest to the user.</li>
<li>Characterising a set of possible results by a post-condition.</li>
<li>Explicit pre-condition.</li>
<li>Less commitment to a specific algorithm.</li>
<li>A direct naming of the result.</li>
</ul>
<h2 id="example-of-implicit-specification">Example of implicit specification</h2>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20%5Ctext%7Bsqrt%7D%28x%3AR%29r%3AR%20" alt=" \text{sqrt}(x:R)r:R " title=" \text{sqrt}(x:R)r:R " /><br /> <br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20%5Ctext%7Bpre%20%7D%20x%20%5Cge%200%20" alt=" \text{pre } x \ge 0 " title=" \text{pre } x \ge 0 " /><br /> <br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20%5Ctext%7Bpost%20%7D%20abs%28x-r%5E2%29%20%5Clt%2010%5E%7B-8%7D%20" alt=" \text{post } abs(x-r^2) \lt 10^{-8} " title=" \text{post } abs(x-r^2) \lt 10^{-8} " /><br /></p>
<p>Now, suppose we want to find the forth root function, we might try to use <code>sqrt</code> twice.</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20y%20%3D%20%5Ctext%7Bsqrt%7D%28x%29%20" alt=" y = \text{sqrt}(x) " title=" y = \text{sqrt}(x) " /><br /> <br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20z%20%3D%20%5Ctext%7Bsqrt%7D%28y%29%20" alt=" z = \text{sqrt}(y) " title=" z = \text{sqrt}(y) " /><br /></p>
<p>For this to work wee need</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20%5Ctext%7Bpost-S1%7D%20%5CRightarrow%20%5Ctext%7Bpre-S2%7D%20" alt=" \text{post-S1} \Rightarrow \text{pre-S2} " title=" \text{post-S1} \Rightarrow \text{pre-S2} " /><br /></p>
<p>i.e.</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20abs%28x-y%5E2%29%20%5Clt%2010%20%5E%20%7B-8%7D%20%5CRightarrow%20y%20%5Cge%200%20" alt=" abs(x-y^2) \lt 10 ^ {-8} \Rightarrow y \ge 0 " title=" abs(x-y^2) \lt 10 ^ {-8} \Rightarrow y \ge 0 " /><br /></p>
<p>Clearly, this is not true because a negative <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=y" alt="y" title="y" /> could satisfy the left-hand side of the implication, but not the right.</p>
<h2 id="formal-logic">Formal Logic</h2>
<p>A <strong>formal language</strong> is:</p>
<ul>
<li>A set of symbols - the <strong>alphabet</strong> of the language, and</li>
<li>A set of rules to specify how the symbols together - the <strong>syntax</strong>.</li>
</ul>
<p>An acceptable string of symbols is a <strong>well formed formular (wff)</strong> of that language.</p>
<p>The <strong>sematics</strong> of a formal language is specified by attaching a meaning to each wff admitted by the syntax.</p>
<h3 id="propositional-logic">Propositional Logic</h3>
<p>Uses truth-valued quantities. <br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20A%2C%20B%2C%20...%2C%20Z%20" alt=" A, B, ..., Z " title=" A, B, ..., Z " /><br /></p>
<p>Normal brackets <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%28" alt="(" title="(" /> and <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%29" alt=")" title=")" />.</p>
<ul>
<li><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cneg" alt="\neg" title="\neg" /> negation (not), unary</li>
<li><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cland" alt="\land" title="\land" /> conjunction (and), binary</li>
<li><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Clor" alt="\lor" title="\lor" /> disjunction (or), binary</li>
<li><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5CRightarrow" alt="\Rightarrow" title="\Rightarrow" /> implication (implies), binary</li>
<li><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5CLeftrightarrow" alt="\Leftrightarrow" title="\Leftrightarrow" /> equivalence (is equivalent to), binary</li>
</ul>
<p>The syntax is simply:</p>
<pre><code>proposition     ::= letter
                 | ¬proposition
                 | proposition ∧ proposition
                 | ptopodiyion V proposition
                 | proposition -&gt; proposition
                 | proposition &lt;-&gt; proposition
                 | (proposition)</code></pre>
<p>Examples of valid wffs:</p>
<pre><code>A,(A),¬A ∧ B</code></pre>
<p>Precedence defined by the order. Note this is strict as no two operators have the same precedence.</p>
<h4 id="implication">Implication</h4>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=A%20%5CRightarrow%20B" alt="A \Rightarrow B" title="A \Rightarrow B" /><br /></p>
<p>Consider:</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20i%20%3D%202%20%5CRightarrow%20i%5E2%20%3D%204%20" alt=" i = 2 \Rightarrow i^2 = 4 " title=" i = 2 \Rightarrow i^2 = 4 " /><br /></p>
<p>When <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=i%20%3D%202" alt="i = 2" title="i = 2" />, both sides will be true. Resolves to true.</p>
<p>When <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=i%20%3D%20-2" alt="i = -2" title="i = -2" /> the left hand side will evaluate to false, the other to true. Resolves to true.</p>
<p>When <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=i%20%3D%201" alt="i = 1" title="i = 1" /> both sides are false, which resolves the implication to true.</p>
<p>For the final entry, consider <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=i%3D1%20%5CRightarrow%20i%5E2%20%3D%204" alt="i=1 \Rightarrow i^2 = 4" title="i=1 \Rightarrow i^2 = 4" /></p>
<p>When <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=i%20%3D%201" alt="i = 1" title="i = 1" /> the left-hand side is true, the other false. Resolves to false.</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20A%20%5CRightarrow%20B%20%5Cequiv%20%5Cneg%20A%20%5Clor%20B%20" alt=" A \Rightarrow B \equiv \neg A \lor B " title=" A \Rightarrow B \equiv \neg A \lor B " /><br /></p>
<h3 id="semantic-reasoning">Semantic Reasoning</h3>
<p>Semantic reasoning leads to the idea of validity denoted by the double turnstile symbol <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cmodels" alt="\models" title="\models" /></p>
<p>Let <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P" alt="P" title="P" /> be a finite list of propositions - the <em>premises</em>.</p>
<p>If, whenever all propositions of <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P" alt="P" title="P" /> are true then the proposition <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=W" alt="W" title="W" /> is true, we say that <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P" alt="P" title="P" /> provides the validity of <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=W" alt="W" title="W" />, written <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P%20%5Cmodels%20W" alt="P \models W" title="P \models W" /></p>
<p>If <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P" alt="P" title="P" /> is empty then <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cmodels%20W" alt="\models W" title="\models W" /> means that <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=W" alt="W" title="W" /> is always true and we say that <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=W" alt="W" title="W" /> is a tautology.</p>
<p>Propositions <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P" alt="P" title="P" /> and <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=Q" alt="Q" title="Q" /> are logically equicalent if <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cmodels%20P%20%5CLeftrightarrow%20Q" alt="\models P \Leftrightarrow Q" title="\models P \Leftrightarrow Q" /> (sometimes written <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P%20%5Cequiv%20Q" alt="P \equiv Q" title="P \equiv Q" />)</p>
<h3 id="syntactic-reasoningformal-proof">Syntactic Reasoning/Formal Proof</h3>
<p>In formal logic we are concerned with the syntatic derivations or <strong>formal proofs</strong>, rather than the meanings.</p>
<p>That is:</p>
<ul>
<li>We have a set of <strong>axioms</strong> - wffs which can be written without reference to any other wff in the language.</li>
<li>A set of <strong>inference rules</strong> - rule which describe how wffs can be produces as <em>immediate consequences</em> of other wffs in the language.</li>
</ul>
<p>A <strong>derivation</strong> or <strong>formal proof</strong> of the wff <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=W" alt="W" title="W" /> form a given set of wffs <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P" alt="P" title="P" /> (the <em>premises</em>) is a finite sequence of wffs, each of which is either:</p>
<ol style="list-style-type: decimal">
<li>An axiom</li>
<li>A premise</li>
<li>An immediate consequence of one or more preceding wffs (as determined by the inference rules)</li>
</ol>
<p>If there is such a derivation of <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=W" alt="W" title="W" /> from <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P" alt="P" title="P" /> we write <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P%20%5Cvdash%20W" alt="P \vdash W" title="P \vdash W" />.</p>
<p><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cvdash" alt="\vdash" title="\vdash" /> is the single turnstyle, or syntactic turnstyle.</p>
<p>Applying formal proofs to propositional logic gives us the <strong>propositional calculus</strong>.</p>
<p>There are many choices of deductive system for the propositional calculus, the system outlined below is called a <em>Gentzen Natural Deductive System</em>.</p>
<h4 id="some-inference-rules">Some Inference Rules</h4>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cfrac%7BA%2CB%7D%7BA%20%5Cland%20B%7D%20%5Ctext%7B%20and%20%7D%20%5Cfrac%7BA%2CB%7D%7BB%20%5Cland%20A%7D%5Ctext%7B%20%20%7D%5Cland%5Ctext%7B-Introduction%7D" alt="\frac{A,B}{A \land B} \text{ and } \frac{A,B}{B \land A}\text{  }\land\text{-Introduction}" title="\frac{A,B}{A \land B} \text{ and } \frac{A,B}{B \land A}\text{  }\land\text{-Introduction}" /><br /></p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cfrac%7BA%20%5Cland%20B%7D%7BA%7D%20%5Ctext%7B%20and%20%7D%20%5Cfrac%7BA%20%5Cland%20B%7D%7BB%7D%20%5Ctext%7B%20%20%7D%5Cland%5Ctext%7B-Elimination%7D" alt="\frac{A \land B}{A} \text{ and } \frac{A \land B}{B} \text{  }\land\text{-Elimination}" title="\frac{A \land B}{A} \text{ and } \frac{A \land B}{B} \text{  }\land\text{-Elimination}" /><br /></p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cfrac%7BA%7D%7BA%20%5Clor%20B%7D%20%5Ctext%7B%20and%20%7D%20%5Cfrac%7BA%7D%7BB%20%5Clor%20A%7D%20%5Ctext%7B%20%20%7D%5Clor%5Ctext%7B-Introduction%7D" alt="\frac{A}{A \lor B} \text{ and } \frac{A}{B \lor A} \text{  }\lor\text{-Introduction}" title="\frac{A}{A \lor B} \text{ and } \frac{A}{B \lor A} \text{  }\lor\text{-Introduction}" /><br /></p>
<p>etc.</p>
<h4 id="an-example">An Example</h4>
<p>Show that <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P%20%5Cland%20Q%20%5Cvdash%20P%20%5Clor%20Q" alt="P \land Q \vdash P \lor Q" title="P \land Q \vdash P \lor Q" /></p>
<p>Proof:</p>
<table>
<tbody>
<tr class="odd">
<td align="left">1</td>
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P%20%5Cland%20Q" alt="P \land Q" title="P \land Q" /></td>
<td align="center">premise</td>
</tr>
<tr class="even">
<td align="left">2</td>
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P" alt="P" title="P" /></td>
<td align="center">1 by <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cland" alt="\land" title="\land" />-Elimination</td>
</tr>
<tr class="odd">
<td align="left">3</td>
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P%20%5Clor%20Q" alt="P \lor Q" title="P \lor Q" /></td>
<td align="center">2 by <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Clor" alt="\lor" title="\lor" />-Introduction</td>
</tr>
</tbody>
</table>
<p>Q.E.D.</p>
<h4 id="another-example">Another example</h4>
<p>Show that <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P%2CP%20%5CRightarrow%20Q%2C%20Q%5CLeftrightarrow%20R%20%5Cvdash%20Q%20%5Cland%20R" alt="P,P \Rightarrow Q, Q\Leftrightarrow R \vdash Q \land R" title="P,P \Rightarrow Q, Q\Leftrightarrow R \vdash Q \land R" /></p>
<table>
<tbody>
<tr class="odd">
<td align="left">1</td>
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P" alt="P" title="P" /></td>
<td align="left">premise</td>
</tr>
<tr class="even">
<td align="left">2</td>
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P%20%5CRightarrow%20Q" alt="P \Rightarrow Q" title="P \Rightarrow Q" /></td>
<td align="left">premise</td>
</tr>
<tr class="odd">
<td align="left">3</td>
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=Q%20%5CLeftrightarrow%20R" alt="Q \Leftrightarrow R" title="Q \Leftrightarrow R" /> premis</td>
<td align="left">e</td>
</tr>
<tr class="even">
<td align="left">4</td>
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=Q" alt="Q" title="Q" /></td>
<td align="left">1,2 by <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5CRightarrow" alt="\Rightarrow" title="\Rightarrow" />-Elimination</td>
</tr>
<tr class="odd">
<td align="left">5</td>
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=Q%20%5CRightarrow%20R" alt="Q \Rightarrow R" title="Q \Rightarrow R" /></td>
<td align="left">3 by <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5CLeftrightarrow" alt="\Leftrightarrow" title="\Leftrightarrow" />-Elminiation</td>
</tr>
<tr class="even">
<td align="left">6</td>
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=R" alt="R" title="R" /></td>
<td align="left">4,5 by <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5CRightarrow" alt="\Rightarrow" title="\Rightarrow" />-Elimination</td>
</tr>
<tr class="odd">
<td align="left">7</td>
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=Q%20%5Cland%20R" alt="Q \land R" title="Q \land R" /></td>
<td align="left">4,6 by <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cland" alt="\land" title="\land" />-Introduction</td>
</tr>
</tbody>
</table>
<p>Q.E.D.</p>
<h2 id="consistency-and-completeness">Consistency and Completeness</h2>
<p>The propositional calculus is boy <strong>consistent</strong> and <strong>complete</strong>.</p>
<p><strong>Consistency</strong> If <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P" alt="P" title="P" /> is any finite set of propositions and <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=W" alt="W" title="W" /> is a proposition such that <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P%20%5Cvdash%20W" alt="P \vdash W" title="P \vdash W" /> then <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=P%20%5Cmodels%20W" alt="P \models W" title="P \models W" /></p>
<p>That is, anything which can be formally proved can be show... (<em>A: I give up see the slides</em>).</p>
<h2 id="application">Application</h2>
<p>Propositional logic can be applied to model the behaviour of digital electronic circuits. Used to reason about the behaviour of circuits, the decidability theorem implies that finite algorithms can be used to create the circuit.</p>
<h2 id="predicate-logic">Predicate Logic</h2>
<p>We want to use logic to reason about the correctness of computer programs. To do this we need a language which is more powerful than the propositional logic. We introduce truth valued functions: <em>predicates</em>:</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=positive%28counter%29" alt="positive(counter)" title="positive(counter)" /><br /></p>
<p>Can have more than one argument:</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=bigger%5C_than%28counter%2Ctotal%29" alt="bigger\_than(counter,total)" title="bigger\_than(counter,total)" /><br /></p>
<p>More conveniently, we write this in <em>infix</em> form as:</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=counter%20%5Clt%20total" alt="counter \lt total" title="counter \lt total" /><br /></p>
<p>The alphabet of the predicate is that for propositional logic, extended by lower case letters, the symbols <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cforall" alt="\forall" title="\forall" /> <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cexists" alt="\exists" title="\exists" /> <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cbullet" alt="\bullet" title="\bullet" />, and arbitary strings of letters (upper or lower case).</p>
<p><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cforall%20x" alt="\forall x" title="\forall x" /> is read &quot;for all <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=x" alt="x" title="x" />&quot;</p>
<p><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cexists%20x" alt="\exists x" title="\exists x" /> is read &quot;there exists <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=x" alt="x" title="x" />&quot;</p>
<h1 id="vdm">VDM</h1>
<h3 id="built-in-sets">Built in Sets</h3>
<p><strong>B</strong> = booleans</p>
<p><strong>N</strong> = Unsigned integers starting at 0</p>
<p><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Ctext%7BN%7D_1" alt="\text{N}_1" title="\text{N}_1" /> = Unsigned integers starting at 1</p>
<p><strong>Z</strong> = Signed integers</p>
<h3 id="some-example-notation">Some example notation</h3>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20%5C_%20%2B%20%5C_%20%3A%20Z%20%5Ctimes%20Z%20%5Crightarrow%20Z%20" alt=" \_ + \_ : Z \times Z \rightarrow Z " title=" \_ + \_ : Z \times Z \rightarrow Z " /><br /></p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20%5C_%20mod%20%5C_%20%3A%20N%20%5Ctimes%20N_1%20%5Crightarrow%20B%20" alt=" \_ mod \_ : N \times N_1 \rightarrow B " title=" \_ mod \_ : N \times N_1 \rightarrow B " /><br /></p>
<h2 id="proof-obligation-for-functions">Proof Obligation for Functions</h2>
<p>Suppose we have an implicit specification:</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=f%28p%3AT_p%29r%3AT_r" alt="f(p:T_p)r:T_r" title="f(p:T_p)r:T_r" /><br /></p>
<p><code>pre pre-f(p)</code></p>
<p><code>post post-f(p,r)</code></p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20f%3AT_P%20%5Crightarrow%20T_r" alt=" f:T_P \rightarrow T_r" title=" f:T_P \rightarrow T_r" /><br /></p>
<p>Suppose we have to define multiplication:</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20multp%28i%2Cj%29%20%20" alt=" multp(i,j)  " title=" multp(i,j)  " /><br /></p>
<pre><code>    if   i = 0
    then 0
    else if   is-even(i)
         then 2 * multp(i/2, j)
         else j + multp(i-1, j)</code></pre>
<p>Then the proof obligation becomes:</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20%5Cforall%20i%2Cj%20%5Cin%20%5Ctext%7BN%7D%20%5Cbullet%20multp%28i%2Cj%29%20%5Cin%20%5Ctext%7BN%7D%20%5Cland%20multp%28i%2Cj%29%20%3D%20i%20%5Ctimes%20j%20" alt=" \forall i,j \in \text{N} \bullet multp(i,j) \in \text{N} \land multp(i,j) = i \times j " title=" \forall i,j \in \text{N} \bullet multp(i,j) \in \text{N} \land multp(i,j) = i \times j " /><br /></p>
<h2 id="partial-functions">Partial Functions</h2>
<p>Consider:</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20subp%28i%3A%5Ctext%7BN%7D%2C%20j%3A%5Ctext%7BN%7D%29r%3A%5Ctext%7BN%7D%20" alt=" subp(i:\text{N}, j:\text{N})r:\text{N} " title=" subp(i:\text{N}, j:\text{N})r:\text{N} " /><br /></p>
<pre><code>pre j &lt;= i
post r + j = i</code></pre>
<p>An explicit definition of <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=subp" alt="subp" title="subp" /> will generate the following proof obligation:</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20%5Cforall%20i%2Cj%3A%5Ctext%7BN%7D%20%5Cbullet%20%5Ctext%7Bpre%7D%20-%20subp%20%28i%2Cj%29%20%5CRightarrow%20subp%28i%2Cj%29%20%5Cin%20%5Ctext%7BN%7D%20%5Cland%20%5Ctext%7Bpost%7D%20-%20subp%28i%2Cj%29%20" alt=" \forall i,j:\text{N} \bullet \text{pre} - subp (i,j) \Rightarrow subp(i,j) \in \text{N} \land \text{post} - subp(i,j) " title=" \forall i,j:\text{N} \bullet \text{pre} - subp (i,j) \Rightarrow subp(i,j) \in \text{N} \land \text{post} - subp(i,j) " /><br /></p>
<p>i.e.</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20%5Cforall%20i%2Cj%3A%5Ctext%7BN%7D%20%5Cbullet%20j%20%5Cle%20i%20%5CRightarrow%20subp%28i%2Cj%29%20%5Cin%20%5Ctext%7BN%7D%20%5Cland%20subp%28i%2Cj%29%20%2B%20i%20%3D%20j" alt=" \forall i,j:\text{N} \bullet j \le i \Rightarrow subp(i,j) \in \text{N} \land subp(i,j) + i = j" title=" \forall i,j:\text{N} \bullet j \le i \Rightarrow subp(i,j) \in \text{N} \land subp(i,j) + i = j" /><br /></p>
<p>Can't complete this evaluation; when <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=j" alt="j" title="j" /> is bigger than <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=i" alt="i" title="i" /> this equation is undefined.</p>
<p>However, using <strong>Logic of Partial Functions</strong> (LPF):</p>
<ol style="list-style-type: decimal">
<li>If <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=j%20%5Cle%20i" alt="j \le i" title="j \le i" /> the implication becomes <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Ctext%7BT%7D%20%5CRightarrow%20%5Ctext%7BT%7D%20%5Cland%20%5Ctext%7BT%7D" alt="\text{T} \Rightarrow \text{T} \land \text{T}" title="\text{T} \Rightarrow \text{T} \land \text{T}" /> which evaluates to <strong>T</strong>.</li>
<li>If <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=j%20%5Cgt%20i" alt="j \gt i" title="j \gt i" /> the implication becomes <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Ctext%7BF%7D%20%5CRightarrow%20%5Ctext%7B%2A%20%7D%20%5Cland%20%5Ctext%7B%20%2A%7D" alt="\text{F} \Rightarrow \text{* } \land \text{ *}" title="\text{F} \Rightarrow \text{* } \land \text{ *}" /> which evaluates to <strong>T</strong>.</li>
</ol>
<p>The &quot;Law of the Excluded Middle&quot; (<img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cvdash%20P%20%5Clor%20%5Cneg%20P" alt="\vdash P \lor \neg P" title="\vdash P \lor \neg P" />) clearly does not hold in LPF.</p>
<p>This is, in fact, a virtue with partially defined functions, for example, there is no reason for:</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20%5Cfrac%7B2%7D%7B0%7D%20%3D%201%20%5Clor%20%5Cfrac%7B2%7D%7B0%7D%20%5Cne%201%20" alt=" \frac{2}{0} = 1 \lor \frac{2}{0} \ne 1 " title=" \frac{2}{0} = 1 \lor \frac{2}{0} \ne 1 " /><br /></p>
<p>However, we do get useful results like:</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cforall%20n%20%5Cbullet%20n%20%5Cin%20%5Ctext%7BZ%7D%20%5CRightarrow%20n%20%3D%200%20%5Clor%20%5Cfrac%7Bn%7D%7Bn%7D%20%3D%201%20" alt="\forall n \bullet n \in \text{Z} \Rightarrow n = 0 \lor \frac{n}{n} = 1 " title="\forall n \bullet n \in \text{Z} \Rightarrow n = 0 \lor \frac{n}{n} = 1 " /><br /></p>
<p>Another rule which doesn't hold in LPF is <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cvdash%20P%20%5CRightarrow%20P" alt="\vdash P \Rightarrow P" title="\vdash P \Rightarrow P" />.</p>
<h2 id="domain-of-interest">Domain of Interest</h2>
<p>The domain of interest can now be defined rigorously by specifigying over which set the bound variables range.</p>
<p>For example</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20%5Cexists%20x%20%5Cbullet%20x%20%5Cgt%204" alt=" \exists x \bullet x \gt 4" title=" \exists x \bullet x \gt 4" /><br /></p>
<p>Can be more precisely specifed by</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20%5Cexists%20x%20%5Cbullet%20x%20%5Cin%20%5Ctext%7BN%7D%20%5Cland%20x%20%5Cgt%204%20" alt=" \exists x \bullet x \in \text{N} \land x \gt 4 " title=" \exists x \bullet x \in \text{N} \land x \gt 4 " /><br /></p>
<p>The expression still has meaning when <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=x%20%5Cgt%204" alt="x \gt 4" title="x \gt 4" /> is undefined.</p>
<p>So, in future, we will always quantify over some set and we introduce an avvreviated notation:</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20%5Cforall%20x%20%5Cin%20S%20%5Cbullet%20P%28x%29%20%5Ctext%7Bfor%7D%20%5Cforall%20x%20%5Cbullet%20%5Cin%20S%20%5CRightarrow%20P%28x%29%20" alt=" \forall x \in S \bullet P(x) \text{for} \forall x \bullet \in S \Rightarrow P(x) " title=" \forall x \in S \bullet P(x) \text{for} \forall x \bullet \in S \Rightarrow P(x) " /><br /></p>
<h2 id="states-and-operations">States and Operations</h2>
<p>Functions may not have side effects, instead we have <strong>states</strong> and <strong>operations</strong> on the states.</p>
<p>Example:</p>
<pre><code>state Register as
    reg: N
end

LOAD(i:n)
ext wr reg:N
post reg = i</code></pre>
<p>The exterior clause (<code>ext</code>) specifies which parts of the state can be accessed by the operation.</p>
<ul>
<li><code>rd</code> means read access</li>
<li><code>wr</code> means write access (implies read access)</li>
</ul>
<p>Operation labels landitalised by convention.</p>
<p>Hooked variables denote the value of that variable prior to the execution of the operation.</p>
<p>Returning works like:</p>
<pre><code>SHOW()r:N
ext rd reg:N
post r = reg</code></pre>
<p>Can also have <code>pre-OP</code> and <code>post-OP</code>.</p>
<h2 id="data-types">Data Types</h2>
<p>Predefined sets: <strong>B</strong>, <strong>N</strong>, <strong>N</strong>1, <strong>Z</strong>, <strong>Q</strong>, <strong>R</strong>.</p>
<p>For a set <em>X</em>, <em>X-set</em> is the set of all finite subsets of <em>X</em>.</p>
<p>e.g.: <strong>B</strong>-set = {{},{true},{false},{true,false}}</p>
<p>A useful abbreviation for sets of integers is:</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5C%7Bi%2C...%2Cj%5C%7D%3D%5C%7B%20k%20%5Cin%20Z%20%5Cldots" alt="\{i,...,j\}=\{ k \in Z \ldots" title="\{i,...,j\}=\{ k \in Z \ldots" /><br /></p>
<p>VDM-SL admits a lot of useful set operations.</p>
<p>Type of <code>To Be Defined</code> is allowed and just means the type is defined somewhere else.</p>
<p><strong>Just a note:</strong> no concurrency in VDM so you don't have to worry about locking.</p>
<h3 id="composite-type">Composite Type</h3>
<p>The general form of a composite type definition is:</p>
<pre><code>Name ::
    s1 : T1
    s2 : T2
    .
    .
    .
    sn : Tn</code></pre>
<p>This type has associated with it the constructor:</p>
<pre><code>mk-Nam : T1 x T2 x ... x Tn -&gt; Name</code></pre>
<p>And selector functions:</p>
<pre><code>s1 : Name -&gt; T1
s2 : Name -&gt; T2
      .
      .
      .
sn : Name -&gt; Tn</code></pre>
<p>Example:</p>
<pre><code>Date ::
    day : {1,...,366}
    year : {1901,...,2099}</code></pre>
<p>Automatically gives us these functions:</p>
<pre><code>mk-Date({1,...,366} x {1901,...,2099} -&gt; Date
day : Date -&gt; {1,.366}
year : Date -&gt; {1901, 2099}</code></pre>
<p>For example: <code>mk-date{45,2003}</code></p>
<p>There is the problem of leap years in this example. So we might want a function <code>valid-Date : Date -&gt; B</code> to determine whether a date is actually valid.</p>
<pre><code>valid-Date(dt) ? is-leapyear(year(dt)) V day(dt) &lt;= 365

is-leapyear(i) ? i mod 4 = 0</code></pre>
<p>Alternatively:</p>
<pre><code>valid-Date(dt) ?
    let mk-Date(d,y) = dt
    in is-leapyear(y) V d &lt;= 365</code></pre>
<p><strong>Note:</strong> Because of the restricted year range our definition of leap year works.</p>
<p>Data type <strong>invariants</strong> can be added to composite types using the construction:</p>
<pre><code>Date ::
    day : {1,...,366}
    year : {1901,...,2099}
where
inv-Date(mk-Date(d,y)) ? is-leapyear(y) V d &lt;= 365</code></pre>
<p>Now only valid dates will be allowed on the constructor.</p>
<h4 id="optional-fields">Optional Fields</h4>
<p>Optional fields are allowed in composite types, denoted by <code>[...]</code>, and an omitted field is denoted by <code>nil</code>:</p>
<pre><code>Record ::
    day : {1,...,366}
    year : {1901,...,2099}
    valid : [ERROR]</code></pre>
<p>Useful for recursive data types.</p>
<h3 id="recursive-data-definitions">Recursive Data Definitions</h3>
<pre><code>List = [Listelt]
Listelt ::
    hd : N
    tl : List

nil in List
mk-Listelt(3,nil) in List
mk-Listelt(1,mk-Listelt(2,mk-Listelt(3,nil))) in List

lsum : List -&gt; N
lsum(l) ?
    cases l:
        nil -&gt; 0
        mk-Listelt(hd,tl) -&gt; hd + lsum(tl)
    end</code></pre>
<h4 id="binary-search-tree-example">Binary Search Tree Example</h4>
<pre><code>Tree = [Node]
Node ::
    left : Tree
    value : N
    right : Tree
where
inv-Node(mk-Node(left,value,right)) ?
    (forall(lv) in values(left) assert lv &lt; value) and (forall(rv) in values(right) assert value &lt; rv)
values : Tree -&gt; N-set
values(t) ?
    cases t of
        nil -&gt; {}
        mk-Node(left,value,right) -&gt; values(left) union {value} union values(right)</code></pre>
<h2 id="maps">Maps</h2>
<p>A <strong>map</strong> is similar to a function defined on a finite set, except that the argument:result pairs are given explicitly.</p>
<p>e.g.: <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cleft%5C%7B%7Ba_1%20%5Cmapsto%20r_1%2C%20a_2%20%5Cmapsto%20r_2%2C%5Cldots%20%2Ca_n%20%5Cmapsto%20r_n%7D%5Cright%5C%7D" alt="\left\{{a_1 \mapsto r_1, a_2 \mapsto r_2,\ldots ,a_n \mapsto r_n}\right\}" title="\left\{{a_1 \mapsto r_1, a_2 \mapsto r_2,\ldots ,a_n \mapsto r_n}\right\}" /></p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cleft%5C%7B%7Bx%20%5Cmapsto%20f%28x%29%7CP%28x%29%7D%5Cright%5C%7D" alt="\left\{{x \mapsto f(x)|P(x)}\right\}" title="\left\{{x \mapsto f(x)|P(x)}\right\}" /><br /></p>
<p>Denoted by</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20X%20%5Crightarrow%5E%7Bm%7D%20Y%20" alt=" X \rightarrow^{m} Y " title=" X \rightarrow^{m} Y " /><br /></p>
<h3 id="map-overriding">Map Overriding</h3>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=m_1%20%5Cdagger%20m_2" alt="m_1 \dagger m_2" title="m_1 \dagger m_2" /><br /></p>
<p><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=m_2" alt="m_2" title="m_2" /> overrides elements in <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=m_1" alt="m_1" title="m_1" />. If an element in exists in both <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=m_1" alt="m_1" title="m_1" /> and <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=m_2" alt="m_2" title="m_2" /> then the return from <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=m_2" alt="m_2" title="m_2" /> is used, otherwise it's just the union of the two maps.</p>
<h2 id="sequences">Sequences</h2>
<p>Given a type <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=X" alt="X" title="X" />, we can have <em>sequences</em> of elements of <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=X" alt="X" title="X" />.</p>
<p>The types of such sequences is denoted by <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=X%2A" alt="X*" title="X*" /></p>
<p>Sequences are denoted by:</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cleft%5B%20a%2Cb%2Cc%20%5Cright%5D" alt="\left[ a,b,c \right]" title="\left[ a,b,c \right]" /><br /></p>
<p>Where:</p>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20a%2Cb%2Cc%2C%20%5Cin%20X%20" alt=" a,b,c, \in X " title=" a,b,c, \in X " /><br /></p>
<h3 id="operations">Operations</h3>
<table>
<tbody>
<tr class="odd">
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=hd%5C_" alt="hd\_" title="hd\_" /></td>
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=X%2A%20%5Crightarrow%20X" alt="X* \rightarrow X" title="X* \rightarrow X" /></td>
<td align="left">head (first element)</td>
</tr>
<tr class="even">
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=tl%5C_" alt="tl\_" title="tl\_" /></td>
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=X%2A%20%5Crightarrow%20X%2A" alt="X* \rightarrow X*" title="X* \rightarrow X*" /></td>
<td align="left">tail</td>
</tr>
<tr class="odd">
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=len%5C_" alt="len\_" title="len\_" /></td>
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=X%2A%20%5Crightarrow%20N" alt="X* \rightarrow N" title="X* \rightarrow N" /></td>
<td align="left">length</td>
</tr>
<tr class="even">
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=elems%5C_" alt="elems\_" title="elems\_" /></td>
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=X%2A%20%5Crightarrow%20X%5Ctext%7B-set%7D" alt="X* \rightarrow X\text{-set}" title="X* \rightarrow X\text{-set}" /></td>
<td align="left">set of elements</td>
</tr>
<tr class="odd">
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5C_%28%5C_%29" alt="\_(\_)" title="\_(\_)" /></td>
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=X%20%5Ctimes%20N_1%20%5Crightarrow%20X" alt="X \times N_1 \rightarrow X" title="X \times N_1 \rightarrow X" /></td>
<td align="left">element selection</td>
</tr>
<tr class="even">
<td align="left"><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5C_%20%5Ccurvearrowright%20%5C_" alt="\_ \curvearrowright \_" title="\_ \curvearrowright \_" /></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>
VDM as a Development Method
===========================

When using VDM, we start with a (very) abstract specification and, in a number of steps, develop this into an implementation

Each step involves:

* Data Reification
* Operation Decomposition

Data reification develops the abstract data types into more concrete data structures.

Operation decomposition develops the abstract implicit specification of functions and operations into algorithms which can be put into code.


Data Reification
----------------

Data reification develops the abstract data types into more concrete data structures.

There may be several steps before an implementation is reached.

Each step involves:

* Given an abstract data representation $ABS$, find a new representation $REP$.
* Find a **retrieve function** that relates $ABS$ to $REP$: $retr : REP \rightarrow ABS$.
* Prove that $REP$ is **adequet** to represent $ABS$. *i.e.* prove $\forall a \in ABS \bullet \exists r \in REP  \bullet a = retr(r)$
* Reqrite the functions and operations in terms of the new representation
* Prove that the new functions and operations preserve any data-type invariants of the new representation
* Prove that the new functions and operations model those of the original specifications; this involves two rules:

###Doman Rule

$$ \forall r \in REP \bullet \text{pre-}OPA(retr(r)) \Rightarrow \text{pre-}OPR(r) $$

###Modelling Rule

$$ \forall r', r \in REP \bullet \text{pre-}OPA(retr(r')) \land \text{post-}OPA(r', r) \Rightarrow \text{post-}OPA(retr(r'),retr(r)) $$

$r'$ is the initial state before the operation was run.


Implementation of Data Reification
----------------------------------

Implementation in a traditional programming language (e.g.: Java) suggests having a sequence of objects.

So, the first data reification step is to represent the data in terms of sequences.

We must not allow repetitions in our sequences because the same employee cannot occur twice; hence, we require an invariant on our new data type.

However, the set $\left\{{p,q}\right\}$ could be represented by $\left[{p,q}\right]$ or by $\left[{q,p}\right]$

A completely rigorous development down to programming language, then the programming language has to be formally specified.


<h1 id="vdm-as-a-development-method">VDM as a Development Method</h1>
<p>When using VDM, we start with a (very) abstract specification and, in a number of steps, develop this into an implementation</p>
<p>Each step involves:</p>
<ul>
<li>Data Reification</li>
<li>Operation Decomposition</li>
</ul>
<p>Data reification develops the abstract data types into more concrete data structures.</p>
<p>Operation decomposition develops the abstract implicit specification of functions and operations into algorithms which can be put into code.</p>
<h2 id="data-reification">Data Reification</h2>
<p>Data reification develops the abstract data types into more concrete data structures.</p>
<p>There may be several steps before an implementation is reached.</p>
<p>Each step involves:</p>
<ul>
<li>Given an abstract data representation <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=ABS" alt="ABS" title="ABS" />, find a new representation <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=REP" alt="REP" title="REP" />.</li>
<li>Find a <strong>retrieve function</strong> that relates <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=ABS" alt="ABS" title="ABS" /> to <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=REP" alt="REP" title="REP" />: <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=retr%20%3A%20REP%20%5Crightarrow%20ABS" alt="retr : REP \rightarrow ABS" title="retr : REP \rightarrow ABS" />.</li>
<li>Prove that <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=REP" alt="REP" title="REP" /> is <strong>adequet</strong> to represent <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=ABS" alt="ABS" title="ABS" />. <em>i.e.</em> prove <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cforall%20a%20%5Cin%20ABS%20%5Cbullet%20%5Cexists%20r%20%5Cin%20REP%20%5Cbullet%20a%20%3D%20retr%28r%29" alt="\forall a \in ABS \bullet \exists r \in REP \bullet a = retr(r)" title="\forall a \in ABS \bullet \exists r \in REP \bullet a = retr(r)" /></li>
<li>Reqrite the functions and operations in terms of the new representation</li>
<li>Prove that the new functions and operations preserve any data-type invariants of the new representation</li>
<li>Prove that the new functions and operations model those of the original specifications; this involves two rules:</li>
</ul>
<h3 id="doman-rule">Doman Rule</h3>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20%5Cforall%20r%20%5Cin%20REP%20%5Cbullet%20%5Ctext%7Bpre-%7DOPA%28retr%28r%29%29%20%5CRightarrow%20%5Ctext%7Bpre-%7DOPR%28r%29%20" alt=" \forall r \in REP \bullet \text{pre-}OPA(retr(r)) \Rightarrow \text{pre-}OPR(r) " title=" \forall r \in REP \bullet \text{pre-}OPA(retr(r)) \Rightarrow \text{pre-}OPR(r) " /><br /></p>
<h3 id="modelling-rule">Modelling Rule</h3>
<p><br /><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%20%5Cforall%20r%27%2C%20r%20%5Cin%20REP%20%5Cbullet%20%5Ctext%7Bpre-%7DOPA%28retr%28r%27%29%29%20%5Cland%20%5Ctext%7Bpost-%7DOPA%28r%27%2C%20r%29%20%5CRightarrow%20%5Ctext%7Bpost-%7DOPA%28retr%28r%27%29%2Cretr%28r%29%29%20" alt=" \forall r&#39;, r \in REP \bullet \text{pre-}OPA(retr(r&#39;)) \land \text{post-}OPA(r&#39;, r) \Rightarrow \text{post-}OPA(retr(r&#39;),retr(r)) " title=" \forall r&#39;, r \in REP \bullet \text{pre-}OPA(retr(r&#39;)) \land \text{post-}OPA(r&#39;, r) \Rightarrow \text{post-}OPA(retr(r&#39;),retr(r)) " /><br /></p>
<p><img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=r%27" alt="r&#39;" title="r&#39;" /> is the initial state before the operation was run.</p>
<h2 id="implementation-of-data-reification">Implementation of Data Reification</h2>
<p>Implementation in a traditional programming language (e.g.: Java) suggests having a sequence of objects.</p>
<p>So, the first data reification step is to represent the data in terms of sequences.</p>
<p>We must not allow repetitions in our sequences because the same employee cannot occur twice; hence, we require an invariant on our new data type.</p>
<p>However, the set <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cleft%5C%7B%7Bp%2Cq%7D%5Cright%5C%7D" alt="\left\{{p,q}\right\}" title="\left\{{p,q}\right\}" /> could be represented by <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cleft%5B%7Bp%2Cq%7D%5Cright%5D" alt="\left[{p,q}\right]" title="\left[{p,q}\right]" /> or by <img style="vertical-align:middle" src="http://chart.apis.google.com/chart?cht=tx&amp;chl=%5Cleft%5B%7Bq%2Cp%7D%5Cright%5D" alt="\left[{q,p}\right]" title="\left[{q,p}\right]" /></p>
<p>A completely rigorous development down to programming language, then the programming language has to be formally specified.</p>
Proving Correctness
===================

* *Validation* - Implementation which does the right thing.
* *Verification* - Implementation meets the specification.


<h1 id="proving-correctness">Proving Correctness</h1>
<ul>
<li><em>Validation</em> - Implementation which does the right thing.</li>
<li><em>Verification</em> - Implementation meets the specification.</li>
</ul>
Other Specification Methods
===========================

Software developers aren't going to use full-blown formal methods *except* where the cost of doing so justifies doing so (safety- and mission- critical systems). The complete use of mathematics is not justifiable in most cases.

There are some techniques to check a piece of code can be proved mathematically without too much effort without the heavy use of maths. This may help to avoid a lot of problems seen in code today.


Deficiencies of VDM
-------------------

VDM SL contains limited constructs for modularisation. Difficult to split a large specification into modules.

No support for palletisation and concurrency.

Must implement in a language which has also been formally specified.

RAISE (Rigorous Approach to Industrial Software Engineering) and others have tried to overcome some of the deficiencies of VDM.
<h1 id="other-specification-methods">Other Specification Methods</h1>
<p>Software developers aren't going to use full-blown formal methods <em>except</em> where the cost of doing so justifies doing so (safety- and mission- critical systems). The complete use of mathematics is not justifiable in most cases.</p>
<p>There are some techniques to check a piece of code can be proved mathematically without too much effort without the heavy use of maths. This may help to avoid a lot of problems seen in code today.</p>
<h2 id="deficiencies-of-vdm">Deficiencies of VDM</h2>
<p>VDM SL contains limited constructs for modularisation. Difficult to split a large specification into modules.</p>
<p>No support for palletisation and concurrency.</p>
<p>Must implement in a language which has also been formally specified.</p>
<p>RAISE (Rigorous Approach to Industrial Software Engineering) and others have tried to overcome some of the deficiencies of VDM.</p>
SE33010 - Formal Methods in Software Engineering
================================================

Fred Long (fwl). 

The use of mathematical formal methods in software specification and techniques for producing reliable software.

**Reminder:** Fred has a good lecturing style :)

You will need to put effort in to succeed. Not all mathematics (but there is a fair amount).

Links on blackboard to books (both out of print).


Assessment
----------

* 80% Exam
* 10% Written Assignment
* 10% Written Assignment

Also $\approx 3$ un-assessed worksheets in workshops.


Why do we need formal methods?
------------------------------

Bugs are common in software.

Legal requirement to report vulnerabilities (vulnerabilities are a special class of bug).

> "If debugging is the process of taking out bugs, programming must be the process of putting them in."

Cannot prove the absence of bugs by testing software. Need to be able to prove there are no bugs in the software $\rightarrow$ prove the software is correct. Mathematical techniques can begin to do this.

Few example of where this has been done successfully:

* Metro lines in Paris (14) Oct. 1998 has an automatic train control system was developed on time, in budget and was proved to be 100% correct using formal proof.
* A real time air-traffic control system used VDM, developed for London airports. Productivity of developers: 13 lines per person per day compared to 7. Wasn't proved to be correct - 35% reduction in defects. Industry standard: 1 defect per 1000 lines of code.
* BMW/Rolls Royce test facility used Z notation for certification testing of the electronic control system.
* NASA international space system fault detection system, irregularities discovered early in development using formal methods.
* IEEE reporting on experience from a student group project. Two classes of groups of students, one using formal development, one using traditional development (small groups, 2 students per group). 45.5% of traditional groups passed testing, 100% of formal groups passed testing.


Introduction to Logic
=====================

Formalisation of Software Development
-------------------------------------

1. User's ideas
2. Requirements Specification
3. System specification
4. Programs
5. Executable Machine Code

Last step is often automated. Idea of formal methods is to move the automation up (use tools to automatically generate code).

To do this the specification must be amenable to processing (cannot be a natural language).

Need to use a "formal" specification language.

There is some research into introducing formal notations for requirement specification, but of course (accept in very few examples) you're never going to be able to completely automate this process.

Ideas are very difficult to formalise.

This module focuses on a formal definition for a system specification.

Compilers can be completely automated from requirements.


Specification
-------------

A specification should be:

* Concise
* Complete
* Consistent

May go through several stages and may come in a number of pieces.

It is important to maintain consistency between stages of specification, traditional methods of software development make this difficult. This is because of the large, natural language nature of the traditional specification (relies on humans to ensure consistency).

Mathematical methods of specification can help with this. This definitely addresses the issue of being concise (downside on people not being familiar with the notion). Big advantage is the use of software tools to analyse the specification for consistency, may be able to have a check for completeness. Some chance of being able to check for missing elements of the specification.



Advantages of Formal Specification
----------------------------------

* Makes you think. Natural languages allow for "sloppiness". Constrained about things like integer values, etc. This is surprisingly important and is often overlooked.
* Unambiguous language. Natural language is very context sensitive.
* May be autonomous. From formal specification it may be possible to generate code, for example. Can lead to inefficient code, this might be used as a prototype rather than end product.
* Automated test data. Very likely to pick up boundary cases where software is likely to go wrong.
* Can be proved to be correct rather than tested. Testing is still important and does a different job. This might make unit testing redundant.
* Errors detected earlier.
* Adapt to changing requirements more reliably. Can also introduce metrics of how it will affect the system.
* Very good for rapid prototyping.

Disadvantages of Formal Specification
-------------------------------------

* Specification difficult to communicate to users. Difficult to get "sign-off".
* Highly specialised workforce.
* May sacrifice efficiency if used blindly. If applied properly it should be just as efficient.
* May need sophisticated (*read: expensive*) tools.
* May need additional computing facilities (theorem provers ran on specialised hardware). Lately this is less of a problem, but most tools are very resource intensive.


###Note on terminology

Sometimes "formal methods" may be via the use of documentation and/or coding standards. In this course we are talking about a Mathematically formal specification.


Approaches to a Formal Specification
------------------------------------

Two approaches

* Algebraic (axiomatic)
* Model-based (operational)

An algebraic specification defines a mathematical object in terms of relations among the operations defined over the object. In many ways this is more abstract

A model-based approach is an explicit system model constructed from abstract or concrete primitives (think of this as another programming language).

Focus on model-based specifications, particularly VDN.


###Example of Algebraic Specification

Example of a boolean type.

```
INITIAL
		boolean

SORT
		bool

CONSTANTS
		true		: bool
		false		: bool

OPERATIONS
		not _		: bool -> bool
		_ or _		: bool, bool -> bool
		_ and _		: bool, bool -> bool
		_ impl _	: bool, bool -> bool
		_equiv _	: bool, bool -> bool

EQUATIONS
		not(not(A))	= A
		A or (B or C)	= (A or B) or C
		A or B		= B or A
		A or true	= true
		A or false	= A
		A and B		= not(not(A) or not(b))
		A impl B	= not(A) or B
		A equiv B	= (A impl B) and (B impl A)
END
```

`INITIAL` means that there are no values or relations other than those which can be deduced from the given ones, for example one can deduce that `A and B = B and A`, buy not `true = false`.

The mathematical branch of *category theory* is needed to reason about such specifications.


```
INITIAL
		lists (elem with {_ eq _ : elem,elem -> bool; undef : -> elem})

USES
		boolean

SORT
		list

CONSTANTS
		empty	: list
		undef	: list

OPERATIONS
		_ . _			: elem,list -> list
		first _			: list -> elem
		rest _			: list -> list
		is-undef _		: list -> bool
		_ is-member-of _	: elem,list -> bool
		_ eq _ 			: list,list -> bool
		at-end _		: list -> bool

EQUATIONS
		first(empty)		= undef
		first(undef)		= undef
		first(A.B)		= A
		rest(empty)		= undef
		rest(undef)		= undef
		rest(A.B)		= B
		is-undef(empty)		= false
		is-undef(undef)		= true
		is-undef(A.B)		= false
		E is-member-of undef	= false
		E is-member-of empty	= false
		E is-member-of (A.B)	= (E eq A) or (E is-member-of B)
		(A.B) eq (C.D)		= (A eq C) and (B eq D)
		empty eq empty		= true
		(A.B) eq empty		= false
		A eq B			= B eq A
		at-end(empty)		= true
		at-end(undef)		= false
		at-end(A.B)		= false
END
```


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


VDM as a Development Method
===========================

When using VDM, we start with a (very) abstract specification and, in a number of steps, develop this into an implementation

Each step involves:

* Data Reification
* Operation Decomposition

Data reification develops the abstract data types into more concrete data structures.

Operation decomposition develops the abstract implicit specification of functions and operations into algorithms which can be put into code.


Data Reification
----------------

Data reification develops the abstract data types into more concrete data structures.

There may be several steps before an implementation is reached.

Each step involves:

* Given an abstract data representation $ABS$, find a new representation $REP$.
* Find a **retrieve function** that relates $ABS$ to $REP$: $retr : REP \rightarrow ABS$.
* Prove that $REP$ is **adequet** to represent $ABS$. *i.e.* prove $\forall a \in ABS \bullet \exists r \in REP  \bullet a = retr(r)$
* Reqrite the functions and operations in terms of the new representation
* Prove that the new functions and operations preserve any data-type invariants of the new representation
* Prove that the new functions and operations model those of the original specifications; this involves two rules:

###Doman Rule

$$ \forall r \in REP \bullet \text{pre-}OPA(retr(r)) \Rightarrow \text{pre-}OPR(r) $$

###Modelling Rule

$$ \forall r', r \in REP \bullet \text{pre-}OPA(retr(r')) \land \text{post-}OPA(r', r) \Rightarrow \text{post-}OPA(retr(r'),retr(r)) $$

$r'$ is the initial state before the operation was run.


Implementation of Data Reification
----------------------------------

Implementation in a traditional programming language (e.g.: Java) suggests having a sequence of objects.

So, the first data reification step is to represent the data in terms of sequences.

We must not allow repetitions in our sequences because the same employee cannot occur twice; hence, we require an invariant on our new data type.

However, the set $\left\{{p,q}\right\}$ could be represented by $\left[{p,q}\right]$ or by $\left[{q,p}\right]$

A completely rigorous development down to programming language, then the programming language has to be formally specified.


Proving Correctness
===================

* *Validation* - Implementation which does the right thing.
* *Verification* - Implementation meets the specification.


Other Specification Methods
===========================

Software developers aren't going to use full-blown formal methods *except* where the cost of doing so justifies doing so (safety- and mission- critical systems). The complete use of mathematics is not justifiable in most cases.

There are some techniques to check a piece of code can be proved mathematically without too much effort without the heavy use of maths. This may help to avoid a lot of problems seen in code today.


Deficiencies of VDM
-------------------

VDM SL contains limited constructs for modularisation. Difficult to split a large specification into modules.

No support for palletisation and concurrency.

Must implement in a language which has also been formally specified.

RAISE (Rigorous Approach to Industrial Software Engineering) and others have tried to overcome some of the deficiencies of VDM.
SE33010 - Formal Methods in Software Engineering
================================================

Fred Long (fwl). 

The use of mathematical formal methods in software specification and techniques for producing reliable software.

**Reminder:** Fred has a good lecturing style :)

You will need to put effort in to succeed. Not all mathematics (but there is a fair amount).

Links on blackboard to books (both out of print).


Assessment
----------

* 80% Exam
* 10% Written Assignment
* 10% Written Assignment

Also $\approx 3$ un-assessed worksheets in workshops.


Why do we need formal methods?
------------------------------

Bugs are common in software.

Legal requirement to report vulnerabilities (vulnerabilities are a special class of bug).

> "If debugging is the process of taking out bugs, programming must be the process of putting them in."

Cannot prove the absence of bugs by testing software. Need to be able to prove there are no bugs in the software $\rightarrow$ prove the software is correct. Mathematical techniques can begin to do this.

Few example of where this has been done successfully:

* Metro lines in Paris (14) Oct. 1998 has an automatic train control system was developed on time, in budget and was proved to be 100% correct using formal proof.
* A real time air-traffic control system used VDM, developed for London airports. Productivity of developers: 13 lines per person per day compared to 7. Wasn't proved to be correct - 35% reduction in defects. Industry standard: 1 defect per 1000 lines of code.
* BMW/Rolls Royce test facility used Z notation for certification testing of the electronic control system.
* NASA international space system fault detection system, irregularities discovered early in development using formal methods.
* IEEE reporting on experience from a student group project. Two classes of groups of students, one using formal development, one using traditional development (small groups, 2 students per group). 45.5% of traditional groups passed testing, 100% of formal groups passed testing.


Introduction to Logic
=====================

Formalisation of Software Development
-------------------------------------

1. User's ideas
2. Requirements Specification
3. System specification
4. Programs
5. Executable Machine Code

Last step is often automated. Idea of formal methods is to move the automation up (use tools to automatically generate code).

To do this the specification must be amenable to processing (cannot be a natural language).

Need to use a "formal" specification language.

There is some research into introducing formal notations for requirement specification, but of course (accept in very few examples) you're never going to be able to completely automate this process.

Ideas are very difficult to formalise.

This module focuses on a formal definition for a system specification.

Compilers can be completely automated from requirements.


Specification
-------------

A specification should be:

* Concise
* Complete
* Consistent

May go through several stages and may come in a number of pieces.

It is important to maintain consistency between stages of specification, traditional methods of software development make this difficult. This is because of the large, natural language nature of the traditional specification (relies on humans to ensure consistency).

Mathematical methods of specification can help with this. This definitely addresses the issue of being concise (downside on people not being familiar with the notion). Big advantage is the use of software tools to analyse the specification for consistency, may be able to have a check for completeness. Some chance of being able to check for missing elements of the specification.



Advantages of Formal Specification
----------------------------------

* Makes you think. Natural languages allow for "sloppiness". Constrained about things like integer values, etc. This is surprisingly important and is often overlooked.
* Unambiguous language. Natural language is very context sensitive.
* May be autonomous. From formal specification it may be possible to generate code, for example. Can lead to inefficient code, this might be used as a prototype rather than end product.
* Automated test data. Very likely to pick up boundary cases where software is likely to go wrong.
* Can be proved to be correct rather than tested. Testing is still important and does a different job. This might make unit testing redundant.
* Errors detected earlier.
* Adapt to changing requirements more reliably. Can also introduce metrics of how it will affect the system.
* Very good for rapid prototyping.

Disadvantages of Formal Specification
-------------------------------------

* Specification difficult to communicate to users. Difficult to get "sign-off".
* Highly specialised workforce.
* May sacrifice efficiency if used blindly. If applied properly it should be just as efficient.
* May need sophisticated (*read: expensive*) tools.
* May need additional computing facilities (theorem provers ran on specialised hardware). Lately this is less of a problem, but most tools are very resource intensive.


###Note on terminology

Sometimes "formal methods" may be via the use of documentation and/or coding standards. In this course we are talking about a Mathematically formal specification.


Approaches to a Formal Specification
------------------------------------

Two approaches

* Algebraic (axiomatic)
* Model-based (operational)

An algebraic specification defines a mathematical object in terms of relations among the operations defined over the object. In many ways this is more abstract

A model-based approach is an explicit system model constructed from abstract or concrete primitives (think of this as another programming language).

Focus on model-based specifications, particularly VDN.


###Example of Algebraic Specification

Example of a boolean type.

```
INITIAL
		boolean

SORT
		bool

CONSTANTS
		true		: bool
		false		: bool

OPERATIONS
		not _		: bool -> bool
		_ or _		: bool, bool -> bool
		_ and _		: bool, bool -> bool
		_ impl _	: bool, bool -> bool
		_equiv _	: bool, bool -> bool

EQUATIONS
		not(not(A))	= A
		A or (B or C)	= (A or B) or C
		A or B		= B or A
		A or true	= true
		A or false	= A
		A and B		= not(not(A) or not(b))
		A impl B	= not(A) or B
		A equiv B	= (A impl B) and (B impl A)
END
```

`INITIAL` means that there are no values or relations other than those which can be deduced from the given ones, for example one can deduce that `A and B = B and A`, buy not `true = false`.

The mathematical branch of *category theory* is needed to reason about such specifications.


```
INITIAL
		lists (elem with {_ eq _ : elem,elem -> bool; undef : -> elem})

USES
		boolean

SORT
		list

CONSTANTS
		empty	: list
		undef	: list

OPERATIONS
		_ . _			: elem,list -> list
		first _			: list -> elem
		rest _			: list -> list
		is-undef _		: list -> bool
		_ is-member-of _	: elem,list -> bool
		_ eq _ 			: list,list -> bool
		at-end _		: list -> bool

EQUATIONS
		first(empty)		= undef
		first(undef)		= undef
		first(A.B)		= A
		rest(empty)		= undef
		rest(undef)		= undef
		rest(A.B)		= B
		is-undef(empty)		= false
		is-undef(undef)		= true
		is-undef(A.B)		= false
		E is-member-of undef	= false
		E is-member-of empty	= false
		E is-member-of (A.B)	= (E eq A) or (E is-member-of B)
		(A.B) eq (C.D)		= (A eq C) and (B eq D)
		empty eq empty		= true
		(A.B) eq empty		= false
		A eq B			= B eq A
		at-end(empty)		= true
		at-end(undef)		= false
		at-end(A.B)		= false
END
```


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


VDM as a Development Method
===========================

When using VDM, we start with a (very) abstract specification and, in a number of steps, develop this into an implementation

Each step involves:

* Data Reification
* Operation Decomposition

Data reification develops the abstract data types into more concrete data structures.

Operation decomposition develops the abstract implicit specification of functions and operations into algorithms which can be put into code.


Data Reification
----------------

Data reification develops the abstract data types into more concrete data structures.

There may be several steps before an implementation is reached.

Each step involves:

* Given an abstract data representation $ABS$, find a new representation $REP$.
* Find a **retrieve function** that relates $ABS$ to $REP$: $retr : REP \rightarrow ABS$.
* Prove that $REP$ is **adequet** to represent $ABS$. *i.e.* prove $\forall a \in ABS \bullet \exists r \in REP  \bullet a = retr(r)$
* Reqrite the functions and operations in terms of the new representation
* Prove that the new functions and operations preserve any data-type invariants of the new representation
* Prove that the new functions and operations model those of the original specifications; this involves two rules:

###Doman Rule

$$ \forall r \in REP \bullet \text{pre-}OPA(retr(r)) \Rightarrow \text{pre-}OPR(r) $$

###Modelling Rule

$$ \forall r', r \in REP \bullet \text{pre-}OPA(retr(r')) \land \text{post-}OPA(r', r) \Rightarrow \text{post-}OPA(retr(r'),retr(r)) $$

$r'$ is the initial state before the operation was run.


Implementation of Data Reification
----------------------------------

Implementation in a traditional programming language (e.g.: Java) suggests having a sequence of objects.

So, the first data reification step is to represent the data in terms of sequences.

We must not allow repetitions in our sequences because the same employee cannot occur twice; hence, we require an invariant on our new data type.

However, the set $\left\{{p,q}\right\}$ could be represented by $\left[{p,q}\right]$ or by $\left[{q,p}\right]$

A completely rigorous development down to programming language, then the programming language has to be formally specified.


Proving Correctness
===================

* *Validation* - Implementation which does the right thing.
* *Verification* - Implementation meets the specification.


Other Specification Methods
===========================

Software developers aren't going to use full-blown formal methods *except* where the cost of doing so justifies doing so (safety- and mission- critical systems). The complete use of mathematics is not justifiable in most cases.

There are some techniques to check a piece of code can be proved mathematically without too much effort without the heavy use of maths. This may help to avoid a lot of problems seen in code today.


Deficiencies of VDM
-------------------

VDM SL contains limited constructs for modularisation. Difficult to split a large specification into modules.

No support for palletisation and concurrency.

Must implement in a language which has also been formally specified.

RAISE (Rigorous Approach to Industrial Software Engineering) and others have tried to overcome some of the deficiencies of VDM.
