Cryptopogy
==========

Reading List
------------

* Applied Cryptography - Schneier B.
* Practical Cryptography - Ferguson N.
* The Code Book - Singh S.

Problems
--------

* Confidentiality
* Data Integrity
* Non-Repudiation
* Identification and Authentication
* Authorisation

All can be solved through cryptography.

Encryption
----------

Typically the process is as follows:

The Plaintext is run through an Encryption algorithm, producing the ciphertext. Which can then be Decrypted to get the plaintext back.

Sometimes we only use the first half of this, one-way encryption, which is useful for things like passwords.

Encryption/Decryption is also known by a few other names:

* Enciphering and Deciphering.
* Encoding and Decoding.

There are very few good encryption and decryption algorithms as security depends on a parameter of a key. This process is as follows:

The plaintext is encryption with a key to produce the ciphertext, then decrypted with a key to retrive the plaintext.

If these keys are the same this is known as symetic key encryption. Otherwise it is known as asymetric key encryption, better known as public key encryption.

Symetric Key Encryption
-----------------------

Symetric key encryption tends to be less secure due to the nature of the keys being identical on either end. One of the first standards, DES, was a fixed length 56-bit key and is now completely insecure. DES had the advantage of being efficient due to hardware optimisation.

DES quickly became Triple DES, a varient which used three applications of DES with two inderpendant keys, reaching an effective length of 112-bits. The stratergy here was to encode with the first key then decode with another (?) then finally encrypt with the third and final key..

### Advanced Encryption Standard

Uses a block cipher which encrypts in blocks of 128, 192 or 256 bits. The key lengths are variable and inderpendant of block size.

Arranges blocks into rectangular matricies and performs 10-14 rounds of operation, which can be some of the following:

* Byte substitution.
* Shift row.
* Mix column.
* And round key.

Can be implemented very efficiently in harware and software.

* IDEA - Fixed length implemetation.
* RC2 and RC4 - Variable length implementation.
* Blowfish - Public domain, variable length implementation.

### Problems with keys

* Exactly the same key from encryption and decryption.
* Keys need to be changed regularly.
* Need to synchronised key changes.
* Ammounts to securly communication the key to communicate data securly.
* See Diffe-Hellman key exhange.

Public Key Encryption
---------------------

In public key encryption the keys are asymetric; a different key is used to decrypt the data from the one used to encrypt the data. This usually relies of some mathemtatical truths, a common public key algorithm might use the product of two prime numbers for the encryption key and the two prime numbers as the decryption key. This works as it is very difficult to factorise both prime numbers.

This has huge benefits; for a start knowing the encryption key does not mean you can decrypt the data. Due to this we can me the encryption key public, so long as we keep the decrpyion key private.

RSA uses the products of prime number. However there is a trade off, this is 100 times slower than DES in software, and 1000 times slower in hardware. Only recently has RSA been implemented in hardware.

There are other methods of public key cryptography:

* Discrete Lograithm Problem.
* Eliptic Curves Cryptosystems.

The intergrity of the private key is the weak link in Public Key encryption.

### Reverse Public Key Encryption

The nature of public key encryption means that you can also use the public key to decrypt ciphertext encrypted with the matching private key. This is more useful for signing requests and messages to verify that the author is who they say they are.

### Diffe-Hellman key exchange

Alice and Bob want to communicate securely. Alice gets the public key from Bob and combines it with her private key. Bob also combines his private key with the public key from Alice. This provides a symetrical key to easy encryption.

Confidentiality
---------------

Any reasonable encryption method can solve this.

Needs good key management:

* Diffe-Hellman key exchange.
* Symetric key encryption for all transmission.
* Public key encryption for all session and symetric key exchange.

Data Integrity
--------------

Simplest way is to include a hash of the original message.

Encryption using a private key means this hash is not easly faked.

All of this is known as a checksum.

Non-Repudiation
---------------

Sign all messages with a secure hash generated from the private key.

Recieved response returns the secure hash with their private key so they cannont deny receiving the message.

Digital Certificates
--------------------

How can we trust that a key?

A digital certificate binds an identity of an entity to their public key. There are several forms of digital certifications

* Personal - For a single person.
* Site - For a website or business.
* Code-signed - For APIs or Client programs.
* Authority - Identifies the Certificate Authority (CA).

To trust a certificate it is typically given as part of a chain from the least to most known organisation. This ends with a self-signed certification from the CA.

You can generate your own certificate, but it will not be recognised by a browser or client program automatically as it will not be signed by a trusted CA.

Secure Sockets Layer (SSL)
--------------------------

Protocol for secure transmission.

Sever and client handshake to agree on the type of technique used.

Bulk of the transmission is done using symetric key encryption for performance.

Transport Layer Security (TLS)
------------------------------

More modern version of SSL with backwards compatability. Main difference is the cipher suites used.

Pretty Good Privacy (PGP)
-------------------------

Developed for email, uses:

* RSA for key exchange
* RSA/DSS for digital signatures
* SHA-1 for integrity
* ZIP for compression
* CAST, TRiple DES, IDEA or Twofish for data encryption
* Rings of trust instead of chains
    * Theory is that you only trust those who you know.
    * Uses fingerprints.
    * Trust a new fingerprint if you have 3 people who know and trust that fingerprint.
    * Parallels to real life.

Pretty Enhanced Mail (PEM)
--------------------------

...

Secure Electronic Transaction (SET)
-----------------------------------

Three private/public keys:

* Customer
* Bank 
* Merchant

Customer details are kept secret from the merchant. Order details are kept secret from the bank.

Currently this is a slow technique and the structure is not in place for it to work. Could be more useful with the prevelance of mobile devices.

Kerebos
-------

Network authentication which uses a Key Distribution Centre (KDC) to store secret keys.

KDC sends Alice a key encrypted with her public key, which is decrypted to the key needed to autenticate on Bobs system

This is very complex when you get into the details of it and has the weakness of being a centralised system. There is a need to synchronise clocks across all systems to support key expiration.

Simple Authentication and Security Layer (SASL)
-----------------------------------------------

Used in LDAP.

SECURITY IS ALWAYS A COMPRIMISE
===============================
