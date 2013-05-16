Architectures
=============

Autonomy
--------

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

LEARN is another suggested primitive, but no current architectures use this paradigm yet so a true paradigm shift has not occurred.


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


###Reflexive Behaviours
Reflexive behaviours are interesting as they imply the need for any type of cognition: if you sense it, you do it..

For a robot this would be a hardwired response, eliminating computation and guaranteeing speed of operation.

Reflexive behaviours can be categorised into three types:

1. Reflexes
2. Taxes
3. Fixed-action patterns

*Reflexes* are where the response lasts only as long as the stimulus and the response is proportional to the intensity of the stimulus.

*Taxes* are where the response it to move to a particular orientation. Baby turtles exhibit *tropotaxis*; they are hatched at night and move to the brightest light which, until recently, would be the ocean reflecting the moonlight. Ants exhibit a similar taxis, following trails of pheromones, this is known as *chemotaxis*.

*Fixed-action patterns* are where the response continues for a longer duration that the stimulus. This is helpful for fleeing predators. It is important to keep in mind that a taxis can be any orientation relative to a stimulus, not moving past.

These categories are not mutually exclusive. For example an animal going over rocks or through a forest where its view might be obscured might persist (fixed-action patterns) in orientating itself to the last sensed location of a food source (taxis) when it loses sight of it.

The tight coupling of action and perception can often be quantified by mathematical expressions. Animals can use external senses of percepts like gravity (*idiothetic*) combined with organs which sense external percepts like vision (*allothetic*) to perform a task.

###Coordination and control of behaviours
There are four ways to acquire a behaviour:

1. Innate
2. Sequence of innate behaviours
3. Innate with memory
4. Learn

*Innate* behaviours are behaviours which an entity is "born" with.

A *sequence of innate behaviours* is a sequence of behaviours which are innate, but which are triggered by the combination of internal state and the environment.

*Innate with memory* behaviours are innate behaviours which need some customisation based on the situation of the environment.

Behaviours which are not innate must be *learned*.



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


