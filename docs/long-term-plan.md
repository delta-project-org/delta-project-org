The long-term plan
==================

Things that need to happen inside the Delta project to get the whole thing off the ground:

* Define the language, build a compiler.
* Write a standard library: integer arithmetic, strings, files.
* Make a good Foreign Function Interface (FFI) so we can call into existing libraries.
* Make the error messages useful to non-experts.
* Set up a library distribution infrastructure.

Things that the Delta project strives to enable, so they can happen inside or outside the project:

* More library writing.
* Drill down to the metal.
* Grow up to the user interface.


Define the language, build a compiler
-------------------------------------

Because no existing language can do what we want.  
Retrofitting an existing language could leverage existing code,
but the effect would be limited:

* Existing code does not come with extensive assertions, so these would have to be added.
* Experience has shown that being assertion-friendly influences API design,
limiting the ability to reuse existing code without a rewrite.
* The vast majority of languages has a far too complicated semantics to be amenable to validation.
* Language communities tend to shy back from outsiders trying to "improve" the language that they know and love.

We'll use LLVM as the compiler back-end.


Write basic libraries
---------------------

We need to write useful code in the language:

* Integer arithmetic.
* String handling.
* Containers: Arrays, lists, trees.
* File handling.
* Internet communication.

This will also be the testbed for the assertion checking system.


Foreign-function interface (FFI)
--------------------------------

Add a way to call functions written in other languages.

For most existing code, it will be easier to rewite it in Delta
than to add enough assertions to make it checkable.  
However, that rewritten code does not exist yet,
so we have to rely on external code as a stopgap measure.  
Some code cannot be rewritten at all, e.g. proprietary code.


Error messages
--------------

Straight-forward compile-time assertion checking
will only say what assertions could not be validated.

A programmer needs more, namely,
information about where his assumptions deviate from what the checker knows about the code.  
One way to provide that kind of information would be providing example inputs that lead to a violated assertion.

This is a field of ergonomy, and hence one of iterative improvement.


Library distribution infrastructure
-----------------------------------

A way to download code.  
The downlod needs to come with guarantees that it is what the requester wanted,
at the requested version, untampered.  
Also, the design should not have technical or organisational single points of failure.

Say, something similar to [Maven Central](http://search.maven.org/),
which is already good for all guarantees except the organisation itself is a point of failure
(Maven Central could be placed under legal pressure e.g. to manipulate specific critical libraries).


More libraries
--------------

Invite people to write libraries.

From regexes to image analysis,  
from data entry forms to game engines,  
from web page generation to webservices.  
And, of course, what the people themselves want to do.  

With the the distribution infrastructure up and running, people should find it easy to publish their results.
Assertions serve to reassure library consumers that the libraries are doing what they say.


Drill down to the metal
-----------------------

Replace FFI interfaces to the libc with Delta code.

Replace LLVM with our own backend.  
Or maybe port LLVM to Delta.  
Or write an LLVM-inspired backend.  
Whatever works.

Replace operating system services,
bridge the gap down to seL4, L4.verified, or whatever validated operating system kernel is available.

Possibly integrate seL4 into Delta.  
Or maybe port seL4 to Delta.  
Or write an seL4-inspired operating system kernel,
this time with validation as in-line assertions instead of as separate proof.  
Again: Whatever works.

If things are getting really wild,
this could extend down to the hardware descriptions that are used to make computer chips.


Grow up to the user interface
-----------------------------

End users need to see security domains that are meaningful to them.  
Less "this is signed by Foo Agency, trust us even if we didn't validate the software",
more "this software is going to see only files X, Y, and Z, nothing else - no files, no user data, no Internet."

This is another case where interaction with humans requires an iterative approach -
this time for end users instead of programmers.
