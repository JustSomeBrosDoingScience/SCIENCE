Worksheet 1
===========

##Question 1
Show, by constructing the appropriate truth tables, that:

###1.a
$$\neg P,P \lor Q \models Q$$

 $P$   $Q$   $\neg P$   $P \lor Q$   $Q$
----- ----- ---------- ------------ -----
T     T     F          T            T
T     F     F          T            F
F     T     T          T            T
F     F     T          F            F


###1.b
$$P \land Q \models P \lor Q$$

 $P$   $Q$   $P \land Q$   $P \lor Q$
----- ----- ------------- ------------
T     T     T             T
T     F     F             T
F     T     F             T
F     F     F             F


###1.c
$$P \Rightarrow Q, Q \Rightarrow R \models P \Rightarrow R$$


 $P$   $Q$   $R$   $P \Rightarrow Q$   $Q \Rightarrow R$   $P \Rightarrow R$
----- ----- ----- ------------------- ------------------- -------------------
T     T     T     T                   T                   T
T     T     F     T                   F                   F
T     F     T     F                   T                   T
T     F     F     F                   T                   F
F     T     T     T                   T                   T
F     T     F     T                   F                   T
F     F     T     T                   T                   T
F     F     F     T                   T                   T


##Question 2
Show, by constructing the appropriate truth tables, that:

###2.a
$$\models (A \land B) \Leftrightarrow (\neg(\neg A \lor \neg B))$$

|c|c||c|c||c|

$A$ & $B$ & $A \land B$ & $(\neg(\neg A \lor \neg B))$ &
$A \land B \equiv \neg(\neg A \lor \neg B)$\
T & T & T & T & T\
T & F & F & F & T\
F & T & F & F & T\
F & F & F & F & T\


###2.b
$$\models (A \Rightarrow B) \Leftrightarrow (\neg A \lor B)$$

|c|c||c|c||c|

$A$ & $B$ & $A \Rightarrow B$ & $\neg A \lor B$ &
$A \Rightarrow B \equiv \neg A \lor B$\
T & T & T & T & T\
T & F & F & F & T\
F & T & T & T & T\
F & F & T & T & T\


###2.c
$$\models (A \Leftrightarrow B) \Leftrightarrow ((A \Rightarrow B) \land (B \Rightarrow A))$$

|c|c||c|c|c|c||c|

$A$ & $B$ & $A \Leftrightarrow B$ & $A \Rightarrow B$ &
$B \Rightarrow A$ & $(A \Rightarrow B) \land (B \Rightarrow A)$ &
$A \Leftrightarrow B \equiv (A \Rightarrow B) \land (B \Rightarrow A)$\
T & T & T & T & T & T & T\
T & F & F & F & T & F & T\
F & T & F & T & F & F & T\
F & F & T & T & T & T & T\

Using the results above, deduce than any proposition is logically
equivalent to one written using only the operators $\neg$ and $\lor$.

---

First, we know:

$$A \land B \equiv \neg(\neg A \lor \neg B)$$

And:

$$A \Rightarrow B \equiv \neg A \lor B$$

And:

$$A \Leftrightarrow B \equiv (A \Rightarrow B) \land (B \Rightarrow B)$$

Then using this, we can deduce:

$$A \Leftrightarrow B \equiv (\neg A \lor B) \land (A \lor \neg B)$$

Substituting out the $\land$:

$$A \Leftrightarrow B &\equiv \neg(\neg(\neg A \lor B) \land \neg(A \lor \neg B))\end$$

Define the operator $|$ (*nand*) by the truth table:

|c|c||c|

$A$ & $B$ & $A|B$\
T & T & F\
T & F & T\
F & T & T\
F & F & T\

Show, by constructing the appropriate truth tables that:

$$\models (\neg A) \Leftrightarrow (A | A)$$

|c||c|c||c|

$A$ & $\neg A$ & $A | A$ & $\neg A \equiv A|A$\
T & F & F & T\
F & T & T & T\

$$\models (A \lor B) \Leftrightarrow ((A|A)|(B|B))$$

|c|c||c|c||c|

$A$ & $B$ & $A \lor B$ & $(A|A)|(B|B)$ & $A \lor B \equiv (A|A)|(B|B)$\
T & T & T & T & T\
T & F & T & T & T\
F & T & T & T & T\
F & F & F & F & T\


###???

Using Q2 and these results, deduce that any proposition is logically
equivalent to one written using only the operator $|$.


We know:

$$\neg A \equiv A | A$$

And:

$$A \lor B \equiv (A|A)|(B|B)$$

And as we have already deduced that any proposition can be written using $\neg$ and $\lor$, we can just substitute in the above identities to replace both these operators in and proposition.

$$A \land B \equiv \neg(\neg A \lor \neg B)$$

$$\equiv \neg(\neg(A|A) | \neg(B|B))$$

Substitute $A|A$ for $\neg A$ to cancel out the double negatives.

$$\equiv \neg(A | B)$$

Therefore:

$$A \land B \equiv (A|B)|(A|B)$$

And:

$$A \lor \neg B \lor C \equiv ((A|A)|(\neg B|\neg B)) \lor C$$

$$\equiv ((A|A)|B) \lor C$$

$$\equiv ((A|A)|B)|(A|A)|B)|(C|C)$$

Prove the following:

$$\neg \neg P, P\Rightarrow Q \vdash P \land Q$$

  --- ------------------- ----------------------------------
  1   $\neg\neg P$        premise
  2   $P \Rightarrow Q$   premise
  3   $P$                 1 by $\neg$-Elimination
  4   $Q$                 3,2 by $\Rightarrow$-Elimination
  5   $P \land Q$         3,4 by $\land$-Introduction
  --- ------------------- ----------------------------------

Q.E.D.

$$P, P \Leftrightarrow Q \vdash Q \lor R$$

  --- ----------------------- ------------------------------------
  1   $P$                     premise
  2   $P \Leftrightarrow Q$   premise
  3   $P \Rightarrow Q$       2 by $\Leftrightarrow$-Elimination
  4   $Q$                     1,3 by $\Rightarrow$-Elimination
  5   $Q \lor R$              4 by $\lor$-Introduction
  --- ----------------------- ------------------------------------

Q.E.D.

$$P \land Q, P \Rightarrow S, Q \Rightarrow T \vdash S \land T$$

  --- ------------------- ----------------------------------
  1   $P \land Q$         premise
  2   $P \Rightarrow S$   premise
  3   $Q \Rightarrow T$   premise
  4   $P$                 1 by $\land$-Elimination
  5   $Q$                 1 by $\land$-Elimination
  6   $S$                 2,4 by $\Rightarrow$-Elimination
  7   $T$                 3,5 by $\Rightarrow$-Elimination
  8   $S \land T$         6,7 by $\land$-Introduction
  --- ------------------- ----------------------------------

Q.E.D.
