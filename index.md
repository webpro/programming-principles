---
layout: index
type: project
title: Programming Principles
slug: programming-principles
---

# Programming Principles

Every programmer benefits from understanding programming principles and patterns. This overview is a reference for myself, and I've just put it here. Maybe it is of help to you during design, discussion, or review. Please note that it's far from complete, and that you often need to make trade-offs between conflicting principles.

The list was inspired by [The Principles of Good Programming](http://www.artima.com/weblogs/viewpost.jsp?thread=331531). I felt that the list closely, but not completely matches what I would personally put into something similar. Additionally, I wanted a bit more reasoning, details, and links to further resources. [Let me know](https://github.com/webpro/programming-principles/issues) if you have any feedback or suggestions for improvement.

## Contents

### Generic

* [KISS (Keep It Simple Stupid)](#kiss)
* [YAGNI](#yagni)
* [Do The Simplest Thing That Could Possibly Work](#do-the-simplest-thing-that-could-possibly-work)
* [Keep Things DRY](#keep-things-dry)
* [Code For The Maintainer](#code-for-the-maintainer)
* [Avoid Premature Optimization](#avoid-premature-optimization)
* [Boy-Scout Rule](#boy-scout-rule)

### Inter-Module/Class

* [Minimise Coupling](#minimise-coupling)
* [Law of Demeter](#law-of-demeter)
* [Composition Over Inheritance](#composition-over-inheritance)
* [Orthogonality](#orthogonality)

### Module/Class

* [Maximise Cohesion](#maximise-cohesion)
* [Liskov Substitution Principle](#liskov-substitution-principle)
* [Open/Closed Principle](#open-closed-principle)
* [Single Responsibility Principle](#single-responsibility-principle)
* [Hide Implementation Details](#hide-implementation-details)
* [Curly's Law](#curly-39-s-law)
* [Encapsulate What Changes](#encapsulate-what-changes)
* [Interface Segregation Principle](#interface-segregation-principle)

## KISS

Most systems work best if they are kept simple rather than made complex.

Why

* Less code takes less time to write, has less bugs, and is easier to modify.
* Simplicity is the ultimate sophistication.
* It seems that perfection is reached not when there is nothing left to add, but when there is nothing left to take away.

Resources

* [KISS principle](http://en.wikipedia.org/wiki/KISS_principle)
* [Keep It Simple Stupid (KISS)](http://principles-wiki.net/principles:keep_it_simple_stupid)

## YAGNI

YAGNI stands for "you aren't gonna need it": don't implement something until it is necessary.

Why

* Any work that's only used for a feature that's needed tomorrow, means losing effort from features that need to be done for the current iteration.
* It leads to code bloat; the software becomes larger and more complicated.

How

* Always implement things when you actually need them, never when you just foresee that you need them.

Resources

* [You Arent Gonna Need It](http://c2.com/xp/YouArentGonnaNeedIt.html)
* [You’re NOT gonna need it!](http://www.xprogramming.com/Practices/PracNotNeed.html)
* [You ain't gonna need it](http://en.wikipedia.org/wiki/You_ain't_gonna_need_it)

## Do The Simplest Thing That Could Possibly Work

Why

* Real progress against the real problem is maximized if we just work on what the problem really is.

How

* Ask yourself: "What is the simplest thing that could possibly work?"

Resources

* [Do The Simplest Thing That Could Possibly Work](http://c2.com/xp/DoTheSimplestThingThatCouldPossiblyWork.html)

## Keep things DRY

Every piece of knowledge must have a single, unambiguous, authoritative representation within a system.

Each significant piece of functionality in a program should be implemented in just one place in the source code. Where similar functions are carried out by distinct pieces of code, it is generally beneficial to combine them into one by abstracting out the varying parts.

Why

* Duplication (inadvertent or purposeful duplication) can lead to maintenance nightmares, poor factoring, and logical contradictions.
* A modification of any single element of a system does not require a change in other logically unrelated elements.
* Additionally, elements that are logically related all change predictably and uniformly, and are thus kept in sync.

How

* Put business rules, long expressions, if statements, math formulas, metadata, etc. in only one place.
* Identify the single, definitive source of every piece of knowledge used in your system, and then use that source to generate applicable instances of that knowledge (code, documentation, tests, etc).
* Apply the [Rule of three](http://en.wikipedia.org/wiki/Rule_of_three_(computer_programming)).

Resources

* [Dont Repeat Yourself](http://c2.com/cgi/wiki?DontRepeatYourself)
* [Don't repeat yourself](http://en.wikipedia.org/wiki/Don't_repeat_yourself)
* [Don't Repeat Yourself](http://programmer.97things.oreilly.com/wiki/index.php/Don't_Repeat_Yourself)

Related

* [Abstraction principle](http://en.wikipedia.org/wiki/Abstraction_principle_(computer_programming))
* [Once And Only Once](http://c2.com/cgi/wiki?OnceAndOnlyOnce) is a subset of DRY (also referred to as the goal of refactoring).
* [Single Source of Truth](http://en.wikipedia.org/wiki/Single_Source_of_Truth)
* A violation of DRY is [WET](http://thedailywtf.com/articles/The-WET-Cart) (Write Everything Twice)

## Code For The Maintainer

Why

* Maintenance is by far the most expensive phase of any project.

How

* *Be* the maintainer.
* Always code as if the person who ends up maintaining your code is a violent psychopath who knows where you live.
* Always code and comment in such a way that if someone a few notches junior picks up the code, they will take pleasure in reading and learning from it.
* [Don't make me think](http://www.sensible.com/dmmt.html).
* Use the [Principle of Least Astonishment](http://en.wikipedia.org/wiki/Principle_of_least_astonishment).

Resources

* [Code For The Maintainer](http://c2.com/cgi/wiki?CodeForTheMaintainer)
* [The Noble Art of Maintenance Programming](http://blog.codinghorror.com/the-noble-art-of-maintenance-programming/)

## Avoid Premature Optimization

Quoting [Donald Knuth](http://en.wikiquote.org/wiki/Donald_Knuth):

> Programmers waste enormous amounts of time thinking about, or worrying about, the speed of noncritical parts of their programs, and these attempts at efficiency actually have a strong negative impact when debugging and maintenance are considered. We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil. Yet we should not pass up our opportunities in that critical 3%.


Understanding what is and isn’t "premature" is critical of course.

Why

* It is unknown upfront where the bottlenecks will be.
* After optimization, it might be harder to read and thus maintain.

How

* [Make It Work Make It Right Make It Fast](http://c2.com/cgi/wiki?MakeItWorkMakeItRightMakeItFast)
* Don't optimize until you need to, and only after profiling you discover a bottleneck optimise that.

Resources

* [Program optimization](http://en.wikipedia.org/wiki/Program_optimization)
* [Premature Optimization](http://c2.com/cgi/wiki?PrematureOptimization)

## Minimise Coupling

Coupling between modules/components is their degree of mutual interdependence; lower coupling is better. In other words, coupling is the probability that code unit "B" will "break" after an unknown change to code unit "A".

Why

* A change in one module usually forces a ripple effect of changes in other modules.
* Assembly of modules might require more effort and/or time due to the increased inter-module dependency.
* A particular module might be harder to reuse and/or test because dependent modules must be included.
* Developers might be afraid to change code because they aren't sure what might be affected.

How

* Eliminate, minimise, and reduce complexity of necessary relationships.
* By hiding implementation details, coupling is reduced.
* Apply the [Law of Demeter](#law-of-demeter).

Resources

* [Coupling](http://en.wikipedia.org/wiki/Coupling_(computer_programming))
* [Coupling And Cohesion](http://c2.com/cgi/wiki?CouplingAndCohesion)

## Law of Demeter

Don't talk to strangers.

Why

* It usually tightens coupling
* It might reveal too much implementation details

How

A method of an object may only call methods of:

  1. The object itself.
  1. An argument of the method.
  1. Any object created within the method.
  1. Any direct properties/fields of the object.

Resources

* [Law of Demeter](http://en.wikipedia.org/wiki/Law_of_Demeter)
* [The Law of Demeter Is Not A Dot Counting Exercise](http://haacked.com/archive/2009/07/14/law-of-demeter-dot-counting.aspx/)

## Composition Over Inheritance

Why

* Less coupling between classes.
* Using inheritance, subclasses easily make assumptions, and break LSP.

How

* Test for LSP (substitutability) to decide when to inherit.
* Compose when there is a "has a" (or "uses a") relationship, inherit when "is a".

Resources

* [Favor Composition Over Inheritance](http://blogs.msdn.com/b/thalesc/archive/2012/09/05/favor-composition-over-inheritance.aspx)

## Orthogonality

> The basic idea of orthogonality is that things that are not related conceptually should not be related in the system.

Source: [Be Orthogonal](http://www.artima.com/intv/dry3.html)

> It is associated with simplicity; the more orthogonal the design, the fewer exceptions. This makes it easier to learn, read and write programs in a programming language. The meaning of an orthogonal feature is independent of context; the key parameters are symmetry and consistency.

Source: [Orthogonality](http://en.wikipedia.org/wiki/Orthogonality_(programming))

## Maximise Cohesion

Cohesion of a single module/component is the degree to which its responsibilities form a meaningful unit; higher cohesion is better.

Why

* Increased difficulty in understanding modules.
* Increased difficulty in maintaining a system, because logical changes in the domain affect multiple modules, and because changes in one module require changes in related modules.
* Increased difficulty in reusing a module because most applications won’t need the random set of operations provided by a module.

How

* Group related functionalities sharing a single responsibility (e.g. in a class).

Resources

* [Cohesion](http://en.wikipedia.org/wiki/Cohesion_(computer_science))
* [Coupling And Cohesion](http://c2.com/cgi/wiki?CouplingAndCohesion)

## Liskov Substitution Principle

The LSP is all about expected behavior of objects:

> Objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program.

Resources

* [Liskov substitution principle](http://en.wikipedia.org/wiki/Liskov_substitution_principle)
* [The Liskov Substitution Principle](http://freshbrewedcode.com/derekgreer/2011/12/31/solid-javascript-the-liskov-substitution-principle/)

## Open/Closed Principle

Software entities (e.g. classes) should be open for extension, but closed for modification. I.e. such an entity can allow its behavior to be modified without altering its source code.

Why

* Improve maintainability and stability by minimizing changes to existing code.

How

* Write classes that can be extended (as opposed to classes that can be modified).
* Expose only the moving parts that need to change, hide everything else.

Resources

* [Open Closed Principle](http://en.wikipedia.org/wiki/Open/closed_principle)
* [SOLID JavaScript: The Open/Closed Principle](http://freshbrewedcode.com/derekgreer/2011/12/19/solid-javascript-the-openclosed-principle/)

## Single Responsibility Principle

A class should never have more than one reason to change.

Long version: Every class should have a single responsibility, and that responsibility should be entirely encapsulated by the class. Responsibility can be defined as a reason to change, so a class or module should have one, and only one, reason to change.

Why

* Maintainability: changes should be necessary only in one module or class.

How

* Apply [Curly's Law](#Curly-s-Law).

Resources

* [Single responsibility principle](http://en.wikipedia.org/wiki/Single_responsibility_principle)

## Hide Implementation Details

A software module hides information (i.e. implementation details) by providing an interface, and not leak any unnecessary information.

Why

* When the implementation changes, the interface clients are using does not have to change.

How

* Minimize accessibility of classes and members.
* Don’t expose member data in public.
* Avoid putting private implementation details into a class’s interface.
* Decrease coupling to hide more implementation details.

Resources

* [Information hiding](http://en.wikipedia.org/wiki/Information_hiding)

## Curly's Law

Curly's Law is about choosing a single, clearly defined goal for any particular bit of code: Do One Thing.

* [Curly's Law: Do One Thing](http://blog.codinghorror.com/curlys-law-do-one-thing/)
* [The Rule of One or Curly’s Law](http://fortyplustwo.com/2008/09/06/the-rule-of-one-or-curlys-law/)

## Encapsulate What Changes

A good design identifies the hotspots that are most likely to change and encapsulates them behind an API. When an anticipated change then occurs, the modifications are kept local.

Why

* To minimize required modifications when a change occurs

How

* Encapsulate the concept that varies behind an API
* Possibly separate the varying concept into its own module

Resources

* [Encapsulate the Concept that Varies](http://principles-wiki.net/principles:encapsulate_the_concept_that_varies)
* [Encapsulate What Varies](http://blogs.msdn.com/b/steverowe/archive/2007/12/26/encapsulate-what-varies.aspx)
* [Information Hiding](https://en.wikipedia.org/wiki/Information_hiding)

## Interface Segregation Principle

Reduce fat interfaces into multiple smaller and more specific client specific interfaces. An interface should be more dependent on the code that calls it than the code that implements it. 

Why

* If a class implements methods that are not needed the caller needs to know about the method implementation of that class. For example if a class implements a method but simply throws then the caller will need to know that this method shouldn't actually be called.

How

* Avoid fat interfaces. Classes should never have to implement methods that violate the [Single responsibility principle](#single-responsibility-principle).

Resources

* [Interface segregation principle](https://en.wikipedia.org/wiki/Interface_segregation_principle)

## Boy-Scout Rule

The Boy Scouts of America have a simple rule that we can apply to our profession: "Leave the campground cleaner than you found it". The boy-scout rule states that we should always leave the code cleaner than we found it.

Why

* When making changes to an existing codebase the code quality tends to degrade, accumulating technical debt. Following the boyscout rule, we should mind the quality with each commit. Technical debt is resisted by continuous refactoring, no matter how small.

How

* With each commit make sure it does not degrade the codebase quality.
* Any time someone sees some code that isn't as clear as it should be, they should take the opportunity to fix it right there and then.

Resources

* [Opportunistic Refactoring](http://martinfowler.com/bliki/OpportunisticRefactoring.html)
