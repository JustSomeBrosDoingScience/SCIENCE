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
  true   : bool
  false  : bool

OPERATIONS
  not _	     : bool -> bool
  _ or _     : bool, bool -> bool
  _ and _    : bool, bool -> bool
  _ impl _   : bool, bool -> bool
  _ equiv _  : bool, bool -> bool

EQUATIONS
  not(not(A))   = A
  A or (B or C) = (A or B) or C
  A or B        = B or A
  A or true     = true
  A or false    = A
  A and B       = not(not(A) or not(b))
  A impl B      = not(A) or B
  A equiv B     = (A impl B) and (B impl A)
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
  empty  : list
  undef  : list

OPERATIONS
  _ . _             : elem,list -> list
  first _           : list -> elem
  rest _            : list -> list
  is-undef _        : list -> bool
  _ is-member-of _  : elem,list -> bool
  _ eq _            : list,list -> bool
  at-end _          : list -> bool

EQUATIONS
  first(empty)         = undef
  first(undef)         = undef
  first(A.B)           = A
  rest(empty)          = undef
  rest(undef)          = undef
  rest(A.B)            = B
  is-undef(empty)      = false
  is-undef(undef)      = true
  is-undef(A.B)        = false
  E is-member-of undef = false
  E is-member-of empty = false
  E is-member-of (A.B) = (E eq A) or (E is-member-of B)
  (A.B) eq (C.D)       = (A eq C) and (B eq D)
  empty eq empty       = true
  (A.B) eq empty       = false
  A eq B               = B eq A
  at-end(empty)        = true
  at-end(undef)        = false
  at-end(A.B)          = false
END
```


