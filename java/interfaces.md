
Interfaces
==========

An interface is a reference type described by an __interface declaration__.

There are __top-level interfaces__ and __nested interfaces__.

An interface is *implicitly abstract*. A member interface is *implicitly static*.

An interface that has no field or method is known as a __marker interface__. Examples are `Serializable` and `Cloneable`.

A generic interface declaration specifies the __type parameters__ after the type name:

    interface Foo<T1, T2, …, TN> { … }


Naming
------

An interface may not have the same name as any enclosing type.


Members
-------

An interface may contain

* __abstract methods__,
* __default methods__,
* __static methods__, and
* __constant fields__.

In an interface, only static and default methods may have block bodies.

A member of an interface is either __declared__, or __inherited__ from a direct superinterface. 

An interface member type is *implicitly public and static*. A member type of an interface may not be protected or private.

Note: Adding new abstract methods to an interface breaks all classes implementing the interface. This can be avoided by adding default methods rather than abstract methods. Adding default or static methods to an interface will not break binary compatibility.

If an interface has no superinterface, it implicitly declares public abstract methods corresponding to all public methods of the `Object` class unless such a method is declared explicitly. (An interface may not declare such a method with a conflicting return type or throws clause.)


Functional Interfaces
---------------------

A functional interface is an interface with *one abstract method* (not counting the methods that correspond to the `Object` class). (This method may be represented by several methods with override-equivalent signatures inherited from superinterfaces.)
