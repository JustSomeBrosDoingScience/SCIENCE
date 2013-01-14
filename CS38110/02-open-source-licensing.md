Free and Open Source Licensing
==============================

Q Public License (QPL)
----------------------

Designed for Qt.

Concerns raised about the limitations raised by the QPL, a lot of Qt was cross-licensed under the GPL instead.

* Permits distribution of modifications to covered software in the form of patches under less restrictive terms than modifications to the source code.
* Viral (all programs "Based on the software").
* Any software which relies on, or links to anything under the QPL must be governed by it's terms.
* Distribute unmodified versions of the software.
* May distribute modifications in the forms of patches only (separate to the original).
    * This has benefits to the original author and drawbacks to users and contributors.
    * Keeps integrity of original authors sound.
* Modifications must not alter or affect the copyright notices
* Must permit the original author a royalty-free license to the patch.
* Permission to distribute binary copies with license intact and access to source code.
* Can make modifications under another license, so long as they are also available under the QPL.
* May combine with any other software, including libraries.
* Restrictions on distribution of QPL'd software as part of linked software. While linked software does not need to be under the QPL, these restrictions require both the source code for the linked software to be made available and under a license that permits distribution and modification without fee.
* No provision for distribution as part of a larger work.
* Limitation of liability.
* Governed by the laws of Norway.


Artistic License
----------------

Intention to allow the original author to maintain "artistic" control over the licensed software. The Perl License is the same, with an added paragraph which provides an option for commercial distribution.

Rather vague and confusing. Fairly specific to Perl rather than being a general license like BSD or MIT.

* Original authors have control over the project whilst encouraging contributors within the project, and innovation outside.
* "Package" over "software", etc.
* "Standard Version" -> Unmodified version.
* Definitions of freely available.
* Distribution of source code of the standard version, as long as the license is distributed along with it.
* Permits users to update packages to include part of the standard version.
* Modifications from the public domain (vague)
* Modification of standard version with a changelog, given you do one of the following:
    * Public domain your modifications (make them freely available).
    * Use the modifications internally.
    * Technical modifications that will likely limit the compatibility of the modified code with the standard version.
    * Make a deal with the original author.
* Distribute, given you do one of the following:
    * Distribute the standard version with details of where to find the source.
    * Distribute with machine-readable version of the source.
    * Distribute any non-standard executables, clearly documenting them.
    * Make a deal with the original author.
* May charge a reasonable copying fee 
* Inputs/Outputs fall under the restrictions of the license
* Usage does not fall under the restrictions of the license
* No use of name without permission.
* Embedded with no attempt to provide a direct interface to the package can be distributed commercially.
* Typically liability disclaimer.


Proprietary Licenses
--------------------

* Unlikely to differentiate between source code and binary forms
* Unlikely to distinguish between original and derivative works with the exception of disallowing them.
* May contain open source elements (under permissive licenses). Own code is not open source (contained to those modules).
* Licensed, not sold, to the customer. This is pretty similar to open source and free licenses. However the only rights granted are those specifically defined in the license.
* Only licenses software rights other than those owned by the licensor (i.e. not in open source code included). This is unlikely to be needed, but is used to counter any IP claims on the Open Source. However due to it being closed-source there should be no way of proving this without breaking the license agreement.
* Strict limitations on the use of the software:
    * No distribution
    * Only one copy installed on one machine, this includes network usage.
    * Typically allowed one extra copy for backup purposes.
* Implicit statement barring derivative works.
* Disclaimer of liability: not designed for high-risk applications
* Bars any transfer or sale of the software, except for the exception mandated by law which permits the user to sell the rights included as part of the original software, along with the physical medium regardless of the terms under which the work was originally licensed. TL;DR - No rights the licensee didn't already have.
* Automatic termination upon breach of the license.
* Limited warranty for the medium on which the software is distributed upon.
* Disclaim all responsibility for damages beyond the legal minimum. (Maximum claim of ~$50).
* Export regulations.
* Notices of included open source software and licenses.

Any breach of the above terminates the license and renders the user liable for further damages.

Known as a "Shrinkwrap" license.

Can do things like license access to the source code, but disallow re-distribution for 5 years.

Proprietary Licenses are typically assume asymmetric bargaining power - the buyer is essential left with a take-it-or-leave-it position. Sometimes, more powerful negotiating positions can get extra benefits.


Sun Community Source License (SCSL)
-----------------------------------

A special type of license which are similar to open source licenses, but which do not conform to the Open Source definitions. These licenses tend to have extra clauses which offer some protection to the licensor (in this case Sun/Oracle) but are still designed to benefit from a bazaar-style development model. In the case of the SCSL users are free to modify the source code, but cannot distribute without compliance compatibility provided by the licensor. This does limit the open source model severely, but is designed to protect the cross-compatibility of Java.

* Community Code, Community member -> Strong focus on community over "you".
* Less free flowing than open source/free licenses to enforce testing, etc.
* "Official Version".
* Lots of BS about reference code and other stuff. 
