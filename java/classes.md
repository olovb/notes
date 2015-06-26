
Classes
=======

A class is a reference type described by a __class declaration__.

A class contains:

- zero or more __members__, 
- one or more __constructors__ and 
- optionally __static__ or __instance initializers__.

There are __top-level classes__ and __nested classes__.

There are 2 types of nested classes: __inner classes__ and __static nested classes__.

There are 3 types of inner classes: 

* __non-static member classes__, 
* __local classes__ and 
* __anonymous classes__.

A class may be incomplete, i.e. leaving some parts undeclared, in which case the class is called an __abstract class__.

A generic class declaration specifies the __type parameters__ after the type name:

    class Klass<T1, T2, …, TN> { … }


Naming
------

A class may not have the same name as any enclosing type.


Members
-------

There are 4 types of class members: 

* __fields__, 
* __methods__, 
* __classes__ and 
* __interfaces__. 

A member is either a __class member__ or an __instance member__.

A class member is __inherited__ (from the direct superclass or the direct superinterface) or __declared__ in the class body.


### Inner Classes

An inner class is a nested class that is not static.

Inner classes *can't declare static initializers or static members* (but may inherit static members).

Inner classes may *refer to instance members of enclosing class* (static nested classes may not). Local variables and formal or exception parameters used by but not declared by an inner class *must be final or effectively final*. Such local variables must also be definitely assigned before the body of the inner class.


Constructors
------------

A class has one or more constructors. A class has an implicit no-argument constructor, __default constructor__, if no constructors are declared. Such a default constructor has the same accessibility as the class.

A constructor is not a member -- constructors are never inherited.

Constructor may be invoked

- by instance creation expressions,
- as a result of the string concatenation operator `+`, and
- by explicit constructor invokation.

An inner class implicitly declares as its first parameter, a variable representing the enclosing class instance.

A constructor may have a `throws` clause just like a method.

The __type__ of a constructor is its signature in combination with the `throws` clause.

The first line of a constructor may be an __explicit constructor invokation__, i.e. an invocation of the form `this(…)` of another constructor of the class, or an invokation of the form `super(…)` of a direct superclass constructor. Unless a constructor begins with an explicit constructor invokation, the constructor implicitly begins with `super()`.

It is legal to use `return` statements in constructors as long as they don't include expressions.

Type parameters for generic constructors are put before the constructor's name:

    <K, V> Klass(…) { … }  // Klass' constructor.


Initializers
------------

A class may contain static or instance initializers.

Initializers are guaranteed to be called in the order that they appear in the source code.

Instance initializers are copied into each constructor.



