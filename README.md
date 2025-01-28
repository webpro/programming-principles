# Programming Principles

Every programmer benefits from understanding programming principles and design
patterns. This overview is a reference for myself, and maybe it is of help to
you during design, discussion, or review. The list is incomplete, and sometimes
trade-offs need to be made between conflicting principles. However, higher
ranked principles usually beat lower ranked ones.

The list was inspired by [The Principles of Good Programming][1]. I've added a
bit more reasoning, details, and links to further resources. [Let me know][2] if
you have any feedback or suggestions for improvement!

## Contents

### Generic

- [KISS][3]
- [YAGNI][4]
- [Do The Simplest Thing That Could Possibly Work][5]
- [Separation of Concerns][6]
- [Code For The Maintainer][7]
- [Avoid Premature Optimization][8]
- [Optimize for Deletion][9]
- [Keep things DRY][10]
- [Boy Scout Rule][11]

### Relationships between modules, classes, components, entities

- [Connascence][12]
- [Minimise Coupling][13]
- [Law of Demeter][14]
- [Composition Over Inheritance][15]
- [Orthogonality][16]
- [Robustness Principle][17]
- [Inversion of Control][18]

### Modules, classes, components, entities

- [Maximise Cohesion][19]
- [Liskov Substitution Principle][20]
- [Open/Closed Principle][21]
- [Single Responsibility Principle][22]
- [Hide Implementation Details][23]
- [Curly's Law][24]
- [Encapsulate What Changes][25]
- [Interface Segregation Principle][26]
- [Command Query Separation][27]
- [Dependency Inversion Principle][28]
- [SOLID][29]

### Test

- [FIRST principles of testing][30]
- [Arrange, Act, Assert][31]

## KISS

**Keep It Simple, Stupid**: most systems work and are understood better if they
are kept simple rather than made complex.

Why

- Less code takes less time to write, has less bugs, and is easier to modify.
- Simplicity is the ultimate sophistication.
- It seems that perfection is reached not when there is nothing left to add, but
  when there is nothing left to take away.

Resources

- [KISS principle (wikipedia.org)][32]
- [Keep It Simple Stupid (KISS) (principles-wiki.net)][33]
- [Cognitive Load is what matters (github.com)][34]
- [The Limits of Human Cognitive Capacities in Programming and Their Impact on
  Code Readability (florian-kraemer.net)][35]
- [Simplicity is An Advantage but Sadly Complexity Sells Better
  (eugeneyan.com)][36]

## YAGNI

**You Aren't Gonna Need It**: don't implement something until it is necessary.

Why

- Any work that's only used for a feature that's needed tomorrow, means losing
  effort from features that need to be done for the current iteration.
- It leads to code bloat; the software becomes larger and more complicated.

How

- Always implement things when you actually need them, never when you just
  foresee that you need them.

Resources

- [You Arent Gonna Need It (wiki.c2.com)][37]
- [You’re NOT gonna need it! (ronjeffries.com)][38]
- [You aren't gonna need it (wikipedia.org)][39]

## Do The Simplest Thing That Could Possibly Work

Why

- Real progress against the real problem is maximized if we just work on what
  the problem really is.

How

- Ask yourself: "What is the simplest thing that could possibly work?"

Resources

- [Do The Simplest Thing That Could Possibly Work (wiki.c2.com)][40]

## Separation of Concerns

Separation of concerns is a design principle for separating a computer program
into distinct sections, such that each section addresses a separate concern. For
example, the business logic and the user interface of an application are
separate concerns. Changing the user interface should not require changes to the
business logic and vice versa.

Quoting [Edsger W. Dijkstra][41] (1974):

> It is what I sometimes have called "the separation of concerns", which, even
> if not perfectly possible, is yet the only available technique for effective
> ordering of one's thoughts, that I know of. This is what I mean by "focusing
> one's attention upon some aspect": it does not mean ignoring the other
> aspects, it is just doing justice to the fact that from this aspect's point of
> view, the other is irrelevant.

Why

- Simplify development and maintenance of software applications.
- When concerns are well-separated, individual sections can be reused, as well
  as developed and updated independently.

How

- Break program functionality into separate modules that overlap as little as
  possible.

Resources

- [Separation of Concerns (wikipedia.org)][42]

## Code For The Maintainer

Why

- Maintenance is by far the most expensive phase of any project.

How

- _Be_ the maintainer.
- Always code as if the person who ends up maintaining your code is a violent
  psychopath who knows where you live.
- Always code and comment in such a way that if someone a few notches junior
  picks up the code, they will take pleasure in reading and learning from it.
- [Don't make me think][43].
- Use the [Principle of Least Astonishment][44].

Resources

- [Code For The Maintainer (wiki.c2.com)][45]
- [The Noble Art of Maintenance Programming (blog.codinghorror.com)][46]

## Avoid Premature Optimization

Quoting [Donald Knuth][47]:

> Programmers waste enormous amounts of time thinking about, or worrying about,
> the speed of non-critical parts of their programs, and these attempts at
> efficiency actually have a strong negative impact when debugging and
> maintenance are considered. We should forget about small efficiencies, say
> about 97% of the time: premature optimization is the root of all evil. Yet we
> should not pass up our opportunities in that critical 3%.

Understanding what is and isn’t "premature" is critical.

Why

- It is unknown upfront where the bottlenecks will be.
- After optimization, it might be harder to read and thus maintain.

How

- [Make It Work Make It Right Make It Fast (wiki.c2.com)][48]
- Don't optimize until you need to, and only after profiling you discover a
  bottleneck to optimise.

Resources

- [Program optimization (wikipedia.org)][49]
- [Premature Optimization (wiki.c2.com)][50]

## Optimize for Deletion

Why

Code should be optimized for change. Code that's easy to delete is easy to
replace or change.

How

Don't try to predict future changes today, instead focus on deletable and
rewriteable code.

Principles such as [separation of concerns][6], [low coupling][13] and the
[Single Responsibility Principle][22] result in increased deletability. In
general, high modularity helps to increase deletability of individual parts.

Resources

- [The art of destroying software (youtube.com)][51]
- [Optimize for Deletion (work.stevegrossi.com)][52]
- [Deletability (kellysutton.com)][53]
- [Write code that is easy to delete, not easy to extend.][54]

## Keep things DRY

**Don't Repeat Yourself**: Every piece of knowledge must have a single,
unambiguous, authoritative representation within a system.

Each significant piece of functionality in a program should be implemented in
just one place in the source code. Where similar functions are carried out by
distinct pieces of code, it is generally beneficial to combine them into one by
abstracting out the varying parts.

Why

- Duplication (inadvertent or purposeful duplication) can lead to maintenance
  nightmares, poor factoring, and logical contradictions.
- A modification of any single element of a system does not require a change in
  other logically unrelated elements.
- Additionally, elements that are logically related all change predictably and
  uniformly, and are thus kept in sync.

How

- Put business rules, long expressions, if statements, math formulas, metadata,
  etc. in only one place.
- Identify the single, definitive source of every piece of knowledge used in
  your system, and then use that source to generate applicable instances of that
  knowledge (code, documentation, tests, etc).
- Apply the [Rule of three][55].

Resources

- [Dont Repeat Yourself (wiki.c2.com)][56]
- [Don't repeat yourself (wikipedia.org)][57]
- [DRY Principle: Its Benefit and Cost with Examples (thevaluable.dev)][58]

Related

- [Abstraction principle (wikipedia.org)][59]
- [Once And Only Once (wiki.c2.com)][60] is a subset of DRY (also referred to as
  the goal of refactoring).
- [Single Source of Truth (wikipedia.org)][61]
- A violation of DRY is [WET][62] (Write Everything Twice)
- [Be careful with the code metric "duplicated lines"
  (rachelcarmena.github.io)][63]

## Boy Scout Rule

The Boy Scouts of America have a simple rule that we can apply to our
profession: "Leave the campground cleaner than you found it". The boy scout rule
states that we should always leave the code cleaner than we found it.

Why

- When making changes to an existing codebase the code quality tends to degrade,
  accumulating technical debt. Following the boy scout rule, we should mind the
  quality with each commit. Technical debt is resisted by continuous
  refactoring, no matter how small.

How

- With each commit make sure it does not degrade the codebase quality.
- Any time someone sees some code that isn't as clear as it should be, they
  should take the opportunity to fix it right there and then.

Resources

- [Opportunistic Refactoring (martinfowler.com)][64]

## Connascence

Connascence is a software quality metric that describes different levels and
dimensions of coupling. Two components are connascent if a change in one would
require a change in the other as well. Lower connascence means higher code
quality.

Why

- Reducing connascence will reduce the cost of change for a software system.
- Arguably one of the most important benefits of connascence is that it gives
  developers a vocabulary to talk about different types of coupling.

How

- Each instance of connascence in a codebase is considered on 3 separate axes:
  strength, degree and locality.
- It provides a system for comparing different types of dependency.

Resources

- [Connascence (connascence.io)][65]
- [Connascence (wikipedia.org)][66]

## Minimise Coupling

Coupling between modules or components is their degree of mutual
interdependence; lower coupling is better. In other words, coupling is the
probability that code unit "B" will "break" after an unknown change to code unit
"A".

Why

- A change in one module usually forces a ripple effect of changes in other
  modules.
- Assembly of modules might require more effort and/or time due to the increased
  inter-module dependency.
- A particular module might be harder to reuse and/or test because dependent
  modules must be included.
- Developers might be afraid to change code because they aren't sure what might
  be affected.

How

- Eliminate, minimise, and reduce complexity of necessary relationships.
- By hiding implementation details, coupling is reduced.
- Apply the [Law of Demeter][14].

Resources

- [Coupling (wikipedia.org)][67]
- [Coupling And Cohesion (wiki.c2.com)][68]

## Law of Demeter

Don't talk to strangers.

Why

- It usually tightens coupling
- It might reveal too much implementation details

How

A method of an object may only call methods of:

1. The object itself.
2. An argument of the method.
3. Any object created within the method.
4. Any direct properties/fields of the object.

Resources

- [Law of Demeter (wikipedia.org)][69]
- [The Law of Demeter Is Not A Dot Counting Exercise (haacked.com)][70]

## Composition Over Inheritance

It is better to compose what an object can do than extend what it is. Compose
when there is a "has a" (or "uses a") relationship, inherit when "is a".

Why

- Less coupling between classes.
- Using inheritance, subclasses easily make assumptions, and break [LSP][71].
- Increase flexibility: accommodate future requirements changes, otherwise
  requiring restructuring of business-domain classes in the inheritance model.
- Avoid problems often associated with relatively minor changes to an
  inheritance-based model including several generations of classes.

How

- Identify system object behaviors in separate interfaces, instead of creating a
  hierarchical relationship to distribute behaviors among business-domain
  classes via inheritance.
- Test for [LSP][71] to decide when to inherit.

Resources

- [Composition over inheritance (wikipedia.org)][72]
- [Favor Composition Over Inheritance (docs.microsoft.com)][73]

## Orthogonality

> The basic idea of orthogonality is that things that are not related
> conceptually should not be related in the system.

Source: [Be Orthogonal][74]

> It is associated with simplicity; the more orthogonal the design, the fewer
> exceptions. This makes it easier to learn, read and write programs in a
> programming language. The meaning of an orthogonal feature is independent of
> context; the key parameters are symmetry and consistency.

Source: [Orthogonality (wikipedia.org)][75]

## Robustness Principle

> Be conservative in what you do, be liberal in what you accept from others

Collaborating services depend on each others interfaces. Often the interfaces
need to evolve causing the other end to receive unspecified data. A naive
implementation refuses to collaborate if the received data does not strictly
follow the specification. A more sophisticated implementation will still work
ignoring the data it does not recognize.

Why

- Ensure that a provider can make changes to support new demands, while causing
  minimal breakage to their existing clients.

How

- Code that sends commands or data to other programs or machines should conform
  completely to the specifications, but code that receives input should accept
  non-conformant input as long as the meaning is clear.

Resources

- [Robustness Principle (wikipedia.org)][76]
- [Tolerant Reader (martinfowler.com)][77]

## Inversion of Control

IoC inverts the flow of control. It's also known as the Hollywood Principle,
"Don't call us, we'll call you". A design principle in which custom-written
portions of a computer program receive the flow of control from a generic
framework. It carries the strong connotation that the reusable code and the
problem-specific code are developed independently even though they operate
together in an application.

Why

- Increase modularity of the program and make it extensible.
- To decouple the execution of a task from implementation.
- To focus a module on the task it is designed for.
- To free modules from assumptions about other systems and instead rely on
  contracts.
- To prevent side effects when replacing a module.

How

- Using Factory pattern
- Using Service Locator pattern
- Using Dependency Injection
- Using contextualized lookup
- Using Template Method pattern
- Using Strategy pattern

Resources

- [Inversion of Control (wikipedia.org)][78]
- [Inversion of Control Containers and the Dependency Injection pattern
  (martinfowler.com)][79]

## Maximise Cohesion

Cohesion of a single module or component is the degree to which its
responsibilities form a meaningful unit. Higher cohesion is better.

Why

- Reduced module complexity
- Increased system maintainability, because logical changes in the domain affect
  fewer modules, and because changes in one module require fewer changes in
  other modules.
- Increased module reusability, because application developers will find the
  component they need more easily among the cohesive set of operations provided
  by the module.

How

- Group related functionalities sharing a single responsibility (e.g. in a
  module or class).

Resources

- [Cohesion (wikipedia.org)][80]
- [Coupling And Cohesion (wiki.c2.com)][68]

## Liskov Substitution Principle

The LSP is all about expected behavior of objects:

> Objects in a program should be replaceable with instances of their subtypes
> without altering the correctness of that program.

**LSP** is the L in [SOLID][29].

Resources

- [Liskov substitution principle (wikipedia.org)][81]
- [The Liskov Substitution Principle Explained (reflectoring.io)][82]

## Open/Closed Principle

Software entities (e.g. classes) should be open for extension, but closed for
modification. Such an entity can allow its behavior to be modified, without
altering its source code.

**Open/Closed** is the O in [SOLID][29].

Why

- Improve maintainability and stability by minimizing changes to existing code.

How

- Write classes that can be extended (as opposed to classes that can be
  modified).
- Expose only the moving parts that need to change, hide everything else.

Resources

- [Open Closed Principle (wikipedia.org)][83]
- [The Open Closed Principle (blog.cleancoder.com)][84]

## Single Responsibility Principle

A class should never have more than one reason to change.

Long version: Every class should have a single responsibility, and that
responsibility should be entirely encapsulated by the class. Responsibility can
be defined as a reason to change, so a class or module should have one, and only
one, reason to change.

**SRP** is the S in [SOLID][29].

Why

- Maintainability: changes should be necessary only in one module or class.

How

- Apply [Curly's Law][85].

Resources

- [Single responsibility principle (wikipedia.org)][86]

## Hide Implementation Details

A software module hides information (i.e. implementation details) by providing
an interface, and not leak any unnecessary information.

Why

- When the implementation changes, the interface clients are using does not have
  to change.

How

- Minimize accessibility of classes and members.
- Don’t expose member data in public.
- Avoid putting private implementation details into a class’s interface.
- Decrease coupling to hide more implementation details.

Resources

- [Information hiding (wikipedia.org)][87]

## Curly's Law

Curly's Law is about choosing a single, clearly defined goal for any particular
bit of code: Do One Thing.

- [Curly's Law: Do One Thing (blog.codinghorror.com)][88]
- [The Rule of One or Curly’s Law (grsmentor.com)][89]

## Encapsulate What Changes

A good design identifies the hotspots that are most likely to change and
encapsulates them behind an interface. When an anticipated change then occurs,
the modifications are kept local.

Why

- To minimize required modifications when a change occurs.

How

- Encapsulate the concept that varies behind an interface.
- Possibly separate the varying concept into its own module.

Resources

- [Encapsulate the Concept that Varies (principles-wiki.net)][90]
- [Encapsulate What Varies (blogs.msdn.microsoft.com)][91]
- [Information hiding (wikipedia.org)][87]

## Interface Segregation Principle

Reduce fat interfaces into multiple smaller and more specific client specific
interfaces. An interface should be more dependent on the code that calls it than
the code that implements it.

**ISP** is the I in [SOLID][29].

Why

- Keep a system decoupled and thus easier to refactor, change, and redeploy.

How

- Avoid fat interfaces. Classes should never have to implement methods that
  violate the [Single responsibility principle][22].

Resources

- [Interface segregation principle (wikipedia.org)][92]

## Command Query Separation

The Command Query Separation principle states that each method should be either
a command that performs an action, or a query that returns data to the caller
but not both. Asking a question should not modify the answer.

With this principle applied the programmer can code with much more confidence.
The query methods can be used anywhere and in any order since they do not mutate
the state. With commands one has to be more careful.

Why

- By clearly separating methods into queries and commands the programmer can
  code with additional confidence without knowing each method's implementation
  details.

How

- Implement each method as either a query or a command
- Apply naming convention to method names that implies whether the method is a
  query or a command

Resources

- [Command Query Separation (wikipedia.org)][93]
- [Command Query Separation (martinfowler.com)][94]

## Dependency Inversion Principle

Dependency Inversion is the strategy of depending upon interfaces or abstract
functions and classes rather than upon concrete functions and classes. Simply
put, when components of our system have dependencies, we don’t want to directly
inject a component’s dependency into another. Instead, we should use a level of
abstraction between them.

**DIP** is the D in [SOLID][29].

Why

- By decoupling the high-level modules from the low-level modules, the
  high-level modules become more reusable and maintainable.
- Facilitates unit testing by allowing the use of mock objects, enabling
  isolated testing of modules.
- Reduces the risk of breaking the system when changes are made.
- Allows adding new implementations without changing the existing code,
  enhancing the system's extensibility.
- Concrete classes change frequently, while abstractions and interfaces change
  much less.

How

- Define interfaces to capture behavior and use them to define the dependencies
  of a class.
- Depends on abstractions, not on concretions.
- Using patterns like Factory, Service Locator, and Dependency Injection.
- Use the [Inversion of Control][18] principle.

Resources

- [SOLID — Dependency Inversion Principle][95]
- [Dependency inversion principle (wikipedia.org)][96]
- [System Design: Dependency Inversion Principle][97]

## SOLID

A subset of programming principles:

- [Single Responsibility Principle][22]
- [Open/Closed Principle][21]
- [Liskov Substitution Principle][20]
- [Interface Segregation Principle][26]
- [Dependency Inversion Principle][28]

## FIRST principles of testing

The FIRST testing principles mean that tests should be Fast, Isolated,
Repeatable, Self-validating and Timely.

Resources

- [F.I.R.S.T.][98]

## Arrange, Act, Assert

The 3A's are a pattern to arrange and format code in unit tests. _Arrange_ all
necessary preconditions and inputs. _Act_ on the object or method under test.
_Assert_ that the expected results have occurred.

Resources

- [Arrange Act Assert (wiki.c2.com)][99]
- [3A - Arrange, Act, Assert (xp123.com)][100]

[1]: https://www.artima.com/weblogs/viewpost.jsp?thread=331531
[2]: https://github.com/webpro/programming-principles/issues
[3]: #kiss
[4]: #yagni
[5]: #do-the-simplest-thing-that-could-possibly-work
[6]: #separation-of-concerns
[7]: #code-for-the-maintainer
[8]: #avoid-premature-optimization
[9]: #optimize-for-deletion
[10]: #keep-things-dry
[11]: #boy-scout-rule
[12]: #connascence
[13]: #minimise-coupling
[14]: #law-of-demeter
[15]: #composition-over-inheritance
[16]: #orthogonality
[17]: #robustness-principle
[18]: #inversion-of-control
[19]: #maximise-cohesion
[20]: #liskov-substitution-principle
[21]: #openclosed-principle
[22]: #single-responsibility-principle
[23]: #hide-implementation-details
[24]: #curlys-law
[25]: #encapsulate-what-changes
[26]: #interface-segregation-principle
[27]: #command-query-separation
[28]: #dependency-inversion-principle
[29]: #solid
[30]: #first-principles-of-testing
[31]: #arrange-act-assert
[32]: https://en.wikipedia.org/wiki/KISS_principle
[33]: http://principles-wiki.net/principles:keep_it_simple_stupid
[34]: https://github.com/zakirullin/cognitive-load
[35]:
  https://florian-kraemer.net/software-architecture/2024/07/25/The-Limits-of-Human-Cognitive-Capacities-in-Programming.html
[36]: https://eugeneyan.com/writing/simplicity/
[37]: http://c2.com/xp/YouArentGonnaNeedIt.html
[38]: https://ronjeffries.com/xprog/articles/practices/pracnotneed/
[39]: https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it
[40]: http://c2.com/xp/DoTheSimplestThingThatCouldPossiblyWork.html
[41]: https://en.wikipedia.org/wiki/Edsger_W._Dijkstra
[42]: https://en.wikipedia.org/wiki/Separation_of_concerns
[43]: http://www.sensible.com/dmmt.html
[44]: https://en.wikipedia.org/wiki/Principle_of_least_astonishment
[45]: http://wiki.c2.com/?CodeForTheMaintainer
[46]: https://blog.codinghorror.com/the-noble-art-of-maintenance-programming/
[47]: https://en.wikiquote.org/wiki/Donald_Knuth
[48]: http://wiki.c2.com/?MakeItWorkMakeItRightMakeItFast
[49]: https://en.wikipedia.org/wiki/Program_optimization
[50]: http://wiki.c2.com/?PrematureOptimization
[51]: https://www.youtube.com/watch?v=Ed94CfxgsCA
[52]: https://work.stevegrossi.com/2016/11/04/optimize-for-deletion/
[53]: https://kellysutton.com/2017/05/29/deletability.html
[54]:
  https://programmingisterrible.com/post/139222674273/write-code-that-is-easy-to-delete-not-easy-to
[55]: https://en.wikipedia.org/wiki/Rule_of_three_(computer_programming)
[56]: http://wiki.c2.com/?DontRepeatYourself
[57]: https://en.wikipedia.org/wiki/Don't_repeat_yourself
[58]: https://thevaluable.dev/dry-principle-cost-benefit-example/
[59]: https://en.wikipedia.org/wiki/Abstraction_principle_(computer_programming)
[60]: http://wiki.c2.com/?OnceAndOnlyOnce
[61]: https://en.wikipedia.org/wiki/Single_Source_of_Truth
[62]: http://thedailywtf.com/articles/The-WET-Cart
[63]:
  https://rachelcarmena.github.io/2018/02/27/duplication-you-are-welcome.html
[64]: https://martinfowler.com/bliki/OpportunisticRefactoring.html
[65]: https://connascence.io
[66]: https://en.wikipedia.org/wiki/Connascence
[67]: https://en.wikipedia.org/wiki/Coupling_(computer_programming)
[68]: http://wiki.c2.com/?CouplingAndCohesion
[69]: https://en.wikipedia.org/wiki/Law_of_Demeter
[70]: https://haacked.com/archive/2009/07/14/law-of-demeter-dot-counting.aspx/
[71]: #lsp
[72]: https://en.wikipedia.org/wiki/Composition_over_inheritance
[73]:
  https://docs.microsoft.com/en-us/archive/blogs/thalesc/favor-composition-over-inheritance
[74]: https://www.artima.com/intv/dry3.html
[75]: https://en.wikipedia.org/wiki/Orthogonality_(programming)
[76]: https://en.wikipedia.org/wiki/Robustness_principle
[77]: https://martinfowler.com/bliki/TolerantReader.html
[78]: https://en.wikipedia.org/wiki/Inversion_of_control
[79]: https://www.martinfowler.com/articles/injection.html
[80]: https://en.wikipedia.org/wiki/Cohesion_(computer_science)
[81]: https://en.wikipedia.org/wiki/Liskov_substitution_principle
[82]: https://reflectoring.io/lsp-explained/
[83]: https://en.wikipedia.org/wiki/Open/closed_principle
[84]:
  https://blog.cleancoder.com/uncle-bob/2014/05/12/TheOpenClosedPrinciple.html
[85]: #curlys-Law
[86]: https://en.wikipedia.org/wiki/Single_responsibility_principle
[87]: https://en.wikipedia.org/wiki/Information_hiding
[88]: https://blog.codinghorror.com/curlys-law-do-one-thing/
[89]: http://grsmentor.com/blog/the-rule-of-one-or-curlys-law/
[90]: http://principles-wiki.net/principles:encapsulate_the_concept_that_varies
[91]:
  https://blogs.msdn.microsoft.com/steverowe/2007/12/26/encapsulate-what-varies/
[92]: https://en.wikipedia.org/wiki/Interface_segregation_principle
[93]: https://en.wikipedia.org/wiki/Command%E2%80%93query_separation
[94]: https://martinfowler.com/bliki/CommandQuerySeparation.html
[95]:
  https://medium.com/@inzuael/solid-dependency-inversion-principle-part-5-f5bec43ab22e
[96]: https://en.wikipedia.org/wiki/Dependency_inversion_principle
[97]: https://www.baeldung.com/cs/dip
[98]: https://agileinaflash.blogspot.com/2009/02/first.html
[99]: https://wiki.c2.com/?ArrangeActAssert
[100]: https://xp123.com/articles/3a-arrange-act-assert/
