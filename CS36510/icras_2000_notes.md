#ICRAS 2000 Paper

#Introduction and Abstract

The ICRAS paper discusses the Carnegie Mellon Rover Navigation architecture.
I've made some notes on the things that are discussed in the paper. The system
provides "globally intelligent behaviour for a small computational resource."


* Large areas unlikely to be mapped high-res a priori so the rover must explore
  as it goes - incorporating new data into its database.
* Dealing with large amounts of information is also difficult. Solved through
  layered approach - local and global navigation.

Two additional challenges:
* There must be the ability to discriminate among obstacles to be avoided vs
  obstacles to be avoided *at all costs*.
* Due to limited computational power, the sensors and decision making must be
  as efficient as possible.

CMU Rover's ATRV-2 is based on NASA JPL Bullwinkle.


#Related Work

Local navigation: 

* Prior to this paper most works consider that the world is composed of obstacles
  and free space. This can cause robot to take a long detour.
* More recently systems that use continuous measures of traversablity to decide
  which obstacles are navigable.
* Seraji uses fuzzy logic terms ('passable', 'highly-impassable') to represent
  traversability measures.

Global navigation:

* Cannot preplan an optimal path (limited sensor information)
* Rover acquires information on its rounds and updates its plan accordingly

