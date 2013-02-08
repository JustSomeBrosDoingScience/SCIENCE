CS36410 - Intelligent Robotics
==============================

Myra Wilson (mxw) and Mark Neal (mjn).

Assessment
----------

* 100% Exam (3 from 5).

CS26410 get it easy and are assessed on practicals :(


Commitment
----------

* 16 Lectures
* 6 hours of practicals after Easter
* Background reading


Robot Definitions
-----------------

> N. "A machine capable of carrying out a complex series of actions automatically, especially one programmable by a computer."

Not the best definition as a washing machine could potentially be defined to be a robot.

A better description of the discipline is one which includes

* Design, manufacture, control and programming of robots
* Use to solve problems.
* Study of control processes, sensors and algorithms used in humans, animals and machines.
* The application of these control processes and algorithms to the design of robots.

Specific organisms have evolved to interact with the environment. So now a lot of research is done to build robots to imitate these simple organisms. We're starting to get to the point where you can do similar mechanical things.

Nature is a big inspiration for robotics

Essential part of robotics is the interaction with the environment. A robot should be able to perceive the world and affect the world around it.

From "Rabota" the Czech meaning for menial labour/work. Term "robot" coined in K. Chapek's play "Rossum's Universal Robots" (1920).

Robotics first used by Issac Asimov in his novels. Also brought up the ethics of robots:

1. A robot may not injure a human being or, through inaction, allow a human to be harmed.
2. A robot must obey orders from a human, except where it conflicts with the first law.
3. A robot must protect it's own existence, except where it conflicts with the first or second law.


What do we want out of a robot?
-------------------------------

Do we want one single robot to do many tasks or lots to do singular ones?

We already have things like Roomba and Asimov. Space robots are particularly popular.

Working on more and more complex robots.

Abstracted biological principals - stealing ideas from nature.

Something will always go wrong with robots.

Swarm robotics quire interesting.


Why would we use a robot?
-------------------------

Where humans would be at significant risk (space exploration, nuclear deactivation, etc.)

Economically better to have a robot where menial and repetitive tasks need a high level of accuracy.

Humanitarian use where there is a great risk (search and rescue in danger areas).

Bottom-up approach tends towards better performance (implement the simplest organism first, then work upwards. Natural selection, different levels of behaviour which can communicate).


Environmental Differences
-------------------------

* Computers
    * Input symbols are static
    * Operation given consistent results
    * Environment is fixed and repeatable
    * System only receives intended inputs
    * Perfect performance assumed
* Robots
    * Noise
    * Actions may have different responses
    * Objects may move independently
    * Influences from external agents can interfere
    * Operation environment is unreliable, dynamic and incomplete.



Intelligent Robotics
--------------------

> *"An intelligent robot is a machine able to extract information from its environment and use knowledge about its world to move safely in a meaningful and purposive manner."* - Arkin

> *"An intelligent robot is a machine creture which can function autonomously."* - Murphy

Usually specific to function.

Popular for industrial usage, especially production lines.

Revolution in computing power has allowed for a rise of more sci-fi robots. Now quite common military.

###3 'D's of Robots

* Dirty
* Dull
* Dangerous


Levels of autonomy
------------------

###Remote Control
Completely controlled via a remote by a human.

Robot Wars (*A: Myra is awesome*).

Not intelligent at all.

###Teleoperation
Human operator controls robot from a distance, who usually cannot physically see the robot.

Sensors acquire information about the environment and is displayed for the operator to see. This can allow for addition sensory capacity (i.e. high pitched noises, etc.) so long as it can be displayed in a meaningful way.

Requires a communication link, there's a number of websites which offer this kind of this.

Requires $\ge$ one operator.

This is most useful when tasks are unstructured and aren't repetitive.

Situations where this is likely: a dynamic environment, dexterous task, need for advanced perception.

Important to have a good form of displaying the data meaningfully.

Needs trained operators.

###Telesense
Introduces Virtual Reality (VR) to teleoperation

Attempts to remove some of the cognitive fatigue and simulation sickness from the operator.

Operator has complete sensory feedback.

This is very expensive and requires a high bandwidth rate. 

###Semi-autonomous
Able to perform tasks autonomously. Good for planetary missions.

Good for unstable communication.

Continuous assistance; delegate tasks to the robot whilst observing it. Can use teleoperation for delegate tasks. Still needs the high bandwidth.

Control trading; human initiates the action for the robot to complete autonomously. Assumes robot is capable of autonomously accomplishing tasks robustly to unexpected situations.

###Autonomous
Able to perform tasks autonomously without any human input.

"Weak Autonomy" - robots which carry on-board controllers and power supplied.

"Strong Autonomy" - Require the power of self-government:

* Ability to move in its environment to perform a number of tasks
* Adapt to changes in environment
* Determine its course of action by its own reasoning processes
* Build internal representation of the world to plan and learn from experience and change its behaviour accordingly

(*A: Reinforcement learning is probably one of the better techniques for this?*)


Achieving Autonomy
------------------

Artificial Intelligence Approach

* Knowledge Representation
* Natural Language Processing (NLP)
* Learning
* Planning and Problem Solving
* Inference
* Search
* Vision (and other sensor readings)

Robotics feeds into AI and vice versa.
