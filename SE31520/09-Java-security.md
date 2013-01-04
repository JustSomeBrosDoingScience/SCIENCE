Java Security
=============

**Note:** This may only be for Oracles JDK and the OpenJDK

Java has been built with security in mind. THe VM itself contains the security, not the underlying system.

Byte code can be verified for JVM code conformance.

`java.lang.SecurityManager` can be registered through `System.setSecurityManager(...)`, but is typically done at the command line.

`java.lang.ClassLoader` establishes trust between system classes and untrusted, imported classes. Java has the idea of a sandbox in which untrusted code can be run in a protected area (side note: how does this affect OSGi?).

Java security is theoretically sound, but there are still some programatic bugs.

Security Policy
---------------

Security policies are typically done via configuration files.

`java.security.Policy` is the security policy.

`java.security.CodeSource` is the idenity of a class, defined in terms of the classes codebase and signature.

A security policy is defined by a map of identities to policies.

THe runtime argument `-Djava.security.manager` sets the default security manager, and `-Djava.security.policy=/path/java.policy` sets the policy.

Permissions
-----------

All from `java.security.Permission`. Certain permissions imply other permissions. For example, allowing read on `/tmp/*` implies all files in `/tmp` are readable.

Something to consider with custom permissions:

```
grant [signedBy "$"][codeBase "$"] {
    permission <PermissionClass> ??? (damn my illegible handwriting)
}
```


