
Notes on Coding Practices
=========================

The Very Basics
---------------
Write S.O.L.I.D. code.

> "The problem […] is what I call ‘else-if-heimer's disease’" --Marshall Cline, C++ FAQ

Depend on abstract interfaces at compile time and inject the concrete dependencies at runtime.

Don't repeat yourself. Share modules and write generic algorithms. (Abstract classes, Templates). 

> "In programming, everything we do is a special case of something more general." --Alan J. Perlis

> "It is the user who should parameterize procedures, not their creators." --Alan J. Perlis

Give everything the narrowest scope possible. The idea is that it should be easy to verify that a variable or an object is used as intended. Ideally a reader of a piece of code should be able to see initialization and usage of a variable on screen without scrolling. 

By the same argument, minimize side-effects and reliance on global state.

Above points regarding scope and global state are especially important in a multithreaded context.

> "As long as you share anything and mutate something, you have the potential for deadlock. Immutable state is the key to solving the dilemma!" --unknown origin

Make code crash rather than trash (the users data).

Q: Is an Ostrich a Bird? A: Not if a Bird can `fly()`.


The Wheel
---------
Don't reinvent the wheel, even if it's not invented here.

> "In every sufficiently complex C program, there exists an ad-hoc, buggy, slow implementation of about half of C++." --Longstreet’s Tenth Law

Write as little code as possible. Do the simplest thing that works.

> "You don't have to maintain code you don't write" --Paul E Davis

Know your APIs, so you don’t have to implement code that already exists.

You write code once but maintain it forever.


Complexity
----------
> "Symmetry is a complexity-reducing concept [...]; seek it everywhere" --ACM's SIGPLAN publication, (September, 1982), Article "Epigrams in Programming", by Alan J. Perlis of Yale University

Minimize complexity. Distinguish between necessary and accidental complexity.

> "If the implementation is hard to explain, it’s a bad idea. If the implementation is easy to explain, it may be a good idea." --Zen of Python

Hide implementation and encapsulate necessary complexity. Make interfaces explain what, not how, so as to avoid premature commitment to strategy.

Distribute necessary complexity. Split solutions into 7±2 units. Each unit should have a clearly defined purpose and should be understandable on its own, in isolation from other units.

Replace expressions by references (or equivalent) if used in more than one place. An expression that evaluates to an object is inherently more subtle and prone to error than a direct reference to that object. Use of pointers or references can simplify code.

> "Using function pointers to encode complexity has some interesting properties. Some of the complexity is passed to the routine pointed to. The routine must obey some standard protocol - it's one of a set of routines invoked identically - but beyond that, what it does is its business alone. The complexity is distributed." --Rob Pike, 1989

> "[…] Postel's Law about being 'conservative in what you emit and liberal in what you accept' is quite frankly not a good engineering principle." --Joel Spolsky


Design and Intent
-----------------
A good computer system can't have a weak human language. Establish a ubiquitous language for the problem domain.

> "If every member of the team shares a mutually-agreed mental map of the system being constructed, then it is possible for everyones' contribution to be in the spirit of the overall design." --Programmers Stone

Make code intention revealing in respect to the problem domain; for example that data is being moved or iterated over and altered is probably not intention revealing.

Don't document merely the behavior of APIs but explain their rationale so that other developers quickly can grasp the underlying design goals. Have developers other than the ones implementing the code write or review the documentation to make it more understandable.


Clear and Clean
---------------
> "Leave the campground cleaner than you found it." --Boy scouts of America

Keep code clean. Clean code exhibits attention to detail, is focused, runs all the tests, contains no duplication, expresses the design ideas of the system and minimizes the number of classes and functions. Unclean code tempts programmers to stop caring. "A building with broken windows looks like nobody cares about it. So other people stop caring." 

A coding standard should insist on algorithmic clarity as opposed to syntactic clarity. 

Program close to the problem domain so as to make the code clearly show the logic. Error handling clutters code, favor exceptions. 

Exceptions should only be used for signaling errors, not changing the program flow. If it's a common case for a function to have no valid data to return, returning null, rather than throwing an exceptions, is good style.

