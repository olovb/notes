
Generics
========

Generics provide ways to

- use stronger compile-time type checks,
- avoid casts (e.g. from `Object`s stored in collections), and
- write generic code (e.g. for collections of different types).

A class or interface that is *parameterized over types* is a __generic type__, introduced by a __generic type declaration__.

A generic type is instantiatied by a __generic type invokation__, in which one or more __type arguments__ are passed to the generic type, yielding a __parameterized type__. *Any non-primitive type can be used as a type argument*.

In addition to generic types, static and non-static __generic methods__ are also allowed, as well as __generic class constructors__. 


Raw Types
---------

A generic class or interface without any type arguments is referred to as a __raw type__. (I.e. `List` is the raw type of the generic type `List<T>`.) Only generic types have corresponding raw types -- non-generic types are never raw types.

The compiler emits notes (or warnings with `-Xlint:unchecked`) when a value of a raw type is assigned to a variable of parameterized type.


Bounded Type Parameters
-----------------------

Type parameters may be restricted in the form of __bounded type parameters__. Bounded type parameters also allow you to invoke any methods corresponding to the bounds. 

An __upper bound__, e.g. `Number`: `<U extends Number>`, means *any class that extends or interface that implements* the given type. Multiple upper bounds are possible: `<T extends B1 & B2 & B3>` (a bound that is a class must be specified first).


Type Inference
--------------

Java can *determine some type arguments* by __type inference__. This is true for *generic method calls* (meaning the type witness can be omitted) and *invokations of generic types* with an empty type argument list, a.k.a. the __diamond operator__, `<>` whenever the type argument can be determined from the context.

    Klass<Integer> k = new Klass<>(…)  // Type inference with diamond operator.
    Klass<Integer> k = new Klass(…)  // Oops… unchecked warning.

To do its job, the type inference algorithm uses

- arguments,
- target types, and
- expected return types.

An expression's __target type__ is the expected type given the expression's location. The target type can be determined in

- variable declarations,
- assignments,
- `return` statements,
- array initializers,
- method and constructor arguments,
- lambda expression bodies,
- conditional expressions `?:`, and
- cast expressions.


Wildcards
---------

There is a __wildcard__, `?`, that *represents an unknown type*. When type parameters are related, *the wildcard can be used to create subtype relationships between generic classes*.

A wildcard can be used in the type of a 

- parameter, 
- field, 
- local variable, or 
- return type.

A wildcard may have *either an upper bound, a lower bound, or no bound*.


### Upper Bounded

An __upper bounded wildcard__, e.g. `<? extends Number>`, means *any class that extends or interface that implements* the given type `Number`.

A type with an upper bounded wildcard, e.g. `List<? extends Number>`, which accepts `List`s of `Number` and all types that extend `Number`, *is less restrictive* than a type without such a wildcard `List<Number>`.

An upper bound, e.g. `<? extends Number>`, used in a list variable type like `List<? extends Number>` would mean that the list elements can be accessed as type `Number`.

Example: `List<Integer>` is a subtype of `List<? extends Integer>` that is a subtype of `List<? extends Number>` that is a subtype of `List<?>`.

Upper bounded wild cards are mostly applicable to objects that hold or produce items meant as input to some algorithm.


### Unbounded

The __unbounded__ wildcard can be used to *specify an unknown type*, e.g. `List<?>` is a list of elements of unknown type. (Elements of unknown type can be treated as elements of the `Object` class.)

The unbounded wildcard is useful when writing code that does not depend on the element type or when the functionality of the `Object` class is sufficient.


### Lower Bounded

A __lower bounded wildcard__, e.g. `<? super Klass>`, restricts the type to be a *specific type or a super type of that type*.

Example: `List<Number>` is a subtype of `List<? super Number>` that is a subtype of `List<? super Integer>` that is a subtype of `List<?>`.

Lower bounded wild cards are mostly applicable to objects that will hold or consume items that are output of some algorithm.


### Limitations

Two variables with the same wildcard type must still be considered different types. E.g. an item from one `List<? extends Number>` cannot be added to another `List<? extends Number>` since they might refer to lists of distinct subtypes.

For the reason given above, wild cards are generally not applicable to objects that both produce and consume items.


Limitations
-----------

Generics are subject to the following limitations:

- Primitive types cannot be used as type arguments.
- Type parameters cannot be used to create instances with `new`. (Although the `newInstance()` method of `Class<T>` may be used as a workaround.)
- Type parameters cannot be used as the type of static fields.
- As a result of type erasure, `instanceof` cannot be used with parameterized types. Furthermore, it's only possible to cast to a parameterized type if it's parameterized by `?`.
- Arrays of parameterized types cannot be created.
- In method overloading, as a result of type erasure, parameterized types are viewed as their corresponding raw types.
- Throwable objects may not be generic.


