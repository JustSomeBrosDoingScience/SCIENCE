Vunerabilities
==============

This section of the course focuses on a lot of attacks that can happen on an internet based application and how to avoid common pitfalls.

Code Injections Attacks
-----------------------

At date of teaching, the biggest vunerabilites are:

1. SQL Injection
2. Operating System command injection
3. ???
4. Code Injection

SQL Injection
-------------

Involves inserting SQL statements into unsanitied inputs. Username/password combinations are a common target.

Most SQL injection involves inserting SQL meta-characters. Take the following example:

If the code is known to use the SQL statement:

```php
$stmt = "SELECT * FROM table WHERE id = '" + input + "';"
```

An attacker to insert the value:

```
' or 't'='t'
```

Which would always resolve to true and allow access to the system.

Obvious a clever attacker can then inject more complex SQL to access or modify the database.

The simplest solution is to avoid unsanatised input, however this is hard than it would seem. Java, for example, will nearly always interpret the string value `\u0027` as the single quote `'` character, which escaping the string cannot prevent.

Quite a few languages have built-in functions to handle this sort of operation.

Another thing to consider is data coming in from unexpected inputs. A form is just a POST request, so there is little point escaping the form data and not the POST data, for example.

A better approach still is not to allow direct input, prepared statements are a good example of this. However, it may not be possible to do such things.

Stored procedures could be used instead of raw SQL.

It might be interesting to see how well ORM frameworks deal with this sort of behaviour. I would personally assume well, but you never know :)

Cross-Site Scripting (XSS)
--------------------------

Just a foreword, these days cross-site scripting does not necessarily have to be from another site, or be a script. It is just the name for any coding attack.

The idea of a XSS is to inject malicious code into webpages. There are two ways of doing this:

* Reflective (non-persistent).
* Stored (persistent).

Reflective attacks are more common.

### Reflective Cross-Site Scripting

The basic premise of reflective XSS attacks is that HTML sent back to the server is not validated and is used as part of the response. For example, if a search engine uses the search string as verbatim, and is sent back to the client this can contain code with is then interpreted.

An example flow of this is that the user is tricked into vistining the scoundrel site. This sends a script back which is then sent on to the target as part of an echo. The target performs the echo with the results.

### Stored Cross-Site Scripting

With stored XSS the malicious code is stored on the server. For example messages containing HTML sent to a message board as a simple example. These scripts may be designed to self-propegate.

An example flow is as follows:

The Cracker interacts with the `/form` page and gains some form of access to the DB, adding a script which changes the `/admin` page.

A naive admin user then interacts with the `/admin` page, which forwards on details to the scoundrel site.

Methods for avoiding this is not to allow unsanitised input, have better security for cookies and disable scripts.

Cross-Site Request Forgery (XSRF)
---------------------------------

Cross-site Request Forgery exploits the trust user has for a site. It can be hidden innocously in something like an image which has a POST request associated with it.

Typically this involves including a link or script to which a user is authenticated. It also typically involves some form of HTTP request.

Users should ensure they are logged out of systems.

Sites should check the HTTP referrer header, limit the lifetime of cookies and session. A user-specific token can be added to all forms and URLs which have side-effects.
