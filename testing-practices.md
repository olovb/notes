
Testing Practices
=================

> "If it isn't tested it's broken."

Two contrasting metods:

* Editing and developing without tests - Edit and Pray.
* Editing and developing with tests - Cover and Modify.

Have an easily usable and quick to use unit testing framework in place so new code can be tested without hassle. Time consuming test frameworks leads to untested code.

Unit tests helpful for both initial coding and changes of existing code. Use unit tests for atomic behavioral code units (units without side effects?).

Use unit tests to:

* Spot errors in small contexts (easier to localize error).
* Spot errors early and quickly (unit tests should be be run frequently during coding).
* Spot regressions when modifying and adding to existing code.
* Specify and document how code is intended to be used.

Good test coverage gives developers freedom to refactor code safely knowing they will be informed if they break something. Unit tests must provide quick feedback (no waiting for unnecessary long builds, etc.) to developers who can then test different approaches to problem solving and write code in small steps at a time (just implement units rather than having to complete complex applications before being able to test). Having a thorough set of test cases also reduces complexity of the separate testing stage (integration and system testing) in the later stages of the development cycle.

Writing code tests-first forces the developer to think about feature design and API design before writing code; writing code test-first puts focus on what you actually want and need which minimizes time spent on unnecessary trivialities and in blind-alleys. 

Writing tests first should assist the programmer in finding a productive workflow, since it encourages focus on small well defined and understood steps.

Before implementing unit tests it is necessary to break dependencies and to find seams in the code to be tested. Seams are places where behavior of code can be altered without the code actually being changed (which means same code in test and production environment). Seams can be used to introduce for example Fake Collaborators and Mock Objects, objects that replace real dependencies and instead can sense effects of tested code.

> "Test-first coding is not a testing technique", "Test-first code tends to be more cohesive and less coupled than code in which testing isn’t part of the intimate coding cycle" --Beck, 2001

When unit tests cannot be introduced in old code, new code can be added in separate functions (Sprout Methods). New code can be tested and is then integrated in old code by minimal adjustments -- adding function calls. Instead of functions, code can also be added in form of new classes (Sprout Classes). New classes are designed to mimic existing classes to ease later work to integrate code from new and old classes (usually necessary at some point later on to fight proliferation of classes).

Always separate object creation from application logic (dependency injection); making it easy to replace real collaborators with mock objects.
