Single Sign-On
==============

Enables a user to log-on once to a system without re-providing credentials.

Security Assertion Markup Lanuage (SAML)
----------------------------------------

Developed by OASIS. SAML makes assertions about users, these assertions may contain statements that are used by resources to grant access to a resource.

There are 3 different kinds of statements:

* Authentication
    * Asserts that the user was authorised and how.
* Attribute
    * Asserts that a user is associated with certain attributes.
* Authentication Decision
    * Asserts that a user is permitted to do the action.

Usually involves a simple request response.

Each statement has a query, the response is a statement (except attribute statements, which result in an assertion containing the statement).

Version 2.0 introduces more protocols.

Use XML, HTTP and SOAP standards.

Shibboleth
----------

Open Source under Apache2.

User SAML.

Adopted by JISC.

Uses public keys to establish trust between domains.

OpenID
------

Open Source decentralised Single Sign-On system.

Used by a lot of major organisations.

Uses XRDS documents.

The user obtains an OpenID with a provider. The user then interacts with a relying party (service provider). The Service provider may convert to a URI and request it.

The service provider has two ways in which they can communicate with the user:

1. `checkid_setup`
2. `checkid_immediate` for which the user is not directly involved.

Steps:

* Establish shared secret.
* ID provider authenticates user and asks if relying party is to recieve details.
    * If not user redirected to relying part unauthenticated.
* User is then redirected to the relying part authenticated.
* The relying party then validates using the shared secret.
* User is logged in.

### OpenID 2.0

URLs are under the users control.

XRI used for cross-domain digital IDs:

* `i-name` May be reassigned.
* `i-number` Is a UUID and cannot be reassigned.

OAuth
-----

IETF.

Uses cryptographic tokens instead of credentials, these tokens are issued for a specific site and time.

Twitter, Facebook, google and microsoft APIs are using OAuth.

OAuth is completely transparent to the user as they are asked if resorces on the server can be used by a client. A token is then provided from the server to the client.

THe user only ever needs to pass credentials to the server, not the client.

By default OAuth does not use SSL or TLS so the data is not confidential by default, however tokens expire quickly enough to prevent bad things™.

OAuth does not autherise the server or the client.

You should aim to use SSL/TLS with OAuth if you need a secure system.

Phising is common and there is no mechanism in place for scoping access.

Denial of service may be possible if an attack cna force a server to process many (fake) tokens quickly.

OAuth uses HMAC-SHA1 and RSA-SHA1 which are known to be weak.

XSRF vunerabilities.

Servers may want to automatically authenticate users.

