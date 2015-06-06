
Patterns
========

Immutable Objects
-----------------

The state of an immutable object never changes. 

Since they *cannot be corrupted by thread interference* and *do not have to be synchronized*, immutable objects are especially useful in multi-threaded programming.

* Don't let subclasses override methods. (Make the class final or make the constructor final and provide factory methods to create instances.)
* Make all fields private and final.
* Defensively copy referenced mutable objects stored within the immutable object, objects that are _passed to its constructors_ or that are _returned from its methods_.
* Provide no methods that can change the object state.


Singleton
---------

A singleton is a class that *has, at most, one single instance*.

### Conventional Approach

* Make the constructor private.
* Store the single instance in a private static volatile field.
* Provide a class method `getInstance()` that returns the singleton instance.

The `getInstance()` method may optionally use __lazy instantiation__, i.e. create the instance on the first call when it hasn't been created as part of the class initialization (e.g. in a class field initializer).


### Enum Approach

A *single element enum* is another way to create a singleton:

    public enum MySingleton {
        INSTANCE;
        … 
    }


