
Execution
=========

The JVM starts execution by invoking the `main(…)` method of a specific class. The `main` method is passed zero or more arguments in the form of an array of `String`s. Typically the qualified class name is passed as a command line argument followed by any arguments then passed to the `main(…)` method.

Class Loading, Linking and Initialization
-----------------------------------------

Before any attempt to run the method of a class the class needs to be __loaded__. This is the process where a __class loader__ loads the binary representation of the needed class.

After a class has been loaded it is first __linked__ and then __initialized__.

Linking a class involves

* __verification__,
* __preparation__, and
* __resolution__.

Verification checks that a class is well-formed and obeys all semantic requirements of the language and the JVM. Preparation involves allocation of static storage and internal JVM data structures. Resolution involves loading all other classes referred to by the current class. (Any supertypes must also be loaded, linked and initialized recursively.)

Referred classes may be loaded eagerly or lazily, depending on the strategy of the Java implementation in use.


Class Instance Creation
-----------------------

A class instance may be explicitly created by an __instance creation expression__.

A class instance may be implicitly created when

- a class containing a `String` literal is loaded,
- a boxing conversion is executed,
- when a string concatenation occurs as a result of the `+` operator, or
- as a result of a method reference expression or a lambda expression.

Class instance creation involves

- memory allocation, 
- initialization of fields, and
- constructor execution.


Class Instance Finalization
---------------------------

Before the storage of an object is reclaimed by the garbage collector, the object is finalized by the JVM that calls the objects __finalizer__, i.e. the object's implementation of the `finalize()` method.

A __finalizable__ object is an object that has not yet had its finalizer invoked by the JVM, but may have its finalizer invoked at some point in the future.

An object may be 
* __reachable__, i.e reachable in the normal fashion by any live thread,
* __finalizer-reachable__, i.e. reachable from a finalizable object but not from a live thread, or
* __unreachable__.

The time when and in what order objects are finalized isn't specified. Neither is from what thread an object is finalized. (E.g. finalization of two objects may happen in any order or even concurrently.)

An object must always call `finalize()` for its superclass unless finalization logic of the superclass is to be nullified.

An exception thrown during finalization terminates the finalization but is otherwise ignored.

A finalizer may be explicitly invoked like any ordinary method.


Class Unloading
---------------

A Java implementation may unload any class except those loaded by the bootstrap loader.


Program Termination
-------------------

A program terminates when

- all non-daemon threads have terminated, or
- some thread invokes `exit(…)` from the `Runtime` or `System` class.


