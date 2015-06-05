
Object-oriented Concepts
========================

> "An object may have identity, state and behavior." --Booch


Encapsulation and Information-hiding
------------------------------------

Encapsulation -- gathering all related data and functionality in one place as a component, often *in the form of a class*, more specifically, *bundling of data with the methods that operate on that data*. 

Encapsulation sometimes also means selectively restricting access to chosen properties and methods of an object, *hiding the object's internal representation* from outside view (or manipulation -- only the object's own methods can directly inspect or manipulate its own properties), although some prefer to call this __information-hiding__.

Information-hiding and encapsulation is said to *enhance program robustness* by *prohibiting users from using objects in inappropriate ways* such as setting an object's data to an inconsistent state.

Furthermore, information-hiding and encapsulation is a way to *isolate clients from implementation details and difficult design decisions* that might be subject to change.


Inheritance and Composition
---------------------------

Classes and inheritance are used to model __is-a__ relationships.

Combining objects into more complex objects is called __composition__. Objects that contain other objects model __has-a__ relationships.


Polymorphism and Dispatch
-------------------------

The general concept of *a specific set of functions applicable to a number of different types* is referred to as __polymorphism__.

There are several more specific types of polymorphism:

* __Ad-hoc polymorphism__ which means a function has implementations for several types, often supported in the form of *function overloading* or *operator overloading*.
* __Parametric polymorphism__ means that some code is implemented in terms of a type parameter, and is therefore *applicable to multiple types*.
* __Inclusion polymorphism__ (a.k.a. __subtyping__) where a number of classes *share the behaviour of a common supertype*.

Polymorphism can further be divided into 

* __run-time polymorphism__ (a.k.a. __dynamic polymorphism__) employing __dynamic dispatch__ and 
* __compile-time polymorphism__ (a.k.a. __static polymorphism__) employing __static dispatch__.

Note: Dynamic dispatch is not the same as dynamic binding (a.k.a. late binding).


Subtyping and Variance
----------------------

Variance tells us how the subtyping of more complex types relate to the subtyping of their components. The subtyping may in this sense be *preserved, reversed or ignored*.

For example if `D` is a subtype of `C`, and

* `Complex<D>` is a subtype of `Complex<C>` then `Complex<T>` is __covariant__ on `T`, 
* `Complex<C>` is a subtype of `Complex<D>` then `Complex<T>` is __contravariant__ on `T`, and
* neither `Complex<C>` nor `Complex<D>` is a subtype of the other then `Complex<T>` is __invariant__ on `T`. 

In a language that allows __covariant return types__, an overriding method may be declared/implemented to return a subtype of the overridden method's return type.

In a language that allows __contravariant method arguments__, an overriding method may be declared/implemented to accept a supertype of the corresponding argument type in the overridden method.


