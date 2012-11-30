REST in more Detail
===================

Resource Orientated Archiecture (ROA)
-------------------------------------

Concepts:
* Resource
* URI
* Representations
* Links

Properties:
* Adressability
* Statelessness.


Resource
--------

Resources are pretty obvious. Usually persistent.


Universal Resource Indicator
----------------------------

Noun based and static.


Statelessness
-------------

Statelessness is the absence of state. It assumes all HTTP requests are self-contained. This means 
everything is addressable, helping accessability and scalability as there are fewer failure modes.

It also works nices as HTTP is stateless.

REST Methods
------------

POST isn't (and shouldn't be) a catch-all.

GET and HEAD are immutable (or really should be).
