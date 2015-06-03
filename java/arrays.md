
Arrays
======

An array holds zero or more variables, a.k.a. __components__. All the components of one array have the same type, the __component type__. The component may itself be an array.

A component that is not an array is an __element__. The type of an element is the __element type__ of the array. (If an array `A` holds arrays, that perhaps also hold arrays, ad infinitum, that holds elements of type `T`, then the element type of the original array `A` is also `T`.)

An array can be assigned to a variable of type `Object`, `Cloneable`, or `Serializable`. Hence, if the element type of an array is one of these then the element may also be an array.

An array has a __length__. (However, the length of an array is not part of its type.)


Creation and Initialization
---------------------------

An array is created by

* an __array create expression__, or
* an __array initializer__.


Access and Assignment
---------------------

An array component is accessed by an __array access expression__. Arrays must be indexed by `int` values. Array accesses are checked at run-time and will throw `ArrayIndexOutOfBoundsExpression` if an index is not within bounds.

Assignment to an array component is checked at run-time. An assignment will throw an `ArrayStoreException` if the value being assigned is not compatible with the component type.


Manipulations and Operations
----------------------------

An array has the following members:

- `public final length`,
- `public clone()`, and
- all other members inherited from `Object`.

All arrays of a specific component type shared an associated `Class` object.

Common array manipulations and operations such as copying, filling, sorting and comparisons are provided by the methods of the `java.util.Arrays` class. There is also the `System.arraycopy(…)` method.

