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