Use built in (language) loop constructs. Let each loop work on one data structure only. Place work on additional data structures to co-routines or equivalent as not to clutter the loop. Let looping constructs match the data structure being worked on for clarity and correctness. 

There should be only one obvious way to accomplish a given task in a given situation within a systems API--the more options, the more incoherence and confusion. To make the one way obvious, policy and clear documentation will probably be needed.

Implementing a system using multiple languages may help achieving clear module interfaces and foster loose coupling.


Naming
------
Establish a clear naming convention. Consistent naming eases the cognitive burden.

> "Imagine you are on a roll. You've seen the way to divide up your functionality, you've got a really elegant way of catching all the odd ways the OS can signal failure, you're half way through coding up all the cases, and you need a new variable name. Your head locks up, overloaded by a triviality!" --Programmers Stone

> "Procedure names should reflect what they do; function names should reflect what they return. Functions are used in expressions, often in things like if's, so they need to read appropriately." --Rob Pike, pikestyle, 1989

> "[C]ould the same set of operations be meaningfully (emphasis added) applied to the quantities in questions? If so, the types are thought to be the same. If there are operations that apply to a quantity in exclusion of others, the type of the quantity is different." --Charles Simonyi

> "Look for coding conventions that make wrong code look wrong. Getting the right information collocated all together in the same place on screen in your code lets you see certain types of problems and fix them right away." --Joel Spolsky, Making wrong code look wrong

Make the names of identifiers reflect purpose and intent. Proper Hungarian Notation (Apps Hungarian) for example, reveals the purpose of variables - not the representation of variables. Apps Hungarian makes the process of variable and method naming easier.


Prototyping
-----------
Rewrite prototype code. The rewrite should be focused on code quality whereas the prototype should be focused on accomplishing results.


Testing
-------
Keep testing in mind—expose programmable interfaces to testing routines. Keep tests in sync with tested software. Tests removes fear of maintenace and refactoring. Extreme viewpoints: 1) never write code until you have a failing test; 2) never write any more code than is necessary to un-fail the test.

Keep unit testing in mind—make methods and classes easy to test thoroughly. Keep unit tests in sync with tested code. Unit testing is at least as much a design methodology as a testing methodology.

> "The anti-TDD people ought to realize that many of the pro-TDD people did many years of development before coming to TDD. It’s not like we just haven’t experienced the joys of cowboy coding and once we do we’ll drop unit-testing as unnecessary."

> "Modification of reused code is particularly error-prone. If more than 20 to 25 percent of a component is to be revised, it is more efficient and effective to rewrite it from scratch." --Facts and fallacies of software engineering, Robert L. Glass


Documentation
-------------
Make every effort to produce robust product and API documentation. Written. Face-to-face documentation is imprecise at best, guesswork at worst and a misuse of valuable time. High level design is particularly important to document since high level design is hard to see from looking at the implementations details. Documentation is good for developers even if they have taken part in the programming of the code, since the human memories are vague, particularly where low level details are concerned. 

Comments are for the why and not the how.

The "how do I interact with this" should go in the public code docs while the "how is this implemented" is better left relegated to code comments

Don’t forget to document error conditions of functions.


Distributed Programming
-----------------------
Local and remote resources should be handled in their own right.

> "Differences in latency, memory access, partial failure, and concurrency make merging of the computational models of local and distributed computing both unwise to attempt and unable to succeed." --Kendall, Waldo, Wollrath and Wyant, Note on Distributed Computing, 1994


Learning and Understanding
--------------------------
Make it easy for users to make small standalone applications when they are learning APIs. A good way to learn is to play around and test features in small contexts.

Let users install, configure and test software in their own environment, as opposed to using applications in shared testing environments, to be able to experiment freely and understand the system in full.

Make it easy for programmers to extend the application with debugging utilities. Furthermore, large amounts of application data and log files is better analyzed with proper tools (SQL queries, scripts) rather than using the applications standard interface or a simple text editor.


Summary
-------
> "[D]uct tape programmers – sacrificing tomorrow’s productivity, today!"

