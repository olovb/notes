
Methods
=======

A method is introduced by a __method declaration__. A method can be __static__ (a.k.a. a class method) or __non-static__ (a.k.a. an instance method). 

A method has a __type__, which is a combination of 

- the methods argument types, 
- the return type, 
- the `throws` clause, and 
- any type parameters.

A method has a __signature__, which is its 

- name and 
- formal parameter list.

Normally, only final methods should be called from constructors. (If a constructor calls a non-final method, a subclass may redefine that method with surprising or undesirable results.)

Type parameters for generic methods are put before the method's return type:

    static <K, V> Type methodx(…) { … }
    public <K, V> Type methody(…) { … }

In a generic method call, the type argument may optionally be specified with a __type witness__ before the name of the method.

    Klass.<Type>method(…)


In Interfaces
-------------

An interface method is *implicitly public*.

Interfaces may have __default methods__. (These are distinct from the concrete methods of classes.) Such a method provides a *default implementation* for classes that implement the interface.

A default method must not have a signature that is override-equivalent with a non-private method of the `Object` class.

An interface method that is not a default method is *implicitly abstract*.


Returning from methods
----------------------

A method returns to the call site when it:

- completes all the statements in the method,
- reaches a `return` statement, or
- throws an exception,

whichever happens first. 

A method with a return type other than void may legally omit a return statement if for example its execution always terminates with a throw statement.
