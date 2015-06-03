
Overview
========

Java is a general-purpose, object-oriented programming language. The project that later became Java was first initiated in 1991, and released to the public as Java 1.0 in 1995.

Some of the principles that guided the creation of the languange are:

- simple and familiar,
- robust and secure,
- architechture neutral and portable,
- high performance.

Java is compiled to bytecode that is executed in a virtual machine, the JVM. The JVM, together with the API, comprises the __Java platform__.


Types
-----

At compile time every variable and every expression has a known type. The types limit what values an expression can produce and the operations on those values. (The language is __statically typed__ and __strongly typed__.)

There are two kinds of values: __primitive values__ and __reference values__.

There are two kinds of types: __primitive types__ and __reference types__.


Statements and Blocks
---------------------

A statement forms a complete unit of execution. 

The following types of expressions can be made into a statement, an __expression statement__, by terminating the expression with a semicolon:

- assignment expressions,
- any use of pre- or postfix operators `++` and `--`,
- method invocations, and
- object creation expressions.

There are two other kinds of statements: __declaration statements__ and __control flow statements__.

A __block__ is a group of zero or more statements between balanced braces. Blocks may be used anywhere a single statement is allowed.


Operators
---------

The operators have the following precedence:

- Postfix: `expr++` and `expr--`.
- Unary: `++expr`, `--expr`, `+expr`, `-expr`, `~`, and `!`.
- Multiplicative: `*`, `/`, and `%`.
- Additive: `+` and `-`.
- Shift: `<<`, `>>`, and `>>>`.
- Relational: `<`, `>`, `<=`, `>=`, and `instanceof`.
- Equality: `==` and `!=`.
- Bitwise AND: `&`.
- Bitwise exclusive OR: `^`.
- Bitwise inclusive OR: `|`.
- Logical AND: `&&`.
- Logical OR: `||`.
- Ternary: `? :`.
- Assignment: `=`, `+=`, `-=`, `*=`, `/=`, `%=`, `&=`, `^=`, `|=`, `<<=`, `>>=`, and `>>>=`.


Literals
--------

Special escape sequences for `char` and `String` literals: 

- `\b` (backspace), 
- `\t` (tab), 
- `\n` (line feed), 
- `\f` (form feed), 
- `\r` (carriage return), 
- `\"` (double quote), 
- `\'` (single quote), and 
- `\\` (backslash).


