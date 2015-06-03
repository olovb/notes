
Inheritance
===========

Classes may __extend__ other classes and __implement__ interfaces, thereby *inheriting methods, fields and member types*. Furthermore, interfaces may extend other interfaces.

Instead of being inherited, members from supertypes may be 

* __hidden__ (fields, member types and class methods), or
* __overridden__ (instance methods).

An inherited method may also be overloaded which neither hides or overrides the original method.

When extending an interface, a default method may be

* __inherited__ as-is,
* __redefined__ thus overriding it with a new default method, or
* __redeclared__ as abstract.

Note: Constructors, static and instance initializers are not members and are not inherited. Static methods of interfaces are also not inherited.

Package private members are only inherited by classes declared in the same package.


Name Clashes
------------

### Fields

Multiple fields or multiple member types with the same name can be inherited (but any of these obviously cannot be referred to by its simple name).

Even though a field or member type might be inherited from an interface through several paths, said member is considered to be inherited only once (and may be refered to by its simple name).


### Methods

When supertypes provide multiple methods having override-equivalent signatures,

- concrete methods are preferred over default methods, and
- methods that are already overridden by other candidates are ignored.

When inheriting from multiple interfaces, *two or more conflicting default methods* (i.e. override-equivalent but having independent implementations -- a behavioral conflict), or *a default method and a conflicting abstract method* (i.e. override-equivalent) cannot be inherited. In this case the inheriting type must

- also inherit an override-equivalent method (concrete or abstract) from a base class, or
- declare its own override-equivalent method (default, concrete or abstract).


Overriding
----------

The access modifier for an overriding method can allow more (but of course not less) access than the overridden method.

An instance method may not override a static method.

An overridden method can be invoked using `super`, but not by casting.

An overriding method may differ in fp-strictness from the overridden method.

An overriding method may __refine the return type__ of the overridden method allowing __covariant return types__.

An overriding method must not be declared to throw more checked exceptions than the overridden method. 


Hiding
------

### Fields 

A field that hides another may be of a different type than the hidden field.

An non-static field may hide a static field and vice versa. 

A hidden field can be accessed using `super`. Furthermore,
* a hidden static field can be accessed using its qualified name and 
* a hidden non-static field can be accessed by casting to a superclass type.

Note: Hiding is distinct from shadowing. Hiding applies only to members. Within a method body, method parameters shadow fields with the same name.


### Methods

A static method may not hide an instance method.

A hidden static method may be accessed by

- using `super`, 
- casting to the relevant supertype, or
- using the qualified name. 

A method that hides another 

- must not be declared to throw more checked exceptions than the hidden method, and
- must be __return-type-substitutable__.


### Types

A member type hides any member type in a superclass or superinterface with the same name.


