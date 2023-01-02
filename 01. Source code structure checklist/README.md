# Source code structure checklist

This is my checklist for a source code structure. Of course, there is no silver bullet and different 
domains/technologies/languages have their specific requirements and limitations. So, here is the language-agnostic 
and domain-agnostic set of questions I usually ask myself while assessing the existing code base 
and before creating a new one. I do not try to get all of those boxes checked altogether, but I should understand 
why any of them is unchecked and determine whether it is a “red flag” for the particular project.


## 1. Does the source code tell you “what does the service do” instead of “which framework or library it is based on”?

This will check how easy it is to open the code and quickly find a place for a new feature, make a bug fix or check 
how the particular part of the business logic works. 

We are used to read the code much more often than to write it. So we need to squeeze the maximum out of our 
programming language’s expressiveness. I’m talking not only about the proper names for variables, classes etc., 
but about the structure of files and directories as well. We often build our projects on top of a certain framework 
which imposes a structure to the entire project. Switching to the new framework often leads to re-writing the whole 
code base. Steve McConnell in his book [“Code Complete”](https://www.oreilly.com/library/view/code-complete-2nd/0735619670/) 
describes this effect as “writing in programming language” opposed to “writing with help of the programming language”. 
In that book, you may find a very profound explanation of how to write a program for people, not for computers.

Try to make the file tree self-explanatory, and try to extend generic terms, like `utils`, `models`, `validators`, and so on.
As for me, is better to see the `utils` directory with a single file per each helper-object instead of the single `utils` 
file with all helpers inside and with dozens of lines of code. I am also not a big fan of shortened entity names. 
I’d rather spend yet another microsecond reading a complex name and catching the concept, 
rather than reading a shortened but ambiguous one. 
All of those points sound obvious, but save hours of time in the long run.


## 2. Can you easily run the project or its test suite locally with a simple command?

This will check how easy it is to pick up the project by a team members (especially newcomers).

We usually do not want to spend an hour in order to find all possible startup options and distract our colleagues 
by asking corresponding questions. Some kind of command automation utility may help. 

I use good old [Makefile](https://en.wikipedia.org/wiki/Make_(software)#Makefile) where I keep all needed complex 
commands associated with shortcuts like: `image`, `deploy`, `bootstrap`, `test`, `clean`, etc. I also add a “help section” to it, 
which prints a brief explanation of all commands and a couple of examples so that any team member can just type `make 
help` in the command line and recall all details. It is much easier to run `make image test clean` or something like that 
instead of typing long docker or docker-compose related commands and try to remember commands specific to each project. 
I am also happy when the CI/CD config may run those Makefile commands. That helps to keep all possible ways to run 
and manage application in a single place.


## 3. Can you add support for the "--dry-run" flag without a significant redesign of the project itself and its tests?

This will check whether your business logic is tightly coupled with the database and external services.

By this “dry run” mode I mean the ability to run the service with isolated or mocked external dependencies.
We need this not only to perform manual testing and debugging but also to increase testability and extensibility 
of the project. This topic is described in details in the 
[“Architecture Patterns with Python”](https://www.oreilly.com/library/view/architecture-patterns-with/9781492052197/) 
book by Harry Percival and Bob Gregory. As written in the book - "patching out the dependency you’re using makes it 
possible to unit test the code, but it does nothing to improve the design. For that, you’ll need to introduce
abstractions". 

As for unit testing, there is two most popular approaches for testing external calls: 
London-school TDD using Mocks (patching the call in place) and the Classic Style using Fakes (Fakes are working implementations 
of the thing they’re replacing). Dynamic languages such as Python allow you to simplify the structure 
and just monkey-patch all needed calls. But, strictly speaking, mocking is a code smell and may lead to complicated tests.
My choice is - Mocks for small or short-term solutions and Fakes for the medium/big and long-lasting ones.


## 4. Can you add support for the new version of the API/Model without a significant redesign of the project itself and its tests?

This check is like the previous one but examines extensibility of the business logic-related parts of the application. 

Not the severe point, but it is better to think about the place for different versions of the same entities ahead 
of time and about how they may live together within the particular code base. 

In my personal experience, the initial version of the API or business logic entities seems the most proper one and stable, 
but the stable requirements are a myth. 
The task to add a new API version usually comes when the service is already deployed to the production and making 
such a change involves lots of steps with further refactoring. 
As proposed in the famous [tweet](https://twitter.com/kentbeck/status/250733358307500032): 
“Make the change easy (warning: this may be hard), then make the easy change.”


## 5. Can you add support for the new interface, e.g. CLI without a significant redesign of the project itself and its tests?

This will check whether your business logic is tightly coupled with the representation layer. 

If so, it would be much harder to add a new external interface or to build a healthy testing-pyramid. 
Loose coupling of the business logic with the representation layers (actual HTTP endpoints in case of a web application) 
helps us to simplify unit tests and to prepare to switching to another framework. That switch might look 
like an impossible case, but in my opinion, it is often almost impossible to painlessly switch to a better framework 
just because of the tightly coupled code. Not because we do not want to switch to the better framework. 
It is usually not just a major refactoring, it means rewriting the major portion of the code (and tests), 
which is not desirable at all. 

I’m going to suggest here any kind of approach based on the inversion of control. 
The [Hexagonal architecture](https://en.wikipedia.org/wiki/Hexagonal_architecture_(software)) or any of its [variants](https://en.wikipedia.org/wiki/Hexagonal_architecture_(software)#Variants) should work.
Such kind of code structure makes it easy to separate business logic from representation and persistence layers 
or to add new layers as the Web interface besides existing CLI Interface and vice versa. 
Although using such approaches for small or short-term solutions may be an overkill.


## 6. Are there any unused/unnecessary dependencies in the source code?

This will check whether the code base depends on things it doesn't use.

Although we mostly use open-sourced dependencies, the risk of having related security issues is still there. 
Also, each added dependency does not decrease the compile time/startup time/binary size (depending on the particular 
programming language) of the service. For the same reasons, it is better not to keep testing-related dependencies 
in a production image/binary. There are also cases when we add dependency on the whole package if we actually need 
one or two helper functions from it. 

In most cases, it is better to copy-paste those helper functions into your code 
base and get rid of the extra dependency.


## 7. Does the source code have a “gentleman set” of root-level helper files?

This will check, I'd say, the general "maturity" of the repository. 

There is a set of commonly used files, which doesn't influence the functionality itself but helps us to 
maintain the codebase in a unified manner.
Such files are: `.gitignore`, `.dockerignore`, `.editorconfig`, `CHANGELOG.md`, `CONTRIBUTING.md`, explicit configs 
for static code analyzers? And by the way... the actual version of the `Readme` file. No joke. 
Let’s end the practice when the main contributors to the readme file are newcomers, who found that steps described 
in the `Readme` file do not work anymore...



## Afterword

**Note that I deliberately skipped any checks for unit-tests as they deserve a separate checklist.**

One of the main goals of such a strict inspection is to increase the readability and maintainability of the project. 
This is extremely important for long-lasting projects. In most cases, we shouldn’t bother a lot about how easy it will 
be for a processor to parse our code base and create a nice abstract syntax tree from it. But we should bother about 
how much time it will take for a newcomer/your colleague/yourself to find the right place for a new feature or a bug fix. 
Let’s be honest, human beings are not so good at keeping a lot of objects and abstractions in memory simultaneously. 
We shouldn’t neglect our natural peculiarities and help ourselves in any ways possible.

## Bibliography

[McConnell, Steve. 2004. Code Complete, 2nd Edition](https://www.oreilly.com/library/view/code-complete-2nd/0735619670/) 

[Percival, Harry and Gregory, Bob. 2020. Architecture Patterns with Python](https://www.oreilly.com/library/view/architecture-patterns-with/9781492052197/)

