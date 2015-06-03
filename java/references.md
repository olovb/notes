
Reference Types
===============

There are 4 kinds of reference types:

* __class types__,
* __interface types__,
* __type variables__, and
* __array types__.

There's a special `null` literal that is valid as a value for any reference type and that *refers to no object*.

String literals are references to instances of the class `String`. 


Run-time Types
--------------

A class, represented by one single class declaration, may have been *loaded multiple times* by different class loaders and may thus be *considered multiple distinct types*. Two reference types are only considered the same __run-time type__ if they correspond to the same type declaration and are loaded by the same class loader. 

Array types are considered the same run-time type if their component types are considered to be the same run-time types.


Casting References
------------------

A `ClassCastException` will be thrown whenever an erroneous cast of a reference is attempted.

You can make a logical test as to the type of a particular object using the `instanceof` operator: `obj instanceof MyClass`.


