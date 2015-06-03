
Variables
=========

A variable is a storage location that, depending on its type, holds a __primitive value__ or a __reference value__.

A variable of a primitive type always holds a value of *that exact type*.

A variable of a class type can hold a reference to an instance of *the variable's class or any subclass thereof*. A variable of an interface type can hold a reference to an instance of *any class that implements said interface type*.

Formally there are 8 kinds of variables:

- class variables,
- instance variables,
- array components,
- method parameters,
- constructor parameters,
- lambda parameters,
- exception parameters, and
- local variables.
 
Class variables and instance variables are also refered to as a fields.

Unlike local variables, *fields and array components* not explicitly initialized *will be implicitly initialized to default values*. Local variables must be initialized sometime before their use.

A final variable not initalized at the point of declaration is known as __blank final variable__. Once a final variable has been assigned, it never changes its value (however the state of the object it references may change).

A value is changed by __assignment__ or as a result of the pre- and postfix operators (`++` and `--`).


Fields
------

Fields are introduced by __field declarations__.

A field may be __static__ (a.k.a. a __class variable__ -- a class member). If not, the field is __non-static__ (a.k.a. an __instance variable__ -- an instance member).

Note: Fields need not always be declared before they are used as long as they're in scope.


### Initialization

A _static_ field may be initialized

* in its declaration with a __field initializer__, or
* within a __static initializer__.

A _non-static_ field may be initialized 

* in its declaration with a __field initializer__,
* within an __instance initializer__, or
* in a constructor.

Note: Instance variables initializers may reference class variables even when such a class variable is declared textually after the initializer.


#### Constants

A constant of primitive type or of `String` type that has a value known at compile time is a __compile-time constant__, and the compiler replaces occurences of the field with its value during compilation. (This means dependent code needs to be recompiled if the value changes.)

Fields that are constant variables are initialized before other fields.


#### Interface fields

Fields of an interface must have a field initializer. (Such an initializer need not be a constant expression.) An interface field initializer must not refer to itself or any other field declared textually later.


### Modifiers

All fields of an interface are implicitly public, static and final.


