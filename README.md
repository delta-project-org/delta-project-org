# main

This is the Delta Project, aiming to improve software reliability.

We do this through assertions, verified by the compiler or at runtime.  
Assertions can be stated about all kinds of interesting behaviour:

* Sequencing of actions: files cannot be read before opened;
* validity of results, such as stating that the result of the sqrt function, when squared, must give the original value within accuracy bounds;
* absence of certain classes of errors such as buffer overflows, null pointer dereferences, or invalid type casts;
* limits on memory or CPU usage.
