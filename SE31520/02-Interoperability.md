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
     * App to App (A2A)
     * Enterprise Application Integration (EAI)
* Between Organisations
     * Business to Business (B2B)

As a side note middleware supports interoperability (see CICS for a great example :D)


Methods of Interoperability
---------------------------

* Sockets
* Remove Method Invokation (RMI) and Remote Procedure Call (RPC)
* Message-based.
* XML-Based
* XML Remote Procedure Call
* SOAP
* REST


Sockets
-------

Advantages:

* Cross platform
* Language inderpendant (via kernel).
* Reliabile (if used over TCP).
* Light-weight (if used over UDP).
* Encryption is easy to add.

Disadvantages:

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


XML-Based
---------
Can be XML-RPC or SOAP/WSDL.

Have the advantage of being language and platform inderpendant, and have descriptors (XSD).


XML Remote Procedure Call
-------------------------

Advantages:

* Similar to RMI/CORBA
* Evolved into SOAP
* Service represented by a single URL.
* Operation defined by the XML body of the HTTP Request (which is a POST).
* Scoping depends on context.

Disadvantages:

* Doesn't use all HTTP methods (only POST). Is a special protocol.
* Resources not identified explicitly.
* Unknown side-effects.


SOAP
----

Advantages:

* Runs over HTTP(S).
* RPC and XML.
* Application-level.
* WSDL defines service operations.
* UDDI (Universtal Description Discovery Initiative) - A registry containing info about web 
  services (e.g. URL).

TODO Diagram here.

Disadvantages:

* Same issues as XML-RPC
* Complex specification.
* Inprecise specification.
* Specification was developed inderpendantly.

REST
----

* Get
* Post (New)
* Put (Update)
* Delete
* Head

REST is inheritantly HTTP focused. As such all resources have a URL.

TODO Diagram here.


