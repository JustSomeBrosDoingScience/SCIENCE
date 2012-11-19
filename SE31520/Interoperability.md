Interoperability
================


Representational State Transfer (REST)
--------------------------------------
Notes for later.

* GET
* POST
* PUT
* DELETE


Interoperability
----------------

Operating between systems. This can be:

* Within an organisation (i.e. within an intranet).
** App to App (A2A)
** Enterprise Application Integration (EAI)
* Between Organisations
** Business to Business (B2B)

As a side note middleware supports interoperability (see CICS for a great example :D)


Methods of Interoperability
---------------------------

* Sockets
* Remove Method Invokation (RMI) and Remote Procedure Call (RPC)
* Message-based.


Sockets
-------

Advantages:
* Cross platform
* Language inderpendant (via kernel).
* Reliabile (if used over TCP).
* Light-weight (if used over UDP).
* Encryption is easy to add.

Disadvantages
* Need application specific protocol which tends not to be scalable.
* Cross language mappings are difficult.
* Lack of distribution services


Remote Method Invokation and Remote Procedure Call
--------------------------------------------------

Advantages:
* (Un)Marshalling handelled automagically.
* Some distribution services.
* Access to CORBA IIOP (Common Object Requres Broker Architecture).
* Builds on services provided by sockets.

Disadvantages:
* Java specific
* Even with IIOP - it can be limited to Intranet due to firewalles.
* Synchronous Communication focus.
* Too low-level.
* Complex

Message-based Protocol
----------------------

Advantages:
* Asynchronous.
* Publish/Subscribe.
* Guarentees on delivery.

Disadvantages:
* Hard to make synchronous.
* Typically proprietary.
* Requires a message broker.



