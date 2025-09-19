## Don't Repeat Yourself
"**Don't repeat yourself**" (**DRY**) is a [principle](https://en.wikipedia.org/wiki/Principle#Principle_as_axiom_or_logical_fundament "Principle") of [software development](https://en.wikipedia.org/wiki/Software_development_process "Software development process") aimed at reducing repetition of [information](https://en.wikipedia.org/wiki/Information_theory "Information theory") which is likely to change, replacing it with [abstractions](https://en.wikipedia.org/wiki/Information_hiding "Information hiding") that are less likely to change, or using [data normalization](https://en.wikipedia.org/wiki/Data_normalization "Data normalization") which avoids redundancy in the first place.

The DRY principle is stated as "Every piece of knowledge must have a single, unambiguous, authoritative representation within a system". The principle has been formulated by [Andy Hunt](https://en.wikipedia.org/wiki/Andy_Hunt_(author) "Andy Hunt (author)") and [Dave Thomas](https://en.wikipedia.org/wiki/Dave_Thomas_(author) "Dave Thomas (author)") in their book _[The Pragmatic Programmer](https://en.wikipedia.org/wiki/The_Pragmatic_Programmer "The Pragmatic Programmer")_. They apply it quite broadly to include [database schemas](https://en.wikipedia.org/wiki/Database_schema "Database schema"), [test plans](https://en.wikipedia.org/wiki/Test_plan "Test plan"), the [build](https://en.wikipedia.org/wiki/Software_build "Software build") system, even [documentation](https://en.wikipedia.org/wiki/Software_documentation "Software documentation"). When the DRY principle is applied successfully, a modification of any single element of a system does not require a change in other logically unrelated elements. Additionally, elements that are logically related all change predictably and uniformly, and are thus kept in [sync](https://en.wikipedia.org/wiki/Synchronization "Synchronization"). Besides using [methods](https://en.wikipedia.org/wiki/Method_(computer_science) "Method (computer science)") and [subroutines](https://en.wikipedia.org/wiki/Subroutine "Subroutine") in their code, Thomas and Hunt rely on [code generators](https://en.wikipedia.org/wiki/Automatic_programming "Automatic programming"), automatic build systems, and [scripting languages](https://en.wikipedia.org/wiki/Scripting_language "Scripting language") to observe the DRY principle across layers.

### Single choice principle
A particular case of DRY is the **single choice principle**. It was defined by [Bertrand Meyer](https://en.wikipedia.org/wiki/Bertrand_Meyer "Bertrand Meyer") as: "Whenever a software system must support a set of alternatives, one and only one module in the system should know their exhaustive list." It was applied when designing [Eiffel](https://en.wikipedia.org/wiki/Eiffel_(programming_language) "Eiffel (programming language)").

### Alternatives
#### WET
The opposing view to DRY is called WET, a [backronym](https://en.wikipedia.org/wiki/Backronym "Backronym") commonly taken to stand for _write everything twice_ (alternatively _write every time_, _we enjoy typing_ or _waste everyone's time_). WET solutions are common in multi-tiered architectures where a developer may be tasked with, for example, adding a comment field on a form in a web application. The text string "comment" might be repeated in the label, the HTML tag, in a read function name, a private variable, database DDL, queries, and so on. A DRY approach eliminates that redundancy by using frameworks that reduce or eliminate all those editing tasks except the most important ones, leaving the extensibility of adding new knowledge variables in one place. This conceptualization of "WET" as an alternative to "DRY" programming has been around since at least 2002 in the Java world, though it is not known who coined the term.

#### AHA
Another approach to abstractions is the AHA principle. AHA stands for _avoid hasty abstractions_, described by [Kent C. Dodds](https://en.wikipedia.org/w/index.php?title=Kent_C._Dodds&action=edit&redlink=1 "Kent C. Dodds (page does not exist)") as optimizing for change first, and avoiding premature optimization. and was influenced by [Sandi Metz](https://en.wikipedia.org/wiki/Sandi_Metz "Sandi Metz")'s "prefer duplication over the wrong abstraction".

AHA is rooted in the understanding that the deeper the investment engineers have made into abstracting a piece of software, the more they perceive that the cost of that investment can never be recovered ([sunk cost fallacy](https://en.wikipedia.org/wiki/Sunk_cost "Sunk cost")). Thus, engineers tend to continue to iterate on the same abstraction each time the requirement changes. AHA programming assumes that both WET and DRY solutions inevitably create software that is rigid and difficult to maintain. Instead of starting with an abstraction, or abstracting at a specific number of duplications, software can be more flexible and robust if abstraction is done when it is needed, or, when the duplication itself has become the barrier and it is known how the abstraction needs to function.

AHA programming was originally named "moist code" by Dodds, later again by Daniel Bartholomae, and originally referred to as DAMP (_Don't Abstract Methods Prematurely_) by Matt Ryer. There was a different programming principle already named DAMP (_Descriptive And Meaningful Phrases_) and described by Jay Fields, and the community pushed back against the usage of MOIST, due to the cultural aversion to the word _moist_. Dodds called for alternatives on [Twitter](https://en.wikipedia.org/wiki/Twitter "Twitter"), and suggested DATE as an alternative before settling on [Cher Scarlett](https://en.wikipedia.org/wiki/Cher_Scarlett "Cher Scarlett")'s suggestion of AHA.

## KISS Principle
**KISS**, an [acronym](https://en.wikipedia.org/wiki/Acronym "Acronym") for "**Keep it simple, stupid!**", is a [design](https://en.wikipedia.org/wiki/Design "Design") principle first noted by the [U.S. Navy](https://en.wikipedia.org/wiki/U.S._Navy "U.S. Navy") in 1960. First seen partly in [American English](https://en.wikipedia.org/wiki/American_English "American English") by at least 1938, KISS implies that [simplicity](https://en.wikipedia.org/wiki/Simplicity "Simplicity") should be a design goal. The phrase has been associated with aircraft engineer [Kelly Johnson](https://en.wikipedia.org/wiki/Kelly_Johnson_(engineer) "Kelly Johnson (engineer)"). The term "KISS principle" was in popular use by 1970. Variations on the phrase (usually as some [euphemism](https://en.wikipedia.org/wiki/Euphemism "Euphemism") for the more churlish "stupid") include "keep it super simple", "keep it simple, silly", "keep it short and simple", "keep it short and sweet", "keep it simple and straightforward", "keep it small and simple", "keep it simple, soldier", "keep it simple, sailor", "keep it simple, sweetie", "keep it stupidly simple", or "keep it sweet and simple".

### Origin
The acronym was reportedly coined by [Kelly Johnson](https://en.wikipedia.org/wiki/Kelly_Johnson_(engineer) "Kelly Johnson (engineer)"), lead engineer at the [Lockheed](https://en.wikipedia.org/wiki/Lockheed_Martin "Lockheed Martin") [Skunk Works](https://en.wikipedia.org/wiki/Skunk_Works "Skunk Works") (creators of the [Lockheed U-2](https://en.wikipedia.org/wiki/Lockheed_U-2 "Lockheed U-2") and [SR-71 Blackbird](https://en.wikipedia.org/wiki/SR-71_Blackbird "SR-71 Blackbird") spy planes, among many others). However, the variant "Keep it Short and Simple" is attested from a 1938 issue of the _[Minneapolis Star](https://en.wikipedia.org/wiki/Minneapolis_Star "Minneapolis Star")_.

While popular usage has transcribed it for decades as "Keep it simple, stupid", Johnson transcribed it simply as "Keep it simple stupid" (no comma), and this reading is still used by many authors.

The principle is best exemplified by the story of Johnson handing a team of design engineers a handful of tools, with the challenge that the [jet aircraft](https://en.wikipedia.org/wiki/Jet_aircraft "Jet aircraft") they were designing must be repairable by an average [mechanic](https://en.wikipedia.org/wiki/Mechanic "Mechanic") in the field under combat conditions with only these tools. Hence, the "stupid" refers to the relationship between the way things break and the sophistication available to repair them.

The acronym has been used by many in the [U.S. military](https://en.wikipedia.org/wiki/List_of_military_slang_terms "List of military slang terms"), especially the [U.S. Navy](https://en.wikipedia.org/wiki/List_of_U.S._Navy_acronyms_and_expressions "List of U.S. Navy acronyms and expressions") and [United States Air Force](https://en.wikipedia.org/wiki/United_States_Air_Force "United States Air Force"), and in the field of [software development](https://en.wikipedia.org/wiki/Software_development "Software development").

### Variants
The principle most probably finds its origins in similar [minimalist](https://en.wikipedia.org/wiki/Minimalism "Minimalism") concepts, such as:
- [Occam's razor](https://en.wikipedia.org/wiki/Occam%27s_razor "Occam's razor");
- "Simplicity is the ultimate sophistication";
- [Shakespeare](https://en.wikipedia.org/wiki/Shakespeare "Shakespeare")'s "Brevity is the soul of wit";
- [Mies van der Rohe](https://en.wikipedia.org/wiki/Mies_van_der_Rohe "Mies van der Rohe")'s "[Less is more](https://en.wikipedia.org/wiki/Less_is_more_(architecture) "Less is more (architecture)")";
- [Bjarne Stroustrup](https://en.wikipedia.org/wiki/Bjarne_Stroustrup "Bjarne Stroustrup")'s "Make Simple Tasks Simple!";
- [Dr. Seuss](https://en.wikipedia.org/wiki/Dr._Seuss "Dr. Seuss")'s ode to brevity: "So the writer who breeds more words than he needs, is making a chore for the reader who reads";
- [Johan Cruyff](https://en.wikipedia.org/wiki/Johan_Cruyff "Johan Cruyff")'s "Playing football is very simple but playing simple football is the hardest thing there is";
- [Antoine de Saint-Exupéry](https://en.wikipedia.org/wiki/Antoine_de_Saint-Exup%C3%A9ry "Antoine de Saint-Exupéry")'s "It seems that perfection is reached not when there is nothing left to add, but when there is nothing left to take away";
- [Colin Chapman](https://en.wikipedia.org/wiki/Colin_Chapman "Colin Chapman"), the founder of [Lotus Cars](https://en.wikipedia.org/wiki/Lotus_Cars "Lotus Cars"), urged his designers to "Simplify, then add lightness";
- Attributed to [Albert Einstein](https://en.wikipedia.org/wiki/Albert_Einstein "Albert Einstein"), although this may be an editor's paraphrase of a lecture he gave, "Make everything as simple as possible, but not simpler";
- [Steve Jobs](https://en.wikipedia.org/wiki/Steve_Jobs "Steve Jobs")'s "~~Simplify~~, ~~Simplify~~, Simplify") which simplified [Henry David Thoreau](https://en.wikipedia.org/wiki/Henry_David_Thoreau "Henry David Thoreau")'s quote "Simplify, simplify, simplify" for emphasis;
- [Northcote Parkinson](https://en.wikipedia.org/wiki/C._Northcote_Parkinson "C. Northcote Parkinson"), British academic and sometimes military officer and military critic, expressed this idea as "Parkinson's Third Law" (c. 1957): "Expansion means complexity and complexity, decay; or to put it even more plainly—the more complex, the sooner dead";

[Heath Robinson](https://en.wikipedia.org/wiki/Heath_Robinson "Heath Robinson") contraptions and [Rube Goldberg's machines](https://en.wikipedia.org/wiki/Rube_Goldberg_machine "Rube Goldberg machine"), intentionally overly-complex solutions to simple tasks or problems, are humorous examples of "non-KISS" solutions.

### Usage
#### In film animation
Master animator [Richard Williams](https://en.wikipedia.org/wiki/Richard_Williams_(animator) "Richard Williams (animator)") explains the KISS principle in his book _[The Animator's Survival Kit](https://en.wikipedia.org/wiki/The_Animator%27s_Survival_Kit "The Animator's Survival Kit")_, and [Disney's Nine Old Men](https://en.wikipedia.org/wiki/Disney%27s_Nine_Old_Men "Disney's Nine Old Men") write about it in _[Disney Animation: The Illusion of Life](https://en.wikipedia.org/wiki/Disney_Animation:_The_Illusion_of_Life "Disney Animation: The Illusion of Life")_, a considerable work of the genre. The problem faced is that inexperienced animators may "over-animate" in their works, that is, a character may move too much and do too much. Williams urges animators to "KISS".

#### In software development
- [Don't repeat yourself](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself "Don't repeat yourself") (DRY)
- [Minimalism](https://en.wikipedia.org/wiki/Minimalism_(computing) "Minimalism (computing)")
- [Unix philosophy](https://en.wikipedia.org/wiki/Unix_philosophy "Unix philosophy")
- [Arch Linux](https://en.wikipedia.org/wiki/Arch_Linux "Arch Linux")
- [Slackware Linux](https://en.wikipedia.org/wiki/Slackware_Linux "Slackware Linux")
- [Chartjunk](https://en.wikipedia.org/wiki/Chartjunk "Chartjunk")
- [List of software development philosophies](https://en.wikipedia.org/wiki/List_of_software_development_philosophies "List of software development philosophies")
- [Reduced instruction set computing](https://en.wikipedia.org/wiki/Reduced_instruction_set_computing "Reduced instruction set computing")
- [Rule of least power](https://en.wikipedia.org/wiki/Rule_of_least_power "Rule of least power")
- [There's more than one way to do it](https://en.wikipedia.org/wiki/There%27s_more_than_one_way_to_do_it "There's more than one way to do it")
- [Worse is better](https://en.wikipedia.org/wiki/Worse_is_better "Worse is better") (Less is more)
- [You aren't gonna need it](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it "You aren't gonna need it") (YAGNI)

## Reusability
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science") and [software engineering](https://en.wikipedia.org/wiki/Software_engineering "Software engineering"), **reusability** is the use of existing _assets_ in some form within the [software product development process](https://en.wikipedia.org/wiki/Software_development_process "Software development process"); these _assets_ are products and by-products of the software development life cycle and include code, software components, test suites, designs and documentation. The opposite concept of _reusability_ is **leverage**, which modifies existing assets as needed to meet specific system requirements. Because reuse implies the creation of a separately maintained version of the assets, it is preferred over leverage.

[Subroutines](https://en.wikipedia.org/wiki/Subroutine "Subroutine") or [functions](https://en.wikipedia.org/wiki/Function_(programming) "Function (programming)") are the simplest form of reuse. A chunk of code is regularly organized using [modules](https://en.wikipedia.org/wiki/Modular_programming "Modular programming") or [namespaces](https://en.wikipedia.org/wiki/Namespace "Namespace") into [layers](https://en.wikipedia.org/wiki/Layer_(object-oriented_design) "Layer (object-oriented design)"). Proponents claim that [objects](https://en.wikipedia.org/wiki/Object_(computer_science) "Object (computer science)") and [software components](https://en.wikipedia.org/wiki/Software_component "Software component") offer a more advanced form of reusability, although it has been tough to objectively measure and define levels or scores of reusability.

The ability to reuse relies in an essential way on the ability to build larger things from smaller parts, and being able to identify commonality among those parts. Reusability is often a required characteristic of [platform](https://en.wikipedia.org/wiki/Platform_(computing) "Platform (computing)") software. Reusability brings several aspects to [software development](https://en.wikipedia.org/wiki/Software_development "Software development") that do not need to be considered when reusability is not required.

Reusability implies some explicit management of [build](https://en.wikipedia.org/wiki/Software_build "Software build"), [packaging](https://en.wikipedia.org/wiki/Packaging "Packaging"), [distribution](https://en.wikipedia.org/wiki/Distribution_(business) "Distribution (business)"), [installation](https://en.wikipedia.org/wiki/Installation_(computer_programs) "Installation (computer programs)"), [configuration](https://en.wikipedia.org/wiki/Computer_configuration "Computer configuration"), [deployment](https://en.wikipedia.org/wiki/Software_deployment "Software deployment"), [maintenance](https://en.wikipedia.org/wiki/Software_maintenance "Software maintenance") and [upgrade](https://en.wikipedia.org/wiki/Upgrade "Upgrade") issues. If these issues are not considered, software may appear to be reusable from [design](https://en.wikipedia.org/wiki/Software_design "Software design") point of view, but will not be reused in practice.

Software reusability more specifically refers to design features of a software element (or collection of software elements) that enhance its suitability for reuse.

Many reuse design principles were developed at the WISR workshops.

Candidate design features for software reuse include:
- [Adaptable](https://en.wikipedia.org/wiki/Adaptability "Adaptability")
- Brief: small size
- [Consistency](https://en.wikipedia.org/wiki/Consistency "Consistency")
- [Correctness](https://en.wikipedia.org/wiki/Correctness_(computer_science) "Correctness (computer science)")
- [Extensibility](https://en.wikipedia.org/wiki/Extensibility "Extensibility")
- [Fast](https://en.wikipedia.org/wiki/Speed "Speed")
- Flexible
- [Generic](https://en.wikipedia.org/wiki/Generic_programming "Generic programming")
- Localization of volatile ([changeable](https://en.wikipedia.org/w/index.php?title=Changeable_design&action=edit&redlink=1 "Changeable design (page does not exist)")) design assumptions ([David Parnas](https://en.wikipedia.org/wiki/David_Parnas "David Parnas"))
- [Modularity](https://en.wikipedia.org/wiki/Modularity_(programming) "Modularity (programming)")
- [Orthogonality](https://en.wikipedia.org/wiki/Orthogonality "Orthogonality")
- Simple: low [complexity](https://en.wikipedia.org/wiki/Complexity_(disambiguation) "Complexity (disambiguation)")
- [Stability](https://en.wikipedia.org/wiki/Stability_Model "Stability Model") under changing [requirements](https://en.wikipedia.org/wiki/Requirements "Requirements")

Consensus has not yet been reached on this list on the relative importance of the entries nor on the issues which make each one important for a particular class of applications.

## Code Reuse
In [software development](https://en.wikipedia.org/wiki/Software_development "Software development") (and [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming") in general), **code reuse**, also called **software reuse**, is the use of existing [software](https://en.wikipedia.org/wiki/Software "Software"), or software knowledge, to build new software, following the [reusability principles](https://en.wikipedia.org/wiki/Reusability "Reusability").

Code reuse may be achieved by different ways depending on a complexity of a [programming language](https://en.wikipedia.org/wiki/Programming_language "Programming language") chosen and range from a lower-level approaches like code [copy-pasting](https://en.wikipedia.org/wiki/Cut,_copy,_and_paste "Cut, copy, and paste") (e.g. via [snippets](https://en.wikipedia.org/wiki/Snippet_(programming) "Snippet (programming)")), simple functions ([procedures](https://en.wikipedia.org/wiki/Procedure_(computer_science) "Procedure (computer science)") or [subroutines](https://en.wikipedia.org/wiki/Subroutine "Subroutine")) or a bunch of [objects](https://en.wikipedia.org/wiki/Object_(computer_science) "Object (computer science)") or [functions](https://en.wikipedia.org/wiki/Subroutine "Subroutine") organized into [modules](https://en.wikipedia.org/wiki/Modular_programming "Modular programming") (e.g. [libraries](https://en.wikipedia.org/wiki/Library_(computing) "Library (computing)")) or custom [namespaces](https://en.wikipedia.org/wiki/Namespace "Namespace"), and [packages](https://en.wikipedia.org/wiki/Package_manager "Package manager"), [frameworks](https://en.wikipedia.org/wiki/Framework_(computer_science) "Framework (computer science)") or [software suites](https://en.wikipedia.org/wiki/Software_suite "Software suite") in higher-levels.

Code reuse implies dependencies which can make [code maintainability](https://en.wikipedia.org/wiki/Software_maintenance "Software maintenance") harder. _At least one study found that code reuse reduces technical debt_.

### Overview
[Ad hoc](https://en.wikipedia.org/wiki/Ad_hoc "Ad hoc") code reuse has been practiced from the earliest days of [programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"). Programmers have always reused sections of code, templates, functions, and procedures. Software reuse as a recognized area of study in software engineering, however, dates only from 1968 when [Douglas McIlroy](https://en.wikipedia.org/wiki/Douglas_McIlroy "Douglas McIlroy") of [Bell Laboratories](https://en.wikipedia.org/wiki/Bell_Labs "Bell Labs") proposed basing the software industry on reusable components.

Code reuse aims to save time and resources and reduce [redundancy](https://en.wikipedia.org/wiki/Redundancy_(information_theory) "Redundancy (information theory)") by taking advantage of assets that have already been created in some form within the software product development process. The key idea in reuse is that parts of a [computer program](https://en.wikipedia.org/wiki/Computer_program "Computer program") written at one time can be or should be used in the construction of other programs written at a later time.

Code reuse may imply the creation of a separately maintained version of the reusable assets. While code is the most common resource selected for reuse, other assets generated during the development cycle may offer opportunities for reuse: software components, test suites, designs, documentation, and so on.
The [software library](https://en.wikipedia.org/wiki/Library_(computing) "Library (computing)") is a good example of code reuse. Programmers may decide to create internal abstractions so that certain parts of their program can be reused, or may create custom libraries for their own use. Some characteristics that make software more easily reusable are [modularity](https://en.wikipedia.org/wiki/Modularity_(programming) "Modularity (programming)"), [loose coupling](https://en.wikipedia.org/wiki/Loose_coupling "Loose coupling"), high [cohesion](https://en.wikipedia.org/wiki/Cohesion_(computer_science) "Cohesion (computer science)"), [information hiding](https://en.wikipedia.org/wiki/Information_hiding "Information hiding") and [separation of concerns](https://en.wikipedia.org/wiki/Separation_of_concerns "Separation of concerns").

For newly written code to use a piece of existing code, some kind of [interface](https://en.wikipedia.org/wiki/Interface_(computing) "Interface (computing)"), or means of communication, must be defined. These commonly include a "call" or use of a [subroutine](https://en.wikipedia.org/wiki/Subroutine "Subroutine"), [object](https://en.wikipedia.org/wiki/Object_(computer_science) "Object (computer science)"), [class](https://en.wikipedia.org/wiki/Class_(computer_science) "Class (computer science)"), or [prototype](https://en.wikipedia.org/wiki/Prototype-based_programming "Prototype-based programming"). In organizations, such practices are formalized and standardized by [domain engineering](https://en.wikipedia.org/wiki/Domain_engineering "Domain engineering"), also known as [software product line](https://en.wikipedia.org/wiki/Product_Family_Engineering "Product Family Engineering") engineering.

The general practice of using a prior version of an extant program as a starting point for the next version, is also a form of code reuse.

Some so-called code "reuse" involves simply copying some or all of the code from an existing program into a new one. While organizations can realize [time to market](https://en.wikipedia.org/wiki/Time_to_market "Time to market") benefits for a new product with this approach, they can subsequently be saddled with many of the same [code duplication](https://en.wikipedia.org/wiki/Code_duplication "Code duplication") problems caused by [cut and paste programming](https://en.wikipedia.org/wiki/Cut_and_paste_programming "Cut and paste programming").

Many researchers have worked to make reuse faster, easier, more systematic, and an integral part of the normal process of programming. These are some of the main goals behind the invention of [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming"), which became one of the most common forms of formalized reuse. A somewhat later invention is [generic programming](https://en.wikipedia.org/wiki/Generic_programming "Generic programming").

Another, newer means is to use software "[generators](https://en.wikipedia.org/wiki/Source_code_generation "Source code generation")", programs which can create new programs of a certain type, based on a set of parameters that users choose. Fields of study about such systems are [generative programming](https://en.wikipedia.org/wiki/Generative_programming "Generative programming") and [metaprogramming](https://en.wikipedia.org/wiki/Metaprogramming "Metaprogramming").

### Types of reuse
Concerning motivation and driving factors, reuse can be:
- Opportunistic – While getting ready to begin a project, the team realizes that there are existing components that they can reuse.
- Planned – A team strategically designs components so that they'll be reusable in future projects.

Reuse can be categorized further:
- Internal reuse – A team reuses its own components. This may be a business decision, since the team may want to control a component critical to the project.
- External reuse – A team may choose to license a third-party component. Licensing a third-party component typically costs the team 1 to 20 percent of what it would cost to develop internally. The team must also consider the time it takes to find, learn and integrate the component.

Concerning form or structure of reuse, code can be:
- Referenced – The client code contains a reference to reused code, and thus they have distinct life cycles and can have distinct versions.
- Forked – The client code contains a local or private copy of the reused code, and thus they share a single life cycle and a single version.

Fork-reuse is often discouraged because it's a form of code duplication, which requires that every bug is corrected in each copy, and enhancements made to reused code need to be manually merged in every copy or they become out-of-date. However, fork-reuse can have benefits such as isolation, flexibility to change the reused code, easier packaging, deployment and version management.

### Systematic
Systematic software reuse is a strategy for increasing productivity and improving the quality of the software industry. Although it is simple in concept, successful software reuse implementation is difficult in practice. A reason put forward for this is the dependence of software reuse on the context in which it is implemented. Some problematic issues that need to be addressed related to systematic software reuse are:
- a clear and well-defined product vision is an essential foundation to a [software product line](https://en.wikipedia.org/wiki/Software_product_line "Software product line") (SPL).
- an evolutionary implementation strategy would be a more pragmatic strategy for the company.
- there exist a need for continuous management support and leadership to ensure success.
- an appropriate organisational structure is needed to support SPL engineering.
- the change of mindset from a project-centric company to a product-oriented company is essential.

## SOLID Principle
In [software programming](https://en.wikipedia.org/wiki/Software_programming "Software programming"), **SOLID** is a [mnemonic](https://en.wikipedia.org/wiki/Mnemonic "Mnemonic") [acronym](https://en.wikipedia.org/wiki/Acronym "Acronym") for five design principles intended to make [object-oriented](https://en.wikipedia.org/wiki/Object-oriented "Object-oriented") designs more understandable, flexible, and [maintainable](https://en.wikipedia.org/wiki/Software_maintenance "Software maintenance"). Although the SOLID principles apply to any object-oriented design, they can also form a core philosophy for methodologies such as [agile development](https://en.wikipedia.org/wiki/Agile_software_development "Agile software development") or [adaptive software development](https://en.wikipedia.org/wiki/Adaptive_software_development "Adaptive software development").

### Principles
#### Single responsibility principle
[Single-responsibility principle](https://en.wikipedia.org/wiki/Single-responsibility_principle "Single-responsibility principle") (**SRP**) states that "[t]here should never be more than one reason for a [class](https://en.wikipedia.org/wiki/Class_(computer_programming) "Class (computer programming)") to change. In other words, every class should have only one responsibility.

##### Importance
- Maintainability: When classes have a single, well-defined responsibility, they're easier to understand and modify.
- Testability: It's easier to write unit tests for classes with a single focus.
- Flexibility: Changes to one responsibility don't affect unrelated parts of the system.

#### Open–closed principle
[Open–closed principle](https://en.wikipedia.org/wiki/Open%E2%80%93closed_principle "Open–closed principle") (**OCP**) states that "[s]oftware entities ... should be open for extension, but closed for modification.

##### Importance
- Extensibility: New features can be added without modifying existing code.
- Stability: Reduces the risk of introducing bugs when making changes.
- Flexibility: Adapts to changing requirements more easily.

#### Liskov substitution principle
[Liskov substitution principle](https://en.wikipedia.org/wiki/Liskov_substitution_principle "Liskov substitution principle") (**LSP**) states that "[f]unctions that use pointers or references to base classes must be able to use objects of derived classes without knowing it. 

##### Importance
- Polymorphism: Enables the use of polymorphic behavior, making code more flexible and reusable.
- Reliability: Ensures that subclasses adhere to the contract defined by the superclass.
- Predictability: Guarantees that replacing a superclass object with a subclass object won't break the program.[[5]](https://en.wikipedia.org/wiki/SOLID#cite_note-:0-5)

#### Interface segregation principle
[Interface segregation principle](https://en.wikipedia.org/wiki/Interface_segregation_principle "Interface segregation principle") (**ISP**) states that clients should not be forced to depend upon interfaces that they do not use.

##### Importance
- Decoupling: Reduces dependencies between classes, making the code more modular and maintainable.
- Flexibility: Allows for more targeted implementations of interfaces.
- Avoids unnecessary dependencies: Clients don't have to depend on methods they don't use.

#### Dependency inversion principle
[Dependency inversion principle](https://en.wikipedia.org/wiki/Dependency_inversion_principle "Dependency inversion principle") (**DIP**) states to depend upon abstractions, not concretes.

##### Importance
- Loose coupling: Reduces dependencies between modules, making the code more flexible and easier to test.
- Flexibility: Enables changes to implementations without affecting clients.
- Maintainability: Makes code easier to understand and modify.


