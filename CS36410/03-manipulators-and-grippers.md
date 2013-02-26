Manipulators and Grippers
=========================

Parts of a Manipulator
----------------------

Arm, wrist, end effector.

Reaching a point in space is done via the arm (3 degrees of freedom (DOF)) (movement in x,y,z).

Wrist provides an additional 3DOF (rotation in x,y,z)

Arm is made up of links connected via joints.

Each link is a degree of motion (DOM), while each joint can provide a new DOF.

DOF is the number of independent movements an arm can make.

DOM $\ne$ DOF


Classifications of Arms
-----------------------

Type of arm   Prismatic/Linear   Revolute/Rotary
------------ ------------------ -----------------
Cartesian            3                0
Cylindrical          2                1
Spherical            1                2
Articulated          0                3

###Cartesian Geometry Arm
Good repeatability.

Straight line motion good.


###Cylindrical Geometry Arm
Resolution depends on extension of the arm.

High speeds due to base rotation.

Inertia can be a problem.

###Spherical Geometry Arm
Two axes of low, variable resolution.

Fairly flexible (can reach below base).

Complex control algorithms.

###Articulated Geometry Arm
Resolution dependant of the arms position.

Accuracy poor.

Repeatability good.

Excellent flexibility.

Complex control.

Error compounds.

###Beyond 3 joints

####Parallel Linkages
Parallel linkages allows for higher load capacity.

Fast motion

High Stiffness

Direct drive.

e.g.: Stewart/Gough platform.

####Serial Linkages
More degrees of motion.

More flexibility.

Allows redundancy.

Many control issues.


Arm Control - Direct Kinematics
-------------------------------

$$\text{Joint space} (d_i,\theta_i) \rightarrow \text{Cartesian space} (x,y,z)$$

Usually use inverse kinematics instead as it's easier to give a set of Cartesian co-ordinates:

$$\text{Joint space} (d_i,\theta_i) \gets \text{Cartesian space} (x,y,z)$$

Sometimes there is no response.


Wrists
------

Wrist provides orientation (yaw, pitch, yaw).


Grippers
--------

Vacuum, Electromagnetic, Fingers, End of arm tooling.
