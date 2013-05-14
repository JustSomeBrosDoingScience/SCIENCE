Architectures
=============

Autonomy:

* Must be able to move around in the real world
* Must be able to respond to the real world
* Should be capable of performing tasks and interacting with the world
* Should be able to survive independently in the world for a period of time


Robotics Paradigms
------------------

* Reactive
* Deliberative/Hierarchical
* Hybrid


Primitives
----------

Robot Primitives  INPUT                     OUTPUT
----------------  ------------------------  ------------------
SENSE             Sensor Data               Sensed Information
PLAN              Information               Directives
ACT               Information or Directives Actuator Commands


Reactive Paradigm
-----------------

Stems from the mid-80's, although other forms were around before then.

Originated through researchers looking at biology and cognitive science.

More accessible due to decrease in hardware costs and increase in processing power

Cheap.

Only uses `SENSE` and `ACT` primitives

Advantage that you're acting immediately with the real world. Lots of knowledge needed by the designer.

* Based on parallel "behaviours"
* Sensors connected directly to actuator
* Usually a simple arbitration mechanism
* Execute in the cycle time of most natural environments
* No generalised model of the world
* Uses the world as its own model
* Typically lacks a formal mechanism for handling complexity.


Deliberative Paradigm
---------------------

Also known as the hierarchical paradigm.

Uses `SENSE`, `PLAN` and `ACT` primitives. `ACT` primitive only works from directives.

Driven by AI research.

Big problem with processing time.

World model is the idealised model of the world.

"Brain" is the bottleneck.

Difficulty when working with dimensions, etc.

###Closed World Assumption and the Frame Problem
The *closed world assumption* says that the world model contains everything the robot needs to know; there can be no surprises.

If this assumption is violated the robot may not be able to function correctly.

The *frame problem* is the size complexity of a problem given the exponential nature of the real world.


Agents Architecture
-------------------

Each agent has a level of competence, no individual is able to complete the whole task.

Together and linking through cues agents are able to complete a task.


Hybrid Paradigm
---------------

Uses all primitives. A combination of both.

Behaviour (`SENSE-ACT`) primitive created by directive from `PLAN` primitive. Behaviour primitives
are effectively reactive systems.

Decomposes tasks into subtasks; figuring out which behaviours are best to achieve subtasks.

Planner can eavesdrop on behaviours.


Evaluation of Paradigms
-----------------------

###Criteria
* Modularity
* Niche target ability
* Portability
* Robustness


