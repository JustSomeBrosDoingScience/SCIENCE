Mobile Robots
=============

No longer so limited, power issues.


Overview
--------

Wheels most common (easily understandable). Legs and fliers less common as more complex. A lot of biologically inspired movement.


Locomotion
----------

> N. "Movement or the ability to move from one place to another."

Tethered are fairly common to, partly due to the expense.

###Stability

Legs less stable than wheels (generally).

* Number and geometry of contact points
* Centre of gravity
* Static/dynamic stability
* Inclination of terrain

Humans can be statically stable, but that's due to muscles always being strained, walking is more like controlled falling and use dynamics of the situation to help conserve energy.

The higher the centre of gravity the less stable you will be. Difficult to control high centre of gravity.

Rough terrain may impair stability.


###Characteristics of contact

Small area of foot or large footprint?

* Contact point/path
* Angle of contact
* Friction

"Umbrella"-like foot to stop sinking in snow, etc.

Friction - pulling, pushing power.


###Environment

* Structure and medium.

Water will affect the sensors you use.

Ground types.

Ground -> air robots are now coming along; fairly impressive :). Transition is the most important in this.

Have to understand the morphology (how the robot is built).

Understanding the relation to the environment.

Understand the material properties, that is what it's made of, how the joints work, etc.

Sometimes a small change in the morphology of the robot can make a large change.


Wheeled robot systems
---------------------

Wheels have been around for a long time and are well understood. Fairly versatile and lots of different types:

* Standard
* Castor
* Swedish
* Spherical

All can be motorized, steered or just passive.

Different types good for different tasks.

4 wheels is good for stability. Different combination of powered and steered wheels. FWD, RWD, 4x4. Turning circles not great. Omnidirectional wheels can help this.

3 wheels are less stable. Quit common to have 2 powered, differential wheels with an extra point of contact. Good lab-based robots. Better turning circles that 4WD typically. 

Machina Speculatrix 3WD with valves and motors. One of the first biological inspired robots. Powered, steerable first wheel, sensor on the same steering column as the wheel.

2 wheels are pretty unstable. First examples of dynamic stability (inverted pendulum). Lots of feedback needed. Low centre of gravity helps.

Unicycle robots very uncommon.

6 wheels better for terrain. Independent suspension usually needed to stop balance issues. Good pulling power. On the Mars Rover the wheels are also steppers. 

Tracks can be very useful for rough terrain (think tanks). Problem with tracks is the maintenance of tracks. Turning is skid based. Can solve some climbing problems.

Statically stable if $\gt$ 2 wheels. Useful on solid terrain; rough terrain requires bigger robots.


###Advantages

* More stable
* Less energy
* Simple Design
* **Cheap**


###Disadvantages

* Specific to environment
* Climbing ability? (Doctor Who: "ELEVATE")


Legged Robots Systems
---------------------

Advantages of adaptability and manoeuvrability over rough terrain - capable of crossing pits and holes.

Disadvantages of power and mechanical complexity. Difficult to control.

Legs must be capable of sustaining part of the robots total weight.

Problem between static stability and dynamic stability.

1 leg: hoppers. MIT looking at controlling legs.
