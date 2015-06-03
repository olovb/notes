
Primitive Types
===============

The primitive types are the __numeric types__ and the `boolean` type.

Note: `boolean` is not a numeric type.

The numeric types are the __integral types__ and the __floating-point types__.

The integral types are

- the signed
  - `byte` (8-bit),
  - `short` (16-bit),
  - `int` (32-bit),
  - `long` (64-bit), and
- the unsigned `char` (16-bit).

The floating-point types are

- `float` (32-bit IEEE 754), and
- `double` (64-bit IEEE 754).


Integral types
--------------

The value ranges are for

- `byte`: -128 to 127 
- `short`: -32,768 to 32,767
- `int`: -2^31 to 2^31-1 = 2,147,483,647
- `long`: -2^63 to 2^63-1 = 9.223372e+18
- `char`: '\u0000' to '\uffff'

Integer literals represent `long` values if the have the `l` or `L` suffix, otherwise they represent an `int` value. Integer literals may be written in hexadecimal form having the prefix `0x` or in binary form having the prefix `0b`.

If an integer operation has at least one `long` operand, then the operation is performed using 64-bit precision and the result is of type `long` (the other operand is widened as necessary by numeric promotion). Otherwise the operation is performed using 32-bit precision and the result is of type `int` (operands are widened as necessary by numeric promotion). 

Integer operators don't indicate overflow.


Floating-point types
--------------------

IEEE 754 includes

* __positive and negative zero__ values,
* __positive and negative infinite__ values, and
* __not-a-number__ (NaN) values.

Floating-point literals represent `float` values if they carry the suffix `f` or `F`, otherwise they represent `double` values. A `double` literal may not be assigned to a `float` variable.

There is no literal for NaN, use `Float.NaN` or `Double.NaN`.

Except for NaN, all floating point values are ordered. Relational operators and `==` evaluate to `false` if either operand is NaN. The `!=` operator evaluates to `true` if either operand is NaN. If `x` is NaN then (and only then) `x != x` will evaluate to `true`.

The language supports serveral distinct NaN bit-patterns, however they are all treated as one *single canonical value*. 

Positive and negative zero compare equal.

The expression 
- `1.0 / -0.0` evaluates to negative infinity, and
- `1.0 / 0.0` to positive infinity.

If at least one of the operands of a binary operator is of a floating-point type, then the operation is a floating-point operation. 

If at least one of the operands of a numerical operation is of type `double` the operation will be performed with 64-bit floating-point arithmetic and the result will be of type `double` (the other operand is widened as required by numeric promotion). Otherwise the operation is performed  using 32-bit floating-point arithmetric.


Conversions
-----------

Integral values and floating-point values may be cast to or from any numeric type.

An integer of floating-point value can't be cast to a `boolean` but can be converted to a `boolean` using an expression like `x != 0`.

An object reference can be converted to a `boolean` using an expression like `o != null`.

A `boolean` can only be cast to 

- a `boolean`,
- a `Boolean`, or
- an `Object`.


