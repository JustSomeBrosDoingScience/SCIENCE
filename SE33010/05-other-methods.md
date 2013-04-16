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
