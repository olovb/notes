
Enums
=====

An enum represents *a set of predefined constants*. An __enum declaration__ defines an __enum type__, which is a special type of class that implicitly extends `java.lang.Enum`. (The direct superclass of an enum type `E` is `Enum<E>`.) Enums can contain methods and fields.


Enum Constants
--------------

The body of an enum declaration normally contains a list of __enum constants__, each defining an instance of the enum type. The only existing instances of an enum type are the constants declared in its enum constant list. 

An enum constant may *optionally have a class body*, in which case the body corresponds to an anonymous class that extends the enclosing enum type. Unless at least one enum constant has a class body the enum type is implicitly final.

An enum type has *one public static final field for each enum constant*, with the same name as the enum constant.


Instance Construction
---------------------

An enum constructor cannot be explicitly invoked (not even through reflective instantiation), and must be declared private. (In an enum declaration, a constructor declaration with no access modifiers is private.) Enum instances cannot be created by the `clone()` method nor can duplicate instances be created via deserialization.

Unlike regular class constructors, an enum constructor *may not contain a superclass constructor invokation*.

A *private default constructor is implicitly declared* if an enum has no explicitly declared constructors.

An enum *may not declare a finalizer* and enum instances may never be finalized.


Implicit Methods
----------------

An enum implicitly contains a static method `values()` that *returns an array of the enum's values* in the order they are declared.

    for (Planet p : Planet.values()) { … }

An enum implicitly contains a static method `valueOf(String name)` that returns the enum constant corresponding to a specific name.


Nested Enums
------------

A nested enum type is *implicitly static*. (I.e. it is impossible to declare an enum type in the body of an inner class.)


Equality
--------

Since only one instance of an enum constant exists, the operator `==` may be used instead of the `equals(…)` method.


