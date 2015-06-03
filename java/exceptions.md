
Exceptions
==========

An exception is an object of a subclass to the class `Throwable`. 

When an exception is thrown, the normal flow of the program's instructions is disrupted, i.e. the execution of any begun but not yet completed

- expression,
- statement,
- method, 
- constructor,
- initializer, or
- field initializer

in the current thread is abruptly completed until a suitable __exception handler__ is encountered somewhere on the call stack. (If no such handler is found one of the __uncaught exception handlers__ may be executed.)


Kinds of Exceptions
-------------------

Exception hierarchy:

    Throwable
     +- Exception
     |   +- RuntimeException
     +- Error

There are __checked exceptions__ and __unchecked exceptions__.

Checked exceptions are exceptions that an application is *expected to recover from*. Checked exceptions are those exceptions derived from the `Throwable` class except those derived from the `RuntimeException` or `Error` classes.

Checked exceptions are subject to __catch-or-specify__.

Unchecked exceptions are further subdivided into __run-time exceptions__ and __errors__.

Run-time exceptions are exceptions that an application *might be able to recover from*. Errors are exceptions that an application is *unlikely to be able to recover from*.


Causes of Exceptions
--------------------

An exception may be thrown for one of three reasons:

- a `throw` statement is executed,
- an abnormal condition was *synchronously* detected, or
- an *asynchronous* exception occurred. 

Abnormal conditions that lead to synchronous exceptions to be thrown might be

- expressions that violate some contraint such as division by zero,
- errors on loading, linking or initializing a class,
- internal JVM problems, such as resource limitations.

Asynchronous exceptions might be thrown in a thread in response to some action such as

- an invokation of the deprecated `stop()` method from `Thread` or `ThreadGroup`, or
- internal JVM problems, such as resource limitations.


Exception Handling
------------------

A thrown exception is __caught__ by the nearest __dynamically enclosing__ `catch` clause that is able to handle the exception.

A single `catch` block can handle multiple exception types. In such a block the exception parameter is implicitly final.

A `finally` block is always executed after the `try` and (optionally) `catch` clause, even if a `return` statement within one of those blocks is executed. (However a `finally` may not execute if the JVM exits, such as on an `System.exit(…)` call or if the executing thread is killed.)


### Try-with-resources

The `close()` methods of resources are *called in the opposite order of their creation* inside a __try-with-resources__ statement. Any `catch` or `finally` block is *run after the resources have been closed*. 

Any object that implements `java.lang.AutoCloseable`, which includes all objects which implement `java.io.Closeable`, can be used as a resource in a try-with-resources statement.


### Supressed exceptions

If exceptions are thrown in both the `try` and `finally` blocks, the exception thrown from the `try` block is suppressed.

If an exception is thrown from the `try` block and one or more exceptions are thrown from the try-with-resources statement, then those exceptions thrown from the try-with-resources statement are suppressed.

You can retrieve suppressed exceptions by calling the `getSuppressed(…)` method of the `Throwable` class.


### Uncaught exceptions

If no `catch` clause is able to handle the exception, the current thread is terminated. (All `finally` clauses are excecuted before such a termination.) Any uncaught exception handler for the thread is executed, and if none exists `uncaughtException()` is invoked for the current `ThreadGroup`.


Chained Exceptions
------------------

An application often responds to an exception by throwing another exception, a concept called __exception chaining__. The following are the methods and constructors in `Throwable` that support chained exceptions:

- `Throwable getCause()`,
- `Throwable initCause(Throwable)`,
- `Throwable(String, Throwable)`, and
- `Throwable(Throwable)`.


Stack Traces
------------

Use the `getStackTrace()` method on exceptions to get an array of `StackTraceElement`.


Creating Exception Classes
--------------------------

You should only write your own exception classes if you answer yes to any of the following questions:

- The exception type needed isn't already represented by an existing class?
- Will your users need to differentiate your exceptions from other exceptions by type, e.g. in `catch` clauses?
- Do you need a family of related classes to distinguish different errors?


