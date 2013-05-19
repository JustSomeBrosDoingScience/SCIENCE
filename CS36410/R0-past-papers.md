Past Paper 2012
===============

[Past Paper 2012](http://www.aber.ac.uk/en/media/CS36410-12.pdf)

Question 1
----------

This question examines the area of robot control architectures.

###Question 1.a)
Provide a description of reactive architectures, giving two examples to illustrate your answer.

---

* No PLAN primitive
* All sensor readings (SENSE) go into actuators (ACT)
* Biologically inspired
* Usually done in hardware for efficiency

Coward and aggressive diagrams.


###Question 1.b)
Provide a description of deliberative architectures, giving two examples to illustrate your answer.

---

* Sensor inputs (SENSE) passed into control algorithms (PLAN) which issue directives to actuators (ACT)
* No link from SENSE to ACT
* Computationally complex
* Can build up a world model

??


###Question 1.c)
A student project is set to design an architecture which allows a small robot to successfully find the centre of a tabletop maze. The robot must repeat the task 10 times with the maze changed randomly each time. 

Marks are awarded for the best average time taken for the robot to find the centre, and the quickest time overall to reach the centre. If you had the choice between using a deliberative or a reactive architecture for the above task, which would you use? Given detailed reasons for your choice.

---

Pros for reactive:

* Simple
* Reliable
* Low (or no) computation
* "Follow the left wall" strategy
* Not affected by the randomisation

Cons for reactive:

* No pathfinding - may get in loops. May go back to locations already visited. Cannot change strategy.
* Maybe too simple?
* Speed purely based on luck of the draw.

Pros for deliberative:

* Pathfinding algorithms to improve speed
* Can be made not to revisit unless necessary
* Can change strategies depending on situation

Cons for deliberative:

* Very complex
* Very difficult to get right
* May not be reliable
* Has to build up a world model to pathfind
* Computational complexity
* Power consumption?


Question 2
----------

This question examines the area of robot bodies and manipulator arms.

###Question 2.a)
What are the main parts of a robot manipulator? Briefly describe the function of each part.

---

* Arm - provides DOF
* Wrist - provides DOM
* End effector - manipulates environment.


###Question 2.b)
Discuss the difference between Degrees of Freedom (DOF) and Degrees of Motion (DOM), giving examples to illustrate your answer.

---

DOF - Cartesian coordinates (x,y,z)

DOM - Rotational (roll, pitch, yaw)


###Question 2.c)
A scientist requires a robot to retrieve experimental data from inside a volcano, including the acquisition of soil samples. A manipulator arm is required on a mobile platform.

####Part i)
What method of locomotion would you recommend for your robot? Discuss why you would choose this method.

---

Legs can deal with the soft terrain and are less likely to melt

Tracks not useful due to temperatures.

Wheels could be useful but all terrain tires may struggle with heat.


####Part ii)
Discuss the issues associated with mounting a manipulator arm on a mobile platform.

---

*No idea, here lies the blagfest*


Question 3
----------
This question examines the area of biologically inspired robotics.

###Question 3.a)
Describe the physical body, and the behaviour exhibited by Grey Walter’s turtles, and detail how the behaviour was achieved.

---

*No idea, revision needed here*


###Question 3.b)
Briefly discuss why many roboticists take inspiration from nature?

---

Known working examples.

Evolutionary design for reactive systems.


###question 3.c)
Using a system you have studied as an example (do not use your answer from the Grey Walter question in part a)), show where inspiration from nature has been successfully implemented in a robotic system.

---

*And some more revision here too*


Question 4
----------
This question examines aspects of the physical robot.

###Question 4.a)
Define the following terms:

---

1. Passive Sensing - reading energy from the environment.
2. Active Sensing - putting some form of energy into the environment to sense it.


###Question 4.b)
Describe stereo vision and active vision systems, highlighting the similarities and differences between them.

---

Stereo - two cameras, uses CV techniques to be able to work out where an object is when the distance between the cameras is known.

Active - the camera is movable.

*more revision*


###Question 4.c)
“Logically redundant sensors can be used interchangeably”. What are logically redundant sensors? Discuss whether the above statement is true, giving detailed reasons for your answer.

---

Logically redundant sensors; using different processing algorithms from the same sensor reading.

Not interchangeable as specific to the type of sensor.



###Question 4.d)
Discuss the 3 different stages of the perception problem (reading a value from sensor, interpreting the data, and performing an action), giving examples to illustrate your answer.

---

Accuracy of sensors. Anomalous values from the sensor.



 

