Sensors and Perception
======================

Fewer limitations than before, power is the biggest issue.

> Sensor (n.) - A device that measure a physical quantity and converts it into a signal which can be read by an observer or by an instrument.

Interpretation performed by observer.


Logical Sensors
---------------
A logical sensor is a unit of sensing or module that supplies a particular percept. It consists of the signal processing from the physical sensor and the software processing needed to extract the percept. It is ythe functional building block for perception.

Encourages modular design.


Behavioural Sensor Fusion
------------------------
*Sensor fusion* is a brad term for any process that combines information from multiple sensors into a single percept.

The motivation for this stems from three basic combinations:

* Redundant
* Complementary
* Coordinated

Can be used when a particular sensor is too imprecise or noisy to give reliable data. Adding a second sensor can give another "vote" for the percept.

This is to try and avoid high *false positives* and *false negatives* rates.

*Physical redundancy* allow two similar sensors to perceive objects from two different locations (one sensor might be better at sensing lower objects whilst the other high objects).

*Logical redundancy* is the use of different algorithms to process the information from a single sensor.



Passive sensors
---------------

Environment provides energy generating the signal (no interaction).

e.g.: Light sensor, temperature sensors, etc.


Active Sensors
--------------

Sensor puts out energy into the environment to either change or enhance it.

More energy usage

e.g.: Sonar


Active Sensing
--------------

Moving the sensor around to get a better view of the environment.


Sensor Categories
-----------------

* Binary
* Analogue
* Discrete
* Arrays:
    * Linear (sonar ring)
    * 2D (camera)
    * IR sensitive pixels
    * Artificial skin
    * etc.

###Robotic Specifics

Global sensors, sensors outside of the robot.

Local sensors which are on-board and powered by the robot.

Internal (proprioceptive) sensors to monitor the robot's internals, or external (extrioceptive)


Sensor Attributes
-----------------

### Field of View (FOV)

How much of the world can *reliably* be measured?

Vertical, horizontal degrees and range.


### Accuracy, repeatability and resolution

Accuracy - How close to a set length can your sensor measure to?

Repeatability - Is it doing the same thing every time? (noise?)

Resolution - What degree can be measured to?


### Responsiveness in the target domain

How well does the sensor work in the current environment?

> You may have a sensor which is brilliant for brick walls, if you then introduce a glass surface does it still respond?


### Power Consumption

Active sensors drain power.


### Hardware Reliability

Sensors work best within a certain range of physical conditions.


### Size

Relative to the robot.


### Computational complexity

How does the computation of the sensor data scale?

Time is the biggest factor involved with this generally ;)

Big-O notation.


### Interpretation Reliability

How reliable will that sensor be in a particular environment?


Attributes for a sensor suite
-----------------------------

Surviving a failure is referred to as *fault tolerance*.

### Simplicity

Straightforward hardware and operating principals are less likely to go wrong.


### Modularity
The ability to remove or add sensors without implications.


### Redundancy
Physical redundancy - having 2+ identical sensors. Remembering the problems of not being able to have two sensors in the exact same place.

Logical redundancy - having 2+ different sensors measuring the same quantity.


Common Sensors in Robotics
--------------------------

### Shaft-encoder
Mounted directly on the motorshaft before the gearbox (higher resolution). Counts the number of ticks.

With two, the phase-shift between encoder signals 1 and 2 indicate direction.


### Accelerometer
Measures acceleration along one axis; one way to do this: linear variable differential transformer (LVDT) measures linear displacement.


### Gyroscope
Measuring rotation change of orientation along one axis. Fundamental to helicopters.


### Inclinometer
Measuring absolute orientation angle about one axis.


### Compass
Measuring absolute orientation using the Earth's magnetic field. Keep away from any electromagnets (wheels, speakers, etc.).

Analogue (low resolution) or digital.

Frequently applied for self-localisation.


### Global Position System (GPS)
Have become more accurate. Within a meter outdoors (is that enough?).

Outdoors better (obviously).


### Sonar Sensors
Proximity measure (15cm - 5m)

FOX approx. 15 deg.

Main problems: reflections and interferences.

Sends out an acoustic signal (50kKHz - 250KHz) is emitted for about 1ms, the time until echo returns is a measure for how far the object is. If no signal is received in a given time then the reading is too far and ignored.

Very cheap. Good for a general view of the environment.

Can be used underwater with a change in frequency.

#### Reflections
Signals seem to take longer to come back as it has reflected.

#### Interferences
A ping from one sensor picked up by another.


### Lasers
Similar principals to sonar but faster and 2D capabilities (indoor 8-32m, outdoor 32-80m).

Scanner is quite large.


### Infra-Red (IR)
Non-linear proximity measure. Below the measure ranges, values indicate larger distances. Strategies needed for close objects.


### Force Sensors
Used to measure the amount of force applied to the sensor.


### Cameras
Digital cameras you get an array of colour model-encoded pixels (3 bytes, 24-bits "true colour"); grey resolution - 1 byte.

CMOS sensor chips measure only brightness, but colour filter for each pixel delivers colour data.

CMOS sensor senses more green as this is more true to the human eye. Format of this is:

-- --
G  R
B  G
-- --

Trade-off between frame-rate and resolution.

Manufacturers focused on resolution while robotisitics would prefer high frame-rate.

Omni-vision via hyperbolic mirror ($2\pi$ vision).

Cameras can be put on an active system - pan and tilt system or pan, tilt and verge system.

####3D cameras
Distance measue via pixel correspondence between two images from different cameras.

Calibration can be difficult and camera configuration cannot be changed afterwards.

Pixel correspondence difficult for homogeneous regions and in general has high computation costs.

Changing light conditions are difficult to handle.

####3D Laser Scanners
Provide distance and reflectivity independent of the lighting conditions.

Expensive and unwieldy.


The Perception Problem
----------------------
Read a value from the sensor, then interpret the data, then perform an action or reaction.

### Reading from Sensors
Information derived directly from the real world.

What do we mean by direct?

* Voltages
* Presence
* etc.

### Interpret Data
How to abstract sensor values into assumptions about the real world.

Perception is limited by:

* Physical Sensory ability
* Method of reading the sensors
* The assumptions made

### Performing actions and reactions
React to the sensor in a pre-defined way (reactive).

Store away for later use (deliberative).

More on this later in the course.

###The problem
Sensor data may be wrong.

Data from different sensors may or may not match.

Some sensor data can take longer to process than others, so there may be time lags.

Sensor data coming in from different sensors may be coming from different areas of the environment.

Deciding what to believe is a difficult task.


