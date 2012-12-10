# Autonomous Robot Localisation, Path Planning Navigation and Obstacle Avoidance
----

## Autonomous Operation

* Ideally issue a high level command - "go to the top of that hill"

## Required Funcionality for Navigation


* Cameras - less power demanding than systems like LIDAR
* Stereo PanCam - Cool filters 'hyperspectral'
* Navigation Cameras and Hazard Cameras - usually lower resolution and often
  monochrome

## Environment Model: 
* DEM - Digital Elevation Model
* DTM - Terain gradient and feature identification
* Data may come back to earth and processed by engineers rather than local processing.

## Localisation Problem

* Knowing where you are on Mars is very difficult: no GPS etc.
* Mars Magnetic regions are localised and anomalous - no compasses
* Can't commit orbital resources full time for navigation
* Can't use radio telescopes and terrestrial resources full time (Jodrel Bank)
* Line of site doesn't always work - i.e. if on the other side of the planet
  from Earth.
* Dead Reckoning - Wheel slippage, instrument drift etc etc.

## Localisation Solution

* Ron Lee et al.
* Always know where you are when you land - then use Lee's algorithm from then
  on
* Not done onboard - could do with having this in the future.

## Obstacle Avoidance

* Reactive Control - sometimes stumbles upon local minima but much faster
* Deliberative Control - Generate a map of the environment and plan the route
  around obstacles etc. Slower and more computationally expensive.

## Path Finding

* A* Works if you have a good model of your world and it doesn't change.
* D* Allows you to modify your existing model to avoid new obstacles etc.
  Avoids throwing away a working model and rebuilding from scratch by updating
  path costs dynamically.
* CMU Navigation Architecture
* Global planner uses D* 
* Arbiter combines Global planner with 'Morphin' which is the local navigation
  system


### Morphin

1) Black areas have not been seen before
2) Grey areas - recent, less recent and old data
3) Textured areas are obstacles
4) sensing arcs 'whiskers' based on steering arcs - mapping each steering
trajectory to see if you're going to collide with anything.
5) Goodness histogram  - sensing arc cells occupancy - refer to how traversable
each whisker is.
6) Certainty histogram - cell data age
7) Traversability histogram - weighted combination of goodness and certainty.
