## Abstract Data Type
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), an **abstract data type** (**ADT**) is a [mathematical model](https://en.wikipedia.org/wiki/Mathematical_model "Mathematical model") for [data types](https://en.wikipedia.org/wiki/Data_type "Data type"), defined by its behavior ([semantics](https://en.wikipedia.org/wiki/Semantics_(computer_science) "Semantics (computer science)")) from the point of view of a _[user](https://en.wikipedia.org/wiki/User_(computing) "User (computing)")_ of the data, specifically in terms of possible values, possible operations on data of this type, and the behavior of these operations. This mathematical model contrasts with _[data structures](https://en.wikipedia.org/wiki/Data_structure "Data structure")_, which are concrete representations of data, and are the point of view of an implementer, not a user. For example, a [stack](https://en.wikipedia.org/wiki/Stack_(abstract_data_type) "Stack (abstract data type)") has push/pop operations that follow a Last-In-First-Out rule, and can be concretely implemented using either a list or an array. Another example is a [set](https://en.wikipedia.org/wiki/Set_(abstract_data_type) "Set (abstract data type)") which stores values, without any particular [order](https://en.wikipedia.org/wiki/Sequence "Sequence"), and no repeated values. Values themselves are not retrieved from sets; rather, one tests a value for membership to obtain a Boolean "in" or "not in".

ADTs are a theoretical concept, used in formal [semantics](https://en.wikipedia.org/wiki/Semantics_(computer_science) "Semantics (computer science)") and program [verification](https://en.wikipedia.org/wiki/Formal_verification "Formal verification") and, less strictly, in the design and analysis of [algorithms](https://en.wikipedia.org/wiki/Algorithm "Algorithm"), [data structures](https://en.wikipedia.org/wiki/Data_structure "Data structure"), and [software systems](https://en.wikipedia.org/wiki/Software_system "Software system"). Most mainstream computer languages do not directly support formally specifying ADTs. However, various language features correspond to certain aspects of implementing ADTs, and are easily confused with ADTs proper; these include [abstract types](https://en.wikipedia.org/wiki/Abstract_type "Abstract type"), [opaque data types](https://en.wikipedia.org/wiki/Opaque_data_type "Opaque data type"), [protocols](https://en.wikipedia.org/wiki/Protocol_(object-oriented_programming) "Protocol (object-oriented programming)"), and [design by contract](https://en.wikipedia.org/wiki/Design_by_contract "Design by contract"). For example, in [modular programming](https://en.wikipedia.org/wiki/Modular_programming "Modular programming"), the module declares procedures that correspond to the ADT operations, often with [comments](https://en.wikipedia.org/wiki/Comment_(computer_programming) "Comment (computer programming)") that describe the constraints. This [information hiding](https://en.wikipedia.org/wiki/Information_hiding "Information hiding") strategy allows the implementation of the module to be changed without disturbing the [client](https://en.wikipedia.org/wiki/Client_(computing) "Client (computing)") programs, but the module only informally defines an ADT. The notion of abstract data types is related to the concept of [data abstraction](https://en.wikipedia.org/wiki/Data_abstraction "Data abstraction"), important in [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming_language "Object-oriented programming language") and design by contract methodologies for [software engineering](https://en.wikipedia.org/wiki/Software_engineering "Software engineering").

### Definition
Formally, an ADT is analogous to an [algebraic structure](https://en.wikipedia.org/wiki/Algebraic_structure "Algebraic structure") in mathematics, consisting of a domain, a collection of operations, and a set of constraints the operations must satisfy. The domain is often defined implicitly, for example the [free object](https://en.wikipedia.org/wiki/Free_object "Free object") over the set of ADT operations. The [interface](https://en.wikipedia.org/wiki/Interface_(computer_science) "Interface (computer science)") of the ADT typically refers only to the domain and operations, and perhaps some of the constraints on the operations, such as pre-conditions and post-conditions; but not to other constraints, such as relations between the operations, which are considered behavior. There are two main styles of formal specifications for behavior, [axiomatic semantics](https://en.wikipedia.org/wiki/Axiomatic_semantics "Axiomatic semantics") and [operational semantics](https://en.wikipedia.org/wiki/Operational_semantics "Operational semantics").
Despite not being part of the interface, the constraints are still important to the definition of the ADT; for example a [stack](https://en.wikipedia.org/wiki/Stack_(abstract_data_type) "Stack (abstract data type)") and a [queue](https://en.wikipedia.org/wiki/Queue_(abstract_data_type) "Queue (abstract data type)") have similar add element/remove element interfaces, but it is the constraints that distinguish last-in-first-out from first-in-first-out behavior. The constraints do not consist only of equations such as `fetch(store(S,v))=v` but also [logical formulas](https://en.wikipedia.org/wiki/Logical_formula "Logical formula").

### Axiomatic Semantics
In the spirit of [functional programming](https://en.wikipedia.org/wiki/Functional_programming "Functional programming"), each state of an abstract data structure is a separate entity or value. In this view, each operation is modeled as a [mathematical function](https://en.wikipedia.org/wiki/Function_(mathematics) "Function (mathematics)") with no [side effects](https://en.wikipedia.org/wiki/Side_effect_(computer_science) "Side effect (computer science)"). Operations that modify the ADT are modeled as functions that take the old state as an argument and returns the new state as part of the result. The order in which operations are evaluated is immaterial, and the same operation applied to the same arguments (including the same input states) will always return the same results (and output states). The constraints are specified as axioms or algebraic laws that the operations must satisfy.

### Abstract Variable
An abstract variable may be regarded as the simplest non-trivial ADT, with the semantics of an imperative variable. It admits two operations, `fetch` and `store`. Operational definitions are often written in terms of abstract variables. In the axiomatic semantics, letting V![{\displaystyle V}](https://wikimedia.org/api/rest_v1/media/math/render/svg/af0f6064540e84211d0ffe4dac72098adfa52845)
be the type of the abstract variable and X![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab)
be the type of its contents, `fetch` is a function V→X![{\displaystyle V\to X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f3648ec5f0db9175314ac725fc8225e76b4cbbd3)
and `store` is a function of type V→X→V
![{\displaystyle V\to X\to V}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c11372f7c91b3a7718e099f6faf57e26f94a9219)

. The main constraint is that `fetch` always returns the value _x_ used in the most recent `store` operation on the same variable _V_, i.e. `fetch(store(V,x)) = x`. We may also require that `store` overwrites the value fully, `store(store(V,x1),x2) = store(V,x2)`.

In the operational semantics, `fetch`(_V_) is a procedure that returns the current value in the location _V_, and `store`(_V_, _x_) is a procedure with `void` return type that stores the value _x_ in the location _V_. The constraints are described informally as that reads are consistent with writes. As in many programming languages, the operation `store`(_V_, _x_) is often written _V_ ← _x_ (or some similar notation), and `fetch`(_V_) is implied whenever a variable _V_ is used in a context where a value is required. Thus, for example, _V_ ← _V_ + 1 is commonly understood to be a shorthand for `store`(_V_,`fetch`(_V_) + 1).

In this definition, it is implicitly assumed that names are always distinct: storing a value into a variable _U_ has no effect on the state of a distinct variable _V_. To make this assumption explicit, one could add the constraint that:

- if _U_ and _V_ are distinct variables, the sequence { `store`(_U_, _x_); `store`(_V_, _y_) } is equivalent to { `store`(_V_, _y_); `store`(_U_, _x_) }.

This definition does not say anything about the result of evaluating `fetch`(_V_) when _V_ is _un-initialized_, that is, before performing any `store` operation on _V_. Fetching before storing can be disallowed, defined to have a certain result, or left unspecified. There are some algorithms whose efficiency depends on the assumption that such a `fetch` is legal, and returns some arbitrary value in the variable's range.

### Abstract Stack
An abstract [stack](https://en.wikipedia.org/wiki/Stack_(abstract_data_type) "Stack (abstract data type)") is a last-in-first-out structure, It is generally defined by three key operations: `push`, that inserts a data item onto the stack; `pop`, that removes a data item from it; and `peek` or `top`, that accesses a data item on top of the stack without removal. A complete abstract stack definition includes also a [Boolean](https://en.wikipedia.org/wiki/Boolean_value "Boolean value")-valued function `empty`(_S_) and a `create`() operation that returns an initial stack instance.

In the axiomatic semantics, letting S![{\displaystyle S}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4611d85173cd3b508e67077d4a1252c9c05abca2) be the type of stack states and X![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab) be the type of values contained in the stack, these could have the types 

, push:S→X→S![{\displaystyle push:S\to X\to S}](https://wikimedia.org/api/rest_v1/media/math/render/svg/264a74682516fe1118910da1dfe374114c3513c1), pop:S→(S,X)![{\displaystyle pop:S\to (S,X)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6853a290c8cf390b74f6bace470eda16a0891f68), top:S→X![{\displaystyle top:S\to X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3122d05e60ae2fe3175ec5ccb79c43bd53cd4da2), create:S![{\displaystyle create:S}](https://wikimedia.org/api/rest_v1/media/math/render/svg/35b7aaea6a6f902de4710f11b434920cc39f5459), and empty:S→B![{\displaystyle empty:S\to \mathbb {B} }](https://wikimedia.org/api/rest_v1/media/math/render/svg/212508dd9d31333da26e28a5f59179fc02e64130)
. In the axiomatic semantics, creating the initial stack is a "trivial" operation, and always returns the same distinguished state. Therefore, it is often designated by a special symbol like [Λ](https://en.wikipedia.org/wiki/Lambda "Lambda") or "()". The `empty` operation predicate can then be written simply as s=Λ![{\displaystyle s=\Lambda }](https://wikimedia.org/api/rest_v1/media/math/render/svg/b29d21306fb07d294239edb60021bcd73c49a673) or s≠Λ![{\displaystyle s\neq \Lambda }](https://wikimedia.org/api/rest_v1/media/math/render/svg/9a618d2ad48121c3b8d17c42526efb370f47ba5b).


The constraints are then `pop(push(S,v))=(S,v)`, `top(push(S,v))=v`, `empty`(`create`) = T (a newly created stack is empty), `empty`(`push`(_S_, _x_)) = F (pushing something into a stack makes it non-empty). These axioms do not define the effect of `top`(_s_) or `pop`(_s_), unless _s_ is a stack state returned by a `push`. Since `push` leaves the stack non-empty, those two operations can be defined to be invalid when _s_ = Λ. From these axioms (and the lack of side effects), it can be deduced that `push`(Λ, _x_) ≠ Λ. Also, `push`(_s_, _x_) = `push`(_t_, _y_) [if and only if](https://en.wikipedia.org/wiki/If_and_only_if "If and only if") _x_ = _y_ and _s_ = _t_.

As in some other branches of mathematics, it is customary to assume also that the stack states are only those whose existence can be proved from the axioms in a finite number of steps. In this case, it means that every stack is a _finite_ sequence of values, that becomes the empty stack (Λ) after a finite number of `pop`s. By themselves, the axioms above do not exclude the existence of infinite stacks (that can be `pop`ped forever, each time yielding a different state) or circular stacks (that return to the same state after a finite number of `pop`s). In particular, they do not exclude states _s_ such that `pop`(_s_) = _s_ or `push`(_s_, _x_) = _s_ for some _x_. However, since one cannot obtain such stack states from the initial stack state with the given operations, they are assumed "not to exist".

In the operational definition of an abstract stack, `push`(_S_, _x_) returns nothing and `pop`(_S_) yields the value as the result but not the new state of the stack. There is then the constraint that, for any value _x_ and any abstract variable _V_, the sequence of operations { `push`(_S_, _x_); _V_ ← `pop`(_S_) } is equivalent to _V_ ← _x_. Since the assignment _V_ ← _x_, by definition, cannot change the state of _S_, this condition implies that _V_ ← `pop`(_S_) restores _S_ to the state it had before the `push`(_S_, _x_). From this condition and from the properties of abstract variables, it follows, for example, that the sequence:

{ `push`(_S_, _x_); `push`(_S_, _y_); _U_ ← `pop`(_S_); `push`(_S_, _z_); _V_ ← `pop`(_S_); _W_ ← `pop`(_S_) }

where _x_, _y_, and _z_ are any values, and _U_, _V_, _W_ are pairwise distinct variables, is equivalent to:

{ _U_ ← _y_; _V_ ← _z_; _W_ ← _x_ }

Unlike the axiomatic semantics, the operational semantics can suffer from aliasing. Here it is implicitly assumed that operations on a stack instance do not modify the state of any other ADT instance, including other stacks; that is:

- For any values _x_, _y_, and any distinct stacks _S_ and _T_, the sequence { `push`(_S_, _x_); `push`(_T_, _y_) } is equivalent to { `push`(_T_, _y_); `push`(_S_, _x_) }.

### Common ADTs
Some common ADTs, which have proved useful in a great variety of applications, are

- [Collection](https://en.wikipedia.org/wiki/Collection_(abstract_data_type) "Collection (abstract data type)")
- [Container](https://en.wikipedia.org/wiki/Container_(abstract_data_type) "Container (abstract data type)")
- [List](https://en.wikipedia.org/wiki/List_(abstract_data_type) "List (abstract data type)")
- [String](https://en.wikipedia.org/wiki/String_(computer_science) "String (computer science)")
- [Set](https://en.wikipedia.org/wiki/Set_(abstract_data_type) "Set (abstract data type)")
- [Multiset](https://en.wikipedia.org/wiki/Multiset "Multiset")
- [Map](https://en.wikipedia.org/wiki/Associative_array "Associative array")
- [Multimap](https://en.wikipedia.org/wiki/Multimap "Multimap")
- [Graph](https://en.wikipedia.org/wiki/Graph_(abstract_data_type) "Graph (abstract data type)")
- [Tree](https://en.wikipedia.org/wiki/Tree_(data_structure) "Tree (data structure)")
- [Stack](https://en.wikipedia.org/wiki/Stack_(abstract_data_type) "Stack (abstract data type)")
- [Queue](https://en.wikipedia.org/wiki/Queue_(abstract_data_type) "Queue (abstract data type)")
- [Priority queue](https://en.wikipedia.org/wiki/Priority_queue "Priority queue")
- [Double-ended queue](https://en.wikipedia.org/wiki/Double-ended_queue "Double-ended queue")
- [Double-ended priority queue](https://en.wikipedia.org/wiki/Double-ended_priority_queue "Double-ended priority queue")

Each of these ADTs may be defined in many ways and variants, not necessarily equivalent. For example, an abstract stack may or may not have a `count` operation that tells how many items have been pushed and not yet popped. This choice makes a difference not only for its clients but also for the implementation.


## Abstract Type
In [programming languages](https://en.wikipedia.org/wiki/Programming_languages "Programming languages"), an **abstract type** (also known as **existential types**) is a [type](https://en.wikipedia.org/wiki/Type_(computer_science) "Type (computer science)") in a [nominative type system](https://en.wikipedia.org/wiki/Nominative_type_system "Nominative type system") that cannot be [instantiated](https://en.wikipedia.org/wiki/Instance_(computer_science) "Instance (computer science)") directly; by contrast, a **concrete type** _can_ be instantiated directly. Instantiation of an abstract type can occur only indirectly, via a concrete [_subtype_](https://en.wikipedia.org/wiki/Subtyping "Subtyping").

An abstract type may provide no implementation, or an incomplete implementation. In some languages, abstract types with no implementation (rather than an incomplete implementation) are known as _[protocols](https://en.wikipedia.org/wiki/Protocol_(object-oriented_programming) "Protocol (object-oriented programming)")_, _interfaces_, _signatures_, or _class types_. In [class-based](https://en.wikipedia.org/wiki/Class-based_programming "Class-based programming") [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming"), abstract types are implemented as _[abstract classes](https://en.wikipedia.org/wiki/Abstract_class "Abstract class")_ (also known as _[abstract base classes](https://en.wikipedia.org/wiki/Abstract_base_class "Abstract base class")_), and concrete types as _[concrete classes](https://en.wikipedia.org/wiki/Concrete_class "Concrete class")_. In [generic programming](https://en.wikipedia.org/wiki/Generic_programming "Generic programming"), the analogous notion is a [_concept_](https://en.wikipedia.org/wiki/Concept_(generic_programming) "Concept (generic programming)"), which similarly specifies syntax and semantics, but does not require a sub-type relationship: two unrelated types may satisfy the same concept.

Often, abstract types will have one or more implementations provided separately, for example, in the form of concrete sub-types that _can_ be instantiated. In object-oriented programming, an abstract class may include _[abstract methods](https://en.wikipedia.org/wiki/Abstract_method "Abstract method")_ or _abstract properties_ that are shared by its sub-classes. Other names for language features that are (or may be) used to implement abstract types include _[traits](https://en.wikipedia.org/wiki/Trait_(computer_science) "Trait (computer science)")_, _[mixins](https://en.wikipedia.org/wiki/Mixin "Mixin")_, _flavors_, _roles_, or _type classes_.

Abstract types may also include any number of non-abstract methods and properties, such as when implementing the [Template Method Pattern](https://en.wikipedia.org/wiki/Template_method_pattern "Template method pattern") which uses a mixture of invariant methods with fixed implementations and [hook methods](https://en.wikipedia.org/wiki/Hooking "Hooking") which can be overridden in concrete sub-classes to provide customised logic.

## Stack (Abstract Data Type)
In computer science, a **stack** is an abstract data type that serves as a collection of elements with two main operations:

- **Push**: which adds an element to the collection, and
- **Pop**: which removes the most recently added element.

Additionally, a peek operation can, without modifying the stack, return the value of the last element added. The name _stack_ is an analogy to a set of physical items stacked one atop another, such as a stack of plates.

The order in which an element added to or removed from a stack is described as **last in, first out**, referred to by the acronym **LIFO** As with a stack of physical objects, this structure makes it easy to take an item off the top of the stack, but accessing a data deeper in the stack may require removing multiple other items first.

Considered a sequential collection, a stack has one end which is the only position at which the push and pop operations may occur, the _top_ of the stack, and is fixed at the other end, the _bottom_. A stack may be implemented as, for example, a singly linked list with a pointer to the top element.

A stack may be implemented to have a bounded capacity. If the stack is full and does not contain enough space to accept another element, the stack is in a state of stack overflow.

A stack is needed to implement depth-first search.

![[Pasted image 20241012102441.png]]


### Hardware Stack
A common use of stacks at the architecture level is as a means of allocating and accessing memory.

#### Basic Architecture Of A Stack
A typical stack is an area of computer memory with a fixed origin and a variable size. Initially the size of the stack is zero. A stack pointer (usually in the form of a processor register "Processor register")) points to the most recently referenced location on the stack; when the stack has a size of zero, the stack pointer points to the origin of the stack.

The two operations applicable to all stacks are:

- A _push_ operation: the address in the stack pointer is adjusted by the size of the data item and a data item is written at the location to which the stack pointer points.
- A _pop_ or _pull_ operation: a data item at the current location to which the stack pointer points is read, and the stack pointer is moved by a distance corresponding to the size of that data item.

There are many variations on the basic principle of stack operations. Every stack has a fixed location in memory at which it begins. As data items are added to the stack, the stack pointer is displaced to indicate the current extent of the stack, which expands away from the origin.

Stack pointers may point to the origin of a stack or to a limited range of addresses above or below the origin (depending on the direction in which the stack grows); however, the stack pointer cannot cross the origin of the stack. In other words, if the origin of the stack is at address 1000 and the stack grows downwards (towards addresses 999, 998, and so on), the stack pointer must never be incremented beyond 1000 (to 1001 or beyond). If a pop operation on the stack causes the stack pointer to move past the origin of the stack, a _stack underflow_ occurs. If a push operation causes the stack pointer to increment or decrement beyond the maximum extent of the stack, a _stack overflow_ occurs.

Some environments that rely heavily on stacks may provide additional operations, for example:

- _Duplicate_: the top item is popped and then pushed twice, such that two copies of the former top item now lie at the top.
- _Peek_: the topmost item is inspected (or returned), but the stack pointer and stack size does not change (meaning the item remains on the stack). This can also be called the _top_ operation.
- _Swap_ or _exchange_: the two topmost items on the stack exchange places.
- _Rotate (or Roll)_: the n topmost items are moved on the stack in a rotating fashion. For example, if _n_ = 3, items 1, 2, and 3 on the stack are moved to positions 2, 3, and 1 on the stack, respectively. Many variants of this operation are possible, with the most common being called _left rotate_ and _right rotate._

Stacks are often visualized growing from the bottom up (like real-world stacks). They may also be visualized growing from left to right, where the top is on the far right, or even growing from top to bottom. The important feature is for the bottom of the stack to be in a fixed position. The illustration in this section is an example of a top-to-bottom growth visualization: the top (28) is the stack "bottom", since the stack "top" (9) is where items are pushed or popped from.

A _right rotate_ will move the first element to the third position, the second to the first and the third to the second. Here are two equivalent visualizations of this process:

```
apple                         banana
banana    ===right rotate==>  cucumber
cucumber                      apple
```

```
cucumber                      apple
banana    ===left rotate==>   cucumber
apple                         banana
```

A stack is usually represented in computers by a block of memory cells, with the "bottom" at a fixed location, and the stack pointer holding the address of the current "top" cell in the stack. The "top" and "bottom" nomenclature is used irrespective of whether the stack actually grows towards higher memory addresses.

Pushing an item on to the stack adjusts the stack pointer by the size of the item (either decrementing or incrementing, depending on the direction in which the stack grows in memory), pointing it to the next cell, and copies the new top item to the stack area. Depending again on the exact implementation, at the end of a push operation, the stack pointer may point to the next unused location in the stack, or it may point to the topmost item in the stack. If the stack points to the current topmost item, the stack pointer will be updated before a new item is pushed onto the stack; if it points to the next available location in the stack, it will be updated _after_ the new item is pushed onto the stack.

Popping the stack is simply the inverse of pushing. The topmost item in the stack is removed and the stack pointer is updated, in the opposite order of that used in the push operation.

## Call Stack
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), a **call stack** is a [stack](https://en.wikipedia.org/wiki/Stack_(abstract_data_type) "Stack (abstract data type)") data structure that stores information about the active [subroutines](https://en.wikipedia.org/wiki/Subroutine "Subroutine") of a [computer program](https://en.wikipedia.org/wiki/Computer_program "Computer program"). This type of stack is also known as an **execution stack**, **program stack**, **control stack**, **run-time stack**, or **machine stack**, and is often shortened to simply the "**stack**". Although maintenance of the call stack is important for the proper functioning of most [software](https://en.wikipedia.org/wiki/Software "Software"), the details are normally hidden and automatic in [high-level programming languages](https://en.wikipedia.org/wiki/High-level_programming_language "High-level programming language"). Many computer [instruction sets](https://en.wikipedia.org/wiki/Instruction_set "Instruction set") provide special instructions for manipulating stacks.

A call stack is used for several related purposes, but the main reason for having one is to keep track of the point to which each active subroutine should return control when it finishes executing. An active subroutine is one that has been called, but is yet to complete execution, after which control should be handed back to the point of call. Such activations of subroutines may be nested to any level (recursive as a special case), hence the stack structure. For example, if a subroutine `DrawSquare` calls a subroutine `DrawLine` from four different places, `DrawLine` must know where to return when its execution completes. To accomplish this, the [address](https://en.wikipedia.org/wiki/Memory_address "Memory address") following the [instruction](https://en.wikipedia.org/wiki/Instruction_(computer_science) "Instruction (computer science)") that jumps to `DrawLine`, the _[return address](https://en.wikipedia.org/wiki/Return_address_(computing) "Return address (computing)")_, is pushed onto the top of the call stack as part of each call.

### Description
Since the call stack is organized as a [stack](https://en.wikipedia.org/wiki/Stack_(abstract_data_type) "Stack (abstract data type)"), the caller pushes the return address onto the stack, and the called subroutine, when it finishes, [pulls or pops](https://en.wikipedia.org/wiki/Pop_(computer_programming) "Pop (computer programming)") the return address off the call stack and transfers control to that address. If a called subroutine calls on yet another subroutine, it will push another return address onto the call stack, and so on, with the information stacking up and unstacking as the program dictates. If the pushing consumes all of the space allocated for the call stack, an error called a [stack overflow](https://en.wikipedia.org/wiki/Stack_overflow "Stack overflow") occurs, generally causing the program to [crash](https://en.wikipedia.org/wiki/Crash_(computing) "Crash (computing)"). Adding a block's or subroutine's entry to the call stack is sometimes called "winding", and removing entries "unwinding".

There is usually exactly one call stack associated with a running program (or more accurately, with each [task](https://en.wikipedia.org/wiki/Task_(computers) "Task (computers)") or [thread](https://en.wikipedia.org/wiki/Thread_(computer_science) "Thread (computer science)") of a [process](https://en.wikipedia.org/wiki/Process_(computing) "Process (computing)")), although additional stacks may be created for [signal](https://en.wikipedia.org/wiki/Signal_(computing) "Signal (computing)") handling or [cooperative multitasking](https://en.wikipedia.org/wiki/Cooperative_multitasking "Cooperative multitasking") (as with [setcontext](https://en.wikipedia.org/wiki/Setcontext "Setcontext")). Since there is only one in this important context, it can be referred to as _the_ stack (implicitly "of the task"); however, in the [Forth programming language](https://en.wikipedia.org/wiki/Forth_programming_language "Forth programming language") the _data stack_ or _parameter stack_ is accessed more explicitly than the call stack and is commonly referred to as _the_ stack (see below).

In [high-level programming languages](https://en.wikipedia.org/wiki/High-level_programming_language "High-level programming language"), the specifics of the call stack are usually hidden from the programmer. They are given access only to a set of functions, and not the memory on the stack itself. This is an example of [abstraction](https://en.wikipedia.org/wiki/Abstraction_(computer_science) "Abstraction (computer science)"). Most [assembly languages](https://en.wikipedia.org/wiki/Assembly_language "Assembly language"), on the other hand, require programmers to be involved in manipulating the stack. The actual details of the stack in a [programming language](https://en.wikipedia.org/wiki/Programming_language "Programming language") depend upon the [compiler](https://en.wikipedia.org/wiki/Compiler "Compiler"), [operating system](https://en.wikipedia.org/wiki/Operating_system "Operating system"), and the available [instruction set](https://en.wikipedia.org/wiki/Instruction_set "Instruction set").

### Functions of the Call Stack
As noted above, the primary purpose of a call stack is to _store the return addresses_. When a subroutine is called, the location (address) of the instruction at which the calling routine can later resume must be saved somewhere. Using a stack to save the return address has important advantages over some alternative [calling conventions](https://en.wikipedia.org/wiki/Calling_convention "Calling convention"), such as saving the return address before the beginning of the called subroutine or in some other fixed location. One is that each task can have its own stack, and thus the subroutine can be [thread-safe](https://en.wikipedia.org/wiki/Thread_safety "Thread safety"), that is, able to be active simultaneously for different tasks doing different things. Another benefit is that by providing [reentrancy](https://en.wikipedia.org/wiki/Reentrancy_(computing) "Reentrancy (computing)"), [recursion](https://en.wikipedia.org/wiki/Recursion_(computer_science) "Recursion (computer science)") is automatically supported. When a function calls itself recursively, a return address needs to be stored for each activation of the function so that it can later be used to return from the function activation. Stack structures provide this capability automatically.

Depending on the language, operating system, and machine environment, a call stack may serve additional purposes, including, for example:

**Local data storage**:
	A subroutine frequently needs memory space for storing the values of [local variables](https://en.wikipedia.org/wiki/Local_variable "Local variable"), the variables that are known only within the active subroutine and do not retain values after it returns. It is often convenient to allocate space for this use by simply moving the top of the stack by enough to provide the space. This is very fast when compared to [dynamic memory allocation](https://en.wikipedia.org/wiki/Dynamic_memory_allocation "Dynamic memory allocation"), which uses the [heap space](https://en.wikipedia.org/wiki/Heap_(programming) "Heap (programming)"). Note that each separate activation of a subroutine gets its own separate space in the stack for locals.

**Parameter passing**:
	Subroutines often require that values for [parameters](https://en.wikipedia.org/wiki/Parameter_(computer_science) "Parameter (computer science)") be supplied to them by the code which calls them, and it is not uncommon that space for these parameters may be laid out in the call stack. Generally if there are only a few small parameters, [processor registers](https://en.wikipedia.org/wiki/Processor_register "Processor register") will be used to pass the values, but if there are more parameters than can be handled this way, memory space will be needed. The call stack works well as a place for these parameters, especially since each call to a subroutine, which will have differing values for parameters, will be given separate space on the call stack for those values. In [object-oriented languages](https://en.wikipedia.org/wiki/Object-oriented_language "Object-oriented language") such as [C++](https://en.wikipedia.org/wiki/C%2B%2B "C++"), the list of parameters may also include the [`this` pointer](https://en.wikipedia.org/wiki/This_(computer_science) "This (computer science)").

**Evaluation stack**
	Operands for arithmetic or logical operations are most often placed into registers and operated on there. However, in some situations the operands may be stacked up to an arbitrary depth, which means something more than registers must be used (this is the case of [register spilling](https://en.wikipedia.org/wiki/Register_allocation#Principle "Register allocation")). The stack of such operands, rather like that in an [RPN calculator](https://en.wikipedia.org/wiki/RPN_calculator "RPN calculator"), is called an evaluation stack, and may occupy space in the call stack.

**Enclosing subroutine context**:
	Some programming languages (e.g., [Pascal](https://en.wikipedia.org/wiki/Pascal_(programming_language) "Pascal (programming language)") and [Ada](https://en.wikipedia.org/wiki/Ada_(programming_language) "Ada (programming language)")) support declaration of [nested subroutines](https://en.wikipedia.org/wiki/Nested_functions "Nested functions"), which are allowed to access the context of their enclosing routines, i.e., the parameters and local variables within the scope of the outer routines. Such static nesting can repeat (a function declared within a function declared within a function…). The implementation must provide a means by which a called function at any given static nesting level can reference the enclosing frame at each enclosing nesting level. This reference is commonly implemented by a pointer to the frame of the most recently activated instance of the enclosing function, called a "downstack link" or "static link", to distinguish it from the "dynamic link" that refers to the immediate caller (which need not be the static parent function).	
	Instead of a static link, the references to the enclosing static frames may be collected into an array of pointers known as a _display_ which is indexed to locate a desired frame. The depth of a routine's lexical nesting is a known constant, so the size of a routine's display is fixed. Also, the number of containing scopes to traverse is known, the index into the display is also fixed. Usually, a routine's display is located in its own stack frame, but the [Burroughs B6500](https://en.wikipedia.org/wiki/Burroughs_large_systems "Burroughs large systems") implemented such a display in hardware which supported up to 32 levels of static nesting.
	The display entries denoting containing scopes are obtained from the appropriate prefix of the caller's display. An inner routine which recurses creates separate call frames for each invocation. In this case, all of the inner routine's static links point to the same outer routine context.

**Enclosed block context**:
	In some languages, e.g., [ALGOL 60](https://en.wikipedia.org/wiki/ALGOL_60 "ALGOL 60"), [PL/I](https://en.wikipedia.org/wiki/PL/I "PL/I"), a block within a procedure may have its own local variables, allocated on block entry and freed on block exit. Similarly, the block may have its own exception handlers, deactivated at block exit.

**Other return state**:
	Beside the return address, in some environments there may be other machine or software states that need to be restored when a subroutine returns. This might include things like privilege level, exception-handling information, arithmetic modes, and so on. If needed, this may be stored in the call stack just as the return address is.
	The typical call stack is used for the return address, locals, and parameters (known as a _call frame_). In some environments there may be more or fewer functions assigned to the call stack. In the [Forth programming language](https://en.wikipedia.org/wiki/Forth_(programming_language) "Forth (programming language)"), for example, ordinarily only the return address, counted loop parameters and indexes, and possibly local variables are stored on the call stack (which in that environment is named the _return stack_), although any data can be temporarily placed there using special return-stack handling code so long as the needs of calls and returns are respected; parameters are ordinarily stored on a separate _data stack_ or _parameter stack_, typically called _the_ stack in Forth terminology even though there is a call stack since it is usually accessed more explicitly. Some Forths also have a third stack for [floating-point](https://en.wikipedia.org/wiki/Floating-point "Floating-point") parameters.

### Structure
![[Pasted image 20241012115007.png]]

A **call stack** is composed of **stack frames** (also called _activation records_ or _activation frames_). These are [machine dependent](https://en.wikipedia.org/wiki/Machine_dependent "Machine dependent") and [ABI](https://en.wikipedia.org/wiki/Application_binary_interface "Application binary interface")-dependent data structures containing subroutine state information. Each stack frame corresponds to a call to a subroutine which has not yet terminated with a return. For example, if a subroutine named `DrawLine` is currently running, having been called by a subroutine `DrawSquare`, the top part of the call stack might be laid out like in the adjacent picture.

A diagram like this can be drawn in either direction as long as the placement of the top, and so direction of stack growth, is understood. Architectures differ as to whether call stacks grow towards higher addresses or towards lower addresses, so the logic of any diagram is not dependent on this addressing choice by convention.

The stack frame at the top of the stack is for the currently executing routine, which can access information within its frame (such as parameters or local variables) in any order. The stack frame usually includes at least the following items (in push order):

- the arguments (parameter values) passed to the routine (if any);
- the return address back to the routine's caller (e.g. in the `DrawLine` stack frame, an address into `DrawSquare`'s code); and
- space for the local variables of the routine (if any).

#### Stack and frame pointers
When stack frame sizes can differ, such as between different functions or between invocations of a particular function, popping a frame off the stack does not constitute a fixed decrement of the **stack pointer**. At function return, the stack pointer is instead restored to the **frame pointer**, the value of the stack pointer just before the function was called. Each stack frame contains a stack pointer to the top of the frame immediately below. The stack pointer is a mutable register shared between all invocations. A frame pointer of a given invocation of a function is a copy of the stack pointer as it was before the function was invoked.

The locations of all other fields in the frame can be defined relative either to the top of the frame, as negative offsets of the stack pointer, or relative to the top of the frame below, as positive offsets of the frame pointer. The location of the frame pointer itself must inherently be defined as a negative offset of the stack pointer.

#### Storing the address to the caller's frame
In most systems a stack frame has a field to contain the previous value of the frame pointer register, the value it had while the caller was executing. For example, the stack frame of `DrawLine` would have a memory location holding the frame pointer value that `DrawSquare` uses (not shown in the diagram above). The value is saved upon entry to the subroutine. Having such a field in a known location in the stack frame enables code to access each frame successively underneath the currently executing routine's frame, and also allows the routine to easily restore the frame pointer to the _caller's_ frame, just before it returns.

#### Lexically nested routines
Programming languages that support [nested subroutines](https://en.wikipedia.org/wiki/Nested_function "Nested function") also have a field in the call frame that points to the stack frame of the _latest_ activation of the procedure that most closely encapsulates the callee, i.e. the immediate _scope_ of the callee. This is called an _access link_ or _static link_ (as it keeps track of static nesting during dynamic and recursive calls) and provides the routine (as well as any other routines it may invoke) access to the local data of its encapsulating routines at every nesting level. Some architectures, compilers, or optimization cases store one link for each enclosing level (not just the immediately enclosing), so that deeply nested routines that access shallow data do not have to traverse several links; this strategy is often called a "display".

Access links can be optimized away when an inner function does not access any (non-constant) local data in the encapsulation, as is the case with pure functions communicating only via arguments and return values, for example. Some historical computers, such as the [Electrologica X8](https://en.wikipedia.org/wiki/Electrologica_X8 "Electrologica X8") and somewhat later the [Burroughs large systems](https://en.wikipedia.org/wiki/Burroughs_large_systems "Burroughs large systems"), had special "display registers" to support nested functions, while compilers for most modern machines (such as the ubiquitous x86) simply reserve a few words on the stack for the pointers, as needed.

#### Overlap
For some purposes, the stack frame of a subroutine and that of its caller can be considered to overlap, the overlap consisting of the area where the parameters are passed from the caller to the callee. In some environments, the caller pushes each argument onto the stack, thus extending its stack frame, then invokes the callee. In other environments, the caller has a preallocated area at the top of its stack frame to hold the arguments it supplies to other subroutines it calls. This area is sometimes termed the _outgoing arguments area_ or _callout area_. Under this approach, the size of the area is calculated by the compiler to be the largest needed by any called subroutine.

## Processor Register
A **processor register** is a quickly accessible location available to a computer's [processor](https://en.wikipedia.org/wiki/Processor_(computing) "Processor (computing)"). Registers usually consist of a small amount of fast [storage](https://en.wikipedia.org/wiki/Computer_storage "Computer storage"), although some registers have specific hardware functions, and may be read-only or write-only. In [computer architecture](https://en.wikipedia.org/wiki/Computer_architecture "Computer architecture"), registers are typically addressed by mechanisms other than [main memory](https://en.wikipedia.org/wiki/Main_memory "Main memory"), but may in some cases be assigned a [memory address](https://en.wikipedia.org/wiki/Memory_address "Memory address") e.g. DEC [PDP-10](https://en.wikipedia.org/wiki/PDP-10 "PDP-10"), [ICT 1900](https://en.wikipedia.org/wiki/ICT_1900_series "ICT 1900 series").

Almost all computers, whether [load/store architecture](https://en.wikipedia.org/wiki/Load/store_architecture "Load/store architecture") or not, load items of data from a larger memory into registers where they are used for [arithmetic operations](https://en.wikipedia.org/wiki/Arithmetic_operation "Arithmetic operation"), [bitwise operations](https://en.wikipedia.org/wiki/Bitwise_operation "Bitwise operation"), and other operations, and are manipulated or tested by [machine instructions](https://en.wikipedia.org/wiki/Machine_instruction "Machine instruction"). Manipulated items are then often stored back to main memory, either by the same instruction or by a subsequent one. Modern processors use either [static](https://en.wikipedia.org/wiki/Static_random-access_memory "Static random-access memory") or [dynamic](https://en.wikipedia.org/wiki/Dynamic_random-access_memory "Dynamic random-access memory") [RAM](https://en.wikipedia.org/wiki/Random-access_memory "Random-access memory") as main memory, with the latter usually accessed via one or more [cache levels](https://en.wikipedia.org/wiki/CPU_cache#Multi-level_caches "CPU cache").

Processor registers are normally at the top of the [memory hierarchy](https://en.wikipedia.org/wiki/Memory_hierarchy "Memory hierarchy"), and provide the fastest way to access data. The term normally refers only to the group of registers that are directly encoded as part of an instruction, as defined by the [instruction set](https://en.wikipedia.org/wiki/Instruction_set "Instruction set"). However, modern high-performance CPUs often have duplicates of these "architectural registers" in order to improve performance via [register renaming](https://en.wikipedia.org/wiki/Register_renaming "Register renaming"), allowing [parallel](https://en.wikipedia.org/wiki/Instruction-level_parallelism "Instruction-level parallelism") and [speculative execution](https://en.wikipedia.org/wiki/Speculative_execution "Speculative execution"). Modern [x86](https://en.wikipedia.org/wiki/X86 "X86") design acquired these techniques around 1995 with the releases of [Pentium Pro](https://en.wikipedia.org/wiki/Pentium_Pro "Pentium Pro"), [Cyrix 6x86](https://en.wikipedia.org/wiki/Cyrix_6x86 "Cyrix 6x86"), [Nx586](https://en.wikipedia.org/wiki/Nx586 "Nx586"), and [AMD K5](https://en.wikipedia.org/wiki/AMD_K5 "AMD K5").

When a [computer program](https://en.wikipedia.org/wiki/Computer_program "Computer program") accesses the same data repeatedly, this is called [locality of reference](https://en.wikipedia.org/wiki/Locality_of_reference "Locality of reference"). Holding frequently used values in registers can be critical to a program's performance. [Register allocation](https://en.wikipedia.org/wiki/Register_allocation "Register allocation") is performed either by a [compiler](https://en.wikipedia.org/wiki/Compiler "Compiler") in the [code generation](https://en.wikipedia.org/wiki/Code_generation_(compiler) "Code generation (compiler)") phase, or manually by an [assembly language](https://en.wikipedia.org/wiki/Assembly_language "Assembly language") programmer.

### Size
Registers are normally measured by the number of [bits](https://en.wikipedia.org/wiki/Bit "Bit") they can hold, for example, an "[8-bit](https://en.wikipedia.org/wiki/8-bit "8-bit") register", "[32-bit](https://en.wikipedia.org/wiki/32-bit "32-bit") register", "[64-bit](https://en.wikipedia.org/wiki/64-bit "64-bit") register", or even more. In some [instruction sets](https://en.wikipedia.org/wiki/Instruction_set_architecture "Instruction set architecture"), the registers can operate in various modes, breaking down their storage memory into smaller parts (32-bit into four 8-bit ones, for instance) to which multiple data (vector, or [one-dimensional array](https://en.wikipedia.org/wiki/One-dimensional_array "One-dimensional array") of data) can be loaded and operated upon at the same time. Typically it is implemented by adding extra registers that map their memory into a larger register. Processors that have the ability to execute single instructions on multiple data are called [vector processors](https://en.wikipedia.org/wiki/Vector_processor "Vector processor").

### Types
A processor often contains several kinds of registers, which can be classified according to the types of values they can store or the instructions that operate on them:

- _**User-accessible registers**_ can be read or written by machine instructions. The most common division of user-accessible registers is a division into data registers and address registers.
    - _**[Control registers](https://en.wikipedia.org/wiki/Control_register "Control register")**_
    - _**Data registers**_ can hold [numeric data values](https://en.wikipedia.org/wiki/Data_(computer_science) "Data (computer science)") such as [integers](https://en.wikipedia.org/wiki/Integer_(computer_science) "Integer (computer science)") and, in some architectures, [floating-point numbers](https://en.wikipedia.org/wiki/Floating-point_numbers "Floating-point numbers"), as well as [characters](https://en.wikipedia.org/wiki/Character_(computing) "Character (computing)"), small [bit rate arrays](https://en.wikipedia.org/w/index.php?title=Bit_rate_array&action=edit&redlink=1 "Bit rate array (page does not exist)") and other data. In some older architectures, such as the [IBM 704](https://en.wikipedia.org/wiki/IBM_704 "IBM 704"), the [IBM 709](https://en.wikipedia.org/wiki/IBM_709 "IBM 709") and successors, the [PDP-1](https://en.wikipedia.org/wiki/PDP-1 "PDP-1"), the [PDP-4](https://en.wikipedia.org/wiki/PDP-4 "PDP-4")/[PDP-7](https://en.wikipedia.org/wiki/PDP-7 "PDP-7")/[PDP-9](https://en.wikipedia.org/wiki/PDP-9 "PDP-9")/[PDP-15](https://en.wikipedia.org/wiki/PDP-15 "PDP-15"), the [PDP-5](https://en.wikipedia.org/wiki/PDP-5 "PDP-5")/[PDP-8](https://en.wikipedia.org/wiki/PDP-8 "PDP-8"), and the [HP 2100](https://en.wikipedia.org/wiki/HP_2100 "HP 2100"), a special data register known as the [accumulator](https://en.wikipedia.org/wiki/Accumulator_(computing) "Accumulator (computing)") is used implicitly for many operations.
    - _**Address registers**_ hold [addresses](https://en.wikipedia.org/wiki/Memory_address "Memory address") and are used by instructions that indirectly access [primary memory](https://en.wikipedia.org/wiki/Primary_memory "Primary memory").
        - Some processors contain registers that may only be used to hold an _address_ or only to hold _numeric values_ (in some cases used as an [index register](https://en.wikipedia.org/wiki/Index_register "Index register") whose value is added as an offset from some address); others allow registers to hold either kind of quantity. A wide variety of possible [addressing modes](https://en.wikipedia.org/wiki/Addressing_mode "Addressing mode"), used to specify the effective address of an operand, exist.
        - The _**[stack pointer](https://en.wikipedia.org/wiki/Stack_pointer "Stack pointer")**_ is used to manage the [run-time stack](https://en.wikipedia.org/wiki/Run-time_stack "Run-time stack"). Rarely, other [data stacks](https://en.wikipedia.org/wiki/Stack_(abstract_data_type) "Stack (abstract data type)") are addressed by dedicated address registers (see [stack machine](https://en.wikipedia.org/wiki/Stack_machine "Stack machine")).
    - _**General-purpose registers**_ (_GPR_s) can store both data and addresses, i.e., they are combined data/address registers; in some architectures, the [register file](https://en.wikipedia.org/wiki/Register_file "Register file") is _unified_ so that the GPRs can store floating-point numbers as well.
    - _**[Status registers](https://en.wikipedia.org/wiki/Status_register "Status register")**_ hold [truth values](https://en.wikipedia.org/wiki/Truth_value "Truth value") often used to determine whether some instruction should or should not be executed.
    - _**Floating-point registers**_ (_FPR_s) store floating-point numbers in many architectures.
    - _**[Constant](https://en.wikipedia.org/wiki/Constant_(computer_programming) "Constant (computer programming)") registers**_ hold read-only values such as zero, one, or [pi](https://en.wikipedia.org/wiki/Pi "Pi").
    - _**Vector registers**_ hold data for [vector processing](https://en.wikipedia.org/wiki/Vector_processing "Vector processing") done by [SIMD](https://en.wikipedia.org/wiki/Single_instruction,_multiple_data "Single instruction, multiple data") instructions (Single Instruction, Multiple Data).
    - _**Special-purpose registers**_ (_SPR_s, or _**[Special Function Registers](https://en.wikipedia.org/wiki/Special_Function_Register "Special Function Register")**_) hold some elements of the [program state](https://en.wikipedia.org/wiki/Program_state "Program state"); they usually include the [program counter](https://en.wikipedia.org/wiki/Program_counter "Program counter"), also called the instruction pointer, and the [status register](https://en.wikipedia.org/wiki/Status_register "Status register"); the program counter and status register might be combined in a [program status word](https://en.wikipedia.org/wiki/Program_status_word "Program status word") (PSW) register. The aforementioned stack pointer is sometimes also included in this group. Embedded microprocessors can also have registers corresponding to specialized hardware elements.
    - _**[Model-specific registers](https://en.wikipedia.org/wiki/Model-specific_register "Model-specific register")**_ (also called _machine-specific registers_) store data and settings related to the processor itself. Because their meanings are attached to the design of a specific processor, they are not expected to remain standard between processor generations.
    - _**[Memory type range registers](https://en.wikipedia.org/wiki/Memory_type_range_register "Memory type range register")**_ (_MTRR_s)
- _**Internal registers**_ are not accessible by instructions and are used internally for processor operations.
    - The _**[instruction register](https://en.wikipedia.org/wiki/Instruction_register "Instruction register")**_ holds the instruction currently being executed.
    - Registers related to fetching information from [RAM](https://en.wikipedia.org/wiki/Random-access_memory "Random-access memory"), a collection of storage registers located on separate chips from the CPU:
        - _**[Memory buffer register](https://en.wikipedia.org/wiki/Memory_buffer_register "Memory buffer register")**_ (_MBR_), also known as _memory data register_ (_MDR_)
        - _**[Memory address register](https://en.wikipedia.org/wiki/Memory_address_register "Memory address register")**_ (_MAR_)
- _**Architectural registers**_ are the registers visible to software and are defined by an architecture. They may not correspond to the physical hardware if [register renaming](https://en.wikipedia.org/wiki/Register_renaming "Register renaming") is being performed by the underlying hardware.

**[Hardware registers](https://en.wikipedia.org/wiki/Hardware_register "Hardware register")** are similar, but occur outside CPUs.

In some architectures (such as [SPARC](https://en.wikipedia.org/wiki/SPARC "SPARC") and [MIPS](https://en.wikipedia.org/wiki/MIPS_architecture "MIPS architecture")), the first or last register in the integer [register file](https://en.wikipedia.org/wiki/Register_file "Register file") is a _[pseudo-register](https://en.wikipedia.org/wiki/Zero_register "Zero register")_ in that it is hardwired to always return zero when read (mostly to simplify indexing modes), and it cannot be overwritten. In [Alpha](https://en.wikipedia.org/wiki/DEC_Alpha "DEC Alpha"), this is also done for the floating-point register file. As a result of this, register files are commonly quoted as having one register more than how many of them are actually usable; for example, 32 registers are quoted when only 31 of them fit within the above definition of a register.

## Hardware Register
In [digital electronics](https://en.wikipedia.org/wiki/Digital_electronics "Digital electronics"), especially [computing](https://en.wikipedia.org/wiki/Computing "Computing"), **hardware registers** are circuits typically composed of [flip-flops](https://en.wikipedia.org/wiki/Flip-flop_(electronics) "Flip-flop (electronics)"), often with many characteristics similar to [memory](https://en.wikipedia.org/wiki/Semiconductor_memory "Semiconductor memory"), such as:
- The ability to read or write multiple [bits](https://en.wikipedia.org/wiki/Bit_(computing) "Bit (computing)") at a time, and
- Using an [address](https://en.wikipedia.org/wiki/Address_(computing) "Address (computing)") to select a particular register in a manner similar to a [memory address](https://en.wikipedia.org/wiki/Memory_address "Memory address").

Their distinguishing characteristic, however, is that they also have special hardware-related functions beyond those of ordinary memory. So, depending on the point of view, hardware registers are like memory with additional hardware-related functions; or, memory circuits are like hardware registers that just store data.

Hardware registers are used in the [interface](https://en.wikipedia.org/wiki/Interface_(computing) "Interface (computing)") between [software](https://en.wikipedia.org/wiki/Software "Software") and [peripherals](https://en.wikipedia.org/wiki/Peripherals "Peripherals"). Software writes them to send information to the device, and reads them to get information from the device. Some hardware devices also include registers that are not visible to software, for their internal use.

Depending on their complexity, modern hardware devices can have many registers. Standard [integrated circuits](https://en.wikipedia.org/wiki/Integrated_circuits "Integrated circuits") typically document their externally-exposed registers as part of their [electronic component](https://en.wikipedia.org/wiki/Electronic_component "Electronic component") [datasheet](https://en.wikipedia.org/wiki/Datasheet "Datasheet").

### Functionality
Typical uses of hardware registers include:
- _configuration_ and start-up of certain features, especially during initialization
- _buffer storage_ e.g. video memory for [graphics cards](https://en.wikipedia.org/wiki/Graphics_card "Graphics card")
- [input/output](https://en.wikipedia.org/wiki/Input/output "Input/output") (I/O) of different kinds
- _status reporting_ such as whether a certain event has occurred in the hardware unit, for example a modem status register or a line status register.

Reading a hardware register in "peripheral units" — [computer hardware](https://en.wikipedia.org/wiki/Computer_hardware "Computer hardware") outside the CPU — involves accessing its [memory-mapped I/O](https://en.wikipedia.org/wiki/Memory-mapped_I/O "Memory-mapped I/O") address or [port-mapped I/O](https://en.wikipedia.org/wiki/Port-mapped_I/O "Port-mapped I/O") address with a "load" or "store" instruction, issued by the processor. Hardware registers are addressed in words, but sometimes only use a few [bits](https://en.wikipedia.org/wiki/Bit "Bit") of the word read in to, or written out to the register.

Commercial design tools simplify and automate memory-mapped register specification and code generation for [hardware](https://en.wikipedia.org/wiki/Hardware_description_language "Hardware description language"), [firmware](https://en.wikipedia.org/wiki/Firmware "Firmware"), [hardware verification](https://en.wikipedia.org/wiki/Hardware_Verification_Language "Hardware Verification Language"), testing and documentation.

Registers can be read/write, read-only or write-only.

[Write-only registers](https://en.wikipedia.org/wiki/Write-only_memory_(engineering) "Write-only memory (engineering)") are generally avoided. They are suitable for registers that cause a transient action when written but store no persistent data to be read, such as a "reset a peripheral" register. They may be the only option in designs that cannot afford gates for the relatively large logic circuit and signal routing needed for register data readback, such as the [Atari 2600](https://en.wikipedia.org/wiki/Atari_2600 "Atari 2600") games console's [TIA](https://en.wikipedia.org/wiki/Television_Interface_Adaptor "Television Interface Adaptor") chip. However, write-only registers make debugging more difficult and lead to the [read-modify-write](https://en.wikipedia.org/wiki/Read-modify-write "Read-modify-write") problem so read/write registers are preferred. On PCs, write-only registers made it difficult for the [Advanced Configuration and Power Interface](https://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface "Advanced Configuration and Power Interface") (ACPI) to determine the device's state when entering [sleep mode](https://en.wikipedia.org/wiki/Sleep_mode "Sleep mode") in order to restore that state when exiting sleep mode.

## Stack Register
A **stack register** is a computer central [processor register](https://en.wikipedia.org/wiki/Processor_register "Processor register") whose purpose is to keep track of a [call stack](https://en.wikipedia.org/wiki/Call_stack "Call stack"). On an [accumulator-based architecture](https://en.wikipedia.org/wiki/Accumulator-based_architecture "Accumulator-based architecture") machine, this may be a dedicated register. On a machine with multiple [general-purpose registers](https://en.wikipedia.org/wiki/General-purpose_registers "General-purpose registers"), it may be a register that is reserved by convention, such as on the [IBM System/360](https://en.wikipedia.org/wiki/IBM_System/360 "IBM System/360") through [z/Architecture](https://en.wikipedia.org/wiki/Z/Architecture "Z/Architecture") architecture and [RISC](https://en.wikipedia.org/wiki/RISC "RISC") architectures, or it may be a register that procedure call and return instructions are hardwired to use, such as on the [PDP-11](https://en.wikipedia.org/wiki/PDP-11 "PDP-11"), [VAX](https://en.wikipedia.org/wiki/VAX "VAX"), and [Intel x86](https://en.wikipedia.org/wiki/Intel_x86 "Intel x86") architectures. Some designs such as the [Data General Eclipse](https://en.wikipedia.org/wiki/Data_General_Eclipse "Data General Eclipse") had no dedicated register, but used a reserved hardware memory address for this function.

Machines before the late 1960s—such as the [PDP-8](https://en.wikipedia.org/wiki/PDP-8 "PDP-8") and [HP 2100](https://en.wikipedia.org/wiki/HP_2100 "HP 2100")—did not have compilers which supported [recursion](https://en.wikipedia.org/wiki/Recursion_(computer_science) "Recursion (computer science)"). Their subroutine instructions typically would save the current location in the jump address, and then set the program counter to the _next_ address. While this is simpler than maintaining a stack, since there is only one return location per subroutine code section, there cannot be recursion without considerable effort on the part of the programmer.

A [stack machine](https://en.wikipedia.org/wiki/Stack_machine "Stack machine") has 2 or more stack registers — one of them keeps track of a [call stack](https://en.wikipedia.org/wiki/Call_stack "Call stack"), the other(s) keep track of other [stack](https://en.wikipedia.org/wiki/Stack_(data_structure) "Stack (data structure)")(s).

### Stack registers in x86
In [8086](https://en.wikipedia.org/wiki/8086 "8086"), the main stack register is called "stack pointer" (SP). The stack segment register (SS) is usually used to store information about the [memory segment](https://en.wikipedia.org/wiki/Memory_segment "Memory segment") that stores the [call stack](https://en.wikipedia.org/wiki/Call_stack "Call stack") of currently executed program. SP points to current stack top. By default, the stack grows downward in memory, so newer values are placed at lower memory addresses. To save a value to the stack, the `PUSH` instruction is used. To retrieve a value from the stack, the `POP` instruction is used.

**Example**: Assuming that SS = 1000h and SP = 0xF820. This means that current stack top is the physical address 0x1F820 (this is due to [memory segmentation in 8086](https://en.wikipedia.org/wiki/Intel_8086#Segmentation "Intel 8086")). The next two machine instructions of the program are:

```
PUSH AX
PUSH BX
```

- These first instruction shall push the value stored in AX (16-bit register) to the stack. This is done by subtracting a value of 2 (2 bytes) from SP.
- The new value of SP becomes 0xF81E. The CPU then copies the value of AX to the memory word whose physical address is 0x1F81E.
- When "PUSH BX" is executed, SP is set to 0xF81C and BX is copied to 0x1F81C.

This illustrates how PUSH works. Usually, the running program pushes registers to the stack to make use of the registers for other purposes, like to call a routine that may change the current values of registers. To restore the values stored at the stack, the program shall contain machine instructions like this:

```
POP BX
POP AX
```

- `POP BX` copies the word at 0x1F81C (which is the old value of BX) to BX, then increases SP by 2. SP now is 0xF81E.
- `POP AX` copies the word at 0x1F81E to AX, then sets SP to 0xF820.

### Stack engine
Simpler processors store the stack pointer in a regular [hardware register](https://en.wikipedia.org/wiki/Hardware_register "Hardware register") and use the [arithmetic logic unit](https://en.wikipedia.org/wiki/Arithmetic_logic_unit "Arithmetic logic unit") (ALU) to manipulate its value. Typically push and pop are translated into multiple [micro-ops](https://en.wikipedia.org/wiki/Micro-op "Micro-op"), to separately add/subtract the stack pointer, and perform the load/store in memory.

Newer processors contain a dedicated **stack engine** to optimize stack operations. [Pentium M](https://en.wikipedia.org/wiki/Pentium_M "Pentium M") was the first x86 processor to introduce a stack engine. In its implementation, the stack pointer is split among two registers: ESPO, which is a 32-bit register, and ESPd, an 8-bit delta value that is updated directly by stack operations. PUSH, POP, CALL and RET opcodes operate directly with the ESPd register. If ESPd is near overflow or the ESP register is referenced from other instructions (when ESPd ≠ 0), a synchronisation micro-op is inserted that updates the ESPO using the ALU and resets ESPd to 0. This design has remained largely unmodified in later Intel processors, although ESPO has been expanded to 64 bits.

A stack engine similar to Intel's was also adopted in the [AMD K8](https://en.wikipedia.org/wiki/AMD_K8 "AMD K8") microarchitecture. In [Bulldozer](https://en.wikipedia.org/wiki/Bulldozer_(microarchitecture) "Bulldozer (microarchitecture)"), the need for synchronization micro-ops was removed, but the internal design of the stack engine is not known.

## Function
In [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"), a **function** (also **procedure**, **method**, **subroutine**, **routine**, or **subprogram**) is a **callable unit** of [software logic](https://en.wikipedia.org/wiki/Software_logic "Software logic") that has a well-defined [interface](https://en.wikipedia.org/wiki/Interface_(computing) "Interface (computing)") and behavior and can be invoked multiple times.

Callable units provide a powerful programming tool. The primary purpose is to allow for the decomposition of a large and/or complicated problem into chunks that have relatively low [cognitive load](https://en.wikipedia.org/wiki/Cognitive_load "Cognitive load") and to assign the chunks meaningful names (unless they are anonymous). Judicious application can reduce the cost of developing and maintaining software, while increasing its quality and reliability.

Callable units are present at multiple levels of [abstraction](https://en.wikipedia.org/wiki/Abstraction "Abstraction") in the programming environment. For example, a [programmer](https://en.wikipedia.org/wiki/Programmer "Programmer") may write a function in [source code](https://en.wikipedia.org/wiki/Source_code "Source code") that is compiled to machine code that implements similar [semantics](https://en.wikipedia.org/wiki/Semantics "Semantics"). There is a callable unit in the source code and an associated one in the machine code, but they are different kinds of callable units – with different implications and features.

### Terminology
The meaning of each callable term (function, procedure, method, ...) is, in fact, different. They are not [synonymous](https://en.wikipedia.org/wiki/Synonymous "Synonymous"). Nevertheless, they each add a capability to programming that has commonality.

The term used tends to reflect the context in which it is used – usually based on the language being used. For example:

- _Subprogram_, _routine_ and _subroutine_ were more commonly used in the past but are less common today

- _Routine_ and _subroutine_ have essentially the same meaning but describe a hierarchical relationship, much like how a subdirectory is structurally subordinate to its parent [directory](https://en.wikipedia.org/wiki/Directory_(computing) "Directory (computing)"); _program_ and _subprogram_ are similarly related

- Some consider _function_ to imply a [mathematical function](https://en.wikipedia.org/wiki/Function_(mathematics) "Function (mathematics)"), having no side-effects, but in many contexts _function_ refers to any callable

- In the context of [Visual Basic](https://en.wikipedia.org/wiki/Visual_Basic "Visual Basic") and [Ada](https://en.wikipedia.org/wiki/Ada_(programming_language) "Ada (programming language)"), `Sub`, short for _subroutine_ or _subprocedure_, is the name of a callable that does not return a value whereas a `Function` does return a value

- [Object-oriented](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming") languages such as [C#](https://en.wikipedia.org/wiki/C_Sharp_(programming_language) "C Sharp (programming language)") and [Java](https://en.wikipedia.org/wiki/Java_(programming_language) "Java (programming language)") use the term _[method](https://en.wikipedia.org/wiki/Method_(computer_programming) "Method (computer programming)")_ to refer to a member function of an [object](https://en.wikipedia.org/wiki/Object_(computer_science) "Object (computer science)")

### Features
In general, a callable unit is a list of instructions that, starting at the first instruction, executes sequentially except as directed via its internal logic. It can be invoked (called) many times during the [execution](https://en.wikipedia.org/wiki/Execution_(computing) "Execution (computing)") of a program. Execution continues at the next instruction after the call instruction when it [returns](https://en.wikipedia.org/wiki/Return_statement "Return statement") control.

### Implementations
The features of [implementations](https://en.wikipedia.org/wiki/Implementation "Implementation") of callable units evolved over time and varies by context. This section describes features of the various common implementations.

#### General characteristics
Most modern programming languages provide features to define and call functions, including [syntax](https://en.wikipedia.org/wiki/Syntax_(programming_languages) "Syntax (programming languages)") for accessing such features, including:

- Delimit the implementation of a function from the rest of the program
- Assign an [identifier](https://en.wikipedia.org/wiki/Identifier "Identifier"), name, to a function
- Define [formal parameters](https://en.wikipedia.org/wiki/Formal_parameters "Formal parameters") with a name and [data type](https://en.wikipedia.org/wiki/Data_type "Data type") for each
- Assign a [data type](https://en.wikipedia.org/wiki/Data_type "Data type") to the return value, if any
- Specify a return value in the function body
- Call a function
- Provide [actual parameters](https://en.wikipedia.org/wiki/Actual_parameters "Actual parameters") that correspond to a called function's formal parameters
- [Return](https://en.wikipedia.org/wiki/Return_statement "Return statement") control to the caller at the point of call
- Consume the return value in the caller
- Dispose of the values returned by a call
- Provide a private [naming scope](https://en.wikipedia.org/wiki/Scope_(computer_science) "Scope (computer science)") for variables
- Identify variables outside the function that are accessible within it
- Propagate an [exceptional condition](https://en.wikipedia.org/wiki/Exception_handling "Exception handling") out of a function and to handle it in the calling context
- Package functions into a container such as [module](https://en.wikipedia.org/wiki/Modular_programming "Modular programming"), [library](https://en.wikipedia.org/wiki/Library_(computing) "Library (computing)"), [object](https://en.wikipedia.org/wiki/Object_(computer_science) "Object (computer science)"), or [class](https://en.wikipedia.org/wiki/Class_(computer_programming) "Class (computer programming)")

#### Naming
Some languages, such as [Pascal](https://en.wikipedia.org/wiki/Pascal_(programming_language) "Pascal (programming language)"), [Fortran](https://en.wikipedia.org/wiki/Fortran "Fortran"), [Ada](https://en.wikipedia.org/wiki/Ada_(programming_language) "Ada (programming language)") and many [dialects](https://en.wikipedia.org/wiki/Dialect_(computing) "Dialect (computing)") of [BASIC](https://en.wikipedia.org/wiki/BASIC "BASIC"), use a different name for a callable unit that returns a value (_function_ or _subprogram_) vs. one that does not (_subroutine_ or _procedure_). Other languages, such as [C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)"), [C++](https://en.wikipedia.org/wiki/C%2B%2B "C++"), [C#](https://en.wikipedia.org/wiki/C_Sharp_(programming_language) "C Sharp (programming language)") and [Lisp](https://en.wikipedia.org/wiki/Lisp_(programming_language) "Lisp (programming language)"), use only one name for a callable unit, _function_. The C-family languages use the keyword `void` to indicate no return value.

#### Call syntax
If declared to return a value, a call can be embedded in an [expression](https://en.wikipedia.org/wiki/Expression_(programming) "Expression (programming)") in order to consume the return value. For example, a square root callable unit might be called like `y = sqrt(x)`.

A callable unit that does not return a value is called as a stand-alone [statement](https://en.wikipedia.org/wiki/Statement_(computer_science) "Statement (computer science)") like `print("hello")`. This syntax can also be used for a callable unit that returns a value, but the return value will be ignored.

Some older languages require a keyword for calls that do not consume a return value, like `CALL print("hello")`.

#### Parameters
Most implementations, especially in modern languages, support [parameters](https://en.wikipedia.org/wiki/Parameter_(computer_science) "Parameter (computer science)") which the callable declares as _formal parameters_. A caller passes _actual parameters_, a.k.a. _arguments_, to match. Different programming languages provide different conventions for passing arguments.

| Convention                                                                                   | Description                                                                                                                                                                              | Used in                                                                                                                                                                                                                             |
| -------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [by value](https://en.wikipedia.org/wiki/Call_by_value "Call by value")                      | A copy of the argment is passed                                                                                                                                                          | Default in most Algol-like languages after [Algol 60](https://en.wikipedia.org/wiki/Algol_60 "Algol 60"), such as Pascal, Delphi, Simula, CPL, PL/M, Modula, Oberon, Ada, and many others including C, C++ and Java                 |
| [by reference](https://en.wikipedia.org/wiki/Call_by_reference "Call by reference")          | A reference to the argument is passed; typically its address                                                                                                                             | Selectable in most Algol-like languages after [Algol 60](https://en.wikipedia.org/wiki/Algol_60 "Algol 60"), such as Algol 68, Pascal, Delphi, Simula, CPL, PL/M, Modula, Oberon, Ada, and many others including C++, Fortran, PL/I |
| [by result](https://en.wikipedia.org/wiki/Call_by_result "Call by result")                   | The value computed during the call is copied to the argument on return                                                                                                                   | Ada OUT parameters                                                                                                                                                                                                                  |
| [by value-result](https://en.wikipedia.org/wiki/Call_by_value-result "Call by value-result") | A copy of the argument is passed in and the value computed during the call is copied to the argument on return                                                                           | Algol, [Swift](https://en.wikipedia.org/wiki/Swift_(programming_language) "Swift (programming language)") in-out parameters                                                                                                         |
| [by name](https://en.wikipedia.org/wiki/Call_by_name "Call by name")                         | Like a macro – replace the parameters with the unevaluated argument expressions, then evaluate the argument in the context of the caller every time that the callable uses the parameter | Algol, [Scala](https://en.wikipedia.org/wiki/Scala_(programming_language) "Scala (programming language)")                                                                                                                           |
| by constant value                                                                            | Like by-value except that the parameter is treated as a constant                                                                                                                         | PL/I NONASSIGNABLE parameters, Ada IN parameters                                                                                                                                                                                    |

#### Return value
In some languages, such as BASIC, a callable has different syntax (i.e. keyword) for a callable that returns a value vs. one that does not. In other languages, the syntax is the same regardless. In some of these languages an extra keyword is used to declare no return value; for example `void` in C, C++ and C#. In some languages, such as Python, the difference is whether the body contains a return statement with a value, and a particular callable may return with or without a value based on control flow.

#### Side effects
In many contexts, a callable may have [side effect](https://en.wikipedia.org/wiki/Side-effect_(computer_science) "Side-effect (computer science)") behavior such as modifying passed or global data, reading from or writing to a [peripheral device](https://en.wikipedia.org/wiki/Peripheral_device "Peripheral device"), accessing a [file](https://en.wikipedia.org/wiki/Computer_file "Computer file"), halting the program or the machine, or temporarily pausing program execution.

Side effects are considered undesireble by [Robert C. Martin](https://en.wikipedia.org/wiki/Robert_C._Martin "Robert C. Martin"), who is known for promoting design principles. Martin argues that side effects can result in [temporal coupling](https://en.wikipedia.org/wiki/Sequential_coupling "Sequential coupling") or order dependencies.

In strictly [functional programming](https://en.wikipedia.org/wiki/Functional_programming "Functional programming") languages such as [Haskell](https://en.wikipedia.org/wiki/Haskell_(programming_language) "Haskell (programming language)"), a function can have no [side effects](https://en.wikipedia.org/wiki/Side_effect_(computer_science) "Side effect (computer science)"), which means it cannot change the state of the program. Functions always return the same result for the same input. Such languages typically only support functions that return a value, since there is no value in a function that has neither return value nor side effect.

#### Local variables
Most contexts support _local variables_ – [memory](https://en.wikipedia.org/wiki/Virtual_memory "Virtual memory") owned by a callable to hold intermediate values. These variables are typically stored in the call's _activation record_ on the [call stack](https://en.wikipedia.org/wiki/Call_stack "Call stack") along with other information such as the [return address](https://en.wikipedia.org/wiki/Return_address_(computing) "Return address (computing)").

#### Nested call – recursion
If supported by the language, a callable may call itself, causing its execution to suspend while another _nested_ execution of the same callable executes. [Recursion](https://en.wikipedia.org/wiki/Recursion "Recursion") is a useful means to simplify some complex algorithms and break down complex problems. Recursive languages provide a new copy of local variables on each call. If the programmer desires the recursive callable to use the same variables instead of using locals, they typically declare them in a shared context such static or global.

Languages going back to [ALGOL](https://en.wikipedia.org/wiki/ALGOL "ALGOL"), [PL/I](https://en.wikipedia.org/wiki/PL/I "PL/I") and [C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)") and modern languages, almost invariably use a call stack, usually supported by the instruction sets to provide an activation record for each call. That way, a nested call can modify its local variables without affecting any of the suspended calls variables.

Recursion allows direct implementation of functionality defined by [mathematical induction](https://en.wikipedia.org/wiki/Mathematical_induction "Mathematical induction") and recursive [divide and conquer algorithms](https://en.wikipedia.org/wiki/Divide_and_conquer_algorithm "Divide and conquer algorithm"). Here is an example of a recursive function in C/C++ to find [Fibonacci](https://en.wikipedia.org/wiki/Fibonacci "Fibonacci") numbers

```c

int Fib(int n) {
  if (n <= 1) {
    return n;
  }
  return Fib(n - 1) + Fib(n - 2);
}
```

Early languages like [Fortran](https://en.wikipedia.org/wiki/Fortran "Fortran") did not initially support recursion because only one set of variables and return address were allocated for each callable. Early computer instruction sets made storing return addresses and variables on a stack difficult. Machines with [index registers](https://en.wikipedia.org/wiki/Index_registers "Index registers") or [general-purpose registers](https://en.wikipedia.org/wiki/General-purpose_registers "General-purpose registers"), e.g., [CDC 6000 series](https://en.wikipedia.org/wiki/CDC_6000_series "CDC 6000 series"), [PDP-6](https://en.wikipedia.org/wiki/PDP-6 "PDP-6"), [GE 635](https://en.wikipedia.org/wiki/GE_635 "GE 635"), [System/360](https://en.wikipedia.org/wiki/System/360 "System/360"), [UNIVAC 1100 series](https://en.wikipedia.org/wiki/UNIVAC_1100_series "UNIVAC 1100 series"), could use one of those registers as a [stack pointer](https://en.wikipedia.org/wiki/Stack_pointer "Stack pointer").

#### Nested scope
Some languages, e.g., [Ada](https://en.wikipedia.org/wiki/Ada_(programming_language) "Ada (programming language)"), [Pascal](https://en.wikipedia.org/wiki/Pascal_(programming_language) "Pascal (programming language)"), [PL/I](https://en.wikipedia.org/wiki/PL/I "PL/I"), [Python](https://en.wikipedia.org/wiki/Python_(programming_language) "Python (programming language)"), support declaring and defining a function inside, e.g., a function body, such that the name of the inner is only visible within the body of the outer.

#### Reentrancy
If a callable can be executed properly even when another execution of the same callable is already in progress, that callable is said to be _[reentrant](https://en.wikipedia.org/wiki/Reentrant_(subroutine) "Reentrant (subroutine)")_. A reentrant callable is also useful in [multi-threaded](https://en.wikipedia.org/wiki/Thread_(computer_science) "Thread (computer science)") situations since multiple threads can call the same callable without fear of interfering with each other. In the [IBM](https://en.wikipedia.org/wiki/IBM "IBM") [CICS](https://en.wikipedia.org/wiki/CICS "CICS") [transaction processing system](https://en.wikipedia.org/wiki/Transaction_processing_system "Transaction processing system"), _quasi-reentrant_ was a slightly less restrictive, but similar, requirement for application programs that were shared by many threads.

#### Overloading
Some languages support _overloading_ – allow multiple callables with the same name in the same scope, but operating on different types of input. Consider the square root function applied to real number, complex number and matrix input. The algorithm for each type of input is different, and the return value may have a different type. By writing three separate callables with the same name. i.e. _sqrt_, the resulting code may be easier to write and to maintain since each one has a name that is relatively easy to understand and to remember instead of giving longer and more complicated names like _sqrt_real_, _sqrt_complex_, _qrt_matrix_.

Overloading is supported in many languages that support [strong typing](https://en.wikipedia.org/wiki/Strong_typing "Strong typing"). Often the compiler selects the overload to call based on the type of the input arguments or it fails if the input arguments do not select an overload. Older and weakly-typed languages generally do not support overloading.

Here is an example of overloading in [C++](https://en.wikipedia.org/wiki/C%2B%2B "C++"), two functions `Area` that accept different types:

```c++
// returns the area of a rectangle defined by height and width
double Area(double h, double w) { return h * w; }

// returns the area of a circle defined by radius
double Area(double r) { return r * r * 3.14; )

int main() {
  double rectangle_area = Area(3, 4);
  double circle_area = Area(5);
}
```

PL/I has the `GENERIC` attribute to define a generic name for a set of entry references called with different types of arguments. Example:

```
DECLARE gen_name GENERIC(
    name  WHEN(FIXED BINARY),
    flame  WHEN(FLOAT),
    pathname OTHERWISE);
```

Multiple argument definitions may be specified for each entry. A call to "gen_name" will result in a call to "name" when the argument is FIXED BINARY, "flame" when FLOAT", etc. If the argument matches none of the choices "pathname" will be called.

#### Closure
A _[closure](https://en.wikipedia.org/wiki/Closure_(computer_science) "Closure (computer science)")_ is a callable plus values of some of its variables captured from the environment in which it was created. Closures were a notable feature of the Lisp programming language, introduced by [John McCarthy](https://en.wikipedia.org/wiki/John_McCarthy_(computer_scientist) "John McCarthy (computer scientist)"). Depending on the implementation, closures can serve as a mechanism for side-effects.

#### Exception reporting
Besides its [happy path](https://en.wikipedia.org/wiki/Happy_path "Happy path") behavior, a callable may need to inform the caller about an [exceptional](https://en.wikipedia.org/wiki/Exception_(computer_science) "Exception (computer science)") condition that occurred during its execution.

Most modern languages support exceptions which allows for exceptional control flow that pops the call stack until an exception handler is found to handle the condition.

Languages that do not support exceptions can use the return value to indicate success or failure of a call. Another approach is to use a well-known location like a global variable for success indication. A callable writes the value and the caller reads it after a call.

In the [IBM System/360](https://en.wikipedia.org/wiki/IBM_System/360 "IBM System/360"), where return code was expected from a subroutine, the return value was often designed to be a multiple of 4—so that it could be used as a direct [branch table](https://en.wikipedia.org/wiki/Branch_table "Branch table") index into a branch table often located immediately after the call instruction to avoid extra conditional tests, further improving efficiency.

#### Call overhead
A call has runtime [overhead](https://en.wikipedia.org/wiki/Computational_overhead "Computational overhead"), which may include but is not limited to:

- Allocating and reclaiming call stack storage
- Saving and restoring processor registers
- Copying input variables
- Copying values after the call into the caller's context
- Automatic testing of the return code
- Handling of exceptions
- Dispatching such as for a virtual method in an object-oriented language

Various techniques are employed to minimize the runtime cost of calls.

#### Compiler optimization
Some optimizations for minimizing call overhead may seem straight forward, but cannot be used if the callable has side effects. For example, in the expression `(f(x)-1)/(f(x)+1)`, the function `f` cannot be called only once with its value used two times since the two calls may return different results. Moreover, in the few languages which define the order of evaluation of the division operator's operands, the value of `x` must be fetched again before the second call, since the first call may have changed it. Determining whether a callable has a side effect is difficult – indeed, [undecidable](https://en.wikipedia.org/wiki/Undecidable_problem "Undecidable problem") by virtue of [Rice's theorem](https://en.wikipedia.org/wiki/Rice%27s_theorem "Rice's theorem"). So, while this optimization is safe in a purely functional programming language, a compiler for an language not limited to functional typically assumes the worst case, that every callable may have side effects.

#### Inlining
[Inlining](https://en.wikipedia.org/wiki/Inline_expansion "Inline expansion") eliminates calls for particular callables. The compiler replaces each call with the compiled code of the callable. Not only does this avoid the call overhead, but it also allows the [compiler](https://en.wikipedia.org/wiki/Compiler "Compiler") to [optimize](https://en.wikipedia.org/wiki/Code_optimization "Code optimization") code of the caller more effectively by taking into account the context and arguments at that call. Inlining, however, usually increases the compiled code size, except when only called once or the body is very short, like one line.

#### Sharing
Callables can be defined within a program, or separately in a [library](https://en.wikipedia.org/wiki/Library_(computing) "Library (computing)") that can be used by multiple programs.

#### Inter-operability
A [compiler](https://en.wikipedia.org/wiki/Compiler "Compiler") translates call and return statements into machine instructions according to a well-defined [calling convention](https://en.wikipedia.org/wiki/Calling_convention "Calling convention"). For code compiled by the same or a compatible compiler, functions can be compiled separately from the programs that call them. The instruction sequences corresponding to call and return statements are called the procedure's [prologue and epilogue](https://en.wikipedia.org/wiki/Function_prologue "Function prologue").

#### Built-in functions
A _built-in function_, or _builtin function_, or _intrinsic function_, is a function for which the compiler generates code at [compile time](https://en.wikipedia.org/wiki/Compile_time "Compile time") or provides in a way other than for other functions. A built-in function does not need to be defined like other functions since it is _built in_ to the programming language.

## Closure
In [programming languages](https://en.wikipedia.org/wiki/Programming_language), a **closure**, also **lexical closure** or **function closure**, is a technique for implementing [lexically scoped](https://en.wikipedia.org/wiki/Lexically_scoped "Lexically scoped") [name binding](https://en.wikipedia.org/wiki/Name_binding "Name binding") in a language with [first-class functions](https://en.wikipedia.org/wiki/First-class_function "First-class function"). [Operationally](https://en.wikipedia.org/wiki/Operational_semantics "Operational semantics"), a closure is a [record](https://en.wikipedia.org/wiki/Record_(computer_science) "Record (computer science)") storing a [function](https://en.wikipedia.org/wiki/Function_(computer_science) "Function (computer science)") together with an environment. The environment is a mapping associating each [free variable](https://en.wikipedia.org/wiki/Free_variable "Free variable") of the function (variables that are used locally, but defined in an enclosing scope) with the [value](https://en.wikipedia.org/wiki/Value_(computer_science) "Value (computer science)") or [reference](https://en.wikipedia.org/wiki/Reference_(computer_science) "Reference (computer science)") to which the name was bound when the closure was created. Unlike a plain function, a closure allows the function to access those _captured variables_ through the closure's copies of their values or references, even when the function is invoked outside their scope.

### Applications
The use of closures is associated with languages where functions are [first-class objects](https://en.wikipedia.org/wiki/First-class_object "First-class object"), in which functions can be returned as results from [higher-order functions](https://en.wikipedia.org/wiki/Higher-order_function "Higher-order function"), or passed as arguments to other function calls; if functions with free variables are first-class, then returning one creates a closure. This includes [functional programming](https://en.wikipedia.org/wiki/Functional_programming "Functional programming") languages such as [Lisp](https://en.wikipedia.org/wiki/Lisp_(programming_language) "Lisp (programming language)") and [ML](https://en.wikipedia.org/wiki/ML_(programming_language) "ML (programming language)"), and many modern, multi-paradigm languages, such as [Julia](https://en.wikipedia.org/wiki/Julia_(programming_language) "Julia (programming language)"), [Python](https://en.wikipedia.org/wiki/Python_(programming_language) "Python (programming language)"), and [Rust](https://en.wikipedia.org/wiki/Rust_(programming_language) "Rust (programming language)"). Closures are also often used with [callbacks](https://en.wikipedia.org/wiki/Callback_(computer_programming) "Callback (computer programming)"), particularly for [event handlers](https://en.wikipedia.org/wiki/Event_handler "Event handler"), such as in [JavaScript](https://en.wikipedia.org/wiki/JavaScript "JavaScript"), where they are used for interactions with a [dynamic web page](https://en.wikipedia.org/wiki/Dynamic_web_page "Dynamic web page").

Closures can also be used in a [continuation-passing style](https://en.wikipedia.org/wiki/Continuation-passing_style "Continuation-passing style") to [hide state](https://en.wikipedia.org/wiki/Information_hiding "Information hiding"). Constructs such as [objects](https://en.wikipedia.org/wiki/Object_(computer_science) "Object (computer science)") and [control structures](https://en.wikipedia.org/wiki/Control_structure "Control structure") can thus be implemented with closures. In some languages, a closure may occur when a function is defined within another function, and the inner function refers to local variables of the outer function. At [run-time](https://en.wikipedia.org/wiki/Run_time_(program_lifecycle_phase) "Run time (program lifecycle phase)"), when the outer function executes, a closure is formed, consisting of the inner function's code and references (the upvalues) to any variables of the outer function required by the closure.

#### First-class functions
Closures typically appear in languages with [first-class functions](https://en.wikipedia.org/wiki/First-class_object "First-class object")—in other words, such languages enable functions to be passed as arguments, returned from function calls, bound to variable names, etc., just like simpler types such as strings and integers. For example, consider the following [Scheme](https://en.wikipedia.org/wiki/Scheme_(programming_language) "Scheme (programming language)") function:

```
; Return a list of all books with at least THRESHOLD copies sold.
(define (best-selling-books threshold)
  (filter
    (lambda (book)
      (>= (book-sales book) threshold))
    book-list))
```

In this example, the [lambda expression](https://en.wikipedia.org/wiki/Lambda_(programming) "Lambda (programming)") `(lambda (book) (>= (book-sales book) threshold))` appears within the function `best-selling-books`. When the lambda expression is evaluated, Scheme creates a closure consisting of the code for the lambda expression and a reference to the `threshold` variable, which is a [free variable](https://en.wikipedia.org/wiki/Free_variable "Free variable") inside the lambda expression.

The closure is then passed to the `filter` function, which calls it repeatedly to determine which books are to be added to the result list and which are to be discarded. Because the closure has a reference to `threshold`, it can use that variable each time `filter` calls it. The function `filter` might be defined in a separate file.

Here is the same example rewritten in [JavaScript](https://en.wikipedia.org/wiki/JavaScript "JavaScript"), another popular language with support for closures:

```javascript
// Return a list of all books with at least 'threshold' copies sold.
function bestSellingBooks(threshold) {
  return bookList.filter(book => book.sales >= threshold);
}
```

The arrow operator `=>` is used to define an [arrow function expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow%20functions), and an `Array.filter` method instead of a global `filter` function, but otherwise the structure and the effect of the code are the same.

A function may create a closure and return it, as in this example:

```javascript
// Return a function that approximates the derivative of f
// using an interval of dx, which should be appropriately small.
function derivative(f, dx) {
  return x => (f(x + dx) - f(x)) / dx;
}
```

Because the closure in this case outlives the execution of the function that creates it, the variables `f` and `dx` live on after the function `derivative` returns, even though execution has left their scope and they are no longer visible. In languages without closures, the lifetime of an automatic local variable coincides with the execution of the stack frame where that variable is declared. In languages with closures, variables must continue to exist as long as any existing closures have references to them. This is most commonly implemented using some form of [garbage collection](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science) "Garbage collection (computer science)").

#### State representation
A closure can be used to associate a function with a set of "[private](https://en.wikipedia.org/wiki/Class_(computer_programming) "Class (computer programming)")" variables, which persist over several invocations of the function. The [scope](https://en.wikipedia.org/wiki/Scope_(programming) "Scope (programming)") of the variable encompasses only the closed-over function, so it cannot be accessed from other program code. These are analogous to [private variables](https://en.wikipedia.org/wiki/Private_variable "Private variable") in [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming"), and in fact closures are similar to stateful [function objects](https://en.wikipedia.org/wiki/Function_objects "Function objects") (or functors) with a single call-operator method.

In stateful languages, closures can thus be used to implement paradigms for state representation and [information hiding](https://en.wikipedia.org/wiki/Information_hiding "Information hiding"), since the closure's upvalues (its closed-over variables) are of indefinite [extent](https://en.wikipedia.org/wiki/Variable_(programming)#Scope_and_extent "Variable (programming)"), so a value established in one invocation remains available in the next. Closures used in this way no longer have [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency "Referential transparency"), and are thus no longer [pure functions](https://en.wikipedia.org/wiki/Pure_function "Pure function"); nevertheless, they are commonly used in impure functional languages such as [Scheme](https://en.wikipedia.org/wiki/Scheme_(programming_language) "Scheme (programming language)").


### Implementations and Theory
Closures are typically implemented with a special [data structure](https://en.wikipedia.org/wiki/Data_structure "Data structure") that contains a [pointer to the function code](https://en.wikipedia.org/wiki/Function_pointer "Function pointer"), plus a representation of the function's lexical environment (i.e., the set of available variables) at the time when the closure was created. The referencing environment [binds](https://en.wikipedia.org/wiki/Name_binding "Name binding") the non-local names to the corresponding variables in the lexical environment at the time the closure is created, additionally extending their lifetime to at least as long as the lifetime of the closure. When the closure is entered at a later time, possibly with a different lexical environment, the function is executed with its non-local variables referring to the ones captured by the closure, not the current environment.

A language implementation cannot easily support full closures if its run-time memory model allocates all [automatic variables](https://en.wikipedia.org/wiki/Automatic_variable "Automatic variable") on a linear [stack](https://en.wikipedia.org/wiki/Stack-based_memory_allocation "Stack-based memory allocation"). In such languages, a function's automatic local variables are deallocated when the function returns. However, a closure requires that the free variables it references survive the enclosing function's execution. Therefore, those variables must be allocated so that they persist until no longer needed, typically via [heap allocation](https://en.wikipedia.org/wiki/Heap_allocation "Heap allocation"), rather than on the stack, and their lifetime must be managed so they survive until all closures referencing them are no longer in use.

This explains why, typically, languages that natively support closures also use [garbage collection](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science) "Garbage collection (computer science)"). The alternatives are manual memory management of non-local variables (explicitly allocating on the heap and freeing when done), or, if using stack allocation, for the language to accept that certain use cases will lead to [undefined behaviour](https://en.wikipedia.org/wiki/Undefined_behaviour "Undefined behaviour"), due to [dangling pointers](https://en.wikipedia.org/wiki/Dangling_pointer "Dangling pointer") to freed automatic variables, as in lambda expressions in C++) or nested functions in GNU C. The [funarg problem](https://en.wikipedia.org/wiki/Funarg_problem "Funarg problem") (or "functional argument" problem) describes the difficulty of implementing functions as first class objects in a stack-based programming language such as C or C++. Similarly in [D](https://en.wikipedia.org/wiki/D_(programming_language) "D (programming language)") version 1, it is assumed that the programmer knows what to do with [delegates](https://en.wikipedia.org/wiki/Delegation_(programming) "Delegation (programming)") and automatic local variables, as their references will be invalid after return from its definition scope (automatic local variables are on the stack) – this still permits many useful functional patterns, but for complex cases needs explicit [heap allocation](https://en.wikipedia.org/wiki/Heap_allocation "Heap allocation") for variables. D version 2 solved this by detecting which variables must be stored on the heap, and performs automatic allocation. Because D uses garbage collection, in both versions, there is no need to track usage of variables as they are passed.

In strict functional languages with immutable data (_e.g._ [Erlang](https://en.wikipedia.org/wiki/Erlang_(programming_language) "Erlang (programming language)")), it is very easy to implement automatic memory management (garbage collection), as there are no possible cycles in variables' references. For example, in Erlang, all arguments and variables are allocated on the heap, but references to them are additionally stored on the stack. After a function returns, references are still valid. Heap cleaning is done by incremental garbage collector.

In ML, local variables are lexically scoped, and hence define a stack-like model, but since they are bound to values and not to objects, an implementation is free to copy these values into the closure's data structure in a way that is invisible to the programmer.

[Scheme](https://en.wikipedia.org/wiki/Scheme_(programming_language) "Scheme (programming language)"), which has an [ALGOL](https://en.wikipedia.org/wiki/ALGOL "ALGOL")-like lexical scope system with dynamic variables and garbage collection, lacks a stack programming model and does not suffer from the limitations of stack-based languages. Closures are expressed naturally in Scheme. The lambda form encloses the code, and the free variables of its environment persist within the program as long as they can possibly be accessed, and so they can be used as freely as any other Scheme expression.

Closures are closely related to Actors in the [Actor model](https://en.wikipedia.org/wiki/Actor_model "Actor model") of concurrent computation where the values in the function's lexical environment are called _acquaintances_. An important issue for closures in [concurrent programming](https://en.wikipedia.org/wiki/Concurrent_programming "Concurrent programming") languages is whether the variables in a closure can be updated and, if so, how these updates can be synchronized. Actors provide one solution.

Closures are closely related to [function objects](https://en.wikipedia.org/wiki/Function_object "Function object"); the transformation from the former to the latter is known as [defunctionalization](https://en.wikipedia.org/wiki/Defunctionalization "Defunctionalization") or [lambda lifting](https://en.wikipedia.org/wiki/Lambda_lifting "Lambda lifting"); see also [closure conversion](https://en.wikipedia.org/wiki/Closure_conversion "Closure conversion").

### Differences In Semantics
#### Lexical environment
As different languages do not always have a common definition of the lexical environment, their definitions of closure may vary also. The commonly held minimalist definition of the lexical environment defines it as a set of all [bindings of variables](https://en.wikipedia.org/wiki/Name_binding "Name binding") in the scope, and that is also what closures in any language have to capture. However the meaning of a [variable](https://en.wikipedia.org/wiki/Variable_(programming) "Variable (programming)") binding also differs. In imperative languages, variables bind to relative locations in memory that can store values. Although the relative location of a binding does not change at runtime, the value in the bound location can. In such languages, since closure captures the binding, any operation on the variable, whether done from the closure or not, are performed on the same relative memory location. This is often called capturing the variable "by reference". Here is an example illustrating the concept in [ECMAScript](https://en.wikipedia.org/wiki/ECMAScript "ECMAScript"), which is one such language:

```javascript
// Javascript
var f, g;
function foo() {
  var x;
  f = function() { return ++x; };
  g = function() { return --x; };
  x = 1;
  alert('inside foo, call to f(): ' + f());
}
foo();  // 2
alert('call to g(): ' + g());  // 1 (--x)
alert('call to g(): ' + g());  // 0 (--x)
alert('call to f(): ' + f());  // 1 (++x)
alert('call to f(): ' + f());  // 2 (++x)
```

Function `foo` and the closures referred to by variables `f` and `g` all use the same relative memory location signified by local variable `x`.

In some instances the above behaviour may be undesirable, and it is necessary to bind a different lexical closure. Again in ECMAScript, this would be done using the `Function.bind()`.

#### Example 1: Reference to an unbound variable
```javascript
var module = {
  x: 42,
  getX: function() {return this.x; }
}
var unboundGetX = module.getX;
console.log(unboundGetX()); // The function gets invoked at the global scope
// emits undefined as 'x' is not specified in global scope.

var boundGetX = unboundGetX.bind(module); // specify object module as the closure
console.log(boundGetX()); // emits 42
```

#### Example 2: Accidental reference to a bound variable
For this example the expected behaviour would be that each link should emit its id when clicked; but because the variable 'e' is bound to the scope above, and lazy evaluated on click, what actually happens is that each on click event emits the id of the last element in 'elements' bound at the end of the for loop.

```javascript
var elements = document.getElementsByTagName('a');
// Incorrect: e is bound to the function containing the 'for' loop, not the closure of "handle"
for (var e of elements) { 
  e.onclick = function handle() { 
    alert(e.id);
  } 
}

```

Again here variable `e` would need to be bound by the scope of the block using `handle.bind(this)` or the `let` keyword.

On the other hand, many functional languages, such as [ML](https://en.wikipedia.org/wiki/ML_(programming_language) "ML (programming language)"), bind variables directly to values. In this case, since there is no way to change the value of the variable once it is bound, there is no need to share the state between closures—they just use the same values. This is often called capturing the variable "by value". Java's local and anonymous classes also fall into this category—they require captured local variables to be `final`, which also means there is no need to share state.

Some languages enable choosing between capturing the value of a variable or its location. For example, in C++11, captured variables are either declared with `[&]`, which means captured by reference, or with `[=]`, which means captured by value.

Yet another subset, [lazy](https://en.wikipedia.org/wiki/Lazy_evaluation "Lazy evaluation") functional languages such as [Haskell](https://en.wikipedia.org/wiki/Haskell "Haskell"), bind variables to results of future computations rather than values. Consider this example in Haskell:

```haskell
-- Haskell
foo :: Fractional a => a -> a -> (a -> a)
foo x y = (\z -> z + r)
          where r = x / y

f :: Fractional a => a -> a
f = foo 1 0

main = print (f 123)
```

The binding of `r` captured by the closure defined within function `foo` is to the computation `(x / y)`—which in this case results in division by zero. However, since it is the computation that is captured, and not the value, the error only manifests when the closure is invoked, and then attempts to use the captured binding.

#### Closure leaving
Yet more differences manifest themselves in the behavior of other lexically scoped constructs, such as `return`, `break` and `continue` statements. Such constructs can, in general, be considered in terms of invoking an [escape continuation](https://en.wikipedia.org/wiki/Escape_continuation "Escape continuation") established by an enclosing control statement (in case of `break` and `continue`, such interpretation requires looping constructs to be considered in terms of recursive function calls). In some languages, such as ECMAScript, `return` refers to the continuation established by the closure lexically innermost with respect to the statement—thus, a `return` within a closure transfers control to the code that called it. However, in [Smalltalk](https://en.wikipedia.org/wiki/Smalltalk "Smalltalk"), the superficially similar operator `^` invokes the escape continuation established for the method invocation, ignoring the escape continuations of any intervening nested closures. The escape continuation of a particular closure can only be invoked in Smalltalk implicitly by reaching the end of the closure's code. These examples in ECMAScript and Smalltalk highlight the difference:
```smalltalk
"Smalltalk"
foo
  | xs |
  xs := #(1 2 3 4).
  xs do: [:x | ^x].
  ^0
bar
  Transcript show: (self foo printString) "prints 1"
```

```ecmascript
// ECMAScript
function foo() {
  var xs = [1, 2, 3, 4];
  xs.forEach(function (x) { return x; });
  return 0;
}
alert(foo()); // prints 0
```

The above code snippets will behave differently because the Smalltalk `^` operator and the JavaScript `return` operator are not analogous. In the ECMAScript example, `return x` will leave the inner closure to begin a new iteration of the `forEach` loop, whereas in the Smalltalk example, `^x` will abort the loop and return from the method `foo`.

[Common Lisp](https://en.wikipedia.org/wiki/Common_Lisp "Common Lisp") provides a construct that can express either of the above actions: Lisp `(return-from foo x)` behaves as [Smalltalk](https://en.wikipedia.org/wiki/Smalltalk "Smalltalk") `^x`, while Lisp `(return-from nil x)` behaves as [JavaScript](https://en.wikipedia.org/wiki/JavaScript "JavaScript") `return x`. Hence, Smalltalk makes it possible for a captured escape continuation to outlive the extent in which it can be successfully invoked. Consider:

```smalltalk
"Smalltalk"
foo
    ^[ :x | ^x ]
bar
    | f |
    f := self foo.
    f value: 123 "error!"
```

When the closure returned by the method `foo` is invoked, it attempts to return a value from the invocation of `foo` that created the closure. Since that call has already returned and the Smalltalk method invocation model does not follow the [spaghetti stack](https://en.wikipedia.org/wiki/Spaghetti_stack "Spaghetti stack") discipline to facilitate multiple returns, this operation results in an error.

## First-Class Citizen
**First Class Citizen** -> In a given [programming language design](https://en.wikipedia.org/wiki/Programming_language#Design_and_implementation "Programming language"), a **first-class citizen** is an entity which supports all the operations generally available to other entities. These operations typically include being passed as an [argument](https://en.wikipedia.org/wiki/Parameter_(computer_programming) "Parameter (computer programming)"), returned from a [function](https://en.wikipedia.org/wiki/Function_(computer_programming) "Function (computer programming)"), and assigned to a [variable](https://en.wikipedia.org/wiki/Variable_(computer_science) "Variable (computer science)").

## First-Class Function
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), a [programming language](https://en.wikipedia.org/wiki/Programming_language "Programming language") is said to have **first-class functions** if it treats [functions](https://en.wikipedia.org/wiki/Function_(programming) "Function (programming)") as [first-class citizens](https://en.wikipedia.org/wiki/First-class_citizen "First-class citizen"). This means the language supports passing functions as arguments to other functions, returning them as the values from other functions, and assigning them to variables or storing them in data structures. Some programming language theorists require support for [anonymous functions](https://en.wikipedia.org/wiki/Anonymous_function "Anonymous function") (function literals) as well. In languages with first-class functions, the [names](https://en.wikipedia.org/wiki/Name_(computer_science) "Name (computer science)") of functions do not have any special status; they are treated like ordinary [variables](https://en.wikipedia.org/wiki/Variable_(computer_science) "Variable (computer science)") with a [function type](https://en.wikipedia.org/wiki/Function_type "Function type"). The term was coined by [Christopher Strachey](https://en.wikipedia.org/wiki/Christopher_Strachey "Christopher Strachey") in the context of "functions as first-class citizens" in the mid-1960s.

First-class functions are a necessity for the [functional programming](https://en.wikipedia.org/wiki/Functional_programming "Functional programming") style, in which the use of [higher-order functions](https://en.wikipedia.org/wiki/Higher-order_function "Higher-order function") is a standard practice. A simple example of a higher-ordered function is the _[map](https://en.wikipedia.org/wiki/Map_(higher-order_function) "Map (higher-order function)")_ function, which takes, as its arguments, a function and a list, and returns the list formed by applying the function to each member of the list. For a language to support _map_, it must support passing a function as an argument.

There are certain implementation difficulties in passing functions as arguments or returning them as results, especially in the presence of [non-local variables](https://en.wikipedia.org/wiki/Non-local_variable "Non-local variable") introduced in [nested](https://en.wikipedia.org/wiki/Nested_function "Nested function") and [anonymous functions](https://en.wikipedia.org/wiki/Anonymous_function "Anonymous function"). Historically, these were termed the [funarg problems](https://en.wikipedia.org/wiki/Funarg_problem "Funarg problem"), the name coming from "function argument". In early imperative languages these problems were avoided by either not supporting functions as result types (e.g. [ALGOL 60](https://en.wikipedia.org/wiki/ALGOL_60 "ALGOL 60"), [Pascal](https://en.wikipedia.org/wiki/Pascal_(programming_language) "Pascal (programming language)")) or omitting nested functions and thus non-local variables (e.g. [C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)")). The early functional language [Lisp](https://en.wikipedia.org/wiki/Lisp_(programming_language) "Lisp (programming language)") took the approach of [dynamic scoping](https://en.wikipedia.org/wiki/Dynamic_scoping "Dynamic scoping"), where non-local variables refer to the closest definition of that variable at the point where the function is executed, instead of where it was defined. Proper support for [lexically scoped](https://en.wikipedia.org/wiki/Lexically_scoped "Lexically scoped") first-class functions was introduced in [Scheme](https://en.wikipedia.org/wiki/Scheme_(programming_language) "Scheme (programming language)") and requires handling references to functions as [closures](https://en.wikipedia.org/wiki/Closure_(computer_science) "Closure (computer science)") instead of bare [function pointers](https://en.wikipedia.org/wiki/Function_pointer "Function pointer"), which in turn makes [garbage collection](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science) "Garbage collection (computer science)") a necessity.

### Concepts
In this section, we compare how particular programming idioms are handled in a functional language with first-class functions ([Haskell](https://en.wikipedia.org/wiki/Haskell_(programming_language) "Haskell (programming language)")) compared to an imperative language where functions are second-class citizens ([C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)")).

#### Higher-order functions: passing functions as arguments
In languages where functions are first-class citizens, functions can be passed as arguments to other functions in the same way as other values (a function taking another function as argument is called a higher-order function). In the language [Haskell](https://en.wikipedia.org/wiki/Haskell_(programming_language) "Haskell (programming language)"):

```haskell
map :: (a -> b) -> [a] -> [b]
map f []     = []
map f (x:xs) = f x : map f xs
```

Languages where functions are not first-class often still allow one to write higher-order functions through the use of features such as [function pointers](https://en.wikipedia.org/wiki/Function_pointer "Function pointer") or [delegates](https://en.wikipedia.org/wiki/Delegate_(CLI) "Delegate (CLI)"). In the language [C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)"):

```c
void map(int (*f)(int), int x[], size_t n) {
    for (int i = 0; i < n; i++)
        x[i] = f(x[i]);
}
```

There are a number of differences between the two approaches that are _not_ directly related to the support of first-class functions. The Haskell sample operates on [lists](https://en.wikipedia.org/wiki/List_(computing) "List (computing)"), while the C sample operates on [arrays](https://en.wikipedia.org/wiki/Array_data_structure "Array data structure"). Both are the most natural compound data structures in the respective languages and making the C sample operate on linked lists would have made it unnecessarily complex. This also accounts for the fact that the C function needs an additional parameter (giving the size of the array.) The C function updates the array [in-place](https://en.wikipedia.org/wiki/In-place "In-place"), returning no value, whereas in Haskell data structures are [persistent](https://en.wikipedia.org/wiki/Persistent_data_structure "Persistent data structure") (a new list is returned while the old is left intact.) The Haskell sample uses [recursion](https://en.wikipedia.org/wiki/Recursion "Recursion") to traverse the list, while the C sample uses [iteration](https://en.wikipedia.org/wiki/Iteration "Iteration"). Again, this is the most natural way to express this function in both languages, but the Haskell sample could easily have been expressed in terms of a [fold](https://en.wikipedia.org/wiki/Fold_(higher-order_function) "Fold (higher-order function)") and the C sample in terms of recursion. Finally, the Haskell function has a [polymorphic](https://en.wikipedia.org/wiki/Polymorphism_(computer_science) "Polymorphism (computer science)") type, as this is not supported by C we have fixed all type variables to the type constant `int`.

#### Anonymous and nested functions
In languages supporting anonymous functions, we can pass such a function as an argument to a higher-order function:

`main = map (\x -> 3 * x + 1) [1, 2, 3, 4, 5]`

In a language which does not support anonymous functions, we have to bind it to a name instead:

```c
int f(int x) {
    return 3 * x + 1;
}

int main() {
    int list[] = {1, 2, 3, 4, 5};
    map(f, list, 5);
}
```

#### Non-local variables and closures

Once we have anonymous or nested functions, it becomes natural for them to refer to variables outside of their body (called _non-local variables_):

```
main = let a = 3
           b = 1
        in map (\x -> a * x + b) [1, 2, 3, 4, 5]
```

If functions are represented with bare function pointers, we can not know anymore how the value that is outside of the function's body should be passed to it, and because of that a closure needs to be built manually. Therefore we can not speak of "first-class" functions here.

```c
typedef struct {
    int (*f)(int, int, int);
    int a;
    int b;
} closure_t;

void map(closure_t *closure, int x[], size_t n) {
    for (int i = 0; i < n; ++i)
        x[i] = (closure->f)(closure->a, closure->b, x[i]);
}

int f(int a, int b, int x) {
    return a * x + b;
}

void main() {
    int l[] = {1, 2, 3, 4, 5};
    int a = 3;
    int b = 1;
    closure_t closure = {f, a, b};
    map(&closure, l, 5);
}
```

Also note that the `map` is now specialized to functions referring to two `int`s outside of their environment. This can be set up more generally, but requires more [boilerplate code](https://en.wikipedia.org/wiki/Boilerplate_code "Boilerplate code"). If `f` would have been a [nested function](https://en.wikipedia.org/wiki/Nested_function "Nested function") we would still have run into the same problem and this is the reason they are not supported in C.

#### Higher-order functions: returning functions as results
When returning a function, we are in fact returning its closure. In the C example any local variables captured by the closure will go out of scope once we return from the function that builds the closure. Forcing the closure at a later point will result in undefined behaviour, possibly corrupting the stack. This is known as the [upwards funarg problem](https://en.wikipedia.org/wiki/Upwards_funarg_problem "Upwards funarg problem").

#### Assigning functions to variables
[Assigning](https://en.wikipedia.org/wiki/Assignment_(computer_science) "Assignment (computer science)") functions to [variables](https://en.wikipedia.org/wiki/Variable_(computer_science) "Variable (computer science)") and storing them inside (global) datastructures potentially suffers from the same difficulties as returning functions.

```
f :: [[Integer] -> [Integer]]
f = let a = 3
        b = 1
     in [map (\x -> a * x + b), map (\x -> b * x + a)]
```

#### Equality of functions
As one can test most literals and values for equality, it is natural to ask whether a programming language can support testing functions for equality. On further inspection, this question appears more difficult and one has to distinguish between several types of function equality:

[Extensional equality](https://en.wikipedia.org/wiki/Extensional_equality "Extensional equality")

Two functions _f_ and _g_ are considered extensionally equal if they agree on their outputs for all inputs (∀_x_. _f_(_x_) = _g_(_x_)). Under this definition of equality, for example, any two implementations of a [stable sorting algorithm](https://en.wikipedia.org/wiki/Stable_sorting_algorithm "Stable sorting algorithm"), such as [insertion sort](https://en.wikipedia.org/wiki/Insertion_sort "Insertion sort") and [merge sort](https://en.wikipedia.org/wiki/Merge_sort "Merge sort"), would be considered equal. Deciding on extensional equality is [undecidable](https://en.wikipedia.org/wiki/Undecidable_problem "Undecidable problem") in general and even for functions with finite domains often intractable. For this reason no programming language implements function equality as extensional equality.

[Intensional equality](https://en.wikipedia.org/wiki/Intensional_equality "Intensional equality")

Under intensional equality, two functions _f_ and _g_ are considered equal if they have the same "internal structure". This kind of equality could be implemented in [interpreted languages](https://en.wikipedia.org/wiki/Interpreted_language "Interpreted language") by comparing the [source code](https://en.wikipedia.org/wiki/Source_code "Source code") of the function bodies (such as in Interpreted Lisp 1.5) or the [object code](https://en.wikipedia.org/wiki/Object_code "Object code") in [compiled languages](https://en.wikipedia.org/wiki/Compiled_language "Compiled language"). Intensional equality implies extensional equality (assuming the functions are deterministic and have no hidden inputs, such as the [program counter](https://en.wikipedia.org/wiki/Program_counter "Program counter") or a mutable [global variable](https://en.wikipedia.org/wiki/Global_variable "Global variable").)

[Reference equality](https://en.wikipedia.org/w/index.php?title=Reference_equality&action=edit&redlink=1 "Reference equality (page does not exist)")

Given the impracticality of implementing extensional and intensional equality, most languages supporting testing functions for equality use reference equality. All functions or closures are assigned a unique identifier (usually the address of the function body or the closure) and equality is decided based on equality of the identifier. Two separately defined, but otherwise identical function definitions will be considered unequal. Referential equality implies intensional and extensional equality. Referential equality breaks [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency "Referential transparency") and is therefore not supported in [pure](https://en.wikipedia.org/w/index.php?title=Purity_(computer_science)&action=edit&redlink=1 "Purity (computer science) (page does not exist)") languages, such as Haskell.

### Type theory
In [type theory](https://en.wikipedia.org/wiki/Type_theory "Type theory"), the type of functions accepting values of type _A_ and returning values of type _B_ may be written as _A_ → _B_ or _B__A_. In the [Curry–Howard correspondence](https://en.wikipedia.org/wiki/Curry%E2%80%93Howard_correspondence "Curry–Howard correspondence"), [function types](https://en.wikipedia.org/wiki/Function_type "Function type") are related to [logical implication](https://en.wikipedia.org/wiki/Logical_implication "Logical implication"); lambda abstraction corresponds to discharging hypothetical assumptions and function application corresponds to the [modus ponens](https://en.wikipedia.org/wiki/Modus_ponens "Modus ponens") inference rule. Besides the usual case of programming functions, type theory also uses first-class functions to model [associative arrays](https://en.wikipedia.org/wiki/Associative_array "Associative array") and similar [data structures](https://en.wikipedia.org/wiki/Data_structure "Data structure").

In [category-theoretical](https://en.wikipedia.org/wiki/Category_theory "Category theory") accounts of programming, the availability of first-class functions corresponds to the [closed category](https://en.wikipedia.org/wiki/Closed_category "Closed category") assumption. For instance, the [simply typed lambda calculus](https://en.wikipedia.org/wiki/Simply_typed_lambda_calculus "Simply typed lambda calculus") corresponds to the internal language of [Cartesian closed categories](https://en.wikipedia.org/wiki/Cartesian_closed_category "Cartesian closed category").

## Function Type
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science") and [mathematical logic](https://en.wikipedia.org/wiki/Mathematical_logic "Mathematical logic"), a **function type** (or **arrow type** or **exponential**) is the type of a [variable](https://en.wikipedia.org/wiki/Variable_(computer_science) "Variable (computer science)") or [parameter](https://en.wikipedia.org/wiki/Parameter_(computer_science) "Parameter (computer science)") to which a [function](https://en.wikipedia.org/wiki/Function_(computer_science) "Function (computer science)") has or can be assigned, or an argument or result type of a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function "Higher-order function") taking or returning a function.

A function type depends on the type of the parameters and the result type of the function (it, or more accurately the unapplied [type constructor](https://en.wikipedia.org/wiki/Type_constructor "Type constructor") `· → ·`, is a [higher-kinded type](https://en.wikipedia.org/wiki/Higher-kinded_type "Higher-kinded type")). In theoretical settings and [programming languages](https://en.wikipedia.org/wiki/Programming_language "Programming language") where functions are defined in [curried form](https://en.wikipedia.org/wiki/Curried_form "Curried form"), such as the [simply typed lambda calculus](https://en.wikipedia.org/wiki/Simply_typed_lambda_calculus "Simply typed lambda calculus"), a function type depends on exactly two types, the [domain](https://en.wikipedia.org/wiki/Domain_of_a_function "Domain of a function") _A_ and the [range](https://en.wikipedia.org/wiki/Range_of_a_function "Range of a function") _B_. Here a function type is often denoted _A_ → _B_, following mathematical convention, or _B__A_, based on there existing exactly _B__A_ (exponentially many) [set-theoretic functions](https://en.wikipedia.org/wiki/Function_space "Function space") mappings _A_ to _B_ in the [category of sets](https://en.wikipedia.org/wiki/Category_of_sets "Category of sets"). The class of such maps or functions is called the [exponential object](https://en.wikipedia.org/wiki/Exponential_object "Exponential object"). The act of [currying](https://en.wikipedia.org/wiki/Currying "Currying") makes the function type [adjoint](https://en.wikipedia.org/wiki/Adjoint_functor "Adjoint functor") to the [product type](https://en.wikipedia.org/wiki/Product_type "Product type"); this is explored in detail in the article on currying.

The function type can be considered to be a special case of the [dependent product type](https://en.wikipedia.org/wiki/Dependent_type#Formal_definition "Dependent type"), which among other properties, encompasses the idea of a [polymorphic function](https://en.wikipedia.org/wiki/Polymorphism_(computer_science) "Polymorphism (computer science)").

## High-Order Function
In [mathematics](https://en.wikipedia.org/wiki/Mathematics "Mathematics") and [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), a **higher-order function** (**HOF**) is a [function](https://en.wikipedia.org/wiki/Function_(mathematics) "Function (mathematics)") that does at least one of the following:

- takes one or more functions as arguments (i.e. a [procedural parameter](https://en.wikipedia.org/wiki/Procedural_parameter "Procedural parameter"), which is a [parameter](https://en.wikipedia.org/wiki/Parameter_(computer_science) "Parameter (computer science)") of a [procedure](https://en.wikipedia.org/wiki/Subroutine "Subroutine") that is itself a procedure),
- returns a function or value as its result.

All other functions are _first-order functions_. In mathematics higher-order functions are also termed _[operators](https://en.wikipedia.org/wiki/Operator_(mathematics) "Operator (mathematics)")_ or _[functionals](https://en.wikipedia.org/wiki/Functional_(mathematics) "Functional (mathematics)")_. The [differential operator](https://en.wikipedia.org/wiki/Differential_operator "Differential operator") in [calculus](https://en.wikipedia.org/wiki/Calculus "Calculus") is a common example, since it maps a function to its [derivative](https://en.wikipedia.org/wiki/Derivative "Derivative"), also a function. Higher-order functions should not be confused with other uses of the word "functor" throughout mathematics, see [Functor (disambiguation)](https://en.wikipedia.org/wiki/Functor_(disambiguation) "Functor (disambiguation)").

In the untyped [lambda calculus](https://en.wikipedia.org/wiki/Lambda_calculus "Lambda calculus"), all functions are higher-order; in a [typed lambda calculus](https://en.wikipedia.org/wiki/Typed_lambda_calculus "Typed lambda calculus"), from which most [functional programming](https://en.wikipedia.org/wiki/Functional_programming "Functional programming") languages are derived, higher-order functions that take one function as argument are values with types of the form (τ1→τ2)→τ3![{\displaystyle (\tau _{1}\to \tau _{2})\to \tau _{3}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/21f4ec10929e414aedfee50d2c07c91e9cb35668)

## Function Pointer
A **function pointer**, also called a **subroutine pointer** or **procedure pointer**, is a [pointer](https://en.wikipedia.org/wiki/Pointer_(computer_programming) "Pointer (computer programming)") referencing executable code, rather than data. [Dereferencing](https://en.wikipedia.org/wiki/Dereference_operator "Dereference operator") the function pointer yields the referenced [function](https://en.wikipedia.org/wiki/Subroutine "Subroutine"), which can be invoked and passed arguments just as in a normal function call. Such an invocation is also known as an "indirect" call, because the function is being invoked _indirectly_ through a variable instead of _directly_ through a fixed identifier or address.

Function pointers allow different code to be executed at runtime. They can also be passed to a function to enable [callbacks](https://en.wikipedia.org/wiki/Callback_(computer_programming) "Callback (computer programming)").

### Simple Function Pointers
The simplest implementation of a function (or subroutine) pointer is as a [variable](https://en.wikipedia.org/wiki/Variable_(computer_science) "Variable (computer science)") containing the [address](https://en.wikipedia.org/wiki/Memory_address "Memory address") of the function within executable memory. Older [third-generation languages](https://en.wikipedia.org/wiki/Third-generation_programming_language "Third-generation programming language") such as [PL/I](https://en.wikipedia.org/wiki/PL/I "PL/I") and [COBOL](https://en.wikipedia.org/wiki/COBOL "COBOL"), as well as more modern languages such as [Pascal](https://en.wikipedia.org/wiki/Pascal_(programming_language) "Pascal (programming language)") and [C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)") generally implement function pointers in this manner.

#### Example
```c
#include <stdio.h>  /* for printf */
#include <string.h> /* for strchr */

double cm_to_inches(double cm) {
	return cm / 2.54;
}

// "strchr" is part of the C string handling (i.e., no need for declaration)

int main(void) {
	double (*func1)(double) = cm_to_inches;
	char * (*func2)(const char *, int) = strchr;
	printf("%f %s", func1(15.0), func2("Wikipedia", 'p'));
	/* prints "5.905512 pedia" */
	return 0;
}
```

```c
#include <math.h>
#include <stdio.h>
// Function taking a function pointer as an argument
double compute_sum(double (*funcp)(double), double lo, double hi) {
    double sum = 0.0;
    // Add values returned by the pointed-to function '*funcp'
    int i;
    for (i = 0; i <= 100; i++) {
        // Use the function pointer 'funcp' to invoke the function
        double x = i / 100.0 * (hi - lo) + lo;
        double y = funcp(x);
        sum += y;
    }
    return sum / 101.0 * (hi - lo);
}
double square(double x) {
     return x * x;
}
int main(void) {
    double  sum;
    // Use standard library function 'sin()' as the pointed-to function
    sum = compute_sum(sin, 0.0, 1.0);
    printf("sum(sin): %g\n", sum);
    // Use standard library function 'cos()' as the pointed-to function
    sum = compute_sum(cos, 0.0, 1.0);
    printf("sum(cos): %g\n", sum);
    // Use user-defined function 'square()' as the pointed-to function
    sum = compute_sum(square, 0.0, 1.0);
    printf("sum(square): %g\n", sum);
    return 0;
}
```

### Functors
Functors, or function objects, are similar to function pointers, and can be used in similar ways. A functor is an object of a class type that implements the [function-call operator](https://en.wikipedia.org/wiki/Function-call_operator "Function-call operator"), allowing the object to be used within expressions using the same syntax as a function call. Functors are more powerful than simple function pointers, being able to contain their own data values, and allowing the programmer to emulate [closures](https://en.wikipedia.org/wiki/Closure_(computer_programming) "Closure (computer programming)"). They are also used as callback functions if it is necessary to use a member function as a callback function.

Many "pure" object-oriented languages do not support function pointers. Something similar can be implemented in these kinds of languages, though, using [references](https://en.wikipedia.org/wiki/Reference_(computer_science) "Reference (computer science)") to [interfaces](https://en.wikipedia.org/wiki/Protocol_(object-oriented_programming) "Protocol (object-oriented programming)") that define a single [method](https://en.wikipedia.org/wiki/Method_(computer_programming) "Method (computer programming)") (member function). [CLI languages](https://en.wikipedia.org/wiki/List_of_CLI_languages "List of CLI languages") such as [C#](https://en.wikipedia.org/wiki/C_Sharp_(programming_language) "C Sharp (programming language)") and [Visual Basic .NET](https://en.wikipedia.org/wiki/Visual_Basic_.NET "Visual Basic .NET") implement [type-safe](https://en.wikipedia.org/wiki/Type_safety "Type safety") function pointers with [delegates](https://en.wikipedia.org/wiki/Delegate_(CLI) "Delegate (CLI)").

In other languages that support [first-class functions](https://en.wikipedia.org/wiki/First-class_function "First-class function"), functions are regarded as data, and can be passed, returned, and created dynamically directly by other functions, eliminating the need for function pointers.

Extensively using function pointers to call functions may produce a slow-down for the code on modern processors, because a [branch predictor](https://en.wikipedia.org/wiki/Branch_predictor "Branch predictor") may not be able to figure out where to branch to (it depends on the value of the function pointer at run time) although this effect can be overstated as it is often amply compensated for by significantly reduced non-indexed table lookups.

### Method Pointers
C++ includes support for [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming"), so classes can have [methods](https://en.wikipedia.org/wiki/Method_(computer_programming) "Method (computer programming)") (usually referred to as member functions). Non-static member functions (instance methods) have an implicit parameter (the _[this](https://en.wikipedia.org/wiki/This_(computer_programming) "This (computer programming)")_ pointer) which is the pointer to the object it is operating on, so the type of the object must be included as part of the type of the function pointer. The method is then used on an object of that class by using one of the "pointer-to-member" operators: `.*` or `->*` (for an object or a pointer to object, respectively).

Although function pointers in C and C++ can be implemented as simple addresses, so that typically `sizeof(Fx)==sizeof(void *)`, member pointers in C++ are sometimes implemented as "[fat pointers](https://en.wikipedia.org/wiki/Fat_pointer "Fat pointer")", typically two or three times the size of a simple function pointer, in order to deal with [virtual methods](https://en.wikipedia.org/wiki/Virtual_methods "Virtual methods") and virtual inheritance.

## Pointer
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), a **pointer** is an [object](https://en.wikipedia.org/wiki/Object_(computer_science) "Object (computer science)") in many [programming languages](https://en.wikipedia.org/wiki/Programming_language "Programming language") that stores a [memory address](https://en.wikipedia.org/wiki/Memory_address "Memory address"). This can be that of another value located in [computer memory](https://en.wikipedia.org/wiki/Computer_memory "Computer memory"), or in some cases, that of [memory-mapped](https://en.wikipedia.org/wiki/Memory-mapped_I/O "Memory-mapped I/O") [computer hardware](https://en.wikipedia.org/wiki/Computer_hardware "Computer hardware"). A pointer _references_ a location in memory, and obtaining the value stored at that location is known as _dereferencing_ the pointer. As an analogy, a page number in a book's index could be considered a pointer to the corresponding page; dereferencing such a pointer would be done by flipping to the page with the given page number and reading the text found on that page. The actual format and content of a pointer variable is dependent on the underlying [computer architecture](https://en.wikipedia.org/wiki/Computer_architecture "Computer architecture").

Using pointers significantly improves [performance](https://en.wikipedia.org/wiki/Computer_performance "Computer performance") for repetitive operations, like traversing [iterable](https://en.wikipedia.org/wiki/Collection_(abstract_data_type)#Linear_collections "Collection (abstract data type)") data [structures](https://en.wikipedia.org/wiki/Data_structure "Data structure") (e.g. [strings](https://en.wikipedia.org/wiki/String_algorithms "String algorithms"), [lookup tables](https://en.wikipedia.org/wiki/Lookup_table "Lookup table"), [control tables](https://en.wikipedia.org/wiki/Control_table "Control table") and [tree](https://en.wikipedia.org/wiki/Tree_(data_structure) "Tree (data structure)") structures). In particular, it is often much cheaper in time and space to copy and dereference pointers than it is to copy and access the data to which the pointers point.

Pointers are also used to hold the addresses of entry points for [called](https://en.wikipedia.org/wiki/System_call "System call") subroutines in [procedural programming](https://en.wikipedia.org/wiki/Procedural_programming "Procedural programming") and for run-time linking to [dynamic link libraries (DLLs)](https://en.wikipedia.org/wiki/Dynamic_link_library#Explicit_run-time_linking "Dynamic link library"). In [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming"), [pointers to functions](https://en.wikipedia.org/wiki/Function_pointer "Function pointer") are used for [binding](https://en.wikipedia.org/wiki/Name_binding "Name binding") [methods](https://en.wikipedia.org/wiki/Method_(computer_programming) "Method (computer programming)"), often using [virtual method tables](https://en.wikipedia.org/wiki/Virtual_method_table "Virtual method table").

A pointer is a simple, more concrete implementation of the more abstract _[reference](https://en.wikipedia.org/wiki/Reference_(computer_science) "Reference (computer science)")_ [data type](https://en.wikipedia.org/wiki/Data_type "Data type"). Several languages, especially [low-level languages](https://en.wikipedia.org/wiki/Low-level_programming_language "Low-level programming language"), support some type of pointer, although some have more restrictions on their use than others. While "pointer" has been used to refer to references in general, it more properly applies to [data structures](https://en.wikipedia.org/wiki/Data_structures "Data structures") whose [interface](https://en.wikipedia.org/wiki/Application_programming_interface "Application programming interface") explicitly allows the pointer to be manipulated (arithmetically via _pointer arithmetic_) as a memory address, as opposed to a [magic cookie](https://en.wikipedia.org/wiki/Magic_cookie "Magic cookie") or [capability](https://en.wikipedia.org/wiki/Capability-based_security "Capability-based security") which does not allow such. Because pointers allow both protected and unprotected access to [memory addresses](https://en.wikipedia.org/wiki/Memory_address "Memory address"), there are risks associated with using them, particularly in the latter case. Primitive pointers are often stored in a format similar to an [integer](https://en.wikipedia.org/wiki/Integer "Integer"); however, attempting to dereference or "look up" such a pointer whose value is not a valid memory address could cause a program to [crash](https://en.wikipedia.org/wiki/Crash_(computing) "Crash (computing)") (or contain invalid data). To alleviate this potential problem, as a matter of [type safety](https://en.wikipedia.org/wiki/Type_safety "Type safety"), pointers are considered a separate type parameterized by the type of data they point to, even if the underlying representation is an integer. Other measures may also be taken (such as [validation](https://en.wikipedia.org/wiki/Data_validation_and_reconciliation "Data validation and reconciliation") and [bounds checking](https://en.wikipedia.org/wiki/Bounds_checking "Bounds checking")), to verify that the pointer variable contains a value that is both a valid memory address and within the numerical range that the processor is capable of addressing.

### Formal Description
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), a pointer is a kind of [reference](https://en.wikipedia.org/wiki/Reference_(computer_science) "Reference (computer science)").

A _data primitive_ (or just _primitive_) is any datum that can be read from or written to [computer memory](https://en.wikipedia.org/wiki/Computer_memory "Computer memory") using one memory access (for instance, both a _[byte](https://en.wikipedia.org/wiki/Byte "Byte")_ and a _[word](https://en.wikipedia.org/wiki/Word_(computer_architecture) "Word (computer architecture)")_ are primitives).

A _data aggregate_ (or just _aggregate_) is a group of primitives that are [logically](https://en.wikipedia.org/wiki/Logical_address "Logical address") contiguous in memory and that are viewed collectively as one datum (for instance, an aggregate could be 3 logically contiguous bytes, the values of which represent the 3 coordinates of a point in space). When an aggregate is entirely composed of the same type of primitive, the aggregate may be called an [_array_](https://en.wikipedia.org/wiki/Array_data_structure "Array data structure"); in a sense, a multi-byte _word_ primitive is an array of bytes, and some programs use words in this way.

A pointer is a programming concept used in computer science to reference or point to a memory location that stores a value or an object. It is essentially a variable that stores the memory address of another variable or data structure rather than storing the data itself.

Pointers are commonly used in programming languages that support direct memory manipulation, such as C and C++. They allow programmers to work with memory directly, enabling efficient memory management and more complex data structures. By using pointers, you can access and modify data located in memory, pass data efficiently between functions, and create dynamic data structures like linked lists, trees, and graphs.

In simpler terms, you can think of a pointer as an arrow that points to a specific spot in a computer's memory, allowing you to interact with the data stored at that location.

A _memory pointer_ (or just _pointer_) is a primitive, the value of which is intended to be used as a memory address; it is said that _a pointer points to a memory address_. It is also said that _a pointer points to a datum [in memory]_ when the pointer's value is the datum's memory address.

More generally, a pointer is a kind of [reference](https://en.wikipedia.org/wiki/Reference_(computer_science) "Reference (computer science)"), and it is said that _a pointer references a datum stored somewhere in memory_; to obtain that datum is _to dereference the pointer_. The feature that separates pointers from other kinds of reference is that a pointer's value is meant to be interpreted as a memory address, which is a rather low-level concept.

References serve as a level of indirection: A pointer's value determines which memory address (that is, which datum) is to be used in a calculation. Because indirection is a fundamental aspect of algorithms, pointers are often expressed as a fundamental [data type](https://en.wikipedia.org/wiki/Data_type "Data type") in [programming languages](https://en.wikipedia.org/wiki/Programming_language "Programming language"); in [statically](https://en.wikipedia.org/wiki/Static_types "Static types") (or [strongly](https://en.wikipedia.org/wiki/Strong_and_weak_typing "Strong and weak typing")) typed programming languages, the [type](https://en.wikipedia.org/wiki/Type_system "Type system") of a pointer determines the type of the datum to which the pointer points.

### Architectural Roots
Pointers are a very thin [abstraction](https://en.wikipedia.org/wiki/Abstraction_(computer_science) "Abstraction (computer science)") on top of the addressing capabilities provided by most modern [architectures](https://en.wikipedia.org/wiki/Software_architecture "Software architecture"). In the simplest scheme, an _[address](https://en.wikipedia.org/wiki/Memory_address "Memory address")_, or a numeric [index](https://en.wikipedia.org/wiki/Array_data_structure "Array data structure"), is assigned to each unit of memory in the system, where the unit is typically either a [byte](https://en.wikipedia.org/wiki/Byte "Byte") or a [word](https://en.wikipedia.org/wiki/Word_(computer_architecture) "Word (computer architecture)") – depending on whether the architecture is [byte-addressable](https://en.wikipedia.org/wiki/Byte_addressing "Byte addressing") or [word-addressable](https://en.wikipedia.org/wiki/Word-addressable "Word-addressable") – effectively transforming all of memory into a very large [array](https://en.wikipedia.org/wiki/Array_data_structure "Array data structure"). The system would then also provide an operation to retrieve the value stored in the memory unit at a given address (usually utilizing the machine's [general-purpose registers](https://en.wikipedia.org/wiki/General-purpose_register "General-purpose register")).

In the usual case, a pointer is large enough to hold more addresses than there are units of memory in the system. This introduces the possibility that a program may attempt to access an address which corresponds to no unit of memory, either because not enough memory is installed (i.e. beyond the range of available memory) or the architecture does not support such addresses. The first case may, in certain platforms such as the [Intel x86](https://en.wikipedia.org/wiki/X86 "X86") architecture, be called a [segmentation fault](https://en.wikipedia.org/wiki/Segmentation_fault "Segmentation fault") (segfault). The second case is possible in the current implementation of [AMD64](https://en.wikipedia.org/wiki/X86-64 "X86-64"), where pointers are 64 bit long and addresses only extend to 48 bits. Pointers must conform to certain rules (canonical addresses), so if a non-canonical pointer is dereferenced, the processor raises a [general protection fault](https://en.wikipedia.org/wiki/General_protection_fault "General protection fault").

On the other hand, some systems have more units of memory than there are addresses. In this case, a more complex scheme such as [memory segmentation](https://en.wikipedia.org/wiki/Memory_segmentation "Memory segmentation") or [paging](https://en.wikipedia.org/wiki/Paging "Paging") is employed to use different parts of the memory at different times. The last incarnations of the x86 architecture support up to 36 bits of physical memory addresses, which were mapped to the 32-bit linear address space through the [PAE](https://en.wikipedia.org/wiki/Physical_Address_Extension "Physical Address Extension") paging mechanism. Thus, only 1/16 of the possible total memory may be accessed at a time. Another example in the same computer family was the 16-bit [protected mode](https://en.wikipedia.org/wiki/Protected_mode "Protected mode") of the [80286](https://en.wikipedia.org/wiki/Intel_80286 "Intel 80286") processor, which, though supporting only 16 MB of physical memory, could access up to 1 GB of virtual memory, but the combination of 16-bit address and segment registers made accessing more than 64 KB in one data structure cumbersome.

In order to provide a consistent interface, some architectures provide [memory-mapped I/O](https://en.wikipedia.org/wiki/Memory-mapped_I/O "Memory-mapped I/O"), which allows some addresses to refer to units of memory while others refer to [device registers](https://en.wikipedia.org/wiki/Device_register "Device register") of other devices in the computer. There are analogous concepts such as file offsets, array indices, and remote object references that serve some of the same purposes as addresses for other types of objects.

## Reference 
In [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"), a **reference** is a value that enables a program to indirectly access a particular [datum](https://en.wikipedia.org/wiki/Datum "Datum"), such as a [variable](https://en.wikipedia.org/wiki/Variable_(computer_science) "Variable (computer science)")'s value or a [record](https://en.wikipedia.org/wiki/Record_(computer_science) "Record (computer science)"), in the [computer](https://en.wikipedia.org/wiki/Computer "Computer")'s [memory](https://en.wikipedia.org/wiki/Memory_(computing) "Memory (computing)") or in some other [storage device](https://en.wikipedia.org/wiki/Data_storage_device "Data storage device"). The reference is said to **refer** to the datum, and accessing the datum is called **[dereferencing](https://en.wikipedia.org/wiki/Dereference_operator "Dereference operator")** the reference. A reference is distinct from the datum itself.

A reference is an [abstract data type](https://en.wikipedia.org/wiki/Abstract_data_type "Abstract data type") and may be implemented in many ways. Typically, a reference refers to data stored in memory on a given system, and its internal value is the [memory address](https://en.wikipedia.org/wiki/Memory_address "Memory address") of the data, i.e. a reference is implemented as a [pointer](https://en.wikipedia.org/wiki/Pointer_(computer_programming) "Pointer (computer programming)"). For this reason a reference is often said to "point to" the data. Other implementations include an offset (difference) between the datum's address and some fixed "base" address, an [index](https://en.wikipedia.org/wiki/Array_index "Array index"), or [identifier](https://en.wikipedia.org/wiki/Identifier "Identifier") used in a [lookup](https://en.wikipedia.org/wiki/Lookup "Lookup") operation into an [array](https://en.wikipedia.org/wiki/Array_data_structure "Array data structure") or [table](https://en.wikipedia.org/wiki/Table_(database) "Table (database)"), an operating system [handle](https://en.wikipedia.org/wiki/Handle_(computing) "Handle (computing)"), a [physical address](https://en.wikipedia.org/wiki/Physical_address "Physical address") on a storage device, or a network address such as a [URL](https://en.wikipedia.org/wiki/URL "URL").

### Formal representation
A reference _R_ is a value that admits one operation, dereference(_R_), which yields a value. Usually the reference is typed so that it returns values of a specific type, e.g.

```r
interface Reference<T> {
  T value();
}
```

Often the reference also admits an assignment operation store(_R_, _x_), meaning it is an [abstract variable](https://en.wikipedia.org/wiki/Abstract_data_type#Abstract_variable "Abstract data type").

### Use
References are widely used in [programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"), especially to efficiently pass large or mutable data as [arguments](https://en.wikipedia.org/wiki/Argument_(computer_science) "Argument (computer science)") to [procedures](https://en.wikipedia.org/wiki/Subroutine "Subroutine"), or to share such data among various uses. In particular, a reference may point to a variable or record that contains references to other data. This idea is the basis of [indirect addressing](https://en.wikipedia.org/wiki/Indirect_addressing "Indirect addressing") and of many [linked data structures](https://en.wikipedia.org/wiki/Linked_data_structure "Linked data structure"), such as [linked lists](https://en.wikipedia.org/wiki/Linked_list "Linked list"). References increase flexibility in where objects can be stored, how they are allocated, and how they are passed between areas of [code](https://en.wikipedia.org/wiki/Code "Code"). As long as one can access a reference to the data, one can access the data through it, and the data itself need not be moved. They also make sharing of data between different code areas easier; each keeps a reference to it.

References can cause significant complexity in a program, partially due to the possibility of [dangling](https://en.wikipedia.org/wiki/Dangling_reference "Dangling reference") and [wild references](https://en.wikipedia.org/wiki/Wild_reference "Wild reference") and partially because the [topology](https://en.wikipedia.org/wiki/Topology "Topology") of data with references is a [directed graph](https://en.wikipedia.org/wiki/Directed_graph "Directed graph"), whose analysis can be quite complicated. Nonetheless, references are still simpler to analyze than [pointers](https://en.wikipedia.org/wiki/Pointer_(computer_programming) "Pointer (computer programming)") due to the absence of [pointer arithmetic](https://en.wikipedia.org/wiki/Pointer_arithmetic "Pointer arithmetic").

The mechanism of references, if varying in implementation, is a fundamental programming language feature common to nearly all modern programming languages. Even some languages that support no direct use of references have some internal or implicit use. For example, the [call by reference](https://en.wikipedia.org/wiki/Evaluation_strategy "Evaluation strategy") calling convention can be implemented with either explicit or implicit use of references.

### Examples
Pointers are the most primitive type of reference. Due to their intimate relationship with the underlying hardware, they are one of the most powerful and efficient types of references. However, also due to this relationship, pointers require a strong understanding by the programmer of the details of memory architecture. Because pointers store a memory location's address, instead of a value directly, inappropriate use of pointers can lead to [undefined behavior](https://en.wikipedia.org/wiki/Undefined_behavior "Undefined behavior") in a program, particularly due to [dangling pointers](https://en.wikipedia.org/wiki/Dangling_pointer "Dangling pointer") or [wild pointers](https://en.wikipedia.org/wiki/Wild_pointer "Wild pointer"). [Smart pointers](https://en.wikipedia.org/wiki/Smart_pointer "Smart pointer") are [opaque data structures](https://en.wikipedia.org/wiki/Opaque_pointer "Opaque pointer") that act like pointers but can only be accessed through particular methods.

A [handle](https://en.wikipedia.org/wiki/Handle_(computing) "Handle (computing)") is an abstract reference, and may be represented in various ways. A common example are [file handles](https://en.wikipedia.org/wiki/File_handle "File handle") (the FILE data structure in the [C standard I/O library](https://en.wikipedia.org/wiki/Stdio "Stdio")), used to abstract file content. It usually represents both the file itself, as when requesting a [lock](https://en.wikipedia.org/wiki/Lock_(computer_science) "Lock (computer science)") on the file, and a specific position within the file's content, as when reading a file.

In [distributed computing](https://en.wikipedia.org/wiki/Distributed_computing "Distributed computing"), the reference may contain more than an address or identifier; it may also include an embedded specification of the network protocols used to locate and access the referenced object, the way information is encoded or serialized. Thus, for example, a [WSDL](https://en.wikipedia.org/wiki/Web_services_description_language "Web services description language") description of a remote web service can be viewed as a form of reference; it includes a complete specification of how to locate and bind to a particular [web service](https://en.wikipedia.org/wiki/Web_service "Web service"). A reference to a [live distributed object](https://en.wikipedia.org/wiki/Live_distributed_object "Live distributed object") is another example: it is a complete specification for how to construct a small software component called a _proxy_ that will subsequently engage in a peer-to-peer interaction, and through which the local machine may gain access to data that is replicated or exists only as a weakly consistent message stream. In all these cases, the reference includes the full set of instructions, or a recipe, for how to access the data; in this sense, it serves the same purpose as an identifier or address in memory.

If we have a set of keys _K_ and a set of data objects _D_, any well-defined (single-valued) function from _K_ to _D_ ∪ {[null](https://en.wikipedia.org/wiki/Nullable_type "Nullable type")} defines a type of reference, where _null_ is the image of a key not referring to anything meaningful.

An alternative representation of such a function is a directed graph called a reachability graph. Here, each datum is represented by a vertex and there is an edge from _u_ to _v_ if the datum in _u_ refers to the datum in _v_. The maximum [out-degree](https://en.wikipedia.org/wiki/Out-degree "Out-degree") is one. These graphs are valuable in [garbage collection](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science) "Garbage collection (computer science)"), where they can be used to separate accessible from [inaccessible objects](https://en.wikipedia.org/wiki/Unreachable_object "Unreachable object").


### External and Internal Storage
In many data structures, large, complex objects are composed of smaller objects. These objects are typically stored in one of two ways:

1. With internal storage, the contents of the smaller object are stored inside the larger object.
2. With external storage, the smaller objects are allocated in their own location, and the larger object only stores references to them.

Internal storage is usually more efficient, because there is a space cost for the references and [dynamic allocation](https://en.wikipedia.org/wiki/Dynamic_memory_allocation "Dynamic memory allocation") metadata, and a time cost associated with dereferencing a reference and with allocating the memory for the smaller objects. Internal storage also enhances [locality of reference](https://en.wikipedia.org/wiki/Locality_of_reference "Locality of reference") by keeping different parts of the same large object close together in memory. However, there are a variety of situations in which external storage is preferred:

- If the [data structure is recursive](https://en.wikipedia.org/wiki/Recursive_data_type "Recursive data type"), meaning it may contain itself. This cannot be represented in the internal way.
- If the larger object is being stored in an area with limited space, such as the stack, then we can prevent running out of storage by storing large component objects in another memory region and referring to them using references.
- If the smaller objects may vary in size, it is often inconvenient or expensive to resize the larger object so that it can still contain them.
- References are often easier to work with and adapt better to new requirements.

Some languages, such as [Java](https://en.wikipedia.org/wiki/Java_(programming_language) "Java (programming language)"), [Smalltalk](https://en.wikipedia.org/wiki/Smalltalk "Smalltalk"), [Python](https://en.wikipedia.org/wiki/Python_(programming_language) "Python (programming language)"), and [Scheme](https://en.wikipedia.org/wiki/Scheme_(programming_language) "Scheme (programming language)"), do not support internal storage. In these languages, all objects are uniformly accessed through references.

## Node
A **node** is a basic unit of a [data structure](https://en.wikipedia.org/wiki/Data_structure "Data structure"), such as a [linked list](https://en.wikipedia.org/wiki/Linked_list "Linked list") or [tree](https://en.wikipedia.org/wiki/Tree_(data_structure) "Tree (data structure)") data structure. Nodes contain [data](https://en.wikipedia.org/wiki/Data "Data") and also may link to other nodes. Links between nodes are often implemented by [pointers](https://en.wikipedia.org/wiki/Pointer_(computer_programming) "Pointer (computer programming)").

### Nodes and Trees
Nodes are often arranged into tree structures. A node represents the information contained in a single data structure. These nodes may contain a value or condition, or possibly serve as another independent data structure. Nodes are represented by a single parent node. The highest point on a tree structure is called a root node, which does not have a parent node, but serves as the parent or 'grandparent' of all of the nodes below it in the tree. The height of a node is determined by the total number of edges on the path from that node to the furthest leaf node, and the height of the tree is equal to the height of the root node. Node depth is determined by the distance between that particular node and the root node. The root node is said to have a depth of zero. Data can be discovered along these network paths. An IP address uses this kind of system of nodes to define its location in a network.

### Definitions
- **Child**: A child node is a node extending from another node. For example, a computer with internet access could be considered a child node of a node representing the internet. The inverse relationship is that of a **parent node**. If node _C_ is a child of node _A_, then _A_ is the parent node of _C_.
- **Degree**: the degree of a node is the number of children of the node.
- **Depth**: the depth of node _A_ is the length of the path from _A_ to the root node. The root node is said to have depth 0.
- **Edge**: the connection between nodes.
- **Forest**: a set of trees.
- **Height**: the height of node _A_ is the length of the longest path through children to a leaf node.
- **Internal node**: a node with at least one child.
- **Leaf node**: a node with no children.
- **Root node**: a node distinguished from the rest of the tree nodes. Usually, it is depicted as the highest node of the tree.
- **Sibling nodes**: these are nodes connected to the same parent node.

### Markup Languages
Another common use of node trees is in [web development](https://en.wikipedia.org/wiki/Web_development "Web development"). In programming, [XML](https://en.wikipedia.org/wiki/XML "XML") is used to communicate information between computer programmers and computers alike. For this reason XML is used to create common [communication protocols](https://en.wikipedia.org/wiki/Communication_protocol "Communication protocol") used in [office productivity software](https://en.wikipedia.org/wiki/Office_productivity_software "Office productivity software"), and serves as the base for the development of modern web [markup languages](https://en.wikipedia.org/wiki/Markup_language "Markup language") like [XHTML](https://en.wikipedia.org/wiki/XHTML "XHTML"). Though similar in how it is approached by a programmer, [HTML](https://en.wikipedia.org/wiki/HTML "HTML") and [CSS](https://en.wikipedia.org/wiki/CSS "CSS") is typically the language used to develop website text and design. While XML, HTML and XHTML provide the language and expression, the [DOM](https://en.wikipedia.org/wiki/Document_Object_Model "Document Object Model") serves as a translator.

#### Node type
Different types of nodes in a tree are represented by specific interfaces. In other words, the node type is defined by how it communicates with other nodes. Each node has a node type property, which specifies the type of node, such as sibling or leaf. For example, if the node type property is the constant properties for a node, this property specifies the type of the node. So if a node type property is the constant node ELEMENT_NODE, one can know that this node object is an object Element. This object uses the Element interface to define all the methods and properties of that particular node.

- **Document** represents the entire document (the root-node of the DOM tree)
- **DocumentFragment** represents a "lightweight" Document object, which can hold a portion of a document
- **DocumentType** provides an interface to the entities defined for the document
- **ProcessingInstruction** represents a processing instruction
- **EntityReference** represents an entity reference
- **Element** represents an element
- **Attr** represents an attribute
- **Text** represents textual content in an element or attribute
- **CDATASection** represents a [CDATA](https://en.wikipedia.org/wiki/CDATA "CDATA") section in a document (text that will NOT be parsed by a parser)
- **Comment** represents a comment
- **Entity** represents an entity
- **Notation** represents a notation declared in the DTD

| NodeType | Named constant              |
| -------- | --------------------------- |
| 1        | ELEMENT_NODE                |
| 2        | ATTRIBUTE_NODE              |
| 3        | TEXT_NODE                   |
| 4        | CDATA_SECTION_NODE          |
| 5        | ENTITY_REFERENCE_NODE       |
| 6        | ENTITY_NODE                 |
| 7        | PROCESSING_INSTRUCTION_NODE |
| 8        | COMMENT_NODE                |
| 9        | DOCUMENT_NODE               |
| 10       | DOCUMENT_TYPE_NODE          |
| 11       | DOCUMENT_FRAGMENT_NODE      |
| 12       | NOTATION_NODE               |

#### Node object
A node object is represented by a single node in a tree. It can be an element node, attribute node, text node, or any type that is described in section "node type". All objects can inherit properties and methods for dealing with parent and child nodes, but not all of the objects have parent or child nodes. For example, with text nodes that cannot have child nodes, trying to add child nodes results in a [DOM](https://en.wikipedia.org/wiki/Document_Object_Model "Document Object Model") error.

Objects in the DOM tree may be addressed and manipulated by using methods on the objects. The public interface of a DOM is specified in its [application programming interface](https://en.wikipedia.org/wiki/Application_programming_interface "Application programming interface") (API). The history of the Document Object Model is intertwined with the history of the "[browser wars](https://en.wikipedia.org/wiki/Browser_wars "Browser wars")" of the late 1990s between [Netscape Navigator](https://en.wikipedia.org/wiki/Netscape_Navigator "Netscape Navigator") and [Microsoft Internet Explorer](https://en.wikipedia.org/wiki/Microsoft_Internet_Explorer "Microsoft Internet Explorer"), as well as with that of [JavaScript](https://en.wikipedia.org/wiki/JavaScript "JavaScript") and [JScript](https://en.wikipedia.org/wiki/JScript "JScript"), the first [scripting languages](https://en.wikipedia.org/wiki/Scripting_language "Scripting language") to be widely implemented in the [layout engines](https://en.wikipedia.org/wiki/Browser_engine "Browser engine") of [web browsers](https://en.wikipedia.org/wiki/Web_browser "Web browser").

## Nested Function
In [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"), a **nested function** (or **nested procedure** or **subroutine**) is a [named](https://en.wikipedia.org/wiki/Identifier "Identifier") [function](https://en.wikipedia.org/wiki/Subroutine "Subroutine") that is defined within another, enclosing, block and is [lexically scoped](https://en.wikipedia.org/wiki/Lexically_scoped "Lexically scoped") within the enclosing block – meaning it is only callable by name within the body of the enclosing block and can use [identifiers](https://en.wikipedia.org/wiki/Identifiers "Identifiers") declared in outer [blocks](https://en.wikipedia.org/wiki/Block_(programming) "Block (programming)"), including outer functions. The enclosing block is typically, but not always, another function.

[Programming language](https://en.wikipedia.org/wiki/Programming_language "Programming language") support for nested functions varies. With respect to [structured programming](https://en.wikipedia.org/wiki/Structured_programming "Structured programming") languages, it is supported in some outdated languages such as [ALGOL](https://en.wikipedia.org/wiki/ALGOL "ALGOL"), [Simula 67](https://en.wikipedia.org/wiki/Simula_67 "Simula 67") and [Pascal](https://en.wikipedia.org/wiki/Pascal_(programming_language) "Pascal (programming language)") and in the commonly used [JavaScript](https://en.wikipedia.org/wiki/JavaScript "JavaScript"). It is commonly supported in [dynamic](https://en.wikipedia.org/wiki/Dynamic_language "Dynamic language") and [functional](https://en.wikipedia.org/wiki/Functional_language "Functional language") languages. However, it is not supported in some commonly used languages including standard [C](https://en.wikipedia.org/wiki/C_language "C language") and [C++](https://en.wikipedia.org/wiki/C%2B%2B "C++").

Other programming technologies provide similar benefit. For example, a [lambda function](https://en.wikipedia.org/wiki/Lambda_function_(computer_programming) "Lambda function (computer programming)") also allows for a function to be defined inside of a function (as well as elsewhere) and allows for similar data hiding and encapsulation. Notably, a lambda function has no name (is anonymous) and therefore cannot be called by name and has no visibility aspect.

### Attributes
The [scope](https://en.wikipedia.org/wiki/Scope_(computer_science) "Scope (computer science)") of a nested function is the block that contains it – be it a function block or block within a function body. It is not visible (cannot be called by name) outside its containing block.

A nested function can use [identifiers](https://en.wikipedia.org/wiki/Identifiers "Identifiers") (i.e. the name of functions, variables, types, classes) declared in any enclosing block, except when they are masked by inner declarations with the same names.

A nested function can be declared within a nested function, recursively, to form a deeply nested structure. A deeply nested function can access identifiers declared in all of its enclosing blocks, including enclosing functions.

Nested functions may in certain situations lead to the creation of a [closure](https://en.wikipedia.org/wiki/Closure_(computer_programming) "Closure (computer programming)"). If it is possible for the nested function to [escape](https://en.wikipedia.org/wiki/Escape_analysis "Escape analysis") the enclosing function, for example if functions are [first class objects](https://en.wikipedia.org/wiki/First_class_object "First class object") and a nested function is passed to another function or returned from the enclosing function, then a closure is created and calls to this function can access the environment of the original function. The frame of the immediately enclosing function must continue to be alive until the last referencing closure dies and [non-local](https://en.wikipedia.org/wiki/Non-local_variable "Non-local variable") [automatic variables](https://en.wikipedia.org/wiki/Automatic_variable "Automatic variable") referenced in closures can therefore not be [stack allocated](https://en.wikipedia.org/wiki/Stack_allocation "Stack allocation") in languages that allow the closure to persist beyond the lifetime of the enclosing block. This is known as the [funarg problem](https://en.wikipedia.org/wiki/Funarg_problem "Funarg problem") and is a key reason why nested functions was not implemented in some simpler languages as it significantly complicates code generation and analysis, especially when functions are nested to various levels, sharing different parts of their environment.

### Value
The nested function technology allows a [programmer](https://en.wikipedia.org/wiki/Programmer "Programmer") to write [source code](https://en.wikipedia.org/wiki/Source_code "Source code") that includes beneficial attributes such as [information hiding](https://en.wikipedia.org/wiki/Information_hiding "Information hiding"), [encapsulation](https://en.wikipedia.org/wiki/Encapsulation_(computer_programming) "Encapsulation (computer programming)") and [decomposition](https://en.wikipedia.org/wiki/Decomposition_(computer_science) "Decomposition (computer science)"). The programmer can divide a task into subtasks which are only meaningful within the context of the task such that the subtask functions are hidden from callers that are not designed to use them.

Block scoping allows functions to share the state of enclosing blocks (including enclosing functions) without passing [parameters](https://en.wikipedia.org/wiki/Parameter_(computer_programming) "Parameter (computer programming)") or using [global variables](https://en.wikipedia.org/wiki/Global_variable "Global variable").

## Parameter (Computer Science)
In [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"), a **parameter** or a **formal argument** is a special kind of [variable](https://en.wikipedia.org/wiki/Variable_(computer_science) "Variable (computer science)") used in a [subroutine](https://en.wikipedia.org/wiki/Subroutine "Subroutine") to refer to one of the pieces of data provided as input to the subroutine. These pieces of data are the values of the **arguments** (often called _actual arguments_ or _actual parameters_) with which the subroutine is going to be called/invoked. An ordered list of parameters is usually included in the [definition of a subroutine](https://en.wikipedia.org/wiki/Function_signature "Function signature"), so that, each time the subroutine is called, its arguments for that call are evaluated, and the resulting values can be assigned to the corresponding parameters.

Unlike [_argument_](https://en.wikipedia.org/wiki/Argument_of_a_function "Argument of a function") in usual mathematical usage, the _argument_ in computer science is the actual input expression passed/supplied to a function, procedure, or routine in the invocation/call statement, whereas the _parameter_ is the variable inside the implementation of the subroutine. For example, if one defines the `add` subroutine as `def add(x, y): return x + y`, then `x, y` are parameters, while if this is called as `add(2, 3)`, then `2, 3` are the arguments. Variables (and expressions thereof) from the calling context can be arguments: if the subroutine is called as `a = 2; b = 3; add(a, b)` then the _variables_ `a, b` are the arguments, not the _values_ `2, 3`. See the [Parameters and arguments](https://en.wikipedia.org/wiki/Parameter_(computer_programming)#Parameters_and_arguments) section for more information.

The semantics for how parameters can be declared and how the (value of) arguments are passed to the parameters of subroutines are defined by the [evaluation strategy](https://en.wikipedia.org/wiki/Evaluation_strategy "Evaluation strategy") of the language, and the details of how this is represented in any particular computer system depend on the [calling convention](https://en.wikipedia.org/wiki/Calling_convention "Calling convention") of that system. In the most common case, [call by value](https://en.wikipedia.org/wiki/Call_by_value "Call by value"), a parameter acts within the subroutine as a new local variable initialized to the value of the argument (a [local](https://en.wikipedia.org/wiki/Local_variable "Local variable") (isolated) copy of the argument if the argument is a variable), but in other cases, e.g. [call by reference](https://en.wikipedia.org/wiki/Call_by_reference "Call by reference"), the argument variable supplied by the caller can be affected by actions within the called subroutine.

### Parameters and Arguments
The terms _parameter_ and _argument_ may have different meanings in different programming languages. Sometimes they are used interchangeably, and the context is used to distinguish the meaning. The term _parameter_ (sometimes called _formal parameter_) is often used to refer to the variable as found in the function [declaration](https://en.wikipedia.org/wiki/Declaration_(computer_programming) "Declaration (computer programming)"), while _argument_ (sometimes called _actual parameter_) refers to the actual input supplied at function call. For example, if one defines a function as `def f(x): ...`, then `x` is the parameter, and if it is called by `a = ...; f(a)` then `a` is the argument. A parameter is an (unbound) variable, while the argument can be a [literal](https://en.wikipedia.org/wiki/Literal_(computer_programming) "Literal (computer programming)") or variable or more complex expression involving literals and variables. In case of call by value, what is passed to the function is the value of the argument – for example, `f(2)` and `a = 2; f(a)` are equivalent calls – while in call by reference, with a variable as argument, what is passed is a reference to that variable - even though the syntax for the function call could stay the same. The specification for [pass-by-reference](https://en.wikipedia.org/wiki/Call_by_reference "Call by reference") or [pass-by-value](https://en.wikipedia.org/wiki/Call_by_value "Call by value") would be made in the function declaration and/or definition.

Parameters appear in procedure definitions; arguments appear in procedure calls. In the function definition `f(x) = x*x` the variable x is a parameter; in the function call `f(2)` the value 2 is the argument of the function. Loosely, a parameter is a type, and an argument is an instance.

A parameter is an intrinsic property of the procedure, included in its definition. For example, in many languages, a procedure to add two supplied integers together and calculate the sum would need two parameters, one for each integer. In general, a procedure may be defined with any number of parameters, or no parameters at all. If a procedure has parameters, the part of its definition that specifies the parameters is called its _parameter list_.

By contrast, the arguments are the expressions supplied to the procedure when it is called, usually one expression matching one of the parameters. Unlike the parameters, which form an unchanging part of the procedure's definition, the arguments may vary from call to call. Each time a procedure is called, the part of the procedure call that specifies the arguments is called the _argument list_.

Although parameters are also commonly referred to as arguments, arguments are sometimes thought of as the actual values or references assigned to the parameter variables when the subroutine is called at [run-time](https://en.wikipedia.org/wiki/Run_time_(program_lifecycle_phase) "Run time (program lifecycle phase)"). When discussing code that is calling into a subroutine, any values or references passed into the subroutine are the arguments, and the place in the code where these values or references are given is the _parameter list_. When discussing the code inside the subroutine definition, the variables in the subroutine's parameter list are the parameters, while the values of the parameters at runtime are the arguments. For example, in C, when dealing with threads it is common to pass in an argument of type void* and cast it to an expected type:

```c
void ThreadFunction(void* pThreadArgument)
{
  // Naming the first parameter 'pThreadArgument' is correct, rather than
  // 'pThreadParameter'. At run time the value we use is an argument. As
  // mentioned above, reserve the term parameter for when discussing
  // subroutine definitions.
}
```

To better understand the difference, consider the following function written in [C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)"):

```c
int Sum(int addend1, int addend2)
{
  return addend1 + addend2;
}
```

The function _Sum_ has two parameters, named _addend1_ and _addend2_. It adds the values passed into the parameters, and returns the result to the subroutine's caller (using a technique automatically supplied by the C compiler).

The code which calls the _Sum_ function might look like this:

```c
int value1 = 40;
int value2 = 2;
int sum_value = Sum(value1, value2);
```

The variables _value1_ and _value2_ are initialized with values. _value1_ and _value2_ are both arguments to the _sum_ function in this context.

At runtime, the values assigned to these variables are passed to the function _Sum_ as arguments. In the _Sum_ function, the parameters _addend1_ and _addend2_ are evaluated, yielding the arguments 40 and 2, respectively. The values of the arguments are added, and the result is returned to the caller, where it is assigned to the variable _sum_value_.

Because of the difference between parameters and arguments, it is possible to supply inappropriate arguments to a procedure. The call may supply too many or too few arguments; one or more of the arguments may be a wrong type; or arguments may be supplied in the wrong order. Any of these situations causes a mismatch between the parameter and argument lists, and the procedure will often return an unintended answer or generate a [runtime error](https://en.wikipedia.org/wiki/Runtime_error "Runtime error").

### Datatypes
In [strongly typed programming languages](https://en.wikipedia.org/wiki/Strongly_typed_programming_language "Strongly typed programming language"), each parameter's [type](https://en.wikipedia.org/wiki/Datatype "Datatype") must be specified in the procedure declaration. Languages using [type inference](https://en.wikipedia.org/wiki/Type_inference "Type inference") attempt to discover the types automatically from the function's body and usage. Dynamically typed programming languages defer type resolution until run-time. Weakly typed languages perform little to no type resolution, relying instead on the programmer for correctness.

Some languages use a special keyword (e.g. _void_) to indicate that the subroutine has no parameters; in formal [type theory](https://en.wikipedia.org/wiki/Type_theory "Type theory"), such functions take an empty parameter list (whose type is not _void_, but rather _[unit](https://en.wikipedia.org/wiki/Unit_type "Unit type")_).

### Argument Passing
The exact mechanism for assigning arguments to parameters, called _argument passing_, depends upon the [evaluation strategy](https://en.wikipedia.org/wiki/Evaluation_strategy "Evaluation strategy") used for that parameter (typically [call by value](https://en.wikipedia.org/wiki/Call_by_value "Call by value")), which may be specified using keywords.

#### Default arguments
Some programming languages such as [Ada](https://en.wikipedia.org/wiki/Ada_(programming_language) "Ada (programming language)"), [C++](https://en.wikipedia.org/wiki/C%2B%2B "C++"), [Clojure](https://en.wikipedia.org/wiki/Clojure "Clojure"), [Common Lisp](https://en.wikipedia.org/wiki/Common_Lisp "Common Lisp"), [Fortran 90](https://en.wikipedia.org/wiki/Fortran_90 "Fortran 90"), [Python](https://en.wikipedia.org/wiki/Python_(programming_language) "Python (programming language)"), [Ruby](https://en.wikipedia.org/wiki/Ruby_(programming_language) "Ruby (programming language)"), [Tcl](https://en.wikipedia.org/wiki/Tcl_(programming_language) "Tcl (programming language)"), and Windows Powershell allow for a [default argument](https://en.wikipedia.org/wiki/Default_argument "Default argument") to be explicitly or implicitly given in a subroutine's declaration. This allows the caller to omit that argument when calling the subroutine. If the default argument is explicitly given, then that value is used if it is not provided by the caller. If the default argument is implicit (sometimes by using a keyword such as _Optional_) then the language provides a well-known value (such as _[null](https://en.wikipedia.org/wiki/Null_pointer "Null pointer")_, _Empty_, zero, an empty string, etc.) if a value is not provided by the caller.

PowerShell example:

```powershell
function doc($g = 1.21) {
    "$g gigawatts? $g gigawatts? Great Scott!"
}

PS  > doc
1.21 gigawatts? 1.21 gigawatts? Great Scott!

PS  > doc 88
88 gigawatts? 88 gigawatts? Great Scott!
```

Default arguments can be seen as a special case of the variable-length argument list.

#### Variable-length parameter lists
Some languages allow subroutines to be defined to accept a [variable number of arguments](https://en.wikipedia.org/wiki/Variadic_function "Variadic function"). For such languages, the subroutines must iterate through the list of arguments.

PowerShell example:

```powershell

function marty {
    $args | foreach { "back to the year $_" }
}

PS  > marty 1985
back to the year 1985

PS  > marty 2015 1985 1955
back to the year 2015
back to the year 1985
back to the year 1955
```

#### Named parameters
Some programming languages—such as [Ada](https://en.wikipedia.org/wiki/Ada_(programming_language) "Ada (programming language)") and [Windows PowerShell](https://en.wikipedia.org/wiki/Windows_PowerShell "Windows PowerShell")—allow subroutines to have [named parameters](https://en.wikipedia.org/wiki/Named_parameter "Named parameter"). This allows the calling code to be more [self-documenting](https://en.wikipedia.org/wiki/Self-documenting "Self-documenting"). It also provides more flexibility to the caller, often allowing the order of the arguments to be changed, or for arguments to be omitted as needed.

PowerShell example:

```powershell
function jennifer($adjectiveYoung, $adjectiveOld) {
    "Young Jennifer: I'm $adjectiveYoung!"
    "Old Jennifer: I'm $adjectiveOld!"
}

PS  > jennifer 'fresh' 'experienced'
Young Jennifer: I'm fresh!
Old Jennifer: I'm experienced!

PS  > jennifer -adjectiveOld 'experienced' -adjectiveYoung 'fresh'
Young Jennifer: I'm fresh!
Old Jennifer: I'm experienced!
```

### Multiple parameters in functional languages
In [lambda calculus](https://en.wikipedia.org/wiki/Lambda_calculus "Lambda calculus"), each function has exactly one parameter. What is thought of as functions with multiple parameters is usually represented in lambda calculus as a function which takes the first argument, and returns a function which takes the rest of the arguments; this is a transformation known as [currying](https://en.wikipedia.org/wiki/Currying "Currying"). Some programming languages, like [ML](https://en.wikipedia.org/wiki/ML_(programming_language) "ML (programming language)") and [Haskell](https://en.wikipedia.org/wiki/Haskell_(programming_language) "Haskell (programming language)"), follow this scheme. In these languages, every function has exactly one parameter, and what may look like the definition of a function of multiple parameters, is actually [syntactic sugar](https://en.wikipedia.org/wiki/Syntactic_sugar "Syntactic sugar") for the definition of a function that returns a function, etc. [Function application](https://en.wikipedia.org/wiki/Function_application "Function application") is [left-associative](https://en.wikipedia.org/wiki/Operator_associativity "Operator associativity") in these languages as well as in lambda calculus, so what looks like an application of a function to multiple arguments is correctly evaluated as the function applied to the first argument, then the resulting function applied to the second argument, etc.

## Scope
In [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"), the **scope** of a [name binding](https://en.wikipedia.org/wiki/Name_binding "Name binding") (an association of a name to an entity, such as a [variable](https://en.wikipedia.org/wiki/Variable_(programming) "Variable (programming)")) is the part of a [program](https://en.wikipedia.org/wiki/Computer_program "Computer program") where the name binding is valid; that is, where the name can be used to refer to the entity. In other parts of the program, the name may refer to a different entity (it may have a different binding), or to nothing at all (it may be unbound). Scope helps prevent [name collisions](https://en.wikipedia.org/wiki/Name_collision "Name collision") by allowing the same name to refer to different objects – as long as the names have separate scopes. The scope of a name binding is also known as the **visibility** of an entity, particularly in older or more technical literature—this is in relation to the referenced entity, not the referencing name.

The term "scope" is also used to refer to the set of _all_ name bindings that are valid within a part of a program or at a given point in a program, which is more correctly referred to as _context_ or _environment_.

Strictly speaking and in practice for most [programming languages](https://en.wikipedia.org/wiki/Programming_language "Programming language"), "part of a program" refers to a portion of [source code](https://en.wikipedia.org/wiki/Source_code "Source code") (area of text), and is known as **lexical scope**. In some languages, however, "part of a program" refers to a portion of [run time](https://en.wikipedia.org/wiki/Runtime_(program_lifecycle_phase) "Runtime (program lifecycle phase)") (period during [execution](https://en.wikipedia.org/wiki/Execution_(computing) "Execution (computing)")), and is known as **dynamic scope**. Both of these terms are somewhat misleading—they misuse technical terms, as discussed in the [definition](https://en.wikipedia.org/wiki/Scope_(computer_science)#Definition)—but the distinction itself is accurate and precise, and these are the standard respective terms. Lexical scope is the main focus of this article, with dynamic scope understood by contrast with lexical scope.

In most cases, name resolution based on lexical scope is relatively straightforward to use and to implement, as in use one can read backwards in the source code to determine to which entity a name refers, and in [implementation](https://en.wikipedia.org/wiki/Programming_language_implementation "Programming language implementation") one can maintain a list of names and contexts when [compiling](https://en.wikipedia.org/wiki/Compiling "Compiling") or [interpreting](https://en.wikipedia.org/wiki/Interpreter_(computing) "Interpreter (computing)") a program. Difficulties arise in [name masking](https://en.wikipedia.org/wiki/Name_masking "Name masking"), [forward declarations](https://en.wikipedia.org/wiki/Forward_declaration "Forward declaration"), and [hoisting](https://en.wikipedia.org/wiki/Variable_hoisting "Variable hoisting"), while considerably subtler ones arise with [non-local variables](https://en.wikipedia.org/wiki/Non-local_variable "Non-local variable"), particularly in [closures](https://en.wikipedia.org/wiki/Closure_(computer_programming) "Closure (computer programming)").

### Definition
The strict definition of the (lexical) "scope" of a name ([identifier](https://en.wikipedia.org/wiki/Identifier "Identifier")) is unambiguous: lexical scope is "the portion of source code in which a binding of a name with an entity applies". This is virtually unchanged from its 1960 definition in the specification of [ALGOL 60](https://en.wikipedia.org/wiki/ALGOL_60 "ALGOL 60"). Representative language specifications follow:

ALGOL 60 (1960)

The following kinds of quantities are distinguished: simple variables, arrays, labels, switches, and procedures. The scope of a quantity is the set of statements and expressions in which the declaration of the identifier associated with that quantity is valid.

[C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)") (2007)

An identifier can denote an object; a function; a tag or a member of a structure, union, or enumeration; a [typedef](https://en.wikipedia.org/wiki/Typedef "Typedef") name; a label name; a macro name; or a macro parameter. The same identifier can denote different entities at different points in the program. [...] For each different entity that an identifier designates, the identifier is _visible_ (i.e., can be used) only within a region of program text called its _scope._

[Go](https://en.wikipedia.org/wiki/Go_(programming_language) "Go (programming language)") (2013)
A declaration binds a non-blank identifier to a constant, type, variable, function, label, or package. [...] The scope of a declared identifier is the extent of source text in which the identifier denotes the specified constant, type, variable, function, label, or package.

Most commonly "scope" refers to when a given name can refer to a given [variable](https://en.wikipedia.org/wiki/Variable_(programming) "Variable (programming)")—when a [declaration](https://en.wikipedia.org/wiki/Declaration_(computer_programming) "Declaration (computer programming)") has effect—but can also apply to other entities, such as functions, types, classes, [labels](https://en.wikipedia.org/wiki/Label_(computer_science) "Label (computer science)"), constants, and enumerations.

### Lexical scope vs. dynamic scope
A fundamental distinction in scope is what "part of a program" means. In languages with **lexical scope** (also called **static scope**), name resolution depends on the location in the source code and the _lexical context_ (also called _static context_), which is defined by where the named variable or function is defined. In contrast, in languages with **dynamic scope** the name resolution depends upon the [program state](https://en.wikipedia.org/wiki/Program_state "Program state") when the name is encountered which is determined by the _execution context_ (also called _runtime context_, _calling context_ or _dynamic context_). In practice, with lexical scope a name is resolved by searching the local lexical context, then if that fails, by searching the outer lexical context, and so on; whereas with dynamic scope, a name is resolved by searching the local execution context, then if that fails, by searching the outer execution context, and so on, progressing up the call stack.
Most modern languages use lexical scope for variables and functions, though dynamic scope is used in some languages, notably some dialects of Lisp, some "scripting" languages, and some [template languages](https://en.wikipedia.org/wiki/Template_language "Template language"). C, Perl 5 offers both lexical and dynamic scope. Even in lexically scoped languages, scope for [closures](https://en.wikipedia.org/wiki/Closure_(computer_science) "Closure (computer science)") can be confusing to the uninitiated, as these depend on the lexical context where the closure is defined, not where it is called.

Lexical resolution can be determined at [compile time](https://en.wikipedia.org/wiki/Compile_time "Compile time"), and is also known as _early binding_, while dynamic resolution can in general only be determined at [run time](https://en.wikipedia.org/wiki/Run_time_(program_lifecycle_phase) "Run time (program lifecycle phase)"), and thus is known as _late binding_.

### Related concepts
In [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming"), [dynamic dispatch](https://en.wikipedia.org/wiki/Dynamic_dispatch "Dynamic dispatch") selects an object [method](https://en.wikipedia.org/wiki/Method_(computer_programming) "Method (computer programming)") at runtime, though whether the actual name binding is done at compile time or run time depends on the language. De facto dynamic scope is common in [macro languages](https://en.wikipedia.org/wiki/Macro_(computer_science) "Macro (computer science)"), which do not directly do name resolution, but instead expand in place.

Some programming frameworks like [AngularJS](https://en.wikipedia.org/wiki/AngularJS#Scope "AngularJS") use the term "scope" to mean something entirely different than how it is used in this article. In those frameworks the scope is just an object of the programming language that they use ([JavaScript](https://en.wikipedia.org/wiki/JavaScript "JavaScript") in case of AngularJS) that is used in certain ways by the framework to emulate dynamic scope in a language that uses lexical scope for its variables. Those [AngularJS scopes](https://en.wikipedia.org/wiki/AngularJS#Scope "AngularJS") can themselves be in context or not in context (using the usual meaning of the term) in any given part of the program, following the usual rules of variable scope of the language like any other object, and using their own [inheritance](https://en.wikipedia.org/wiki/Inheritance_(object-oriented_programming) "Inheritance (object-oriented programming)") and [transclusion](https://en.wikipedia.org/wiki/Transclusion "Transclusion") rules. In the context of AngularJS, sometimes the term "$scope" (with a dollar sign) is used to avoid confusion, but using the dollar sign in variable names is often discouraged by the style guides.

### Use
cope is an important component of [name resolution](https://en.wikipedia.org/wiki/Name_resolution_(programming_languages) "Name resolution (programming languages)"), which is in turn fundamental to [language semantics](https://en.wikipedia.org/wiki/Formal_semantics_of_programming_languages). Name resolution (including scope) varies between programming languages, and within a programming language, varies by type of entity; the rules for scope are called **scope rules** (or **scoping rules**). Together with [namespaces](https://en.wikipedia.org/wiki/Namespaces "Namespaces"), scope rules are crucial in [modular programming](https://en.wikipedia.org/wiki/Modular_programming "Modular programming"), so a change in one part of the program does not break an unrelated part.

### Overview
When discussing scope, there are three basic concepts: _scope,_ _extent,_ and _context._ "Scope" and "context" in particular are frequently confused: scope is a property of a name binding, while context is a property of a part of a program, that is either a portion of source code (_lexical context_ or _static context_) or a portion of [run time](https://en.wikipedia.org/wiki/Run_time_(program_lifecycle_phase) "Run time (program lifecycle phase)") (_execution context,_ _runtime context,_ _calling context_ or _dynamic context_). Execution context consists of lexical context (at the current execution point) plus additional runtime state such as the [call stack](https://en.wikipedia.org/wiki/Call_stack "Call stack"). Strictly speaking, during execution a program enters and exits various name bindings' scopes, and at a point in execution name bindings are "in context" or "not in context", hence name bindings "come into context" or "go out of context" as the program execution enters or exits the scope. However, in practice usage is much looser.

Scope is a source-code level concept, and a property of name bindings, particularly variable or function name bindings—names in the source code are [references](https://en.wikipedia.org/wiki/Reference_(computer_science) "Reference (computer science)") to entities in the program—and is part of the behavior of a compiler or interpreter of a language. As such, issues of scope are similar to [pointers](https://en.wikipedia.org/wiki/Pointer_(computer_programming) "Pointer (computer programming)"), which are a type of reference used in programs more generally. Using the value of a variable when the name is in context but the variable is uninitialized is analogous to dereferencing (accessing the value of) a [wild pointer](https://en.wikipedia.org/wiki/Wild_pointer "Wild pointer"), as it is undefined. However, as variables are not destroyed until they go out of context, the analog of a [dangling pointer](https://en.wikipedia.org/wiki/Dangling_pointer "Dangling pointer") does not exist.

For entities such as variables, scope is a subset of [lifetime](https://en.wikipedia.org/wiki/Object_lifetime "Object lifetime") (also known as [extent](https://en.wikipedia.org/wiki/Variable_(programming)#Scope_and_extent "Variable (programming)"))—a name can only refer to a variable that exists (possibly with undefined value), but variables that exist are not necessarily visible: a variable may exist but be inaccessible (the value is stored but not referred to within a given context), or accessible but not via the given name, in which case it is not in context (the program is "out of the scope of the name"). In other cases "lifetime" is irrelevant—a label (named position in the source code) has lifetime identical with the program (for statically compiled languages), but may be in context or not at a given point in the program, and likewise for [static variables](https://en.wikipedia.org/wiki/Static_variable "Static variable")—a [static global variable](https://en.wikipedia.org/wiki/Static_global_variable "Static global variable") is in context for the entire program, while a [static local variable](https://en.wikipedia.org/wiki/Static_local_variable "Static local variable") is only in context within a function or other local context, but both have lifetime of the entire run of the program.

Determining which entity a name refers to is known as [name resolution](https://en.wikipedia.org/wiki/Name_resolution_(programming_languages) "Name resolution (programming languages)") or [name binding](https://en.wikipedia.org/wiki/Name_binding "Name binding") (particularly in [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming")), and varies between languages. Given a name, the language (properly, the compiler or interpreter) checks all entities that are in context for matches; in case of ambiguity (two entities with the same name, such as a global and local variable with the same name), the name resolution rules are used to distinguish them. Most frequently, name resolution relies on an "inner-to-outer context" rule, such as the Python LEGB (Local, Enclosing, Global, Built-in) rule: names implicitly resolves to the narrowest relevant context. In some cases name resolution can be explicitly specified, such as by the `global` and `nonlocal` keywords in Python; in other cases the default rules cannot be overridden.

When two identical names are in context at the same time, referring to different entities, one says that _[name masking](https://en.wikipedia.org/wiki/Name_masking "Name masking")_ is occurring, where the higher-priority name (usually innermost) is "masking" the lower-priority name. At the level of variables, this is known as [variable shadowing](https://en.wikipedia.org/wiki/Variable_shadowing "Variable shadowing"). Due to the potential for [logic errors](https://en.wikipedia.org/wiki/Logic_error "Logic error") from masking, some languages disallow or discourage masking, raising an error or warning at compile time or run time.

Various [programming languages](https://en.wikipedia.org/wiki/Programming_language "Programming language") have various different scope rules for different kinds of declarations and names. Such scope rules have a large effect on [language semantics](https://en.wikipedia.org/wiki/Formal_semantics_of_programming_languages "Formal semantics of programming languages") and, consequently, on the behavior and correctness of programs. In languages like [C++](https://en.wikipedia.org/wiki/C%2B%2B "C++"), accessing an unbound variable does not have well-defined semantics and may result in [undefined behavior](https://en.wikipedia.org/wiki/Undefined_behavior "Undefined behavior"), similar to referring to a [dangling pointer](https://en.wikipedia.org/wiki/Dangling_pointer "Dangling pointer"); and declarations or names used outside their scope will generate [syntax errors](https://en.wikipedia.org/wiki/Syntax_error "Syntax error").

Scopes are frequently tied to other language constructs and determined implicitly, but many languages also offer constructs specifically for controlling scope.

### Levels Of Scope
Scope can vary from as little as a single expression to as much as the entire program, with many possible gradations in between. The simplest scope rule is global scope—all entities are visible throughout the entire program. The most basic modular scope rule is two-level scope, with a global scope anywhere in the program, and local scope within a function. More sophisticated modular programming allows a separate module scope, where names are visible within the module (private to the module) but not visible outside it. Within a function, some languages, such as C, allow block scope to restrict scope to a subset of a function; others, notably functional languages, allow expression scope, to restrict scope to a single expression. Other scopes include file scope (notably in C) which behaves similarly to module scope, and block scope outside of functions (notably in Perl).

A subtle issue is exactly when a scope begins and ends. In some languages, such as C, a name's scope begins at the name declaration, and thus different names declared within a given block can have different scopes. This requires declaring functions before use, though not necessarily defining them, and requires [forward declaration](https://en.wikipedia.org/wiki/Forward_declaration "Forward declaration") in some cases, notably for mutual recursion. In other languages, such as Python, a name's scope begins at the start of the relevant block where the name is declared (such as the start of a function), regardless of where it is defined, so all names within a given block have the same scope. In JavaScript, the scope of a name declared with `let` or `const` begins at the name declaration, and the scope of a name declared with `var` begins at the start of the function where the name is declared, which is known as _[variable hoisting](https://en.wikipedia.org/wiki/Variable_hoisting "Variable hoisting")_. Behavior of names in context that have undefined value differs: in Python use of undefined names yields a runtime error, while in JavaScript undefined names declared with `var` are usable throughout the function because they are implicitly bound to the value `undefined`.

#### Expression scope
The scope of a name binding is an [expression](https://en.wikipedia.org/wiki/Expression_(computer_science) "Expression (computer science)"), which is known as **expression scope**. Expression scope is available in many languages, especially [functional](https://en.wikipedia.org/wiki/Functional_programming "Functional programming") languages which offer a feature called _[let expressions](https://en.wikipedia.org/wiki/Let_expression "Let expression")_ allowing a declaration's scope to be a single expression. This is convenient if, for example, an intermediate value is needed for a computation. For example, in [Standard ML](https://en.wikipedia.org/wiki/Standard_ML "Standard ML"), if `f()` returns `12`, then `**let val** x = f() **in** x * x **end**` is an expression that evaluates to `144`, using a temporary variable named `x` to avoid calling `f()` twice. Some languages with block scope approximate this functionality by offering syntax for a block to be embedded into an expression; for example, the aforementioned Standard ML expression could be written in [Perl](https://en.wikipedia.org/wiki/Perl "Perl") as `do { my $x = f(); $x * $x }`, or in [GNU C](https://en.wikipedia.org/wiki/GNU_Compiler_Collection "GNU Compiler Collection") as `({ int x = f(); x * x; })`.

In Python, auxiliary variables in generator expressions and list comprehensions (in Python 3) have expression scope.

In C, variable names in a [function prototype](https://en.wikipedia.org/wiki/Function_prototype "Function prototype") have expression scope, known in this context as **function protocol scope**. As the variable names in the prototype are not referred to (they may be different in the actual definition)—they are just dummies—these are often omitted, though they may be used for generating documentation, for instance.

#### Block scope
The scope of a name binding is a [block](https://en.wikipedia.org/wiki/Block_(programming) "Block (programming)"), which is known as **block scope**. Block scope is available in many, but not all, block-structured programming languages. This began with [ALGOL 60](https://en.wikipedia.org/wiki/ALGOL_60 "ALGOL 60"), where "[e]very declaration ... is valid only for that block.", and today is particularly associated with languages in the [Pascal](https://en.wikipedia.org/wiki/Pascal_(programming_language) "Pascal (programming language)") and [C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)") families and traditions. Most often this block is contained within a function, thus restricting the scope to a part of a function, but in some cases, such as Perl, the block may not be within a function.

```c
unsigned int sum_of_squares(const unsigned int N) {
  unsigned int ret = 0;
  for (unsigned int n = 1; n <= N; n++) {
    const unsigned int n_squared = n * n;
    ret += n_squared;
  }
  return ret;
}
```

A representative example of the use of block scope is the C code shown here, where two variables are scoped to the loop: the loop variable n, which is initialized once and incremented on each iteration of the loop, and the auxiliary variable n_squared, which is initialized at each iteration. The purpose is to avoid adding variables to the function scope that are only relevant to a particular block—for example, this prevents errors where the generic loop variable i has accidentally already been set to another value. In this example the expression `n * n` would generally not be assigned to an auxiliary variable, and the body of the loop would simply be written `ret += n * n` but in more complicated examples auxiliary variables are useful.

Blocks are primarily used for control flow, such as with if, while, and for loops, and in these cases block scope means the scope of variable depends on the structure of a function's flow of execution. However, languages with block scope typically also allow the use of "naked" blocks, whose sole purpose is to allow fine-grained control of variable scope. For example, an auxiliary variable may be defined in a block, then used (say, added to a variable with function scope) and discarded when the block ends, or a while loop might be enclosed in a block that initializes variables used inside the loop that should only be initialized once.

A subtlety of several programming languages, such as [Algol 68](https://en.wikipedia.org/wiki/Algol_68 "Algol 68") and C (demonstrated in this example and standardized since [C99](https://en.wikipedia.org/wiki/C99 "C99")), is that block-scope variables can be declared not only within the body of the block, but also within the control statement, if any. This is analogous to function parameters, which are declared in the function declaration (before the block of the function body starts), and in scope for the whole function body. This is primarily used in [for loops](https://en.wikipedia.org/wiki/For_loop "For loop"), which have an initialization statement separate from the loop condition, unlike while loops, and is a common idiom.

Block scope can be used for shadowing. In this example, inside the block the auxiliary variable could also have been called n, shadowing the parameter name, but this is considered poor style due to the potential for errors. Furthermore, some descendants of C, such as Java and C#, despite having support for block scope (in that a local variable can be made to go out of context before the end of a function), do not allow one local variable to hide another. In such languages, the attempted declaration of the second n would result in a syntax error, and one of the n variables would have to be renamed.

If a block is used to set the value of a variable, block scope requires that the variable be declared outside of the block. This complicates the use of conditional statements with [single assignment](https://en.wikipedia.org/wiki/Single_assignment "Single assignment"). For example, in Python, which does not use block scope, one may initialize a variable as such:
```python
if c:
    a = "foo"
else:
    a = ""
```

where `a` is accessible after the `if` statement.

In Perl, which has block scope, this instead requires declaring the variable prior to the block:
```perl
my $a;
if (c) {
    $a = 'foo';
} else {
    $a = '';
}
```

Often this is instead rewritten using multiple assignment, initializing the variable to a default value. In Python (where it is not necessary) this would be:
```python
a = ""
if c:
    a = "foo"
```

while in Perl this would be:
```perl
my $a = '';
if (c) {
    $a = 'foo';
}
```

In case of a single variable assignment, an alternative is to use the [ternary operator](https://en.wikipedia.org/wiki/Ternary_operator "Ternary operator") to avoid a block, but this is not in general possible for multiple variable assignments, and is difficult to read for complex logic.

This is a more significant issue in C, notably for string assignment, as string initialization can automatically allocate memory, while string assignment to an already initialized variable requires allocating memory, a string copy, and checking that these are successful.
```c
{
  my $counter = 0;
  sub increment_counter {
      return  ++$counter;
  }
}
```

Some languages allow the concept of block scope to be applied, to varying extents, outside of a function. For example, in the Perl snippet at right, `$counter` is a variable name with block scope (due to the use of the `my` keyword), while `increment_counter` is a function name with global scope. Each call to `increment_counter` will increase the value of `$counter` by one, and return the new value. Code outside of this block can call `increment_counter`, but cannot otherwise obtain or alter the value of `$counter`. This idiom allows one to define closures in Perl.

#### Function scope
When the scope of variables declared within a function does not extend beyond that function, this is known as **function scope**. Function scope is available in most programming languages which offer a way to create a _[local variable](https://en.wikipedia.org/wiki/Local_variable "Local variable")_ in a function or [subroutine](https://en.wikipedia.org/wiki/Subroutine "Subroutine"): a variable whose scope ends (that goes out of context) when the function returns. In most cases the lifetime of the variable is the duration of the function call—it is an [automatic variable](https://en.wikipedia.org/wiki/Automatic_variable "Automatic variable"), created when the function starts (or the variable is declared), destroyed when the function returns—while the scope of the variable is within the function, though the meaning of "within" depends on whether scope is lexical or dynamic. However, some languages, such as C, also provide for [static local variables](https://en.wikipedia.org/wiki/Static_local_variable "Static local variable"), where the lifetime of the variable is the entire lifetime of the program, but the variable is only in context when inside the function. In the case of static local variables, the variable is created when the program initializes, and destroyed only when the program terminates, as with a [static global variable](https://en.wikipedia.org/wiki/Static_global_variable "Static global variable"), but is only in context within a function, like an automatic local variable.

Importantly, in lexical scope a variable with function scope has scope only within the _lexical context_ of the function: it goes out of context when another function is called within the function, and comes back into context when the function returns—called functions have no access to the local variables of calling functions, and local variables are only in context within the body of the function in which they are declared. By contrast, in dynamic scope, the scope extends to the _execution context_ of the function: local variables _stay in context_ when another function is called, only going out of context when the defining function ends, and thus local variables are in context of the function in which they are defined _and all called functions_. In languages with lexical scope and [nested functions](https://en.wikipedia.org/wiki/Nested_function "Nested function"), local variables are in context for nested functions, since these are within the same lexical context, but not for other functions that are not lexically nested. A local variable of an enclosing function is known as a [non-local variable](https://en.wikipedia.org/wiki/Non-local_variable "Non-local variable") for the nested function. Function scope is also applicable to [anonymous functions](https://en.wikipedia.org/wiki/Anonymous_function "Anonymous function").

```python
def square(n):
    return n * n

def sum_of_squares(n):
    total = 0 
    i = 0
    while i <= n:
        total += square(i)
        i += 1
    return total
```

For example, in the snippet of Python code on the right, two functions are defined: `square` and `sum_of_squares`. `square` computes the square of a number; `sum_of_squares` computes the sum of all squares up to a number. (For example, `square(4)` is 42 = `16`, and `sum_of_squares(4)` is 02 + 12 + 22 + 32 + 42 = `30`.)

Each of these functions has a variable named n that represents the argument to the function. These two n variables are completely separate and unrelated, despite having the same name, because they are lexically scoped local variables with function scope: each one's scope is its own, lexically separate function and thus, they don't overlap. Therefore, `sum_of_squares` can call `square` without its own n being altered. Similarly, `sum_of_squares` has variables named total and i; these variables, because of their limited scope, will not interfere with any variables named total or i that might belong to any other function. In other words, there is no risk of a _name collision_ between these names and any unrelated names, even if they are identical.

No name masking is occurring: only one variable named n is in context at any given time, as the scopes do not overlap. By contrast, were a similar fragment to be written in a language with dynamic scope, the n in the calling function would remain in context in the called function—the scopes would overlap—and would be masked ("shadowed") by the new n in the called function.

Function scope is significantly more complicated if functions are first-class objects and can be created locally to a function and then returned. In this case any variables in the nested function that are not local to it (unbound variables in the function definition, that resolve to variables in an enclosing context) create a [closure](https://en.wikipedia.org/wiki/Closure_(computer_science) "Closure (computer science)"), as not only the function itself, but also its context (of variables) must be returned, and then potentially called in a different context. This requires significantly more support from the compiler, and can complicate program analysis.

#### File scope
The scope of a name binding is a file, which is known as **file scope**. File scope is largely particular to C (and C++), where scope of variables and functions declared at the top level of a file (not within any function) is for the entire file—or rather for C, from the declaration until the end of the source file, or more precisely [translation unit](https://en.wikipedia.org/wiki/Translation_unit_(programming) "Translation unit (programming)") (internal linking). This can be seen as a form of module scope, where modules are identified with files, and in more modern languages is replaced by an explicit module scope. Due to the presence of include statements, which add variables and functions to the internal context and may themselves call further include statements, it can be difficult to determine what is in context in the body of a file.

In the C code snippet above, the function name `sum_of_squares` has global scope (in C, extern linkage). Adding `static` to the function signature would result in file scope (internal linkage).

#### Module scope
The scope of a name binding is a module, which is known as **module scope**. Module scope is available in [modular programming languages](https://en.wikipedia.org/wiki/Modular_programming "Modular programming") where modules (which may span various files) are the basic unit of a complex program, as they allow [information hiding](https://en.wikipedia.org/wiki/Information_hiding "Information hiding") and exposing a limited interface. Module scope was pioneered in the [Modula](https://en.wikipedia.org/wiki/Modula "Modula") family of languages, and Python (which was influenced by Modula) is a representative contemporary example.

In some [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming") languages that lack direct support for modules, such as C++ before C++20, a similar structure is instead provided by the class hierarchy, where classes are the basic unit of the program, and a class can have private methods. This is properly understood in the context of [dynamic dispatch](https://en.wikipedia.org/wiki/Dynamic_dispatch "Dynamic dispatch") rather than name resolution and scope, though they often play analogous roles. In some cases both these facilities are available, such as in Python, which has both modules and classes, and code organization (as a module-level function or a conventionally private method) is a choice of the programmer.

#### Global scope
The scope of a name binding is an entire program, which is known as **global scope**. Variable names with global scope—called _[global variables](https://en.wikipedia.org/wiki/Global_variables "Global variables")_—are frequently considered bad practice, at least in some languages, due to the possibility of name collisions and unintentional masking, together with poor modularity, and function scope or block scope are considered preferable. However, global scope is typically used (depending on the language) for various other sorts of names, such as names of functions, names of [classes](https://en.wikipedia.org/wiki/Class_(computer_programming) "Class (computer programming)") and names of other [data types](https://en.wikipedia.org/wiki/Data_type "Data type"). In these cases mechanisms such as [namespaces](https://en.wikipedia.org/wiki/Namespaces "Namespaces") are used to avoid collisions.

### Lexical scope vs. dynamic scope 
The use of local variables — of variable names with limited scope, that only exist within a specific function — helps avoid the risk of a name collision between two identically named variables. However, there are two very different approaches to answering this question: What does it mean to be "within" a function?

In **lexical scope** (or **lexical scoping**; also called **static scope** or **static scoping**), if a variable name's scope is a certain function, then its scope is the program text of the function definition: within that text, the variable name exists, and is bound to the variable's value, but outside that text, the variable name does not exist. By contrast, in **dynamic scope** (or **dynamic scoping**), if a variable name's scope is a certain function, then its scope is the time-period during which the function is executing: while the function is running, the variable name exists, and is bound to its value, but after the function returns, the variable name does not exist. This means that if function `f` invokes a separately defined function `g`, then under lexical scope, function `g` does _not_ have access to `f`'s local variables (assuming the text of `g` is not inside the text of `f`), while under dynamic scope, function `g` _does_ have access to `f`'s local variables (since `g` is invoked during the invocation of `f`).

```bash
$ # bash language
$ x=1
$ function g() { echo $x ; x=2 ; }
$ function f() { local x=3 ; g ; }
$ f # does this print 1, or 3?
3
$ echo $x # does this print 1, or 2?
1
```

Consider, for example, the program on the right. The first line, `x=1`, creates a global variable `x` and initializes it to `1`. The second line, `function g() { echo $x ; x=2 ; }`, defines a function `g` that prints out ("echoes") the current value of `x`, and then sets `x` to `2` (overwriting the previous value). The third line, `function f() { local x=3 ; g ; }` defines a function `f` that creates a local variable `x` (hiding the identically named global variable) and initializes it to `3`, and then calls `g`. The fourth line, `f`, calls `f`. The fifth line, `echo $x`, prints out the current value of `x`.

So, what exactly does this program print? It depends on the scope rules. If the language of this program is one that uses lexical scope, then `g` prints and modifies the global variable `x` (because `g` is defined outside `f`), so the program prints `1` and then `2`. By contrast, if this language uses dynamic scope, then `g` prints and modifies `f`'s local variable `x` (because `g` is called from within `f`), so the program prints `3` and then `1`. (As it happens, the language of the program is [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell) "Bash (Unix shell)"), which uses dynamic scope; so the program prints `3` and then `1`. If the same code was run with [ksh93](https://en.wikipedia.org/wiki/KornShell "KornShell") which uses lexical scope, the results would be different.)

### Lexical scope (Static Scope)
With **lexical scope**, a name always refers to its lexical context. This is a property of the program text and is made independent of the runtime [call stack](https://en.wikipedia.org/wiki/Call_stack "Call stack") by the language implementation. Because this matching only requires analysis of the static program text, this type of scope is also called **static scope**. Lexical scope is standard in all [ALGOL](https://en.wikipedia.org/wiki/ALGOL "ALGOL")-based languages such as [Pascal](https://en.wikipedia.org/wiki/Pascal_(programming_language) "Pascal (programming language)"), [Modula-2](https://en.wikipedia.org/wiki/Modula-2 "Modula-2") and [Ada](https://en.wikipedia.org/wiki/Ada_(programming_language) "Ada (programming language)") as well as in modern functional languages such as [ML](https://en.wikipedia.org/wiki/ML_(programming_language) "ML (programming language)") and [Haskell](https://en.wikipedia.org/wiki/Haskell_(programming_language) "Haskell (programming language)"). It is also used in the [C language](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)") and its syntactic and semantic relatives, although with different kinds of limitations. Static scope allows the programmer to reason about object references such as parameters, variables, constants, types, functions, etc. as simple name substitutions. This makes it much easier to make modular code and reason about it, since the local naming structure can be understood in isolation. In contrast, dynamic scope forces the programmer to anticipate all possible execution contexts in which the module's code may be invoked.

program A;

```pascal
var I:integer;
    K:char;

    procedure B;
    var K:real;
        L:integer;

        procedure C;
        var M:real;
        begin
         (*scope A+B+C*)
        end;

     (*scope A+B*)
    end;

 (*scope A*)
end.
```

For example, Pascal is lexically scoped. Consider the Pascal program fragment at right. The variable `I` is visible at all points, because it is never hidden by another variable of the same name. The `char` variable `K` is visible only in the main program because it is hidden by the `real` variable `K` visible in procedure `B` and `C` only. Variable `L` is also visible only in procedure `B` and `C` but it does not hide any other variable. Variable `M` is only visible in procedure `C` and therefore not accessible either from procedure `B` or the main program. Also, procedure `C` is visible only in procedure `B` and can therefore not be called from the main program.

There could have been another procedure `C` declared in the program outside of procedure `B`. The place in the program where "`C`" is mentioned then determines which of the two procedures named `C` it represents, thus precisely analogous with the scope of variables.

Correct implementation of lexical scope in languages with [first-class](https://en.wikipedia.org/wiki/First-class_function "First-class function") [nested functions](https://en.wikipedia.org/wiki/Nested_function "Nested function") is not trivial, as it requires each function value to carry with it a record of the values of the variables that it depends on (the pair of the function and this context is called a [closure](https://en.wikipedia.org/wiki/Closure_(computer_science) "Closure (computer science)")). Depending on implementation and [computer architecture](https://en.wikipedia.org/wiki/Computer_architecture "Computer architecture"), variable [lookup](https://en.wikipedia.org/wiki/Lookup "Lookup") _may_ become slightly inefficient when very deeply lexically [nested](https://en.wikipedia.org/wiki/Nesting_(computing) "Nesting (computing)") functions are used, although there are well-known techniques to mitigate this. Also, for nested functions that only refer to their own arguments and (immediately) local variables, all relative locations can be known at [compile time](https://en.wikipedia.org/wiki/Compile_time "Compile time"). No overhead at all is therefore incurred when using that type of nested function. The same applies to particular parts of a program where nested functions are not used, and, naturally, to programs written in a language where nested functions are not available (such as in the C language).

### Dynamic scope
With **dynamic scope**, a name refers to execution context. In technical terms, this means that each name has a global [stack](https://en.wikipedia.org/wiki/Stack_(data_structure) "Stack (data structure)") of bindings. Introducing a local variable with name `x` pushes a binding onto the global `x` stack (which may have been empty), which is popped off when the [control flow](https://en.wikipedia.org/wiki/Control_flow "Control flow") leaves the scope. Evaluating `x` in any context always yields the top binding. Note that this cannot be done at compile-time because the binding stack only exists at [run-time](https://en.wikipedia.org/wiki/Run_time_(program_lifecycle_phase) "Run time (program lifecycle phase)"), which is why this type of scope is called _dynamic_ scope.

Dynamic scope is uncommon in modern languages.

Generally, certain [blocks](https://en.wikipedia.org/wiki/Block_(programming) "Block (programming)") are defined to create bindings whose lifetime is the execution time of the block; this adds some features of static scope to the dynamic scope process. However, since a section of code can be called from many different locations and situations, it can be difficult to determine at the outset what bindings will apply when a variable is used (or if one exists at all). This can be beneficial; application of the [principle of least knowledge](https://en.wikipedia.org/wiki/Principle_of_least_knowledge "Principle of least knowledge") suggests that code avoid depending on the _reasons_ for (or circumstances of) a variable's value, but simply use the value according to the variable's definition. This narrow interpretation of shared data can provide a very flexible system for adapting the behavior of a function to the current state (or policy) of the system. However, this benefit relies on careful documentation of all variables used this way as well as on careful avoidance of assumptions about a variable's behavior, and does not provide any mechanism to detect interference between different parts of a program. Some languages, like [Perl](https://en.wikipedia.org/wiki/Perl "Perl") and [Common Lisp](https://en.wikipedia.org/wiki/Common_Lisp "Common Lisp"), allow the programmer to choose static or dynamic scope when defining or redefining a variable. Examples of languages that use dynamic scope include [Logo](https://en.wikipedia.org/wiki/Logo_(programming_language) "Logo (programming language)"), [Emacs Lisp](https://en.wikipedia.org/wiki/Emacs_Lisp "Emacs Lisp"), [LaTeX](https://en.wikipedia.org/wiki/LaTeX "LaTeX") and the shell languages [bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell) "Bash (Unix shell)"), [dash](https://en.wikipedia.org/wiki/Debian_Almquist_shell "Debian Almquist shell"), and [PowerShell](https://en.wikipedia.org/wiki/Windows_PowerShell "Windows PowerShell").

Dynamic scope is fairly easy to implement. To find an name's value, the program could traverse the runtime stack, checking each activation record (each function's stack frame) for a value for the name. In practice, this is made more efficient via the use of an [association list](https://en.wikipedia.org/wiki/Association_list "Association list"), which is a stack of name/value pairs. Pairs are pushed onto this stack whenever declarations are made, and popped whenever variables go out of context. _Shallow binding_ is an alternative strategy that is considerably faster, making use of a _central reference table_, which associates each name with its own stack of meanings. This avoids a linear search during run-time to find a particular name, but care should be taken to properly maintain this table. Note that both of these strategies assume a last-in-first-out ([LIFO](https://en.wikipedia.org/wiki/LIFO_(computing) "LIFO (computing)")) ordering to bindings for any one variable; in practice all bindings are so ordered.

An even simpler implementation is the representation of dynamic variables with simple global variables. The local binding is performed by saving the original value in an anonymous location on the stack that is invisible to the program. When that binding scope terminates, the original value is restored from this location. In fact, dynamic scope originated in this manner. Early implementations of Lisp used this obvious strategy for implementing local variables, and the practice survives in some dialects which are still in use, such as GNU Emacs Lisp. Lexical scope was introduced into Lisp later. This is equivalent to the above shallow binding scheme, except that the central reference table is simply the global variable binding context, in which the current meaning of the variable is its global value. Maintaining global variables isn't complex. For instance, a symbol object can have a dedicated slot for its global value.

Dynamic scope provides an excellent abstraction for [thread-local storage](https://en.wikipedia.org/wiki/Thread-local_storage "Thread-local storage"), but if it is used that way it cannot be based on saving and restoring a global variable. A possible implementation strategy is for each variable to have a thread-local key. When the variable is accessed, the thread-local key is used to access the thread-local memory location (by code generated by the compiler, which knows which variables are dynamic and which are lexical). If the thread-local key does not exist for the calling thread, then the global location is used. When a variable is locally bound, the prior value is stored in a hidden location on the stack. The thread-local storage is created under the variable's key, and the new value is stored there. Further nested overrides of the variable within that thread simply save and restore this thread-local location. When the initial, outermost override's context terminates, the thread-local key is deleted, exposing the global version of the variable once again to that thread.

With [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency "Referential transparency") the dynamic scope is restricted to the argument stack of the current function only, and coincides with the lexical scope.

#### Macro expansion
In modern languages, [macro expansion](https://en.wikipedia.org/wiki/Macro_expansion "Macro expansion") in a [preprocessor](https://en.wikipedia.org/wiki/Preprocessor "Preprocessor") is a key example of de facto dynamic scope. The macro language itself only transforms the source code, without resolving names, but since the expansion is done in place, when the names in the expanded text are then resolved (notably free variables), they are resolved based on where they are expanded (loosely "called"), as if dynamic scope were occurring.

The [C preprocessor](https://en.wikipedia.org/wiki/C_preprocessor "C preprocessor"), used for [macro expansion](https://en.wikipedia.org/wiki/Macro_expansion "Macro expansion"), has de facto dynamic scope, as it does not do name resolution by itself and it is independent of where the macro is defined. For example, the macro:

`#define ADD_A(x) x + a`

will expand to add `a` to the passed variable, with this name only later resolved by the compiler based on where the macro `ADD_A` is "called" (properly, expanded). Properly, the C preprocessor only does [lexical analysis](https://en.wikipedia.org/wiki/Lexical_analysis "Lexical analysis"), expanding the macro during the tokenization stage, but not parsing into a syntax tree or doing name resolution.

For example, in the following code, the name `a` in the macro is resolved (after expansion) to the local variable at the expansion site:

```c
#define ADD_A(x) x + a

void add_one(int *x) {
  const int a = 1;
  *x = ADD_A(*x);
}

void add_two(int *x) {
  const int a = 2;
  *x = ADD_A(*x);
}
```

### Qualified names
As we have seen, one of the key reasons for scope is that it helps prevent name collisions, by allowing identical names to refer to distinct things, with the restriction that the names must have separate scopes. Sometimes this restriction is inconvenient; when many different things need to be accessible throughout a program, they generally all need names with global scope, so different techniques are required to avoid name collisions.

To address this, many languages offer mechanisms for organizing global names. The details of these mechanisms, and the terms used, depend on the language; but the general idea is that a group of names can itself be given a name — a prefix — and, when necessary, an entity can be referred to by a _qualified name_ consisting of the name plus the prefix. Normally such names will have, in a sense, two sets of scopes: a scope (usually the global scope) in which the qualified name is visible, and one or more narrower scopes in which the _unqualified name_ (without the prefix) is visible as well. And normally these groups can themselves be organized into groups; that is, they can be _nested_.

Although many languages support this concept, the details vary greatly. Some languages have mechanisms, such as _namespaces_ in [C++](https://en.wikipedia.org/wiki/C%2B%2B "C++") and [C#](https://en.wikipedia.org/wiki/C_Sharp_(programming_language) "C Sharp (programming language)"), that serve almost exclusively to enable global names to be organized into groups. Other languages have mechanisms, such as _packages_ in [Ada](https://en.wikipedia.org/wiki/Ada_(programming_language) "Ada (programming language)") and _structures_ in [Standard ML](https://en.wikipedia.org/wiki/Standard_ML "Standard ML"), that combine this with the additional purpose of allowing some names to be visible only to other members of their group. And object-oriented languages often allow classes or singleton objects to fulfill this purpose (whether or not they _also_ have a mechanism for which this is the primary purpose). Furthermore, languages often meld these approaches; for example, [Perl](https://en.wikipedia.org/wiki/Perl "Perl")'s packages are largely similar to C++'s namespaces, but optionally double as classes for object-oriented programming; and [Java](https://en.wikipedia.org/wiki/Java_(programming_language) "Java (programming language)") organizes its variables and functions into classes, but then organizes those classes into Ada-like packages.

## Block
In [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"), a **block** or **code block** or **block of code** is a lexical structure of [source code](https://en.wikipedia.org/wiki/Source_code "Source code") which is grouped together. Blocks consist of one or more [declarations](https://en.wikipedia.org/wiki/Declaration_(computer_programming) "Declaration (computer programming)") and [statements](https://en.wikipedia.org/wiki/Statement_(computer_science) "Statement (computer science)"). A [programming language](https://en.wikipedia.org/wiki/Programming_language "Programming language") that permits the creation of blocks, including blocks [nested](https://en.wikipedia.org/wiki/Nesting_(computing) "Nesting (computing)") within other blocks, is called a **block-structured programming language**. Blocks are fundamental to [structured programming](https://en.wikipedia.org/wiki/Structured_programming "Structured programming"), where [control structures](https://en.wikipedia.org/wiki/Control_structure "Control structure") are formed from blocks.

Blocks have two functions: to group statements so that they can be treated as one statement, and to define [scopes](https://en.wikipedia.org/wiki/Scope_(computer_science) "Scope (computer science)") for [names](https://en.wikipedia.org/wiki/Name_binding "Name binding") to distinguish them from the same name used elsewhere. In a block-structured programming language, the objects named in outer blocks are visible inside inner blocks, unless they are [masked](https://en.wikipedia.org/wiki/Name_masking "Name masking") by an [object](https://en.wikipedia.org/wiki/Object_(computer_science) "Object (computer science)") declared with the same name.

## Local Variable
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), a **local variable** is a [variable](https://en.wikipedia.org/wiki/Variable_(programming) "Variable (programming)") that is given _local [scope](https://en.wikipedia.org/wiki/Scope_(programming) "Scope (programming)")_. A local variable reference in the [function](https://en.wikipedia.org/wiki/Subroutine "Subroutine") or [block](https://en.wikipedia.org/wiki/Block_(programming) "Block (programming)") in which it is declared overrides the same variable name in the larger scope. In [programming languages](https://en.wikipedia.org/wiki/Programming_language "Programming language") with only two levels of visibility, local variables are contrasted with [global variables](https://en.wikipedia.org/wiki/Global_variables "Global variables"). On the other hand, many [ALGOL](https://en.wikipedia.org/wiki/ALGOL "ALGOL")-derived languages allow any number of nested levels of visibility, with private variables, functions, constants and types hidden within them, either by nested blocks or [nested functions](https://en.wikipedia.org/wiki/Nested_function "Nested function"). Local variables are fundamental to [procedural programming](https://en.wikipedia.org/wiki/Procedural_programming "Procedural programming"), and more generally [modular programming](https://en.wikipedia.org/wiki/Modular_programming "Modular programming"): variables of local scope are used to avoid issues with [side-effects](https://en.wikipedia.org/wiki/Side-effect_(computer_science) "Side-effect (computer science)") that can occur with [global variables](https://en.wikipedia.org/wiki/Global_variable "Global variable").

### Scope
Local variables may have a lexical or dynamic [scope](https://en.wikipedia.org/wiki/Scope_(programming) "Scope (programming)"), though lexical (static) scoping is far more common. In lexical scoping (or lexical scope; also called static scoping or static scope), if a variable name's scope is a certain block, then its scope is the program text of the block definition: within that block's text, the variable name exists, and is bound to the variable's value, but outside that block's text, the variable name does not exist. By contrast, in dynamic scoping (or dynamic scope), if a variable name's scope is a certain block, then its scope is that block and all functions transitively called by that block (except when overridden again by another declaration); after the block ends, the variable name does not exist. Some languages, like [Perl](https://en.wikipedia.org/wiki/Perl "Perl") and [Common Lisp](https://en.wikipedia.org/wiki/Common_Lisp "Common Lisp"), allow the programmer to choose static or dynamic scoping when defining or redefining a variable. Examples of languages that use dynamic scoping include [Logo](https://en.wikipedia.org/wiki/Logo_(programming_language) "Logo (programming language)"), [Emacs lisp](https://en.wikipedia.org/wiki/Emacs_lisp "Emacs lisp"), and the shell languages [bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell) "Bash (Unix shell)"), [dash](https://en.wikipedia.org/wiki/Dash_(shell) "Dash (shell)"), and the MirBSD Korn shell ([mksh](https://en.wikipedia.org/wiki/Mksh "Mksh"))'s "local" declaration. Most other languages provide lexically scoped local variables.

In most languages, local variables are [automatic variables](https://en.wikipedia.org/wiki/Automatic_variable "Automatic variable") stored on the [call stack](https://en.wikipedia.org/wiki/Call_stack "Call stack") directly. This means that when a [recursive function](https://en.wikipedia.org/wiki/Recursion_(computer_science) "Recursion (computer science)") calls itself, local variables in each instance of the function are given distinct [addresses](https://en.wikipedia.org/wiki/Memory_address "Memory address"). Hence variables of this scope can be declared, written to, and read, without any risk of [side-effects](https://en.wikipedia.org/wiki/Side-effect_(computer_science) "Side-effect (computer science)") to functions outside of the block in which they are declared.

Programming languages that employ _[call by value](https://en.wikipedia.org/wiki/Call_by_value "Call by value")_ semantics provide a called subroutine with its own local copy of the [arguments](https://en.wikipedia.org/wiki/Function_argument "Function argument") passed to it. In most languages, these local parameters are treated the same as other local variables within the subroutine. In contrast, _[call by reference](https://en.wikipedia.org/wiki/Call_by_reference "Call by reference")_ and _[call by name](https://en.wikipedia.org/wiki/Call_by_name "Call by name")_ semantics allow the parameters to act as aliases of the values passed as arguments, allowing the subroutine to modify variables outside its own scope.

### Static local variables
A special type of local variable, called a _static local,_ is available in many mainstream languages (including [C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)")/[C++](https://en.wikipedia.org/wiki/C%2B%2B "C++"), [Visual Basic](https://en.wikipedia.org/wiki/Visual_Basic "Visual Basic"), [VB.NET](https://en.wikipedia.org/wiki/Visual_Basic_(.NET) "Visual Basic (.NET)") and [PHP](https://en.wikipedia.org/wiki/PHP "PHP")) which allows a value to be retained from one call of the function to another – it is a [static variable](https://en.wikipedia.org/wiki/Static_variable "Static variable") with local scope. In this case, recursive calls to the function also have access to the (single, [statically allocated](https://en.wikipedia.org/wiki/Static_memory_allocation "Static memory allocation")) variable. In all of the above languages, static variables are declared as such with a special _storage class_ keyword (e.g., `static`).

Static locals in global functions have the same lifetime as [static global variables](https://en.wikipedia.org/wiki/Static_global_variable "Static global variable"), because their value remains in memory for the life of the program, but have [function scope](https://en.wikipedia.org/wiki/Function_scope "Function scope") (not global scope), as with automatic local variables.

This is distinct from other usages of the [`static` keyword](https://en.wikipedia.org/wiki/Static_(keyword) "Static (keyword)"), which has several different meanings in various languages.

## Global Variable
In [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"), a **global variable** is a variable with global [scope](https://en.wikipedia.org/wiki/Scope_(programming) "Scope (programming)"), meaning that it is visible (hence accessible) throughout the program, unless [shadowed](https://en.wikipedia.org/wiki/Variable_shadowing "Variable shadowing"). The set of all global variables is known as the _global environment_ or _global state._ In [compiled languages](https://en.wikipedia.org/wiki/Compiled_language "Compiled language"), global variables are generally [static variables](https://en.wikipedia.org/wiki/Static_variable "Static variable"), whose [extent](https://en.wikipedia.org/wiki/Variable_(programming)#Scope_and_extent "Variable (programming)") (lifetime) is the entire runtime of the program, though in [interpreted languages](https://en.wikipedia.org/wiki/Interpreted_language "Interpreted language") (including [command-line interpreters](https://en.wikipedia.org/wiki/Command-line_interpreter "Command-line interpreter")), global variables are generally dynamically allocated when declared, since they are not known ahead of time.

In some languages, all variables are global, or global by default, while in most modern languages variables have limited scope, generally [lexical scope](https://en.wikipedia.org/wiki/Lexical_scope "Lexical scope"), though global variables are often available by declaring a variable at the top level of the program. In other languages, however, global variables do not exist; these are generally [modular programming](https://en.wikipedia.org/wiki/Modular_programming "Modular programming") languages that enforce a module structure, or [class-based](https://en.wikipedia.org/wiki/Class-based_programming "Class-based programming") [object-oriented programming languages](https://en.wikipedia.org/wiki/Object-oriented_programming_language "Object-oriented programming language") that enforce a class structure.

### Use
Interaction mechanisms with global variables are called **global environment** (see also **global state**) mechanisms. The global environment paradigm is contrasted with the [local environment](https://en.wikipedia.org/w/index.php?title=Local_environment&action=edit&redlink=1 "Local environment (page does not exist)") paradigm, where all variables are [local](https://en.wikipedia.org/wiki/Subprogram#Local_variables,_recursion_and_reentrancy "Subprogram") with no [shared memory](https://en.wikipedia.org/wiki/Shared_memory_(interprocess_communication) "Shared memory (interprocess communication)") (and therefore all interactions can be reconducted to [message passing](https://en.wikipedia.org/wiki/Message_passing "Message passing")).

Global variables are used extensively to pass information between sections of code that do not share a caller/callee relation like concurrent threads and signal handlers. Languages (including C) where each file defines an implicit namespace eliminate most of the problems seen with languages with a global [namespace](https://en.wikipedia.org/wiki/Namespace "Namespace") though some problems may persist without proper encapsulation. Without proper locking (such as with a [mutex](https://en.wikipedia.org/wiki/Mutex "Mutex")), code using global variables will not be [thread-safe](https://en.wikipedia.org/wiki/Thread-safe "Thread-safe") except for read only values in [protected memory](https://en.wikipedia.org/wiki/Protected_memory "Protected memory").

### Environment variables
[Environment variables](https://en.wikipedia.org/wiki/Environment_variables "Environment variables") are a facility provided by some [operating systems](https://en.wikipedia.org/wiki/Operating_systems "Operating systems"). Within the OS's [shell](https://en.wikipedia.org/wiki/Shell_(computing) "Shell (computing)") ([ksh](https://en.wikipedia.org/wiki/KornShell "KornShell") in [Unix](https://en.wikipedia.org/wiki/Unix "Unix"), [bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell) "Bash (Unix shell)") in [Linux](https://en.wikipedia.org/wiki/Linux "Linux"), [COMMAND.COM](https://en.wikipedia.org/wiki/COMMAND.COM "COMMAND.COM") in [DOS](https://en.wikipedia.org/wiki/DOS "DOS") and [CMD.EXE](https://en.wikipedia.org/wiki/CMD.EXE "CMD.EXE") in [Windows](https://en.wikipedia.org/wiki/Windows "Windows")) they are a kind of variable: for instance, in unix and related systems an ordinary variable becomes an environment variable when the `export` keyword is used. Program code other than shells has to access them by [API](https://en.wikipedia.org/wiki/API "API") calls, such as `getenv()` and `setenv()`.

They are local to the process in which they were set. That means if we open two terminal windows (Two different processes running shell) and change value of environment variable in one window, that change will not be seen by other window.

When a child process is created, it inherits all the environment variables and their values from the parent process. Usually, when a program calls another program, it first creates a child process by [forking](https://en.wikipedia.org/wiki/Fork_(Unix) "Fork (Unix)"), then the child adjusts the environment as needed and lastly the child [replaces](https://en.wikipedia.org/wiki/Exec_(Unix) "Exec (Unix)") itself with the program to be called. Child processes therefore cannot use environment variables to communicate with their peers, avoiding the action at a distance problem.

### Global-only and global-by-default
A number of non-[structured](https://en.wikipedia.org/wiki/Structured_programming "Structured programming") languages, such as (early versions of) [BASIC](https://en.wikipedia.org/wiki/BASIC "BASIC"), [COBOL](https://en.wikipedia.org/wiki/COBOL "COBOL") and [Fortran](https://en.wikipedia.org/wiki/Fortran "Fortran") I (1956) only provide global variables. Fortran II (1958) introduced subroutines with local variables, and the COMMON keyword for accessing global variables. Usage of COMMON in FORTRAN continued in FORTRAN 77, and influenced later languages such as PL/SQL. Named COMMON groups for globals behave somewhat like structured namespaces. Variables are also global by default in [Forth](https://en.wikipedia.org/wiki/Forth_(programming_language) "Forth (programming language)"), [Lua](https://en.wikipedia.org/wiki/Lua_(programming_language) "Lua (programming language)"), [Perl](https://en.wikipedia.org/wiki/Perl "Perl"), and most shells.

## Side Effect
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), an operation, [function](https://en.wikipedia.org/wiki/Subroutine "Subroutine") or [expression](https://en.wikipedia.org/wiki/Expression_(programming) "Expression (programming)") is said to have a **side effect** if it has any observable effect other than its primary effect of reading the value of its arguments and returning a value to the invoker of the operation. Example side effects include modifying a [non-local variable](https://en.wikipedia.org/wiki/Non-local_variable "Non-local variable"), a [static local variable](https://en.wikipedia.org/wiki/Static_local_variable "Static local variable") or a mutable argument [passed by reference](https://en.wikipedia.org/wiki/Evaluation_strategy#Call_by_reference "Evaluation strategy"); raising errors or exceptions; performing [I/O](https://en.wikipedia.org/wiki/I/O "I/O"); or calling other functions with side-effects. In the presence of side effects, a program's behaviour may depend on history; that is, the order of evaluation matters. Understanding and debugging a function with side effects requires knowledge about the context and its possible histories. Side effects play an important role in the design and analysis of [programming languages](https://en.wikipedia.org/wiki/Programming_language "Programming language"). The degree to which side effects are used depends on the programming paradigm. For example, [imperative programming](https://en.wikipedia.org/wiki/Imperative_programming "Imperative programming") is commonly used to produce side effects, to update a system's state. By contrast, [declarative programming](https://en.wikipedia.org/wiki/Declarative_programming "Declarative programming") is commonly used to report on the state of system, without side effects.

[Functional programming](https://en.wikipedia.org/wiki/Functional_programming "Functional programming") aims to minimize or eliminate side effects. The lack of side effects makes it easier to do [formal verification](https://en.wikipedia.org/wiki/Formal_verification "Formal verification") of a program. The functional language [Haskell](https://en.wikipedia.org/wiki/Haskell_(programming_language) "Haskell (programming language)") eliminates side effects such as [I/O](https://en.wikipedia.org/wiki/Input/output "Input/output") and other stateful computations by replacing them with [monadic](https://en.wikipedia.org/wiki/Monad_(functional_programming) "Monad (functional programming)") actions. Functional languages such as [Standard ML](https://en.wikipedia.org/wiki/Standard_ML "Standard ML"), [Scheme](https://en.wikipedia.org/wiki/Scheme_(programming_language) "Scheme (programming language)") and [Scala](https://en.wikipedia.org/wiki/Scala_(programming_language) "Scala (programming language)") do not restrict side effects, but it is customary for programmers to avoid them.

[Assembly language](https://en.wikipedia.org/wiki/Assembly_language "Assembly language") programmers must be aware of _hidden_ side effects—instructions that modify parts of the processor state which are not mentioned in the instruction's mnemonic. A classic example of a hidden side effect is an arithmetic instruction that implicitly modifies [condition codes](https://en.wikipedia.org/wiki/Status_register "Status register") (a hidden side effect) while it explicitly modifies a [register](https://en.wikipedia.org/wiki/Processor_register "Processor register") (the intended effect). One potential drawback of an [instruction set](https://en.wikipedia.org/wiki/Instruction_set "Instruction set") with hidden side effects is that, if many instructions have side effects on a single piece of state, like condition codes, then the logic required to update that state sequentially may become a performance bottleneck. The problem is particularly acute on some processors designed with [pipelining](https://en.wikipedia.org/wiki/Instruction_pipeline "Instruction pipeline") (since 1990) or with [out-of-order execution](https://en.wikipedia.org/wiki/Out-of-order_execution "Out-of-order execution"). Such a processor may require additional control circuitry to detect hidden side effects and stall the pipeline if the next instruction depends on the results of those effects.

### Referential transparency
Absence of side effects is a necessary, but not sufficient, condition for referential transparency. Referential transparency means that an expression (such as a function call) can be replaced with its value. This requires that the expression is [pure](https://en.wikipedia.org/wiki/Pure_function "Pure function"), that is to say the expression must be [deterministic](https://en.wikipedia.org/wiki/Deterministic_algorithm "Deterministic algorithm") (always give the same [value](https://en.wikipedia.org/wiki/Value_(computer_science) "Value (computer science)") for the same input) and side-effect free.

### Temporal side effects
Side effects caused by the time taken for an operation to execute are usually ignored when discussing side effects and referential transparency. There are some cases, such as with hardware timing or testing, where operations are inserted specifically for their temporal side effects e.g. `sleep(5000)` or `for (int i = 0; i < 10000; ++i) {}`. These instructions do not change state other than taking an amount of time to complete.

### Idempotence
A [subroutine](https://en.wikipedia.org/wiki/Subroutine "Subroutine") with side effects is idempotent if multiple applications of the subroutine have the same effect on the system state as a single application, in other words if the function from the system state space to itself associated with the subroutine is idempotent in the [mathematical sense](https://en.wikipedia.org/wiki/Idempotence#Definition "Idempotence"). For instance, consider the following [Python](https://en.wikipedia.org/wiki/Python_(programming_language) "Python (programming language)") program:

```python
x = 0

def setx(n):
    global x
    x = n

setx(3)
assert x == 3
setx(3)
assert x == 3
```

`setx` is idempotent because the second application of `setx` to 3 has the same effect on the system state as the first application: `x` was already set to 3 after the first application, and it is still set to 3 after the second application.

A [pure function](https://en.wikipedia.org/wiki/Pure_function "Pure function") is idempotent if it is idempotent in the [mathematical sense](https://en.wikipedia.org/wiki/Idempotence#Definition "Idempotence"). For instance, consider the following Python program:

```python
def abs(n):
    return -n if n < 0 else n

assert abs(abs(-3)) == abs(-3)
```

`abs` is idempotent because the second application of `abs` to the return value of the first application to -3 returns the same value as the first application to -3.

## Pure Function
In [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"), a **pure function** is a [function](https://en.wikipedia.org/wiki/Subroutine "Subroutine") that has the following properties:

1. the function [return values](https://en.wikipedia.org/wiki/Return_statement "Return statement") are [identical](https://en.wikipedia.org/wiki/Relational_operator#Location_equality_vs._content_equality "Relational operator") for identical [arguments](https://en.wikipedia.org/wiki/Argument_of_a_function "Argument of a function") (no variation with local [static variables](https://en.wikipedia.org/wiki/Static_variable "Static variable"), [non-local variables](https://en.wikipedia.org/wiki/Non-local_variable "Non-local variable"), mutable [reference arguments](https://en.wikipedia.org/wiki/Value_type_and_reference_type "Value type and reference type") or [input streams](https://en.wikipedia.org/wiki/Input/output "Input/output"), i.e., [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency "Referential transparency")), and
2. the function has no [side effects](https://en.wikipedia.org/wiki/Side_effect_(computer_science) "Side effect (computer science)") (no mutation of local static variables, non-local variables, mutable reference arguments or input/output streams).


## Stack-Based Memory Allocation
[Stacks](https://en.wikipedia.org/wiki/Stack_(abstract_data_type)#Hardware_stack "Stack (abstract data type)") in computing architectures are regions of [memory](https://en.wikipedia.org/wiki/Memory_(computers) "Memory (computers)") where data is added or removed in a [last-in-first-out (LIFO)](https://en.wikipedia.org/wiki/LIFO_(computing) "LIFO (computing)") manner.

In most modern computer systems, each [thread](https://en.wikipedia.org/wiki/Thread_(computer_science) "Thread (computer science)") has a reserved region of memory referred to as its stack. When a function executes, it may add some of its local state data to the top of the stack; when the function exits it is responsible for removing that data from the stack. At a minimum, a thread's stack is used to store the location of a return address provided by the caller in order to allow return statements to return to the correct location.

The stack is often used to store variables of fixed length local to the currently active functions. Programmers may further choose to explicitly use the stack to store local data of variable length. If a region of memory lies on the thread's stack, that memory is said to have been allocated on the stack, i.e. stack-based memory allocation (SBMA). This is contrasted with a [heap-based memory allocation](https://en.wikipedia.org/wiki/Heap-based_memory_allocation "Heap-based memory allocation") (HBMA). The SBMA is often closely coupled with a [function call stack](https://en.wikipedia.org/wiki/Call_stack#Functions_of_the_call_stack "Call stack").

### Advantages and disadvantages
Because the data is added and removed in a last-in-first-out manner, stack-based memory allocation is very simple and typically much faster than heap-based memory allocation (also known as [dynamic memory allocation](https://en.wikipedia.org/wiki/Dynamic_memory_allocation "Dynamic memory allocation")) e.g. [C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)")'s `malloc`.

Another feature is that memory on the stack is automatically, and very efficiently, reclaimed when the function exits, which can be convenient for the programmer if the data is no longer required. (The same applies to [longjmp](https://en.wikipedia.org/wiki/Setjmp.h "Setjmp.h") if it moved to a point before the call to `alloca` happened.) If, however, the data needs to be kept in some form, then it must be copied from the stack to the heap before the function exits. Therefore, stack based allocation is suitable for temporary data or data which is no longer required after the current function exits.

A thread's assigned stack size can be as small as only a few bytes on some small CPUs. Allocating more memory on the stack than is available can result in a [crash](https://en.wikipedia.org/wiki/Crash_(computing) "Crash (computing)") due to [stack overflow](https://en.wikipedia.org/wiki/Stack_overflow "Stack overflow"). This is also why functions that use `alloca` are usually prevented from being inlined: should such a function be inlined into a loop, the caller would suffer from an unanticipated growth in stack usage, making an overflow much more likely.

Stack-based allocation can also cause minor performance problems: it leads to variable-size stack frames, so that both [stack and frame pointers](https://en.wikipedia.org/wiki/Call_stack#STACK-POINTER "Call stack") need to be managed (with fixed-size stack frames, the stack pointer is redundant due to multiplying the stack frame pointer by the size of each frame). This is usually much less costly than calling `malloc` and `free` anyway. In particular, if the current function contains both calls to alloca and blocks containing variable-length local data then a conflict occurs between alloca's attempts to increase the current stack frame until the current function exits versus the compiler's need to place local variables of variable length in the same location in the stack frame. This conflict is typically resolved by creating a separate chain of heap storage for each call to alloca. The chain records the stack depth at which each allocation occurs, subsequent calls to alloca in any function trim this chain down to the current stack depth to eventually (but not immediately) free any storage on this chain. A call to alloca with an argument of zero can also be used to trigger the freeing of memory without allocating any more such memory. As a consequence of this conflict between alloca and local variable storage, using alloca might be no more efficient than using malloc.

### System interface
Many [Unix-like](https://en.wikipedia.org/wiki/Unix-like "Unix-like") systems as well as [Microsoft Windows](https://en.wikipedia.org/wiki/Microsoft_Windows "Microsoft Windows") implement a function called `alloca` for dynamically allocating stack memory in a way similar to the heap-based `malloc`. A compiler typically translates it to inlined instructions manipulating the stack pointer, similar to how [variable-length arrays](https://en.wikipedia.org/wiki/Variable-length_array "Variable-length array") are handled. Although there is no need to explicitly free the memory, there is a risk of undefined behavior due to stack overflow. The function was present on Unix systems as early as [32/V](https://en.wikipedia.org/wiki/UNIX/32V "UNIX/32V") (1978), but is not part of [Standard C](https://en.wikipedia.org/wiki/Standard_C "Standard C") or any [POSIX](https://en.wikipedia.org/wiki/POSIX "POSIX") standard.

A safer version of `alloca` called `_malloca`, which allocates on the heap if the allocation size is too large, and reports stack overflow errors, exists on Microsoft Windows. It requires the use of `_freea`. gnulib provides an equivalent interface, albeit instead of throwing an SEH exception on overflow, it delegates to `malloc` when an overlarge size is detected. A similar feature can be emulated using manual accounting and size-checking, such as in the uses of `alloca_account` in glibc.

Some processor families, such as the [x86](https://en.wikipedia.org/wiki/X86 "X86"), have special instructions for manipulating the stack of the currently executing thread. Other processor families, including [RISC-V](https://en.wikipedia.org/wiki/RISC-V "RISC-V"), [PowerPC](https://en.wikipedia.org/wiki/PowerPC "PowerPC") and [MIPS](https://en.wikipedia.org/wiki/MIPS_architecture "MIPS architecture"), do not have explicit stack support, but instead rely on convention and delegate stack management to the operating system's [application binary interface](https://en.wikipedia.org/wiki/Application_binary_interface "Application binary interface") (ABI).

#### Auto VLAs
In addition, since the C version C99 (optional since C11), it is possible to create an array on the stack within a function, automatically, known as an _auto VLA_ ([variable-length array](https://en.wikipedia.org/wiki/Variable-length_array "Variable-length array")).

```c
void f(int arrayLength)
{
    int b[arrayLength]; // auto VLA - this array's length is set at 
                      // the time of the function invocation / stack generation.
    for (int i = 0; i < arrayLength; i++)
        b[i] = 1;
    // at the end of this function, b[] is within the stack frame, and will 
    // disappear when the function exits, so no explicit call to free() is required.
}
```

## Request-Response
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), **request–response** or **request–reply** is one of the basic methods [computers](https://en.wikipedia.org/wiki/Computer "Computer") use to communicate with each other in a [network](https://en.wikipedia.org/wiki/Computer_network "Computer network"), in which the first computer sends a _request_ for some [data](https://en.wikipedia.org/wiki/Data_(computing) "Data (computing)") and the second _responds_ to the request. More specifically, it is a [message exchange pattern](https://en.wikipedia.org/wiki/Messaging_pattern "Messaging pattern") in which a requestor sends a request message to a replier system, which receives and processes the request, ultimately returning a message in response. It is analogous to a [telephone call](https://en.wikipedia.org/wiki/Telephone_call "Telephone call"), in which the caller must wait for the recipient to pick up before anything can be discussed. This is a simple but powerful messaging pattern which allows two [applications](https://en.wikipedia.org/wiki/Application_software "Application software") to have a two-way conversation with one another over a [channel](https://en.wikipedia.org/wiki/Communication_channel "Communication channel"); it is especially common in [client–server](https://en.wikipedia.org/wiki/Client%E2%80%93server "Client–server") architectures.

For simplicity, this pattern is typically implemented in a purely [synchronous](https://en.wikipedia.org/wiki/Synchronous_communication "Synchronous communication") fashion, as in [web service](https://en.wikipedia.org/wiki/Web_service "Web service") calls over [HTTP](https://en.wikipedia.org/wiki/HTTP "HTTP"), which holds a connection open and waits until the response is delivered or the [timeout](https://en.wikipedia.org/wiki/Timeout_(telecommunication) "Timeout (telecommunication)") period expires. However, request–response may also be implemented [asynchronously](https://en.wikipedia.org/wiki/Asynchronous_communication "Asynchronous communication"), with a response being returned at some unknown later time. When a synchronous system communicates with an asynchronous system, it is referred to as "sync over async" or "sync/async". (EAI) implementations where slow [aggregations](https://en.wikipedia.org/wiki/Aggregate_function "Aggregate function"), time-intensive functions, or human [workflow](https://en.wikipedia.org/wiki/Workflow "Workflow") must be performed before a response can be constructed and delivered.

In contrast, **one-way** computer communication, which is like the [push-to-talk](https://en.wikipedia.org/wiki/Push-to-talk "Push-to-talk") or "barge in" feature found on some phones and [two-way radios](https://en.wikipedia.org/wiki/Two-way_radio "Two-way radio"), sends a message without waiting for a response. Sending an [email](https://en.wikipedia.org/wiki/Email "Email") is an example of one-way communication, and another example are [fieldbus](https://en.wikipedia.org/wiki/Fieldbus "Fieldbus") sensors, such as most [CAN bus](https://en.wikipedia.org/wiki/CAN_bus "CAN bus") sensors, which periodically and autonomously send out their data, whether or not any other devices on the bus are listening for it. (Most of these systems use a "listen before talk" or other [contention-based protocol](https://en.wikipedia.org/wiki/Contention-based_protocol "Contention-based protocol") so multiple sensors can transmit periodic updates without any pre-coordination.)

## Futures and Promises
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), **future**, **promise**, **delay**, and **deferred** refer to constructs used for [synchronizing](https://en.wikipedia.org/wiki/Synchronization_(computer_science) "Synchronization (computer science)") program [execution](https://en.wikipedia.org/wiki/Execution_(computing) "Execution (computing)") in some [concurrent programming languages](https://en.wikipedia.org/wiki/Concurrent_programming_language "Concurrent programming language"). They describe an object that acts as a proxy for a result that is initially unknown, usually because the [computation](https://en.wikipedia.org/wiki/Computation "Computation") of its value is not yet complete.

The term _promise_ was proposed in 1976 by [Daniel P. Friedman](https://en.wikipedia.org/wiki/Daniel_P._Friedman "Daniel P. Friedman") and David Wise, and Peter Hibbard called it _eventual_. A somewhat similar concept _future_ was introduced in 1977 in a paper by [Henry Baker](https://en.wikipedia.org/wiki/Henry_Baker_(computer_scientist) "Henry Baker (computer scientist)") and [Carl Hewitt](https://en.wikipedia.org/wiki/Carl_Hewitt "Carl Hewitt").
The terms _future_, _promise_, _delay_, and _deferred_ are often used interchangeably, although some differences in usage between _future_ and _promise_ are treated below. Specifically, when usage is distinguished, a future is a _read-only_ placeholder view of a variable, while a promise is a writable, [single assignment](https://en.wikipedia.org/wiki/Single_assignment "Single assignment") container which sets the value of the future. Notably, a future may be defined without specifying which specific promise will set its value, and different possible promises may set the value of a given future, though this can be done only once for a given future. In other cases a future and a promise are created together and associated with each other: the future is the value, the promise is the function that sets the value – essentially the return value (future) of an asynchronous function (promise). Setting the value of a future is also called _resolving_, _fulfilling_, or _binding_ it.

### Applications
Futures and promises originated in [functional programming](https://en.wikipedia.org/wiki/Functional_programming "Functional programming") and related paradigms (such as [logic programming](https://en.wikipedia.org/wiki/Logic_programming "Logic programming")) to decouple a value (a future) from how it was computed (a promise), allowing the computation to be done more flexibly, notably by parallelizing it. Later, it found use in [distributed computing](https://en.wikipedia.org/wiki/Distributed_computing "Distributed computing"), in reducing the latency from communication round trips. Later still, it gained more use by allowing writing asynchronous programs in [direct style](https://en.wikipedia.org/wiki/Direct_style "Direct style"), rather than in [continuation-passing style](https://en.wikipedia.org/wiki/Continuation-passing_style "Continuation-passing style").

### Implicit vs. explicit
Use of futures may be _implicit_ (any use of the future automatically obtains its value, as if it were an ordinary [reference](https://en.wikipedia.org/wiki/Reference_(programming) "Reference (programming)")) or _explicit_ (the user must call a function to obtain the value, Obtaining the value of an explicit future can be called _stinging_ or _forcing_. Explicit futures can be implemented as a library, whereas implicit futures are usually implemented as part of the language.

The original Baker and Hewitt paper described implicit futures, which are naturally supported in the [actor model](https://en.wikipedia.org/wiki/Actor_model "Actor model") of computation and pure [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming") languages like [Smalltalk](https://en.wikipedia.org/wiki/Smalltalk "Smalltalk"). The Friedman and Wise paper described only explicit futures, probably reflecting the difficulty of efficiently implementing implicit futures on stock hardware. The difficulty is that stock hardware does not deal with futures for primitive data types like integers. For example, an add instruction does not know how to deal with `3 + _future_ factorial(100000)`. In pure actor or object languages this problem can be solved by sending `_future_ factorial(100000)` the message `+[3]`, which asks the future to add `3` to itself and return the result. Note that the message passing approach works regardless of when `factorial(100000)` finishes computation and that no stinging/forcing is needed.

### Blocking vs non-blocking semantics
If the value of a future is accessed asynchronously, for example by sending a message to it, or by explicitly waiting for it using a construct such as `when` in E, then there is no difficulty in delaying until the future is resolved before the message can be received or the wait completes. This is the only case to be considered in purely asynchronous systems such as pure actor languages.

However, in some systems it may also be possible to attempt to _immediately_ or _synchronously_ access a future's value. Then there is a design choice to be made:

- the access could block the current thread or process until the future is resolved (possibly with a timeout). This is the semantics of _dataflow variables_ in the language [Oz](https://en.wikipedia.org/wiki/Oz_(programming_language) "Oz (programming language)").
- the attempted synchronous access could always signal an error, for example throwing an [exception](https://en.wikipedia.org/wiki/Exception_(computer_science) "Exception (computer science)"). This is the semantics of remote promises in E.
- potentially, the access could succeed if the future is already resolved, but signal an error if it is not. This would have the disadvantage of introducing nondeterminism and the potential for [race conditions](https://en.wikipedia.org/wiki/Race_conditions "Race conditions"), and seems to be an uncommon design choice.

As an example of the first possibility, in [C++11](https://en.wikipedia.org/wiki/C%2B%2B11 "C++11"), a thread that needs the value of a future can block until it is available by calling the `wait()` or `get()` member functions. A timeout can also be specified on the wait using the `wait_for()` or `wait_until()` member functions to avoid indefinite blocking. If the future arose from a call to `std::async` then a blocking wait (without a timeout) may cause synchronous invocation of the function to compute the result on the waiting thread.

### Related constructs
_Futures_ are a particular case of the [synchronization primitive](https://en.wikipedia.org/wiki/Synchronization_primitive "Synchronization primitive") "[events](https://en.wikipedia.org/wiki/Event_(synchronization_primitive) "Event (synchronization primitive)")," which can be completed only once. In general, events can be reset to initial empty state and, thus, completed as many times as desired.

An _I-var_ (as in the language [Id](https://en.wikipedia.org/wiki/Id_(programming_language) "Id (programming language)")) is a future with blocking semantics as defined above. An _I-structure_ is a [data structure](https://en.wikipedia.org/wiki/Data_structure "Data structure") containing I-vars. A related synchronization construct that can be set multiple times with different values is called an _M-var_. M-vars support atomic operations to _take_ or _put_ the current value, where taking the value also sets the M-var back to its initial _empty_ state.

A _concurrent logic variable_ is similar to a future, but is updated by [unification](https://en.wikipedia.org/wiki/Unification_(computing) "Unification (computing)"), in the same way as _logic variables_ in [logic programming](https://en.wikipedia.org/wiki/Logic_programming "Logic programming"). Thus it can be bound more than once to unifiable values, but cannot be set back to an empty or unresolved state. The dataflow variables of Oz act as concurrent logic variables, and also have blocking semantics as mentioned above.

A _concurrent constraint variable_ is a generalization of concurrent logic variables to support [constraint logic programming](https://en.wikipedia.org/wiki/Constraint_logic_programming "Constraint logic programming"): the constraint may be _narrowed_ multiple times, indicating smaller sets of possible values. Typically there is a way to specify a thunk that should run whenever the constraint is narrowed further; this is needed to support _constraint propagation_.

### Relations between the expressiveness of different forms of future
Eager thread-specific futures can be straightforwardly implemented in non-thread-specific futures, by creating a thread to calculate the value at the same time as creating the future. In this case it is desirable to return a read-only view to the client, so that only the newly created thread is able to resolve this future.

To implement implicit lazy thread-specific futures (as provided by Alice ML, for example) in terms in non-thread-specific futures, needs a mechanism to determine when the future's value is first needed (for example, the `WaitNeeded` construct in Oz. If all values are objects, then the ability to implement transparent forwarding objects is sufficient, since the first message sent to the forwarder indicates that the future's value is needed.

Non-thread-specific futures can be implemented in thread-specific futures, assuming that the system supports message passing, by having the resolving thread send a message to the future's own thread. However, this can be viewed as unneeded complexity. In programming languages based on threads, the most expressive approach seems to be to provide a mix of non-thread-specific futures, read-only views, and either a _WaitNeeded_ construct, or support for transparent forwarding.

## Evaluation Strategy
In a [programming language](https://en.wikipedia.org/wiki/Programming_language "Programming language"), an **evaluation strategy** is a set of rules for evaluating expressions. The term is often used to refer to the more specific notion of a _parameter-passing strategy that defines the kind of value that is passed to the function for each parameter (the _binding strategy_) and whether to evaluate the [parameters](https://en.wikipedia.org/wiki/Parameter_(computer_science) "Parameter (computer science)") of a function call, and if so in what order (the _evaluation order_). The notion of [reduction strategy](https://en.wikipedia.org/wiki/Reduction_strategy "Reduction strategy") is distinct, although some authors conflate the two terms and the definition of each term is not widely agreed upon.

To illustrate, executing a function call `f(a,b)` may first evaluate the arguments `a` and `b`, store the results in [references](https://en.wikipedia.org/wiki/Reference_(computer_science) "Reference (computer science)") or memory locations `ref_a` and `ref_b`, then evaluate the function's body with those references passed in. This gives the function the ability to look up the original argument values passed in through dereferencing the parameters (some languages use specific operators to perform this), to modify them via [assignment](https://en.wikipedia.org/wiki/Assignment_(computer_science) "Assignment (computer science)") as if they were local variables, and to return values via the references. This is the call-by-reference evaluation strategy.

Evaluation strategy is part of the semantics of the programming language definition. Some languages, such as [PureScript](https://en.wikipedia.org/wiki/PureScript "PureScript"), have variants with different evaluation strategies. Some [declarative languages](https://en.wikipedia.org/wiki/Declarative_language "Declarative language"), such as [Datalog](https://en.wikipedia.org/wiki/Datalog "Datalog"), support multiple evaluation strategies. Some languages define a [calling convention](https://en.wikipedia.org/wiki/Calling_convention "Calling convention").

### Evaluation orders
While the [order of operations](https://en.wikipedia.org/wiki/Order_of_operations "Order of operations") defines the [abstract syntax tree](https://en.wikipedia.org/wiki/Abstract_syntax_tree "Abstract syntax tree") of the expression, the evaluation order defines the order in which expressions are evaluated. For example, the Python program

```python
def f(x):
    print(x, end='')
    return x

print(f(1) + f(2),end='')
```

outputs `123` due to Python's left-to-right evaluation order, but a similar program in [OCaml](https://en.wikipedia.org/wiki/OCaml "OCaml"):

```ocaml
let f x = print_int x; x ;;
print_int (f 1 + f 2)
```

outputs `213` due to OCaml's right-to-left evaluation order.

The evaluation order is mainly visible in code with [side effects](https://en.wikipedia.org/wiki/Side_effect_(computer_science) "Side effect (computer science)"), but it also affects the performance of the code because a rigid order inhibits [instruction scheduling](https://en.wikipedia.org/wiki/Instruction_scheduling "Instruction scheduling"). For this reason language standards such as C++ traditionally left the order unspecified, although languages such as Java and C# define the evaluation order as left-to-right:  240–241  and the [C++17](https://en.wikipedia.org/wiki/C%2B%2B17 "C++17") standard has added constraints on the evaluation order.

#### Strict evaluation 
**Applicative order** is a family of evaluation orders in which a function's arguments are evaluated completely before the function is applied. This has the effect of making the function [strict](https://en.wikipedia.org/wiki/Strict_function "Strict function"), i.e. the function's result is undefined if any of the arguments are undefined, so applicative order evaluation is more commonly called **strict evaluation**. Furthermore, a function call is performed as soon as it is encountered in a procedure, so it is also called **eager evaluation** or **greedy evaluation**. Some authors refer to strict evaluation as "call by value" due to the call-by-value binding strategy requiring strict evaluation.

Common Lisp, [Eiffel](https://en.wikipedia.org/wiki/Eiffel_(programming_language) "Eiffel (programming language)") and Java evaluate function arguments left-to-right. C leaves the order undefined. Scheme requires the execution order to be the sequential execution of an unspecified permutation of the arguments. Ocaml similarly leaves the order unspecified, but in practice evaluates arguments right-to-left due to the design of its [abstract machine](https://en.wikipedia.org/wiki/Abstract_machine "Abstract machine"). All of these are strict evaluation.

#### Non-strict evaluation 
A **non-strict evaluation order** is an evaluation order that is not strict, that is, a function may return a result before all of its arguments are fully evaluated. The prototypical example is **normal order evaluation**, which does not evaluate any of the arguments until they are needed in the body of the function. Normal order evaluation has the property that it terminates without error whenever any other evaluation order would have terminated without error. The name "normal order" comes from the lambda calculus, where normal order reduction will find a normal form if there is one (it is a "normalizing" [reduction strategy](https://en.wikipedia.org/wiki/Reduction_strategy "Reduction strategy")). [Lazy evaluation](https://en.wikipedia.org/wiki/Lazy_evaluation "Lazy evaluation") is classified in this article as a binding technique rather than an evaluation order. But this distinction is not always followed and some authors define lazy evaluation as normal order evaluation or vice-versa, or confuse non-strictness with lazy evaluation.

Boolean expressions in many languages use a form of non-strict evaluation called [short-circuit evaluation](https://en.wikipedia.org/wiki/Short-circuit_evaluation "Short-circuit evaluation"), where evaluation evaluates the left expression but may skip the right expression if the result can be determined—for example, in a disjunctive expression (OR) where `true` is encountered, or in a conjunctive expression (AND) where `false` is encountered, and so forth. Conditional expressions similarly use non-strict evaluation - only one of the branches is evaluated.

#### Comparison of applicative order and normal order evaluation
With normal order evaluation, expressions containing an expensive computation, an error, or an infinite loop will be ignored if not needed, allowing the specification of user-defined control flow constructs, a facility not available with applicative order evaluation. Normal order evaluation uses complex structures such as [thunks](https://en.wikipedia.org/wiki/Thunk "Thunk") for unevaluated expressions, compared to the [call stack](https://en.wikipedia.org/wiki/Call_stack "Call stack") used in applicative order evaluation. Normal order evaluation has historically had a lack of usable debugging tools due to its complexity.

### Strict binding strategies
#### Call by value
In call by value (or pass by value), the evaluated value of the argument expression is bound to the corresponding variable in the function (frequently by copying the value into a new memory region). If the function or procedure is able to assign values to its parameters, only its local variable is assigned—that is, anything passed into a function call is unchanged in the caller's [scope](https://en.wikipedia.org/wiki/Scope_(programming) "Scope (programming)") when the function returns. For example, in [Pascal](https://en.wikipedia.org/wiki/Pascal_(programming_language) "Pascal (programming language)"), passing an array by value will cause the entire array to be copied, and any mutations to this array will be invisible to the caller:

```pascal
program Main;
uses crt;

procedure PrintArray(a: Array of integer);
var
  i: Integer;
begin
  for i := Low(a) to High(a) do
    Write(a[i]);
  WriteLn();
end;

Procedure Modify(Row : Array of integer);  
begin  
  PrintArray(Row); // 123
  Row[1] := 4;
  PrintArray(Row); // 143
end;

Var
  A : Array of integer; 
begin
  A := [1,2,3];
  PrintArray(A); // 123
  Modify(A);
  PrintArray(A); // 123
end.
```

##### Semantic drift
Strictly speaking, under call by value, no operations performed by the called routine can be visible to the caller, other than as part of the return value. This implies a form of [purely functional programming](https://en.wikipedia.org/wiki/Purely_functional_programming "Purely functional programming") in the implementation semantics. However, the circumlocution "call by value where the value is a reference" has become common in some languages, for example, the Java community. Compared to traditional pass by value, the value which is passed is not a value as understood by the ordinary meaning of value, such as an integer that can be written as a literal, but an implementation-internal [reference](https://en.wikipedia.org/wiki/Reference_(computer_science) "Reference (computer science)") handle. Mutations to this reference handle are visible in the caller. Due to the visible mutation, this form of "call by value" is more properly referred to as [call by sharing](https://en.wikipedia.org/wiki/Evaluation_strategy#Call_by_sharing).

In [purely functional languages](https://en.wikipedia.org/wiki/Purely_functional_language "Purely functional language"), values and data structures are immutable, so there is no possibility for a function to modify any of its arguments. As such, there is typically no semantic difference between passing by value and passing by reference or a pointer to the data structure, and implementations frequently use call by reference internally for the efficiency benefits. Nonetheless, these languages are typically described as call by value languages.

#### Call by reference
Call by reference (or pass by reference) is an evaluation strategy where a parameter is bound to an implicit [reference](https://en.wikipedia.org/wiki/Reference_(computer_science) "Reference (computer science)") to the variable used as argument, rather than a copy of its value. This typically means that the function can modify (i.e., [assign to](https://en.wikipedia.org/wiki/Assignment_(computer_science) "Assignment (computer science)")) the variable used as argument—something that will be seen by its caller. Call by reference can therefore be used to provide an additional channel of communication between the called function and the calling function. Pass by reference can significantly improve performance: calling a function with a many-megabyte structure as an argument does not have to copy the large structure, only the reference to the structure (which is generally a machine word and only a few bytes). However, a call-by-reference language makes it more difficult for a programmer to track the effects of a function call, and may introduce subtle bugs.

Due to variation in syntax, the difference between call by reference (where the reference type is implicit) and call by sharing (where the reference type is explicit) is often unclear on first glance. A simple litmus test is if it's possible to write a traditional `swap(a, b)` function in the language. For example in Fortran:

```fortran
program Main
    implicit none
    integer :: a = 1
    integer :: b = 2
    call Swap(a, b)
    print *, a, b ! 2 1
contains
    subroutine Swap(a, b)
        integer, intent(inout) :: a, b
        integer :: temp
        temp = a
        a = b
        b = temp
    end subroutine Swap
end program Main
```

Therefore, Fortran's `inout` intent implements call-by-reference; any variable can be implicitly converted to a reference handle. In contrast the closest one can get in Java is:

```java
class Main {
    static class Box {
        int value;
        public Box(int value) {
            this.value = value;
        }
    }
    static void swap(Box a, Box b) {
        int temp = a.value;
        a.value = b.value;
        b.value = temp;
    }
    public static void main(String[] args) {
        Box a = new Box(1);
        Box b = new Box(2);
        swap(a, b);
        System.out.println(String.format("%d %d", a.value, b.value));
    }
}
// output: 2 1
```

where an explicit `Box` type must be used to introduce a handle. Java is call-by-sharing but not call-by-reference.

#### Call by copy-restore
Call by copy-restore—also known as "copy-in copy-out", "call by value result", "call by value return" (as termed in the [Fortran](https://en.wikipedia.org/wiki/Fortran "Fortran") community)—is a variation of call by reference. With call by copy-restore, the contents of the argument are copied to a new variable local to the call invocation. The function may then modify this variable, similarly to call by reference, but as the variable is local, the modifications are not visible outside of the call invocation during the call. When the function call returns, the updated contents of this variable are copied back to overwrite the original argument ("restored").

The semantics of call by copy-restore is similar in many cases to call by reference, but differs when two or more function arguments [alias](https://en.wikipedia.org/wiki/Aliasing_(computing) "Aliasing (computing)") one another (i.e., point to the same variable in the caller's environment). Under call by reference, writing to one argument will affect the other during the function's execution. Under call by copy-restore, writing to one argument will not affect the other during the function's execution, but at the end of the call, the values of the two arguments may differ, and it is unclear which argument is copied back first and therefore what value the caller's variable receives. For example, Ada specifies that the copy-out assignment for each `in out` or `out` parameter occurs in an arbitrary order. From the following program (illegal in Ada 2012) it can be seen that the behavior of [GNAT](https://en.wikipedia.org/wiki/GNAT "GNAT") is to copy in left-to-right order on return:

```Ada
with Ada.Text_IO; use Ada.Text_IO;

procedure Test_Copy_Restore is
  procedure Modify (A, B : in out Integer) is
  begin
      A := A + 1;
      B := B + 2;
  end Modify;
  X : Integer := 0;
begin
  Modify(X, X);
  Put_Line("X = " & Integer'Image(X));
end Test_Copy_Restore;
-- $ gnatmake -gnatd.E test_copy_restore.adb; ./test_copy_restore
-- test_copy_restore.adb:12:10: warning: writable actual for "A" overlaps with actual for "B" [-gnatw.i]
-- X = 2
```

If the program returned 1 it would be copying right-to-left, and under call by reference semantics the program would return 3.

When the reference is passed to the caller uninitialized (for example an `out` parameter in Ada as opposed to an `in out` parameter), this evaluation strategy may be called "call by result".

This strategy has gained attention in [multiprocessing](https://en.wikipedia.org/wiki/Multiprocessing "Multiprocessing") and [remote procedure calls](https://en.wikipedia.org/wiki/Remote_procedure_call "Remote procedure call"), as unlike call-by-reference it does not require frequent communication between threads of execution for variable access.

#### Call by sharing
Call by sharing (also known as "pass by sharing", "call by object", or "call by object-sharing") is an evaluation strategy that is intermediate between call by value and call by reference. Rather than every variable being exposed as a reference, only a specific class of values, termed "references", "[boxed types](https://en.wikipedia.org/wiki/Boxed_type "Boxed type")", or "objects", have reference semantics, and it is the addresses of these pointers that are passed into the function. Like call by value, the value of the address passed is a copy, and direct assignment to the parameter of the function overwrites the copy and is not visible to the calling function. Like call by reference, mutating the target of the pointer is visible to the calling function. Mutations of a mutable object within the function are visible to the caller because the object is not copied or cloned—it is _shared_, hence the name "call by sharing".

The technique was first noted by [Barbara Liskov](https://en.wikipedia.org/wiki/Barbara_Liskov "Barbara Liskov") in 1974 for the [CLU](https://en.wikipedia.org/wiki/CLU_(programming_language) "CLU (programming language)") language. It is used by many modern languages such as [Python](https://en.wikipedia.org/wiki/Python_(programming_language) "Python (programming language)") (the shared values being called "objects"), Java (objects), [Ruby](https://en.wikipedia.org/wiki/Ruby_(programming_language) "Ruby (programming language)") (objects), [JavaScript](https://en.wikipedia.org/wiki/JavaScript "JavaScript") (objects), Scheme (data structures such as vectors), [AppleScript](https://en.wikipedia.org/wiki/AppleScript "AppleScript") (lists, records, dates, and script objects), OCaml and [ML](https://en.wikipedia.org/wiki/ML_(programming_language) "ML (programming language)") (references, records, arrays, objects, and other compound data types), [Maple](https://en.wikipedia.org/wiki/Maple_(software) "Maple (software)") (rtables and tables), and [Tcl](https://en.wikipedia.org/wiki/Tcl "Tcl") (objects). The term "call by sharing" as used in this article is not in common use; the terminology is inconsistent across different sources. For example, in the Java community, they say that Java is call by value.

For [immutable objects](https://en.wikipedia.org/wiki/Immutable_object "Immutable object"), there is no real difference between call by sharing and call by value, except if object identity is visible in the language. The use of call by sharing with mutable objects is an alternative to [input/output parameters](https://en.wikipedia.org/wiki/Output_parameter "Output parameter"): the parameter is not assigned to (the argument is not overwritten and object identity is not changed), but the object (argument) is mutated.

For example, in Python, lists are mutable and passed with call by sharing, so:

```python
def f(a_list):
    a_list.append(1)

m = []
f(m)
print(m)
```

outputs `[1]` because the `append` method modifies the object on which it is called.

In contrast, assignments within a function are not noticeable to the caller. For example, this code binds the formal argument to a new object, but it is not visible to the caller because it does not mutate `a_list`:

```python
def f(a_list):
    a_list = a_list + [1]
    print(a_list) # [1]

m = []
f(m)
print(m) # []
```

#### Call by address
**Call by address**, pass by address, or call/pass by [pointer](https://en.wikipedia.org/wiki/Pointer_(computer_programming) "Pointer (computer programming)") is a parameter passing method where the address of the argument is passed as the formal parameter. Inside the function, the address (pointer) may be used to access or modify the value of the argument. For example, the swap operation can be implemented as follows in C:

```c
#include <stdio.h>

void swap(int* a, int* b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int a = 1;
    int b = 2;
    swap(&a, &b);
    printf("%d %d", a, b); // 2 1
    return 0;
}
```

Some authors treat `&` as part of the syntax of calling `swap`. Under this view, C supports the call-by-reference parameter passing strategy. Other authors take a differing view that the presented implementation of `swap` in C is only a simulation of call-by-reference using pointers. Under this "simulation" view, mutable variables in C are not first-class (that is, l-values are not expressions), rather pointer types are. In this view, the presented swap program is syntactic sugar for a program that uses pointers throughout, for example this program (`read` and `assign` have been added to highlight the similarities to the Java `Box` call-by-sharing program [above](https://en.wikipedia.org/wiki/Evaluation_strategy#Java-box)):

```c
#include <stdio.h>

int read(int *p) {
  return *p;
}

void assign(int *p, int v) {
  *p = v;
}

void swap(int* a, int* b) {
    int temp_storage; int* temp = &temp_storage;
    assign(temp, read(a));
    assign(a, read(b));
    assign(b, read(temp));
}

int main() {
    int a_storage; int* a = &a_storage;
    int b_storage; int* b = &b_storage;
    assign(a,1);
    assign(b,2);
    swap(a, b);
    printf("%d %d", read(a), read(b)); // 2 1
    return 0;
}
```

Because in this program, `swap` operates on pointers and cannot change the pointers themselves, but only the values the pointers point to, this view holds that C's main evaluation strategy is more similar to call-by-sharing.

C++ confuses the issue further by allowing `swap` to be declared and used with a very lightweight "reference" syntax:

```c
void swap(int& a, int& b) {
    int temp = a;
    a = b;
    b = temp;
}

int main() {
    int a = 1;
    int b = 2;
    swap(a, b);
    std::cout << a << b << std::endl; // 2 1
    return 0;
}
```

Semantically, this is equivalent to the C examples. As such, many authors consider call-by-address to be a unique parameter passing strategy distinct from call-by-value, call-by-reference, and call-by-sharing.

#### Call by unification
In [logic programming](https://en.wikipedia.org/wiki/Logic_programming "Logic programming"), the evaluation of an expression may simply correspond to the [unification](https://en.wikipedia.org/wiki/Unification_(computer_science) "Unification (computer science)") of the terms involved combined with the application of some form of [resolution](https://en.wikipedia.org/wiki/Resolution_(logic) "Resolution (logic)"). Unification must be classified as a strict binding strategy because it is fully performed. However, unification can also be performed on unbounded variables, so calls may not necessarily commit to final values for all its variables.

### Non-strict binding strategies
#### Call by name
Call by name is an evaluation strategy where the arguments to a function are not evaluated before the function is called—rather, they are substituted directly into the function body (using [capture-avoiding substitution](https://en.wikipedia.org/wiki/Capture-avoiding_substitution "Capture-avoiding substitution")) and then left to be evaluated whenever they appear in the function. If an argument is not used in the function body, the argument is never evaluated; if it is used several times, it is re-evaluated each time it appears. (See [Jensen's device](https://en.wikipedia.org/wiki/Jensen%27s_device "Jensen's device") for a programming technique that exploits this.)

Call-by-name evaluation is occasionally preferable to call-by-value evaluation. If a function's argument is not used in the function, call by name will save time by not evaluating the argument, whereas call by value will evaluate it regardless. If the argument is a non-terminating computation, the advantage is enormous. However, when the function argument is used, call by name is often slower, requiring a mechanism such as a [thunk](https://en.wikipedia.org/wiki/Thunk_(functional_programming)#Call_by_name "Thunk (functional programming)").

[.NET languages](https://en.wikipedia.org/wiki/List_of_CLI_languages "List of CLI languages") can simulate call by name using delegates or `Expression<T>` parameters. The latter results in an [abstract syntax tree](https://en.wikipedia.org/wiki/Abstract_syntax_tree "Abstract syntax tree") being given to the function. [Eiffel](https://en.wikipedia.org/wiki/Eiffel_(programming_language) "Eiffel (programming language)") provides agents, which represent an operation to be evaluated when needed. [Seed7](https://en.wikipedia.org/wiki/Seed7 "Seed7") provides call by name with function parameters. [Java](https://en.wikipedia.org/wiki/Java_(programming_language) "Java (programming language)") programs can accomplish similar lazy evaluation using [lambda expressions](https://en.wikipedia.org/wiki/Anonymous_function "Anonymous function") and the `java.util.function.Supplier<T>` interface.

#### Call by need
Call by need is a [memoized](https://en.wikipedia.org/wiki/Memoization "Memoization") variant of call by name, where, if the function argument is evaluated, that value is stored for subsequent use. If the argument is [pure](https://en.wikipedia.org/wiki/Pure_function "Pure function") (i.e., free of side effects), this produces the same results as call by name, saving the cost of recomputing the argument.

[Haskell](https://en.wikipedia.org/wiki/Haskell "Haskell") is a well-known language that uses call-by-need evaluation. Because evaluation of expressions may happen arbitrarily far into a computation, Haskell supports only side effects (such as [mutation](https://en.wikipedia.org/wiki/Mutable_object "Mutable object")) via the use of [monads](https://en.wikipedia.org/wiki/Monad_(functional_programming) "Monad (functional programming)"). This eliminates any unexpected behavior from variables whose values change prior to their delayed evaluation.

In [R](https://en.wikipedia.org/wiki/R_(programming_language) "R (programming language)")'s implementation of call by need, all arguments are passed, meaning that R allows arbitrary side effects.

[Lazy evaluation](https://en.wikipedia.org/wiki/Lazy_evaluation "Lazy evaluation") is the most common implementation of call-by-need semantics, but variations like [optimistic evaluation](https://en.wikipedia.org/wiki/Evaluation_strategy#Optimistic_evaluation) exist. [.NET languages](https://en.wikipedia.org/wiki/List_of_CLI_languages "List of CLI languages") implement call by need using the type `Lazy<T>`.

[Graph reduction](https://en.wikipedia.org/wiki/Graph_reduction "Graph reduction") is an efficient implementation of lazy evaluation.

#### Call by macro expansion
Call by macro expansion is similar to call by name, but uses textual substitution rather than [capture-avoiding substitution](https://en.wikipedia.org/wiki/Capture-avoiding_substitution "Capture-avoiding substitution"). Macro substitution may therefore result in variable capture, leading to mistakes and undesired behavior. [Hygienic macros](https://en.wikipedia.org/wiki/Hygienic_macros "Hygienic macros") avoid this problem by checking for and replacing [shadowed variables](https://en.wikipedia.org/wiki/Variable_shadowing "Variable shadowing") that are not parameters.

#### Call by future
"Call by future", also known as "parallel call by name" or "lenient evaluation", is a [concurrent](https://en.wikipedia.org/wiki/Concurrent_programming "Concurrent programming") evaluation strategy combining non-strict semantics with eager evaluation. The method requires fine-grained dynamic scheduling and synchronization but is suitable for massively parallel machines.

The strategy creates a [future (promise)](https://en.wikipedia.org/wiki/Futures_and_promises "Futures and promises") for the function's body and each of its arguments. These futures are computed [concurrently](https://en.wikipedia.org/wiki/Concurrency_(computer_science) "Concurrency (computer science)") with the flow of the rest of the program. When a future A requires the value of another future B that has not yet been computed, future A blocks until future B finishes computing and has a value. If future B has already finished computing the value is returned immediately. Conditionals block until their condition is evaluated, and lambdas do not create futures until they are fully applied.
If implemented with processes or threads, creating a future will spawn one or more new processes or threads (for the promises), accessing the value will synchronize these with the main thread, and terminating the computation of the future corresponds to killing the promises computing its value. If implemented with a [coroutine](https://en.wikipedia.org/wiki/Coroutine "Coroutine"), as in [.NET](https://en.wikipedia.org/wiki/.NET ".NET") [async/await](https://en.wikipedia.org/wiki/Async/await "Async/await"), creating a future calls a coroutine (an async function), which may yield to the caller, and in turn be yielded back to when the value is used, cooperatively multitasking.

The strategy is non-deterministic, as the evaluation can occur at any time between creation of the future (i.e., when the expression is given) and use of the future's value. The strategy is non-strict because the function body may return a value before the arguments are evaluated. However, in most implementations, execution may still get stuck evaluating an unneeded argument. For example, the program

```
f x = 1/x
g y = 1
main = print (g (f 0))
```


may either have `g` finish before `f`, and output 1, or may result in an error due to evaluating `1/0`.

Call-by-future is similar to call by need in that values are computed only once. With careful handling of errors and nontermination, in particular terminating futures partway through if it is determined they will not be needed, call-by-future also has the same termination properties as call-by-need evaluation. However, call-by-future may perform unnecessary speculative work compared to call-by-need, such as deeply evaluating a lazy data structure. This can be avoided by using lazy futures that do not start computation until it is certain the value is needed.

#### Optimistic evaluation
Optimistic evaluation is a call-by-need variant where the function's argument is partly evaluated in a call-by-value style for some amount of time (which may be adjusted at [runtime](https://en.wikipedia.org/wiki/Run_time_(program_lifecycle_phase) "Run time (program lifecycle phase)")). After that time has passed, evaluation is aborted and the function is applied using call by need. This approach avoids some of call-by-need's runtime expenses while retaining desired termination characteristics.

## Lazy Evaluation
In [programming language theory](https://en.wikipedia.org/wiki/Programming_language_theory "Programming language theory"), **lazy evaluation**, or **call-by-need**, is an [evaluation strategy](https://en.wikipedia.org/wiki/Evaluation_strategy "Evaluation strategy") which delays the evaluation of an [expression](https://en.wikipedia.org/wiki/Expression_(computer_science) "Expression (computer science)") until its value is needed ([non-strict evaluation](https://en.wikipedia.org/wiki/Non-strict_evaluation "Non-strict evaluation")) and which also avoids repeated evaluations (by the use of [sharing](https://en.wikipedia.org/wiki/Sharing_(computer_science) "Sharing (computer science)")).

The benefits of lazy evaluation include:
- The ability to define [control flow](https://en.wikipedia.org/wiki/Control_flow "Control flow") (structures) as abstractions instead of [primitives](https://en.wikipedia.org/wiki/Language_primitive "Language primitive").
- The ability to define [potentially infinite](https://en.wikipedia.org/wiki/Actual_infinity "Actual infinity") [data structures](https://en.wikipedia.org/wiki/Data_structure "Data structure"). This allows for more straightforward implementation of some [algorithms](https://en.wikipedia.org/wiki/Algorithm "Algorithm").
- The ability to define partly-defined data structures where some elements are errors. This allows for rapid prototyping.

Lazy evaluation is often combined with [memoization](https://en.wikipedia.org/wiki/Memoization "Memoization"), as described in [Jon Bentley](https://en.wikipedia.org/wiki/Jon_Bentley_(computer_scientist) "Jon Bentley (computer scientist)")'s _Writing Efficient Programs_. After a function's value is computed for that [parameter](https://en.wikipedia.org/wiki/Parameter_(computer_programming) "Parameter (computer programming)") or set of parameters, the result is stored in a [lookup table](https://en.wikipedia.org/wiki/Lookup_table "Lookup table") that is indexed by the values of those parameters; the next time the function is called, the table is consulted to determine whether the result for that combination of parameter values is already available. If so, the stored result is simply returned. If not, the function is evaluated, and another entry is added to the lookup table for reuse.

Lazy evaluation is difficult to combine with [imperative](https://en.wikipedia.org/wiki/Imperative_programming "Imperative programming") features such as [exception handling](https://en.wikipedia.org/wiki/Exception_handling "Exception handling") and [input/output](https://en.wikipedia.org/wiki/Input/output "Input/output"), because the [order of operations](https://en.wikipedia.org/wiki/Order_of_operations "Order of operations") becomes indeterminate.

The opposite of lazy evaluation is [eager evaluation](https://en.wikipedia.org/wiki/Eager_evaluation "Eager evaluation"), sometimes known as strict evaluation. Eager evaluation is the evaluation strategy employed in most programming languages.

## Memory Management
**Memory management** (also **dynamic memory management**, **dynamic storage allocation**, or **dynamic memory allocation**) is a form of [resource management](https://en.wikipedia.org/wiki/Resource_management_(computing) "Resource management (computing)") applied to [computer memory](https://en.wikipedia.org/wiki/Computer_memory "Computer memory"). The essential requirement of memory management is to provide ways to dynamically allocate portions of memory to programs at their request, and free it for reuse when no longer needed. This is critical to any advanced computer system where more than a single [process](https://en.wikipedia.org/wiki/Process_(computing) "Process (computing)") might be underway at any time.

Several methods have been devised that increase the effectiveness of memory management. [Virtual memory](https://en.wikipedia.org/wiki/Virtual_memory "Virtual memory") systems separate the [memory addresses](https://en.wikipedia.org/wiki/Memory_address "Memory address") used by a process from actual physical addresses, allowing separation of processes and increasing the size of the [virtual address space](https://en.wikipedia.org/wiki/Virtual_address_space "Virtual address space") beyond the available amount of [RAM](https://en.wikipedia.org/wiki/Random-access_memory "Random-access memory") using [paging](https://en.wikipedia.org/wiki/Paging "Paging") or swapping to [secondary storage](https://en.wikipedia.org/wiki/Secondary_storage "Secondary storage"). The quality of the virtual memory manager can have an extensive effect on overall system [performance](https://en.wikipedia.org/wiki/Computer_performance "Computer performance"). The system allows a computer to appear as if it may have more memory available than physically present, thereby allowing multiple processes to share it.

In some [operating systems](https://en.wikipedia.org/wiki/Operating_system "Operating system"), e.g. [Burroughs/Unisys MCP](https://en.wikipedia.org/wiki/Burroughs_MCP "Burroughs MCP"), and [OS/360 and successors](https://en.wikipedia.org/wiki/OS/360_and_successors "OS/360 and successors"), memory is managed by the operating system. In other operating systems, e.g. [Unix-like](https://en.wikipedia.org/wiki/Unix-like "Unix-like") operating systems, memory is managed at the application level.

Memory management within an address space is generally categorized as either [manual memory management](https://en.wikipedia.org/wiki/Manual_memory_management "Manual memory management") or automatic memory management.

![[Pasted image 20241027194150.png]]

### Manual Memory Management
The task of fulfilling an allocation request consists of locating a block of unused memory of sufficient size. Memory requests are satisfied by allocating portions from a large pool of memory called the _heap_ or _free store_. At any given time, some parts of the heap are in use, while some are "free" (unused) and thus available for future allocations. In the C language, the function which allocates memory from the heap is called `malloc` and the function which takes previously allocated memory and marks it as "free" (to be used by future allocations) is called `free`. 

Several issues complicate the implementation, such as [external fragmentation](https://en.wikipedia.org/wiki/Fragmentation_(computer)#External_fragmentation "Fragmentation (computer)"), which arises when there are many small gaps between allocated memory blocks, which invalidates their use for an allocation request. The allocator's [metadata](https://en.wikipedia.org/wiki/Metadata_(computing) "Metadata (computing)") can also inflate the size of (individually) small allocations. This is often managed by [chunking](https://en.wikipedia.org/wiki/Chunking_(computing) "Chunking (computing)"). The memory management system must track outstanding allocations to ensure that they do not overlap and that no memory is ever "lost" (i.e. that there are no "[memory leaks](https://en.wikipedia.org/wiki/Memory_leak "Memory leak")").

![[Pasted image 20241027194300.png]]

#### Efficiency
The specific dynamic memory allocation algorithm implemented can impact performance significantly. A study conducted in 1994 by [Digital Equipment Corporation](https://en.wikipedia.org/wiki/Digital_Equipment_Corporation "Digital Equipment Corporation") illustrates the [overheads](https://en.wikipedia.org/wiki/Computational_overhead "Computational overhead") involved for a variety of allocators. The lowest average [instruction path length](https://en.wikipedia.org/wiki/Instruction_path_length "Instruction path length") required to allocate a single memory slot was 52 (as measured with an instruction level [profiler](https://en.wikipedia.org/wiki/Profiling_(computer_programming) "Profiling (computer programming)") on a variety of software).

#### Implementations
Since the precise location of the allocation is not known in advance, the memory is accessed indirectly, usually through a [pointer](https://en.wikipedia.org/wiki/Pointer_(computer_programming) "Pointer (computer programming)") [reference](https://en.wikipedia.org/wiki/Reference_(computer_science) "Reference (computer science)"). The specific algorithm used to organize the memory area and allocate and deallocate chunks is interlinked with the [kernel](https://en.wikipedia.org/wiki/Kernel_(operating_system) "Kernel (operating system)"), and may use any of the following methods:

#### Fixed-size blocks allocation
Fixed-size blocks allocation, also called memory pool allocation, uses a [free list](https://en.wikipedia.org/wiki/Free_list "Free list") of fixed-size blocks of memory (often all of the same size). This works well for simple [embedded systems](https://en.wikipedia.org/wiki/Embedded_system "Embedded system") where no large objects need to be allocated but suffers from [fragmentation](https://en.wikipedia.org/wiki/Fragmentation_(computing) "Fragmentation (computing)") especially with long memory addresses. However, due to the significantly reduced overhead, this method can substantially improve performance for objects that need frequent allocation and deallocation, and so it is often used in [video games](https://en.wikipedia.org/wiki/Video_games "Video games").

#### Buddy blocks
In this system, memory is allocated into several pools of memory instead of just one, where each pool represents blocks of memory of a certain [power of two](https://en.wikipedia.org/wiki/Power_of_two "Power of two") in size, or blocks of some other convenient size progression. All blocks of a particular size are kept in a sorted [linked list](https://en.wikipedia.org/wiki/Linked_list "Linked list") or [tree](https://en.wikipedia.org/wiki/Tree_data_structure "Tree data structure") and all new blocks that are formed during allocation are added to their respective memory pools for later use. If a smaller size is requested than is available, the smallest available size is selected and split. One of the resulting parts is selected, and the process repeats until the request is complete. When a block is allocated, the allocator will start with the smallest sufficiently large block to avoid needlessly breaking blocks. When a block is freed, it is compared to its buddy. If they are both free, they are combined and placed in the correspondingly larger-sized buddy-block list.

#### Slab allocation
This memory allocation mechanism preallocates memory chunks suitable to fit objects of a certain type or size. These chunks are called caches and the allocator only has to keep track of a list of free cache slots. Constructing an object will use any one of the free cache slots and destructing an object will add a slot back to the free cache slot list. This technique alleviates memory fragmentation and is efficient as there is no need to search for a suitable portion of memory, as any open slot will suffice.

#### Stack allocation
Many [Unix-like](https://en.wikipedia.org/wiki/Unix-like "Unix-like") systems as well as [Microsoft Windows](https://en.wikipedia.org/wiki/Microsoft_Windows "Microsoft Windows") implement a function called `alloca` for dynamically allocating stack memory in a way similar to the heap-based `malloc`. A compiler typically translates it to inlined instructions manipulating the stack pointer. Although there is no need of manually freeing memory allocated this way as it is automatically freed when the function that called `alloca` returns, there exists a risk of overflow. And since alloca is an _ad hoc_ expansion seen in many systems but never in POSIX or the C standard, its behavior in case of a stack overflow is undefined.

A safer version of alloca called `_malloca`, which reports errors, exists on Microsoft Windows. It requires the use of `_freea`. GNULIB provides an equivalent interface, albeit instead of throwing an SEH exception on overflow, it delegates to malloc when an overlarge size is detected. A similar feature can be emulated using manual accounting and size-checking, such as in the uses of `alloca_account` in glibc.

### Automated memory management
The proper management of memory in an application is a difficult problem, and several different strategies for handling memory management have been devised.

#### Automatic management of call stack variables
In many programming language implementations, the runtime environment for the program automatically allocates memory in the [call stack](https://en.wikipedia.org/wiki/Call_stack "Call stack") for non-static [local variables](https://en.wikipedia.org/wiki/Local_variable "Local variable") of a [subroutine](https://en.wikipedia.org/wiki/Subroutine "Subroutine"), called [automatic variables](https://en.wikipedia.org/wiki/Automatic_variable "Automatic variable"), when the subroutine is called, and automatically releases that memory when the subroutine is exited. Special declarations may allow local variables to retain values between invocations of the procedure, or may allow local variables to be accessed by other subroutines. The automatic allocation of local variables makes [recursion](https://en.wikipedia.org/wiki/Recursion_(computer_science) "Recursion (computer science)") possible, to a depth limited by available memory.

#### Garbage collection
Garbage collection is a strategy for automatically detecting memory allocated to objects that are no longer usable in a program, and returning that allocated memory to a pool of free memory locations. This method is in contrast to "manual" memory management where a programmer explicitly codes memory requests and memory releases in the program. While automatic garbage collection has the advantages of reducing programmer workload and preventing certain kinds of memory allocation bugs, garbage collection does require memory resources of its own, and can compete with the application program for processor time.

#### Reference counting
Reference counting is a strategy for detecting that memory is no longer usable by a program by maintaining a counter for how many independent pointers point to the memory. Whenever a new pointer points to a piece of memory, the programmer is supposed to increase the counter. When the pointer changes where it points, or when the pointer is no longer pointing to any area or has itself been freed, the counter should decrease. When the counter drops to zero, the memory should be considered unused and freed. Some reference counting systems require programmer involvement and some are implemented automatically by the compiler. A disadvantage of reference counting is that circular references can develop which cause a memory leak to occur. This can be mitigated by either adding the concept of a "weak reference" (a reference that does not participate in reference counting, but is notified when the area it is pointing to is no longer valid) or by combining reference counting and garbage collection together.

#### Memory pools
A memory pool is a technique of automatically deallocating memory based on the state of the application, such as the lifecycle of a request or transaction. The idea is that many applications execute large chunks of code which may generate memory allocations, but that there is a point in execution where all of those chunks are known to be no longer valid. For example, in a web service, after each request the web service no longer needs any of the memory allocated during the execution of the request. Therefore, rather than keeping track of whether or not memory is currently being referenced, the memory is allocated according to the request or lifecycle stage with which it is associated. When that request or stage has passed, all associated memory is deallocated simultaneously.

## Memory Pool
**Memory pools**, also called [fixed-size blocks allocation](https://en.wikipedia.org/wiki/Fixed-size_blocks_allocation "Fixed-size blocks allocation"), is the use of [pools](https://en.wikipedia.org/wiki/Pool_(computer_science) "Pool (computer science)") for [memory management](https://en.wikipedia.org/wiki/Memory_management "Memory management") that allows [dynamic memory allocation](https://en.wikipedia.org/wiki/Dynamic_memory_allocation "Dynamic memory allocation"). Dynamic memory allocation can, and has been achieved through the use of techniques such as [malloc](https://en.wikipedia.org/wiki/Malloc "Malloc") and [C++](https://en.wikipedia.org/wiki/C%2B%2B "C++")'s [operator new](https://en.wikipedia.org/wiki/New_(C%2B%2B) "New (C++)"); although established and reliable implementations, these suffer from [fragmentation](https://en.wikipedia.org/wiki/Fragmentation_(computer) "Fragmentation (computer)") because of variable block sizes, it is not recommendable to use them in a [real time system](https://en.wikipedia.org/wiki/Real-time_computing "Real-time computing") due to performance. A more efficient solution is preallocating a number of memory blocks with the same size called the **memory pool**. The application can allocate, access, and free blocks represented by [handles](https://en.wikipedia.org/wiki/Handle_(computing) "Handle (computing)") at [run time](https://en.wikipedia.org/wiki/Run_time_(program_lifecycle_phase) "Run time (program lifecycle phase)").

Many [real-time operating systems](https://en.wikipedia.org/wiki/RTOS#Memory_allocation "RTOS") use memory pools, such as the [Transaction Processing Facility](https://en.wikipedia.org/wiki/Transaction_Processing_Facility "Transaction Processing Facility").

Some systems, like the web server [Nginx](https://en.wikipedia.org/wiki/Nginx "Nginx"), use the term _memory pool_ to refer to a group of variable-size allocations which can be later deallocated all at once. This is also known as a _region_; 

![[Pasted image 20241027194838.png]]

### Simple memory pool implementation
A simple memory pool module can allocate, for example, three pools at [compile time](https://en.wikipedia.org/wiki/Compile_time "Compile time") with block sizes optimized for the application deploying the module. The application can allocate, access and free memory through the following interface:

- Allocate memory from the pools. The function will determine the pool where the required block fits in. If all blocks of that pool are already reserved, the function tries to find one in the next bigger pool(s). An allocated memory block is represented with a [handle](https://en.wikipedia.org/wiki/Handle_(computing) "Handle (computing)").
- Get an access pointer to the allocated memory.
- Free the formerly allocated memory block.
- The handle can for example be implemented with an `unsigned int`. The module can interpret the handle internally by dividing it into pool index, memory block index and a version. The pool and memory block index allow fast access to the corresponding block with the handle, while the version, which is incremented at each new allocation, allows detection of handles whose memory block is already freed (caused by handles retained too long).

### Memory pool vs malloc
**Benefits**
- Memory pools allow memory allocation with constant execution time. The memory release for thousands of objects in a pool is just one operation, not one by one if _malloc_ is used to allocate memory for each object.
- Memory pools can be grouped in hierarchical tree structures, which is suitable for special programming structures like [loops](https://en.wikipedia.org/wiki/Control_flow#Loops "Control flow") and [recursions](https://en.wikipedia.org/wiki/Recursion_(computer_science) "Recursion (computer science)").
- Fixed-size block memory pools do not need to store allocation metadata for each allocation, describing characteristics like the size of the allocated block. Particularly for small allocations, this provides substantial space savings.
- Allows deterministic behavior on real-time systems avoiding the out of memory errors.

**Drawbacks**
- Memory pools may need to be tuned for the application which deploys them.

## Region Based memory management
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), **region-based memory management** is a type of [memory management](https://en.wikipedia.org/wiki/Memory_management "Memory management") in which each allocated object is assigned to a **region**. A region, also called a **zone**, **arena**, **area**, or **memory context**, is a collection of allocated objects that can be efficiently reallocated or deallocated all at once. Memory allocators using region-based managements are often called **area allocators**, and when they work by only "bumping" a single pointer, as **bump allocators**.

Like [stack allocation](https://en.wikipedia.org/wiki/Stack_allocation "Stack allocation"), regions facilitate allocation and deallocation of memory with low overhead; but they are more flexible, allowing objects to live longer than the [stack frame](https://en.wikipedia.org/wiki/Stack_frame "Stack frame") in which they were allocated. In typical implementations, all objects in a region are allocated in a single contiguous range of memory addresses, similarly to how stack frames are typically allocated.

### Example
As a simple example, consider the following [C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)") code which allocates and then deallocates a [linked list](https://en.wikipedia.org/wiki/Linked_list "Linked list") data structure:

```c
Region *r = createRegion();
ListNode *head = NULL;
for (int i = 1; i <= 1000; i++) {
    ListNode* newNode = allocateFromRegion(r, sizeof(ListNode));
    newNode->next = head;
    head = newNode;
}
// ...
// (use list here)
// ...


destroyRegion(r);
```

Although it required many operations to construct the linked list, it can be quickly deallocated in a single operation by destroying the region in which the nodes were allocated. There is no need to traverse the list.

### Implementation
Simple explicit regions are straightforward to implement; the following description is based on the work of Hanson. Each region is implemented as a [linked list](https://en.wikipedia.org/wiki/Linked_list "Linked list") of large blocks of memory; each block should be large enough to serve many allocations. The current block maintains a pointer to the next free position in the block, and if the block is filled, a new one is allocated and added to the list. When the region is deallocated, the next-free-position pointer is reset to the beginning of the first block, and the list of blocks can be reused for the next allocated region. Alternatively, when a region is deallocated, its list of blocks can be appended to a global freelist from which other regions may later allocate new blocks. With either case of this simple scheme, it is not possible to deallocate individual objects in regions.

The overall cost per allocated byte of this scheme is very low; almost all allocations involve only a comparison and an update to the next-free-position pointer. Deallocating a region is a constant-time operation, and is done rarely. Unlike in typical [garbage collection](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science) "Garbage collection (computer science)") systems, there is no need to tag data with its type.

## Manual Memory Management
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), **manual memory management** refers to the usage of manual instructions by the programmer to identify and deallocate unused objects, or [garbage](https://en.wikipedia.org/wiki/Garbage_(computer_science) "Garbage (computer science)"). Up until the mid-1990s, the majority of [programming languages](https://en.wikipedia.org/wiki/Programming_language "Programming language") used in industry supported manual memory management, though [garbage collection](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science) "Garbage collection (computer science)") has existed since 1959, when it was introduced with [Lisp](https://en.wikipedia.org/wiki/Lisp_(programming_language) "Lisp (programming language)"). Today, however, languages with garbage collection such as [Java](https://en.wikipedia.org/wiki/Java_(programming_language) "Java (programming language)") are increasingly popular and the languages [Objective-C](https://en.wikipedia.org/wiki/Objective-C "Objective-C") and [Swift](https://en.wikipedia.org/wiki/Swift_(programming_language) "Swift (programming language)") provide similar functionality through [Automatic Reference Counting](https://en.wikipedia.org/wiki/Automatic_Reference_Counting "Automatic Reference Counting"). The main manually managed languages still in widespread use today are [C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)") and [C++](https://en.wikipedia.org/wiki/C%2B%2B "C++") – see [C dynamic memory allocation](https://en.wikipedia.org/wiki/C_dynamic_memory_allocation "C dynamic memory allocation").

### Description
Many programming languages use manual techniques to determine when to _allocate_ a new object from the free store. C uses the `malloc` function; C++ and Java use the `new` operator; and many other languages (such as Python) allocate all objects from the free store. Determining when an object ought to be created ([object creation](https://en.wikipedia.org/wiki/Object_creation "Object creation")) is generally trivial and unproblematic, though techniques such as [object pools](https://en.wikipedia.org/wiki/Object_pool "Object pool") mean an object may be created before immediate use. The real challenge is [object destruction](https://en.wikipedia.org/wiki/Object_destruction "Object destruction") – determination of when an object is no longer needed (i.e. is garbage), and arranging for its underlying storage to be returned to the free store for re-use. In manual memory allocation, this is also specified manually by the programmer; via functions such as `free()` in C, or the `delete` operator in C++ – this contrasts with automatic destruction of objects held in [automatic variables](https://en.wikipedia.org/wiki/Automatic_variable "Automatic variable"), notably (non-static) [local variables](https://en.wikipedia.org/wiki/Local_variable "Local variable") of functions, which are destroyed at the end of their scope in C and C++.

### Manual management and correctness
Manual memory management is known to enable several major classes of bugs into a program when used incorrectly, notably violations of [memory safety](https://en.wikipedia.org/wiki/Memory_safety "Memory safety") or [memory leaks](https://en.wikipedia.org/wiki/Memory_leak "Memory leak"). These are a significant source of [security bugs](https://en.wikipedia.org/wiki/Security_bug "Security bug").

- When an unused object is never released back to the free store, this is known as a [memory leak](https://en.wikipedia.org/wiki/Memory_leak "Memory leak"). In some cases, memory leaks may be tolerable, such as a program which "leaks" a bounded amount of memory over its lifetime, or a short-running program which relies on an [operating system](https://en.wikipedia.org/wiki/Operating_system "Operating system") to deallocate its resources when it terminates. However, in many cases memory leaks occur in long-running programs, and in such cases an _unbounded_ amount of memory is leaked. When this occurs, the size of the available free store continues to decrease over time; when it is finally exhausted, the program then crashes.
- Catastrophic failure of the [dynamic memory management](https://en.wikipedia.org/wiki/Dynamic_memory_management "Dynamic memory management") system may result when an object's backing memory is deleted out from under it more than once; an object is explicitly destroyed more than once; when, while using a pointer to manipulate an object _not_ allocated on the free store, a programmer attempts to release said pointer's target object's backing memory; or when, while manipulating an object via a pointer to another, arbitrary area of memory managed by an unknown external task, thread, or process, a programmer corrupts that object's state, possibly in such a way as to write outside of its bounds and corrupt its memory management data. The result of such actions can include [heap corruption](https://en.wikipedia.org/wiki/Heap_corruption "Heap corruption"), premature destruction of a _different_ (and newly created) object which happens to occupy the same location in memory as the multiply deleted object, program crashes due to a [segmentation fault](https://en.wikipedia.org/wiki/Segmentation_fault "Segmentation fault") (violation of [memory protection](https://en.wikipedia.org/wiki/Memory_protection "Memory protection")) and other forms of [undefined behavior](https://en.wikipedia.org/wiki/Undefined_behavior "Undefined behavior").
- Pointers to deleted objects become [wild pointers](https://en.wikipedia.org/wiki/Wild_pointer "Wild pointer") if used post-deletion; attempting to use such pointers can result in difficult-to-diagnose bugs.

Languages which exclusively use [garbage collection](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science) "Garbage collection (computer science)") are known to avoid the last two classes of defects. Memory leaks can still occur (and bounded leaks frequently occur with generational or conservative garbage collection), but are generally less severe than memory leaks in manual systems.

## Big O Notation
**Big _O_ notation** is a mathematical notation that describes the [limiting behavior](https://en.wikipedia.org/wiki/Asymptotic_analysis "Asymptotic analysis") of a [function](https://en.wikipedia.org/wiki/Function_(mathematics) "Function (mathematics)") when the [argument](https://en.wikipedia.org/wiki/Argument_of_a_function "Argument of a function") tends towards a particular value or infinity. Big O is a member of a [family of notations](https://en.wikipedia.org/wiki/Big_O_notation#Related_asymptotic_notations) invented by German mathematicians [Paul Bachmann](https://en.wikipedia.org/wiki/Paul_Gustav_Heinrich_Bachmann "Paul Gustav Heinrich Bachmann"), and others, collectively called **Bachmann–Landau notation** or **asymptotic notation**. The letter O was chosen by Bachmann to stand for _[Ordnung](https://en.wiktionary.org/wiki/Ordnung#German "wikt:Ordnung")_, meaning the [order of approximation](https://en.wikipedia.org/wiki/Order_of_approximation "Order of approximation").

In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), big O notation is used to [classify algorithms](https://en.wikipedia.org/wiki/Computational_complexity_theory "Computational complexity theory") according to how their run time or space requirements grow as the input size grows. In [analytic number theory](https://en.wikipedia.org/wiki/Analytic_number_theory "Analytic number theory"), big O notation is often used to express a bound on the difference between an [arithmetical function](https://en.wikipedia.org/wiki/Arithmetic_function "Arithmetic function") and a better understood approximation; a famous example of such a difference is the remainder term in the [prime number theorem](https://en.wikipedia.org/wiki/Prime_number_theorem "Prime number theorem"). Big O notation is also used in many other fields to provide similar estimates.

Big O notation characterizes functions according to their growth rates: different functions with the same asymptotic growth rate may be represented using the same O notation. The letter O is used because the growth rate of a function is also referred to as the **order of the function**. A description of a function in terms of big O notation usually only provides an [upper bound](https://en.wikipedia.org/wiki/Upper_bound "Upper bound") on the growth rate of the function.

Associated with big O notation are several related notations, using the symbols _o_, Ω, _ω_, and Θ, to describe other kinds of bounds on asymptotic growth rates.

### Formal definition
Let f,
![{\displaystyle f,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9e9687ea22c0f310582e97ee5f6c6a5fca28203d)

the function to be estimated, be a [real](https://en.wikipedia.org/wiki/Real_number "Real number") or [complex](https://en.wikipedia.org/wiki/Complex_number "Complex number") valued function, and let  g
![{\displaystyle \ g\,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c4f953d0045fe6c7829caf82d345f4545c84ca71)

the comparison function, be a real valued function. Let both functions be defined on some [unbounded](https://en.wikipedia.org/wiki/Bounded_set "Bounded set") [subset](https://en.wikipedia.org/wiki/Subset "Subset") of the positive [real numbers](https://en.wikipedia.org/wiki/Real_number "Real number"), and g(x)
![{\displaystyle g(x)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c6ca91363022bd5e4dcb17e5ef29f78b8ef00b59)
be non-zero (often, but not necessarilly, strictly positive) for all large enough values of x.
![{\displaystyle x.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d07e9f568a88785ae48006ac3c4b951020f1699a)

One writesf(x)=O(g(x)) as x→∞
![{\displaystyle f(x)=O{\bigl (}g(x){\bigr )}\quad {\text{ as }}x\to \infty }](https://wikimedia.org/api/rest_v1/media/math/render/svg/e45ededce98fd7f1d8866cff71d6311e6510e850)

and it is read " f(x) 
![{\displaystyle \ f(x)\ }](https://wikimedia.org/api/rest_v1/media/math/render/svg/93e672050841d667b55e1ff33d567a3ed879d883)

is big O of g(x)
![{\displaystyle g(x)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c6ca91363022bd5e4dcb17e5ef29f78b8ef00b59)

" or more often "f(x)
![{\displaystyle f(x)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/202945cce41ecebb6f643f31d119c514bec7a074)

is of the order of g(x)
![{\displaystyle g(x)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c6ca91363022bd5e4dcb17e5ef29f78b8ef00b59)

" if the [absolute value](https://en.wikipedia.org/wiki/Absolute_value "Absolute value") of f(x)
![{\displaystyle f(x)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/202945cce41ecebb6f643f31d119c514bec7a074)

is at most a positive constant multiple of the absolute value of g(x)
![{\displaystyle g(x)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c6ca91363022bd5e4dcb17e5ef29f78b8ef00b59)

for all sufficiently large values of x.
![{\displaystyle x.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d07e9f568a88785ae48006ac3c4b951020f1699a)

That is, f(x)=O(g(x))
![{\displaystyle f(x)=O{\bigl (}g(x){\bigr )}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9b171ef5a4bf9979e88b862b43b44196c70a2cbe)

if there exists a positive real number M![{\displaystyle M}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f82cade9898ced02fdd08712e5f0c0151758a0dd)
and a real number x0
![{\displaystyle x_{0}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/86f21d0e31751534cd6584264ecf864a6aa792cf)

such that|f(x)|≤M |g(x)| for all x≥x0.
![{\displaystyle |f(x)|\leq M\ |g(x)|\quad {\text{ for all }}x\geq x_{0}~.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c616aa2ad74f1d52a60648eedf973b7f06b96733)

In many contexts, the assumption that we are interested in the growth rate as the variable  x 
![{\displaystyle \ x\ }](https://wikimedia.org/api/rest_v1/media/math/render/svg/b8870480257369121bf218c4814f88d4f5c43108)

goes to infinity or to zero is left unstated, and one writes more simply thatf(x)=O(g(x)).
![{\displaystyle f(x)=O{\bigl (}g(x){\bigr )}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0cd5c1bc330a1a7a4a1784b75d08d386a426434c)

The notation can also be used to describe the behavior of f
![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61)

near some real number a
![{\displaystyle a}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ffd2487510aa438433a2579450ab2b3d557e5edc) 

(often, a=0
![{\displaystyle a=0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/90d476e5e765a5d77bbcff32e4584579207ec7d8)

): we sayf(x)=O(g(x)) as  x→a
![{\displaystyle f(x)=O{\bigl (}g(x){\bigr )}\quad {\text{ as }}\ x\to a}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1d86a6ccab54b0c0969bcda1c5021ced57fcc155)

if there exist positive numbers δ
![{\displaystyle \delta }](https://wikimedia.org/api/rest_v1/media/math/render/svg/c5321cfa797202b3e1f8620663ff43c4660ea03a)

and M
![{\displaystyle M}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f82cade9898ced02fdd08712e5f0c0151758a0dd) 

such that for all defined x
![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) 

with 0<|x−a|<δ,
![{\displaystyle 0<|x-a|<\delta ,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c09500e7e9381b238aa30d66c37a707ecc5781da)

|f(x)|≤M|g(x)|.
![{\displaystyle |f(x)|\leq M|g(x)|.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/eb3b1907dc88a74ce67749e0ecb3ed7c4a48f0aa)

As g(x)
![{\displaystyle g(x)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c6ca91363022bd5e4dcb17e5ef29f78b8ef00b59) 

is non-zero for adequately large (or small) values of x,
![{\displaystyle x,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/feff4d40084c7351bf57b11ba2427f6331f5bdbe) 

both of these definitions can be unified using the [limit superior](https://en.wikipedia.org/wiki/Limit_superior "Limit superior"):f(x)=O(g(x)) as  x→a
![{\displaystyle f(x)=O{\bigl (}g(x){\bigr )}\quad {\text{ as }}\ x\to a}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1d86a6ccab54b0c0969bcda1c5021ced57fcc155)

iflim supx→a|f(x)||g(x)|<∞.
![{\displaystyle \limsup _{x\to a}{\frac {\left|f(x)\right|}{\left|g(x)\right|}}<\infty .}](https://wikimedia.org/api/rest_v1/media/math/render/svg/176cfe091b474a99b1a9e6c2c86b6a2cfd5d80aa)

And in both of these definitions the [limit point](https://en.wikipedia.org/wiki/Limit_point "Limit point") a
![{\displaystyle a}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ffd2487510aa438433a2579450ab2b3d557e5edc) 

(whether ∞
![{\displaystyle \infty }](https://wikimedia.org/api/rest_v1/media/math/render/svg/c26c105004f30c27aa7c2a9c601550a4183b1f21) 

or not) is a [cluster point](https://en.wikipedia.org/wiki/Cluster_point "Cluster point") of the domains of f
![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) 

and g,
![{\displaystyle g,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81f2986cd965e404a1ee33ec84baee5c43da47fa) 

i. e., in every neighbourhood of a
![{\displaystyle a}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ffd2487510aa438433a2579450ab2b3d557e5edc) 

there have to be infinitely many points in common. Moreover, as pointed out in the article about the [limit inferior and limit superior](https://en.wikipedia.org/wiki/Limit_inferior_and_limit_superior#Real-valued_functions "Limit inferior and limit superior"), the lim supx→a
![{\displaystyle \textstyle \limsup _{x\to a}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/053814e8519054bbf8e10109acd77ad38e1052c2) 

(at least on the [extended real number line](https://en.wikipedia.org/wiki/Extended_real_number_line "Extended real number line")) always exists.

In computer science, a slightly more restrictive definition is common: f
![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) 

and g
![{\displaystyle g}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d3556280e66fe2c0d0140df20935a6f057381d77) 

are both required to be functions from some unbounded subset of the [positive integers](https://en.wikipedia.org/wiki/Natural_numbers "Natural numbers") to the nonnegative real numbers; then f(x)=O(g(x))
![{\displaystyle f(x)=O{\bigl (}g(x){\bigr )}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9b171ef5a4bf9979e88b862b43b44196c70a2cbe) 

if there exist positive integer numbers M
![{\displaystyle M}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f82cade9898ced02fdd08712e5f0c0151758a0dd) 

and n0
![{\displaystyle n_{0}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/63584d203ecb012a7bcb90f422408bbfe4018956) 

such that |f(n)|≤M|g(n)|
![{\displaystyle |f(n)|\leq M|g(n)|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3346019a35f57a8347a1af4bc0aa46060e1cc73c) 

for all n≥n0.
![{\displaystyle n\geq n_{0}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9d69154ee97b1c6af1b7fc6b0240891a549c3666)

### Example
In typical usage the _O_ notation is asymptotical, that is, it refers to very large x. In this setting, the contribution of the terms that grow "most quickly" will eventually make the other ones irrelevant. As a result, the following simplification rules can be applied:

- If _f_(_x_) is a sum of several terms, if there is one with largest growth rate, it can be kept, and all others omitted.
- If _f_(_x_) is a product of several factors, any constants (factors in the product that do not depend on x) can be omitted.

For example, let _f_(_x_) = 6_x_4 − 2_x_3 + 5, and suppose we wish to simplify this function, using _O_ notation, to describe its growth rate as x approaches infinity. This function is the sum of three terms: 6_x_4, −2_x_3, and 5. Of these three terms, the one with the highest growth rate is the one with the largest exponent as a function of x, namely 6_x_4. Now one may apply the second rule: 6_x_4 is a product of 6 and _x_4 in which the first factor does not depend on _x_. Omitting this factor results in the simplified form _x_4. Thus, we say that _f_(_x_) is a "big O" of _x_4. Mathematically, we can write _f_(_x_) = _O_(_x_4). One may confirm this calculation using the formal definition: let _f_(_x_) = 6_x_4 − 2_x_3 + 5 and _g_(_x_) = _x_4. Applying the [formal definition](https://en.wikipedia.org/wiki/Big_O_notation#Formal_definition) from above, the statement that _f_(_x_) = _O_(_x_4) is equivalent to its expansion,|f(x)|≤Mx4![{\displaystyle |f(x)|\leq Mx^{4}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e05e585265f72da0079873c3bc4a8711ebd115d8)for some suitable choice of a real number _x_0 and a positive real number M and for all _x_ > _x_0. To prove this, let _x_0 = 1 and _M_ = 13. Then, for all _x_ > _x_0:|6x4−2x3+5|≤6x4+|2x3|+5≤6x4+2x4+5x4=13x4
![{\displaystyle {\begin{aligned}|6x^{4}-2x^{3}+5|&\leq 6x^{4}+|2x^{3}|+5\\&\leq 6x^{4}+2x^{4}+5x^{4}\\&=13x^{4}\end{aligned}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/dc926b093c721dee9f23185efef90e122c0acdf4)so|6x4−2x3+5|≤13x4.
![{\displaystyle |6x^{4}-2x^{3}+5|\leq 13x^{4}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/eb23b946983d89787b6ee97bc4cab8ebd39aca96)


## Computational Complexity Theory
In [theoretical computer science](https://en.wikipedia.org/wiki/Theoretical_computer_science "Theoretical computer science") and mathematics, **computational complexity theory** focuses on classifying [computational problems](https://en.wikipedia.org/wiki/Computational_problem "Computational problem") according to their resource usage, and explores the relationships between these classifications. A computational problem is a task solved by a computer. A computation problem is solvable by mechanical application of mathematical steps, such as an [algorithm](https://en.wikipedia.org/wiki/Algorithm "Algorithm").

A problem is regarded as inherently difficult if its solution requires significant resources, whatever the algorithm used. The theory formalizes this intuition, by introducing mathematical [models of computation](https://en.wikipedia.org/wiki/Models_of_computation "Models of computation") to study these problems and quantifying their [computational complexity](https://en.wikipedia.org/wiki/Computational_complexity "Computational complexity"), i.e., the amount of resources needed to solve them, such as time and storage. Other measures of complexity are also used, such as the amount of communication (used in [communication complexity](https://en.wikipedia.org/wiki/Communication_complexity "Communication complexity")), the number of [gates](https://en.wikipedia.org/wiki/Logic_gate "Logic gate") in a circuit (used in [circuit complexity](https://en.wikipedia.org/wiki/Circuit_complexity "Circuit complexity")) and the number of processors (used in [parallel computing](https://en.wikipedia.org/wiki/Parallel_computing "Parallel computing")). One of the roles of computational complexity theory is to determine the practical limits on what computers can and cannot do. The [P versus NP problem](https://en.wikipedia.org/wiki/P_versus_NP_problem "P versus NP problem"), one of the seven [Millennium Prize Problems](https://en.wikipedia.org/wiki/Millennium_Prize_Problems "Millennium Prize Problems"), is part of the field of computational complexity.

Closely related fields in [theoretical computer science](https://en.wikipedia.org/wiki/Theoretical_computer_science "Theoretical computer science") are [analysis of algorithms](https://en.wikipedia.org/wiki/Analysis_of_algorithms "Analysis of algorithms") and [computability theory](https://en.wikipedia.org/wiki/Computability_theory "Computability theory"). A key distinction between analysis of algorithms and computational complexity theory is that the former is devoted to analyzing the amount of resources needed by a particular algorithm to solve a problem, whereas the latter asks a more general question about all possible algorithms that could be used to solve the same problem. More precisely, computational complexity theory tries to classify problems that can or cannot be solved with appropriately restricted resources. In turn, imposing restrictions on the available resources is what distinguishes computational complexity from computability theory: the latter theory asks what kinds of problems can, in principle, be solved algorithmically.

### Computational problems
[![](https://upload.wikimedia.org/wikipedia/commons/c/c4/TSP_Deutschland_3.png)](https://en.wikipedia.org/wiki/File:TSP_Deutschland_3.png)

A traveling salesman tour through 14 German cities

#### Problem instances
A [computational problem](https://en.wikipedia.org/wiki/Computational_problem "Computational problem") can be viewed as an infinite collection of _instances_ together with a set (possibly empty) of _solutions_ for every instance. The input string for a computational problem is referred to as a problem instance, and should not be confused with the problem itself. In computational complexity theory, a problem refers to the abstract question to be solved. In contrast, an instance of this problem is a rather concrete utterance, which can serve as the input for a decision problem. For example, consider the problem of [primality testing](https://en.wikipedia.org/wiki/Primality_testing "Primality testing"). The instance is a number (e.g., 15) and the solution is "yes" if the number is prime and "no" otherwise (in this case, 15 is not prime and the answer is "no"). Stated another way, the _instance_ is a particular input to the problem, and the _solution_ is the output corresponding to the given input.

To further highlight the difference between a problem and an instance, consider the following instance of the decision version of the [travelling salesman problem](https://en.wikipedia.org/wiki/Travelling_salesman_problem "Travelling salesman problem"): Is there a route of at most 2000 kilometres passing through all of Germany's 15 largest cities? The quantitative answer to this particular problem instance is of little use for solving other instances of the problem, such as asking for a round trip through all sites in [Milan](https://en.wikipedia.org/wiki/Milan "Milan") whose total length is at most 10 km. For this reason, complexity theory addresses computational problems and not particular problem instances.

#### Representing problem instances
When considering computational problems, a problem instance is a [string](https://en.wikipedia.org/wiki/String_(computer_science) "String (computer science)") over an [alphabet](https://en.wikipedia.org/wiki/Alphabet_(computer_science) "Alphabet (computer science)"). Usually, the alphabet is taken to be the binary alphabet (i.e., the set {0,1}), and thus the strings are [bitstrings](https://en.wikipedia.org/wiki/Bitstring "Bitstring"). As in a real-world [computer](https://en.wikipedia.org/wiki/Computer "Computer"), mathematical objects other than bitstrings must be suitably encoded. For example, [integers](https://en.wikipedia.org/wiki/Integer "Integer") can be represented in [binary notation](https://en.wikipedia.org/wiki/Binary_notation "Binary notation"), and [graphs](https://en.wikipedia.org/wiki/Graph_(discrete_mathematics) "Graph (discrete mathematics)") can be encoded directly via their [adjacency matrices](https://en.wikipedia.org/wiki/Adjacency_matrix "Adjacency matrix"), or by encoding their [adjacency lists](https://en.wikipedia.org/wiki/Adjacency_list "Adjacency list") in binary.

Even though some proofs of complexity-theoretic theorems regularly assume some concrete choice of input encoding, one tries to keep the discussion abstract enough to be independent of the choice of encoding. This can be achieved by ensuring that different representations can be transformed into each other efficiently.

#### Decision problems as formal languages
[![](https://upload.wikimedia.org/wikipedia/commons/thumb/0/06/Decision_Problem.svg/220px-Decision_Problem.svg.png)](https://en.wikipedia.org/wiki/File:Decision_Problem.svg)

A [decision problem](https://en.wikipedia.org/wiki/Decision_problem "Decision problem") has only two possible outputs, _yes_ or _no_ (or alternately 1 or 0) on any input.

[Decision problems](https://en.wikipedia.org/wiki/Decision_problem "Decision problem") are one of the central objects of study in computational complexity theory. A decision problem is a type of computational problem where the answer is either _yes_ or _no_ (alternatively, 1 or 0). A decision problem can be viewed as a [formal language](https://en.wikipedia.org/wiki/Formal_language "Formal language"), where the members of the language are instances whose output is yes, and the non-members are those instances whose output is no. The objective is to decide, with the aid of an [algorithm](https://en.wikipedia.org/wiki/Algorithm "Algorithm"), whether a given input string is a member of the formal language under consideration. If the algorithm deciding this problem returns the answer _yes_, the algorithm is said to accept the input string, otherwise it is said to reject the input.

An example of a decision problem is the following. The input is an arbitrary [graph](https://en.wikipedia.org/wiki/Graph_(discrete_mathematics) "Graph (discrete mathematics)"). The problem consists in deciding whether the given graph is [connected](https://en.wikipedia.org/wiki/Connectivity_(graph_theory) "Connectivity (graph theory)") or not. The formal language associated with this decision problem is then the set of all connected graphs — to obtain a precise definition of this language, one has to decide how graphs are encoded as binary strings.

#### Function problems
A [function problem](https://en.wikipedia.org/wiki/Function_problem "Function problem") is a computational problem where a single output (of a [total function](https://en.wikipedia.org/wiki/Total_function "Total function")) is expected for every input, but the output is more complex than that of a [decision problem](https://en.wikipedia.org/wiki/Decision_problem "Decision problem")—that is, the output is not just yes or no. Notable examples include the [traveling salesman problem](https://en.wikipedia.org/wiki/Traveling_salesman_problem "Traveling salesman problem") and the [integer factorization problem](https://en.wikipedia.org/wiki/Integer_factorization_problem "Integer factorization problem").

It is tempting to think that the notion of function problems is much richer than the notion of decision problems. However, this is not really the case, since function problems can be recast as decision problems. For example, the multiplication of two integers can be expressed as the set of triples (a,b,c)
![{\displaystyle (a,b,c)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ae973a762a92b9cd3eafe7f283890ccfa9b887e8) 

such that the relation a×b=c
![{\displaystyle a\times b=c}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1272c2667a4b31fc639ab3c998d30fb011f89b2f) 

holds. Deciding whether a given triple is a member of this set corresponds to solving the problem of multiplying two numbers.

#### Measuring the size of an instance
To measure the difficulty of solving a computational problem, one may wish to see how much time the best algorithm requires to solve the problem. However, the running time may, in general, depend on the instance. In particular, larger instances will require more time to solve. Thus the time required to solve a problem (or the space required, or any measure of complexity) is calculated as a function of the size of the instance. The input size is typically measured in bits. Complexity theory studies how algorithms scale as input size increases. For instance, in the problem of finding whether a graph is connected, how much more time does it take to solve a problem for a graph with 2n
![{\displaystyle 2n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/134afa8ff09fdddd24b06f289e92e3a045092bd1) 

vertices compared to the time taken for a graph with n
![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) 

vertices?

If the input size is n
![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b)

, the time taken can be expressed as a function of n
![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b)

. Since the time taken on different inputs of the same size can be different, the worst-case time complexity T(n)
![{\displaystyle T(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0be5a46684e1279c27414b285fa995f30407d002) 

is defined to be the maximum time taken over all inputs of size n
![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b)

. If T(n)
![{\displaystyle T(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0be5a46684e1279c27414b285fa995f30407d002) 

is a polynomial in n
![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b)

, then the algorithm is said to be a [polynomial time](https://en.wikipedia.org/wiki/Polynomial_time "Polynomial time") algorithm. [Cobham's thesis](https://en.wikipedia.org/wiki/Cobham%27s_thesis "Cobham's thesis") argues that a problem can be solved with a feasible amount of resources if it admits a polynomial-time algorithm.

### Machine models and complexity measures
#### Turing machine

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a2/Turing_machine_2b.svg/220px-Turing_machine_2b.svg.png)](https://en.wikipedia.org/wiki/File:Turing_machine_2b.svg)

An illustration of a Turing machine

A Turing machine is a mathematical model of a general computing machine. It is a theoretical device that manipulates symbols contained on a strip of tape. Turing machines are not intended as a practical computing technology, but rather as a general model of a computing machine—anything from an advanced supercomputer to a mathematician with a pencil and paper. It is believed that if a problem can be solved by an algorithm, there exists a Turing machine that solves the problem. Indeed, this is the statement of the [Church–Turing thesis](https://en.wikipedia.org/wiki/Church%E2%80%93Turing_thesis "Church–Turing thesis"). Furthermore, it is known that everything that can be computed on other models of computation known to us today, such as a [RAM machine](https://en.wikipedia.org/wiki/RAM_machine "RAM machine"), [Conway's Game of Life](https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life "Conway's Game of Life"), [cellular automata](https://en.wikipedia.org/wiki/Cellular_automata "Cellular automata"), [lambda calculus](https://en.wikipedia.org/wiki/Lambda_calculus "Lambda calculus") or any programming language can be computed on a Turing machine. Since Turing machines are easy to analyze mathematically, and are believed to be as powerful as any other model of computation, the Turing machine is the most commonly used model in complexity theory.

Many types of Turing machines are used to define complexity classes, such as [deterministic Turing machines](https://en.wikipedia.org/wiki/Deterministic_Turing_machine "Deterministic Turing machine"), [probabilistic Turing machines](https://en.wikipedia.org/wiki/Probabilistic_Turing_machine "Probabilistic Turing machine"), [non-deterministic Turing machines](https://en.wikipedia.org/wiki/Non-deterministic_Turing_machine "Non-deterministic Turing machine"), [quantum Turing machines](https://en.wikipedia.org/wiki/Quantum_Turing_machine "Quantum Turing machine"), [symmetric Turing machines](https://en.wikipedia.org/wiki/Symmetric_Turing_machine "Symmetric Turing machine") and [alternating Turing machines](https://en.wikipedia.org/wiki/Alternating_Turing_machine "Alternating Turing machine"). They are all equally powerful in principle, but when resources (such as time or space) are bounded, some of these may be more powerful than others.

A deterministic Turing machine is the most basic Turing machine, which uses a fixed set of rules to determine its future actions. A probabilistic Turing machine is a deterministic Turing machine with an extra supply of random bits. The ability to make probabilistic decisions often helps algorithms solve problems more efficiently. Algorithms that use random bits are called [randomized algorithms](https://en.wikipedia.org/wiki/Randomized_algorithm "Randomized algorithm"). A non-deterministic Turing machine is a deterministic Turing machine with an added feature of non-determinism, which allows a Turing machine to have multiple possible future actions from a given state. One way to view non-determinism is that the Turing machine branches into many possible computational paths at each step, and if it solves the problem in any of these branches, it is said to have solved the problem. Clearly, this model is not meant to be a physically realizable model, it is just a theoretically interesting abstract machine that gives rise to particularly interesting complexity classes. For examples, see [non-deterministic algorithm](https://en.wikipedia.org/wiki/Non-deterministic_algorithm "Non-deterministic algorithm").

#### Other machine models
Many machine models different from the standard [multi-tape Turing machines](https://en.wikipedia.org/wiki/Turing_machine_equivalents#Multi-tape_Turing_machines "Turing machine equivalents") have been proposed in the literature, for example [random-access machines](https://en.wikipedia.org/wiki/Random-access_machine "Random-access machine"). Perhaps surprisingly, each of these models can be converted to another without providing any extra computational power. The time and memory consumption of these alternate models may vary. What all these models have in common is that the machines operate [deterministically](https://en.wikipedia.org/wiki/Deterministic_algorithm "Deterministic algorithm").

However, some computational problems are easier to analyze in terms of more unusual resources. For example, a non-deterministic Turing machine is a computational model that is allowed to branch out to check many different possibilities at once. The non-deterministic Turing machine has very little to do with how we physically want to compute algorithms, but its branching exactly captures many of the mathematical models we want to analyze, so that [non-deterministic time](https://en.wikipedia.org/wiki/Non-deterministic_time "Non-deterministic time") is a very important resource in analyzing computational problems.

#### Complexity measures
For a precise definition of what it means to solve a problem using a given amount of time and space, a computational model such as the [deterministic Turing machine](https://en.wikipedia.org/wiki/Deterministic_Turing_machine "Deterministic Turing machine") is used. The _time required_ by a deterministic Turing machine M
![{\displaystyle M}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f82cade9898ced02fdd08712e5f0c0151758a0dd) 

on input x
![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) 

is the total number of state transitions, or steps, the machine makes before it halts and outputs the answer ("yes" or "no"). A Turing machine M
![{\displaystyle M}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f82cade9898ced02fdd08712e5f0c0151758a0dd) 

is said to operate within time f(n)
![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973) 

if the time required by M
![{\displaystyle M}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f82cade9898ced02fdd08712e5f0c0151758a0dd) 

on each input of length n
![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) 

is at most f(n)
![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973)

. A decision problem A
![{\displaystyle A}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3) 

can be solved in time f(n)
![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973) 

if there exists a Turing machine operating in time f(n)
![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973) 

that solves the problem. Since complexity theory is interested in classifying problems based on their difficulty, one defines sets of problems based on some criteria. For instance, the set of problems solvable within time f(n)
![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973) 

on a deterministic Turing machine is then denoted by [DTIME](https://en.wikipedia.org/wiki/DTIME "DTIME")(f(n)
![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973)

).

Analogous definitions can be made for space requirements. Although time and space are the most well-known complexity resources, any [complexity measure](https://en.wikipedia.org/wiki/Complexity "Complexity") can be viewed as a computational resource. Complexity measures are very generally defined by the [Blum complexity axioms](https://en.wikipedia.org/wiki/Blum_complexity_axioms "Blum complexity axioms"). Other complexity measures used in complexity theory include [communication complexity](https://en.wikipedia.org/wiki/Communication_complexity "Communication complexity"), [circuit complexity](https://en.wikipedia.org/wiki/Circuit_complexity "Circuit complexity"), and [decision tree complexity](https://en.wikipedia.org/wiki/Decision_tree_complexity "Decision tree complexity").
#### Best, worst and average case complexity
[![](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6a/Sorting_quicksort_anim.gif/220px-Sorting_quicksort_anim.gif)](https://en.wikipedia.org/wiki/File:Sorting_quicksort_anim.gif)

Visualization of the [quicksort](https://en.wikipedia.org/wiki/Quicksort "Quicksort") [algorithm](https://en.wikipedia.org/wiki/Algorithm "Algorithm") that has [average case performance](https://en.wikipedia.org/wiki/Best,_worst_and_average_case "Best, worst and average case") O(nlog⁡n)
![{\displaystyle {\mathcal {O}}(n\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9981ede263cbf28215d3a70bf30f55db41a6e692)

The [best, worst and average case](https://en.wikipedia.org/wiki/Best,_worst_and_average_case "Best, worst and average case") complexity refer to three different ways of measuring the time complexity (or any other complexity measure) of different inputs of the same size. Since some inputs of size n
![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) 

may be faster to solve than others, we define the following complexities:
1. Best-case complexity: This is the complexity of solving the problem for the best input of size n
 ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b)
2. Average-case complexity: This is the complexity of solving the problem on an average. This complexity is only defined with respect to a [probability distribution](https://en.wikipedia.org/wiki/Probability_distribution "Probability distribution") over the inputs. For instance, if all inputs of the same size are assumed to be equally likely to appear, the average case complexity can be defined with respect to the uniform distribution over all inputs of size n
 ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b)
3. [Amortized analysis](https://en.wikipedia.org/wiki/Amortized_analysis "Amortized analysis"): Amortized analysis considers both the costly and less costly operations together over the whole series of operations of the algorithm.
4. Worst-case complexity: This is the complexity of solving the problem for the worst input of size n
![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b)

The order from cheap to costly is: Best, average (of [discrete uniform distribution](https://en.wikipedia.org/wiki/Discrete_uniform_distribution "Discrete uniform distribution")), amortized, worst.

For example, the deterministic sorting algorithm [quicksort](https://en.wikipedia.org/wiki/Quicksort "Quicksort") addresses the problem of sorting a list of integers. The worst-case is when the pivot is always the largest or smallest value in the list (so the list is never divided). In this case, the algorithm takes time [O](https://en.wikipedia.org/wiki/Big_O_notation "Big O notation")(n2
![{\displaystyle n^{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ac9810bbdafe4a6a8061338db0f74e25b7952620)). If we assume that all possible permutations of the input list are equally likely, the average time taken for sorting is O(nlog⁡n)
![{\displaystyle O(n\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9d2320768fb54880ca4356e61f60eb02a3f9d9f1)

. The best case occurs when each pivoting divides the list in half, also needing O(nlog⁡n)
![{\displaystyle O(n\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9d2320768fb54880ca4356e61f60eb02a3f9d9f1) 

time.

#### Upper and lower bounds on the complexity of problems
To classify the computation time (or similar resources, such as space consumption), it is helpful to demonstrate upper and lower bounds on the maximum amount of time required by the most efficient algorithm to solve a given problem. The complexity of an algorithm is usually taken to be its worst-case complexity unless specified otherwise. Analyzing a particular algorithm falls under the field of [analysis of algorithms](https://en.wikipedia.org/wiki/Analysis_of_algorithms "Analysis of algorithms"). To show an upper bound T(n)
![{\displaystyle T(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0be5a46684e1279c27414b285fa995f30407d002) 

on the time complexity of a problem, one needs to show only that there is a particular algorithm with running time at most T(n)
![{\displaystyle T(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0be5a46684e1279c27414b285fa995f30407d002)

. However, proving lower bounds is much more difficult, since lower bounds make a statement about all possible algorithms that solve a given problem. The phrase "all possible algorithms" includes not just the algorithms known today, but any algorithm that might be discovered in the future. To show a lower bound of T(n)
![{\displaystyle T(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0be5a46684e1279c27414b285fa995f30407d002) 

for a problem requires showing that no algorithm can have time complexity lower than T(n)
![{\displaystyle T(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0be5a46684e1279c27414b285fa995f30407d002)

Upper and lower bounds are usually stated using the [big O notation](https://en.wikipedia.org/wiki/Big_O_notation "Big O notation"), which hides constant factors and smaller terms. This makes the bounds independent of the specific details of the computational model used. For instance, if T(n)=7n2+15n+40
![{\displaystyle T(n)=7n^{2}+15n+40}](https://wikimedia.org/api/rest_v1/media/math/render/svg/290239c7be0f10b25e09862f2cbb6429ff503ce3)

, in big O notation one would write T(n)=O(n2)
![{\displaystyle T(n)=O(n^{2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8526253f8646d3899c4b3f99b6b1c1d3d911a33c)

### Complexity classes
#### Defining complexity classes
A **complexity class** is a set of problems of related complexity. Simpler complexity classes are defined by the following factors:

- The type of computational problem: The most commonly used problems are decision problems. However, complexity classes can be defined based on [function problems](https://en.wikipedia.org/wiki/Function_problem "Function problem"), [counting problems](https://en.wikipedia.org/wiki/Counting_problem_(complexity) "Counting problem (complexity)"), [optimization problems](https://en.wikipedia.org/wiki/Optimization_problem "Optimization problem"), [promise problems](https://en.wikipedia.org/wiki/Promise_problem "Promise problem"), etc.
- The model of computation: The most common model of computation is the deterministic Turing machine, but many complexity classes are based on non-deterministic Turing machines, [Boolean circuits](https://en.wikipedia.org/wiki/Boolean_circuit "Boolean circuit"), [quantum Turing machines](https://en.wikipedia.org/wiki/Quantum_Turing_machine "Quantum Turing machine"), [monotone circuits](https://en.wikipedia.org/wiki/Monotone_circuit "Monotone circuit"), etc.
- The resource (or resources) that is being bounded and the bound: These two properties are usually stated together, such as "polynomial time", "logarithmic space", "constant depth", etc.

Some complexity classes have complicated definitions that do not fit into this framework. Thus, a typical complexity class has a definition like the following:

The set of decision problems solvable by a deterministic Turing machine within time f(n)
![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973)

. (This complexity class is known as DTIME(f(n)
![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973)

).)

But bounding the computation time above by some concrete function f(n)
![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973) 

often yields complexity classes that depend on the chosen machine model. For instance, the language {xx∣x is any binary string}
![{\displaystyle \{xx\mid x{\text{ is any binary string}}\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/18769151cf5f5bfcc9b996d4beebb23bcfc32dbc) 

can be solved in [linear time](https://en.wikipedia.org/wiki/Linear_time "Linear time") on a multi-tape Turing machine, but necessarily requires quadratic time in the model of single-tape Turing machines. If we allow polynomial variations in running time, [Cobham-Edmonds thesis](https://en.wikipedia.org/wiki/Cobham%27s_thesis "Cobham's thesis") states that "the time complexities in any two reasonable and general models of computation are polynomially related" ([Goldreich 2008](https://en.wikipedia.org/wiki/Computational_complexity_theory#CITEREFGoldreich2008), Chapter 1.2). This forms the basis for the complexity class [P](https://en.wikipedia.org/wiki/P_(complexity) "P (complexity)"), which is the set of decision problems solvable by a deterministic Turing machine within polynomial time. The corresponding set of function problems is [FP](https://en.wikipedia.org/wiki/FP_(complexity) "FP (complexity)").

#### Important complexity classes
[![](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6e/Complexity_subsets_pspace.svg/220px-Complexity_subsets_pspace.svg.png)](https://en.wikipedia.org/wiki/File:Complexity_subsets_pspace.svg)

A representation of the relation among complexity classes; L would be another step "inside" NL

Many important complexity classes can be defined by bounding the time or space used by the algorithm. Some important complexity classes of decision problems defined in this manner are the following:

|Resource|Determinism|Complexity class|Resource constraint|
|---|---|---|---|
|Space|Non-Deterministic|[NSPACE](https://en.wikipedia.org/wiki/NSPACE "NSPACE")(f(n)![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973))|O(f(n))![{\displaystyle O(f(n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/756b4d8648334719f65bf5e6269c7a2b3a502f13)|
|[NL](https://en.wikipedia.org/wiki/NL_(complexity) "NL (complexity)")|O(log⁡n)![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d)|
|[NPSPACE](https://en.wikipedia.org/wiki/NPSPACE "NPSPACE")|O(poly(n))![{\displaystyle O({\text{poly}}(n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/668c1881ecd020e37ec301b68377cf2b38dc3d7e)|
|[NEXPSPACE](https://en.wikipedia.org/wiki/NEXPSPACE "NEXPSPACE")|O(2poly(n))![{\displaystyle O(2^{{\text{poly}}(n)})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fa41c21ee3cdbe36df6dc6ffed8a44ba63b5034f)|
|Deterministic|[DSPACE](https://en.wikipedia.org/wiki/DSPACE "DSPACE")(f(n)![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973))|O(f(n))![{\displaystyle O(f(n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/756b4d8648334719f65bf5e6269c7a2b3a502f13)|
|[L](https://en.wikipedia.org/wiki/L_(complexity) "L (complexity)")|O(log⁡n)![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d)|
|[PSPACE](https://en.wikipedia.org/wiki/PSPACE "PSPACE")|O(poly(n))![{\displaystyle O({\text{poly}}(n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/668c1881ecd020e37ec301b68377cf2b38dc3d7e)|
|[EXPSPACE](https://en.wikipedia.org/wiki/EXPSPACE "EXPSPACE")|O(2poly(n))![{\displaystyle O(2^{{\text{poly}}(n)})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fa41c21ee3cdbe36df6dc6ffed8a44ba63b5034f)|
|Time|Non-Deterministic|[NTIME](https://en.wikipedia.org/wiki/NTIME "NTIME")(f(n)![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973))|O(f(n))![{\displaystyle O(f(n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/756b4d8648334719f65bf5e6269c7a2b3a502f13)|
|[NP](https://en.wikipedia.org/wiki/NP_(complexity) "NP (complexity)")|O(poly(n))![{\displaystyle O({\text{poly}}(n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/668c1881ecd020e37ec301b68377cf2b38dc3d7e)|
|[NEXPTIME](https://en.wikipedia.org/wiki/NEXPTIME "NEXPTIME")|O(2poly(n))![{\displaystyle O(2^{{\text{poly}}(n)})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fa41c21ee3cdbe36df6dc6ffed8a44ba63b5034f)|
|Deterministic|[DTIME](https://en.wikipedia.org/wiki/DTIME "DTIME")(f(n)![{\displaystyle f(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c1c49fad1eccc4e9af1e4f23f32efdc3ac4da973))|O(f(n))![{\displaystyle O(f(n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/756b4d8648334719f65bf5e6269c7a2b3a502f13)|
|[P](https://en.wikipedia.org/wiki/P_(complexity) "P (complexity)")|O(poly(n))![{\displaystyle O({\text{poly}}(n))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/668c1881ecd020e37ec301b68377cf2b38dc3d7e)|
|[EXPTIME](https://en.wikipedia.org/wiki/EXPTIME "EXPTIME")|O(2poly(n))![{\displaystyle O(2^{{\text{poly}}(n)})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fa41c21ee3cdbe36df6dc6ffed8a44ba63b5034f)|

Logarithmic-space classes do not account for the space required to represent the problem.

It turns out that PSPACE = NPSPACE and EXPSPACE = NEXPSPACE by [Savitch's theorem](https://en.wikipedia.org/wiki/Savitch%27s_theorem "Savitch's theorem").

Other important complexity classes include [BPP](https://en.wikipedia.org/wiki/BPP_(complexity) "BPP (complexity)"), [ZPP](https://en.wikipedia.org/wiki/ZPP_(complexity) "ZPP (complexity)") and [RP](https://en.wikipedia.org/wiki/RP_(complexity) "RP (complexity)"), which are defined using [probabilistic Turing machines](https://en.wikipedia.org/wiki/Probabilistic_Turing_machine "Probabilistic Turing machine"); [AC](https://en.wikipedia.org/wiki/AC_(complexity) "AC (complexity)") and [NC](https://en.wikipedia.org/wiki/NC_(complexity) "NC (complexity)"), which are defined using Boolean circuits; and [BQP](https://en.wikipedia.org/wiki/BQP "BQP") and [QMA](https://en.wikipedia.org/wiki/QMA "QMA"), which are defined using quantum Turing machines. [#P](https://en.wikipedia.org/wiki/Sharp-P "Sharp-P") is an important complexity class of counting problems (not decision problems). Classes like [IP](https://en.wikipedia.org/wiki/IP_(complexity) "IP (complexity)") and [AM](https://en.wikipedia.org/wiki/AM_(complexity) "AM (complexity)") are defined using [Interactive proof systems](https://en.wikipedia.org/wiki/Interactive_proof_system "Interactive proof system"). [ALL](https://en.wikipedia.org/wiki/ALL_(complexity) "ALL (complexity)") is the class of all decision problems.

#### Hierarchy theorems
For the complexity classes defined in this way, it is desirable to prove that relaxing the requirements on (say) computation time indeed defines a bigger set of problems. In particular, although DTIME(n
![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b)

) is contained in DTIME(n2
![{\displaystyle n^{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ac9810bbdafe4a6a8061338db0f74e25b7952620)

), it would be interesting to know if the inclusion is strict. For time and space requirements, the answer to such questions is given by the time and space hierarchy theorems respectively. They are called hierarchy theorems because they induce a proper hierarchy on the classes defined by constraining the respective resources. Thus there are pairs of complexity classes such that one is properly included in the other. Having deduced such proper set inclusions, we can proceed to make quantitative statements about how much more additional time or space is needed in order to increase the number of problems that can be solved.

More precisely, the [time hierarchy theorem](https://en.wikipedia.org/wiki/Time_hierarchy_theorem "Time hierarchy theorem") states that DTIME(o(f(n)))⊊DTIME(f(n)⋅log⁡(f(n)))
![{\displaystyle {\mathsf {DTIME}}{\big (}o(f(n)){\big )}\subsetneq {\mathsf {DTIME}}{\big (}f(n)\cdot \log(f(n)){\big )}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3132fd5c216316bd45568d19d23eb750c12a0c54)

The [space hierarchy theorem](https://en.wikipedia.org/wiki/Space_hierarchy_theorem "Space hierarchy theorem") states that DSPACE(o(f(n)))⊊DSPACE(f(n))
![{\displaystyle {\mathsf {DSPACE}}{\big (}o(f(n)){\big )}\subsetneq {\mathsf {DSPACE}}{\big (}f(n){\big )}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/988ed215d1eb420de36722d6440842177aefd288)

The time and space hierarchy theorems form the basis for most separation results of complexity classes. For instance, the time hierarchy theorem tells us that P is strictly contained in EXPTIME, and the space hierarchy theorem tells us that L is strictly contained in PSPACE.

#### Reduction
Many complexity classes are defined using the concept of a reduction. A reduction is a transformation of one problem into another problem. It captures the informal notion of a problem being at most as difficult as another problem. For instance, if a problem X![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab) can be solved using an algorithm for Y![{\displaystyle Y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/961d67d6b454b4df2301ac571808a3538b3a6d3f), X![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab) is no more difficult than Y![{\displaystyle Y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/961d67d6b454b4df2301ac571808a3538b3a6d3f), and we say that X![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab) _reduces_ to Y![{\displaystyle Y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/961d67d6b454b4df2301ac571808a3538b3a6d3f). There are many different types of reductions, based on the method of reduction, such as Cook reductions, Karp reductions and Levin reductions, and the bound on the complexity of reductions, such as [polynomial-time reductions](https://en.wikipedia.org/wiki/Polynomial-time_reduction "Polynomial-time reduction") or [log-space reductions](https://en.wikipedia.org/wiki/Log-space_reduction "Log-space reduction").

The most commonly used reduction is a polynomial-time reduction. This means that the reduction process takes polynomial time. For example, the problem of squaring an integer can be reduced to the problem of multiplying two integers. This means an algorithm for multiplying two integers can be used to square an integer. Indeed, this can be done by giving the same input to both inputs of the multiplication algorithm. Thus we see that squaring is not more difficult than multiplication, since squaring can be reduced to multiplication.

This motivates the concept of a problem being hard for a complexity class. A problem X![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab) is _hard_ for a class of problems C![{\displaystyle C}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4fc55753007cd3c18576f7933f6f089196732029) if every problem in C![{\displaystyle C}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4fc55753007cd3c18576f7933f6f089196732029) can be reduced to X![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab). Thus no problem in C![{\displaystyle C}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4fc55753007cd3c18576f7933f6f089196732029) is harder than X![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab), since an algorithm for X![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab) allows us to solve any problem in C![{\displaystyle C}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4fc55753007cd3c18576f7933f6f089196732029). The notion of hard problems depends on the type of reduction being used. For complexity classes larger than P, polynomial-time reductions are commonly used. In particular, the set of problems that are hard for NP is the set of [NP-hard](https://en.wikipedia.org/wiki/NP-hard "NP-hard") problems.

If a problem X![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab) is in C![{\displaystyle C}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4fc55753007cd3c18576f7933f6f089196732029) and hard for C![{\displaystyle C}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4fc55753007cd3c18576f7933f6f089196732029), then X![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab) is said to be _[complete](https://en.wikipedia.org/wiki/Complete_(complexity) "Complete (complexity)")_ for C![{\displaystyle C}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4fc55753007cd3c18576f7933f6f089196732029). This means that X![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab) is the hardest problem in C![{\displaystyle C}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4fc55753007cd3c18576f7933f6f089196732029). (Since many problems could be equally hard, one might say that X![{\displaystyle X}](https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab) is one of the hardest problems in C![{\displaystyle C}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4fc55753007cd3c18576f7933f6f089196732029).) Thus the class of [NP-complete](https://en.wikipedia.org/wiki/NP-complete "NP-complete") problems contains the most difficult problems in NP, in the sense that they are the ones most likely not to be in P. Because the problem P = NP is not solved, being able to reduce a known NP-complete problem, Π2![{\displaystyle \Pi _{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/10e0f32ab9da5560199913701cfdb210e7b32736), to another problem, Π1![{\displaystyle \Pi _{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4aab5a28da997de9084eef3e569bd1e072efc1aa), would indicate that there is no known polynomial-time solution for Π1![{\displaystyle \Pi _{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4aab5a28da997de9084eef3e569bd1e072efc1aa). This is because a polynomial-time solution to Π1![{\displaystyle \Pi _{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4aab5a28da997de9084eef3e569bd1e072efc1aa) would yield a polynomial-time solution to Π2![{\displaystyle \Pi _{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/10e0f32ab9da5560199913701cfdb210e7b32736). Similarly, because all NP problems can be reduced to the set, finding an [NP-complete](https://en.wikipedia.org/wiki/NP-complete "NP-complete") problem that can be solved in polynomial time would mean that P = NP.

### Important open problems
[![](https://upload.wikimedia.org/wikipedia/commons/thumb/b/bc/Complexity_classes.svg/220px-Complexity_classes.svg.png)](https://en.wikipedia.org/wiki/File:Complexity_classes.svg)

Diagram of complexity classes provided that P ≠ NP. The existence of problems in NP outside both P and NP-complete in this case was established by Ladner.

#### P versus NP problem
The complexity class P is often seen as a mathematical abstraction modeling those computational tasks that admit an efficient algorithm. This hypothesis is called the [Cobham–Edmonds thesis](https://en.wikipedia.org/wiki/Cobham%E2%80%93Edmonds_thesis "Cobham–Edmonds thesis"). The complexity class [NP](https://en.wikipedia.org/wiki/NP_(complexity) "NP (complexity)"), on the other hand, contains many problems that people would like to solve efficiently, but for which no efficient algorithm is known, such as the [Boolean satisfiability problem](https://en.wikipedia.org/wiki/Boolean_satisfiability_problem "Boolean satisfiability problem"), the [Hamiltonian path problem](https://en.wikipedia.org/wiki/Hamiltonian_path_problem "Hamiltonian path problem") and the [vertex cover problem](https://en.wikipedia.org/wiki/Vertex_cover_problem "Vertex cover problem"). Since deterministic Turing machines are special non-deterministic Turing machines, it is easily observed that each problem in P is also member of the class NP.

The question of whether P equals NP is one of the most important open questions in theoretical computer science because of the wide implications of a solution. If the answer is yes, many important problems can be shown to have more efficient solutions. These include various types of [integer programming](https://en.wikipedia.org/wiki/Integer_programming "Integer programming") problems in [operations research](https://en.wikipedia.org/wiki/Operations_research "Operations research"), many problems in [logistics](https://en.wikipedia.org/wiki/Logistics "Logistics"), [protein structure prediction](https://en.wikipedia.org/wiki/Protein_structure_prediction "Protein structure prediction") in [biology](https://en.wikipedia.org/wiki/Biology "Biology"), and the ability to find formal proofs of [pure mathematics](https://en.wikipedia.org/wiki/Pure_mathematics "Pure mathematics") theorems. The P versus NP problem is one of the [Millennium Prize Problems](https://en.wikipedia.org/wiki/Millennium_Prize_Problems "Millennium Prize Problems") proposed by the [Clay Mathematics Institute](https://en.wikipedia.org/wiki/Clay_Mathematics_Institute "Clay Mathematics Institute"). There is a US$1,000,000 prize for resolving the problem.

#### Problems in NP not known to be in P or NP-complete
It was shown by Ladner that if P≠NP![{\displaystyle P\neq NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/91730efe5e62816c7c61cdc6eafc8e77e924540e) then there exist problems in NP![{\displaystyle NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cbb96b0c7cdeba71278d234f3478d41964dfa1dd) that are neither in P![{\displaystyle P}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b4dc73bf40314945ff376bd363916a738548d40a) nor NP![{\displaystyle NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cbb96b0c7cdeba71278d234f3478d41964dfa1dd)-complete. Such problems are called [NP-intermediate](https://en.wikipedia.org/wiki/NP-intermediate "NP-intermediate") problems. The [graph isomorphism problem](https://en.wikipedia.org/wiki/Graph_isomorphism_problem "Graph isomorphism problem"), the [discrete logarithm problem](https://en.wikipedia.org/wiki/Discrete_logarithm_problem "Discrete logarithm problem") and the [integer factorization problem](https://en.wikipedia.org/wiki/Integer_factorization_problem "Integer factorization problem") are examples of problems believed to be NP-intermediate. They are some of the very few NP problems not known to be in P![{\displaystyle P}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b4dc73bf40314945ff376bd363916a738548d40a) or to be NP![{\displaystyle NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cbb96b0c7cdeba71278d234f3478d41964dfa1dd)-complete.

The [graph isomorphism problem](https://en.wikipedia.org/wiki/Graph_isomorphism_problem "Graph isomorphism problem") is the computational problem of determining whether two finite [graphs](https://en.wikipedia.org/wiki/Graph_(discrete_mathematics) "Graph (discrete mathematics)") are [isomorphic](https://en.wikipedia.org/wiki/Graph_isomorphism "Graph isomorphism"). An important unsolved problem in complexity theory is whether the graph isomorphism problem is in P![{\displaystyle P}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b4dc73bf40314945ff376bd363916a738548d40a), NP![{\displaystyle NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cbb96b0c7cdeba71278d234f3478d41964dfa1dd)-complete, or NP-intermediate. The answer is not known, but it is believed that the problem is at least not NP-complete. If graph isomorphism is NP-complete, the [polynomial time hierarchy](https://en.wikipedia.org/wiki/Polynomial_time_hierarchy "Polynomial time hierarchy") collapses to its second level. Since it is widely believed that the polynomial hierarchy does not collapse to any finite level, it is believed that graph isomorphism is not NP-complete. The best algorithm for this problem, due to [László Babai](https://en.wikipedia.org/wiki/L%C3%A1szl%C3%B3_Babai "László Babai") and [Eugene Luks](https://en.wikipedia.org/wiki/Eugene_Luks "Eugene Luks") has run time O(2nlog⁡n)![{\displaystyle O(2^{\sqrt {n\log n}})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d4186036dc1b46116f1fbd2d2ca92d9c4bf3d040) for graphs with n![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) vertices, although some recent work by Babai offers some potentially new perspectives on this.

The [integer factorization problem](https://en.wikipedia.org/wiki/Integer_factorization_problem "Integer factorization problem") is the computational problem of determining the [prime factorization](https://en.wikipedia.org/wiki/Prime_factorization "Prime factorization") of a given integer. Phrased as a decision problem, it is the problem of deciding whether the input has a prime factor less than k![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40). No efficient integer factorization algorithm is known, and this fact forms the basis of several modern cryptographic systems, such as the [RSA](https://en.wikipedia.org/wiki/RSA_(algorithm) "RSA (algorithm)") algorithm. The integer factorization problem is in NP![{\displaystyle NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cbb96b0c7cdeba71278d234f3478d41964dfa1dd) and in co-NP![{\displaystyle co{\text{-}}NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9c3aec36706d41c2817026fd07e1bda1b251093d) (and even in UP and co-UP. If the problem is NP![{\displaystyle NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cbb96b0c7cdeba71278d234f3478d41964dfa1dd)-complete, the polynomial time hierarchy will collapse to its first level (i.e., NP![{\displaystyle NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cbb96b0c7cdeba71278d234f3478d41964dfa1dd) will equal co-NP![{\displaystyle co{\text{-}}NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9c3aec36706d41c2817026fd07e1bda1b251093d)). The best known algorithm for integer factorization is the [general number field sieve](https://en.wikipedia.org/wiki/General_number_field_sieve "General number field sieve"), which takes time O(e(6493)(log⁡n)3(log⁡log⁡n)23)! to factor an odd integer n![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b). However, the best known [quantum algorithm](https://en.wikipedia.org/wiki/Quantum_algorithm "Quantum algorithm") for this problem, [Shor's algorithm](https://en.wikipedia.org/wiki/Shor%27s_algorithm "Shor's algorithm"), does run in polynomial time. Unfortunately, this fact doesn't say much about where the problem lies with respect to non-quantum complexity classes.

#### Separations between other complexity classes
Many known complexity classes are suspected to be unequal, but this has not been proved. For instance P⊆NP⊆PP⊆PSPACE![{\displaystyle P\subseteq NP\subseteq PP\subseteq PSPACE}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f0617bae24485207f43afe3a906af897f71d201f), but it is possible that P=PSPACE![{\displaystyle P=PSPACE}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34004fd89f5ee33f15ee2128dd397d0054a0b316). If P![{\displaystyle P}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b4dc73bf40314945ff376bd363916a738548d40a) is not equal to NP![{\displaystyle NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cbb96b0c7cdeba71278d234f3478d41964dfa1dd), then P![{\displaystyle P}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b4dc73bf40314945ff376bd363916a738548d40a) is not equal to PSPACE![{\displaystyle PSPACE}](https://wikimedia.org/api/rest_v1/media/math/render/svg/39a7c3cf8fd055a634ae6bed85e7bf680c913ef6) either. Since there are many known complexity classes between P![{\displaystyle P}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b4dc73bf40314945ff376bd363916a738548d40a) and PSPACE![{\displaystyle PSPACE}](https://wikimedia.org/api/rest_v1/media/math/render/svg/39a7c3cf8fd055a634ae6bed85e7bf680c913ef6), such as RP![{\displaystyle RP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3e6ee2dec8276007eca18596d7bf5a7aeac64e7b), BPP![{\displaystyle BPP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b80e7fbd490e008c7b4c7b903d0f4e1059124401), PP![{\displaystyle PP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/811106f33a07c68d0569ab65da38994d96533099), BQP![{\displaystyle BQP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4911ab75d35efb67fb52e0908479b7ad94a322d1), MA![{\displaystyle MA}](https://wikimedia.org/api/rest_v1/media/math/render/svg/be6250feb34ae98d9b710a8b069d15811718a9c1), PH![{\displaystyle PH}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8aeedfd422ea2359bafabc7c3dd1d5beff4b5833), etc., it is possible that all these complexity classes collapse to one class. Proving that any of these classes are unequal would be a major breakthrough in complexity theory.

Along the same lines, co-NP![{\displaystyle co{\text{-}}NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9c3aec36706d41c2817026fd07e1bda1b251093d) is the class containing the [complement](https://en.wikipedia.org/wiki/Complement_(complexity) "Complement (complexity)") problems (i.e. problems with the _yes_/_no_ answers reversed) of NP![{\displaystyle NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cbb96b0c7cdeba71278d234f3478d41964dfa1dd) problems. It is believed that NP![{\displaystyle NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cbb96b0c7cdeba71278d234f3478d41964dfa1dd) is not equal to co-NP![{\displaystyle co{\text{-}}NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9c3aec36706d41c2817026fd07e1bda1b251093d); however, it has not yet been proven. It is clear that if these two complexity classes are not equal then P![{\displaystyle P}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b4dc73bf40314945ff376bd363916a738548d40a) is not equal to NP![{\displaystyle NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cbb96b0c7cdeba71278d234f3478d41964dfa1dd), since P=co-P![{\displaystyle P=co{\text{-}}P}](https://wikimedia.org/api/rest_v1/media/math/render/svg/03a838cc47bad6da7542476e48533edc5695a6bc). Thus if P=NP![{\displaystyle P=NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/04c4c7e4303f3c01c40c865c6a1a09c4632bb7e1) we would have co-P=co-NP![{\displaystyle co{\text{-}}P=co{\text{-}}NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2be5b0889f16c2e33584ac006c7577796f7af71d) whence NP=P=co-P=co-NP![{\displaystyle NP=P=co{\text{-}}P=co{\text{-}}NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5e9acdef3c4feeca7776bd8bb215707319a9f40b).

Similarly, it is not known if L![{\displaystyle L}](https://wikimedia.org/api/rest_v1/media/math/render/svg/103168b86f781fe6e9a4a87b8ea1cebe0ad4ede8) (the set of all problems that can be solved in logarithmic space) is strictly contained in P![{\displaystyle P}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b4dc73bf40314945ff376bd363916a738548d40a) or equal to P![{\displaystyle P}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b4dc73bf40314945ff376bd363916a738548d40a). Again, there are many complexity classes between the two, such as NL![{\displaystyle NL}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cac9c46b1af6aada8ab8f9799fddbba8fc451f90) and NC![{\displaystyle NC}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d01d5d050f3f5f55ffc77dc9a4bb8bb606d3abc0), and it is not known if they are distinct or equal classes.

It is suspected that P![{\displaystyle P}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b4dc73bf40314945ff376bd363916a738548d40a) and BPP![{\displaystyle BPP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b80e7fbd490e008c7b4c7b903d0f4e1059124401) are equal. However, it is currently open if BPP=NEXP![{\displaystyle BPP=NEXP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fc756f901663e753360ce8baabf116d5d97eb43d).

### Intractability
A problem that can theoretically be solved, but requires impractical and finite resources (e.g., time) to do so, is known as an _**intractable problem**_. Conversely, a problem that can be solved in practice is called a _**tractable problem**_, literally "a problem that can be handled". The term _[infeasible](https://en.wiktionary.org/wiki/infeasible "wikt:infeasible")_ (literally "cannot be done") is sometimes used interchangeably with _[intractable](https://en.wiktionary.org/wiki/intractable "wikt:intractable")_, though this risks confusion with a [feasible solution](https://en.wikipedia.org/wiki/Feasible_solution "Feasible solution") in [mathematical optimization](https://en.wikipedia.org/wiki/Mathematical_optimization "Mathematical optimization").
Tractable problems are frequently identified with problems that have polynomial-time solutions (P![{\displaystyle P}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b4dc73bf40314945ff376bd363916a738548d40a), PTIME![{\displaystyle PTIME}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6269acfa6002633c5c4eff68e66cbd8e9863a1e4)); this is known as the [Cobham–Edmonds thesis](https://en.wikipedia.org/wiki/Cobham%E2%80%93Edmonds_thesis "Cobham–Edmonds thesis"). Problems that are known to be intractable in this sense include those that are [EXPTIME](https://en.wikipedia.org/wiki/EXPTIME "EXPTIME")-hard. If NP![{\displaystyle NP}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cbb96b0c7cdeba71278d234f3478d41964dfa1dd) is not the same as P![{\displaystyle P}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b4dc73bf40314945ff376bd363916a738548d40a), then [NP-hard](https://en.wikipedia.org/wiki/NP-hard "NP-hard") problems are also intractable in this sense.

However, this identification is inexact: a polynomial-time solution with large degree or large leading coefficient grows quickly, and may be impractical for practical size problems; conversely, an exponential-time solution that grows slowly may be practical on realistic input, or a solution that takes a long time in the worst case may take a short time in most cases or the average case, and thus still be practical. Saying that a problem is not in P![{\displaystyle P}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b4dc73bf40314945ff376bd363916a738548d40a) does not imply that all large cases of the problem are hard or even that most of them are. For example, the decision problem in [Presburger arithmetic](https://en.wikipedia.org/wiki/Presburger_arithmetic "Presburger arithmetic") has been shown not to be in P![{\displaystyle P}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b4dc73bf40314945ff376bd363916a738548d40a), yet algorithms have been written that solve the problem in reasonable times in most cases. Similarly, algorithms can solve the NP-complete [knapsack problem](https://en.wikipedia.org/wiki/Knapsack_problem "Knapsack problem") over a wide range of sizes in less than quadratic time and [SAT solvers](https://en.wikipedia.org/wiki/SAT_solver "SAT solver") routinely handle large instances of the NP-complete [Boolean satisfiability problem](https://en.wikipedia.org/wiki/Boolean_satisfiability_problem "Boolean satisfiability problem").

To see why exponential-time algorithms are generally unusable in practice, consider a program that makes 2n![{\displaystyle 2^{n}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8226f30650ee4fe4e640c6d2798127e80e9c160d) operations before halting. For small n![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b), say 100, and assuming for the sake of example that the computer does 1012![{\displaystyle 10^{12}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9c90fc8874dafeb075a01985c74c1d31f51e7c3b) operations each second, the program would run for about 4×1010![{\displaystyle 4\times 10^{10}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2b5c76e9b40d690e1411fc8c799d63492a11678b) years, which is the same order of magnitude as the [age of the universe](https://en.wikipedia.org/wiki/Age_of_the_universe "Age of the universe"). Even with a much faster computer, the program would only be useful for very small instances and in that sense the intractability of a problem is somewhat independent of technological progress. However, an exponential-time algorithm that takes 1.0001n![{\displaystyle 1.0001^{n}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/586ed7ba1079e3822a1cb4252e24ea5d90092187) operations is practical until n![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) gets relatively large.

Similarly, a polynomial time algorithm is not always practical. If its running time is, say, n15![{\displaystyle n^{15}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2bc2e63ff8edb996fc3e92714dd8f6a1f3561f6d), it is unreasonable to consider it efficient and it is still useless except on small instances. Indeed, in practice even n3![{\displaystyle n^{3}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3e9d1a52e455a7a5272a345b2697e35f1579b681) or n2![{\displaystyle n^{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ac9810bbdafe4a6a8061338db0f74e25b7952620) algorithms are often impractical on realistic sizes of problems.

### Continuous complexity theory
Continuous complexity theory can refer to complexity theory of problems that involve continuous functions that are approximated by discretizations, as studied in [numerical analysis](https://en.wikipedia.org/wiki/Numerical_analysis "Numerical analysis"). One approach to complexity theory of numerical analysis is [information based complexity](https://en.wikipedia.org/wiki/Information_based_complexity "Information based complexity").

Continuous complexity theory can also refer to complexity theory of the use of [analog computation](https://en.wikipedia.org/wiki/Analog_computation "Analog computation"), which uses continuous [dynamical systems](https://en.wikipedia.org/wiki/Dynamical_system "Dynamical system") and [differential equations](https://en.wikipedia.org/wiki/Differential_equation "Differential equation"). [Control theory](https://en.wikipedia.org/wiki/Control_theory "Control theory") can be considered a form of computation and differential equations are used in the modelling of continuous-time and hybrid discrete-continuous-time systems.

## Declaration
In [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"), a **declaration** is a [language construct](https://en.wikipedia.org/wiki/Language_construct "Language construct") specifying [identifier](https://en.wikipedia.org/wiki/Identifier_(computer_programming) "Identifier (computer programming)") properties: it declares a word's (identifier's) meaning. Declarations are most commonly used for [functions](https://en.wikipedia.org/wiki/Subroutine "Subroutine"), [variables](https://en.wikipedia.org/wiki/Variable_(computer_science) "Variable (computer science)"), [constants](https://en.wikipedia.org/wiki/Constant_(computer_programming) "Constant (computer programming)"), and [classes](https://en.wikipedia.org/wiki/Class_(computer_programming) "Class (computer programming)"), but can also be used for other entities such as [enumerations](https://en.wikipedia.org/wiki/Enumerator_(computer_science) "Enumerator (computer science)") and type definitions. Beyond the name (the identifier itself) and the kind of entity (function, variable, etc.), declarations typically specify the [data type](https://en.wikipedia.org/wiki/Data_type "Data type") (for variables and constants), or the [type signature](https://en.wikipedia.org/wiki/Type_signature "Type signature") (for functions); types may also include dimensions, such as for [arrays](https://en.wikipedia.org/wiki/Array_data_structure "Array data structure"). A declaration is used to announce the existence of the entity to the [compiler](https://en.wikipedia.org/wiki/Compiler "Compiler"); this is important in those [strongly typed](https://en.wikipedia.org/wiki/Strongly_typed "Strongly typed") languages that require functions, variables, and constants, and their types to be specified with a declaration before use, and is used in [forward declaration](https://en.wikipedia.org/wiki/Forward_declaration "Forward declaration"). The term "declaration" is frequently contrasted with the term "definition", but meaning and usage varies significantly between languages; see below.

Declarations are particularly prominent in languages in the [ALGOL](https://en.wikipedia.org/wiki/ALGOL "ALGOL") tradition, including the [BCPL](https://en.wikipedia.org/wiki/BCPL "BCPL") family, most prominently [C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)") and [C++](https://en.wikipedia.org/wiki/C%2B%2B "C++"), and also [Pascal](https://en.wikipedia.org/wiki/Pascal_(programming_language) "Pascal (programming language)"). [Java](https://en.wikipedia.org/wiki/Java_(programming_language) "Java (programming language)") uses the term "declaration", though Java does not require separate declarations and definitions.

### Declaration vs. definition
One basic dichotomy is whether or not a declaration contains a definition: for example, whether a variable or constant declaration [specifies its value](https://en.wikipedia.org/wiki/Initialization_(programming) "Initialization (programming)"), or only its type; and similarly whether a declaration of a function specifies the body ([implementation](https://en.wikipedia.org/wiki/Implementation "Implementation")) of the function, or only its type signature. Not all languages make this distinction: in many languages, declarations always include a definition, and may be referred to as either "declarations" or "definitions", depending on the language. However, these concepts are distinguished in languages that require declaration before use (for which forward declarations are used), and in languages where interface and implementation are separated: the interface contains declarations, the implementation contains definitions.

In informal usage, a "declaration" refers only to a pure declaration (types only, no value or body), while a "definition" refers to a declaration that includes a value or body. However, in formal usage (in language specifications), "declaration" includes _both_ of these senses, with finer distinctions by language: in C and C++, a declaration of a function that does not include a body is called a [function prototype](https://en.wikipedia.org/wiki/Function_prototype "Function prototype"), while a declaration of a function that does include a body is called a "function definition". In Java declarations occur in two forms. For public methods they can be presented in interfaces as method signatures, which consist of the method names, input types and output type. A similar notation can be used in the definition of [abstract methods](https://en.wikipedia.org/wiki/Abstract_method "Abstract method"), which do not contain a definition. The enclosing class can be instantiated, rather a new derived class, which provides the definition of the method, would need to be created in order to create an [instance](https://en.wikipedia.org/wiki/Instance_(computer_science) "Instance (computer science)") of the class. Starting with [Java 8](https://en.wikipedia.org/wiki/Java_8 "Java 8"), the lambda expression was included in the language, which could be viewed as a function declaration.

### Declarations and definitions
In the C-family of programming languages, declarations are often collected into [header files](https://en.wikipedia.org/wiki/Header_file "Header file"), which are included in other source files that reference and use these declarations, but don't have access to the definition. The information in the header file provides the interface between code that uses the declaration and that which defines it, a form of [information hiding](https://en.wikipedia.org/wiki/Information_hiding "Information hiding"). A declaration is often used in order to access functions or variables defined in different source files, or in a [library](https://en.wikipedia.org/wiki/Library_(computing) "Library (computing)"). A mismatch between the definition type and the declaration type generates a compiler error.

For variables, definitions assign values to an area of memory that was reserved during the declaration phase. For functions, definitions supply the function body. While a variable or function may be declared many times, it is typically defined once (in [C++](https://en.wikipedia.org/wiki/C%2B%2B "C++"), this is known as the [One Definition Rule](https://en.wikipedia.org/wiki/One_Definition_Rule "One Definition Rule") or ODR).

Dynamic languages such as [JavaScript](https://en.wikipedia.org/wiki/JavaScript "JavaScript") or [Python](https://en.wikipedia.org/wiki/Python_(programming_language) "Python (programming language)") generally allow functions to be redefined, that is, [re-bound](https://en.wikipedia.org/wiki/Name_binding "Name binding"); a function is a variable much like any other, with a name and a value (the definition).

Here are some examples of declarations that are not definitions, in C:

```c
extern char example1;
extern int example2;
void example3(void);
```

Here are some examples of declarations that are definitions, again in C:

```c
char example1; /* Outside of a function definition it will be initialized to zero.  */
int example2 = 5;
void example3(void) { /* definition between braces */ }
```

## Identifier
In computer [programming languages](https://en.wikipedia.org/wiki/Programming_language "Programming language"), an **identifier** is a lexical token (also called a [symbol](https://en.wikipedia.org/wiki/Symbol "Symbol"), but not to be confused with the [symbol primitive data type](https://en.wikipedia.org/wiki/Symbol_(programming) "Symbol (programming)")) that names the language's entities. Some of the kinds of entities an identifier might denote include variables, data types, labels, subroutines, and modules.

### Lexical form
Which character sequences constitute identifiers depends on the [lexical grammar](https://en.wikipedia.org/wiki/Lexical_grammar "Lexical grammar") of the language. A common rule is [alphanumeric](https://en.wikipedia.org/wiki/Alphanumeric "Alphanumeric") sequences, with underscore also allowed (in some languages, _ is not allowed), and with the condition that it can not begin with a numerical digit (to simplify [lexing](https://en.wikipedia.org/wiki/Lexical_analysis "Lexical analysis") by avoiding confusing with [integer literals](https://en.wikipedia.org/wiki/Integer_literal "Integer literal")) – so `foo, foo1, foo_bar, _foo` are allowed, but `1foo` is not – this is the definition used in earlier versions of [C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)") and [C++](https://en.wikipedia.org/wiki/C%2B%2B "C++"), [Python](https://en.wikipedia.org/wiki/Python_(programming_language) "Python (programming language)"), and many other languages. Later versions of these languages, along with many other modern languages, support many more [Unicode](https://en.wikipedia.org/wiki/Unicode "Unicode") characters in an identifier. However, a common restriction is not to permit whitespace characters and language operators; this simplifies tokenization by making it [free-form](https://en.wikipedia.org/wiki/Free-form_language "Free-form language") and [context-free](https://en.wikipedia.org/wiki/Context-free_grammar "Context-free grammar"). For example, forbidding `+` in identifiers due to its use as a binary operation means that `a+b` and `a + b` can be tokenized the same, while if it were allowed, `a+b` would be an identifier, not an addition. Whitespace in identifier is particularly problematic, as if spaces are allowed in identifiers, then a clause such as `if rainy day then 1` is legal, with `rainy day` as an identifier, but tokenizing this requires the phrasal context of being in the condition of an if clause. Some languages do allow spaces in identifiers, however, such as [ALGOL 68](https://en.wikipedia.org/wiki/ALGOL_68 "ALGOL 68") and some ALGOL variants – for example, the following is a valid statement: `**real** half pi;` which could be entered as `.real. half pi;` (keywords are represented in boldface, concretely via [stropping](https://en.wikipedia.org/wiki/Stropping_(syntax) "Stropping (syntax)")). In ALGOL this was possible because keywords are syntactically differentiated, so there is no risk of collision or ambiguity, spaces are eliminated during the [line reconstruction](https://en.wikipedia.org/wiki/Line_reconstruction "Line reconstruction") phase, and the source was processed via [scannerless parsing](https://en.wikipedia.org/wiki/Scannerless_parsing "Scannerless parsing"), so lexing could be context-sensitive.

In most languages, some character sequences have the lexical form of an identifier but are known as [keywords](https://en.wikipedia.org/wiki/Keyword_(computer_programming) "Keyword (computer programming)") – for example, `if` is frequently a keyword for an if clause, but lexically is of the same form as `ig` or `foo` namely a sequence of letters. This overlap can be handled in various ways: these may be forbidden from being identifiers – which simplifies tokenization and parsing – in which case they are [reserved words](https://en.wikipedia.org/wiki/Reserved_words "Reserved words"); they may both be allowed but distinguished in other ways, such as via stropping; or keyword sequences may be allowed as identifiers and which sense is determined from context, which requires a context-sensitive lexer. Non-keywords may also be reserved words (forbidden as identifiers), particularly for [forward compatibility](https://en.wikipedia.org/wiki/Forward_compatibility "Forward compatibility"), in case a word may become a keyword in future. In a few languages, e.g., [PL/1](https://en.wikipedia.org/wiki/PL/1 "PL/1"), the distinction is not clear.

### Semantics
The scope, or accessibility within a program of an identifier can be either local or global. A global identifier is declared outside of functions and is available throughout the program. A local identifier is declared within a specific function and only available within that function.

For implementations of programming languages that are using a [compiler](https://en.wikipedia.org/wiki/Compiler "Compiler"), identifiers are often only [compile time](https://en.wikipedia.org/wiki/Compile_time "Compile time") entities. That is, at [runtime](https://en.wikipedia.org/wiki/Run_time_(program_lifecycle_phase) "Run time (program lifecycle phase)") the compiled program contains references to memory addresses and offsets rather than the textual identifier tokens (these memory addresses, or offsets, having been assigned by the compiler to each identifier).

In languages that support [reflection](https://en.wikipedia.org/wiki/Reflection_(computer_programming) "Reflection (computer programming)"), such as interactive evaluation of source code (using an interpreter or an incremental compiler), identifiers are also runtime entities, sometimes even as [first-class objects](https://en.wikipedia.org/wiki/First-class_object "First-class object") that can be freely manipulated and evaluated. In [Lisp](https://en.wikipedia.org/wiki/Lisp_(programming_language) "Lisp (programming language)"), these are called [symbols](https://en.wikipedia.org/wiki/Symbol_(Lisp) "Symbol (Lisp)").

Compilers and interpreters do not usually assign any semantic meaning to an identifier based on the actual character sequence used. However, there are exceptions. For example:

- In [Perl](https://en.wikipedia.org/wiki/Perl "Perl") a variable is indicated using a prefix called a [sigil](https://en.wikipedia.org/wiki/Sigil_(computer_programming) "Sigil (computer programming)"), which specifies aspects of how the variable is interpreted in [expressions](https://en.wikipedia.org/wiki/Expression_(programming) "Expression (programming)").
- In [Ruby](https://en.wikipedia.org/wiki/Ruby_programming_language "Ruby programming language") a variable is automatically considered [immutable](https://en.wikipedia.org/wiki/Immutable_object "Immutable object") if its identifier starts with a capital letter.
- In [Go](https://en.wikipedia.org/wiki/Go_(programming_language) "Go (programming language)"), the capitalization of the first letter of a variable's name determines its visibility (uppercase for public, lowercase for private).

In some languages such as Go, identifiers uniqueness is based on their spelling and their visibility.

In [HTML](https://en.wikipedia.org/wiki/HTML "HTML") an identifier is one of the possible [attributes](https://en.wikipedia.org/wiki/HTML_attribute "HTML attribute") of an [HTML element](https://en.wikipedia.org/wiki/HTML_element "HTML element"). It is unique within the document.

## Pool
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), a **pool** is a collection of resources that are kept in memory, ready to use, rather than the memory acquired on use or the memory released afterwards. In this context, _resources_ can refer to [system resources](https://en.wikipedia.org/wiki/System_resource "System resource") such as [file handles](https://en.wikipedia.org/wiki/File_handle "File handle"), which are external to a process, or internal resources such as [objects](https://en.wikipedia.org/wiki/Object_(computing) "Object (computing)"). A pool [client](https://en.wikipedia.org/wiki/Client_(computing) "Client (computing)") requests a resource from the pool and performs desired operations on the returned resource. When the client finishes its use of the resource, it is returned to the pool rather than released and lost.

The pooling of resources can offer a significant response-time boost in situations that have high cost associated with resource acquiring, high rate of the requests for resources, and a low overall count of simultaneously used resources. Pooling is also useful when the [latency](https://en.wikipedia.org/wiki/Latency_(engineering) "Latency (engineering)") is a concern, because a pool offers predictable times required to obtain resources since they have already been acquired. These benefits are mostly true for system resources that require a [system call](https://en.wikipedia.org/wiki/System_call "System call"), or remote resources that require a network communication, such as [database connections](https://en.wikipedia.org/wiki/Database_connection "Database connection"), [socket connections](https://en.wikipedia.org/wiki/Socket_connection "Socket connection"), [threads](https://en.wikipedia.org/wiki/Thread_(computing) "Thread (computing)"), and [memory allocation](https://en.wikipedia.org/wiki/Memory_allocation "Memory allocation"). Pooling is also useful for expensive-to-compute data, notably large graphic objects like [fonts](https://en.wikipedia.org/wiki/Font "Font") or [bitmaps](https://en.wikipedia.org/wiki/Bitmap "Bitmap"), acting essentially as a data [cache](https://en.wikipedia.org/wiki/Cache_(computing) "Cache (computing)") or a [memoization](https://en.wikipedia.org/wiki/Memoization "Memoization") technique.

Special cases of pools are [connection pools](https://en.wikipedia.org/wiki/Connection_pool "Connection pool"), [thread pools](https://en.wikipedia.org/wiki/Thread_pool "Thread pool"), and [memory pools](https://en.wikipedia.org/wiki/Memory_pool "Memory pool").

### Object pools
Pools can also be used for objects, in which context a _pool_ refers to a [design pattern](https://en.wikipedia.org/wiki/Design_pattern "Design pattern") for implementing pools in [object-oriented languages](https://en.wikipedia.org/wiki/Object-oriented_language "Object-oriented language"), such as in the [object pool pattern](https://en.wikipedia.org/wiki/Object_pool_pattern "Object pool pattern"). Objects themselves hold no external resources and only occupy memory, although an already created object avoids the memory allocation required on object creation. Object pools are useful when the cost of [object creation](https://en.wikipedia.org/wiki/Object_creation "Object creation") is high, but in certain situations this simple object pooling may not be efficient and could in fact decrease performance.

## Initialization
In [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"), **initialization** or **initialisation** is the [assignment](https://en.wikipedia.org/wiki/Assignment_(computer_science) "Assignment (computer science)") of an initial value for a [data object](https://en.wikipedia.org/wiki/Data_object "Data object") or variable. The manner in which initialization is performed depends on the [programming language](https://en.wikipedia.org/wiki/Programming_language "Programming language"), as well as the type, storage class, etc., of an object to be initialized. Programming constructs which perform initialization are typically called **initializers** and **initializer lists**. Initialization is distinct from (and preceded by) [declaration](https://en.wikipedia.org/wiki/Declaration_(computer_programming) "Declaration (computer programming)"), although the two can sometimes be conflated in practice. The complement of initialization is [finalization](https://en.wikipedia.org/wiki/Finalization "Finalization"), which is primarily used for objects, but not variables.

Initialization is done either by statically embedding the value at compile time, or else by assignment at [run time](https://en.wikipedia.org/wiki/Run_time_(program_lifecycle_phase) "Run time (program lifecycle phase)"). A section of code that performs such initialization is generally known as "initialization code" and may include other, one-time-only, functions such as opening files; in [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming"), initialization code may be part of a _[constructor](https://en.wikipedia.org/wiki/Constructor_(object-oriented_programming) "Constructor (object-oriented programming)")_ (class method) or an _initializer_ (instance method). Setting a memory location to [hexadecimal](https://en.wikipedia.org/wiki/Hexadecimal "Hexadecimal") zeroes is also sometimes known as "clearing" and is often performed by an [exclusive or](https://en.wikipedia.org/wiki/Exclusive_or "Exclusive or") instruction (both operands specifying the same variable), at [machine code](https://en.wikipedia.org/wiki/Machine_code "Machine code") level, since it requires no additional memory access.

### C family of languages
#### Initializer
In C/C99/C++, an **initializer** is an optional part of a [declarator](https://en.wikipedia.org/wiki/Declarator_(computing) "Declarator (computing)"). It consists of the '=' character followed by an [expression](https://en.wikipedia.org/wiki/Expression_(programming) "Expression (programming)") or a comma-separated list of expressions placed in curly brackets (braces). The latter list is sometimes called the "initializer list" or "initialization list" (although the term "initializer list" is formally reserved for initialization of class/struct members in C++; [see below](https://en.wikipedia.org/wiki/Initialization_(programming)#Initializer_list)). A declaration which creates a data object, instead of merely describing its existence, is commonly called a **definition**.

Many find it convenient to draw a distinction between the terms "declaration" and "definition", as in the commonly seen phrase "the distinction between a _declaration_ and _definition_...", implying that a declaration merely designates a data object (or function). In fact, according to the [C++ standard](https://en.wikipedia.org/wiki/C%2B%2B_standard "C++ standard"), a definition _is_ a declaration. Still, the usage "declarations and definitions", although formally incorrect, is common. Although all definitions are declarations, not all declarations are definitions.

C examples:
```c
int i = 0;
int k[4] = {0, 1};
char tx[3] = 'a';
char ty[2] = 'f';
struct Point {int x; int y;} p = { .y = 13, .x = 7 };
```

C++ examples:
```c++
int i2(0);
int j[2] = {rand(), k[0]};
MyClass* xox = new MyClass(0, "zaza");
point q = {0, i + 1};
```

#### Initializer list
In C++, a [constructor](https://en.wikipedia.org/wiki/Constructor_(object-oriented_programming) "Constructor (object-oriented programming)") of a class/struct can have an **initializer list** within the definition but prior to the constructor body. It is important to note that when you use an initialization list, the values are not assigned to the variable. They are initialized. In the below example, 0 is initialized into re and im. Example:

```c++
struct IntComplex {
  IntComplex() : re(0), im(0) {}

  int re;
  int im;
};
```

Here, the construct  `: re(0), im(0)` is the initializer list.

Sometimes the term "initializer list" is also used to refer to the list of expressions in the array or struct initializer.

[C++11](https://en.wikipedia.org/wiki/C%2B%2B11 "C++11") provides for a [more powerful concept of initializer lists](https://en.wikipedia.org/wiki/C%2B%2B11#Initializer_lists "C++11"), by means of a template, called `std::initializer_list`.

#### Default initialization
Data initialization may occur without explicit syntax in a program to do so. For example, if [static variables](https://en.wikipedia.org/wiki/Static_variable "Static variable") are declared without an initializer, then those of [primitive data types](https://en.wikipedia.org/wiki/Primitive_data_type "Primitive data type") are initialized with the value of zero of the corresponding type, while static objects of class type are initialized with their [default constructors](https://en.wikipedia.org/wiki/Default_constructor "Default constructor").

## Bit
The **bit** is the most basic [unit of information](https://en.wikipedia.org/wiki/Units_of_information "Units of information") in [computing](https://en.wikipedia.org/wiki/Computing "Computing") and digital [communication](https://en.wikipedia.org/wiki/Communication "Communication"). The name is a [portmanteau](https://en.wikipedia.org/wiki/Portmanteau "Portmanteau") of **binary digit**. The bit represents a [logical state](https://en.wikipedia.org/wiki/Truth_value "Truth value") with one of two possible [values](https://en.wikipedia.org/wiki/Value_(computer_science) "Value (computer science)"). These values are most commonly represented as either "1" or "0", but other representations such as _true_/_false_, _yes_/_no_, _on_/_off_, or _+_/_−_ are also widely used.

The relation between these values and the physical states of the underlying [storage](https://en.wikipedia.org/wiki/Data_storage_device "Data storage device") or [device](https://en.wikipedia.org/wiki/Computing_device "Computing device") is a matter of convention, and different assignments may be used even within the same device or [program](https://en.wikipedia.org/wiki/Computer_program "Computer program"). It may be physically implemented with a two-state device.

A contiguous group of binary digits is commonly called a _[bit string](https://en.wikipedia.org/wiki/Bit_string "Bit string")_, a bit vector, or a single-dimensional (or multi-dimensional) _[bit array](https://en.wikipedia.org/wiki/Bit_array "Bit array")_. A group of eight bits is called one _[byte](https://en.wikipedia.org/wiki/Byte "Byte")_, but historically the size of the byte is not strictly defined. Frequently, half, full, double and quadruple words consist of a number of bytes which is a low power of two. A string of four bits is usually a _[nibble](https://en.wikipedia.org/wiki/Nibble "Nibble")_.

In [information theory](https://en.wikipedia.org/wiki/Information_theory "Information theory"), one bit is the [information entropy](https://en.wikipedia.org/wiki/Information_entropy "Information entropy") of a random [binary](https://en.wikipedia.org/wiki/Binary_number "Binary number") variable that is 0 or 1 with equal probability, or the information that is gained when the value of such a variable becomes known. As a [unit of information](https://en.wikipedia.org/wiki/Unit_of_information "Unit of information"), the bit is also known as a _[shannon](https://en.wikipedia.org/wiki/Shannon_(unit) "Shannon (unit)")_, named after [Claude E. Shannon](https://en.wikipedia.org/wiki/Claude_E._Shannon "Claude E. Shannon").

The symbol for the binary digit is either "bit", per the [IEC 80000-13](https://en.wikipedia.org/wiki/IEC_80000-13 "IEC 80000-13"):2008 standard, or the lowercase character "b", per the [IEEE 1541-2002](https://en.wikipedia.org/wiki/IEEE_1541-2002 "IEEE 1541-2002") standard. Use of the latter may create confusion with the capital "B" which is the international standard symbol for the byte.

### Physical representation 
A bit can be stored by a digital device or other physical system that exists in either of two possible distinct [states](https://en.wikipedia.org/wiki/State_(computer_science) "State (computer science)"). These may be the two stable states of a [flip-flop](https://en.wikipedia.org/wiki/Flip-flop_(electronics) "Flip-flop (electronics)"), two positions of an [electrical switch](https://en.wikipedia.org/wiki/Switch "Switch"), two distinct [voltage](https://en.wikipedia.org/wiki/Voltage "Voltage") or [current](https://en.wikipedia.org/wiki/Electric_current "Electric current") levels allowed by a [circuit](https://en.wikipedia.org/wiki/Electrical_circuit "Electrical circuit"), two distinct levels of [light intensity](https://en.wikipedia.org/wiki/Irradiance "Irradiance"), two directions of [magnetization](https://en.wikipedia.org/wiki/Magnetism "Magnetism") or [polarization](https://en.wikipedia.org/wiki/Electrical_polarity "Electrical polarity"), the orientation of reversible double stranded [DNA](https://en.wikipedia.org/wiki/DNA "DNA"), etc.

Bits can be implemented in several forms. In most modern computing devices, a bit is usually represented by an [electrical](https://en.wikipedia.org/wiki/Electricity "Electricity") [voltage](https://en.wikipedia.org/wiki/Voltage "Voltage") or [current](https://en.wikipedia.org/wiki/Electric_current "Electric current") pulse, or by the electrical state of a flip-flop circuit.

For devices using [positive logic](https://en.wikipedia.org/wiki/Positive_logic "Positive logic"), a digit value of 1 (or a logical value of true) is represented by a more positive voltage relative to the representation of 0. Different logic families require different voltages, and variations are allowed to account for component aging and noise immunity. For example, in [transistor–transistor logic](https://en.wikipedia.org/wiki/Transistor%E2%80%93transistor_logic "Transistor–transistor logic") (TTL) and compatible circuits, digit values 0 and 1 at the output of a device are represented by no higher than 0.4 V and no lower than 2.6 V, respectively; while TTL inputs are specified to recognize 0.8 V or below as 0 and 2.2 V or above as 1.

#### Transmission and processing
Bits are transmitted one at a time in [serial transmission](https://en.wikipedia.org/wiki/Serial_transmission "Serial transmission"), and by a multiple number of bits in [parallel transmission](https://en.wikipedia.org/wiki/Parallel_transmission "Parallel transmission"). A [bitwise operation](https://en.wikipedia.org/wiki/Bitwise_operation "Bitwise operation") optionally processes bits one at a time. Data transfer rates are usually measured in decimal SI multiples of the unit [bit per second](https://en.wikipedia.org/wiki/Bit_per_second "Bit per second") (bit/s), such as kbit/s.

#### Storage
In the earliest non-electronic information processing devices, such as Jacquard's loom or Babbage's [Analytical Engine](https://en.wikipedia.org/wiki/Analytical_Engine "Analytical Engine"), a bit was often stored as the position of a mechanical lever or gear, or the presence or absence of a hole at a specific point of a [paper card](https://en.wikipedia.org/wiki/Punched_card "Punched card") or [tape](https://en.wikipedia.org/wiki/Punched_tape "Punched tape"). The first electrical devices for discrete logic (such as [elevator](https://en.wikipedia.org/wiki/Elevator "Elevator") and [traffic light](https://en.wikipedia.org/wiki/Traffic_light "Traffic light") control [circuits](https://en.wikipedia.org/wiki/Electronic_circuit "Electronic circuit"), [telephone switches](https://en.wikipedia.org/wiki/Telephone_switches "Telephone switches"), and Konrad Zuse's computer) represented bits as the states of [electrical relays](https://en.wikipedia.org/wiki/Electrical_relay "Electrical relay") which could be either "open" or "closed". When relays were replaced by [vacuum tubes](https://en.wikipedia.org/wiki/Vacuum_tube "Vacuum tube"), starting in the 1940s, computer builders experimented with a variety of storage methods, such as pressure pulses traveling down a [mercury delay line](https://en.wikipedia.org/wiki/Mercury_delay_line "Mercury delay line"), charges stored on the inside surface of a [cathode-ray tube](https://en.wikipedia.org/wiki/Cathode-ray_tube "Cathode-ray tube"), or opaque spots printed on [glass discs](https://en.wikipedia.org/wiki/Optical_disc "Optical disc") by [photolithographic](https://en.wikipedia.org/wiki/Photolithographic "Photolithographic") techniques.

In the 1950s and 1960s, these methods were largely supplanted by [magnetic storage](https://en.wikipedia.org/wiki/Magnetic_storage "Magnetic storage") devices such as [magnetic-core memory](https://en.wikipedia.org/wiki/Magnetic-core_memory "Magnetic-core memory"), [magnetic tapes](https://en.wikipedia.org/wiki/Magnetic_tape "Magnetic tape"), [drums](https://en.wikipedia.org/wiki/Magnetic_drum "Magnetic drum"), and [disks](https://en.wikipedia.org/wiki/Disk_storage "Disk storage"), where a bit was represented by the polarity of [magnetization](https://en.wikipedia.org/wiki/Magnetism "Magnetism") of a certain area of a [ferromagnetic](https://en.wikipedia.org/wiki/Ferromagnetic "Ferromagnetic") film, or by a change in polarity from one direction to the other. The same principle was later used in the [magnetic bubble memory](https://en.wikipedia.org/wiki/Magnetic_bubble_memory "Magnetic bubble memory") developed in the 1980s, and is still found in various [magnetic strip](https://en.wikipedia.org/wiki/Magnetic_strip "Magnetic strip") items such as [metro](https://en.wikipedia.org/wiki/Rapid_transit "Rapid transit") tickets and some [credit cards](https://en.wikipedia.org/wiki/Credit_card "Credit card").

In modern [semiconductor memory](https://en.wikipedia.org/wiki/Semiconductor_memory "Semiconductor memory"), such as [dynamic random-access memory](https://en.wikipedia.org/wiki/Dynamic_random-access_memory "Dynamic random-access memory"), the two values of a bit may be represented by two levels of [electric charge](https://en.wikipedia.org/wiki/Electric_charge "Electric charge") stored in a [capacitor](https://en.wikipedia.org/wiki/Capacitor "Capacitor"). In certain types of [programmable logic arrays](https://en.wikipedia.org/wiki/Programmable_logic_array "Programmable logic array") and [read-only memory](https://en.wikipedia.org/wiki/Read-only_memory "Read-only memory"), a bit may be represented by the presence or absence of a conducting path at a certain point of a circuit. In [optical discs](https://en.wikipedia.org/wiki/Optical_disc "Optical disc"), a bit is encoded as the presence or absence of a [microscopic](https://en.wikipedia.org/wiki/Microscopic "Microscopic") pit on a reflective surface. In one-dimensional [bar codes](https://en.wikipedia.org/wiki/Bar_code "Bar code"), bits are encoded as the thickness of alternating black and white lines.

### Unit and symbol
The bit is not defined in the [International System of Units](https://en.wikipedia.org/wiki/International_System_of_Units "International System of Units") (SI). However, the [International Electrotechnical Commission](https://en.wikipedia.org/wiki/International_Electrotechnical_Commission "International Electrotechnical Commission") issued standard [IEC 60027](https://en.wikipedia.org/wiki/IEC_60027 "IEC 60027"), which specifies that the symbol for binary digit should be 'bit', and this should be used in all multiples, such as 'kbit', for kilobit.[[11]](https://en.wikipedia.org/wiki/Bit#cite_note-NIST_2008-11) However, the lower-case letter 'b' is widely used as well and was recommended by the [IEEE 1541 Standard (2002)](https://en.wikipedia.org/wiki/IEEE_1541-2002 "IEEE 1541-2002"). In contrast, the upper case letter 'B' is the standard and customary symbol for byte.

#### Multiple bits
Multiple bits may be expressed and represented in several ways. For convenience of representing commonly reoccurring groups of bits in information technology, several [units of information](https://en.wikipedia.org/wiki/Units_of_information "Units of information") have traditionally been used. The most common is the unit [byte](https://en.wikipedia.org/wiki/Byte "Byte"), coined by [Werner Buchholz](https://en.wikipedia.org/wiki/Werner_Buchholz "Werner Buchholz") in June 1956, which historically was used to represent the group of bits used to encode a single [character](https://en.wikipedia.org/wiki/Character_(computing) "Character (computing)") of text (until [UTF-8](https://en.wikipedia.org/wiki/UTF-8 "UTF-8") multibyte encoding took over) in a computer and for this reason it was used as the basic [addressable](https://en.wikipedia.org/wiki/Address_space "Address space") element in many [computer architectures](https://en.wikipedia.org/wiki/Computer_architecture "Computer architecture"). The trend in hardware design converged on the most common implementation of using eight bits per byte, as it is widely used today. However, because of the ambiguity of relying on the underlying hardware design, the unit [octet](https://en.wikipedia.org/wiki/Octet_(computing) "Octet (computing)") was defined to explicitly denote a sequence of eight bits.

Computers usually manipulate bits in groups of a fixed size, conventionally named "[words](https://en.wikipedia.org/wiki/Word_(computer_architecture) "Word (computer architecture)")". Like the byte, the number of bits in a word also varies with the hardware design, and is typically between 8 and 80 bits, or even more in some specialized computers. In the early 21st century, retail personal or server computers have a word size of 32 or 64 bits.

The [International System of Units](https://en.wikipedia.org/wiki/International_System_of_Units "International System of Units") defines a series of decimal prefixes for multiples of standardized units which are commonly also used with the bit and the byte. The prefixes [kilo](https://en.wikipedia.org/wiki/Kilo- "Kilo-") (103) through [yotta](https://en.wikipedia.org/wiki/Yotta- "Yotta-") (1024) increment by multiples of one thousand, and the corresponding units are the [kilobit](https://en.wikipedia.org/wiki/Kilobit "Kilobit") (kbit) through the [yottabit](https://en.wikipedia.org/wiki/Yottabit "Yottabit") (Ybit).

### Information capacity and information compression
When the information capacity of a storage system or a communication channel is presented in _bits_ or _bits per second_, this often refers to binary digits, which is a [computer hardware](https://en.wikipedia.org/wiki/Computer_hardware "Computer hardware") capacity to store binary data (0 or 1, up or down, current or not, etc.). Information capacity of a storage system is only an upper bound to the quantity of information stored therein. If the two possible values of one bit of storage are not equally likely, that bit of storage contains less than one bit of information. If the value is completely predictable, then the reading of that value provides no information at all (zero entropic bits, because no resolution of uncertainty occurs and therefore no information is available). If a computer file that uses _n_ bits of storage contains only _m_ < _n_ bits of information, then that information can in principle be encoded in about _m_ bits, at least on the average. This principle is the basis of [data compression](https://en.wikipedia.org/wiki/Lossless_data_compression "Lossless data compression") technology. Using an analogy, the hardware binary digits refer to the amount of storage space available (like the number of buckets available to store things), and the information content the filling, which comes in different levels of granularity (fine or coarse, that is, compressed or uncompressed information). When the granularity is finer—when information is more compressed—the same bucket can hold more.

For example, it is estimated that the combined technological capacity of the world to store information provides 1,300 [exabytes](https://en.wikipedia.org/wiki/Exabyte "Exabyte") of hardware digits. However, when this storage space is filled and the corresponding content is optimally compressed, this only represents 295 exabytes of information. When optimally compressed, the resulting carrying capacity approaches [Shannon information](https://en.wikipedia.org/wiki/Shannon_information "Shannon information") or [information entropy](https://en.wikipedia.org/wiki/Information_entropy "Information entropy").

### Bit-based computing
Certain [bitwise](https://en.wikipedia.org/wiki/Bitwise_operation "Bitwise operation") computer [processor](https://en.wikipedia.org/wiki/Central_processing_unit "Central processing unit") instructions (such as _bit set_) operate at the level of manipulating bits rather than manipulating data interpreted as an aggregate of bits.

In the 1980s, when [bitmapped](https://en.wikipedia.org/wiki/Bitmap "Bitmap") computer displays became popular, some computers provided specialized [bit block transfer](https://en.wikipedia.org/wiki/Bitblt "Bitblt") instructions to set or copy the bits that corresponded to a given rectangular area on the screen.

In most computers and programming languages, when a bit within a group of bits, such as a [byte](https://en.wikipedia.org/wiki/Byte "Byte") or [word](https://en.wikipedia.org/wiki/Word "Word"), is referred to, it is usually specified by a number from 0 upwards corresponding to its position within the byte or word. However, 0 can refer to either the [most](https://en.wikipedia.org/wiki/Most_significant_bit "Most significant bit") or [least significant bit](https://en.wikipedia.org/wiki/Least_significant_bit "Least significant bit") depending on the context.

## Units of Information
In digital [computing](https://en.wikipedia.org/wiki/Computing "Computing") and [telecommunications](https://en.wikipedia.org/wiki/Telecommunication "Telecommunication"), a **unit of information** is the capacity of some standard [data](https://en.wikipedia.org/wiki/Data "Data") storage system or [communication channel](https://en.wikipedia.org/wiki/Communication_channel "Communication channel"), used to measure the capacities of other systems and channels. In [information theory](https://en.wikipedia.org/wiki/Information_theory "Information theory"), units of information are also used to measure [information](https://en.wikipedia.org/wiki/Information "Information") contained in messages and the [entropy](https://en.wikipedia.org/wiki/Entropy_(information_theory) "Entropy (information theory)") of random variables.

The most commonly used units of data storage capacity are the [bit](https://en.wikipedia.org/wiki/Bit "Bit"), the capacity of a system that has only two states, and the [byte](https://en.wikipedia.org/wiki/Byte "Byte") (or [octet](https://en.wikipedia.org/wiki/Octet_(computing) "Octet (computing)")), which is equivalent to eight bits. Multiples of these units can be formed from these with the [SI prefixes](https://en.wikipedia.org/wiki/Metric_prefix "Metric prefix") (power-of-ten prefixes) or the newer IEC [binary prefixes](https://en.wikipedia.org/wiki/Binary_prefix "Binary prefix") (power-of-two prefixes).

### Primary units
In 1928, [Ralph Hartley](https://en.wikipedia.org/wiki/Ralph_Hartley "Ralph Hartley") observed a fundamental storage principle, which was further formalized by [Claude Shannon](https://en.wikipedia.org/wiki/Claude_Shannon "Claude Shannon") in 1945: the information that can be stored in a system is proportional to the [logarithm](https://en.wikipedia.org/wiki/Logarithm "Logarithm") of _N_ possible states of that system, denoted log_b_ _N_. Changing the base of the logarithm from _b_ to a different number _c_ has the effect of multiplying the value of the logarithm by a fixed constant, namely log_c_ _N_ = (log_c_ _b_) log_b_ _N_. Therefore, the choice of the base _b_ determines the unit used to measure information. In particular, if _b_ is a [positive](https://en.wikipedia.org/wiki/Positive_and_negative_numbers "Positive and negative numbers") integer, then the unit is the amount of information that can be stored in a system with _b_ possible states.

When _b_ is 2, the unit is the [shannon](https://en.wikipedia.org/wiki/Shannon_(unit) "Shannon (unit)"), equal to the [information content](https://en.wikipedia.org/wiki/Information_content "Information content") of one "bit" (a portmanteau of binary digit). A system with 8 possible states, for example, can store up to log2 8 = 3 bits of information. Other units that have been named include:

Base _b_ = 3

the unit is called "[trit](https://en.wikipedia.org/wiki/Ternary_numeral_system "Ternary numeral system")", and is equal to log2 3 (≈ 1.585) bits.

Base _b_ = 10

the unit is called _[decimal](https://en.wikipedia.org/wiki/Decimal "Decimal") [digit](https://en.wikipedia.org/wiki/Numerical_digit "Numerical digit")_, _[hartley](https://en.wikipedia.org/wiki/Hartley_(unit) "Hartley (unit)")_, _ban_, _decit_, or _dit_, and is equal to log2 10 (≈ 3.322) bits.

Base _b_ = _e_, the [base of natural logarithms](https://en.wikipedia.org/wiki/Base_of_natural_logarithm "Base of natural logarithm")

the unit is called a _[nat](https://en.wikipedia.org/wiki/Nat_(unit) "Nat (unit)")_, _nit_, or _nepit_ (from [Neperian](https://en.wikipedia.org/wiki/John_Napier "John Napier")), and is worth log2 _e_ (≈ 1.443) bits.

The trit, ban, and nat are rarely used to measure storage capacity; but the nat, in particular, is often used in information theory, because natural logarithms are mathematically more convenient than logarithms in other bases.

### Units derived from bit
Several conventional names are used for collections or groups of bits.

#### Byte
Historically, a [byte](https://en.wikipedia.org/wiki/Byte "Byte") was the number of bits used to encode a [character](https://en.wikipedia.org/wiki/Character_(computing) "Character (computing)") of text in the computer, which depended on computer hardware architecture, but today it almost always means eight bits – that is, an [octet](https://en.wikipedia.org/wiki/Octet_(computing) "Octet (computing)"). An 8-bit byte can represent 256 (28) distinct values, such as non-negative integers from 0 to 255, or [signed](https://en.wikipedia.org/wiki/Two%27s_complement "Two's complement") integers from −128 to 127. The [IEEE 1541-2002](https://en.wikipedia.org/wiki/IEEE_1541-2002 "IEEE 1541-2002") standard specifies "B" (upper case) as the symbol for byte ([IEC 80000-13](https://en.wikipedia.org/wiki/IEC_80000-13 "IEC 80000-13") uses "o" for octet in French, but also allows "B" in English). Bytes, or multiples thereof, are almost always used to specify the sizes of computer files and the capacity of storage units. Most modern computers and peripheral devices are designed to manipulate data in whole bytes or groups of bytes, rather than individual bits.

#### Nibble
A group of four bits, or half a byte, is sometimes called a [nibble](https://en.wikipedia.org/wiki/Nibble "Nibble"), nybble or nyble. This unit is most often used in the context of [hexadecimal](https://en.wikipedia.org/wiki/Hexadecimal "Hexadecimal") number representations, since a nibble has the same number of possible values as one hexadecimal digit has.

#### Word, block, and page
Computers usually manipulate bits in groups of a fixed size, conventionally called _[words](https://en.wikipedia.org/wiki/Word_(computer_architecture) "Word (computer architecture)")_. The number of bits in a word is usually defined by the size of the [registers](https://en.wikipedia.org/wiki/Register_(computing) "Register (computing)") in the computer's [CPU](https://en.wikipedia.org/wiki/CPU "CPU"), or by the number of data bits that are fetched from its [main memory](https://en.wikipedia.org/wiki/Main_memory "Main memory") in a single operation. In the [IA-32](https://en.wikipedia.org/wiki/IA-32 "IA-32") architecture more commonly known as x86-32, a word is 32 bits, but other past and current architectures use words with 4, 8, 9, 12, 13, 16, 18, 20, 21, 22, 24, 25, 29, 30, 31, 32, 33, 35, 36, 38, 39, 40, 42, 44, 48, 50, 52, 54, 56, 60, 64, 72 bits or others.

Some [machine instructions](https://en.wikipedia.org/wiki/Machine_instruction "Machine instruction") and [computer number formats](https://en.wikipedia.org/wiki/Computer_number_format "Computer number format") use two words (a "double word" or "dword"), or four words (a "quad word" or "quad").

Computer [memory caches](https://en.wikipedia.org/wiki/Memory_cache "Memory cache") usually operate on _[blocks](https://en.wikipedia.org/wiki/Block_(data_storage) "Block (data storage)")_ of memory that consist of several consecutive words. These units are customarily called _cache blocks_, or, in [CPU caches](https://en.wikipedia.org/wiki/CPU_cache "CPU cache"), _cache lines_.

[Virtual memory](https://en.wikipedia.org/wiki/Virtual_memory "Virtual memory") systems partition the computer's [main storage](https://en.wikipedia.org/wiki/Main_storage "Main storage") into even larger units, traditionally called _[pages](https://en.wikipedia.org/wiki/Page_(computer_memory) "Page (computer memory)")_.

#### Systematic multiples
Terms for large quantities of bits can be formed using the standard range of SI prefixes for powers of 10, e.g., [kilo](https://en.wikipedia.org/wiki/Kilo- "Kilo-") = 103 = 1000 (as in [kilobit](https://en.wikipedia.org/wiki/Kilobit "Kilobit") or kbit), [mega](https://en.wikipedia.org/wiki/Mega- "Mega-") = 106 = 1000000 (as in [megabit](https://en.wikipedia.org/wiki/Megabit "Megabit") or Mbit) and [giga](https://en.wikipedia.org/wiki/Giga- "Giga-") = 109 = 1000000000 (as in [gigabit](https://en.wikipedia.org/wiki/Gigabit "Gigabit") or Gbit). These prefixes are more often used for multiples of bytes, as in [kilobyte](https://en.wikipedia.org/wiki/Kilobyte "Kilobyte") (1 kB = 8000 bit), [megabyte](https://en.wikipedia.org/wiki/Megabyte "Megabyte") (1 MB = 8000000bit), and [gigabyte](https://en.wikipedia.org/wiki/Gigabyte "Gigabyte") (1 GB = 8000000000bit).

However, for technical reasons, the capacities of computer memories and some storage units are often multiples of some large power of two, such as 228 = 268435456 bytes. To avoid such unwieldy numbers, people have often repurposed the SI prefixes to mean the nearest power of two, e.g., using the prefix _kilo_ for 210 = 1024, _mega_ for 220 = 1048576, and _giga_ for 230 = 1073741824, and so on. For example, a [random access memory](https://en.wikipedia.org/wiki/Random_access_memory "Random access memory") chip with a capacity of 228 bytes would be referred to as a 256-megabyte chip. The table below illustrates these differences.

|Symbol|Prefix|[SI](https://en.wikipedia.org/wiki/SI_prefix "SI prefix") meaning|[Binary](https://en.wikipedia.org/wiki/Binary_prefix "Binary prefix") use|Size difference|
|---|---|---|---|---|
|k|kilo|103   = 10001|210 = 10241|2.40%|
|M|mega|106   = 10002|220 = 10242|4.86%|
|G|giga|109   = 10003|230 = 10243|7.37%|
|T|tera|1012 = 10004|240 = 10244|9.95%|
|P|peta|1015 = 10005|250 = 10245|12.59%|
|E|exa|1018 = 10006|260 = 10246|15.29%|
|Z|zetta|1021 = 10007|270 = 10247|18.06%|
|Y|yotta|1024 = 10008|280 = 10248|20.89%|
|R|ronna|1027 = 10009|290 = 10249|23.79%|
|Q|quetta|1030 = 100010|2100 = 102410|26.77%|

In the past, uppercase _K_ has been used instead of lowercase _k_ to indicate 1024 instead of 1000. However, this usage was not consistently applied.

On the other hand, for external storage systems (such as [optical discs](https://en.wikipedia.org/wiki/Optical_disc "Optical disc")), the SI prefixes are commonly used with their decimal values (powers of 10). Many attempts have sought to resolve the confusion by providing alternative notations for power-of-two multiples. The [International Electrotechnical Commission](https://en.wikipedia.org/wiki/International_Electrotechnical_Commission "International Electrotechnical Commission") (IEC) issued a standard for this purpose by defining a series of [binary prefixes](https://en.wikipedia.org/wiki/Binary_prefixes "Binary prefixes") that use 1024 instead of 1000 as the main radix:

|Symbol|Prefix| |   |   |
|---|---|---|---|---|
|Ki|kibi, _binary kilo_|1 [kibibyte](https://en.wikipedia.org/wiki/Kibibyte "Kibibyte") (KiB)|210 bytes|1024 B|
|Mi|mebi, _binary mega_|1 [mebibyte](https://en.wikipedia.org/wiki/Mebibyte "Mebibyte") (MiB)|220 bytes|1024 KiB|
|Gi|gibi, _binary giga_|1 [gibibyte](https://en.wikipedia.org/wiki/Gibibyte "Gibibyte") (GiB)|230 bytes|1024 MiB|
|Ti|tebi, _binary tera_|1 [tebibyte](https://en.wikipedia.org/wiki/Tebibyte "Tebibyte") (TiB)|240 bytes|1024 GiB|
|Pi|pebi, _binary peta_|1 [pebibyte](https://en.wikipedia.org/wiki/Pebibyte "Pebibyte") (PiB)|250 bytes|1024 TiB|
|Ei|exbi, _binary exa_ |1 [exbibyte](https://en.wikipedia.org/wiki/Exbibyte "Exbibyte") (EiB)|260 bytes|1024 PiB|
|Zi|zebi, _binary zetta_|1 [zebibyte](https://en.wikipedia.org/wiki/Zebibyte "Zebibyte") (ZiB)|270 bytes|1024 EiB|
|Yi|yobi, _binary yotta_|1 [yobibyte](https://en.wikipedia.org/wiki/Yobibyte "Yobibyte") (YiB)|280 bytes|1024 ZiB|
 
The [JEDEC memory standard](https://en.wikipedia.org/wiki/JEDEC_memory_standards "JEDEC memory standards") JESD88F notes that the definitions of kilo (K), giga (G), and mega (M) based on powers of two are included only to reflect common usage, but are otherwise deprecated.

## Uniform Resource Identifier (URI)
A **Uniform Resource Identifier** (**URI**), formerly **Universal Resource Identifier**, is a unique sequence of characters that identifies an abstract or physical resource, such as resources on a webpage, mail address, phone number, books, real-world objects such as people and places, concepts. URIs are used to identify anything described using the [Resource Description Framework](https://en.wikipedia.org/wiki/Resource_Description_Framework "Resource Description Framework") (RDF), for example, concepts that are part of an [ontology](https://en.wikipedia.org/wiki/Ontology_(information_science) "Ontology (information science)") defined using the [Web Ontology Language](https://en.wikipedia.org/wiki/Web_Ontology_Language "Web Ontology Language") (OWL), and people who are described using the [Friend of a Friend vocabulary](https://en.wikipedia.org/wiki/FOAF_(ontology) "FOAF (ontology)") would each have an individual URI.

URIs which provide a means of locating and [retrieving](https://en.wikipedia.org/wiki/Information_retrieval "Information retrieval") information resources on a network (either on the Internet or on another private network, such as a computer filesystem or an [Intranet](https://en.wikipedia.org/wiki/Intranet "Intranet")) are [Uniform Resource Locators](https://en.wikipedia.org/wiki/Uniform_Resource_Locator "Uniform Resource Locator") (**URLs**). Therefore, URLs are a subset of URIs, ie. every URL is a URI (and not necessarily the other way around). Other URIs provide only a unique name, without a means of locating or retrieving the resource or information about it; these are [Uniform Resource Names](https://en.wikipedia.org/wiki/Uniform_Resource_Name "Uniform Resource Name") (URNs). The web technologies that use URIs are not limited to [web browsers](https://en.wikipedia.org/wiki/Web_browser "Web browser").

### Design
#### URLs and URNs
A [Uniform Resource Name](https://en.wikipedia.org/wiki/Uniform_Resource_Name "Uniform Resource Name") (URN) is a URI that identifies a resource by name in a particular namespace. A URN may be used to talk about a resource without implying its location or how to access it. For example, in the [International Standard Book Number](https://en.wikipedia.org/wiki/International_Standard_Book_Number "International Standard Book Number") (ISBN) system, _ISBN 0-486-27557-4_ identifies a specific edition of the [William Shakespeare](https://en.wikipedia.org/wiki/William_Shakespeare "William Shakespeare") play _[Romeo and Juliet](https://en.wikipedia.org/wiki/Romeo_and_Juliet "Romeo and Juliet")_. The URN for that edition would be _urn:isbn:0-486-27557-4_. However, it gives no information as to where to find a copy of that book.

A [Uniform Resource Locator](https://en.wikipedia.org/wiki/Uniform_Resource_Locator "Uniform Resource Locator") (URL) is a URI that specifies the means of acting upon or obtaining the representation of a resource, i.e. specifying both its primary access mechanism and network location. For example, the URL `http://example.org/wiki/Main_Page` refers to a resource identified as `/wiki/Main_Page`, whose representation is obtainable via the [Hypertext Transfer Protocol](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol "Hypertext Transfer Protocol") (_http:_) from a network host whose [domain name](https://en.wikipedia.org/wiki/Domain_name "Domain name") is `example.org`. (In this case, HTTP usually implies it to be in the form of [HTML](https://en.wikipedia.org/wiki/HTML "HTML") and related code. In practice, that is not necessarily the case, as HTTP allows specifying arbitrary formats in its header.)

A URN is analogous to a person's name, while a URL is analogous to their street address. In other words, a URN identifies an item and a URL provides a method for finding it.

Technical publications, especially standards produced by the IETF and by the W3C, normally reflect a view outlined in a [W3C Recommendation](https://en.wikipedia.org/wiki/W3C_Recommendation "W3C Recommendation") of 30 July 2001, which acknowledges the precedence of the term URI rather than endorsing any formal subdivision into URL and URN.

> URL is a useful but informal concept: a URL is a type of URI that identifies a resource via a representation of its primary access mechanism (e.g., its network "location"), rather than by some other attributes it may have.

As such, a URL is simply a URI that happens to point to a resource over a network. However, in non-technical contexts and in software for the World Wide Web, the term "URL" remains widely used. Additionally, the term "web address" (which has no formal definition) often occurs in non-technical publications as a synonym for a URI that uses the _http_ or _https_ schemes. Such assumptions can lead to confusion, for example, in the case of XML namespaces that have a [visual similarity to resolvable URIs](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier#Relation_to_XML_namespaces).

Specifications produced by the [WHATWG](https://en.wikipedia.org/wiki/WHATWG "WHATWG") prefer _URL_ over _URI_, and so newer HTML5 APIs use _URL_ over _URI_.

> Standardize on the term URL. URI and IRI are just confusing. In practice a single algorithm is used for both so keeping them distinct is not helping anyone. URL also easily wins the search result popularity contest.

While most URI schemes were originally designed to be used with a particular [protocol](https://en.wikipedia.org/wiki/Protocol_(computing) "Protocol (computing)"), and often have the same name, they are semantically different from protocols. For example, the scheme _http_ is generally used for interacting with [web resources](https://en.wikipedia.org/wiki/Web_resource "Web resource") using HTTP, but the scheme _[file](https://en.wikipedia.org/wiki/File_URI_scheme "File URI scheme")_ has no protocol.

#### Syntax
A URI has a scheme that refers to a specification for assigning identifiers within that scheme. As such, the URI syntax is a federated and extensible naming system wherein each scheme's specification may further restrict the syntax and semantics of identifiers using that scheme. The URI generic syntax is a superset of the syntax of all URI schemes. It was first defined in [RFC](https://en.wikipedia.org/wiki/RFC_(identifier) "RFC (identifier)") [2396](https://datatracker.ietf.org/doc/html/rfc2396), published in August 1998, and finalized in [RFC](https://en.wikipedia.org/wiki/RFC_(identifier) "RFC (identifier)") [3986](https://datatracker.ietf.org/doc/html/rfc3986), published in January 2005.

A URI is composed from an allowed set of [ASCII](https://en.wikipedia.org/wiki/ASCII "ASCII") characters consisting of [reserved characters](https://en.wikipedia.org/wiki/Filename "Filename") (gen-delims: `:`, `/`, `?`, `#`, `[`, `]`, and `@`; sub-delims: `!`, `$`, `&`, `'`, `(`, `)`, `*`, `+`, `,`, `;`, and `=`), unreserved characters ([uppercase and lowercase letters](https://en.wikipedia.org/wiki/Latin-script_alphabet "Latin-script alphabet"), [decimal digits](https://en.wikipedia.org/wiki/Arabic_numerals "Arabic numerals"), `-`, `.`, `_`, and `~`), and the character `%`. Syntax components and subcomponents are separated by _delimiters_ from the reserved characters (only from generic reserved characters for components) and define _identifying data_ represented as unreserved characters, reserved characters that do not act as delimiters in the component and subcomponent respectively, and [percent-encodings](https://en.wikipedia.org/wiki/Percent-encoding "Percent-encoding") when the corresponding character is outside the allowed set or is being used as a delimiter of, or within, the component. A percent-encoding of an identifying data [octet](https://en.wikipedia.org/wiki/Octet_(computing) "Octet (computing)") is a sequence of three characters, consisting of the character `%` followed by the two hexadecimal digits representing that octet's numeric value.

The URI generic syntax consists of five _components_ organized hierarchically in order of decreasing significance from left to right:
URI = scheme ":" ["//" authority] path ["?" query] ["#" fragment]

A component is _undefined_ if it has an associated delimiter and the delimiter does not appear in the URI; the scheme and path components are always defined. A component is _empty_ if it has no characters; the scheme component is always non-empty.

The authority component consists of _subcomponents_:

authority = [userinfo "@"] host [":" port]

This is represented in a [syntax diagram](https://en.wikipedia.org/wiki/Syntax_diagram "Syntax diagram") as:

[![URI syntax diagram](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d6/URI_syntax_diagram.svg/1068px-URI_syntax_diagram.svg.png)](https://en.wikipedia.org/wiki/File:URI_syntax_diagram.svg "URI syntax diagram")

The URI comprises:

- A non-empty **scheme** component followed by a colon (`:`), consisting of a sequence of characters beginning with a letter and followed by any combination of letters, digits, plus (`+`), period (`.`), or hyphen (`-`). Although schemes are case-insensitive, the canonical form is lowercase and documents that specify schemes must do so with lowercase letters. Examples of popular schemes include `[http] "Hypertext Transfer Protocol")`, `[https] HTTP Secure")`, `[ftp] "File Transfer Protocol")`, `[mailto] "Mailto")`, `[file] "File URI scheme")`, `[data] "Data URI scheme")` and `[irc] ("Internet Relay Chat")`. URI schemes should be registered with the [Internet Assigned Numbers Authority (IANA)](https://en.wikipedia.org/wiki/Internet_Assigned_Numbers_Authority "Internet Assigned Numbers Authority"), although non-registered schemes are used in practice.
- An optional **authority** component preceded by two slashes (`//`), comprising:
    - An optional **userinfo** subcomponent followed by an at symbol (`@`), that may consist of a [user name](https://en.wikipedia.org/wiki/User_(computing) "User (computing)") and an optional [password](https://en.wikipedia.org/wiki/Password "Password") preceded by a colon (`:`). Use of the format `username:password` in the userinfo subcomponent is deprecated for security reasons. Applications should not render as clear text any data after the first colon (`:`) found within a userinfo subcomponent unless the data after the colon is the empty string (indicating no password).
    - A **host** subcomponent, consisting of either a registered name (including but not limited to a [hostname](https://en.wikipedia.org/wiki/Hostname "Hostname")) or an [IP address](https://en.wikipedia.org/wiki/IP_address "IP address"). [IPv4](https://en.wikipedia.org/wiki/IPv4 "IPv4") addresses must be in [dot-decimal notation](https://en.wikipedia.org/wiki/Dot-decimal_notation "Dot-decimal notation"), and [IPv6](https://en.wikipedia.org/wiki/IPv6 "IPv6") addresses must be enclosed in brackets (`[]`).
    - An optional **port** subcomponent preceded by a colon (`:`), consisting of decimal digits.
- A **path** component, consisting of a sequence of path segments separated by a slash (`/`). A path is always defined for a URI, though the defined path may be empty (zero length). A segment may also be empty, resulting in two consecutive slashes (`//`) in the path component. A path component may resemble or map exactly to a [file system path](https://en.wikipedia.org/wiki/Path_(computing) "Path (computing)") but does not always imply a relation to one. If an authority component is defined, then the path component must either be empty or begin with a slash (`/`). If an authority component is undefined, then the path cannot begin with an empty segment—that is, with two slashes (`//`)—since the following characters would be interpreted as an authority component.

By convention, in **http** and **https** URIs, the last part of a _path_ is named **pathinfo** and it is optional. It is composed by zero or more path segments that do not refer to an existing physical resource name (e.g. a file, an internal module program or an executable program) but to a logical part (e.g. a command or a qualifier part) that has to be passed separately to the first part of the path that identifies an executable module or program managed by a [web server](https://en.wikipedia.org/wiki/Web_server "Web server"); this is often used to select dynamic content (a document, etc.) or to tailor it as requested (see also: [CGI](https://en.wikipedia.org/wiki/Common_Gateway_Interface "Common Gateway Interface") and PATH_INFO, etc.).

Example:

URI: `"http://www.example.com/questions/3456/my-document"`

where: `"/questions"` is the first part of the _path_ (an executable module or program) and `"/3456/my-document"` is the second part of the _path_ named _pathinfo_, which is passed to the executable module or program named `"/questions"` to select the requested document.

An **http** or **https** URI containing a _pathinfo_ part without a [query](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier#query) part may also be referred to as a '[clean URL](https://en.wikipedia.org/wiki/Clean_URL "Clean URL"),' whose last part may be a '[slug](https://en.wikipedia.org/wiki/Clean_URL#Slug "Clean URL").'

| Query delimiter | Example                   |
| --------------- | ------------------------- |
| Ampersand (`&`) | `key1=value1&key2=value2` |
| Semicolon (`;`) | `key1=value1;key2=value2` |

- An optional **query** component preceded by a question mark (`?`), consisting of a [query string](https://en.wikipedia.org/wiki/Query_string "Query string") of non-hierarchical data. Its syntax is not well defined, but by convention is most often a sequence of [attribute–value pairs](https://en.wikipedia.org/wiki/Attribute%E2%80%93value_pair "Attribute–value pair") separated by a [delimiter](https://en.wikipedia.org/wiki/Delimiter "Delimiter").
- An optional **fragment** component preceded by a [hash](https://en.wikipedia.org/wiki/Number_sign "Number sign") (`#`). The fragment contains a [fragment identifier](https://en.wikipedia.org/wiki/Fragment_identifier "Fragment identifier") providing direction to a secondary resource, such as a section heading in an article identified by the remainder of the URI. When the primary resource is an [HTML](https://en.wikipedia.org/wiki/HTML "HTML") document, the fragment is often an [`id` attribute](https://en.wikipedia.org/wiki/HTML#Attributes "HTML") of a specific element, and web browsers will scroll this element into view.

The scheme- or implementation-specific reserved character `+` may be used in the scheme, userinfo, host, path, query, and fragment, and the scheme- or implementation-specific reserved characters `!`, `$`, `&`, `'`, `(`, `)`, `*`, `,`, `;`, and `=` may be used in the userinfo, host, path, query, and fragment. Additionally, the generic reserved character `:` may be used in the userinfo, path, query and fragment, the generic reserved characters `@` and `/` may be used in the path, query and fragment, and the generic reserved character `?` may be used in the query and fragment.

#### Example URIs
The following figure displays example URIs and their component parts.

          userinfo       host      port
          ┌──┴───┐ ┌──────┴──────┐ ┌┴─┐
  `https://john.doe@www.example.com:1234/forum/questions/?tag=networking&order=newest#top`
  └─┬─┘   └─────────────┬─────────────┘└───────┬───────┘ └────────────┬────────────┘ └┬┘
  scheme            authority                path                   query          fragment
          userinfo       host      port
          ┌──┴───┐ ┌──────┴──────┐ ┌┴─┐
  `https://john.doe@www.example.com:1234/forum/questions/?tag=networking&order=newest#:~:text=whatever`
  └─┬─┘   └─────────────┬─────────────┘└───────┬───────┘ └────────────┬────────────┘ └───────┬───────┘
  scheme            authority                path                   query                 fragment

  `ldap://[2001:db8::7]/c=GB?objectClass?one`
  └┬─┘   └─────┬─────┘└─┬─┘ └──────┬──────┘
  scheme   authority   path      query

  `mailto:John.Doe@example.com`
  └─┬──┘ └────┬─────────────┘
  scheme     path

  `news:comp.infosystems.www.servers.unix`
  └┬─┘ └─────────────┬─────────────────┘
  scheme            path

  tel:+1-816-555-1212
  └┬┘ └──────┬──────┘
  scheme    path

  `telnet://192.0.2.16:80/`
  └─┬──┘   └─────┬─────┘│
  scheme     authority  path

  `urn:oasis:names:specification:docbook:dtd:xml:4.1.2`
  └┬┘ └──────────────────────┬──────────────────────┘
  scheme                    path

DOIs ([digital object identifiers](https://en.wikipedia.org/wiki/Digital_object_identifier "Digital object identifier")) fit within the [Handle System](https://en.wikipedia.org/wiki/Handle_System "Handle System") and fit within the URI system, [as facilitated by appropriate syntax](https://en.wikipedia.org/wiki/Handle_System#DOIs-Handles-URIs "Handle System").

#### URI references
A _URI reference_ is either a URI or a _relative reference_ when it does not begin with a scheme component followed by a colon (`:`). A path segment that contains a colon character (e.g., `foo:bar`) cannot be used as the first path segment of a relative reference if its path component does not begin with a slash (`/`), as it would be mistaken for a scheme component. Such a path segment must be preceded by a dot path segment (e.g., `./foo:bar`).

Web document [markup languages](https://en.wikipedia.org/wiki/Markup_language "Markup language") frequently use URI references to point to other resources, such as external documents or specific portions of the same logical document:

- in [HTML](https://en.wikipedia.org/wiki/HTML "HTML"), the value of the `src` attribute of the `img` element provides a URI reference, as does the value of the `href` attribute of the `a` or `link` element;
- in [XML](https://en.wikipedia.org/wiki/XML "XML"), the [system identifier](https://en.wikipedia.org/wiki/System_identifier "System identifier") appearing after the `SYSTEM` keyword in a [DTD](https://en.wikipedia.org/wiki/Document_Type_Definition "Document Type Definition") is a fragmentless URI reference;
- in [XSLT](https://en.wikipedia.org/wiki/XSLT "XSLT"), the value of the `href` attribute of the `xsl:import` element/instruction is a URI reference; likewise the first argument to the `document()` function.

`https://example.com/path/resource.txt#fragment`
`//example.com/path/resource.txt`
`/path/resource.txt`
`path/resource.txt`
`../resource.txt`
`./resource.txt`
`resource.txt`
`#fragment`

#### Resolution
_Resolving_ a URI reference against a _base URI_ results in a _target URI_. This implies that the base URI exists and is an _absolute URI_ (a URI with no fragment component). The base URI can be obtained, in order of precedence, from:

- the reference URI itself if it is a URI;
- the content of the representation;
- the entity encapsulating the representation;
- the URI used for the actual retrieval of the representation;
- the context of the application.

Within a representation with a well defined base URI of

`http://a/b/c/d;p?q`

a relative reference is resolved to its target URI as follows:

`"g:h"     -> "g:h"`
`"g"       -> "http://a/b/c/g"`
`"./g"     -> "http://a/b/c/g"`
`"g/"      -> "http://a/b/c/g/"`
`"/g"      -> "http://a/g"`
`"//g"     -> "http://g"`
`"?y"      -> "http://a/b/c/d;p?y"`
`"g?y"     -> "http://a/b/c/g?y"`
`"#s"      -> "http://a/b/c/d;p?q#s"`
`"g#s"     -> "http://a/b/c/g#s"`
`"g?y#s"   -> "http://a/b/c/g?y#s"`
`";x"      -> "http://a/b/c/;x"`
`"g;x"     -> "http://a/b/c/g;x"`
`"g;x?y#s" -> "http://a/b/c/g;x?y#s"`
`""        -> "http://a/b/c/d;p?q"`
`"."       -> "http://a/b/c/"`
`"./"      -> "http://a/b/c/"`
`".."      -> "http://a/b/"`
`"../"     -> "http://a/b/"`
`"../g"    -> "http://a/b/g"`
`"../.."   -> "http://a/"`
`"../../"  -> "http://a/"`
`"../../g" -> "http://a/g"`

#### URL munging
URL munging is a technique by which a [command](https://en.wikipedia.org/wiki/Command_(computing) "Command (computing)") is appended to a URL, usually at the end, after a "?" [token](https://en.wikipedia.org/wiki/Lexical_analysis#Token "Lexical analysis"). It is commonly used in [WebDAV](https://en.wikipedia.org/wiki/WebDAV "WebDAV") as a mechanism of adding functionality to [HTTP](https://en.wikipedia.org/wiki/HTTP "HTTP"). In a versioning system, for example, to add a "checkout" command to a URL, it is written as `http://editing.com/resource/file.php?command=checkout`. It has the advantage of both being easy for [CGI parsers](https://en.wikipedia.org/wiki/Common_Gateway_Interface "Common Gateway Interface") and also acts as an intermediary between HTTP and underlying resource, in this case.

#### Relation to XML namespaces
In [XML](https://en.wikipedia.org/wiki/XML "XML"), a [namespace](https://en.wikipedia.org/wiki/XML_namespace "XML namespace") is an abstract domain to which a collection of element and attribute names can be assigned. The namespace name is a character string which must adhere to the generic URI syntax. However, the name is generally not considered to be a URI, because the URI specification bases the decision not only on lexical components, but also on their intended use. A namespace name does not necessarily imply any of the semantics of URI schemes; for example, a namespace name beginning with _http:_ may have no connotation to the use of the [HTTP](https://en.wikipedia.org/wiki/HTTP "HTTP").

Originally, the namespace name could match the syntax of any non-empty URI reference, but the use of relative URI references was deprecated by the W3C. A separate W3C specification for namespaces in XML 1.1 permits [Internationalized Resource Identifier](https://en.wikipedia.org/wiki/Internationalized_Resource_Identifier "Internationalized Resource Identifier") (IRI) references to serve as the basis for namespace names in addition to URI references.

## Internationalized Resource Identifier (IRI)
The **Internationalized Resource Identifier** (**IRI**) is an [internet protocol standard](https://en.wikipedia.org/wiki/Internet_Standard "Internet Standard") which builds on the [Uniform Resource Identifier](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier "Uniform Resource Identifier") (URI) protocol by greatly expanding the set of permitted characters. It was defined by the [Internet Engineering Task Force](https://en.wikipedia.org/wiki/Internet_Engineering_Task_Force "Internet Engineering Task Force") (IETF) in 2005 in RFC 3987. While URIs are limited to a subset of the [US-ASCII](https://en.wikipedia.org/wiki/US-ASCII "US-ASCII") character set (characters outside that set must be mapped to octets according to some unspecified character encoding, then [percent-encoded](https://en.wikipedia.org/wiki/Percent-encoding "Percent-encoding")), IRIs may additionally contain most characters from the [Universal Character Set](https://en.wikipedia.org/wiki/Universal_Character_Set "Universal Character Set") (Unicode/[ISO 10646](https://en.wikipedia.org/wiki/ISO_10646 "ISO 10646")), including [Chinese](https://en.wikipedia.org/wiki/Chinese_characters "Chinese characters"), [Japanese](https://en.wikipedia.org/wiki/Japanese_writing_system "Japanese writing system"), [Korean](https://en.wikipedia.org/wiki/Korean_alphabet "Korean alphabet"), and [Cyrillic](https://en.wikipedia.org/wiki/Cyrillic_script "Cyrillic script") characters.

### Syntax
IRIs extend URIs by using the [Universal Character Set](https://en.wikipedia.org/wiki/Universal_Character_Set "Universal Character Set"), where URIs were limited to [ASCII](https://en.wikipedia.org/wiki/ASCII "ASCII"), with far fewer characters. IRIs may be represented by a sequence of octets but by definition are defined as a sequence of characters, because IRIs may be spoken or written by hand.

### Compatibility
IRIs are mapped to URIs to retain backwards-compatibility with systems that do not support the new format.

For applications and protocols that do not allow direct consumption of IRIs, the IRI should first be converted to Unicode using [canonical composition normalization (NFC)](https://en.wikipedia.org/wiki/Unicode_equivalence "Unicode equivalence"), if not already in Unicode format.

All non-ASCII code points in the IRI should next be encoded as [UTF-8](https://en.wikipedia.org/wiki/UTF-8 "UTF-8"), and the resulting bytes [percent-encoded](https://en.wikipedia.org/wiki/Percent-encoding "Percent-encoding"), to produce a valid URI.

Example: The IRI [https://en.wiktionary.org/wiki/Ῥόδος](https://en.wiktionary.org/wiki/%E1%BF%AC%CF%8C%CE%B4%CE%BF%CF%82) becomes the URI [https://en.wiktionary.org/wiki/%E1%BF%AC%CF%8C%CE%B4%CE%BF%CF%82](https://en.wiktionary.org/wiki/%E1%BF%AC%CF%8C%CE%B4%CE%BF%CF%82)

ASCII code points that are invalid URI characters _may_ be encoded the same way, depending on implementation.

This conversion is easily reversible; by definition, converting an IRI to an URI and back again will yield an IRI that is semantically equivalent to the original IRI, even though it may differ in exact representation.

Some protocols may impose further transformations; e.g. [Punycode](https://en.wikipedia.org/wiki/Punycode "Punycode") for [DNS](https://en.wikipedia.org/wiki/Domain_Name_System "Domain Name System") labels.

### Advantages
There are reasons to see URIs displayed in different languages; mostly, it makes it easier for users who are unfamiliar with the Latin (A–Z) alphabet. Assuming that it isn't too difficult for anyone to replicate arbitrary Unicode on their keyboards, this can make the [URI](https://en.wikipedia.org/wiki/URI "URI") system more accessible.

### Disadvantages
Mixing IRIs and [ASCII](https://en.wikipedia.org/wiki/ASCII "ASCII") [URIs](https://en.wikipedia.org/wiki/Uniform_resource_identifier "Uniform resource identifier") can make it much easier to execute [phishing](https://en.wikipedia.org/wiki/Phishing "Phishing") attacks that trick someone into believing they are on a different site than they really are. For example, one can replace an ASCII "a" in `www.myfictionalbank.com` with the Unicode look-alike "[α](https://en.wikipedia.org/wiki/%CE%91 "Α")" to give `www.myfictionαlbank.com` and point that IRI to a malicious site. This is known as an [IDN homograph attack](https://en.wikipedia.org/wiki/IDN_homograph_attack "IDN homograph attack").

While a URI does not provide people with a way to specify web resources using their own alphabets, an IRI does not make clear how web resources can be accessed with keyboards that are not capable of generating the requisite internationalized characters. This means that IRIs are now handled in a way very similar to many other software which might require the use of a non-keyboard [input method](https://en.wikipedia.org/wiki/Input_method "Input method") when dealing with texts in various languages.

## URL
A **uniform resource locator** (**URL**), colloquially known as an **address** on the [Web](https://en.wikipedia.org/wiki/World_Wide_Web "World Wide Web"), is a reference to a [resource](https://en.wikipedia.org/wiki/Web_resource "Web resource") that specifies its location on a [computer network](https://en.wikipedia.org/wiki/Computer_network "Computer network") and a mechanism for retrieving it. A URL is a specific type of [Uniform Resource Identifier](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier "Uniform Resource Identifier") (URI), although many people use the two terms interchangeably. URLs occur most commonly to reference [web pages](https://en.wikipedia.org/wiki/Web_page "Web page") ([HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol "Hypertext Transfer Protocol")/[HTTPS](https://en.wikipedia.org/wiki/HTTPS "HTTPS")) but are also used for file transfer ([FTP](https://en.wikipedia.org/wiki/File_Transfer_Protocol "File Transfer Protocol")), email ([mailto](https://en.wikipedia.org/wiki/Mailto "Mailto")), database access ([JDBC](https://en.wikipedia.org/wiki/Java_Database_Connectivity "Java Database Connectivity")), and many other applications.

Most [web browsers](https://en.wikipedia.org/wiki/Web_browser "Web browser") display the URL of a web page above the page in an [address bar](https://en.wikipedia.org/wiki/Address_bar "Address bar"). A typical URL could have the form `http://www.example.com/index.html`, which indicates a protocol (`http`), a [hostname](https://en.wikipedia.org/wiki/Hostname "Hostname") (`www.example.com`), and a file name (`index.html`).

### Syntax
Every HTTP URL conforms to the syntax of a generic URI. The URI generic syntax consists of five _components_ organized hierarchically in order of decreasing significance from left to right:

URI = scheme ":" ["//" authority] path ["?" query] ["#" fragment]

A component is _undefined_ if it has an associated delimiter and the delimiter does not appear in the URI; the scheme and path components are always defined. A component is _empty_ if it has no characters; the scheme component is always non-empty.

The authority component consists of _subcomponents_:

authority = [userinfo "@"] host [":" port]

This is represented in a [syntax diagram](https://en.wikipedia.org/wiki/Syntax_diagram "Syntax diagram") as:

[![URI syntax diagram](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d6/URI_syntax_diagram.svg/1068px-URI_syntax_diagram.svg.png)](https://en.wikipedia.org/wiki/File:URI_syntax_diagram.svg "URI syntax diagram")

The URI comprises:

- A non-empty **scheme** component followed by a colon (`:`), consisting of a sequence of characters beginning with a letter and followed by any combination of letters, digits, plus (`+`), period (`.`), or hyphen (`-`). Although schemes are case-insensitive, the canonical form is lowercase and documents that specify schemes must do so with lowercase letters. Examples of popular schemes include `[http]"Hypertext Transfer Protocol")`, `[https] "HTTP Secure")`, `[ftp] "File Transfer Protocol")`, `[mailto] "Mailto")`, `[file] "File URI scheme")`, `[data] "Data URI scheme")` and `[irc] "Internet Relay Chat")`. URI schemes should be registered with the [Internet Assigned Numbers Authority (IANA)](https://en.wikipedia.org/wiki/Internet_Assigned_Numbers_Authority "Internet Assigned Numbers Authority"), although non-registered schemes are used in practice.
- An optional **authority** component preceded by two slashes (`//`), comprising:
    - An optional **userinfo** subcomponent followed by an at symbol (`@`), that may consist of a [user name](https://en.wikipedia.org/wiki/User_(computing) "User (computing)") and an optional [password](https://en.wikipedia.org/wiki/Password "Password") preceded by a colon (`:`). Use of the format `username:password` in the userinfo subcomponent is deprecated for security reasons. Applications should not render as clear text any data after the first colon (`:`) found within a userinfo subcomponent unless the data after the colon is the empty string (indicating no password).
    - A **host** subcomponent, consisting of either a registered name (including but not limited to a [hostname](https://en.wikipedia.org/wiki/Hostname "Hostname")) or an [IP address](https://en.wikipedia.org/wiki/IP_address "IP address"). [IPv4](https://en.wikipedia.org/wiki/IPv4 "IPv4") addresses must be in [dot-decimal notation](https://en.wikipedia.org/wiki/Dot-decimal_notation "Dot-decimal notation"), and [IPv6](https://en.wikipedia.org/wiki/IPv6 "IPv6") addresses must be enclosed in brackets (`[]`).
    - An optional **port** subcomponent preceded by a colon (`:`), consisting of decimal digits.
- A **path** component, consisting of a sequence of path segments separated by a slash (`/`). A path is always defined for a URI, though the defined path may be empty (zero length). A segment may also be empty, resulting in two consecutive slashes (`//`) in the path component. A path component may resemble or map exactly to a [file system path](https://en.wikipedia.org/wiki/Path_(computing) "Path (computing)") but does not always imply a relation to one. If an authority component is defined, then the path component must either be empty or begin with a slash (`/`). If an authority component is undefined, then the path cannot begin with an empty segment—that is, with two slashes (`//`)—since the following characters would be interpreted as an authority component.

By convention, in **http** and **https** URIs, the last part of a _path_ is named **pathinfo** and it is optional. It is composed by zero or more path segments that do not refer to an existing physical resource name (e.g. a file, an internal module program or an executable program) but to a logical part (e.g. a command or a qualifier part) that has to be passed separately to the first part of the path that identifies an executable module or program managed by a [web server](https://en.wikipedia.org/wiki/Web_server "Web server"); this is often used to select dynamic content (a document, etc.) or to tailor it as requested (see also: [CGI](https://en.wikipedia.org/wiki/Common_Gateway_Interface "Common Gateway Interface") and PATH_INFO, etc.).

Example:

URI: `"http://www.example.com/questions/3456/my-document"`

where: `"/questions"` is the first part of the _path_ (an executable module or program) and `"/3456/my-document"` is the second part of the _path_ named _pathinfo_, which is passed to the executable module or program named `"/questions"` to select the requested document.

An **http** or **https** URI containing a _pathinfo_ part without a [query](https://en.wikipedia.org/wiki/URL#query) part may also be referred to as a '[clean URL](https://en.wikipedia.org/wiki/Clean_URL "Clean URL"),' whose last part may be a '[slug](https://en.wikipedia.org/wiki/Clean_URL#Slug "Clean URL").'

| Query delimiter | Example                   |
| --------------- | ------------------------- |
| Ampersand (`&`) | `key1=value1&key2=value2` |
| Semicolon (`;`) | `key1=value1;key2=value2` |

- An optional **query** component preceded by a question mark (`?`), consisting of a [query string](https://en.wikipedia.org/wiki/Query_string "Query string") of non-hierarchical data. Its syntax is not well defined, but by convention is most often a sequence of [attribute–value pairs](https://en.wikipedia.org/wiki/Attribute%E2%80%93value_pair "Attribute–value pair") separated by a [delimiter](https://en.wikipedia.org/wiki/Delimiter "Delimiter").
- An optional **fragment** component preceded by a [hash](https://en.wikipedia.org/wiki/Number_sign "Number sign") (`#`). The fragment contains a [fragment identifier](https://en.wikipedia.org/wiki/Fragment_identifier "Fragment identifier") providing direction to a secondary resource, such as a section heading in an article identified by the remainder of the URI. When the primary resource is an [HTML](https://en.wikipedia.org/wiki/HTML "HTML") document, the fragment is often an [`id` attribute](https://en.wikipedia.org/wiki/HTML#Attributes "HTML") of a specific element, and web browsers will scroll this element into view.

A web browser will usually [dereference](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier#Resolution "Uniform Resource Identifier") a URL by performing an [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol "Hypertext Transfer Protocol") request to the specified host, by default on port number 80. URLs using the `https` scheme require that requests and responses be made over a [secure connection to the website](https://en.wikipedia.org/wiki/HTTPS "HTTPS").

### Internationalized URL

Internet users are distributed throughout the world using a wide variety of languages and alphabets, and expect to be able to create URLs in their own local alphabets. An [Internationalized Resource Identifier](https://en.wikipedia.org/wiki/Internationalized_Resource_Identifier "Internationalized Resource Identifier") (IRI) is a form of URL that includes [Unicode](https://en.wikipedia.org/wiki/Unicode "Unicode") characters. All modern browsers support IRIs. The parts of the URL requiring special treatment for different alphabets are the domain name and path.

The domain name in the IRI is known as an [Internationalized Domain Name](https://en.wikipedia.org/wiki/Internationalized_Domain_Name "Internationalized Domain Name") (IDN). Web and Internet software automatically convert the domain name into [punycode](https://en.wikipedia.org/wiki/Punycode "Punycode") usable by the [Domain Name System](https://en.wikipedia.org/wiki/Domain_Name_System "Domain Name System"); for example, the Chinese URL `http://例子.卷筒纸` becomes `http://xn--fsqu00a.xn--3lr804guic/`. The `xn--` indicates that the character was not originally [ASCII](https://en.wikipedia.org/wiki/ASCII "ASCII").

The URL path name can also be specified by the user in the local writing system. If not already encoded, it is converted to [UTF-8](https://en.wikipedia.org/wiki/UTF-8 "UTF-8"), and any characters not part of the basic URL character set are escaped as [hexadecimal](https://en.wikipedia.org/wiki/Hexadecimal "Hexadecimal") using [percent-encoding](https://en.wikipedia.org/wiki/Percent-encoding "Percent-encoding"); for example, the Japanese URL `http://example.com/引き割り.html` becomes `http://example.com/%E5%BC%95%E3%81%8D%E5%89%B2%E3%82%8A.html`. The target computer decodes the address and displays the page.

### Protocol-relative URLs
Protocol-relative links (PRL), also known as protocol-relative URLs (PRURL), are URLs that have no protocol specified. For example, `//example.com` will use the protocol of the current page, typically HTTP or HTTPS.

## Routing
**Routing** is the process of selecting a path for traffic in a [network](https://en.wikipedia.org/wiki/Network_theory "Network theory") or between or across multiple networks. Broadly, routing is performed in many types of networks, including [circuit-switched networks](https://en.wikipedia.org/wiki/Circuit-switched_network "Circuit-switched network"), such as the [public switched telephone network](https://en.wikipedia.org/wiki/Public_switched_telephone_network "Public switched telephone network") (PSTN), and [computer networks](https://en.wikipedia.org/wiki/Computer_network "Computer network"), such as the [Internet](https://en.wikipedia.org/wiki/Internet "Internet").

In packet switching networks, routing is the higher-level decision making that directs [network packets](https://en.wikipedia.org/wiki/Network_packet "Network packet") from their source toward their destination through intermediate [network nodes](https://en.wikipedia.org/wiki/Network_node "Network node") by specific packet forwarding mechanisms. [Packet forwarding](https://en.wikipedia.org/wiki/Packet_forwarding "Packet forwarding") is the transit of network packets from one [network interface](https://en.wikipedia.org/wiki/Network_interface_controller "Network interface controller") to another. Intermediate nodes are typically [network hardware](https://en.wikipedia.org/wiki/Network_hardware "Network hardware") devices such as [routers](https://en.wikipedia.org/wiki/Router_(computing) "Router (computing)"), [gateways](https://en.wikipedia.org/wiki/Gateway_(telecommunications) "Gateway (telecommunications)"), [firewalls](https://en.wikipedia.org/wiki/Firewall_(computing) "Firewall (computing)"), or [switches](https://en.wikipedia.org/wiki/Network_switch "Network switch"). General-purpose [computers](https://en.wikipedia.org/wiki/Computer "Computer") also forward packets and perform routing, although they have no specially optimized hardware for the task.

The routing process usually directs forwarding on the basis of [routing tables](https://en.wikipedia.org/wiki/Routing_table "Routing table"). Routing tables maintain a record of the routes to various network destinations. Routing tables may be specified by an administrator, learned by observing network traffic or built with the assistance of [routing protocols](https://en.wikipedia.org/wiki/Routing_protocol "Routing protocol").

Routing, in a narrower sense of the term, often refers to [IP routing](https://en.wikipedia.org/wiki/IP_routing "IP routing") and is contrasted with [bridging](https://en.wikipedia.org/wiki/Bridging_(networking) "Bridging (networking)"). IP routing assumes that [network addresses](https://en.wikipedia.org/wiki/Network_address "Network address") are structured and that similar addresses imply proximity within the network. Structured addresses allow a single routing table entry to represent the route to a group of devices. In large networks, structured addressing (routing, in the narrow sense) outperforms unstructured addressing (bridging). Routing has become the dominant form of addressing on the Internet. Bridging is still widely used within [local area networks](https://en.wikipedia.org/wiki/Local_area_network "Local area network").

### Delivery schemes

| [Routing schemes](https://en.wikipedia.org/wiki/Routing#Delivery_schemes)                                                                                                                                                                                                                           |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Unicast](https://en.wikipedia.org/wiki/Unicast "Unicast")<br><br>[![](https://upload.wikimedia.org/wikipedia/commons/thumb/7/75/Unicast.svg/100px-Unicast.svg.png)](https://en.wikipedia.org/wiki/Unicast "Unicast")                                                                               |
| [Broadcast](https://en.wikipedia.org/wiki/Broadcasting_(networking) "Broadcasting (networking)")<br><br>[![](https://upload.wikimedia.org/wikipedia/commons/thumb/d/dc/Broadcast.svg/100px-Broadcast.svg.png)](https://en.wikipedia.org/wiki/Broadcasting_(networking) "Broadcasting (networking)") |
| [Multicast](https://en.wikipedia.org/wiki/Multicast "Multicast")<br><br>[![](https://upload.wikimedia.org/wikipedia/commons/thumb/3/30/Multicast.svg/100px-Multicast.svg.png)](https://en.wikipedia.org/wiki/Multicast "Multicast")                                                                 |
| [Anycast](https://en.wikipedia.org/wiki/Anycast "Anycast")<br><br>[![](https://upload.wikimedia.org/wikipedia/en/thumb/1/18/Anycast-BM.svg/100px-Anycast-BM.svg.png)](https://en.wikipedia.org/wiki/Anycast "Anycast")                                                                              |

Routing schemes differ in how they deliver messages:
- [Unicast](https://en.wikipedia.org/wiki/Unicast "Unicast") delivers a message to a single specific node using a _one-to-one_ association between a sender and destination: each destination address uniquely identifies a single receiver endpoint.
- [Broadcast](https://en.wikipedia.org/wiki/Broadcasting_(networking) "Broadcasting (networking)") delivers a message to all nodes in the network using a _one-to-all_ association; a single [datagram](https://en.wikipedia.org/wiki/Datagram "Datagram") (or [packet](https://en.wikipedia.org/wiki/Packet_(information_technology) "Packet (information technology)")) from one sender is routed to all of the possibly multiple endpoints associated with the [broadcast address](https://en.wikipedia.org/wiki/Broadcast_address "Broadcast address"). The network automatically replicates datagrams as needed to reach all the recipients within the scope of the broadcast, which is generally an entire network [subnet](https://en.wikipedia.org/wiki/Subnetwork "Subnetwork").
- [Multicast](https://en.wikipedia.org/wiki/Multicast "Multicast") delivers a message to a group of nodes that have expressed interest in receiving the message using a _one-to-many-of-many_ or _many-to-many-of-many_ association; datagrams are routed simultaneously in a single transmission to many recipients. Multicast differs from broadcast in that the destination address designates a subset, not necessarily all, of the accessible nodes.
- [Anycast](https://en.wikipedia.org/wiki/Anycast "Anycast") delivers a message to any one out of a group of nodes, typically the one nearest to the source using a _one-to-one-of-many_ association where datagrams are routed to any single member of a group of potential receivers that are all identified by the same destination address. The routing algorithm selects the single receiver from the group based on which is the nearest according to some distance or cost measure.

Unicast is the dominant form of message delivery on the Internet. This article focuses on unicast routing algorithms.

### Topology distribution
With [static routing](https://en.wikipedia.org/wiki/Static_routing "Static routing"), small networks may use manually configured routing tables. Larger networks have complex [topologies](https://en.wikipedia.org/wiki/Network_topology "Network topology") that can change rapidly, making the manual construction of routing tables unfeasible. Nevertheless, most of the [public switched telephone network](https://en.wikipedia.org/wiki/Public_switched_telephone_network "Public switched telephone network") (PSTN) uses pre-computed routing tables, with fallback routes if the most direct route becomes blocked (see [routing in the PSTN](https://en.wikipedia.org/wiki/Routing_in_the_PSTN "Routing in the PSTN")).

[Dynamic routing](https://en.wikipedia.org/wiki/Dynamic_routing "Dynamic routing") attempts to solve this problem by constructing routing tables automatically, based on information carried by [routing protocols](https://en.wikipedia.org/wiki/Routing_protocol "Routing protocol"), allowing the network to act nearly autonomously in avoiding network failures and blockages. Dynamic routing dominates the Internet. Examples of dynamic-routing protocols and algorithms include [Routing Information Protocol](https://en.wikipedia.org/wiki/Routing_Information_Protocol "Routing Information Protocol") (RIP), [Open Shortest Path First](https://en.wikipedia.org/wiki/Open_Shortest_Path_First "Open Shortest Path First") (OSPF) and [Enhanced Interior Gateway Routing Protocol](https://en.wikipedia.org/wiki/Enhanced_Interior_Gateway_Routing_Protocol "Enhanced Interior Gateway Routing Protocol") (EIGRP).

#### Distance vector algorithms
Distance vector algorithms use the [Bellman–Ford algorithm](https://en.wikipedia.org/wiki/Bellman%E2%80%93Ford_algorithm "Bellman–Ford algorithm"). This approach assigns a _cost_ number to each of the links between each node in the network. Nodes send information from point A to point B via the path that results in the lowest _total cost_ (i.e. the sum of the costs of the links between the nodes used).

When a node first starts, it only knows of its immediate neighbors and the direct cost involved in reaching them. (This information — the list of destinations, the total cost to each, and the _next hop_ to send data to get there — makes up the routing table, or _distance table_.) Each node, on a regular basis, sends to each neighbor node its own current assessment of the total cost to get to all the destinations it knows of. The neighboring nodes examine this information and compare it to what they already know; anything that represents an improvement on what they already have, they insert in their own table. Over time, all the nodes in the network discover the best next hop and total cost for all destinations.

When a network node goes down, any nodes that used it as their next hop discard the entry and convey the updated routing information to all adjacent nodes, which in turn repeat the process. Eventually, all the nodes in the network receive the updates and discover new paths to all the destinations that do not involve the down node.

#### Link-state algorithms
When applying link-state algorithms, a [graphical map](https://en.wikipedia.org/wiki/Graph_(discrete_mathematics) "Graph (discrete mathematics)") of the network is the fundamental data used for each node. To produce its map, each node floods the entire network with information about the other nodes it can connect to. Each node then independently assembles this information into a map. Using this map, each router independently determines the least-cost path from itself to every other node using a standard [shortest paths](https://en.wikipedia.org/wiki/Shortest_paths "Shortest paths") algorithm such as [Dijkstra's algorithm](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm "Dijkstra's algorithm"). The result is a [tree graph](https://en.wikipedia.org/wiki/Tree_graph "Tree graph") rooted at the current node, such that the path through the tree from the root to any other node is the least-cost path to that node. This tree then serves to construct the routing table, which specifies the best next hop to get from the current node to any other node.

#### Optimized Link State Routing algorithm
A link-state routing algorithm optimized for [mobile ad hoc networks](https://en.wikipedia.org/wiki/Mobile_ad_hoc_network "Mobile ad hoc network") is the optimized Link State Routing Protocol (OLSR). OLSR is proactive; it uses Hello and Topology Control (TC) messages to discover and disseminate link-state information through the mobile ad hoc network. Using Hello messages, each node discovers 2-hop neighbor information and elects a set of _multipoint relays_ (MPRs). MPRs distinguish OLSR from other link-state routing protocols.

#### Path-vector protocol
Distance vector and link-state routing are both intra-domain routing protocols. They are used inside an [autonomous system](https://en.wikipedia.org/wiki/Autonomous_system_(Internet) "Autonomous system (Internet)"), but not between autonomous systems. Both of these routing protocols become intractable in large networks and cannot be used in [inter-domain](https://en.wikipedia.org/wiki/Inter-domain "Inter-domain") routing. Distance vector routing is subject to instability if there are more than a few hops in the domain. Link state routing needs significant resources to calculate routing tables. It also creates heavy traffic due to flooding.

Path-vector routing is used for inter-domain routing. It is similar to distance vector routing. Path-vector routing assumes that one node (there can be many) in each autonomous system acts on behalf of the entire autonomous system. This node is called the _speaker node._ The speaker node creates a routing table and advertises it to neighboring speaker nodes in neighboring autonomous systems. The idea is the same as distance vector routing except that only speaker nodes in each autonomous system can communicate with each other. The speaker node advertises the path, not the metric, of the nodes in its autonomous system or other autonomous systems.

The path-vector routing algorithm is similar to the distance vector algorithm in the sense that each border router advertises the destinations it can reach to its neighboring router. However, instead of advertising networks in terms of a destination and the distance to that destination, networks are advertised as destination addresses and path descriptions to reach those destinations. The path, expressed in terms of the domains (or confederations) traversed so far, is carried in a special path attribute that records the sequence of routing domains through which the reachability information has passed. A route is defined as a pairing between a destination and the attributes of the path to that destination, thus the name, path-vector routing; The routers receive a vector that contains paths to a set of destinations.

### Path selection
Path selection involves applying a [routing metric](https://en.wikipedia.org/wiki/Routing_metric "Routing metric") to multiple routes to select (or predict) the best route. Most routing algorithms use only one network path at a time. [Multipath routing](https://en.wikipedia.org/wiki/Multipath_routing "Multipath routing") and specifically [equal-cost multi-path routing](https://en.wikipedia.org/wiki/Equal-cost_multi-path_routing "Equal-cost multi-path routing") techniques enable the use of multiple alternative paths.

In computer networking, the metric is computed by a routing algorithm, and can cover information such as [bandwidth](https://en.wikipedia.org/wiki/Bandwidth_(computing) "Bandwidth (computing)"), [network delay](https://en.wikipedia.org/wiki/Network_delay "Network delay"), [hop count](https://en.wikipedia.org/wiki/Hop_count "Hop count"), path cost, load, [maximum transmission unit](https://en.wikipedia.org/wiki/Maximum_transmission_unit "Maximum transmission unit"), reliability, and communication cost. The routing table stores only the best possible routes, while [link-state](https://en.wikipedia.org/wiki/Link-state "Link-state") or topological databases may store all other information as well.

In case of overlapping or equal routes, algorithms consider the following elements in priority order to decide which routes to install into the routing table:

1. _Prefix length_: A matching route table entry with a longer subnet mask is always preferred as it specifies the destination more exactly.
2. _[Metric](https://en.wikipedia.org/wiki/Metrics_(networking) "Metrics (networking)")_: When comparing routes learned via the same routing protocol, a lower metric is preferred. Metrics cannot be compared between routes learned from different routing protocols.
3. _[Administrative distance](https://en.wikipedia.org/wiki/Administrative_distance "Administrative distance")_: When comparing route table entries from different sources such as different routing protocols and static configuration, a lower administrative distance indicates a more reliable source and thus a preferred route.

Because a routing metric is specific to a given routing protocol, multi-protocol routers must use some external [heuristic](https://en.wikipedia.org/wiki/Heuristic "Heuristic") to select between routes learned from different routing protocols. [Cisco](https://en.wikipedia.org/wiki/Cisco "Cisco") routers, for example, attribute a value known as the [administrative distance](https://en.wikipedia.org/wiki/Administrative_distance "Administrative distance") to each route, where smaller administrative distances indicate routes learned from a protocol assumed to be more reliable.

A local administrator can set up host-specific routes that provide more control over network usage, permits testing, and better overall security. This is useful for debugging network connections or routing tables.

In some small systems, a single central device decides ahead of time the complete path of every packet. In some other small systems, whichever edge device injects a packet into the network decides ahead of time the complete path of that particular packet. In either case, the route-planning device needs to know a lot of information about what devices are connected to the network and how they are connected to each other. Once it has this information, it can use an algorithm such as [A* search algorithm](https://en.wikipedia.org/wiki/A*_search_algorithm "A* search algorithm") to find the best path.

In high-speed systems, there are so many packets transmitted every second that it is infeasible for a single device to calculate the complete path for each and every packet. Early high-speed systems dealt with this with [circuit switching](https://en.wikipedia.org/wiki/Circuit_switching "Circuit switching") by setting up a path once for the first packet between some source and some destination; later packets between that same source and that same destination continue to follow the same path without recalculating until the circuit [teardown](https://en.wikipedia.org/wiki/Teardown_(communications) "Teardown (communications)"). Later high-speed systems inject packets into the network without any one device ever calculating a complete path for packets.

In large systems, there are so many connections between devices, and those connections change so frequently, that it is infeasible for any one device to even know how all the devices are connected to each other, much less calculate a complete path through them. Such systems generally use [next-hop](https://en.wikipedia.org/wiki/Hop_(networking)#Next_hop "Hop (networking)") routing.

Most systems use a deterministic [dynamic routing](https://en.wikipedia.org/wiki/Dynamic_routing "Dynamic routing") algorithm. When a device chooses a path to a particular final destination, that device always chooses the same path to that destination until it receives information that makes it think some other path is better.

A few routing algorithms do not use a deterministic algorithm to find the best link for a packet to get from its original source to its final destination. Instead, to avoid congestion hot spots in packet systems, a few algorithms use a randomized algorithm—Valiant's paradigm—that routes a path to a randomly picked intermediate destination, and from there to its true final destination. In many early telephone switches, a randomizer was often used to select the start of a path through a [multistage switching fabric](https://en.wikipedia.org/wiki/1ESS_switch#Switching_fabric "1ESS switch").

Depending on the application for which path selection is performed, different metrics can be used. For example, for web requests one can use minimum latency paths to minimize web page load time, or for bulk data transfers one can choose the least utilized path to balance load across the network and increase throughput. A popular path selection objective is to reduce the average completion times of traffic flows and the total network bandwidth consumption. Recently, a path selection metric was proposed that computes the total number of bytes scheduled on the edges per path as selection metric. An empirical analysis of several path selection metrics, including this new proposal, has been made available.

### Multiple agents
In some networks, routing is complicated by the fact that no single entity is responsible for selecting paths; instead, multiple entities are involved in selecting paths or even parts of a single path. Complications or inefficiency can result if these entities choose paths to optimize their own objectives, which may conflict with the objectives of other participants.

A classic example involves traffic in a road system, in which each driver picks a path that minimizes their travel time. With such routing, the [equilibrium](https://en.wikipedia.org/wiki/Nash_equilibrium "Nash equilibrium") routes can be longer than optimal for all drivers. In particular, [Braess's paradox](https://en.wikipedia.org/wiki/Braess%27s_paradox "Braess's paradox") shows that adding a new road can _lengthen_ travel times for all drivers.

In a single-agent model used, for example, for routing [automated guided vehicles](https://en.wikipedia.org/wiki/Automated_guided_vehicle "Automated guided vehicle") (AGVs) on a terminal, reservations are made for each vehicle to prevent simultaneous use of the same part of an infrastructure. This approach is also referred to as context-aware routing.

The Internet is partitioned into [autonomous systems](https://en.wikipedia.org/wiki/Autonomous_system_(Internet) "Autonomous system (Internet)") (ASs) such as [internet service providers](https://en.wikipedia.org/wiki/Internet_service_provider "Internet service provider") (ISPs), each of which controls routes involving its network. Routing occurs at multiple levels. First, AS-level paths are selected via the [BGP](https://en.wikipedia.org/wiki/BGP "BGP") protocol that produces a sequence of ASs through which packets flow. Each AS may have multiple paths, offered by neighboring ASs, from which to choose. These routing decisions often correlate with business relationships with these neighboring ASs, which may be unrelated to path quality or latency. Second, once an AS-level path has been selected, there are often multiple corresponding router-level paths to choose from. This is due, in part, because two ISPs may be connected through multiple connections. In choosing the single router-level path, it is common practice for each ISP to employ [hot-potato routing](https://en.wikipedia.org/wiki/Hot-potato_routing "Hot-potato routing"): sending traffic along the path that minimizes the distance through the ISP's own network—even if that path lengthens the total distance to the destination.

For example, consider two ISPs, _A_ and _B_. Each has a presence in [New York](https://en.wikipedia.org/wiki/New_York_City "New York City"), connected by a fast link with latency 5 [ms](https://en.wikipedia.org/wiki/Millisecond "Millisecond")—and each has a presence in [London](https://en.wikipedia.org/wiki/London "London") connected by a 5 ms link. Suppose both ISPs have trans-Atlantic links that connect their two networks, but _A_'s link has latency 100 ms and _B_'s has latency 120 ms. When routing a message from a source in _A_'s London network to a destination in _B_'s New York network, _A_ may choose to immediately send the message to _B_ in London. This saves _A_ the work of sending it along an expensive trans-Atlantic link, but causes the message to experience latency 125 ms when the other route would have been 20 ms faster.

Additionally, a similar routing challenge can be observed in cellular networks, where different packets are destined for various endpoints, and each link exhibits varying spectral efficiency. In this context, the selection of the _optimal_ path involves considering latency and packet error rate. To address this, multiple independent entities, one for each base station, play a crucial role in path selection while striving to optimize overall network performance.

A 2003 measurement study of Internet routes found that, between pairs of neighboring ISPs, more than 30% of paths have inflated latency due to hot-potato routing, with 5% of paths being delayed by at least 12 ms. Inflation due to AS-level path selection, while substantial, was attributed primarily to BGP's lack of a mechanism to directly optimize for latency, rather than to selfish routing policies. It was also suggested that, were an appropriate mechanism in place, ISPs would be willing to cooperate to reduce latency rather than use hot-potato routing. Such a mechanism was later published by the same authors, first for the case of two ISPs and then for the global case.
### Route analytics
As the Internet and IP networks have become [mission critical](https://en.wikipedia.org/wiki/Mission_critical "Mission critical") business tools, there has been increased interest in techniques and methods to monitor the routing posture of networks. Incorrect routing or routing issues cause undesirable performance degradation, [flapping](https://en.wikipedia.org/wiki/Route_flapping "Route flapping") or downtime. Monitoring routing in a network is achieved using [route analytics](https://en.wikipedia.org/wiki/Route_analytics "Route analytics") tools and techniques.

### Centralized routing
In networks where a logically centralized control is available over the forwarding state, for example, using [software-defined networking](https://en.wikipedia.org/wiki/Software-defined_networking "Software-defined networking"), routing techniques can be used that aim to optimize global and network-wide performance metrics. This has been used by large internet companies that operate many data centers in different geographical locations attached using private optical links, examples of which include Microsoft's Global WAN, Facebook's Express Backbone, and Google's B4.

Global performance metrics to optimize include maximizing network utilization, minimizing traffic flow completion times, maximizing the traffic delivered prior to specific deadlines and reducing the completion times of flows. Work on the later over private WAN discusses modeling routing as a graph optimization problem by pushing all the queuing to the end-points. The authors also propose a heuristic to solve the problem efficiently while sacrificing negligible performance.

## Static Routing
**Static routing** describes a process by which [routing](https://en.wikipedia.org/wiki/Routing "Routing") is configured with fixed values which do not change at runtime unless manually edited. Static routes are used with and without dynamic [Routing protocols](https://en.wikipedia.org/wiki/Routing_protocol "Routing protocol") and usually share the same [routing table](https://en.wikipedia.org/wiki/Routing_table "Routing table") as those protocols. Routes require at least two attributes; the destination and the gateway, but may contain additional attributes such as a [metric](https://en.wikipedia.org/wiki/Metrics_(networking) "Metrics (networking)") (sometimes called the _administrative distance_). Some implementations treat the network address and [subnet mask](https://en.wikipedia.org/wiki/Subnet_mask "Subnet mask") as separate values, however in practice both of the values have to be considered for any given routing decision to determine the [longest prefix match](https://en.wikipedia.org/wiki/Longest_prefix_match "Longest prefix match"). Static routes together with _connected_ routes and routes from configuration protocols such as [DHCP](https://en.wikipedia.org/wiki/DHCP "DHCP") or [Router Advertisements](https://en.wikipedia.org/wiki/Neighbor_Discovery_Protocol "Neighbor Discovery Protocol") provide the routes which are then redistributed using dynamic routing protocols. While static routes are entered into the system and remain there until removed or changed manually, dynamic routing protocols create and delete routes dynamically at runtime without intervention. Thus the term _static_ here refers to the nature of remaining unchanged by the system itself. The most prominent example of a static route is a [default route](https://en.wikipedia.org/wiki/Default_route "Default route") which is often used on devices with a statically configured [IP address](https://en.wikipedia.org/wiki/IP_address "IP address") to provide the device with access to the rest of the network or the internet by default. In contrast to a so called _connected_ route which is automatically generated upon address assignment based on the used subnet mask, a static route must be manually configured. Due to this the configuration may fail if there is no route to the provided gateway at the time of configuration, other than the connected route which will always succeed as it does not require a gateway. The gateway of a static route need not be an address, but can also specify an interface in most implementations.

### Uses
Static routing may have the following uses:
- When using static address configuration (in the absence of DHCP or Router Advertisements) it can be used to provide a [default route](https://en.wikipedia.org/wiki/Default_route "Default route"), forming a special case of the longest prefix match as it has a prefix length of zero and therefore always matches, and always matches last.
- In small networks it is a viable method for providing alternative routes to direct traffic when multiple routers exist. This is a simple but limited form of [Teletraffic engineering](https://en.wikipedia.org/wiki/Teletraffic_engineering "Teletraffic engineering").
- Static routing has applications in environments with many routes with infrequent changes as it reduces the delay it would take to synchronize the routes from another device.
- On heavily resource constrained devices where routing protocols may not be viable due to lack of computation power, static routes may be used instead.
- Static routes, connected routes, and routes from dynamic configuration protocols can be redistributed by dynamic routing protocols. For instance a router may have a static or connected route for a local network segment, which is then redistributed over dynamic routing protocols to enable connectivity to that network.
- By using the [metric](https://en.wikipedia.org/wiki/Metrics_(networking) "Metrics (networking)") to reduce the priority of a static route a fallback can be provided for instance when a DHCP server becomes unavailable. This can also prevent a type of lockout situation in which one would be unable to access the device otherwise.

### Advantages
Static routing has the following advantages:
- Due to being configured on the device it can serve as a bootstrap for other protocols.
- It does not require connectivity to work, providing high fault-tolerance in case of network failures.
- Compared to dynamic routing protocols, static routes are much more widely available, for instance many low-end consumer switches are capable of setting static routes.
- As static routes are not read from the network, there are also fewer security considerations. Dynamic routing protocols may need to be secured such that an attacker cannot redirect traffic from the outside.

### Disadvantages
Static routing can have some potential disadvantages:
- **Human error:** As the routes have to be manually configured this may be a source of human error in the absence of automated configuration management.
- **Administrative overhead:** Similarly the routes have to be provided to the devices. This can be remedied by configuration management, but also using simpler means of using a [template engine](https://en.wikipedia.org/wiki/Template_engine "Template engine") to generate configuration using repetition or [IP address management](https://en.wikipedia.org/wiki/IP_address_management "IP address management") software.
- **Fault tolerance:** While static routes not being removed during a network failure can be good in that routes continue to function, however most implementations continue to use a static route as long as the interface the gateway is on is in an _up_ state. When [network hardware fails](https://en.wikipedia.org/wiki/Failure_of_electronic_components "Failure of electronic components") it is not necessary _down_; a [hang](https://en.wikipedia.org/wiki/Hang_(computing) "Hang (computing)") may cause interfaces to keep running but not accepting traffic. Routing protocols usually implement timeouts after which routes are removed, or have integration with additional protocols such as [Bidirectional Forwarding Detection](https://en.wikipedia.org/wiki/Bidirectional_Forwarding_Detection "Bidirectional Forwarding Detection") to reduce the time the faulty route is present to sub-second.
- **Observability:** Static routes themselves do not propagate, which means that in a network built using only static routes it is hard to get a big picture of all present routes unless [monitored](https://en.wikipedia.org/wiki/Event_monitoring "Event monitoring"). Dynamic routing protocols often transmit topology information or can be connected to debugging tools such as a [Looking Glass server](https://en.wikipedia.org/wiki/Looking_Glass_server "Looking Glass server").

## Dynamic Routing
**Dynamic routing**, also called **adaptive routing**, is a process where a router can forward data via a different route for a given destination based on the current conditions of the communication circuits within a system. The term is most commonly associated with [data networking](https://en.wikipedia.org/wiki/Data_networking "Data networking") to describe the capability of a network to 'route around' damage, such as loss of a node or a connection between nodes, as long as other path choices are available. Dynamic routing allows as many routes as possible to remain valid in response to the change.

Systems that do not implement dynamic routing are described as using [static routing](https://en.wikipedia.org/wiki/Static_routing "Static routing"), where routes through a network are described by fixed paths. A change, such as the loss of a node, or loss of a connection between nodes, is not compensated for. This means that anything that wishes to take an affected path will either have to wait for the failure to be repaired before restarting its journey, or will have to fail to reach its destination and give up the journey.
### All protocols
There are several [routing protocols](https://en.wikipedia.org/wiki/Routing_protocols "Routing protocols") that can be used for dynamic routing. [Routing Information Protocol](https://en.wikipedia.org/wiki/Routing_Information_Protocol "Routing Information Protocol") (RIP) is a [distance-vector routing protocol](https://en.wikipedia.org/wiki/Distance-vector_routing_protocol "Distance-vector routing protocol") that prevents [routing loops](https://en.wikipedia.org/wiki/Routing_loop_problem "Routing loop problem") by implementing a limit on the number of [hops](https://en.wikipedia.org/wiki/Hop_(telecommunications) "Hop (telecommunications)") allowed in a path from source to destination. [Open Shortest Path First](https://en.wikipedia.org/wiki/Open_Shortest_Path_First "Open Shortest Path First") (OSPF) uses a [link state routing](https://en.wikipedia.org/wiki/Link-state_routing_protocol "Link-state routing protocol") (LSR) algorithm and falls into the group of [interior gateway protocols](https://en.wikipedia.org/wiki/Interior_gateway_protocol "Interior gateway protocol") (IGPs). [Intermediate System to Intermediate System](https://en.wikipedia.org/wiki/Intermediate_System_to_Intermediate_System "Intermediate System to Intermediate System") (IS-IS) determines the best [route](https://en.wikipedia.org/wiki/Routing "Routing") for data through a [packet-switched network](https://en.wikipedia.org/wiki/Packet-switched_network "Packet-switched network").Interior Gateway Routing Protocol (IGRP) and its advanced form [Enhanced Interior Gateway Routing Protocol](https://en.wikipedia.org/wiki/Enhanced_Interior_Gateway_Routing_Protocol "Enhanced Interior Gateway Routing Protocol") (EIGRP) are used by [routers](https://en.wikipedia.org/wiki/Router_(computing) "Router (computing)") to exchange [routing](https://en.wikipedia.org/wiki/Routing "Routing") data within an [autonomous system](https://en.wikipedia.org/wiki/Autonomous_system_(Internet) "Autonomous system (Internet)").

### Alternate paths
Many systems use some [next-hop](https://en.wikipedia.org/wiki/Hop_(networking)#Next_hop "Hop (networking)") forwarding protocol—when a packet arrives at some node, that node decides on-the-fly which link to use to push the packet one hop closer to its final destination.

Routers that use some adaptive protocols, such as the [Spanning Tree Protocol](https://en.wikipedia.org/wiki/Spanning_Tree_Protocol "Spanning Tree Protocol"), in order to "avoid [bridge loops](https://en.wikipedia.org/wiki/Bridge_loop "Bridge loop") and [routing loops](https://en.wikipedia.org/wiki/Routing_loop "Routing loop")", calculate a tree that indicates the one "best" link for a packet to get to its destination. Alternate "redundant" links not on the tree are temporarily disabled—until one of the links on the main tree fails, and the routers calculate a new tree using those links to route around the broken link.

Routers that use other adaptive protocols, such as **grouped adaptive routing**, find a group of _all_ the links that could be used to get the packet one hop closer to its final destination. The router sends the packet out any link of that group which is idle. The [link aggregation](https://en.wikipedia.org/wiki/Link_aggregation "Link aggregation") of that group of links effectively becomes a single high-bandwidth connection.

### Outside of computer networks
[Contact centres](https://en.wikipedia.org/wiki/Call_centre "Call centre") employ dynamic routing based on the customer's enquiry and agent's skills to increase the operational efficiency of the call handling by agents, which boosts both agent and customer satisfaction. This adaptive strategy is known as [omnichannel](https://en.wikipedia.org/wiki/Omnichannel "Omnichannel").

Dynamic routing in found the [brain](https://en.wikipedia.org/wiki/Brain "Brain") in relation between sensory and mnemonic signals and decision making, and is a subject of studies in [neuroscience](https://en.wikipedia.org/wiki/Neuroscience "Neuroscience").

People using [public transport](https://en.wikipedia.org/wiki/Public_transport "Public transport") also exhibit dynamic routing behaviour. For example, if a local railway station is closed, people can alight from the train at a different station and use a bus to reach their destination.

## Instance
In computer science, an **instance** is an occurrence of a [software](https://en.wikipedia.org/wiki/Software "Software") element that is based on a [type](https://en.wikipedia.org/wiki/Data_type "Data type") definition. When created, an occurrence is said to have been _instantiated_, and both the creation process and the result of creation are called _instantiation_.

### Examples
#### Class instance
A **class instance** is an object-oriented programming (OOP) [object](https://en.wikipedia.org/wiki/Object_(computer_science) "Object (computer science)") created from a [class](https://en.wikipedia.org/wiki/Class_(computer_programming) "Class (computer programming)"). Each instance of a class shares a data layout but has its own memory allocation.

#### Computer instance
A **computer instance** is an occurrence of a [virtual machine](https://en.wikipedia.org/wiki/Virtual_machine "Virtual machine") which typically includes storage, a virtual [CPU](https://en.wikipedia.org/wiki/Central_processing_unit "Central processing unit").

#### Polygonal model
A computer graphics **polygonal model** can be instantiated in order to be drawn several times in different locations in a scene which can improve the performance of [rendering](https://en.wikipedia.org/wiki/Rendering_(computer_graphics) "Rendering (computer graphics)") since a portion of the work needed to display each instance is reused.

#### Program instance
In a [POSIX-oriented operating system](https://en.wikipedia.org/wiki/POSIX#POSIX-oriented_operating_systems "POSIX"), **program instance** refers to an executing [process](https://en.wikipedia.org/wiki/Process_(computing) "Process (computing)"). It is instantiated for a [program](https://en.wikipedia.org/wiki/Computer_program "Computer program") via [system calls](https://en.wikipedia.org/wiki/System_call "System call") such as [fork()](https://en.wikipedia.org/wiki/Fork_(system_call) "Fork (system call)") and [exec()](https://en.wikipedia.org/wiki/Exec_(system_call) "Exec (system call)"). Each executing process is an instance of a program which it has been instantiated from.

## Function Composition
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), **function composition** is an act or mechanism to combine simple [functions](https://en.wikipedia.org/wiki/Subroutine "Subroutine") to build more complicated ones. Like the usual [composition of functions](https://en.wikipedia.org/wiki/Function_composition "Function composition") in [mathematics](https://en.wikipedia.org/wiki/Mathematics "Mathematics"), the result of each function is passed as the argument of the next, and the result of the last one is the result of the whole.

Programmers frequently apply functions to results of other functions, and almost all programming languages allow it. In some cases, the composition of functions is interesting as a function in its own right, to be used later. Such a function can always be defined but languages with [first-class functions](https://en.wikipedia.org/wiki/First-class_function "First-class function") make it easier.

The ability to easily compose functions encourages [factoring](https://en.wikipedia.org/wiki/Factoring_\(computer_science\) "Factoring (computer science)") (breaking apart) [functions](https://en.wikipedia.org/wiki/Subroutine "Subroutine") for maintainability and [code reuse](https://en.wikipedia.org/wiki/Code_reuse "Code reuse"). More generally, big systems might be built by composing whole programs.

Narrowly speaking, function composition applies to functions that operate on a finite amount of data, each step sequentially processing it before handing it to the next. Functions that operate on potentially infinite data (a [stream](https://en.wikipedia.org/wiki/Stream_\(computing\) "Stream (computing)") or other [codata](https://en.wikipedia.org/wiki/Codata_\(computer_science\) "Codata (computer science)")) are known as [filters](https://en.wikipedia.org/wiki/Filter_\(software\) "Filter (software)"), and are instead connected in a [pipeline](https://en.wikipedia.org/wiki/Pipeline_\(software\) "Pipeline (software)"), which is analogous to function composition and can execute [concurrently](https://en.wikipedia.org/wiki/Concurrent_computing "Concurrent computing").

### Composing function calls
For example, suppose we have two [functions](https://en.wikipedia.org/wiki/Function_\(mathematics\) "Function (mathematics)") f and g, as in _z_ = _f_(_y_) and _y_ = _g_(_x_). Composing them means we first compute _y_ = _g_(_x_), and then use y to compute _z_ = _f_(_y_). Here is the example in the [C language](https://en.wikipedia.org/wiki/C_\(programming_language\) "C (programming language)"):

```c
float x, y, z;
// ...
y = g(x);
z = f(y);
```

The steps can be combined if we don't give a name to the intermediate result:
```c
z = f(g(x));
```

Despite differences in length, these two implementations compute the same result. The second implementation requires only one line of code and is colloquially referred to as a "highly composed" form. Readability and hence maintainability is one advantage of highly composed forms, since they require fewer lines of code, minimizing a program's "surface area". DeMarco and Lister empirically verify an inverse relationship between surface area and maintainability. On the other hand, it may be possible to overuse highly composed forms. A nesting of too many functions may have the opposite effect, making the code less maintainable.

In a [stack-based language](https://en.wikipedia.org/wiki/Stack-based_language "Stack-based language"), functional composition is even more natural: it is performed by [concatenation](https://en.wikipedia.org/wiki/Concatenation "Concatenation"), and is usually the primary method of program design. The above example in [Forth](https://en.wikipedia.org/wiki/Forth_\(programming_language\) "Forth (programming language)"):

```forth
g f
```

Which will take whatever was on the stack before, apply g, then f, and leave the result on the stack. See [postfix composition notation](https://en.wikipedia.org/wiki/Function_composition#Alternative_notations "Function composition") for the corresponding mathematical notation.

### Naming the composition of functions
Now suppose that the combination of calling f() on the result of g() is frequently useful, and which we want to name foo() to be used as a function in its own right.

In most languages, we can define a new function implemented by composition. Example in [C](https://en.wikipedia.org/wiki/C_\(programming_language\) "C (programming language)"):
```c
float foo(float x) {
    return f(g(x));
}
```

(the long form with intermediates would work as well.) Example in [Forth](https://en.wikipedia.org/wiki/Forth_\(programming_language\) "Forth (programming language)"):

```forth
  : foo g f ;
```

In languages such as [C](https://en.wikipedia.org/wiki/C_\(programming_language\) "C (programming language)"), the only way to create a new function is to define it in the program source, which means that functions can't be composed at [run time](https://en.wikipedia.org/wiki/Run_time_\(program_lifecycle_phase\) "Run time (program lifecycle phase)"). An evaluation of an arbitrary composition of _predefined_ functions, however, is possible:

```c
#include <stdio.h>

typedef int FXN(int);

int f(int x) { return x+1; }
int g(int x) { return x*2; }
int h(int x) { return x-3; }

int eval(FXN *fs[], int size, int x)
{
   for (int i=0; i<size; i++) x = (*fs[i])(x);

   return x;
}

int main()
{
   // ((6+1)*2)-3 = 11
   FXN *arr[] = {f,g,h};
   printf("%d\n", eval(arr, 3, 6));

   // ((6-3)*2)+1 = 7
   arr[2] = f;  arr[0] = h;
   printf("%d\n", eval(arr, 3, 6));
}
```

### First-class composition
In [functional programming](https://en.wikipedia.org/wiki/Functional_programming "Functional programming") languages, function composition can be naturally expressed as a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function "Higher-order function") or operator. In other programming languages you can write your own mechanisms to perform function composition.

#### Haskell
In [Haskell](https://en.wikipedia.org/wiki/Haskell_\(programming_language\) "Haskell (programming language)"), the example _foo_ = _f_  ∘  _g_ given above becomes:

```haskell
foo = f . g
```

using the built-in composition operator (.) which can be read as _f after g_ or _g composed with f_.

The composition operator  ∘   itself can be defined in Haskell using a [lambda expression](https://en.wikipedia.org/wiki/Lambda_calculus "Lambda calculus"):

```haskell
(.) :: (b -> c) -> (a -> b) -> a -> c
f . g = \x -> f (g x)
```

The first line describes the type of (.) - it takes a pair of functions, _f_,  _g_ and returns a function (the lambda expression on the second line). Note that Haskell doesn't require specification of the exact input and output types of f and g; the a, b, c, and x are placeholders; only the relation between _f_,  _g_ matters (f must accept what g returns). This makes (.) a [polymorphic](https://en.wikipedia.org/wiki/Polymorphism_\(computer_science\) "Polymorphism (computer science)") operator.

#### Lisp
Variants of [Lisp](https://en.wikipedia.org/wiki/Lisp_\(programming_language\) "Lisp (programming language)"), especially [Scheme](https://en.wikipedia.org/wiki/Scheme_\(programming_language\) "Scheme (programming language)"), the [interchangeability of code and data](https://en.wikipedia.org/wiki/Homoiconic "Homoiconic") together with the treatment of functions lend themselves extremely well for a recursive definition of a [variadic](https://en.wikipedia.org/wiki/Variadic "Variadic") compositional operator.

```lisp
(define (compose . fs)
  (if (null? fs) (lambda (x) x) ; if no argument is given, evaluates to the identity function
      (lambda (x) ((car fs) ((apply compose (cdr fs)) x)))))

; examples
(define (add-a-bang str)
  (string-append str "!"))

(define givebang
  (compose string->symbol add-a-bang symbol->string))

(givebang 'set) ; ===> set!

; anonymous composition
((compose sqrt - sqr) 5) ; ===> 0+5i
```

#### APL
Many dialects of [APL](https://en.wikipedia.org/wiki/APL_\(programming_language\) "APL (programming language)") feature built in function composition using the symbol `∘`. This higher-order function extends function composition to [dyadic](https://en.wikipedia.org/wiki/Arity#Binary "Arity") application of the left side function such that `A f∘g B` is `A f g B`.

```apl
foo←f∘g
```

Additionally, you can define function composition:

```apl
o←{⍺⍺ ⍵⍵ ⍵}
```

In dialect that does not support inline definition using braces, the traditional definition is available:

```apl
∇ r←(f o g)x
  r←f g x
∇
```

#### Raku
[Raku](https://en.wikipedia.org/wiki/Raku_\(programming_language\) "Raku (programming language)") like [Haskell](https://en.wikipedia.org/wiki/Haskell_\(programming_language\) "Haskell (programming language)") has a built in function composition operator, the main difference is it is spelled as `∘` or `o`.

```Raku
my &foo = &f ∘ &g;
```

Also like [Haskell](https://en.wikipedia.org/wiki/Haskell_\(programming_language\) "Haskell (programming language)") you could define the operator yourself. In fact the following is the Raku code used to define it in the [Rakudo](https://en.wikipedia.org/wiki/Rakudo "Rakudo") implementation.

```Raku
# the implementation has a slightly different line here because it cheats
proto sub infix:<∘> (&?, &?) is equiv(&[~]) is assoc<left> {*}

multi sub infix:<∘> () { *.self } # allows `[∘] @array` to work when `@array` is empty
multi sub infix:<∘> (&f) { &f }   # allows `[∘] @array` to work when `@array` has one element
multi sub infix:<∘> (&f, &g --> Block) {
    (&f).count > 1
    ?? -> |args { f |g |args }
    !! -> |args { f g |args }
}

# alias it to the "Texas" spelling ( everything is bigger, and ASCII in Texas )
my &infix:<o> := &infix:<∘>;
```

#### Nim
Nim supports [uniform function call syntax](https://en.wikipedia.org/wiki/Uniform_Function_Call_Syntax "Uniform Function Call Syntax"), which allows for arbitrary function composition through the method syntax `.` operator.

```nim
func foo(a: int): string = $a
func bar(a: string, count: int): seq[string] =
  for i in 0 ..< count:
    result.add(a)
func baz(a: seq[string]) =
  for i in a:
    echo i

# equivalent!
echo foo(5).bar(6).baz()
echo baz(bar(6, foo(5)))
```

#### Python
In [Python](https://en.wikipedia.org/wiki/Python_\(programming_language\) "Python (programming language)"), a way to define the composition for any group of functions, is using [reduce](https://en.wikipedia.org/wiki/Fold_\(higher-order_function\) "Fold (higher-order function)") function (use functools.reduce in Python 3):

```python
# Available since Python v2.6
from functools import reduce
from typing import Callable

def compose(*funcs) -> Callable[[int], int]:
    """Compose a group of functions (f(g(h(...)))) into a single composite func."""
    return reduce(lambda f, g: lambda x: f(g(x)), funcs)

# Example
f = lambda x: x + 1
g = lambda x: x * 2
h = lambda x: x - 3

# Call the function x=10 : ((x-3)*2)+1 = 15
print(compose(f, g, h)(10))
```

#### JavaScript
In [JavaScript](https://en.wikipedia.org/wiki/JavaScript "JavaScript") we can define it as a function which takes two functions f and g, and produces a function:

```javascript
function o(f, g) {
    return function(x) {
        return f(g(x));
    }
}

// Alternatively, using the rest operator and lambda expressions in ES2015
const compose = (...fs) => (x) => fs.reduceRight((acc, f) => f(acc), x)
```

#### C# 
In [C#](https://en.wikipedia.org/wiki/C_Sharp_\(programming_language\) "C Sharp (programming language)") we can define it as an Extension method which takes Funcs f and g, and produces a new Func:

```C#
// Call example:
//   var c = f.ComposeWith(g);
//
//   Func<int, bool> g = _ => ...
//   Func<bool, string> f = _ => ...

public static Func<T1, T3> ComposeWith<T1, T2, T3>(this Func<T2, T3> f, Func<T1, T2> g) => x => f(g(x));
```

#### Ruby
Languages like [Ruby](https://en.wikipedia.org/wiki/Ruby_\(programming_language\) "Ruby (programming language)") let you construct a binary operator yourself:

```ruby
class Proc
  def compose(other_fn)
    ->(*as) { other_fn.call(call(*as)) }
  end
  alias_method :+, :compose
end

f = ->(x) { x * 2 }
g = ->(x) { x ** 3 }
(f + g).call(12) # => 13824
```

However, a native function composition operator was introduced in Ruby 2.6:[[4]](https://en.wikipedia.org/wiki/Function_composition_\(computer_science\)#cite_note-4)

```ruby
f = proc{|x| x + 2}
g = proc{|x| x * 3}
(f << g).call(3) # -> 11; identical to f(g(3))
(f >> g).call(3) # -> 15; identical to g(f(3))
```

### Research survey
Notions of composition, including the [principle of compositionality](https://en.wikipedia.org/wiki/Principle_of_compositionality "Principle of compositionality") and [composability](https://en.wikipedia.org/wiki/Composability "Composability"), are so ubiquitous that numerous strands of research have separately evolved. The following is a sampling of the kind of research in which the notion of composition is central.

- [Steele (1994)](https://en.wikipedia.org/wiki/Function_composition_\(computer_science\)#CITEREFSteele1994) directly applied function composition to the assemblage of building blocks known as '[monads](https://en.wikipedia.org/wiki/Monad_\(functional_programming\) "Monad (functional programming)")' in the [Haskell programming language](https://en.wikipedia.org/wiki/Haskell_\(programming_language\) "Haskell (programming language)").
- [Meyer (1988)](https://en.wikipedia.org/wiki/Function_composition_\(computer_science\)#CITEREFMeyer1988) addressed the [software reuse](https://en.wikipedia.org/wiki/Code_reuse "Code reuse") problem in terms of composability.
- [Abadi & Lamport (1993)](https://en.wikipedia.org/wiki/Function_composition_\(computer_science\)#CITEREFAbadiLamport1993) formally defined a proof rule for functional composition that assures a program's safety and liveness.
- [Kracht (2001)](https://en.wikipedia.org/wiki/Function_composition_\(computer_science\)#CITEREFKracht2001) identified a strengthened form of compositionality by placing it into a [semiotic](https://en.wikipedia.org/wiki/Computational_semiotics "Computational semiotics") system and applying it to the problem of structural [ambiguity](https://en.wikipedia.org/wiki/Ambiguity "Ambiguity") frequently encountered in [computational linguistics](https://en.wikipedia.org/wiki/Computational_linguistics "Computational linguistics").
- [van Gelder & Port (1993)](https://en.wikipedia.org/wiki/Function_composition_\(computer_science\)#CITEREFvan_GelderPort1993) examined the role of compositionality in analog aspects of natural language processing.
- According to a review by [Gibbons (2002)](https://en.wikipedia.org/wiki/Function_composition_\(computer_science\)#CITEREFGibbons2002), formal treatment of composition underlies validation of component assembly in visual programming languages like IBM's Visual Age for the [Java](https://en.wikipedia.org/wiki/Java_\(programming_language\) "Java (programming language)") language.

### Large-scale composition]
Whole programs or systems can be treated as functions, which can be readily composed if their inputs and outputs are well-defined. [Pipelines](https://en.wikipedia.org/wiki/Pipeline_\(software\) "Pipeline (software)") allowing easy composition of [filters](https://en.wikipedia.org/wiki/Filter_\(software\) "Filter (software)") were so successful that they became a [design pattern](https://en.wikipedia.org/wiki/Pipeline_\(software\) "Pipeline (software)") of operating systems.

[Imperative procedures](https://en.wikipedia.org/wiki/Imperative_programming "Imperative programming") with side effects violate [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency "Referential transparency") and therefore are not cleanly composable. However if one considers the "state of the world" before and after running the code as its input and output, one gets a clean function. Composition of such functions corresponds to running the procedures one after the other. The [monad](https://en.wikipedia.org/wiki/Monad_\(functional_programming\) "Monad (functional programming)") formalism uses this idea to incorporate side effects and input/output (I/O) into functional languages.

## Object Composition
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), **object composition** and **object aggregation** are closely related ways to combine [objects](https://en.wikipedia.org/wiki/Object_\(computer_science\) "Object (computer science)") or [data types](https://en.wikipedia.org/wiki/Data_type "Data type") into more complex ones. In conversation, the distinction between composition and aggregation is often ignored. Common kinds of compositions are [objects](https://en.wikipedia.org/wiki/Object_\(computer_science\) "Object (computer science)") used in [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming"), [tagged unions](https://en.wikipedia.org/wiki/Tagged_union "Tagged union"), [sets](https://en.wikipedia.org/wiki/Set_\(abstract_data_type\) "Set (abstract data type)"), [sequences](https://en.wikipedia.org/wiki/Sequence "Sequence"), and various [graph](https://en.wikipedia.org/wiki/Graph_\(abstract_data_type\) "Graph (abstract data type)") structures. Object compositions relate to, but are not the same as, data structures.

Object composition refers to the logical or conceptual structure of the information, not the implementation or physical [data structure](https://en.wikipedia.org/wiki/Data_structure "Data structure") used to represent it. For example, a **sequence** differs from a **set** because (among other things) the order of the composed items matters for the former but not the latter. Data structures such as [arrays](https://en.wikipedia.org/wiki/Arrays "Arrays"), [linked lists](https://en.wikipedia.org/wiki/Linked_lists "Linked lists"), [hash tables](https://en.wikipedia.org/wiki/Hash_tables "Hash tables"), and many others can be used to implement either of them. Perhaps confusingly, some of the same terms are used for both data structures and composites. For example, "[binary tree](https://en.wikipedia.org/wiki/Binary_tree "Binary tree")" can refer to either: as a data structure it is a means of accessing a linear sequence of items, and the actual positions of items in the tree are irrelevant (the tree can be internally rearranged however one likes, without changing its meaning). However, as an object composition, the positions are relevant, and changing them would change the meaning (as for example in [cladograms](https://en.wikipedia.org/wiki/Cladogram "Cladogram")).

### Programming technique
[Object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming") is based on using [objects](https://en.wikipedia.org/wiki/Object_\(computer_science\) "Object (computer science)") to [encapsulate](https://en.wikipedia.org/wiki/Encapsulation_\(computer_programming\) "Encapsulation (computer programming)") data and behavior. It uses two main techniques for assembling and composing functionality into more complex ones, sub-typing and object composition. Object composition is about combining objects within compound objects, and at the same time, ensuring the encapsulation of each object by using their well-defined [interface](https://en.wikipedia.org/wiki/Interface_\(object-oriented_programming\) "Interface (object-oriented programming)") without visibility of their internals. In this regard, object composition differs from data structures, which do not enforce encapsulation.

Object composition may also be about a group of multiple related objects, such as a set or a sequence of objects. [Delegation](https://en.wikipedia.org/wiki/Delegation_\(object-oriented_programming\) "Delegation (object-oriented programming)") may enrich composition by forwarding requests or calls made to the enclosing composite object to one of its internal components.

In [class](https://en.wikipedia.org/wiki/Class_\(computer_programming\) "Class (computer programming)")-based and [typed](https://en.wikipedia.org/wiki/Strong_and_weak_typing "Strong and weak typing") programming languages, types can be divided into composite and non-composite types, and composition can be regarded as a relationship between types: an object of a composite type (e.g. _car_) "[has](https://en.wikipedia.org/wiki/Has-a "Has-a")" objects of other types (e.g. _wheel_). When a composite object contains several sub-objects of the same type, they may be assigned to particular [roles](https://en.wikipedia.org/wiki/Role "Role"), often distinguished by names or numbers. For example, a **Point** object might contain 3 numbers, each representing distance along a different axis, such as 'x', 'y', and 'z'. The study of part-whole relationships in general, is [mereology](https://en.wikipedia.org/wiki/Mereology "Mereology").

Composition must be distinguished from [subtyping](https://en.wikipedia.org/wiki/Subtyping "Subtyping"), which is the process of adding detail to a general data type to create a more specific data type. For instance, cars may be a specific type of vehicle: _car_ [is a](https://en.wikipedia.org/wiki/Is-a "Is-a") _vehicle_. Subtyping doesn't describe a relationship between different objects, but instead, says that objects of a type are simultaneously objects of another type. The study of such relationships is [ontology](https://en.wikipedia.org/wiki/Ontology "Ontology").

In [prototype](https://en.wikipedia.org/wiki/Prototype-based_programming "Prototype-based programming")-based programming languages such as [JavaScript](https://en.wikipedia.org/wiki/JavaScript "JavaScript"), objects can dynamically inherit the behaviors from a prototype object at the moment of their instantiation. Composition must be distinguished from prototyping: the newly instantiated object inherits the composition of its prototype, but it may itself be composed on its own.

Composite objects may be represented in storage by co-locating the composed objects, by co-locating references, or in many other ways. The items within a composite object may be referred to as _attributes_, _[fields](https://en.wikipedia.org/wiki/Field_\(computer_science\) "Field (computer science)")_, _members_, _properties_, or other names, and the resulting composition as _[composite type](https://en.wikipedia.org/wiki/Composite_type "Composite type")_, _[storage record](https://en.wikipedia.org/wiki/Storage_record "Storage record")_, _structure_, _[tuple](https://en.wikipedia.org/wiki/Tuple "Tuple")_, or a _user-defined type (UDT)_. For details, see the [aggregation](https://en.wikipedia.org/wiki/Object_composition#Aggregation) section below.

### UML modeling technique

[![A bycicle class represented in UML, with three properties: saddle, wheels and parts, the two last having a multiplicity indicating several objects](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4f/UML_properties_of_a_bicycle.png/220px-UML_properties_of_a_bicycle.png)](https://en.wikipedia.org/wiki/File:UML_properties_of_a_bicycle.png)

Object composition using UML properties to compose objects

In [UML](https://en.wikipedia.org/wiki/Unified_Modeling_Language "Unified Modeling Language") modeling, objects can be conceptually composed, independently of the implementation with a programming language. There are four ways of composing objects in UML: property, association, aggregation and composition:

- A property represents an attribute of the class.
- An association represents a [semantic relationship](https://en.wikipedia.org/wiki/Semantic_relationship "Semantic relationship") between instances of the associated classes. The member-end of an association corresponds to a property of the associated class.
- An aggregation is a kind of association that models a part/whole relationship between an aggregate (whole) and a group of related components (parts).
- A composition, also called a composite aggregation, is a kind of aggregation that models a part/whole relationship between a composite (whole) and a group of exclusively owned parts.

The relationship between the aggregate and its components is a weak "has-a" relationship: The components may be part of several aggregates, may be accessed through other objects without going through the aggregate, and may outlive the aggregate object. The state of the component object still forms part of the aggregate object.

The relationship between the composite and its parts is a strong “has-a” relationship: The composite object has sole "_responsibility for the existence and storage of the composed objects_", the composed object can be part of at most one composite, and "_If a composite object is deleted, all of its part instances that are objects are deleted with it_". Thus in UML, composition has a more narrow meaning than the usual object composition.

[![Association between several bicycles each having one owner; Composition of a bicycle with frame parts which make the bicycle; and aggregation of a bicycle with its wheels, which exist without the bicycle](https://upload.wikimedia.org/wikipedia/commons/thumb/2/21/UML_association%2C_aggregation_and_composition_examples_for_a_bicycle.png/220px-UML_association%2C_aggregation_and_composition_examples_for_a_bicycle.png)](https://en.wikipedia.org/wiki/File:UML_association,_aggregation_and_composition_examples_for_a_bicycle.png)

UML notation for association, composition and aggregation

The graphical notation represents:

- the property as a typed element in the box of the enclosing class,
- the association as a plain line between the associated classes,
- the [aggregation](https://en.wikipedia.org/wiki/Object_composition#Aggregation) as an unfilled diamond on the side of the aggregate and a solid line,

- the composition as a filled diamond on the side of the composite and a solid line.

### Aggregation
Aggregation differs from ordinary composition in that it does not imply ownership. In composition, when the owning object is destroyed, so are the contained objects. In aggregation, this is not necessarily true. For example, a [university](https://en.wikipedia.org/wiki/University "University") owns various departments (e.g., [chemistry](https://en.wikipedia.org/wiki/Chemistry "Chemistry")), and each department has a number of professors. If the university closes, the departments will no longer exist, but the professors in those departments will continue to exist. Therefore, a university can be seen as a composition of departments, whereas departments have an aggregation of professors. In addition, a professor could work in more than one department, but a department could not be part of more than one university.

Composition is usually implemented such that an object contains another object. For example, in [C++](https://en.wikipedia.org/wiki/C%2B%2B "C++"):

```C++
class Professor;  // Defined elsewhere

class Department {
 public:
  Department(const std::string& title): title_(title) {}

 private:
  // Aggregation: |Professors| may outlive the |Department|.
  std::vector<std::weak_ptr<Professor>> members_;
  const std::string title_;
};

class University {
 public:
  University() = default;

 private:
  // Composition: |Department|s exist only as long as the faculty exists.
  std::vector<Department> faculty_ = {
      Department("chemistry"),
      Department("physics"),
      Department("arts"),
  };
};
```

In aggregation, the object may only contain a reference or pointer to the object (and not have [lifetime](https://en.wikipedia.org/wiki/Object_lifetime "Object lifetime") responsibility for it).

Sometimes aggregation is referred to as composition when the distinction between ordinary composition and aggregation is unimportant.

The above code would transform into the following UML Class diagram:

[![](https://upload.wikimedia.org/wikipedia/commons/d/d0/Aggregation-Composition3.png)](https://en.wikipedia.org/wiki/File:Aggregation-Composition3.png)

#### Aggregation in COM
[![](https://upload.wikimedia.org/wikipedia/commons/thumb/d/dc/Simple_COM_aggregation_diagram.svg/220px-Simple_COM_aggregation_diagram.svg.png)](https://en.wikipedia.org/wiki/File:Simple_COM_aggregation_diagram.svg)

Aggregation in COM

In Microsoft's [Component Object Model](https://en.wikipedia.org/wiki/Component_Object_Model "Component Object Model"), aggregation means that an object exports, as if it were their owner, one or several [interfaces](https://en.wikipedia.org/wiki/Interface_\(computer_science\) "Interface (computer science)") of another object it owns. Formally, this is more similar to [composition](https://en.wikipedia.org/wiki/Composition_\(object-oriented_programming\) "Composition (object-oriented programming)") or [encapsulation](https://en.wikipedia.org/wiki/Encapsulation_\(object-oriented_programming\) "Encapsulation (object-oriented programming)") than aggregation. However, instead of implementing the exported interfaces by calling the interfaces of the owned object, the interfaces of the owned object themselves are exported. The owned object is responsible for assuring that methods of those interfaces inherited from [IUnknown](https://en.wikipedia.org/wiki/IUnknown "IUnknown") actually invoke the corresponding methods of the owner. This is to guarantee that the reference count of the owner is correct and all interfaces of the owner are accessible through the exported interface, while no other (private) interfaces of the owned object are accessible.[[5]](https://en.wikipedia.org/wiki/Object_composition#cite_note-5)

### Special forms
#### Containment
Composition that is used to store several instances of the composited data type is referred to as containment. Examples of such containers are [arrays](https://en.wikipedia.org/wiki/Array_\(data_structure\) "Array (data structure)"), [associative arrays](https://en.wikipedia.org/wiki/Associative_array "Associative array"), [binary trees](https://en.wikipedia.org/wiki/Binary_tree "Binary tree"), and [linked lists](https://en.wikipedia.org/wiki/Linked_list "Linked list").

In [UML](https://en.wikipedia.org/wiki/Unified_Modeling_Language "Unified Modeling Language"), containment is depicted with a multiplicity of 0..* or 1..*, indicating that the composite object is composed of an unknown number of instances of the composed class.

#### Recursive composition
Objects can be composed recursively, and their type is then called [recursive type](https://en.wikipedia.org/wiki/Recursive_type "Recursive type"). Examples includes various kinds of [trees](https://en.wikipedia.org/wiki/Tree_\(data_structure\) "Tree (data structure)"), [DAGs](https://en.wikipedia.org/wiki/Directed_acyclic_graph "Directed acyclic graph"), and [graphs](https://en.wikipedia.org/wiki/Graph_\(abstract_data_type\) "Graph (abstract data type)"). Each node in a tree may be a branch or leaf; in other words, each node is a tree at the same time when it belongs to another tree.

In UML, recursive composition is depicted with an association, aggregation or composition of a class with itself.

#### Composite pattern
The [composite design pattern](https://en.wikipedia.org/wiki/Composite_pattern "Composite pattern") is an object-oriented design based on composite types, that combines recursive composition and containment to implement complex part-whole hierarchies.

### Composite types in C
This is an example of composition in [C](https://en.wikipedia.org/wiki/C_\(programming_language\) "C (programming language)").

```C
struct Person
{
  int age;
  char name[20];
  enum {job_seeking, professional, non_professional, retired, student} employment;
};
```

In this example, the primitive (noncomposite) types int, `enum {job_seeking, professional, non_professional, retired, student}` and the composite array type `char[]` are combined to form the composite structure Person. Each Person structure then "has an" age, name, and an employment type.

## Object (Computer Science)
In [software development](https://en.wikipedia.org/wiki/Software_development "Software development"), an **object** is an [entity](https://en.wikipedia.org/wiki/Entity "Entity") that has [state](https://en.wikipedia.org/wiki/State_\(computer_science\) "State (computer science)"), [behavior](https://en.wikipedia.org/wiki/Behavior "Behavior"), and [identity](https://en.wikipedia.org/wiki/Identity_\(object-oriented_programming\) "Identity (object-oriented programming)"). An object can [model](https://en.wikipedia.org/wiki/Model "Model") some part of [reality](https://en.wikipedia.org/wiki/Reality "Reality") or can be an [invention](https://en.wikipedia.org/wiki/Invention "Invention") of the [design process](https://en.wikipedia.org/wiki/Design_process "Design process") whose collaborations with other such objects serve as the mechanisms that provide some higher-level behavior. Put another way, an object represents an individual, identifiable item, unit, or entity, either real or abstract, with a well-defined role in the problem domain.

A [programming language](https://en.wikipedia.org/wiki/Programming_language "Programming language") can be classified based on its support for objects. A language that provides an encapsulation construct for state, behavior, and identity is classified as [object-based](https://en.wikipedia.org/wiki/Object-based_language "Object-based language"). If the language also provides [polymorphism](https://en.wikipedia.org/wiki/Polymorphism_\(computer_science\) "Polymorphism (computer science)") and [inheritance](https://en.wikipedia.org/wiki/Inheritance_\(object-oriented_programming\) "Inheritance (object-oriented programming)") it is classified as [object-oriented](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming"). A language that supports creating an object from a [class](https://en.wikipedia.org/wiki/Class_\(computer_science\) "Class (computer science)") is classified as [class-based](https://en.wikipedia.org/wiki/Class-based_programming "Class-based programming"). A language that supports object creation via a template object is classified as [prototype-based](https://en.wikipedia.org/wiki/Prototype-based_programming "Prototype-based programming").

The concept of object is used in many different software contexts, including:
- Possibly the most common use is [in-memory](https://en.wikipedia.org/wiki/Computer_memory "Computer memory") objects in a [computer program](https://en.wikipedia.org/wiki/Computer_program "Computer program") written in an object-based language.
- [Information systems](https://en.wikipedia.org/wiki/Information_systems "Information systems") can be [modeled](https://en.wikipedia.org/wiki/Object-oriented_analysis_and_design "Object-oriented analysis and design") with objects representing their components and interfaces.
- In the [relational model](https://en.wikipedia.org/wiki/Relational_model "Relational model") of [database](https://en.wikipedia.org/wiki/Database "Database") management, aspects such as [table](https://en.wikipedia.org/wiki/Table_\(database\) "Table (database)") and [column](https://en.wikipedia.org/wiki/Column_\(database\) "Column (database)") may act as objects.
- [Objects](https://en.wikipedia.org/wiki/Distributed_object "Distributed object") of a [distributed computing](https://en.wikipedia.org/wiki/Distributed_computing "Distributed computing") system tend to be larger grained, longer lasting, and more service-oriented than programming objects.

## State (Computer Science)
In [information technology](https://en.wikipedia.org/wiki/Information_technology "Information technology") and [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), a system is described as **stateful** if it is designed to remember preceding events or user interactions; the remembered information is called the **state** of the system.

The set of states a system can occupy is known as its [state space](https://en.wikipedia.org/wiki/State_space "State space"). In a [discrete system](https://en.wikipedia.org/wiki/Discrete_system "Discrete system"), the state space is [countable](https://en.wikipedia.org/wiki/Countable "Countable") and often [finite](https://en.wikipedia.org/wiki/Finite_set "Finite set"). The system's internal behaviour or interaction with its environment consists of separately occurring individual actions or events, such as accepting input or producing output, that may or may not cause the system to change its state. Examples of such systems are [digital logic](https://en.wikipedia.org/wiki/Digital_logic "Digital logic") circuits and components, [automata](https://en.wikipedia.org/wiki/Automata_theory "Automata theory") and [formal language](https://en.wikipedia.org/wiki/Formal_language "Formal language"), [computer programs](https://en.wikipedia.org/wiki/Computer_program "Computer program"), and [computers](https://en.wikipedia.org/wiki/Computer "Computer").

The output of a digital circuit or [deterministic computer program](https://en.wikipedia.org/wiki/Deterministic_algorithm "Deterministic algorithm") at any time is completely determined by its current inputs and its state.

### Digital logic circuit state
[Digital logic](https://en.wikipedia.org/wiki/Digital_logic "Digital logic") circuits can be divided into two types: [combinational logic](https://en.wikipedia.org/wiki/Combinational_logic "Combinational logic"), whose output [signals](https://en.wikipedia.org/wiki/Digital_signal_\(electronics\) "Digital signal (electronics)") are dependent only on its present input signals, and [sequential logic](https://en.wikipedia.org/wiki/Sequential_logic "Sequential logic"), whose outputs are a function of both the current inputs and the past history of inputs. In sequential logic, information from past inputs is stored in electronic memory elements, such as [flip-flops](https://en.wikipedia.org/wiki/Flip-flop_\(electronics\) "Flip-flop (electronics)"). The stored contents of these memory elements, at a given point in time, is collectively referred to as the circuit's _state_ and contains all the information about the past to which the circuit has access.

Since each [binary memory element](https://en.wikipedia.org/wiki/Semiconductor_memory "Semiconductor memory"), such as a flip-flop, has only two possible states, _one_ or _zero_, and there is a finite number of memory elements, a digital circuit has only a certain finite number of possible states. If _**N**_ is the number of binary memory elements in the circuit, the maximum number of states a circuit can have is **2^N**.

### Program state
Similarly, a computer program stores data in [variables](https://en.wikipedia.org/wiki/Variable_\(computer_science\) "Variable (computer science)"), which represent storage locations in the [computer's memory](https://en.wikipedia.org/wiki/Computer_memory "Computer memory"). The contents of these memory locations, at any given point in the program's execution, are called the program's _state_.

A more specialized definition of state is used for computer programs that operate serially or sequentially on [streams of data](https://en.wikipedia.org/wiki/Stream_\(computing\) "Stream (computing)"), such as [parsers](https://en.wikipedia.org/wiki/Parser "Parser"), [firewalls](https://en.wikipedia.org/wiki/Firewall_\(computing\) "Firewall (computing)"), [communication protocols](https://en.wikipedia.org/wiki/Communication_protocol "Communication protocol") and [encryption](https://en.wikipedia.org/wiki/Encryption "Encryption"). Serial programs operate on the incoming data characters or packets sequentially, one at a time. In some of these programs, information about previous data characters or packets received is stored in variables and used to affect the processing of the current character or packet. This is called a [stateful protocol](https://en.wikipedia.org/wiki/Stateful_protocol "Stateful protocol") and the data carried over from the previous processing cycle is called the _state_. In others, the program has no information about the previous data stream and starts fresh with each data input; this is called a [stateless protocol](https://en.wikipedia.org/wiki/Stateless_protocol "Stateless protocol").

[Imperative programming](https://en.wikipedia.org/wiki/Imperative_programming "Imperative programming") is a [programming paradigm](https://en.wikipedia.org/wiki/Programming_paradigm "Programming paradigm") (way of designing a [programming language](https://en.wikipedia.org/wiki/Programming_language "Programming language")) that describes computation in terms of the program state, and of the statements which change the program state. Changes of state are implicit, managed by the program runtime, so that a subroutine has [visibility](https://en.wikipedia.org/wiki/Visibility_\(computer_science\) "Visibility (computer science)") of the changes of state made by other parts of the program, known as [side effects](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\) "Side effect (computer science)").

In [declarative programming](https://en.wikipedia.org/wiki/Declarative_programming "Declarative programming") languages, the program describes the desired results and doesn't specify changes to the state directly.

In [functional programming](https://en.wikipedia.org/wiki/Functional_programming "Functional programming"), state is usually represented with [temporal logic](https://en.wikipedia.org/wiki/Temporal_logic "Temporal logic") as explicit variables that represent the program state at each step of a program execution: a state variable is passed as an [input parameter](https://en.wikipedia.org/wiki/Input_parameter "Input parameter") of a state-transforming function, which returns the updated state as part of its return value. A [pure functional](https://en.wikipedia.org/wiki/Pure_functional "Pure functional") subroutine only has visibility of changes of state represented by the state variables in its scope.

### Finite-state machines
The output of a sequential circuit or computer program at any time is completely determined by its current inputs and current state. Since each [binary](https://en.wikipedia.org/wiki/Binary_digit "Binary digit") memory element has only two possible states, 0 or 1, the total number of different states a circuit can assume is finite, and fixed by the number of memory elements. If there are _N_ binary memory elements, a digital circuit can have at most 2_N_ distinct states. The concept of state is formalized in an abstract mathematical [model of computation](https://en.wikipedia.org/wiki/Model_of_computation "Model of computation") called a [finite-state machine](https://en.wikipedia.org/wiki/Finite-state_machine "Finite-state machine"), used to design both sequential digital circuits and computer programs.

### Examples
An example of an everyday device that has a state is a [television set](https://en.wikipedia.org/wiki/Television_set "Television set"). To change the channel of a TV, the user usually presses a channel up or channel down button on the remote control, which sends a coded message to the set. In order to calculate the new channel that the user desires, the digital tuner in the television must have stored in it the number of the _current channel_ it is on. It then adds one or subtracts one from this number to get the number for the new channel, and adjusts the TV to receive that channel. This new number is then stored as the _current channel_. Similarly, the television also stores a number that controls the level of [volume](https://en.wikipedia.org/wiki/Loudness "Loudness") produced by the speaker. Pressing the volume up or volume down buttons increments or decrements this number, setting a new level of volume. Both the _current channel_ and _current volume_ numbers are part of the TV's state. They are stored in [non-volatile memory](https://en.wikipedia.org/wiki/Non-volatile_memory "Non-volatile memory"), which preserves the information when the TV is turned off, so when it is turned on again the TV will return to its previous station and volume level.

As another example, the state of a [microprocessor](https://en.wikipedia.org/wiki/Microprocessor "Microprocessor") is the contents of all the memory elements in it: the [accumulators](https://en.wikipedia.org/wiki/Accumulator_\(computing\) "Accumulator (computing)"), [storage registers](https://en.wikipedia.org/wiki/Processor_register "Processor register"), [data caches](https://en.wikipedia.org/wiki/Data_cache "Data cache"), and [flags](https://en.wikipedia.org/wiki/Flag_\(computing\) "Flag (computing)"). When computers such as laptops go into [hibernation mode](https://en.wikipedia.org/wiki/Hibernation_mode "Hibernation mode") to save energy by shutting down the processor, the state of the processor is stored on the computer's [hard disk](https://en.wikipedia.org/wiki/Hard_disk "Hard disk"), so it can be restored when the computer comes out of hibernation, and the processor can take up operations where it left off.

## Entity
An **entity** is something that [exists](https://en.wikipedia.org/wiki/Existence "Existence") as itself. It does not need to be of material existence. In particular, [abstractions](https://en.wikipedia.org/wiki/Abstraction "Abstraction") and [legal fictions](https://en.wikipedia.org/wiki/Legal_fiction "Legal fiction") are usually regarded as entities. In general, there is also no presumption that an entity is [animate](https://en.wikipedia.org/wiki/Life "Life"), or [present](https://en.wikipedia.org/wiki/Present "Present").

The term is broad in scope and may refer to animals; natural features such as mountains; inanimate objects such as tables; numbers or sets as symbols written on a paper; human contrivances such as laws, corporations and academic disciplines; or [supernatural](https://en.wikipedia.org/wiki/Supernatural "Supernatural") beings such as gods and spirits.

The adjectival form is _entitative_.

### Etymology
The word _entity_ is derived from the Latin _entitas_, which in turn derives from the Latin _ens_ meaning "being" or "existing" (compare English _[essence](https://en.wikipedia.org/wiki/Essence "Essence")_). _Entity_ may hence literally be taken to mean "thing which exists".

### In philosophy
Ontology is the study of concepts of existence, and of recognition of entities. The words ontic and entity are derived respectively from the ancient Greek and Latin present participles that mean "[being](https://en.wikipedia.org/wiki/Being "Being")".

> In an ontic inquiry... one asks about the properties or the physical relations and structures peculiar to some entity – in the pen's case, for example, we might make the following ontic observations about it: it is black, full of blue ink, and sitting on top of my desk.

### In law and politics
In [law](https://en.wikipedia.org/wiki/Law "Law"), a legal entity is an entity that is capable of bearing legal [rights](https://en.wikipedia.org/wiki/Rights "Rights") and [obligations](https://en.wikipedia.org/wiki/Obligation "Obligation"), such as a [natural person](https://en.wikipedia.org/wiki/Natural_person "Natural person") or an [artificial person](https://en.wikipedia.org/wiki/Legal_person "Legal person") (e.g. business entity or a corporate entity).

In [politics](https://en.wikipedia.org/wiki/Politics "Politics"), _entity_ is used as term for territorial divisions of some countries (e.g. [Bosnia and Herzegovina](https://en.wikipedia.org/wiki/Political_divisions_of_Bosnia_and_Herzegovina "Political divisions of Bosnia and Herzegovina")).

### In medicine
In medicine, a [disease entity](https://en.wikipedia.org/wiki/Disease_entity "Disease entity") is an illness due to a particular definite cause or to a specific pathological process. While a disease entity is not defined by a [syndrome](https://en.wikipedia.org/wiki/Syndrome "Syndrome"), it may or may not be manifest in one or more particular syndromes.

### In computer science
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), an entity is an [object](https://en.wikipedia.org/wiki/Object_\(computer_science\) "Object (computer science)") that has an [identity](https://en.wikipedia.org/wiki/Identifier "Identifier"), which is independent of the changes of its [attributes](https://en.wikipedia.org/wiki/Attribute_\(computing\) "Attribute (computing)"). It represents long-lived information relevant for the users and is usually stored in a [database](https://en.wikipedia.org/wiki/Database "Database").

## Array 
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), an **array** is a [data structure](https://en.wikipedia.org/wiki/Data_structure "Data structure") consisting of a collection of _elements_ ([values](https://en.wikipedia.org/wiki/Value_\(computer_science\) "Value (computer science)") or [variables](https://en.wikipedia.org/wiki/Variable_\(programming\) "Variable (programming)")), of same memory size, each identified by at least one _array index_ or _key_, a collection of which may be a tuple, known as an index tuple. An array is stored such that the position (memory address) of each element can be computed from its index [tuple](https://en.wikipedia.org/wiki/Tuple "Tuple") by a mathematical formula. The simplest type of data structure is a linear array, also called a one-dimensional array.

For example, an array of ten [32-bit](https://en.wikipedia.org/wiki/32-bit "32-bit") (4-byte) integer variables, with indices 0 through 9, may be stored as ten [words](https://en.wikipedia.org/wiki/Word_\(data_type\) "Word (data type)") at memory addresses 2000, 2004, 2008, ..., 2036, (in [hexadecimal](https://en.wikipedia.org/wiki/Hexadecimal "Hexadecimal"): `0x7D0`, `0x7D4`, `0x7D8`, ..., `0x7F4`) so that the element with index _i_ has the address 2000 + (_i_ × 4). The memory address of the first element of an array is called first address, foundation address, or base address.

Because the mathematical concept of a [matrix](https://en.wikipedia.org/wiki/Matrix_\(mathematics\) "Matrix (mathematics)") can be represented as a two-dimensional grid, two-dimensional arrays are also sometimes called "matrices". In some cases the term "vector" is used in computing to refer to an array, although [tuples](https://en.wikipedia.org/wiki/Tuple "Tuple") rather than [vectors](https://en.wikipedia.org/wiki/Vector_space "Vector space") are the more mathematically correct equivalent. [Tables](https://en.wikipedia.org/wiki/Table_\(information\) "Table (information)") are often implemented in the form of arrays, especially [lookup tables](https://en.wikipedia.org/wiki/Lookup_table "Lookup table"); the word "table" is sometimes used as a synonym of array.

Arrays are among the oldest and most important data structures, and are used by almost every program. They are also used to implement many other data structures, such as [lists](https://en.wikipedia.org/wiki/List_\(computing\) "List (computing)") and [strings](https://en.wikipedia.org/wiki/String_\(computer_science\) "String (computer science)"). They effectively exploit the addressing logic of computers. In most modern computers and many [external storage](https://en.wikipedia.org/wiki/External_storage "External storage") devices, the memory is a one-dimensional array of words, whose indices are their addresses. [Processors](https://en.wikipedia.org/wiki/Central_processing_unit "Central processing unit"), especially [vector processors](https://en.wikipedia.org/wiki/Vector_processor "Vector processor"), are often optimized for array operations.

Arrays are useful mostly because the element indices can be computed at [run time](https://en.wikipedia.org/wiki/Run_time_\(program_lifecycle_phase\) "Run time (program lifecycle phase)"). Among other things, this feature allows a single iterative [statement](https://en.wikipedia.org/wiki/Statement_\(programming\) "Statement (programming)") to process arbitrarily many elements of an array. For that reason, the elements of an array data structure are required to have the same size and should use the same data representation. The set of valid index tuples and the addresses of the elements (and hence the element addressing formula) are usually, but not always, fixed while the array is in use.

The term "array" may also refer to an [array data type](https://en.wikipedia.org/wiki/Array_data_type "Array data type"), a kind of [data type](https://en.wikipedia.org/wiki/Data_type "Data type") provided by most [high-level programming languages](https://en.wikipedia.org/wiki/High-level_programming_language "High-level programming language") that consists of a collection of values or variables that can be selected by one or more indices computed at run-time. Array types are often implemented by array structures; however, in some languages they may be implemented by [hash tables](https://en.wikipedia.org/wiki/Hash_table "Hash table"), [linked lists](https://en.wikipedia.org/wiki/Linked_list "Linked list"), [search trees](https://en.wikipedia.org/wiki/Search_tree "Search tree"), or other data structures.

The term is also used, especially in the description of [algorithms](https://en.wikipedia.org/wiki/Algorithm "Algorithm"), to mean [associative array](https://en.wikipedia.org/wiki/Associative_array "Associative array") or "abstract array", a [theoretical computer science](https://en.wikipedia.org/wiki/Theoretical_computer_science "Theoretical computer science") model (an [abstract data type](https://en.wikipedia.org/wiki/Abstract_data_type "Abstract data type") or ADT) intended to capture the essential properties of arrays.

### Applications
Arrays are used to implement mathematical [vectors](https://en.wikipedia.org/wiki/Coordinate_vector "Coordinate vector") and [matrices](https://en.wikipedia.org/wiki/Matrix_\(mathematics\) "Matrix (mathematics)"), as well as other kinds of rectangular tables. Many [databases](https://en.wikipedia.org/wiki/Database "Database"), small and large, consist of (or include) one-dimensional arrays whose elements are [records](https://en.wikipedia.org/wiki/Record_\(computer_science\) "Record (computer science)").

Arrays are used to implement other data structures, such as lists, [heaps](https://en.wikipedia.org/wiki/Heap_\(data_structure\) "Heap (data structure)"), [hash tables](https://en.wikipedia.org/wiki/Hash_table "Hash table"), [deques](https://en.wikipedia.org/wiki/Double-ended_queue "Double-ended queue"), [queues](https://en.wikipedia.org/wiki/Queue_\(data_structure\) "Queue (data structure)"), [stacks](https://en.wikipedia.org/wiki/Stack_\(data_structure\) "Stack (data structure)"), [strings](https://en.wikipedia.org/wiki/String_\(computer_science\) "String (computer science)"), and VLists. Array-based implementations of other data structures are frequently simple and space-efficient ([implicit data structures](https://en.wikipedia.org/wiki/Implicit_data_structure "Implicit data structure")), requiring little space [overhead](https://en.wikipedia.org/wiki/Overhead_\(computing\) "Overhead (computing)"), but may have poor space complexity, particularly when modified, compared to tree-based data structures (compare a [sorted array](https://en.wikipedia.org/wiki/Sorted_array "Sorted array") to a [search tree](https://en.wikipedia.org/wiki/Search_tree "Search tree")).

One or more large arrays are sometimes used to emulate in-program [dynamic memory allocation](https://en.wikipedia.org/wiki/Dynamic_memory_allocation "Dynamic memory allocation"), particularly [memory pool](https://en.wikipedia.org/wiki/Memory_pool "Memory pool") allocation. Historically, this has sometimes been the only way to allocate "dynamic memory" portably.

Arrays can be used to determine partial or complete [control flow](https://en.wikipedia.org/wiki/Control_flow "Control flow") in programs, as a compact alternative to (otherwise repetitive) multiple `IF` statements. They are known in this context as [control tables](https://en.wikipedia.org/wiki/Control_table "Control table") and are used in conjunction with a purpose-built interpreter whose [control flow](https://en.wikipedia.org/wiki/Control_flow "Control flow") is altered according to values contained in the array. The array may contain [subroutine](https://en.wikipedia.org/wiki/Subroutine "Subroutine") [pointers](https://en.wikipedia.org/wiki/Pointer_\(computer_programming\) "Pointer (computer programming)") (or relative subroutine numbers that can be acted upon by [SWITCH](https://en.wikipedia.org/wiki/Switch_statement "Switch statement") statements) that direct the path of the execution.

### Element identifier and addressing formulas
When data objects are stored in an array, individual objects are selected by an index that is usually a non-negative [scalar](https://en.wikipedia.org/wiki/Scalar_\(computing\) "Scalar (computing)") [integer](https://en.wikipedia.org/wiki/Integer "Integer"). Indexes are also called subscripts. An index _maps_ the array value to a stored object.

There are three ways in which the elements of an array can be indexed:

0 (_[zero-based indexing](https://en.wikipedia.org/wiki/Zero-based_numbering "Zero-based numbering")_)

The first element of the array is indexed by subscript of 0.
1 (_one-based indexing_)

The first element of the array is indexed by subscript of 1.

n (_n-based indexing_)

The base index of an array can be freely chosen. Usually programming languages allowing _n-based indexing_ also allow negative index values and other [scalar](https://en.wikipedia.org/wiki/Scalar_\(computing\) "Scalar (computing)") data types like [enumerations](https://en.wikipedia.org/wiki/Enumerated_type "Enumerated type"), or [characters](https://en.wikipedia.org/wiki/Character_\(computing\) "Character (computing)") may be used as an array index.

Using zero based indexing is the design choice of many influential programming languages, including [C](https://en.wikipedia.org/wiki/C_\(programming_language\) "C (programming language)"), [Java](https://en.wikipedia.org/wiki/Java_\(programming_language\) "Java (programming language)") and [Lisp](https://en.wikipedia.org/wiki/Lisp_\(programming_language\) "Lisp (programming language)"). This leads to simpler implementation where the subscript refers to an offset from the starting position of an array, so the first element has an offset of zero.

Arrays can have multiple dimensions, thus it is not uncommon to access an array using multiple indices. For example, a two-dimensional array `A` with three rows and four columns might provide access to the element at the 2nd row and 4th column by the expression `A[1][3]` in the case of a zero-based indexing system. Thus two indices are used for a two-dimensional array, three for a three-dimensional array, and _n_ for an _n_-dimensional array.

The number of indices needed to specify an element is called the dimension, dimensionality, or [rank](https://en.wikipedia.org/wiki/Rank_\(computer_programming\) "Rank (computer programming)") of the array.

In standard arrays, each index is restricted to a certain range of consecutive integers (or consecutive values of some [enumerated type](https://en.wikipedia.org/wiki/Enumerated_type "Enumerated type")), and the address of an element is computed by a "linear" formula on the indices.

#### One-dimensional arrays

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/4/40/1D_array_diagram.svg/250px-1D_array_diagram.svg.png)](https://en.wikipedia.org/wiki/File:1D_array_diagram.svg)

Diagram of a typical 1D array

A one-dimensional array (or single dimension array) is a type of linear array. Accessing its elements involves a single subscript which can either represent a row or column index.

As an example consider the C declaration `int anArrayName[10];` which declares a one-dimensional array of ten integers. Here, the array can store ten elements of type `int` . This array has indices starting from zero through nine. For example, the expressions `anArrayName[0]` and `anArrayName[9]` are the first and last elements respectively.

For a vector with linear addressing, the element with index _i_ is located at the address _B_ + _c_ · _i_, where _B_ is a fixed _base address_ and _c_ a fixed constant, sometimes called the _address increment_ or _stride_.

If the valid element indices begin at 0, the constant _B_ is simply the address of the first element of the array. For this reason, the [C programming language](https://en.wikipedia.org/wiki/C_\(programming_language\) "C (programming language)") specifies that array indices always begin at 0; and many programmers will call that element "[zeroth](https://en.wikipedia.org/wiki/Zero-based_numbering "Zero-based numbering")" rather than "first".

However, one can choose the index of the first element by an appropriate choice of the base address _B_. For example, if the array has five elements, indexed 1 through 5, and the base address _B_ is replaced by _B_ + 30_c_, then the indices of those same elements will be 31 to 35. If the numbering does not start at 0, the constant _B_ may not be the address of any element.

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f3/2D_array_diagram.svg/250px-2D_array_diagram.svg.png)](https://en.wikipedia.org/wiki/File:2D_array_diagram.svg)

Diagram of a typical 2D array

#### Multidimensional arrays
[![](https://upload.wikimedia.org/wikipedia/commons/thumb/9/97/3D_array_diagram.svg/250px-3D_array_diagram.svg.png)](https://en.wikipedia.org/wiki/File:3D_array_diagram.svg)

Diagram of a typical 3D array

For a multidimensional array, the element with indices _i_,_j_ would have address _B_ + _c_ · _i_ + _d_ · _j_, where the coefficients _c_ and _d_ are the _row_ and _column address increments_, respectively.

More generally, in a _k_-dimensional array, the address of an element with indices _i_1, _i_2, ..., _i__k_ is

_B_ + _c_1 · _i_1 + _c_2 · _i_2 + … + _c__k_ · _i__k_.

For example: int a[2][3];

This means that array a has 2 rows and 3 columns, and the array is of integer type. Here we can store 6 elements they will be stored linearly but starting from first row linear then continuing with second row. The above array will be stored as a11, a12, a13, a21, a22, a23.

This formula requires only _k_ multiplications and _k_ additions, for any array that can fit in memory. Moreover, if any coefficient is a fixed power of 2, the multiplication can be replaced by [bit shifting](https://en.wikipedia.org/wiki/Bitwise_operation "Bitwise operation").

The coefficients _c__k_ must be chosen so that every valid index tuple maps to the address of a distinct element.

If the minimum legal value for every index is 0, then _B_ is the address of the element whose indices are all zero. As in the one-dimensional case, the element indices may be changed by changing the base address _B_. Thus, if a two-dimensional array has rows and columns indexed from 1 to 10 and 1 to 20, respectively, then replacing _B_ by _B_ + _c_1 − 3_c_2 will cause them to be renumbered from 0 through 9 and 4 through 23, respectively. Taking advantage of this feature, some languages (like FORTRAN 77) specify that array indices begin at 1, as in mathematical tradition while other languages (like Fortran 90, Pascal and Algol) let the user choose the minimum value for each index.

#### Dope vectors
The addressing formula is completely defined by the dimension _d_, the base address _B_, and the increments _c_1, _c_2, ..., _c__k_. It is often useful to pack these parameters into a record called the array's descriptor, stride vector, or [dope vector](https://en.wikipedia.org/wiki/Dope_vector "Dope vector"). The size of each element, and the minimum and maximum values allowed for each index may also be included in the dope vector. The dope vector is a complete [handle](https://en.wikipedia.org/wiki/Handle_\(computing\) "Handle (computing)") for the array, and is a convenient way to pass arrays as arguments to [procedures](https://en.wikipedia.org/wiki/Subroutine "Subroutine"). Many useful [array slicing](https://en.wikipedia.org/wiki/Array_slicing "Array slicing") operations (such as selecting a sub-array, swapping indices, or reversing the direction of the indices) can be performed very efficiently by manipulating the dope vector.

#### Compact layouts
Often the coefficients are chosen so that the elements occupy a contiguous area of memory. However, that is not necessary. Even if arrays are always created with contiguous elements, some array slicing operations may create non-contiguous sub-arrays from them.

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4d/Row_and_column_major_order.svg/250px-Row_and_column_major_order.svg.png)](https://en.wikipedia.org/wiki/File:Row_and_column_major_order.svg)

Illustration of row- and column-major order

There are two systematic compact layouts for a two-dimensional array. For example, consider the matrix

A=[123456789].![{\displaystyle A={\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e5ce1bbaec43174abf6887a29b8f3a3612d0b1f5)

In the row-major order layout (adopted by C for statically declared arrays), the elements in each row are stored in consecutive positions and all of the elements of a row have a lower address than any of the elements of a consecutive row:

|     |     |     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   |

In column-major order (traditionally used by Fortran), the elements in each column are consecutive in memory and all of the elements of a column have a lower address than any of the elements of a consecutive column:

|   |   |   |   |   |   |   |   |   |
|---|---|---|---|---|---|---|---|---|
|1|4|7|2|5|8|3|6|9|

For arrays with three or more indices, "row major order" puts in consecutive positions any two elements whose index tuples differ only by one in the _last_ index. "Column major order" is analogous with respect to the _first_ index.

In systems which use [processor cache](https://en.wikipedia.org/wiki/Processor_cache "Processor cache") or [virtual memory](https://en.wikipedia.org/wiki/Virtual_memory "Virtual memory"), scanning an array is much faster if successive elements are stored in consecutive positions in memory, rather than sparsely scattered. This is known as spatial locality, which is a type of [locality of reference](https://en.wikipedia.org/wiki/Locality_of_reference "Locality of reference"). Many algorithms that use multidimensional arrays will scan them in a predictable order. A programmer (or a sophisticated compiler) may use this information to choose between row- or column-major layout for each array. For example, when computing the product _A_·_B_ of two matrices, it would be best to have _A_ stored in row-major order, and _B_ in column-major order.

#### Resizing
Static arrays have a size that is fixed when they are created and consequently do not allow elements to be inserted or removed. However, by allocating a new array and copying the contents of the old array to it, it is possible to effectively implement a _dynamic_ version of an array; see [dynamic array](https://en.wikipedia.org/wiki/Dynamic_array "Dynamic array"). If this operation is done infrequently, insertions at the end of the array require only amortized constant time.

Some array data structures do not reallocate storage, but do store a count of the number of elements of the array in use, called the count or size. This effectively makes the array a [dynamic array](https://en.wikipedia.org/wiki/Dynamic_array "Dynamic array") with a fixed maximum size or capacity; [Pascal strings](https://en.wikipedia.org/wiki/Pascal_string "Pascal string") are examples of this.

#### Non-linear formulas

More complicated (non-linear) formulas are occasionally used. For a compact two-dimensional [triangular array](https://en.wikipedia.org/wiki/Triangular_array "Triangular array"), for instance, the addressing formula is a polynomial of degree 2.

### Efficiency
Both _store_ and _select_ take (deterministic worst case) [constant time](https://en.wikipedia.org/wiki/Constant_time "Constant time"). Arrays take linear ([O](https://en.wikipedia.org/wiki/Big-O_notation "Big-O notation")(_n_)) space in the number of elements _n_ that they hold.

In an array with element size _k_ and on a machine with a cache line size of B bytes, iterating through an array of _n_ elements requires the minimum of ceiling(_nk_/B) cache misses, because its elements occupy contiguous memory locations. This is roughly a factor of B/_k_ better than the number of cache misses needed to access _n_ elements at random memory locations. As a consequence, sequential iteration over an array is noticeably faster in practice than iteration over many other data structures, a property called [locality of reference](https://en.wikipedia.org/wiki/Locality_of_reference "Locality of reference") (this does _not_ mean however, that using a [perfect hash](https://en.wikipedia.org/wiki/Perfect_hash_function "Perfect hash function") or [trivial hash](https://en.wikipedia.org/wiki/Hash_function#Trivial_hash_function "Hash function") within the same (local) array, will not be even faster - and achievable in [constant time](https://en.wikipedia.org/wiki/Constant_time "Constant time")). Libraries provide low-level optimized facilities for copying ranges of memory (such as [memcpy](https://en.wikipedia.org/wiki/String.h "String.h")) which can be used to move [contiguous](https://en.wikipedia.org/wiki/Contiguous_data_storage "Contiguous data storage") blocks of array elements significantly faster than can be achieved through individual element access. The speedup of such optimized routines varies by array element size, architecture, and implementation.

Memory-wise, arrays are compact data structures with no per-element [overhead](https://en.wikipedia.org/wiki/Computational_overhead "Computational overhead"). There may be a per-array overhead (e.g., to store index bounds) but this is language-dependent. It can also happen that elements stored in an array require _less_ memory than the same elements stored in individual variables, because several array elements can be stored in a single [word](https://en.wikipedia.org/wiki/Word_\(data_type\) "Word (data type)"); such arrays are often called _packed_ arrays. An extreme (but commonly used) case is the [bit array](https://en.wikipedia.org/wiki/Bit_array "Bit array"), where every bit represents a single element. A single [octet](https://en.wikipedia.org/wiki/Octet_\(computing\) "Octet (computing)") can thus hold up to 256 different combinations of up to 8 different conditions, in the most compact form.

Array accesses with statically predictable access patterns are a major source of [data parallelism](https://en.wikipedia.org/wiki/Data_parallelism "Data parallelism").

#### Comparison with other data structures
[Dynamic arrays](https://en.wikipedia.org/wiki/Dynamic_array "Dynamic array") or growable arrays are similar to arrays but add the ability to insert and delete elements; adding and deleting at the end is particularly efficient. However, they reserve linear ([Θ](https://en.wikipedia.org/wiki/Big-O_notation#Family_of_Bachmann%E2%80%93Landau_notations "Big-O notation")(_n_)) additional storage, whereas arrays do not reserve additional storage.

[Associative arrays](https://en.wikipedia.org/wiki/Associative_array "Associative array") provide a mechanism for array-like functionality without huge storage overheads when the index values are sparse. For example, an array that contains values only at indexes 1 and 2 billion may benefit from using such a structure. Specialized associative arrays with integer keys include [Patricia tries](https://en.wikipedia.org/wiki/Radix_tree "Radix tree"), [Judy arrays](https://en.wikipedia.org/wiki/Judy_array "Judy array"), and [van Emde Boas trees](https://en.wikipedia.org/wiki/Van_Emde_Boas_tree "Van Emde Boas tree").

[Balanced trees](https://en.wikipedia.org/wiki/Self-balancing_binary_search_tree "Self-balancing binary search tree") require O(log _n_) time for indexed access, but also permit inserting or deleting elements in O(log _n_) time, whereas growable arrays require linear (Θ(_n_)) time to insert or delete elements at an arbitrary position.

[Linked lists](https://en.wikipedia.org/wiki/Linked_list "Linked list") allow constant time removal and insertion in the middle but take linear time for indexed access. Their memory use is typically worse than arrays, but is still linear.

[![A two-dimensional array stored as a one-dimensional array of one-dimensional arrays (rows).](https://upload.wikimedia.org/wikipedia/commons/thumb/0/01/Array_of_array_storage.svg/120px-Array_of_array_storage.svg.png)](https://en.wikipedia.org/wiki/File:Array_of_array_storage.svg "A two-dimensional array stored as a one-dimensional array of one-dimensional arrays (rows).")

An [Iliffe vector](https://en.wikipedia.org/wiki/Iliffe_vector "Iliffe vector") is an alternative to a multidimensional array structure. It uses a one-dimensional array of [references](https://en.wikipedia.org/wiki/Reference_\(computer_science\) "Reference (computer science)") to arrays of one dimension less. For two dimensions, in particular, this alternative structure would be a vector of pointers to vectors, one for each row(pointer on c or c++). Thus an element in row _i_ and column _j_ of an array _A_ would be accessed by double indexing (_A_[_i_][_j_] in typical notation). This alternative structure allows [jagged arrays](https://en.wikipedia.org/wiki/Jagged_array "Jagged array"), where each row may have a different size—or, in general, where the valid range of each index depends on the values of all preceding indices. It also saves one multiplication (by the column address increment) replacing it by a bit shift (to index the vector of row pointers) and one extra memory access (fetching the row address), which may be worthwhile in some architectures.

### Dimension
The _dimension_ of an array is the number of indices needed to select an element. Thus, if the array is seen as a function on a set of possible index combinations, it is the dimension of the space of which its domain is a discrete subset. Thus a one-dimensional array is a list of data, a two-dimensional array is a rectangle of data, a three-dimensional array a block of data, etc.

This should not be confused with the dimension of the set of all matrices with a given domain, that is, the number of elements in the array. For example, an array with 5 rows and 4 columns is two-dimensional, but such matrices form a 20-dimensional space. Similarly, a three-dimensional vector can be represented by a one-dimensional array of size three.

## Describing Parameters
In OpenAPI 3.0, parameters are defined in the `parameters` section of an operation or path. To describe a parameter, you specify its `name`, location (`in`), data type (defined by either `schema` or `content`) and other attributes, such as `description` or `required`. Here is an example:

```
paths:
  /users/{userId}:
    get:
      summary: Get a user by ID
      parameters:
        - in: path
          name: userId
          schema:
            type: integer
          required: true
          description: Numeric ID of the user to get
```

Note that `parameters` is an array, so, in YAML, each parameter definition must be listed with a dash (`-`) in front of it.

### Parameter Types
OpenAPI 3.0 distinguishes between the following parameter types based on the parameter location. The location is determined by the parameter’s `in` key, for example, `in: query` or `in: path`.

- [path parameters](https://swagger.io/docs/specification/v3_0/describing-parameters/#path-parameters), such as `/users/{id}`
- [query parameters](https://swagger.io/docs/specification/v3_0/describing-parameters/#query-parameters), such as `/users?role=admin`
- [header parameters](https://swagger.io/docs/specification/v3_0/describing-parameters/#header-parameters), such as `X-MyHeader: Value`
- [cookie parameters](https://swagger.io/docs/specification/v3_0/describing-parameters/#cookie-parameters), which are passed in the `Cookie` header, such as `Cookie: debug=0; csrftoken=BUSe35dohU3O1MZvDCU`

### Path Parameters
Path parameters are variable parts of a URL path. They are typically used to point to a specific resource within a collection, such as a user identified by ID. A URL can have several path parameters, each denoted with curly braces `{ }`.

```
GET /users/{id}
GET /cars/{carId}/drivers/{driverId}
GET /report.{format}
```

Each path parameter must be substituted with an actual value when the client makes an API call. In OpenAPI, a path parameter is defined using `in: path`. The parameter name must be the same as specified in the path. Also remember to add `required: true`, because path parameters are always required. For example, the `/users/{id}` endpoint would be described as:

```
paths:
  /users/{id}:
    get:
      parameters:
        - in: path
          name: id # Note the name is the same as in the path
          required: true
          schema:
            type: integer
            minimum: 1
          description: The user ID
```

Path parameters containing arrays and objects can be serialized in different ways:

- path-style expansion (matrix) – semicolon-prefixed, such as `/map/point;x=50;y=20`
- label expansion – dot-prefixed, such as `/color.R=100.G=200.B=150`
- simple-style – comma-delimited, such as `/users/12,34,56`

The serialization method is specified by the `style` and `explode` keywords. To learn more, see [Parameter Serialization](https://swagger.io/docs/specification/serialization/).

### Query Parameters
Query parameters are the most common type of parameters. They appear at the end of the request URL after a question mark (`?`), with different `name=value`/`key=value` pairs separated by ampersands (`&`). Query parameters can be required and optional.

```
GET /pets/findByStatus?status=available
GET /notes?offset=100&limit=50
```

Use `in: query` to denote query parameters:

```
parameters:
  - in: query
    name: offset
    schema:
      type: integer
    description: The number of items to skip before starting to collect the result set
  - in: query
    name: limit
    schema:
      type: integer
    description: The numbers of items to return
```

**Note:** To describe API keys passed as query parameters, use `securitySchemes` and `security` instead. See [API Keys](https://swagger.io/docs/specification/authentication/api-keys/).

Query parameters can be primitive values, arrays and objects. OpenAPI 3.0 provides several ways to serialize objects and arrays in the query string.

Arrays can be serialized as:

- `form` – `/products?color=blue,green,red` or `/products?color=blue&color=green`, depending on the `explode` keyword
- `spaceDelimited` (same as `collectionFormat: ssv` in OpenAPI 2.0) – `/products?color=blue%20green%20red`
- `pipeDelimited` (same as `collectionFormat: pipes` in OpenAPI 2.0) – `/products?color=blue|green|red`

Objects can be serialized as:

- `form` – `/points?color=R,100,G,200,B,150` or `/points?R=100&G=200&B=150`, depending on the `explode` keyword
- `deepObject` – `/points?color[R]=100&color[G]=200&color[B]=150`

The serialization method is specified by the `style` and `explode` keywords. To learn more, see [Parameter Serialization](https://swagger.io/docs/specification/serialization/).

#### Reserved Characters in Query Parameters
[RFC 3986](https://tools.ietf.org/html/rfc3986#section-2.2) defines a set of reserved characters `:/?#[]@!$&'()*+,;=` that are used as URI component delimiters. When these characters need to be used literally in a query parameter value, they are usually percent-encoded. For example, `/` is encoded as `%2F` (or `%2f`), so that the parameter value `quotes/h2g2.txt` would be sent as

```
GET /file?path=quotes%2Fh2g2.txt
```

If you want a query parameter that is not percent-encoded, add `allowReserved: true` to the parameter definition:

```
parameters:
  - in: query
    name: path
    required: true
    schema:
      type: string
    allowReserved: true # <-----
```

In this case, the parameter value would be sent like so:

```
GET /file?path=quotes/h2g2.txt
```

### Header Parameters
An API call may require that custom headers be sent with an HTTP request. OpenAPI lets you define custom request headers as `in: header` parameters. For example, suppose, a call to `GET /ping` requires the `X-Request-ID` header:

```
GET /ping HTTP/1.1
Host: example.com
X-Request-ID: 77e1c83b-7bb0-437b-bc50-a7a58e5660ac
```

Using OpenAPI 3.0, you would define this operation as follows:

```
paths:
  /ping:
    get:
      summary: Checks if the server is alive
      parameters:
        - in: header
          name: X-Request-ID
          schema:
            type: string
            format: uuid
          required: true
```

In a similar way, you can define [custom response headers](https://swagger.io/docs/specification/describing-responses/#response-headers). Header parameter can be primitives, arrays and objects. Arrays and objects are serialized using the `simple` style. For more information, see [Parameter Serialization](https://swagger.io/docs/specification/serialization/).

**Note:** Header parameters named `Accept`, `Content-Type` and `Authorization` are not allowed. To describe these headers, use the corresponding OpenAPI keywords:

|Header|OpenAPI keywords|For more information, see...|
|---|---|---|
|`Content-Type`|Request content type: `requestBody.content.<media-type>`  <br>  <br>Response content type: `responses.<code>.content.<media-type>`|[Describing Request Body](https://swagger.io/docs/specification/describing-request-body/describing-request-body/),  <br>[Describing Responses](https://swagger.io/docs/specification/describing-responses/),  <br>[Media Types](https://swagger.io/docs/specification/media-types)|
|`Accept`|`responses.<code>.content.<media-type>`|[Describing Responses](https://swagger.io/docs/specification/describing-responses/),  <br>[Media Types](https://swagger.io/docs/specification/media-types)|
|`Authorization`|`securitySchemes`, `security`|[Authentication](https://swagger.io/docs/specification/authentication/)|

### Cookie Parameters
Operations can also pass parameters in the `Cookie` header, as `Cookie: name=value`. Multiple cookie parameters are sent in the same header, separated by a semicolon and space.

```
GET /api/users
Host: example.com
Cookie: debug=0; csrftoken=BUSe35dohU3O1MZvDCUOJ
```

Use `in: cookie` to define cookie parameters:

```
parameters:
  - in: cookie
    name: debug
    schema:
      type: integer
      enum: [0, 1]
      default: 0
  - in: cookie
    name: csrftoken
    schema:
      type: string
```

Cookie parameters can be primitive values, arrays and objects. Arrays and objects are serialized using the `form` style. For more information, see [Parameter Serialization](https://swagger.io/docs/specification/serialization/).

**Note:** To define cookie authentication, use [API keys](https://swagger.io/docs/specification/authentication/api-keys/) instead.

### Required and Optional Parameters
By default, OpenAPI treats all request parameters as optional. You can add `required: true` to mark a parameter as required. Note that path parameters must have `required: true`, because they are always required.

```
parameters:
  - in: path
    name: userId
    schema:
      type: integer
    required: true # <----------
    description: Numeric ID of the user to get.
```

### schema vs content
To describe the parameter contents, you can use either the `schema` or `content` keyword. They are mutually exclusive and used in different scenarios. In most cases, you would use **`schema`**. It lets you describe primitive values, as well as simple arrays and objects serialized into a string. The serialization method for array and object parameters is defined by the `style` and `explode` keywords used in that parameter.

```
parameters:
  - in: query
    name: color
    schema:
      type: array
      items:
        type: string

    # Serialize as color=blue,black,brown (default)
    style: form
    explode: false
```

**`content`** is used in complex serialization scenarios that are not covered by `style` and `explode`. For example, if you need to send a JSON string in the query string like so:

```
filter={"type":"t-shirt","color":"blue"}
```

In this case, you need to wrap the parameter `schema` into `content/<media-type>` as shown below. The `schema` defines the parameter data structure, and the media type (in this example – `application/json`) serves as a reference to an external specification that describes the serialization format.

```
parameters:
  - in: query
    name: filter

    # Wrap 'schema' into 'content.<media-type>'
    content:
      application/json: # <---- media type indicates how to serialize / deserialize the parameter content
        schema:
          type: object
          properties:
            type:
              type: string
            color:
              type: string
```

**Note for Swagger UI and Swagger Editor users:** Parameters with `content` are supported in Swagger UI 3.23.7+ and Swagger Editor 3.6.34+.

### Default Parameter Values
Use the `default` keyword in the parameter schema to specify the default value for an optional parameter. The default value is the one that the server uses if the client does not supply the parameter value in the request. The value type must be the same as the parameter’s data type. A typical example is paging parameters such as `offset` and `limit`:

```
GET /users
GET /users?offset=30&limit=10
```

Assuming `offset` defaults to 0 and `limit` defaults to 20 and ranges from 0 to 100, you would define these parameters as:

```
parameters:
  - in: query
    name: offset
    schema:
      type: integer
      minimum: 0
      default: 0
    required: false
    description: The number of items to skip before starting to collect the result set.
  - in: query
    name: limit
    schema:
      type: integer
      minimum: 1
      maximum: 100
      default: 20
    required: false
    description: The number of items to return.
```

#### Common Mistakes
There are two common mistakes when using the `default` keyword:

- Using `default` with `required` parameters or properties, for example, with path parameters. This does not make sense – if a value is required, the client must always send it, and the default value is never used.
- Using `default` to specify a sample value. This is not intended use of `default` and can lead to unexpected behavior in some Swagger tools. Use the `example` or `examples` keyword for this purpose instead. See [Adding Examples](https://swagger.io/docs/specification/adding-examples/).

### Enum Parameters
You can restrict a parameter to a fixed set of values by adding the `enum` to the parameter’s `schema`. The enum values must be of the same type as the parameter data type.

```
parameters:
  - in: query
    name: status
    schema:
      type: string
      enum:
        - available
        - pending
        - sold
```

### Constant Parameters
You can define a constant parameter as a required parameter with only one possible value:

```
parameters:
  - in: query
    name: rel_date
    required: true
    schema:
      type: string
      enum:
        - now
```

The `enum` property specifies possible values. In this example, only one value can be used, and this will be the only value available in the Swagger UI for the user to choose from.

**Note:** A constant parameter is not the same as the [default parameter value](https://swagger.io/docs/specification/v3_0/describing-parameters/#default). A constant parameter is always sent by the client, whereas the default value is something that the server uses if the parameter is not sent by the client.

### Empty-Valued and Nullable Parameters
Query string parameters may only have a name and no value, like so:

```
GET /foo?metadata
```

Use `allowEmptyValue` to describe such parameters:

```
parameters:
  - in: query
    name: metadata
    schema:
      type: boolean
    allowEmptyValue: true # <-----
```

OpenAPI 3.0 also supports `nullable` in schemas, allowing operation parameters to have the `null` value. For example, the following schema corresponds to `int?` in C# and `java.lang.Integer` in Java:

```
schema:
  type: integer
  format: int32
  nullable: true
```

**Note:** `nullable` is not the same as an optional parameter or an empty-valued parameter. `nullable` means the parameter value can be `null`. Specific implementations may choose to map an absent or empty-valued parameter to `null`, but strictly speaking these are not the same thing.

### Parameter Examples
You can specify an `example` or multiple `examples` for a parameter. The example value should match the parameter schema. Single example:

```
parameters:
  - in: query
    name: limit
    schema:
      type: integer
      minimum: 1
    example: 20
```

Multiple named examples:

```
parameters:
  - in: query
    name: ids
    description: One or more IDs
    required: true
    schema:
      type: array
      items:
        type: integer
    style: form
    explode: false
    examples:
      oneId:
        summary: Example of a single ID
        value: [5] # ?ids=5
      multipleIds:
        summary: Example of multiple IDs
        value: [1, 5, 7] # ?ids=1,5,7
```

### Deprecated Parameters
Use `deprecated: true` to mark a parameter as deprecated.

```
- in: query
  name: format
  required: true
  schema:
    type: string
    enum: [json, xml, yaml]
  deprecated: true
  description: Deprecated, use the appropriate `Accept` header instead.
```

### Common Parameters
#### Common Parameters for All Methods of a Path
Parameters shared by all operations of a path can be defined on the path level instead of the operation level. Path-level parameters are inherited by all operations of that path. A typical use case are the GET/PUT/PATCH/DELETE operations that manipulate a resource accessed via a path parameter.

```
paths:
  /user/{id}:
    parameters:
      - in: path
        name: id
        schema:
          type: integer
        required: true
        description: The user ID
    get:
      summary: Gets a user by ID
      ...
    patch:
      summary: Updates an existing user with the specified ID
      ...
    delete:
      summary: Deletes the user with the specified ID
      ...
```

Any extra parameters defined at the operation level are used together with path-level parameters:

```
paths:
  /users/{id}:
    parameters:
      - in: path
        name: id
        schema:
          type: integer
        required: true
        description: The user ID.

    # GET/users/{id}?metadata=true
    get:
      summary: Gets a user by ID
      # Note we only define the query parameter, because the {id} is defined at the path level.
      parameters:
        - in: query
          name: metadata
          schema:
            type: boolean
          required: false
          description: If true, the endpoint returns only the user metadata.
      responses:
        "200":
          description: OK
```

Specific path-level parameters can be overridden on the operation level, but cannot be removed.

```
paths:
  /users/{id}:
    parameters:
      - in: path
        name: id
        schema:
          type: integer
        required: true
        description: The user ID.

    # DELETE /users/{id} - uses a single ID.
    # Reuses the {id} parameter definition from the path level.
    delete:
      summary: Deletes the user with the specified ID.
      responses:
        "204":
          description: User was deleted.

    # GET /users/id1,id2,id3 - uses one or more user IDs.
    # Overrides the path-level {id} parameter.
    get:
      summary: Gets one or more users by ID.
      parameters:
        - in: path
          name: id
          required: true
          description: A comma-separated list of user IDs.
          schema:
            type: array
            items:
              type: integer
            minItems: 1
          explode: false
          style: simple
      responses:
        "200":
          description: OK
```

#### Common Parameters for Various Paths
Different API paths may have common parameters, such as pagination parameters. You can define common parameters under parameters in the global `components` section and reference them elsewhere via `$ref`.

```
components:
  parameters:
    offsetParam: # <-- Arbitrary name for the definition that will be used to refer to it.
      # Not necessarily the same as the parameter name.
      in: query
      name: offset
      required: false
      schema:
        type: integer
        minimum: 0
      description: The number of items to skip before starting to collect the result set.
    limitParam:
      in: query
      name: limit
      required: false
      schema:
        type: integer
        minimum: 1
        maximum: 50
        default: 20
      description: The numbers of items to return.

paths:
  /users:
    get:
      summary: Gets a list of users.
      parameters:
        - $ref: "#/components/parameters/offsetParam"
        - $ref: "#/components/parameters/limitParam"
      responses:
        "200":
          description: OK
  /teams:
    get:
      summary: Gets a list of teams.
      parameters:
        - $ref: "#/components/parameters/offsetParam"
        - $ref: "#/components/parameters/limitParam"
      responses:
        "200":
          description: OK
```

Note that the parameters defined in `components` are not parameters applied to all operations — they are simply global definitions that can be easily re-used.

### Parameter Dependencies
OpenAPI 3.0 does not support parameter dependencies and mutually exclusive parameters. There is an open feature request at [https://github.com/OAI/OpenAPI-Specification/issues/256](https://github.com/OAI/OpenAPI-Specification/issues/256). What you can do is document the restrictions in the parameter description and define the logic in the 400 Bad Request response. For example, consider the `/report` endpoint that accepts either a relative date range (`rdate`) or an exact range (`start_date`+`end_date`):

```
GET /report?rdate=Today
GET /report?start_date=2016-11-15&end_date=2016-11-20
```

You can describe this endpoint as follows:

```
paths:
  /report:
    get:
      parameters:
        - name: rdate
          in: query
          schema:
            type: string
          description: >
            A relative date range for the report, such as `Today` or `LastWeek`.
            For an exact range, use `start_date` and `end_date` instead.
        - name: start_date
          in: query
          schema:
            type: string
            format: date
          description: >
            The start date for the report. Must be used together with `end_date`.
            This parameter is incompatible with `rdate`.
        - name: end_date
          in: query
          schema:
            type: string
            format: date
          description: >
            The end date for the report. Must be used together with `start_date`.
            This parameter is incompatible with `rdate`.
      responses:
        "400":
          description: Either `rdate` or `start_date`+`end_date` are required.
```

## Parameter (Computer Programming)
In [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"), a **parameter**, a.k.a. **formal argument**, is a [variable](https://en.wikipedia.org/wiki/Variable_\(computer_science\) "Variable (computer science)") that represents an argument, a.k.a. actual argument, a.k.a. actual parameter, to a [subroutine](https://en.wikipedia.org/wiki/Subroutine "Subroutine") call. A function's [signature](https://en.wikipedia.org/wiki/Function_signature "Function signature") defines its parameters. A call invocation involves evaluating each argument expression of a call and associating the result with the corresponding parameter.

For example, consider subroutine `def add(x, y): return x + y`. Variables `x` and `y` are parameters. For call `add(2, 3)`, the expressions `2` and `3` are arguments. For call `add(a+1, b+2)`, the arguments are `a+1` and `b+2`.

Parameter passing is defined by a programming language. [Evaluation strategy](https://en.wikipedia.org/wiki/Evaluation_strategy "Evaluation strategy") defines the semantics for how parameters can be declared and how arguments are passed to a subroutine. Generally, with [call by value](https://en.wikipedia.org/wiki/Call_by_value "Call by value"), a parameter acts like a new, local variable initialized to the value of the argument. If the argument is a variable, the subroutine cannot modify the argument state because the parameter is a copy. With [call by reference](https://en.wikipedia.org/wiki/Call_by_reference "Call by reference"), which requires the argument to be a variable, the parameter is an alias of the argument.

### Example
The following program defines a function named `SalesTax` with one parameter named `price`; both typed `double`.
```C
double SalesTax(double price)
{
	return 0.05 * price;
}
```
For call `SalesTax(10.00)`, the argument `10.00` is evaluated to a [double](https://en.wikipedia.org/wiki/Double-precision_floating-point_format "Double-precision floating-point format") value (10) and assigned to parameter variable `price`. The function is executed and returns the value 0.5.

### Parameters and arguments
The terms _parameter_ and _argument_ may have different meanings in different programming languages. Sometimes they are used interchangeably, and the context is used to distinguish the meaning. The term _parameter_ (sometimes called _formal parameter_) is often used to refer to the variable as found in the function [declaration](https://en.wikipedia.org/wiki/Declaration_\(computer_programming\) "Declaration (computer programming)"), while _argument_ (sometimes called _actual parameter_) refers to the actual input supplied at a function call statement. For example, if one defines a function as `def f(x): ...`, then `x` is the parameter, and if it is called by `a = ...; f(a)` then `a` is the argument. A parameter is an (unbound) variable, while the argument can be a [literal](https://en.wikipedia.org/wiki/Literal_\(computer_programming\) "Literal (computer programming)") or variable or more complex expression involving literals and variables. In case of call by value, what is passed to the function is the value of the argument – for example, `f(2)` and `a = 2; f(a)` are equivalent calls – while in call by reference, with a variable as argument, what is passed is a reference to that variable - even though the syntax for the function call could stay the same. The specification for [pass-by-reference](https://en.wikipedia.org/wiki/Call_by_reference "Call by reference") or [pass-by-value](https://en.wikipedia.org/wiki/Call_by_value "Call by value") would be made in the function declaration and/or definition.

Parameters appear in procedure definitions; arguments appear in procedure calls. In the function definition `f(x) = x*x` the variable x is a parameter; in the function call `f(2)` the value 2 is the argument of the function. Loosely, a parameter is a type, and an argument is an instance.

A parameter is an intrinsic property of the procedure, included in its definition. For example, in many languages, a procedure to add two supplied integers together and calculate the sum would need two parameters, one for each integer. In general, a procedure may be defined with any number of parameters, or no parameters at all. If a procedure has parameters, the part of its definition that specifies the parameters is called its _parameter list_.

By contrast, the arguments are the expressions supplied to the procedure when it is called, usually one expression matching one of the parameters. Unlike the parameters, which form an unchanging part of the procedure's definition, the arguments may vary from call to call. Each time a procedure is called, the part of the procedure call that specifies the arguments is called the _argument list_.

Although parameters are also commonly referred to as arguments, arguments are sometimes thought of as the actual values or references assigned to the parameter variables when the subroutine is called at [run-time](https://en.wikipedia.org/wiki/Run_time_\(program_lifecycle_phase\) "Run time (program lifecycle phase)"). When discussing code that is calling into a subroutine, any values or references passed into the subroutine are the arguments, and the place in the code where these values or references are given is the _parameter list_. When discussing the code inside the subroutine definition, the variables in the subroutine's parameter list are the parameters, while the values of the parameters at runtime are the arguments. For example, in C, when dealing with threads it is common to pass in an argument of type void* and cast it to an expected type:
```C
void ThreadFunction(void* pThreadArgument)
{
  // Naming the first parameter 'pThreadArgument' is correct, rather than
  // 'pThreadParameter'. At run time the value we use is an argument. As
  // mentioned above, reserve the term parameter for when discussing
  // subroutine definitions.
}
```
To better understand the difference, consider the following function written in [C](https://en.wikipedia.org/wiki/C_\(programming_language\) "C (programming language)"):
```C
int Sum(int addend1, int addend2)
{
  return addend1 + addend2;
}
```

The function _Sum_ has two parameters, named _addend1_ and _addend2_. It adds the values passed into the parameters, and returns the result to the subroutine's caller (using a technique automatically supplied by the C compiler).

The code which calls the _Sum_ function might look like this:
```C
int value1 = 40;
int value2 = 2;
int sum_value = Sum(value1, value2);
```

The variables _value1_ and _value2_ are initialized with values. _value1_ and _value2_ are both arguments to the _sum_ function in this context.

At runtime, the values assigned to these variables are passed to the function _Sum_ as arguments. In the _Sum_ function, the parameters _addend1_ and _addend2_ are evaluated, yielding the arguments 40 and 2, respectively. The values of the arguments are added, and the result is returned to the caller, where it is assigned to the variable _sum_value_.

Because of the difference between parameters and arguments, it is possible to supply inappropriate arguments to a procedure. The call may supply too many or too few arguments; one or more of the arguments may be a wrong type; or arguments may be supplied in the wrong order. Any of these situations causes a mismatch between the parameter and argument lists, and the procedure will often return an unintended answer or generate a [runtime error](https://en.wikipedia.org/wiki/Runtime_error "Runtime error").

#### Alternative convention in Eiffel
Within the [Eiffel](https://en.wikipedia.org/wiki/Eiffel_\(programming_language\) "Eiffel (programming language)") software development method and language, the terms _argument_ and _parameter_ have distinct uses established by convention. The term _argument_ is used exclusively in reference to a routine's inputs, and the term _parameter_ is used exclusively in type parameterization for [generic classes](https://en.wikipedia.org/wiki/Generic_programming "Generic programming").
Consider the following routine definition:
```eiffel
sum (addend1: INTEGER; addend2: INTEGER): INTEGER
    do
        Result := addend1 + addend2
    end
```

The routine `sum` takes two arguments `addend1` and `addend2`, which are called the routine's **formal arguments**. A call to `sum` specifies **actual arguments**, as shown below with `value1` and `value2`.
```eiffel
sum_value: INTEGER
value1: INTEGER = 40
value2: INTEGER = 2
sum_value := sum (value1, value2)
```
Parameters are also thought of as either **formal** or **actual**. **Formal generic parameters** are used in the definition of generic classes. In the example below, the class `HASH_TABLE` is declared as a generic class which has two formal generic parameters, `G` representing data of interest and `K` representing the hash key for the data:

```eiffel
class HASH_TABLE [G, K -> HASHABLE] 
            ...
```

When a class becomes a client to `HASH_TABLE`, the formal generic parameters are substituted with **actual generic parameters** in a **generic derivation**. In the following attribute declaration, `my_dictionary` is to be used as a character string based [dictionary](https://en.wikipedia.org/wiki/Associative_array "Associative array"). As such, both data and key formal generic parameters are substituted with actual generic parameters of type `STRING`.

```eiffel
my_dictionary: HASH_TABLE [STRING, STRING]
```

### Datatypes
In [strongly typed programming languages](https://en.wikipedia.org/wiki/Strongly_typed_programming_language "Strongly typed programming language"), each parameter's [type](https://en.wikipedia.org/wiki/Datatype "Datatype") must be specified in the procedure declaration. Languages using [type inference](https://en.wikipedia.org/wiki/Type_inference "Type inference") attempt to discover the types automatically from the function's body and usage. Dynamically typed programming languages defer type resolution until run-time. Weakly typed languages perform little to no type resolution, relying instead on the programmer for correctness.

Some languages use a special keyword (e.g. _void_) to indicate that the subroutine has no parameters; in formal [type theory](https://en.wikipedia.org/wiki/Type_theory "Type theory"), such functions take an empty parameter list (whose type is not _void_, but rather _[unit](https://en.wikipedia.org/wiki/Unit_type "Unit type")_).

### Argument passing
The exact mechanism for assigning arguments to parameters, called _argument passing_, depends upon the [evaluation strategy](https://en.wikipedia.org/wiki/Evaluation_strategy "Evaluation strategy") used for that parameter (typically [call by value](https://en.wikipedia.org/wiki/Call_by_value "Call by value")), which may be specified using keywords.

#### Default arguments
Some programming languages such as [Ada](https://en.wikipedia.org/wiki/Ada_\(programming_language\) "Ada (programming language)"), [C++](https://en.wikipedia.org/wiki/C%2B%2B "C++"), [Clojure](https://en.wikipedia.org/wiki/Clojure "Clojure"), allow for a [default argument](https://en.wikipedia.org/wiki/Default_argument "Default argument") to be explicitly or implicitly given in a subroutine's declaration. This allows the caller to omit that argument when calling the subroutine. If the default argument is explicitly given, then that value is used if it is not provided by the caller. If the default argument is implicit (sometimes by using a keyword such as _Optional_) then the language provides a well-known value (such as _[null](https://en.wikipedia.org/wiki/Null_pointer "Null pointer")_, _Empty_, zero, an empty string, etc.) if a value is not provided by the caller.

PowerShell example:
```powershell
function doc($g = 1.21) {
    "$g gigawatts? $g gigawatts? Great Scott!"
}

PS  > doc
1.21 gigawatts? 1.21 gigawatts? Great Scott!

PS  > doc 88
88 gigawatts? 88 gigawatts? Great Scott!
```

Default arguments can be seen as a special case of the variable-length argument list.

#### Variable-length parameter lists
Some languages allow subroutines to be defined to accept a [variable number of arguments](https://en.wikipedia.org/wiki/Variadic_function "Variadic function"). For such languages, the subroutines must iterate through the list of arguments.

PowerShell example:
```powershell
function marty {
    $args | foreach { "back to the year $_" }
}

PS  > marty 1985
back to the year 1985

PS  > marty 2015 1985 1955
back to the year 2015
back to the year 1985
back to the year 1955
```

#### Named parameters
Some programming languages—such as [Ada](https://en.wikipedia.org/wiki/Ada_\(programming_language\) "Ada (programming language)") and [Windows PowerShell](https://en.wikipedia.org/wiki/Windows_PowerShell "Windows PowerShell")—allow subroutines to have [named parameters](https://en.wikipedia.org/wiki/Named_parameter "Named parameter"). This allows the calling code to be more [self-documenting](https://en.wikipedia.org/wiki/Self-documenting "Self-documenting"). It also provides more flexibility to the caller, often allowing the order of the arguments to be changed, or for arguments to be omitted as needed.

PowerShell example:

```powershell
function jennifer($adjectiveYoung, $adjectiveOld) {
    "Young Jennifer: I'm $adjectiveYoung!"
    "Old Jennifer: I'm $adjectiveOld!"
}

PS  > jennifer 'fresh' 'experienced'
Young Jennifer: I'm fresh!
Old Jennifer: I'm experienced!

PS  > jennifer -adjectiveOld 'experienced' -adjectiveYoung 'fresh'
Young Jennifer: I'm fresh!
Old Jennifer: I'm experienced!
```

#### Multiple parameters in functional languages
In [lambda calculus](https://en.wikipedia.org/wiki/Lambda_calculus "Lambda calculus"), each function has exactly one parameter. What is thought of as functions with multiple parameters is usually represented in lambda calculus as a function which takes the first argument, and returns a function which takes the rest of the arguments; this is a transformation known as [currying](https://en.wikipedia.org/wiki/Currying "Currying"). Some programming languages, like [ML](https://en.wikipedia.org/wiki/ML_\(programming_language\) "ML (programming language)") and [Haskell](https://en.wikipedia.org/wiki/Haskell_\(programming_language\) "Haskell (programming language)"), follow this scheme. In these languages, every function has exactly one parameter, and what may look like the definition of a function of multiple parameters, is actually [syntactic sugar](https://en.wikipedia.org/wiki/Syntactic_sugar "Syntactic sugar") for the definition of a function that returns a function, etc. [Function application](https://en.wikipedia.org/wiki/Function_application "Function application") is [left-associative](https://en.wikipedia.org/wiki/Operator_associativity "Operator associativity") in these languages as well as in lambda calculus, so what looks like an application of a function to multiple arguments is correctly evaluated as the function applied to the first argument, then the resulting function applied to the second argument, etc.

### Output parameters
An **output parameter**, also known as an **out parameter** or **return parameter**, is a parameter used for output, rather than the more usual use for input. Using [call by reference](https://en.wikipedia.org/wiki/Call_by_reference "Call by reference") parameters, or call by value parameters where the value is a reference, as output parameters is an idiom in some languages, notably C and C++, while other languages have built-in support for output parameters. Languages with built-in support for output parameters include [Ada](https://en.wikipedia.org/wiki/Ada_\(programming_language\) "Ada (programming language)" (see [Ada subprograms](https://en.wikibooks.org/wiki/Ada_Programming/Subprograms "b:Ada Programming/Subprograms")), [Fortran](https://en.wikipedia.org/wiki/Fortran "Fortran") (since [Fortran 90](https://en.wikipedia.org/wiki/Fortran_90 "Fortran 90"); see [Fortran "intent"](https://en.wikibooks.org/wiki/Fortran/Fortran_procedures_and_functions#Intent "b:Fortran/Fortran procedures and functions")), various procedural extensions to [SQL](https://en.wikipedia.org/wiki/SQL "SQL"), such as [PL/SQL](https://en.wikipedia.org/wiki/PL/SQL "PL/SQL") (see [PL/SQL functions](https://en.wikipedia.org/wiki/PL/SQL#Functions "PL/SQL")) and [Transact-SQL](https://en.wikipedia.org/wiki/Transact-SQL "Transact-SQL"), C# and the [.NET Framework](https://en.wikipedia.org/wiki/.NET_Framework ".NET Framework"), [Swift](https://en.wikipedia.org/wiki/Swift_\(programming_language\) "Swift (programming language)"), and the scripting language [TScript](https://en.wikipedia.org/wiki/TScript "TScript") (see [TScript function declarations](https://en.wikipedia.org/wiki/TScript#Function_declarations "TScript")).

More precisely, one may distinguish three types of parameters or **parameter modes**: _input parameters_, _output parameters,_ and _input/output parameters;_ these are often denoted `in`, `out`, and `in out` or `inout`. An input argument (the argument to an input parameter) must be a value, such as an initialized variable or literal, and must not be redefined or assigned to; an output argument must be an assignable variable, but it need not be initialized, any existing value is not accessible, and must be assigned a value; and an input/output argument must be an initialized, assignable variable, and can optionally be assigned a value. The exact requirements and enforcement vary between languages – for example, in [Ada 83](https://en.wikipedia.org/wiki/Ada_83 "Ada 83") output parameters can only be assigned to, not read, even after assignment (this was removed in [Ada 95](https://en.wikipedia.org/wiki/Ada_95 "Ada 95") to remove the need for an auxiliary accumulator variable). These are analogous to the notion of a [value](https://en.wikipedia.org/wiki/Value_\(computer_science\) "Value (computer science)") in an expression being an r-value (has a value), an l-value (can be assigned), or an r-value/l-value (has a value and can be assigned), respectively, though these terms have specialized meanings in C.

In some cases only input and input/output are distinguished, with output being considered a specific use of input/output, and in other cases only input and output (but not input/output) are supported. The default mode varies between languages: in Fortran 90 input/output is default, while in C# and SQL extensions input is default, and in TScript each parameter is explicitly specified as input or output.

Syntactically, parameter mode is generally indicated with a keyword in the function declaration, such as `void f(out int x)` in C#. Conventionally output parameters are often put at the end of the parameter list to clearly distinguish them, though this is not always followed. TScript uses a different approach, where in the function declaration input parameters are listed, then output parameters, separated by a colon (:) and there is no return type to the function itself, as in this function, which computes the size of a text fragment:

TextExtent(WString text, Font font : Integer width, Integer height)

Parameter modes are a form of [denotational semantics](https://en.wikipedia.org/wiki/Denotational_semantics "Denotational semantics"), stating the programmer's intent and allowing compilers to catch errors and apply optimizations – they do not necessarily imply [operational semantics](https://en.wikipedia.org/wiki/Operational_semantics "Operational semantics") (how the parameter passing actually occurs). Notably, while input parameters can be implemented by call by value, and output and input/output parameters by call by reference – and this is a straightforward way to implement these modes in languages without built-in support – this is not always how they are implemented. This distinction is discussed in detail in the _Ada '83 Rationale,_ which emphasizes that the parameter mode is abstracted from which parameter passing mechanism (by reference or by copy) is actually implemented. For instance, while in C# input parameters (default, no keyword) are passed by value, and output and input/output parameters (`out` and `ref`) are passed by reference, in PL/SQL input parameters (`IN`) are passed by reference, and output and input/output parameters (`OUT` and `IN OUT`) are by default passed by value and the result copied back, but can be passed by reference by using the `NOCOPY` compiler hint.

A syntactically similar construction to output parameters is to assign the [return value](https://en.wikipedia.org/wiki/Return_value "Return value") to a variable with the same name as the function. This is found in [Pascal](https://en.wikipedia.org/wiki/Pascal_\(programming_language\) "Pascal (programming language)") and [Fortran 66](https://en.wikipedia.org/wiki/Fortran_66 "Fortran 66") and [Fortran 77](https://en.wikipedia.org/wiki/Fortran_77 "Fortran 77"), as in this Pascal example:
```pascal
function f(x, y: integer): integer;
begin
    f := x + y;
end;
```

This is semantically different in that when called, the function is simply evaluated – it is not passed a variable from the calling [scope](https://en.wikipedia.org/wiki/Scope_\(computer_science\) "Scope (computer science)") to store the output in.

#### Use
The primary use of output parameters is to return multiple values from a function, while the use of input/output parameters is to modify state using parameter passing (rather than by shared environment, as in global variables). An important use of returning multiple values is to solve the [semipredicate problem](https://en.wikipedia.org/wiki/Semipredicate_problem "Semipredicate problem") of returning both a value and an error status – see [Semipredicate problem: Multivalued return](https://en.wikipedia.org/wiki/Semipredicate_problem#Multivalued_return "Semipredicate problem").

For example, to return two variables from a function in C, one may write:
```C
int width
int height;

F(x, &width, &height);
```
where `x` is an input parameter and `width` and `height` are output parameters.

A common use case in C and related languages is for [exception handling](https://en.wikipedia.org/wiki/Exception_handling "Exception handling"), where a function places the return value in an output variable, and returns a Boolean corresponding to whether the function succeeded or not. An archetypal example is the `TryParse` method in .NET, especially C#, which parses a string into an integer, returning `true` on success and `false` on failure. This has the following signature:
```C#
public static bool TryParse(string s, out int result)

and may be used as follows:

int result;
if (!Int32.TryParse(s, result)) {
    // exception handling
}
```
Similar considerations apply to returning a value of one of several possible types, where the return value can specify the type and then value is stored in one of several output variables.

#### Drawbacks
Output parameters are often discouraged in modern programming, essentially as being awkward, confusing, and too low-level – commonplace return values are considerably easier to understand and work with. Notably, output parameters involve functions with side effects (modifying the output parameter) and are semantically similar to references, which are more confusing than pure functions and values, and the distinction between output parameters and input/output parameters can be subtle. Further, since in common programming styles most parameters are simply input parameters, output parameters and input/output parameters are unusual and hence susceptible to misunderstanding.

Output and input/output parameters prevent [function composition](https://en.wikipedia.org/wiki/Function_composition_\(computer_science\) "Function composition (computer science)"), since the output is stored in variables, rather than in the value of an expression. Thus one must initially declare a variable, and then each step of a chain of functions must be a separate statement. For example, in C++ the following function composition:
```C++
Object obj = G(y, F(x));
```

when written with output and input/output parameters instead becomes (for `F` it is an output parameter, for `G` an input/output parameter):
```C++
Object obj;
F(x, &obj);
G(y, &obj);
```

In the special case of a function with a single output or input/output parameter and no return value, function composition is possible if the output or input/output parameter (or in C/C++, its address) is also returned by the function, in which case the above becomes:
```C++
Object obj;
G(y, F(x, &obj));
```

#### Alternatives
There are various alternatives to the use cases of output parameters.

For returning multiple values from a function, an alternative is to return a [tuple](https://en.wikipedia.org/wiki/Tuple "Tuple"). Syntactically this is clearer if automatic sequence unpacking and [parallel assignment](https://en.wikipedia.org/wiki/Parallel_assignment "Parallel assignment") can be used, as in [Go](https://en.wikipedia.org/wiki/Go_\(programming_language\) "Go (programming language)") or Python, such as:
```C
def f():
    return 1, 2
a, b = f()
```

For returning a value of one of several types, a [tagged union](https://en.wikipedia.org/wiki/Tagged_union "Tagged union") can be used instead; the most common cases are [nullable types](https://en.wikipedia.org/wiki/Nullable_type "Nullable type") ([option types](https://en.wikipedia.org/wiki/Option_type "Option type")), where the return value can be null to indicate failure. For exception handling, one can return a nullable type, or raise an exception. For example, in Python one might have either:
```C
result = parse(s)
if result is None:
    # exception handling
```

or, more idiomatically:
```C
try:
    result = parse(s)
except ParseError:
    # exception handling
```

The micro-optimization of not requiring a local variable and copying the return when using output variables can also be applied to conventional functions and return values by sufficiently sophisticated compilers.

The usual alternative to output parameters in C and related languages is to return a single data structure containing all return values. For example, given a structure encapsulating width and height, one can write:
```C
WidthHeight width_and_height = F(x);
```

In object-oriented languages, instead of using input/output parameters, one can often use [call by sharing](https://en.wikipedia.org/wiki/Call_by_sharing "Call by sharing"), passing a reference to an object and then mutating the object, though not changing which object the variable refers to.

## Parameter (General/CS Definition)
A **parameter** (from [Ancient Greek](https://en.wikipedia.org/wiki/Ancient_Greek_language "Ancient Greek language") [παρά](https://en.wiktionary.org/wiki/%CF%80%CE%B1%CF%81%CE%AC#Ancient_Greek "wikt:παρά") _(_pará_)_ 'beside, subsidiary' and [μέτρον](https://en.wiktionary.org/wiki/%CE%BC%CE%AD%CF%84%CF%81%CE%BF%CE%BD#Ancient_Greek "wikt:μέτρον") _(_métron_)_ 'measure'), generally, is any characteristic that can help in defining or classifying a particular [system](https://en.wikipedia.org/wiki/System "System") (meaning an event, project, object, situation, etc.). That is, a parameter is an element of a system that is useful, or critical, when identifying the system, or when evaluating its performance, status, condition, etc.

_Parameter_ has more specific meanings within various disciplines, including [mathematics](https://en.wikipedia.org/wiki/Mathematics "Mathematics"), [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"), [engineering](https://en.wikipedia.org/wiki/Engineering "Engineering"), [statistics](https://en.wikipedia.org/wiki/Statistics "Statistics"), [logic](https://en.wikipedia.org/wiki/Logic "Logic"), [linguistics](https://en.wikipedia.org/wiki/Linguistics "Linguistics"), and electronic musical composition.

In addition to its technical uses, there are also extended uses, especially in non-scientific contexts, where it is used to mean defining characteristics or boundaries, as in the phrases 'test parameters' or 'game play parameters'.

### Modelization
When a [system](https://en.wikipedia.org/wiki/System_theory "System theory") is modeled by equations, the values that describe the system are called _parameters_. For example, in [mechanics](https://en.wikipedia.org/wiki/Mechanics "Mechanics"), the masses, the dimensions and shapes (for solid bodies), the densities and the viscosities (for fluids), appear as parameters in the equations modeling movements. There are often several choices for the parameters, and choosing a convenient set of parameters is called _parametrization_.

For example, if one were considering the movement of an object on the surface of a sphere much larger than the object (e.g. the Earth), there are two commonly used parametrizations of its position: angular coordinates (like latitude/longitude), which neatly describe large movements along circles on the sphere, and directional distance from a known point (e.g. "10km NNW of Toronto" or equivalently "8km due North, and then 6km due West, from Toronto" ), which are often simpler for movement confined to a (relatively) small area, like within a particular country or region. Such parametrizations are also relevant to the modelization of geographic areas (i.e. [map drawing](https://en.wikipedia.org/wiki/Map_projection "Map projection")).

### Mathematical functions
[Mathematical functions](https://en.wikipedia.org/wiki/Mathematical_function "Mathematical function") have one or more [arguments](https://en.wikipedia.org/wiki/Argument_of_a_function "Argument of a function") that are designated in the definition by [variables](https://en.wikipedia.org/wiki/Variable_\(mathematics\) "Variable (mathematics)"). A function definition can also contain parameters, but unlike variables, parameters are not listed among the arguments that the function takes. When parameters are present, the definition actually defines a whole family of functions, one for every valid set of values of the parameters. For instance, one could define a general [quadratic function](https://en.wikipedia.org/wiki/Quadratic_function "Quadratic function") by declaring

f(x)=ax2+bx+c![{\displaystyle f(x)=ax^{2}+bx+c}](https://wikimedia.org/api/rest_v1/media/math/render/svg/66fca4dfe28e7b4a4a336578daaab18c87397073);

Here, the variable _x_ designates the function's argument, but _a_, _b_, and _c_ are parameters (in this instance, also called _[coefficients](https://en.wikipedia.org/wiki/Coefficient "Coefficient")_) that determine which particular quadratic function is being considered. A parameter could be incorporated into the function name to indicate its dependence on the parameter. For instance, one may define the base-_b_ logarithm by the formula

logb⁡(x)=log⁡(x)log⁡(b)![{\displaystyle \log _{b}(x)={\frac {\log(x)}{\log(b)}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d3d7d1164f4d4438fa5ce485036e2fae851b87cc)

where _b_ is a parameter that indicates which logarithmic function is being used. It is not an argument of the function, and will, for instance, be a constant when considering the [derivative](https://en.wikipedia.org/wiki/Derivative_\(mathematics\) "Derivative (mathematics)") logb′⁡(x)=(xln⁡(b))−1![{\displaystyle \textstyle \log _{b}'(x)=(x\ln(b))^{-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1f804dda37fa98bfbc56fe5eacd08c04554306b2).

In some informal situations it is a matter of convention (or historical accident) whether some or all of the symbols in a function definition are called parameters. However, changing the status of symbols between parameter and variable changes the function as a mathematical object. For instance, the notation for the [falling factorial power](https://en.wikipedia.org/wiki/Falling_factorial_power "Falling factorial power")

nk_=n(n−1)(n−2)⋯(n−k+1)![{\displaystyle n^{\underline {k}}=n(n-1)(n-2)\cdots (n-k+1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8edddc122177240d34baebd656f49c30b6f80832),

defines a [polynomial function](https://en.wikipedia.org/wiki/Polynomial#Polynomial_functions "Polynomial") of _n_ (when _k_ is considered a parameter), but is not a polynomial function of _k_ (when _n_ is considered a parameter). Indeed, in the latter case, it is only defined for non-negative integer arguments. More formal presentations of such situations typically start out with a function of several variables (including all those that might sometimes be called "parameters") such as

(n,k)↦nk_![{\displaystyle (n,k)\mapsto n^{\underline {k}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c9747b56d919f6d00c0c7e9daea24878476b4f8a)

as the most fundamental object being considered, then defining functions with fewer variables from the main one by means of [currying](https://en.wikipedia.org/wiki/Currying "Currying").

Sometimes it is useful to consider all functions with certain parameters as _parametric family_, i.e. as an [indexed family](https://en.wikipedia.org/wiki/Indexed_family "Indexed family") of functions. Examples from probability theory [are given further below](https://en.wikipedia.org/wiki/Parameter#Probability_theory).

#### Examples
- In a section on frequently misused words in his book _The Writer's Art_, [James J. Kilpatrick](https://en.wikipedia.org/wiki/James_J._Kilpatrick "James J. Kilpatrick") quoted a letter from a correspondent, giving examples to illustrate the correct use of the word _parameter_:

> W.M. Woods ... a mathematician ... writes ... "... a variable is one of the many things a _parameter_ is not." ... The dependent variable, the speed of the car, depends on the independent variable, the position of the gas pedal.

> [Kilpatrick quoting Woods] "Now ... the engineers ... change the lever arms of the linkage ... the speed of the car ... will still depend on the pedal position ... _but in a ... different manner_. You have changed a parameter"

- A [parametric equaliser](https://en.wikipedia.org/wiki/Parametric_equaliser "Parametric equaliser") is an [audio filter](https://en.wikipedia.org/wiki/Audio_filter "Audio filter") that allows the [frequency](https://en.wikipedia.org/wiki/Frequency "Frequency") of maximum cut or boost to be set by one control, and the size of the cut or boost by another. These settings, the frequency level of the peak or trough, are two of the parameters of a frequency response curve, and in a two-control equaliser they completely describe the curve. More elaborate parametric equalisers may allow other parameters to be varied, such as skew. These parameters each describe some aspect of the response curve seen as a whole, over all frequencies. A [graphic equaliser](https://en.wikipedia.org/wiki/Graphic_equaliser "Graphic equaliser") provides individual level controls for various frequency bands, each of which acts only on that particular frequency band.
- If asked to imagine the graph of the relationship _y_ = _ax_2, one typically visualizes a range of values of _x_, but only one value of _a_. Of course a different value of _a_ can be used, generating a different relation between _x_ and _y_. Thus _a_ is a parameter: it is less variable than the variable _x_ or _y_, but it is not an explicit constant like the exponent 2. More precisely, changing the parameter _a_ gives a different (though related) problem, whereas the variations of the variables _x_ and _y_ (and their interrelation) are part of the problem itself.
- In calculating income based on wage and hours worked (income equals wage multiplied by hours worked), it is typically assumed that the number of hours worked is easily changed, but the wage is more static. This makes _wage_ a parameter, _hours worked_ an [independent variable](https://en.wikipedia.org/wiki/Independent_variable "Independent variable"), and _income_ a [dependent variable](https://en.wikipedia.org/wiki/Dependent_variable "Dependent variable").

#### Mathematical models
In the context of a [mathematical model](https://en.wikipedia.org/wiki/Mathematical_model "Mathematical model"), such as a [probability distribution](https://en.wikipedia.org/wiki/Probability_distribution "Probability distribution"), the distinction between variables and parameters was described by Bard as follows:

We refer to the relations which supposedly describe a certain physical situation, as a _model_. Typically, a model consists of one or more equations. The quantities appearing in the equations we classify into _variables_ and _parameters_. The distinction between these is not always clear cut, and it frequently depends on the context in which the variables appear. Usually a model is designed to explain the relationships that exist among quantities which can be measured independently in an experiment; these are the variables of the model. To formulate these relationships, however, one frequently introduces "constants" which stand for inherent properties of nature (or of the materials and equipment used in a given experiment). These are the parameters.

#### Analytic geometry
In [analytic geometry](https://en.wikipedia.org/wiki/Analytic_geometry "Analytic geometry"), a [curve](https://en.wikipedia.org/wiki/Curve "Curve") can be described as the image of a function whose argument, typically called the _parameter_, lies in a [real interval](https://en.wikipedia.org/wiki/Interval_\(mathematics\) "Interval (mathematics)").

For example, the [unit circle](https://en.wikipedia.org/wiki/Unit_circle "Unit circle") can be specified in the following two ways:

- _implicit_ form, the curve is the locus of points (_x_, _y_) in the [Cartesian plane](https://en.wikipedia.org/wiki/Cartesian_coordinate_system "Cartesian coordinate system") that satisfy the relationx2+y2=1.![{\displaystyle x^{2}+y^{2}=1.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bd4ba9a57bd82841e5889575e2ff3e1ef5fad8e9)
- _parametric_ form, the curve is the image of the functiont↦(cos⁡t,sin⁡t)![{\displaystyle t\mapsto (\cos t,\sin t)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aa92a7e0db1cc38274018d283d4a2e8f0d9b381a)
    
    with parameter t∈[0,2π).![{\displaystyle t\in [0,2\pi ).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d4e52f713bba43d916a2647b3a2b564580788537) 
    (x,y)=(cos⁡t,sin⁡t).![{\displaystyle (x,y)=(\cos t,\sin t).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d3b999530b7d8039bf3cc945ccb50fc9abd5559a)
    
    The parameter t in this equation would elsewhere in mathematics be called the _[independent variable](https://en.wikipedia.org/wiki/Independent_variable "Independent variable")_.
    

#### Mathematical analysis
In [mathematical analysis](https://en.wikipedia.org/wiki/Mathematical_analysis "Mathematical analysis"), integrals dependent on a parameter are often considered. These are of the form

F(t)=∫x0(t)x1(t)f(x;t)dx.![{\displaystyle F(t)=\int _{x_{0}(t)}^{x_{1}(t)}f(x;t)\,dx.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7bd5da1388eaf7fdc69de547f1971a7560e2434e)

In this formula, _t_ is the argument of the function _F_, and on the right-hand side the _parameter_ on which the integral depends. When evaluating the integral, _t_ is held constant, and so it is considered to be a parameter. If we are interested in the value of _F_ for different values of _t_, we then consider _t_ to be a variable. The quantity _x_ is a _[dummy variable](https://en.wikipedia.org/wiki/Bound_variable "Bound variable")_ or _variable of integration_ (confusingly, also sometimes called a _parameter of integration_).

#### Statistics and econometrics
In [statistics](https://en.wikipedia.org/wiki/Statistics "Statistics") and [econometrics](https://en.wikipedia.org/wiki/Econometrics "Econometrics"), the probability framework above still holds, but attention shifts to [estimating](https://en.wikipedia.org/wiki/Statistical_estimation "Statistical estimation") the parameters of a distribution based on observed data, or [testing hypotheses](https://en.wikipedia.org/wiki/Hypothesis_testing "Hypothesis testing") about them. In [frequentist estimation](https://en.wikipedia.org/wiki/Frequentist_inference "Frequentist inference") parameters are considered "fixed but unknown", whereas in [Bayesian estimation](https://en.wikipedia.org/wiki/Bayesian_probability "Bayesian probability") they are treated as random variables, and their uncertainty is described as a distribution.

In [estimation theory](https://en.wikipedia.org/wiki/Estimation_theory "Estimation theory") of statistics, "statistic" or [estimator](https://en.wikipedia.org/wiki/Estimator "Estimator") refers to samples, whereas "parameter" or [estimand](https://en.wikipedia.org/wiki/Estimand "Estimand") refers to populations, where the samples are taken from. A [statistic](https://en.wikipedia.org/wiki/Statistic "Statistic") is a numerical characteristic of a sample that can be used as an estimate of the corresponding parameter, the numerical characteristic of the [population](https://en.wikipedia.org/wiki/Statistical_population "Statistical population") from which the sample was drawn.

For example, the [sample mean](https://en.wikipedia.org/wiki/Sample_mean "Sample mean") (estimator), denoted X¯![{\displaystyle {\overline {X}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/08fd87d3502c4f9e1b02ac74644474258aeea176), can be used as an estimate of the _mean_ parameter (estimand), denoted _μ_, of the population from which the sample was drawn. Similarly, the [sample variance](https://en.wikipedia.org/wiki/Sample_variance "Sample variance") (estimator), denoted _S_2, can be used to estimate the _variance_ parameter (estimand), denoted _σ_2, of the population from which the sample was drawn. (Note that the sample standard deviation (_S_) is not an unbiased estimate of the population standard deviation (_σ_): see [Unbiased estimation of standard deviation](https://en.wikipedia.org/wiki/Unbiased_estimation_of_standard_deviation "Unbiased estimation of standard deviation").)

It is possible to make statistical inferences without assuming a particular parametric family of [probability distributions](https://en.wikipedia.org/wiki/Probability_distribution "Probability distribution"). In that case, one speaks of _[non-parametric statistics](https://en.wikipedia.org/wiki/Non-parametric_statistics "Non-parametric statistics")_ as opposed to the [parametric statistics](https://en.wikipedia.org/wiki/Parametric_statistics "Parametric statistics") just described. For example, a test based on [Spearman's rank correlation coefficient](https://en.wikipedia.org/wiki/Spearman%27s_rank_correlation_coefficient "Spearman's rank correlation coefficient") would be called non-parametric since the statistic is computed from the rank-order of the data disregarding their actual values (and thus regardless of the distribution they were sampled from), whereas those based on the [Pearson product-moment correlation coefficient](https://en.wikipedia.org/wiki/Pearson_product-moment_correlation_coefficient "Pearson product-moment correlation coefficient") are parametric tests since it is computed directly from the data values and thus estimates the parameter known as the [population correlation](https://en.wikipedia.org/wiki/Correlation_and_dependence "Correlation and dependence").

#### Probability theory

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/1/16/Poisson_pmf.svg/250px-Poisson_pmf.svg.png)](https://en.wikipedia.org/wiki/File:Poisson_pmf.svg)

These traces all represent Poisson distributions, but with different values for the parameter λ

In [probability theory](https://en.wikipedia.org/wiki/Probability_theory "Probability theory"), one may describe the [distribution](https://en.wikipedia.org/wiki/Probability_distribution "Probability distribution") of a [random variable](https://en.wikipedia.org/wiki/Random_variable "Random variable") as belonging to a _family_ of [probability distributions](https://en.wikipedia.org/wiki/Probability_distribution "Probability distribution"), distinguished from each other by the values of a finite number of _parameters_. For example, one talks about "a [Poisson distribution](https://en.wikipedia.org/wiki/Poisson_distribution "Poisson distribution") with mean value λ". The function defining the distribution (the [probability mass function](https://en.wikipedia.org/wiki/Probability_mass_function "Probability mass function")) is:

f(k;λ)=e−λλkk!.![{\displaystyle f(k;\lambda )={\frac {e^{-\lambda }\lambda ^{k}}{k!}}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/54ab28b4e2fa2d19b1fdbb849c47fe32e5047cab)

This example nicely illustrates the distinction between constants, parameters, and variables. _e_ is [Euler's number](https://en.wikipedia.org/wiki/Euler%27s_number "Euler's number"), a fundamental [mathematical constant](https://en.wikipedia.org/wiki/Mathematical_constant "Mathematical constant"). The parameter λ is the [mean](https://en.wikipedia.org/wiki/Mean "Mean") number of observations of some phenomenon in question, a property characteristic of the system. _k_ is a variable, in this case the number of occurrences of the phenomenon actually observed from a particular sample. If we want to know the probability of observing _k_1 occurrences, we plug it into the function to get f(k1;λ)![{\displaystyle f(k_{1};\lambda )}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2b057adcffb75a0be9e9b2a9873ce4c5cd960d75). Without altering the system, we can take multiple samples, which will have a range of values of _k_, but the system is always characterized by the same λ.

For instance, suppose we have a [radioactive](https://en.wikipedia.org/wiki/Radioactivity "Radioactivity") sample that emits, on average, five particles every ten minutes. We take measurements of how many particles the sample emits over ten-minute periods. The measurements exhibit different values of _k_, and if the sample behaves according to Poisson statistics, then each value of _k_ will come up in a proportion given by the probability mass function above. From measurement to measurement, however, λ remains constant at 5. If we do not alter the system, then the parameter λ is unchanged from measurement to measurement; if, on the other hand, we modulate the system by replacing the sample with a more radioactive one, then the parameter λ would increase.

Another common distribution is the [normal distribution](https://en.wikipedia.org/wiki/Normal_distribution "Normal distribution"), which has as parameters the mean μ and the variance σ².

In these above examples, the distributions of the random variables are completely specified by the type of distribution, i.e. Poisson or normal, and the parameter values, i.e. mean and variance. In such a case, we have a parameterized distribution.

It is possible to use the sequence of [moments](https://en.wikipedia.org/wiki/Moment_\(mathematics\) "Moment (mathematics)") (mean, mean square, ...) or [cumulants](https://en.wikipedia.org/wiki/Cumulant "Cumulant") (mean, variance, ...) as parameters for a probability distribution: see [Statistical parameter](https://en.wikipedia.org/wiki/Statistical_parameter "Statistical parameter").

### Computer programming
In [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"), two notions of [parameter](https://en.wikipedia.org/wiki/Parameter_\(computer_programming\) "Parameter (computer programming)") are commonly used, and are referred to as [parameters and arguments](https://en.wikipedia.org/wiki/Parameter_\(computer_programming\)#Parameters_and_arguments "Parameter (computer programming)")—or more formally as a **formal parameter** and an **actual parameter**.

For example, in the definition of a function such as

y = _f_(_x_) = _x_ + 2,

_x_ is the _formal parameter_ (the _parameter_) of the defined function.

When the function is evaluated for a given value, as in

_f_(3): or, _y_ = _f_(3) = 3 + 2 = 5,

3 is the _actual parameter_ (the _argument_) for evaluation by the defined function; it is a given value (actual value) that is substituted for the _formal parameter_ of the defined function. (In casual usage the terms _parameter_ and _argument_ might inadvertently be interchanged, and thereby used incorrectly.)

These concepts are discussed in a more precise way in [functional programming](https://en.wikipedia.org/wiki/Functional_programming "Functional programming") and its foundational disciplines, [lambda calculus](https://en.wikipedia.org/wiki/Lambda_calculus "Lambda calculus") and [combinatory logic](https://en.wikipedia.org/wiki/Combinatory_logic "Combinatory logic"). Terminology varies between languages; some computer languages such as [C](https://en.wikipedia.org/wiki/C_\(programming_language\) "C (programming language)") define parameter and argument as given here, while [Eiffel](https://en.wikipedia.org/wiki/Eiffel_\(programming_language\) "Eiffel (programming language)") uses an [alternative convention](https://en.wikipedia.org/wiki/Parameter_\(computer_programming\)#Alternative_convention_in_Eiffel "Parameter (computer programming)").

### Artificial intelligence
In [artificial intelligence](https://en.wikipedia.org/wiki/Artificial_intelligence "Artificial intelligence"), a [model](https://en.wikipedia.org/wiki/Probability_distribution "Probability distribution") describes the probability that something will occur. Parameters in a model are the weight of the various probabilities. Tiernan Ray, in an article on GPT-3, described parameters this way:

> A parameter is a calculation in a neural network that applies a great or lesser weighting to some aspect of the data, to give that aspect greater or lesser prominence in the overall calculation of the data. It is these weights that give shape to the data, and give the neural network a learned perspective on the data.

### Engineering
In [engineering](https://en.wikipedia.org/wiki/Engineering "Engineering") (especially involving data acquisition) the term _parameter_ sometimes loosely refers to an individual measured item. This usage is not consistent, as sometimes the term _channel_ refers to an individual measured item, with _parameter_ referring to the setup information about that channel.

"Speaking generally, **properties** are those physical quantities which directly describe the physical attributes of the system; **parameters** are those combinations of the properties which suffice to determine the response of the system. Properties can have all sorts of dimensions, depending upon the system being considered; parameters are dimensionless, or have the dimension of time or its reciprocal."
The term can also be used in engineering contexts, however, as it is typically used in the physical sciences.

### Environmental science
In [environmental science](https://en.wikipedia.org/wiki/Environmental_science "Environmental science") and particularly in [chemistry](https://en.wikipedia.org/wiki/Chemistry "Chemistry") and [microbiology](https://en.wikipedia.org/wiki/Microbiology "Microbiology"), a parameter is used to describe a discrete chemical or microbiological entity that can be assigned a value: commonly a concentration, but may also be a logical entity (present or absent), a [statistical](https://en.wikipedia.org/wiki/Statistics "Statistics") result such as a [95 percentile](https://en.wikipedia.org/wiki/Percentile "Percentile") value or in some cases a subjective value.

### Logic
In [logic](https://en.wikipedia.org/wiki/Logic "Logic"), the parameters passed to (or operated on by) an _open predicate_ are called _parameters_ by some authors (e.g., [Prawitz](https://en.wikipedia.org/wiki/Dag_Prawitz "Dag Prawitz")'s _Natural Deduction_;[Paulson](https://en.wikipedia.org/wiki/Lawrence_Paulson "Lawrence Paulson")'s _Designing a theorem prover_). Parameters locally defined within the predicate are called _variables_. This extra distinction pays off when defining substitution (without this distinction special provision must be made to avoid variable capture). Others (maybe most) just call parameters passed to (or operated on by) an open predicate _variables_, and when defining substitution have to distinguish between _[free variables](https://en.wikipedia.org/wiki/Free_variable "Free variable")_ and _[bound variables](https://en.wikipedia.org/wiki/Bound_variable "Bound variable")_.

## HTTP
**HTTP** (**Hypertext Transfer Protocol**) is an [application layer](https://en.wikipedia.org/wiki/Application_layer "Application layer") protocol in the [Internet protocol suite](https://en.wikipedia.org/wiki/Internet_protocol_suite "Internet protocol suite") model for distributed, collaborative, [hypermedia](https://en.wikipedia.org/wiki/Hypermedia "Hypermedia") information systems. HTTP is the foundation of data communication for the [World Wide Web](https://en.wikipedia.org/wiki/World_Wide_Web "World Wide Web"), where [hypertext](https://en.wikipedia.org/wiki/Hypertext "Hypertext") documents include [hyperlinks](https://en.wikipedia.org/wiki/Hyperlink "Hyperlink") to other resources that the user can easily access, for example by a [mouse](https://en.wikipedia.org/wiki/Computer_mouse "Computer mouse") click or by tapping the screen in a [web browser](https://en.wikipedia.org/wiki/Web_browser "Web browser").

Development of HTTP was initiated by [Tim Berners-Lee](https://en.wikipedia.org/wiki/Tim_Berners-Lee "Tim Berners-Lee") at [CERN](https://en.wikipedia.org/wiki/CERN "CERN") in 1989 and summarized in a simple document describing the behavior of a client and a server using the first HTTP version, named 0.9. That version was subsequently developed, eventually becoming the public 1.0.

Development of early HTTP [Requests for Comments](https://en.wikipedia.org/wiki/Requests_for_Comments "Requests for Comments") (RFCs) started a few years later in a coordinated effort by the [Internet Engineering Task Force](https://en.wikipedia.org/wiki/Internet_Engineering_Task_Force "Internet Engineering Task Force") (IETF) and the [World Wide Web Consortium](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium "World Wide Web Consortium") (W3C), with work later moving to the IETF.

HTTP/1 was finalized and fully documented (as version 1.0) in 1996. It evolved (as version 1.1) in 1997 and then its specifications were updated in 1999, 2014, and 2022. Its secure variant named [HTTPS](https://en.wikipedia.org/wiki/HTTPS "HTTPS") is used by more than 85% of websites.

[HTTP/2](https://en.wikipedia.org/wiki/HTTP/2 "HTTP/2"), published in 2015, provides a more efficient expression of HTTP's semantics "on the wire". As of August 2024, it is supported by 66.2% of websites (35.3% HTTP/2 + 30.9% HTTP/3 with backwards compatibility) and supported by almost all web browsers (over 98% of users). It is also supported by major web servers over [Transport Layer Security](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security") (TLS) using an [Application-Layer Protocol Negotiation](https://en.wikipedia.org/wiki/Application-Layer_Protocol_Negotiation "Application-Layer Protocol Negotiation") (ALPN) extension where [TLS 1.2](https://en.wikipedia.org/wiki/TLS_1.2 "TLS 1.2") or newer is required.

[HTTP/3](https://en.wikipedia.org/wiki/HTTP/3 "HTTP/3"), the successor to HTTP/2, was published in 2022. As of February 2024, it is now used on 30.9% of websites and is supported by most web browsers, i.e. (at least partially) supported by 97% of users. HTTP/3 uses [QUIC](https://en.wikipedia.org/wiki/QUIC "QUIC") instead of [TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol "Transmission Control Protocol") for the underlying transport protocol. Like HTTP/2, it does not obsolete previous major versions of the protocol. Support for HTTP/3 was added to [Cloudflare](https://en.wikipedia.org/wiki/Cloudflare "Cloudflare") and [Google Chrome](https://en.wikipedia.org/wiki/Google_Chrome "Google Chrome") first, and is also enabled in [Firefox](https://en.wikipedia.org/wiki/Firefox "Firefox"). HTTP/3 has lower latency for real-world web pages, if enabled on the server, and loads faster than with HTTP/2, in some cases over three times faster than HTTP/1.1 (which is still commonly only enabled).

### Technical overview
HTTP functions as a [request–response](https://en.wikipedia.org/wiki/Request%E2%80%93response "Request–response") protocol in the [client–server model](https://en.wikipedia.org/wiki/Client%E2%80%93server_model "Client–server model"). A [web browser](https://en.wikipedia.org/wiki/Web_browser "Web browser"), for example, may be the _client_ whereas a [process](https://en.wikipedia.org/wiki/Process_\(computing\) "Process (computing)"), named [web server](https://en.wikipedia.org/wiki/Web_server "Web server"), running on a computer [hosting](https://en.wikipedia.org/wiki/Host_\(network\) "Host (network)") one or more [websites](https://en.wikipedia.org/wiki/Website "Website") may be the _server_. The client submits an HTTP _request_ message to the server. The server, which provides _resources_ such as [HTML](https://en.wikipedia.org/wiki/HTML "HTML") files and other content or performs other functions on behalf of the client, returns a _response_ message to the client. The response contains completion status information about the request and may also contain requested content in its message body.

A web browser is an example of a _[user agent](https://en.wikipedia.org/wiki/User_agent "User agent")_ (UA). Other types of user agent include the indexing software used by search providers ([web crawlers](https://en.wikipedia.org/wiki/Web_crawler "Web crawler")), [voice browsers](https://en.wikipedia.org/wiki/Voice_browser "Voice browser"), [mobile apps](https://en.wikipedia.org/wiki/Mobile_app "Mobile app"), and other [software](https://en.wikipedia.org/wiki/Software "Software") that accesses, consumes, or displays web content.

HTTP is designed to permit intermediate network elements to improve or enable communications between clients and servers. High-traffic websites often benefit from [web cache](https://en.wikipedia.org/wiki/Web_cache "Web cache") servers that deliver content on behalf of [upstream servers](https://en.wikipedia.org/wiki/Upstream_server "Upstream server") to improve response time. Web browsers cache previously accessed web resources and reuse them, whenever possible, to reduce network traffic. HTTP [proxy servers](https://en.wikipedia.org/wiki/Proxy_server "Proxy server") at [private network](https://en.wikipedia.org/wiki/Private_network "Private network") boundaries can facilitate communication for clients without a globally routable address, by relaying messages with external servers.

To allow intermediate HTTP nodes (proxy servers, web caches, etc.) to accomplish their functions, some of the [HTTP headers](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields "List of HTTP header fields") (found in HTTP requests/responses) are managed [hop-by-hop](https://en.wikipedia.org/wiki/Hop-by-hop_transport "Hop-by-hop transport") whereas other HTTP headers are managed [end-to-end](https://en.wikipedia.org/wiki/End-to-end_principle "End-to-end principle") (managed only by the source client and by the target web server).

HTTP is an [application layer](https://en.wikipedia.org/wiki/Application_layer "Application layer") protocol designed within the framework of the [Internet protocol suite](https://en.wikipedia.org/wiki/Internet_protocol_suite "Internet protocol suite"). Its definition presumes an underlying and reliable [transport layer](https://en.wikipedia.org/wiki/Transport_layer "Transport layer") protocol. In [HTTP/3](https://en.wikipedia.org/wiki/HTTP/3 "HTTP/3"), the [Transmission Control Protocol](https://en.wikipedia.org/wiki/Transmission_Control_Protocol "Transmission Control Protocol") (TCP) is no longer used, but the older versions are still more used and they most commonly use TCP. They have also been adapted to use unreliable protocols such as the [User Datagram Protocol](https://en.wikipedia.org/wiki/User_Datagram_Protocol "User Datagram Protocol") (UDP), which HTTP/3 also (indirectly) always builds on, for example in [HTTPU](https://en.wikipedia.org/wiki/HTTPU "HTTPU") and [Simple Service Discovery Protocol](https://en.wikipedia.org/wiki/Simple_Service_Discovery_Protocol "Simple Service Discovery Protocol") (SSDP).

[HTTP resources](https://en.wikipedia.org/wiki/Web_resource "Web resource") are identified and located on the network by [Uniform Resource Locators](https://en.wikipedia.org/wiki/Uniform_Resource_Locator "Uniform Resource Locator") (URLs), using the [Uniform Resource Identifiers](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier "Uniform Resource Identifier") (URIs) schemes _http_ and _[https](https://en.wikipedia.org/wiki/Https "Https")_. As defined in [RFC](https://en.wikipedia.org/wiki/RFC_\(identifier\) "RFC (identifier)") [3986](https://www.rfc-editor.org/rfc/rfc3986), URIs are encoded as [hyperlinks](https://en.wikipedia.org/wiki/Hyperlink "Hyperlink") in [HTML](https://en.wikipedia.org/wiki/HTML "HTML") documents, so as to form interlinked [hypertext](https://en.wikipedia.org/wiki/Hypertext "Hypertext") documents.

In HTTP/1.0 a separate TCP [connection](https://en.wikipedia.org/wiki/Connection-oriented_communication "Connection-oriented communication") to the same server is made for every resource request.

In HTTP/1.1 instead a TCP connection can be reused to make multiple resource requests (i.e. of HTML pages, frames, images, [scripts](https://en.wikipedia.org/wiki/Client-side_scripting "Client-side scripting"), [stylesheets](https://en.wikipedia.org/wiki/Cascading_Style_Sheets "Cascading Style Sheets"), etc.).

HTTP/1.1 communications therefore experience less [latency](https://en.wikipedia.org/wiki/Network_latency "Network latency") as the establishment of TCP connections presents considerable overhead, especially under high traffic conditions.

[HTTP/2](https://en.wikipedia.org/wiki/HTTP/2 "HTTP/2") is a revision of previous HTTP/1.1 in order to maintain the same client–server model and the same protocol methods but with these differences in order:

- to use a compressed binary representation of metadata (HTTP headers) instead of a textual one, so that headers require much less space;
- to use a single [TCP/IP](https://en.wikipedia.org/wiki/Internet_Protocol_suite "Internet Protocol suite") (usually [encrypted](https://en.wikipedia.org/wiki/Encryption "Encryption")) connection per accessed server domain instead of 2 to 8 TCP/IP connections;
- to use one or more bidirectional streams per TCP/IP connection in which HTTP requests and responses are broken down and transmitted in small packets to almost solve the problem of the HOLB ([head-of-line blocking](https://en.wikipedia.org/wiki/Head-of-line_blocking "Head-of-line blocking")).
- to add a push capability to allow server application to send data to clients whenever new data is available (without forcing clients to request periodically new data to server by using [polling](https://en.wikipedia.org/wiki/Polling_\(computer_science\) "Polling (computer science)") methods).

HTTP/2 communications therefore experience much less latency and, in most cases, even higher speeds than HTTP/1.1 communications.

[HTTP/3](https://en.wikipedia.org/wiki/HTTP/3 "HTTP/3") is a revision of previous HTTP/2 in order to use [QUIC](https://en.wikipedia.org/wiki/QUIC "QUIC") + UDP transport protocols instead of TCP. Before that version, TCP/IP connections were used; but now, only the IP layer is used (which UDP, like TCP, builds on). This slightly improves the average speed of communications and to avoid the occasional (very rare) problem of TCP connection [congestion](https://en.wikipedia.org/wiki/TCP_congestion_control "TCP congestion control") that can temporarily block or slow down the data flow of all its streams (another form of "_head of line blocking_").

### HTTP data exchange
HTTP is a [stateless](https://en.wikipedia.org/wiki/Stateless_protocol "Stateless protocol") application-level protocol and it requires a reliable network transport connection to exchange data between client and server. In HTTP implementations, [TCP/IP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol "Transmission Control Protocol") connections are used using [well-known ports](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#Well-known_ports "List of TCP and UDP port numbers") (typically [port 80](https://en.wikipedia.org/wiki/TCP_port "TCP port") if the connection is unencrypted or port 443 if the connection is encrypted, see also [List of TCP and UDP port numbers](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers "List of TCP and UDP port numbers")). In HTTP/2, a TCP/IP connection plus multiple protocol channels are used. In HTTP/3, the application transport protocol [QUIC](https://en.wikipedia.org/wiki/QUIC "QUIC") over UDP is used.

#### Request and response messages through connections
Data is exchanged through a sequence of [request–response messages](https://en.wikipedia.org/wiki/Request-response "Request-response") which are exchanged by a [session layer](https://en.wikipedia.org/wiki/Session_layer "Session layer") transport connection. An HTTP client initially tries to connect to a server establishing a connection (real or virtual). An HTTP(S) server listening on that port accepts the connection and then waits for a client's request message. The client sends its HTTP request message. Upon receiving the request the server sends back an HTTP response message, which includes header(s) plus a body if it is required. The body of this response message is typically the requested resource, although an error message or other information may also be returned. At any time (for many reasons) client or server can close the connection. Closing a connection is usually advertised in advance by using one or more HTTP headers in the last request/response message sent to server or client.

#### Persistent connections
In **HTTP/0.9**, the TCP/IP connection is always closed after server response has been sent, so it is never persistent.

In **HTTP/1.0**, as stated in RFC 1945, the TCP/IP connection should always be closed by server after a response has been sent.

In **HTTP/1.1** a keep-alive-mechanism was officially introduced so that a connection could be reused for more than one request/response. Such persistent connections reduce request [latency](https://en.wikipedia.org/wiki/Network_latency "Network latency") perceptibly because the client does not need to re-negotiate the [TCP 3-Way-Handshake connection](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#Connection_establishment "Transmission Control Protocol") after the first request has been sent. Another positive side effect is that, in general, the connection becomes faster with time due to TCP's [slow-start](https://en.wikipedia.org/wiki/TCP_congestion_control#Slow_start "TCP congestion control")-mechanism.

**HTTP/1.1** added also [HTTP pipelining](https://en.wikipedia.org/wiki/HTTP_pipelining "HTTP pipelining") in order to further reduce lag time when using persistent connections by allowing clients to send multiple requests before waiting for each response. This optimization was never considered really safe because a few web servers and many [proxy servers](https://en.wikipedia.org/wiki/Proxy_server "Proxy server"), specially transparent proxy servers placed in Internet / [Intranets](https://en.wikipedia.org/wiki/Intranet "Intranet") between clients and servers, did not handle pipelined requests properly (they served only the first request discarding the others, they closed the connection because they saw more data after the first request or some proxies even returned responses out of order etc.). Because of this, only HEAD and some GET requests (i.e. limited to real file requests and so with [URLs](https://en.wikipedia.org/wiki/URL "URL") without query string used as a command, etc.) could be pipelined in a [safe](https://en.wikipedia.org/wiki/HTTP#Safe_methods) and [idempotent](https://en.wikipedia.org/wiki/HTTP#Idempotent_methods) mode. After many years of struggling with the problems introduced by enabling pipelining, this feature was first disabled and then removed from most browsers also because of the announced adoption of HTTP/2.

**HTTP/2** extended the usage of persistent connections by multiplexing many concurrent requests/responses through a single TCP/IP connection.

**HTTP/3** does not use TCP/IP connections but QUIC + UDP (see also: [technical overview](https://en.wikipedia.org/wiki/HTTP#Technical_overview)).

#### Content retrieval optimizations
HTTP/0.9

A requested resource was always sent in its entirety.

HTTP/1.0

HTTP/1.0 added headers to manage resources cached by client in order to allow conditional GET requests; in practice a server has to return the entire content of the requested resource only if its last modified time is not known by client or if it changed since last full response to GET request. One of these headers, "Content-Encoding", was added to specify whether the returned content of a resource was or was not [compressed](https://en.wikipedia.org/wiki/HTTP_compression "HTTP compression").

If the total length of the content of a resource was not known in advance (i.e. because it was dynamically generated, etc.) then the header `"Content-Length: number"` was not present in HTTP headers and the client assumed that when server closed the connection, the content had been sent in its entirety. This mechanism could not distinguish between a resource transfer successfully completed and an interrupted one (because of a server / network error or something else).

HTTP/1.1

HTTP/1.1 introduced:

- new headers to better manage the conditional retrieval of cached resources.
- [chunked transfer encoding](https://en.wikipedia.org/wiki/Chunked_transfer_encoding "Chunked transfer encoding") to allow content to be streamed in chunks in order to reliably send it even when the server does not know its length in advance (i.e. because it is dynamically generated, etc.).
- [byte range serving](https://en.wikipedia.org/wiki/Byte_serving "Byte serving"), where a client can request only one or more portions (ranges of bytes) of a resource (i.e. the first part, a part in the middle or in the end of the entire content, etc.) and the server usually sends only the requested part(s). This is useful to resume an interrupted download (when a file is very large), when only a part of a content has to be shown or dynamically added to the already visible part by a browser (i.e. only the first or the following n comments of a web page) in order to spare time, bandwidth and system resources, etc.

HTTP/2, HTTP/3

Both HTTP/2 and HTTP/3 have kept the above mentioned features of HTTP/1.1.

### HTTP authentication
HTTP provides multiple authentication schemes such as [basic access authentication](https://en.wikipedia.org/wiki/Basic_access_authentication "Basic access authentication") and [digest access authentication](https://en.wikipedia.org/wiki/Digest_access_authentication "Digest access authentication") which operate via a challenge–response mechanism whereby the server identifies and issues a challenge before serving the requested content.

HTTP provides a general framework for access control and authentication, via an extensible set of challenge–response authentication schemes, which can be used by a server to challenge a client request and by a client to provide authentication information.

The authentication mechanisms described above belong to the HTTP protocol and are managed by client and server HTTP software (if configured to require authentication before allowing client access to one or more web resources), and not by the web applications using [a web application session](https://en.wikipedia.org/wiki/HTTP#HTTP_application_session).

#### Authentication realms
The HTTP Authentication specification also provides an arbitrary, implementation-specific construct for further dividing resources common to a given root [URI](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier "Uniform Resource Identifier"). The realm value string, if present, is combined with the canonical root URI to form the protection space component of the challenge. This in effect allows the server to define separate authentication scopes under one root URI.

### HTTP application session
HTTP is a [stateless protocol](https://en.wikipedia.org/wiki/Stateless_protocol "Stateless protocol"). A stateless protocol does not require the web server to retain information or status about each user for the duration of multiple requests.

Some [web applications](https://en.wikipedia.org/wiki/Web_application "Web application") need to manage user sessions, so they implement states, or [server side sessions](https://en.wikipedia.org/wiki/Session_\(computer_science\) "Session (computer science)"), using for instance [HTTP cookies](https://en.wikipedia.org/wiki/HTTP_cookie "HTTP cookie") or hidden [variables](https://en.wikipedia.org/wiki/Variable_\(computer_science\) "Variable (computer science)") within [web forms](https://en.wikipedia.org/wiki/Form_\(web\) "Form (web)").

To start an application user session, an interactive [authentication](https://en.wikipedia.org/wiki/Authentication "Authentication") via web application [login](https://en.wikipedia.org/wiki/Login "Login") must be performed. To stop a user session a [logout](https://en.wikipedia.org/wiki/Logout "Logout") operation must be requested by user. These kind of operations do not use [HTTP authentication](https://en.wikipedia.org/wiki/HTTP#HTTP_authentication) but a custom managed web application authentication.

### HTTP/1.1 request messages
Request messages are sent by a client to a target server.

#### Request syntax

A client sends _request messages_ to the server, which consist of:
- a **request line**, consisting of the case-sensitive request method, a [space](https://en.wikipedia.org/wiki/Space_\(punctuation\) "Space (punctuation)"), the requested URI, another space, the protocol version, a [carriage return](https://en.wikipedia.org/wiki/Carriage_return "Carriage return"), and a [line feed](https://en.wikipedia.org/wiki/Line_feed "Line feed"), e.g.:

```http
GET /images/logo.png HTTP/1.1
```

- zero or more [request header fields](https://en.wikipedia.org/wiki/HTTP_request_header_field "HTTP request header field") (at least 1 or more headers in case of HTTP/1.1), each consisting of the case-insensitive field name, a colon, optional leading [whitespace](https://en.wikipedia.org/wiki/Whitespace_\(computer_science\) "Whitespace (computer science)"), the field value, an optional trailing whitespace and ending with a carriage return and a line feed, e.g.:

Host: www.example.com
Accept-Language: en

- an empty line, consisting of a carriage return and a line feed;
- an optional [message body](https://en.wikipedia.org/wiki/HTTP_message_body "HTTP message body").

In the HTTP/1.1 protocol, all header fields except `Host: hostname` are optional.

A request line containing only the path name is accepted by servers to maintain compatibility with HTTP clients before the HTTP/1.0 specification in [RFC](https://en.wikipedia.org/wiki/RFC_\(identifier\) "RFC (identifier)") [1945](https://www.rfc-editor.org/rfc/rfc1945).

#### Request methods

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c6/Http_request_telnet_ubuntu.png/250px-Http_request_telnet_ubuntu.png)](https://en.wikipedia.org/wiki/File:Http_request_telnet_ubuntu.png)

An HTTP/1.1 request made using telnet. The [request](https://en.wikipedia.org/wiki/HTTP_request "HTTP request") message, [response](https://en.wikipedia.org/wiki/HTTP_response "HTTP response") header section, and response body are highlighted.

HTTP defines methods (sometimes referred to as _verbs_, but nowhere in the specification does it mention _verb_) to indicate the desired action to be performed on the identified resource. What this resource represents, whether pre-existing data or data that is generated dynamically, depends on the implementation of the server. Often, the resource corresponds to a file or the output of an executable residing on the server. The HTTP/1.0 specification defined the GET, HEAD, and POST methods as well as listing the PUT, DELETE, LINK and UNLINK methods under additional methods. However, the HTTP/1.1 specification formally defined and added five new methods: PUT, DELETE, CONNECT, OPTIONS, and TRACE. Any client can use any method and the server can be configured to support any combination of methods. If a method is unknown to an intermediate, it will be treated as an unsafe and [non-idempotent](https://en.wikipedia.org/wiki/Idempotence "Idempotence") method. There is no limit to the number of methods that can be defined, which allows for future methods to be specified without breaking existing infrastructure. For example, [WebDAV](https://en.wikipedia.org/wiki/WebDAV "WebDAV") defined seven new methods and [RFC](https://en.wikipedia.org/wiki/RFC_\(identifier\) "RFC (identifier)") [5789](https://www.rfc-editor.org/rfc/rfc5789) specified the [PATCH](https://en.wikipedia.org/wiki/PATCH_\(HTTP\) "PATCH (HTTP)") method.

Method names are case sensitive. This is in contrast to HTTP header field names which are case-insensitive.
GET

The GET method requests that the target resource transfer a representation of its state. GET requests should only [retrieve data](https://en.wikipedia.org/wiki/Data_retrieval "Data retrieval") and should have no other effect. (This is also true of some other HTTP methods. For retrieving resources without making changes, GET is preferred over POST, as they can be [addressed](https://en.wikipedia.org/wiki/Addressability "Addressability") through a [URL](https://en.wikipedia.org/wiki/URL "URL"). This enables bookmarking and sharing and makes GET responses eligible for [caching](https://en.wikipedia.org/wiki/Browser_cache "Browser cache"), which can save bandwidth. The [W3C](https://en.wikipedia.org/wiki/W3C "W3C") has published guidance principles on this distinction, saying, "[Web application](https://en.wikipedia.org/wiki/Web_application "Web application") design should be informed by the above principles, but also by the relevant limitations.

**HEAD**
The HEAD method requests that the target resource transfer a representation of its state, as for a GET request, but without the representation data enclosed in the response body. This is useful for retrieving the representation metadata in the response header, without having to transfer the entire representation. Uses include checking whether a page is available through the [status code](https://en.wikipedia.org/wiki/HTTP_status_code "HTTP status code") and quickly finding the size of a [file](https://en.wikipedia.org/wiki/Computer_file "Computer file") (`Content-Length`).

**POST**
The [POST method](https://en.wikipedia.org/wiki/POST_\(HTTP\) "POST (HTTP)") requests that the target resource process the representation enclosed in the request according to the semantics of the target resource. For example, it is used for posting a message to an [Internet forum](https://en.wikipedia.org/wiki/Internet_forum "Internet forum"), subscribing to a [mailing list](https://en.wikipedia.org/wiki/Mailing_list "Mailing list"), or completing an [online shopping](https://en.wikipedia.org/wiki/Online_shopping "Online shopping") transaction.

**PUT**
The PUT method requests that the target resource create or update its state with the state defined by the representation enclosed in the request. A distinction from POST is that the client specifies the target location on the server.

**DELETE**
The DELETE method requests that the target resource delete its state.

**CONNECT**
The CONNECT method requests that the intermediary establish a [TCP/IP tunnel](https://en.wikipedia.org/wiki/Tunneling_protocol "Tunneling protocol") to the origin server identified by the request target. It is often used to secure connections through one or more [HTTP proxies](https://en.wikipedia.org/wiki/HTTP_proxy "HTTP proxy") with [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security").

**OPTIONS**
The OPTIONS method requests that the target resource transfer the HTTP methods that it supports. This can be used to check the functionality of a web server by requesting '*' instead of a specific resource.

**TRACE**
The TRACE method requests that the target resource transfer the received request in the response body. That way a client can see what (if any) changes or additions have been made by intermediaries.

**PATCH**
The [PATCH method](https://en.wikipedia.org/wiki/PATCH_\(HTTP\) "PATCH (HTTP)") requests that the target resource modify its state according to the partial update defined in the representation enclosed in the request. This can save bandwidth by updating a part of a file or document without having to transfer it entirely.

All general-purpose web servers are required to implement at least the GET and HEAD methods, and all other methods are considered optional by the specification.

##### Safe methods
A request method is _safe_ if a request with that method has no intended effect on the server. The methods GET, HEAD, OPTIONS, and TRACE are defined as safe. In other words, safe methods are intended to be [read-only](https://en.wikipedia.org/wiki/Command%E2%80%93query_separation "Command–query separation"). Safe methods can still have [side effects](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\) "Side effect (computer science)") not seen by the client, such as appending request information to a [log file](https://en.wikipedia.org/wiki/Server_log "Server log") or charging an [advertising account](https://en.wikipedia.org/wiki/Web_banner "Web banner").

In contrast, the methods POST, PUT, DELETE, CONNECT, and PATCH are not safe. They may modify the state of the server or have other effects such as sending an [email](https://en.wikipedia.org/wiki/Email "Email"). Such methods are therefore not usually used by conforming [web robots](https://en.wikipedia.org/wiki/Internet_bot "Internet bot") or web crawlers; some that do not conform tend to make requests without regard to context or consequences.

Despite the prescribed safety of GET requests, in practice their handling by the server is not technically limited in any way. Careless or deliberately irregular programming can allow GET requests to cause non-trivial changes on the server. This is discouraged because of the problems which can occur when [web caching](https://en.wikipedia.org/wiki/Web_caching "Web caching"), [search engines](https://en.wikipedia.org/wiki/Search_engines "Search engines"), and other automated agents make unintended changes on the server. For example, a website might allow deletion of a resource through a URL such as _https://example.com/article/1234/delete_, which, if arbitrarily fetched, even using GET, would simply delete the article. A properly coded website would require a DELETE or POST method for this action, which non-malicious bots would not make.

One example of this occurring in practice was during the short-lived [Google Web Accelerator](https://en.wikipedia.org/wiki/Google_Web_Accelerator "Google Web Accelerator") beta, which prefetched arbitrary URLs on the page a user was viewing, causing records to be automatically altered or deleted _en masse_. The [beta](https://en.wikipedia.org/wiki/Beta_test "Beta test") was suspended only weeks after its first release, following widespread criticism.

##### Idempotent methods
A request method is _idempotent_ if multiple identical requests with that method have the same effect as a single such request. The methods PUT and DELETE, and safe methods are defined as idempotent. Safe methods are trivially idempotent, since they are intended to have no effect on the server whatsoever; the PUT and DELETE methods, meanwhile, are idempotent since successive identical requests will be ignored. A website might, for instance, set up a PUT endpoint to modify a user's recorded email address. If this endpoint is configured correctly, any requests which ask to change a user's email address to the same email address which is already recorded—e.g. duplicate requests following a successful request—will have no effect. Similarly, a request to DELETE a certain user will have no effect if that user has already been deleted.

In contrast, the methods POST, CONNECT, and PATCH are not necessarily idempotent, and therefore sending an identical POST request multiple times may further modify the state of the server or have further effects, such as sending multiple [emails](https://en.wikipedia.org/wiki/Email "Email"). In some cases this is the desired effect, but in other cases it may occur accidentally. A user might, for example, inadvertently send multiple POST requests by clicking a button again if they were not given clear feedback that the first click was being processed. While [web browsers](https://en.wikipedia.org/wiki/Web_browser "Web browser") may show [alert dialog boxes](https://en.wikipedia.org/wiki/Alert_dialog_box "Alert dialog box") to warn users in some cases where reloading a page may re-submit a POST request, it is generally up to the web application to handle cases where a POST request should not be submitted more than once.

Note that whether or not a method is idempotent is not enforced by the protocol or web server. It is perfectly possible to write a web application in which (for example) a database insert or other non-idempotent action is triggered by a GET or other request. To do so against recommendations, however, may result in undesirable consequences, if a [user agent](https://en.wikipedia.org/wiki/User_agent "User agent") assumes that repeating the same request is safe when it is not.

##### Cacheable methods
A request method is _cacheable_ if responses to requests with that method may be stored for future reuse. The methods GET, HEAD, and POST are defined as cacheable.

In contrast, the methods PUT, DELETE, CONNECT, OPTIONS, TRACE, and PATCH are not cacheable.

#### Request header fields
Request header fields allow the client to pass additional information beyond the request line, acting as request modifiers (similarly to the parameters of a procedure). They give information about the client, about the target resource, or about the expected handling of the request.

### HTTP/1.1 response messages
A response message is sent by a server to a client as a reply to its former request message.

#### Response syntax
A server sends _response messages_ to the client, which consist of:
- a **status line**, consisting of the protocol version, a [space](https://en.wikipedia.org/wiki/Space_\(punctuation\) "Space (punctuation)"), the [response status code](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes "List of HTTP status codes"), another space, a possibly empty reason phrase, a [carriage return](https://en.wikipedia.org/wiki/Carriage_return "Carriage return") and a [line feed](https://en.wikipedia.org/wiki/Line_feed "Line feed"), e.g.:
```http
    HTTP/1.1 200 OK
```

- zero or more [response header fields](https://en.wikipedia.org/wiki/HTTP_response_header_field "HTTP response header field"), each consisting of the case-insensitive field name, a colon, optional leading [whitespace](https://en.wikipedia.org/wiki/Whitespace_\(computer_science\) "Whitespace (computer science)"), the field value, an optional trailing whitespace and ending with a carriage return and a line feed, e.g.:
    
    Content-Type: text/html
    
- an empty line, consisting of a carriage return and a line feed;
- an optional [message body](https://en.wikipedia.org/wiki/HTTP_message_body "HTTP message body").

#### Response status codes
In HTTP/1.0 and since, the first line of the HTTP response is called the _status line_ and includes a numeric _status code_ (such as "[404](https://en.wikipedia.org/wiki/HTTP_404 "HTTP 404")") and a textual _reason phrase_ (such as "Not Found"). The response status code is a three-digit integer code representing the result of the server's attempt to understand and satisfy the client's corresponding request. The way the client handles the response depends primarily on the status code, and secondarily on the other response header fields. Clients may not understand all registered status codes but they must understand their class (given by the first digit of the status code) and treat an unrecognized status code as being equivalent to the x00 status code of that class.

The standard _reason phrases_ are only recommendations, and can be replaced with "local equivalents" at the [web developer](https://en.wikipedia.org/wiki/Web_developer "Web developer")'s discretion. If the status code indicated a problem, the user agent might display the _reason phrase_ to the user to provide further information about the nature of the problem. The standard also allows the user agent to attempt to interpret the _reason phrase_, though this might be unwise since the standard explicitly specifies that status codes are machine-readable and _reason phrases_ are human-readable.

The first digit of the status code defines its class:

`1XX` (informational)

The request was received, continuing process.

`2XX` (successful)

The request was successfully received, understood, and accepted.

`3XX` (redirection)

Further action needs to be taken in order to complete the request.

`4XX` (client error)

The request contains bad syntax or cannot be fulfilled.

`5XX` (server error)

The server failed to fulfill an apparently valid request.

#### Response header fields
The response header fields allow the server to pass additional information beyond the status line, acting as response modifiers. They give information about the server or about further access to the target resource or related resources.

Each response header field has a defined meaning which can be further refined by the semantics of the request method or response status code.

### HTTP/1.1 example of request / response transaction
Below is a sample HTTP transaction between an HTTP/1.1 client and an HTTP/1.1 server running on [www.example.com](https://en.wikipedia.org/wiki/Example.com "Example.com"), port 80.

#### Client request
```http
GET / HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-GB,en;q=0.5
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
```

A client request (consisting in this case of the request line and a few headers that can be reduced to only the `"Host: hostname"` header) is followed by a blank line, so that the request ends with a double end of line, each in the form of a [carriage return](https://en.wikipedia.org/wiki/Carriage_return "Carriage return") followed by a [line feed](https://en.wikipedia.org/wiki/Line_feed "Line feed"). The `"Host: hostname"` header value distinguishes between various [DNS](https://en.wikipedia.org/wiki/Domain_Name_System "Domain Name System") names sharing a single [IP address](https://en.wikipedia.org/wiki/IP_address "IP address"), allowing name-based [virtual hosting](https://en.wikipedia.org/wiki/Virtual_hosting "Virtual hosting"). While optional in HTTP/1.0, it is mandatory in HTTP/1.1. (A "/" (slash) will usually fetch a [/index.html](https://en.wikipedia.org/wiki/Webserver_directory_index "Webserver directory index") file if there is one.)

#### Server response
```http 
HTTP/1.1 200 OK
Date: Mon, 23 May 2005 22:38:34 GMT
Content-Type: text/html; charset=UTF-8
Content-Length: 155
Last-Modified: Wed, 08 Jan 2003 23:11:55 GMT
Server: Apache/1.3.3.7 (Unix) (Red-Hat/Linux)
ETag: "3f80f-1b6-3e1cb03b"
Accept-Ranges: bytes
Connection: close
```
<html>
  <head>
    <title>An Example Page</title>
  </head>
  <body>
    <p>Hello World, this is a very simple HTML document.</p>
  </body>
</html>

The [ETag](https://en.wikipedia.org/wiki/HTTP_ETag "HTTP ETag") (entity tag) header field is used to determine if a cached version of the requested resource is identical to the current version of the resource on the server. `"Content-Type"` specifies the [Internet media type](https://en.wikipedia.org/wiki/Internet_media_type "Internet media type") of the data conveyed by the HTTP message, while `"Content-Length"` indicates its length in bytes. The HTTP/1.1 [webserver](https://en.wikipedia.org/wiki/Webserver "Webserver") publishes its ability to respond to requests for certain byte ranges of the document by setting the field `"Accept-Ranges: bytes"`. This is useful, if the client needs to have only certain portions of a resource sent by the server, which is called [byte serving](https://en.wikipedia.org/wiki/Byte_serving "Byte serving"). When `"Connection: close"` is sent, it means that the [web server](https://en.wikipedia.org/wiki/Web_server "Web server") will close the [TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol "Transmission Control Protocol") connection immediately after the end of the transfer of this response.

Most of the header lines are optional but some are mandatory. When header `"Content-Length: number"` is missing in a response with an entity body then this should be considered an error in HTTP/1.0 but it may not be an error in HTTP/1.1 if header `"Transfer-Encoding: chunked"` is present. Chunked transfer encoding uses a chunk size of 0 to mark the end of the content. Some old implementations of HTTP/1.0 omitted the header `"Content-Length"` when the length of the body entity was not known at the beginning of the response and so the transfer of data to client continued until server closed the socket.

A `"Content-Encoding: [gzip](https://en.wikipedia.org/wiki/Gzip "Gzip")"` can be used to inform the client that the body entity part of the transmitted data is compressed by gzip algorithm.

### Encrypted connections
The most popular way of establishing an encrypted HTTP connection is [HTTPS](https://en.wikipedia.org/wiki/HTTPS "HTTPS"). Two other methods for establishing an encrypted HTTP connection also exist: [Secure Hypertext Transfer Protocol](https://en.wikipedia.org/wiki/Secure_Hypertext_Transfer_Protocol "Secure Hypertext Transfer Protocol"), and using the [HTTP/1.1 Upgrade header](https://en.wikipedia.org/wiki/HTTP/1.1_Upgrade_header "HTTP/1.1 Upgrade header") to specify an upgrade to TLS. Browser support for these two is, however, nearly non-existent.

## HTTP Persistent Connection
**[HTTP](https://en.wikipedia.org/wiki/HTTP "HTTP") persistent connection**, also called **HTTP keep-alive**, or **HTTP connection reuse**, is the idea of using a single [TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol "Transmission Control Protocol") connection to send and receive multiple [HTTP requests](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol "Hypertext Transfer Protocol")/responses, as opposed to opening a new connection for every single request/response pair. The newer [HTTP/2](https://en.wikipedia.org/wiki/HTTP/2 "HTTP/2") protocol uses the same idea and takes it further to allow multiple concurrent requests/responses to be multiplexed over a single connection.

### Operation
#### HTTP 1.0
Under HTTP 1.0, connections should always be **closed** by the server after sending the response.

Since at least late 1995, developers of popular products (browsers, web servers, etc.) using HTTP/1.0, started to add an unofficial extension (to the protocol) named "keep-alive" in order to allow the reuse of a connection for multiple requests/responses.

If the client supports keep-alive, it adds an additional header to the request:

```http
Connection: keep-alive
```

When the server receives this request and generates a response, if it supports keep-alive then it also adds the same above header to the response. Following this, the connection is not dropped, but is instead kept open. When the client sends another request, it uses the same connection.

This will continue until either the client or the server decides that the conversation is over and in this case they omit the `"Connection:"` header from the last message sent or, better, they add the keyword "close" to it:

Connection: close

After that the connection is closed following specified rules.

Since 1997, the various versions of HTTP/1.1 specifications acknowledged the usage of this unofficial extension and included a few caveats regarding the interoperability between HTTP/1.0 (keep-alive) and HTTP/1.1 clients / servers.

#### HTTP 1.1
In HTTP 1.1, all connections are considered persistent unless declared otherwise. The HTTP **persistent connections** do not use separate keepalive messages, they just allow multiple requests to use a single connection. However, the default connection timeout of Apache httpd 1.3 and 2.0 is as little as 15 seconds and just 5 seconds for Apache httpd 2.2 and above. The advantage of a short timeout is the ability to deliver multiple components of a web page quickly while not consuming resources to run multiple server processes or threads for too long.

##### Keepalive with [chunked transfer encoding](https://en.wikipedia.org/wiki/Chunked_transfer_encoding "Chunked transfer encoding")

Keepalive makes it difficult for the client to determine where one response ends and the next response begins, particularly during pipelined HTTP operation. This is a serious problem when `Content-Length` cannot be used due to streaming. To solve this problem, HTTP 1.1 introduced a [chunked transfer coding](https://en.wikipedia.org/wiki/Chunked_transfer_coding "Chunked transfer coding") that defines a `last-chunk` bit. The `last-chunk` bit is set at the end of each response so that the client knows where the next response begins.

### Advantages
- Reduced [latency](https://en.wikipedia.org/wiki/Latency_\(engineering\) "Latency (engineering)") in subsequent requests (no [handshaking](https://en.wikipedia.org/wiki/Handshake_\(computing\) "Handshake (computing)") and no [slow start](https://en.wikipedia.org/wiki/TCP_congestion_control#Slow_start "TCP congestion control")).
- Reduced [CPU](https://en.wikipedia.org/wiki/CPU "CPU") usage and round-trips because of fewer new connections and [TLS handshakes](https://en.wikipedia.org/wiki/Transport_Layer_Security#TLS_handshake "Transport Layer Security").
- Enables [HTTP pipelining](https://en.wikipedia.org/wiki/HTTP_pipelining "HTTP pipelining") of requests and responses.
- Reduced [network congestion](https://en.wikipedia.org/wiki/Network_congestion "Network congestion") (fewer [TCP connections](https://en.wikipedia.org/wiki/Transmission_Control_Protocol "Transmission Control Protocol")).
- Errors can be reported without the penalty of closing the TCP connection.

According to [RFC 7230, section 6.4](http://tools.ietf.org/html/rfc7230#section-6.4), "a client ought to limit the number of simultaneous open connections that it maintains to a given server". The previous version of the HTTP/1.1 specification [stated specific maximum values](http://tools.ietf.org/html/rfc2616#section-8.1.4) but in the words of RFC 7230 "this was found to be impractical for many applications... instead... be conservative when opening multiple connections". These guidelines are intended to improve HTTP response times and avoid congestion. If HTTP pipelining is correctly implemented, there is no performance benefit to be gained from additional connections, while additional connections may cause issues with congestion.

### Disadvantages
If the client does not close the connection when all of the data it needs has been received, the resources needed to keep the connection open on the server will be unavailable for other clients. How much this affects the server's availability and how long the resources are unavailable depend on the server's architecture and configuration.

Also a [race condition](https://en.wikipedia.org/wiki/Race_condition "Race condition") can occur where the client sends a request to the server at the same time that the server closes the TCP connection. A server should send a 408 Request Timeout status code to the client immediately before closing the connection. When a client receives the 408 status code, after having sent the request, it may open a new connection to the server and re-send the request. Not all clients will re-send the request, and many that do will only do so if the request has an [idempotent HTTP method](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Idempotent_methods_and_web_applications "Hypertext Transfer Protocol").

### Use in web browsers
[![](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d5/HTTP_persistent_connection.svg/330px-HTTP_persistent_connection.svg.png)](https://en.wikipedia.org/wiki/File:HTTP_persistent_connection.svg)

Schema of multiple vs. persistent connection.

All modern web browsers including [Google Chrome](https://en.wikipedia.org/wiki/Google_Chrome "Google Chrome"), [Firefox](https://en.wikipedia.org/wiki/Firefox "Firefox"), [Microsoft Edge](https://en.wikipedia.org/wiki/Microsoft_Edge "Microsoft Edge"), [Opera](https://en.wikipedia.org/wiki/Opera_\(web_browser\) "Opera (web browser)") (since 4.0) and [Safari](https://en.wikipedia.org/wiki/Safari_\(web_browser\) "Safari (web browser)") use persistent connections.

In [Firefox](https://en.wikipedia.org/wiki/Firefox "Firefox"), the number of simultaneous connections can be customized (per-server, per-proxy, total). Persistent connections time out after 115 seconds (1.92 minutes) of inactivity which is changeable via the configuration.

### Implementation
Python's `requests` library contains `requests.Session()`, which establishes a persistent HTTP connection, thereby allowing the underlying TCP connection to be reused, which can result in a significant performance increase.

## Chunked Transfer Encoding
**Chunked transfer encoding** is a [streaming](https://en.wikipedia.org/wiki/Stream_\(computing\) "Stream (computing)") data transfer mechanism available in [Hypertext Transfer Protocol](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol "Hypertext Transfer Protocol") (HTTP) version 1.1, defined in [RFC 9112 §7.1](https://datatracker.ietf.org/doc/html/rfc9112#section-7.1 "rfc:9112"). In chunked transfer encoding, the data stream is divided into a series of non-overlapping "chunks". The chunks are sent out and received independently of one another. No knowledge of the data stream outside the currently-being-processed chunk is necessary for both the sender and the receiver at any given time.

Each chunk is preceded by its size in bytes. The transmission ends when a zero-length chunk is received. The _chunked_ keyword in the [Transfer-Encoding](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields#transfer-encoding-response-header "List of HTTP header fields") header is used to indicate chunked transfer.

Chunked transfer encoding is not supported in [HTTP/2](https://en.wikipedia.org/wiki/HTTP/2 "HTTP/2"), which provides its own mechanisms for data streaming.

### Rationale
The introduction of chunked encoding provided various benefits:

- Chunked transfer encoding allows a server to maintain an [HTTP persistent connection](https://en.wikipedia.org/wiki/HTTP_persistent_connection "HTTP persistent connection") for dynamically generated content. In this case, the HTTP Content-Length header cannot be used to delimit the content and the next HTTP request/response, as the content size is not yet known. Chunked encoding has the benefit that it is not necessary to generate the full content before writing the header, as it allows streaming of content as chunks and explicitly signaling the end of the content, making the connection available for the next HTTP request/response.
- Chunked encoding allows the sender to send additional header fields after the message body. This is important in cases where values of a field cannot be known until the content has been produced, such as when the content of the message must be digitally signed. Without chunked encoding, the sender would have to buffer the content until it was complete in order to calculate a field value and send it before the content.

### Applicability
For version 1.1 of the HTTP protocol, the chunked transfer mechanism is considered to be always and anyway acceptable, even if not listed in the [TE](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields#te-request-header "List of HTTP header fields") (transfer encoding) request header field, and when used with other transfer mechanisms, should always be applied last to the transferred data and never more than one time. This transfer coding method also allows additional entity header fields to be sent after the last chunk if the client specified the "trailers" parameter as an argument of the TE field. The origin server of the response can also decide to send additional entity trailers even if the client did not specify the "trailers" option in the TE request field, but only if the metadata is optional (i.e. the client can use the received entity without them). Whenever the trailers are used, the server should list their names in the Trailer header field; three header field types are specifically prohibited from appearing as a trailer field: [Transfer-Encoding](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields#transfer-encoding-response-header "List of HTTP header fields"), [Content-Length](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields#content-length-response-header "List of HTTP header fields") and [Trailer](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields#trailer-response-header "List of HTTP header fields").

### Format
If a Transfer-Encoding field with a value of "chunked" is specified in an HTTP message (either a request sent by a client or the response from the server), the body of the message consists of one or more chunks and one terminating chunk with an optional trailer before the final ␍␊ sequence (i.e. [carriage return](https://en.wikipedia.org/wiki/Carriage_return "Carriage return") followed by [line feed](https://en.wikipedia.org/wiki/Line_feed "Line feed")).

Each chunk starts with the number of [octets](https://en.wikipedia.org/wiki/Octet_\(computing\) "Octet (computing)") of the data it embeds expressed as a [hexadecimal](https://en.wikipedia.org/wiki/Hexadecimal "Hexadecimal") number in [ASCII](https://en.wikipedia.org/wiki/ASCII "ASCII") followed by optional parameters (_chunk extension_) and a terminating ␍␊ sequence, followed by the chunk data. The chunk is terminated by ␍␊.

If chunk extensions are provided, the chunk size is terminated by a semicolon and followed by the parameters, each also delimited by semicolons. Each parameter is encoded as an extension name followed by an optional equal sign and value. These parameters could be used for a running [message digest](https://en.wikipedia.org/wiki/Message_digest "Message digest") or [digital signature](https://en.wikipedia.org/wiki/Digital_signature "Digital signature"), or to indicate an estimated transfer progress, for instance.

The terminating chunk is a special chunk of zero length. It may contain a trailer, which consists of a (possibly empty) sequence of entity header fields. Normally, such header fields would be sent in the message's header; however, it may be more efficient to determine them after processing the entire message entity. In that case, it is useful to send those headers in the trailer.

Header fields that regulate the use of trailers are _TE_ (used in requests), and _Trailers_ (used in responses).

### Use with compression
HTTP servers often use [compression](https://en.wikipedia.org/wiki/Data_compression "Data compression") to optimize transmission, for example with Content-Encoding: [gzip](https://en.wikipedia.org/wiki/Gzip "Gzip") or Content-Encoding: [deflate](https://en.wikipedia.org/wiki/Deflate "Deflate"). If both compression and chunked encoding are enabled, then the content stream is first compressed, then chunked; so the chunk encoding itself is not compressed, and the data in each chunk is compressed individually. The remote endpoint then decodes the stream by concatenating the chunks and uncompressing the result.

### Example
#### Encoded data
The following example contains three chunks of size 4, 7, and 11 (hexadecimal "B") octets of data.
```
4␍␊Wiki␍␊7␍␊pedia i␍␊B␍␊n ␍␊chunks.␍␊0␍␊␍␊
```

Below is an annotated version of the encoded data.
```
4␍␊            _(chunk size is four octets)_
Wiki           _(four octets of data)_
␍␊             _(end of chunk)_

7␍␊            _(chunk size is seven octets)_
pedia i        _(seven octets of data)_
␍␊             _(end of chunk)_

B␍␊            _(chunk size is eleven octets)_
n ␍␊chunks.    _(eleven octets of data)_
␍␊             _(end of chunk)_

0␍␊            _(chunk size is zero octets, no more chunks)_
␍␊             _(end of final chunk with zero data octets)_
```

Note: Each chunk's size excludes the two ␍␊ bytes that terminate the data of each chunk.

#### Decoded data
Decoding the above example produces the following octets:
```
Wikipedia in ␍␊chunks.
```

The bytes above are typically displayed as
```
Wikipedia in 
chunks.
```


## Snapshot (Computer Storage)
In [computer systems](https://en.wikipedia.org/wiki/Computer "Computer"), a **snapshot** is the [state](https://en.wikipedia.org/wiki/State_\(computer_science\) "State (computer science)") of a system at a particular point in time. The term was coined as an analogy to that in [photography](https://en.wikipedia.org/wiki/Snapshot_\(photography\) "Snapshot (photography)").

### Rationale
A full [backup](https://en.wikipedia.org/wiki/Backup "Backup") of a large data set may take a long time to complete. On [multi-tasking](https://en.wikipedia.org/wiki/Computer_multitasking "Computer multitasking") or [multi-user systems](https://en.wikipedia.org/wiki/Multi-user_systems "Multi-user systems"), there may be writes to that data while it is being backed up. This prevents the backup from being [atomic](https://en.wikipedia.org/wiki/Atomicity_\(database_systems\) "Atomicity (database systems)") and introduces a version skew that may result in [data corruption](https://en.wikipedia.org/wiki/Data_corruption "Data corruption"). For example, if a user moves a file into a directory that has already been backed up, then that file would be completely missing on the [backup media](https://en.wikipedia.org/wiki/Computer_data_storage "Computer data storage"), since the backup operation had already taken place before the addition of the file. Version skew may also cause corruption with files which change their size or contents underfoot while being read.

One [approach](https://en.wikipedia.org/wiki/Backup#Approaches_to_backing_up_live_data "Backup") to safely backing up live data is to temporarily disable write access to data during the backup, either by stopping the accessing applications or by using the [locking](https://en.wikipedia.org/wiki/Lock_\(computer_science\) "Lock (computer science)") [API](https://en.wikipedia.org/wiki/Application_programming_interface "Application programming interface") provided by the operating system to enforce exclusive read access. This is tolerable for low-availability systems (on desktop computers and small workgroup servers, on which regular [downtime](https://en.wikipedia.org/wiki/Downtime "Downtime") is acceptable). High-availability [24/7](https://en.wikipedia.org/wiki/24/7 "24/7") systems, however, cannot bear service stoppages.

To avoid downtime, high-availability systems may instead perform the backup on a _snapshot_—a [read-only](https://en.wikipedia.org/wiki/File_system_permissions "File system permissions") copy of the data set frozen at a [point in time](https://en.wikipedia.org/wiki/Point_in_time "Point in time")—and allow applications to continue writing to their data. Most snapshot implementations are efficient and can create snapshots in _[O(1)](https://en.wikipedia.org/wiki/Big_O_notation "Big O notation")_. In other words, the time and I/O needed to create the snapshot does not increase with the size of the data set; by contrast, the time and I/O required for a direct backup is proportional to the size of the data set. In some systems once the initial snapshot is taken of a data set, subsequent snapshots copy the changed data only, and use a system of pointers to reference the initial snapshot. This method of pointer-based snapshots consumes less disk capacity than if the data set was repeatedly cloned.

### Implementations
#### Volume managers
Some [Unix](https://en.wikipedia.org/wiki/Unix "Unix") systems have snapshot-capable [logical volume managers](https://en.wikipedia.org/wiki/Logical_volume_management "Logical volume management"). These implement [copy-on-write](https://en.wikipedia.org/wiki/Copy-on-write "Copy-on-write") on entire [block devices](https://en.wikipedia.org/wiki/Block_device "Block device") by copying changed blocks‍—‌just before they are to be overwritten within "parent" volumes‍—‌to other storage, thus preserving a self-consistent past image of the block device. Filesystems on such snapshot images can later be mounted as if they were on a read-only media.

Some volume managers also allow creation of _writable_ snapshots, extending the copy-on-write approach by disassociating any blocks modified within the snapshot from their "parent" blocks in the original volume. Such a scheme could be also described as performing additional copy-on-write operations triggered by the writes to snapshots.

On Linux, [Logical Volume Manager](https://en.wikipedia.org/wiki/Logical_Volume_Manager_\(Linux\) "Logical Volume Manager (Linux)") (LVM) allows creation of both read-only and read-write snapshots. Writable snapshots were introduced with the LVM version 2 (LVM2).

#### File systems
Some file systems, such as [WAFL](https://en.wikipedia.org/wiki/Write_Anywhere_File_Layout "Write Anywhere File Layout"), [fossil](https://en.wikipedia.org/wiki/Fossil_\(file_system\) "Fossil (file system)") for [Plan 9 from Bell Labs](https://en.wikipedia.org/wiki/Plan_9_from_Bell_Labs "Plan 9 from Bell Labs"), and [ODS-5](https://en.wikipedia.org/wiki/ODS-5 "ODS-5"), internally track old versions of files and make snapshots available through a special [namespace](https://en.wikipedia.org/wiki/Namespace "Namespace"). Others, like [UFS2](https://en.wikipedia.org/wiki/Unix_File_System "Unix File System"), provide an operating system [API](https://en.wikipedia.org/wiki/API "API") for accessing file histories. In [NTFS](https://en.wikipedia.org/wiki/NTFS "NTFS"), access to snapshots is provided by the Volume Shadow-copying Service (VSS) in [Windows XP](https://en.wikipedia.org/wiki/Windows_XP "Windows XP") and [Windows Server 2003](https://en.wikipedia.org/wiki/Windows_Server_2003 "Windows Server 2003") and [Shadow Copy](https://en.wikipedia.org/wiki/Shadow_Copy "Shadow Copy") in [Windows Vista](https://en.wikipedia.org/wiki/Windows_Vista "Windows Vista"). [Melio FS](https://en.wikipedia.org/w/index.php?title=Melio_FS&action=edit&redlink=1 "Melio FS (page does not exist)") provides snapshots via the same VSS interface for shared storage. Snapshots have also been available in the NSS ([Novell Storage Services](https://en.wikipedia.org/wiki/Novell_Storage_Services "Novell Storage Services")) file system on [NetWare](https://en.wikipedia.org/wiki/NetWare "NetWare") since version 4.11, and more recently on [Linux](https://en.wikipedia.org/wiki/Linux "Linux") platforms in the [Open Enterprise Server](https://en.wikipedia.org/wiki/Open_Enterprise_Server "Open Enterprise Server") product.

EMC's Isilon OneFS clustered storage platform implements a single scalable file system that supports read-only snapshots at the file or directory level. Any file or directory within the file system can be snapshotted and the system will implement a copy-on-write or point-in-time snapshot dynamically based on which method is determined to be optimal for the system.

On Linux, the [Btrfs](https://en.wikipedia.org/wiki/Btrfs "Btrfs") and [OCFS2](https://en.wikipedia.org/wiki/OCFS2 "OCFS2") file systems support creating snapshots (cloning) of individual files. Additionally, Btrfs also supports the creation of snapshots of subvolumes. On AIX, [JFS2](https://en.wikipedia.org/wiki/JFS2 "JFS2") also support snapshots.

## Transmission Control Protocol (TCP)
The **Transmission Control Protocol** (**TCP**) is one of the main [protocols](https://en.wikipedia.org/wiki/Communications_protocol "Communications protocol") of the [Internet protocol suite](https://en.wikipedia.org/wiki/Internet_protocol_suite "Internet protocol suite"). It originated in the initial network implementation in which it complemented the [Internet Protocol](https://en.wikipedia.org/wiki/Internet_Protocol "Internet Protocol") (IP). Therefore, the entire suite is commonly referred to as [TCP/IP](https://en.wikipedia.org/wiki/TCP/IP "TCP/IP"). TCP provides [reliable](https://en.wikipedia.org/wiki/Reliability_\(computer_networking\) "Reliability (computer networking)"), ordered, and [error-checked](https://en.wikipedia.org/wiki/Error_detection_and_correction "Error detection and correction") delivery of a [stream](https://en.wikipedia.org/wiki/Reliable_byte_stream "Reliable byte stream") of [octets](https://en.wikipedia.org/wiki/Octet_\(computing\) "Octet (computing)") (bytes) between applications running on hosts communicating via an IP network. Major internet applications such as the [World Wide Web](https://en.wikipedia.org/wiki/World_Wide_Web "World Wide Web"), email, [remote administration](https://en.wikipedia.org/wiki/Remote_administration "Remote administration"), and [file transfer](https://en.wikipedia.org/wiki/File_transfer "File transfer") rely on TCP, which is part of the [transport layer](https://en.wikipedia.org/wiki/Transport_layer "Transport layer") of the TCP/IP suite. [SSL/TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security") often runs on top of TCP.

TCP is [connection-oriented](https://en.wikipedia.org/wiki/Connection-oriented_communication "Connection-oriented communication"), meaning that sender and receiver firstly need to establish a connection based on agreed parameters; they do this through three-way handshake procedure. The server must be listening (passive open) for connection requests from clients before a connection is established. Three-way [handshake](https://en.wikipedia.org/wiki/Handshake_\(computing\) "Handshake (computing)") (active open), [retransmission](https://en.wikipedia.org/wiki/Retransmission_\(data_networks\) "Retransmission (data networks)"), and error detection adds to reliability but lengthens [latency](https://en.wikipedia.org/wiki/Network_latency "Network latency"). Applications that do not require reliable [data stream](https://en.wikipedia.org/wiki/Data_stream "Data stream") service may use the [User Datagram Protocol](https://en.wikipedia.org/wiki/User_Datagram_Protocol "User Datagram Protocol") (UDP) instead, which provides a [connectionless](https://en.wikipedia.org/wiki/Connectionless_communication "Connectionless communication") [datagram](https://en.wikipedia.org/wiki/Datagram "Datagram") service that prioritizes time over reliability. TCP employs [network congestion avoidance](https://en.wikipedia.org/wiki/TCP_congestion_control "TCP congestion control"). However, there are vulnerabilities in TCP, including [denial of service](https://en.wikipedia.org/wiki/Denial-of-service_attack "Denial-of-service attack"), [connection hijacking](https://en.wikipedia.org/wiki/TCP_sequence_prediction_attack "TCP sequence prediction attack"), TCP veto, and [reset attack](https://en.wikipedia.org/wiki/TCP_reset_attack "TCP reset attack").

### Network function
The Transmission Control Protocol provides a communication service at an intermediate level between an application program and the Internet Protocol. It provides host-to-host connectivity at the [transport layer](https://en.wikipedia.org/wiki/Transport_layer "Transport layer") of the [Internet model](https://en.wikipedia.org/wiki/Internet_model "Internet model"). An application does not need to know the particular mechanisms for sending data via a link to another host, such as the required [IP fragmentation](https://en.wikipedia.org/wiki/IP_fragmentation "IP fragmentation") to accommodate the [maximum transmission unit](https://en.wikipedia.org/wiki/Maximum_transmission_unit "Maximum transmission unit") of the transmission medium. At the transport layer, TCP handles all handshaking and transmission details and presents an abstraction of the network connection to the application typically through a [network socket](https://en.wikipedia.org/wiki/Network_socket "Network socket") interface.

At the lower levels of the protocol stack, due to [network congestion](https://en.wikipedia.org/wiki/Network_congestion "Network congestion"), traffic [load balancing](https://en.wikipedia.org/wiki/Load_balancing_\(computing\) "Load balancing (computing)"), or unpredictable network behavior, IP packets may be [lost](https://en.wikipedia.org/wiki/Packet_loss "Packet loss"), duplicated, or [delivered out of order](https://en.wikipedia.org/wiki/Out-of-order_delivery "Out-of-order delivery"). TCP detects these problems, requests [re-transmission](https://en.wikipedia.org/wiki/Retransmission_\(data_networks\) "Retransmission (data networks)") of lost data, rearranges out-of-order data and even helps minimize network congestion to reduce the occurrence of the other problems. If the data still remains undelivered, the source is notified of this failure. Once the TCP receiver has reassembled the sequence of octets originally transmitted, it passes them to the receiving application. Thus, TCP [abstracts](https://en.wikipedia.org/wiki/Abstraction_\(computer_science\) "Abstraction (computer science)") the application's communication from the underlying networking details.

TCP is used extensively by many internet applications, including the [World Wide Web](https://en.wikipedia.org/wiki/World_Wide_Web "World Wide Web") (WWW), email, [File Transfer Protocol](https://en.wikipedia.org/wiki/File_Transfer_Protocol "File Transfer Protocol"), [Secure Shell](https://en.wikipedia.org/wiki/Secure_Shell "Secure Shell"), [peer-to-peer file sharing](https://en.wikipedia.org/wiki/Peer-to-peer_file_sharing "Peer-to-peer file sharing"), and [streaming media](https://en.wikipedia.org/wiki/Streaming_media "Streaming media").

TCP is optimized for accurate delivery rather than timely delivery and can incur relatively long delays (on the order of seconds) while waiting for out-of-order messages or re-transmissions of lost messages. Therefore, it is not particularly suitable for real-time applications such as [voice over IP](https://en.wikipedia.org/wiki/Voice_over_IP "Voice over IP"). For such applications, protocols like the [Real-time Transport Protocol](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol "Real-time Transport Protocol") (RTP) operating over the [User Datagram Protocol](https://en.wikipedia.org/wiki/User_Datagram_Protocol "User Datagram Protocol") (UDP) are usually recommended instead.

TCP is a [reliable byte stream](https://en.wikipedia.org/wiki/Reliable_byte_stream "Reliable byte stream") delivery service that guarantees that all bytes received will be identical and in the same order as those sent. Since packet transfer by many networks is not reliable, TCP achieves this using a technique known as _positive acknowledgment with re-transmission_. This requires the receiver to respond with an [acknowledgment](https://en.wikipedia.org/wiki/Acknowledgement_\(data_networks\) "Acknowledgement (data networks)") message as it receives the data. The sender keeps a record of each packet it sends and maintains a timer from when the packet was sent. The sender re-transmits a packet if the timer expires before receiving the acknowledgment. The timer is needed in case a packet gets lost or corrupted.

While IP handles actual delivery of the data, TCP keeps track of _segments_ – the individual units of data transmission that a message is divided into for efficient routing through the network. For example, when an HTML file is sent from a web server, the TCP software layer of that server divides the file into segments and forwards them individually to the [internet layer](https://en.wikipedia.org/wiki/Internet_layer "Internet layer") in the [network stack](https://en.wikipedia.org/wiki/Network_stack "Network stack"). The internet layer software encapsulates each TCP segment into an IP packet by adding a header that includes (among other data) the destination [IP address](https://en.wikipedia.org/wiki/IP_address "IP address"). When the client program on the destination computer receives them, the TCP software in the transport layer re-assembles the segments and ensures they are correctly ordered and error-free as it streams the file contents to the receiving application.

### TCP segment structure
Transmission Control Protocol accepts data from a data stream, divides it into chunks, and adds a TCP header creating a TCP segment. The TCP segment is then [encapsulated](https://en.wikipedia.org/wiki/Encapsulation_\(networking\) "Encapsulation (networking)") into an Internet Protocol (IP) datagram, and exchanged with peers.

The term _TCP packet_ appears in both informal and formal usage, whereas in more precise terminology _segment_ refers to the TCP [protocol data unit](https://en.wikipedia.org/wiki/Protocol_data_unit "Protocol data unit") (PDU), _datagram to the IP PDU, and _frame_ to the [data link layer](https://en.wikipedia.org/wiki/Data_link_layer "Data link layer") PDU:

> Processes transmit data by calling on the TCP and passing buffers of data as arguments. The TCP packages the data from these buffers into segments and calls on the internet module [e.g. IP] to transmit each segment to the destination TCP.

A TCP segment consists of a segment _header_ and a _data_ section. The segment header contains 10 mandatory fields, and an optional extension field (_Options_, pink background in table). The data section follows the header and is the payload data carried for the application. The length of the data section is not specified in the segment header; it can be calculated by subtracting the combined length of the segment header and IP header from the total IP datagram length specified in the IP header.

Source Port: 16 bits

Identifies the sending port.

Destination Port: 16 bits

Identifies the receiving port.

Sequence Number: 32 bits

Has a dual role:

- If the SYN flag is set (1), then this is the initial sequence number. The sequence number of the actual first data byte and the acknowledged number in the corresponding ACK are then this sequence number plus 1.
- If the SYN flag is unset (0), then this is the accumulated sequence number of the first data byte of this segment for the current session.

Acknowledgment Number: 32 bits

If the ACK flag is set then the value of this field is the next sequence number that the sender of the ACK is expecting. This acknowledges receipt of all prior bytes (if any). The first ACK sent by each end acknowledges the other end's initial sequence number itself, but no data.

Data Offset (DOffset): 4 bits

Specifies the size of the TCP header in 32-bit [words](https://en.wikipedia.org/wiki/Word_\(computer_architecture\) "Word (computer architecture)"). The minimum size header is 5 words and the maximum is 15 words thus giving the minimum size of 20 bytes and maximum of 60 bytes, allowing for up to 40 bytes of options in the header. This field gets its name from the fact that it is also the offset from the start of the TCP segment to the actual data._]

Reserved (Rsrvd): 4 bits

For future use and should be set to zero; senders should not set these and receivers should ignore them if set, in the absence of further specification and implementation.

From 2003 to 2017, the last bit (bit 103 of the header) was defined as the NS (Nonce Sum) flag by the experimental [RFC 3540](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#CITEREFRFC_3540), ECN-nonce. ECN-nonce never gained widespread use and the RFC was moved to Historic status.

Flags: 8 bits

Contains 8 1-bit flags (control bits) as follows:

CWR: 1 bit

Congestion window reduced (CWR) flag is set by the sending host to indicate that it received a TCP segment with the ECE flag set and had responded in congestion control mechanism.
ECE: 1 bit

ECN-Echo has a dual role, depending on the value of the SYN flag. It indicates:

- If the SYN flag is set (1), the TCP peer is [ECN](https://en.wikipedia.org/wiki/Explicit_Congestion_Notification "Explicit Congestion Notification") capable.
- If the SYN flag is unset (0), a packet with the Congestion Experienced flag set (ECN=11) in its IP header was received during normal transmission. This serves as an indication of network congestion (or impending congestion) to the TCP sender.

URG: 1 bit

Indicates that the Urgent pointer field is significant.

ACK: 1 bit

Indicates that the Acknowledgment field is significant. All packets after the initial SYN packet sent by the client should have this flag set.
PSH: 1 bit

Push function. Asks to push the buffered data to the receiving application.

RST: 1 bit

Reset the connection

SYN: 1 bit

Synchronize sequence numbers. Only the first packet sent from each end should have this flag set. Some other flags and fields change meaning based on this flag, and some are only valid when it is set, and others when it is clear.

FIN: 1 bit

Last packet from sender

Window: 16 bits

The size of the _receive window_, which specifies the number of window size units that the sender of this segment is currently willing to receive.) (See [§ Flow control](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#Flow_control) and [§ Window scaling](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#Window_scaling).)

[Checksum](https://en.wikipedia.org/wiki/Internet_checksum "Internet checksum"): 16 bits

The 16-bit [checksum](https://en.wikipedia.org/wiki/Checksum "Checksum") field is used for error-checking of the TCP header, the payload and an IP pseudo-header. The pseudo-header consists of the [source IP address](https://en.wikipedia.org/wiki/IPv4#Source_address "IPv4"), the [destination IP address](https://en.wikipedia.org/wiki/IPv4#Destination_address "IPv4"), the [protocol number](https://en.wikipedia.org/wiki/List_of_IP_protocol_numbers "List of IP protocol numbers") for the TCP protocol (6) and the length of the TCP headers and payload (in bytes).

Urgent Pointer: 16 bits

If the URG flag is set, then this 16-bit field is an offset from the sequence number indicating the last urgent data byte.

Options (TCP Option): Variable 0–320 bits, in units of 32 bits; `size(Options) == (DOffset - 5) * 32`

The length of this field is determined by the _[Data Offset](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#Data_Offset)_ field. The TCP header padding is used to ensure that the TCP header ends, and data begins, on a 32-bit boundary. The padding is composed of zeros.

Options have up to three fields: Option-Kind (1 byte), Option-Length (1 byte), Option-Data (variable). The Option-Kind field indicates the type of option and is the only field that is not optional. Depending on Option-Kind value, the next two fields may be set. Option-Length indicates the total length of the option, and Option-Data contains data associated with the option, if applicable. For example, an Option-Kind byte of 1 indicates that this is a no operation option used only for padding, and does not have an Option-Length or Option-Data fields following it. An Option-Kind byte of 0 marks the end of options, and is also only one byte. An Option-Kind byte of 2 is used to indicate Maximum Segment Size option, and will be followed by an Option-Length byte specifying the length of the MSS field. Option-Length is the total length of the given options field, including Option-Kind and Option-Length fields. So while the MSS value is typically expressed in two bytes, Option-Length will be 4. As an example, an MSS option field with a value of 0x05B4 is coded as (0x02 0x04 0x05B4) in the TCP options section.

Some options may only be sent when SYN is set; they are indicated below as `[SYN]`. Option-Kind and standard lengths given as (Option-Kind, Option-Length).

| Option-Kind | Option-Length         | Option-Data     | Purpose                                                                                                                      | Notes                                                                                                                                                                                                                                                                                                                                                                                   |
| ----------- | --------------------- | --------------- | ---------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0           | —                     | —               | End of options list                                                                                                          |                                                                                                                                                                                                                                                                                                                                                                                         |
| 1           | —                     | —               | No operation                                                                                                                 | This may be used to align option fields on 32-bit boundaries for better performance.                                                                                                                                                                                                                                                                                                    |
| 2           | 4                     | SS              | Maximum segment size                                                                                                         | See [§ Maximum segment size](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#Maximum_segment_size) for details. `[SYN]`                                                                                                                                                                                                                                                     |
| 3           | 3                     | S               | Window scale                                                                                                                 | See [§ Window scaling](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#Window_scaling) for details.[[26]](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#cite_note-FOOTNOTERFC_7323-29) `[SYN]`                                                                                                                                                                |
| 4           | 2                     | —               | Selective Acknowledgement permitted                                                                                          | See [§ Selective acknowledgments](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#Selective_acknowledgments) for details.[[27]](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#cite_note-FOOTNOTERFC_20182._Sack-Permitted_Option-30) `[SYN]`                                                                                                                  |
| 5           | N (10, 18, 26, or 34) | BBBB, EEEE, ... | (SACK)[[28]](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#cite_note-FOOTNOTERFC_20183._Sack_Option_Format-31) | These first two bytes are followed by a list of 1–4 blocks being selectively acknowledged, specified as 32-bit begin/end pointers.                                                                                                                                                                                                                                                      |
| 8           | 10                    | TTTT, EEEE      | Timestamp and echo of previous timestamp                                                                                     | See [§ TCP timestamps](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#TCP_timestamps) for details.[[26]](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#cite_note-FOOTNOTERFC_7323-29)                                                                                                                                                                        |
| 28          | 4                     | —               | User Timeout Option                                                                                                          | See RFC [5482](https://www.rfc-editor.org/rfc/rfc5482).                                                                                                                                                                                                                                                                                                                                 |
| 29          | N                     | —               | TCP Authentication Option (TCP-AO)                                                                                           | For message authentication, replacing [MD5](https://en.wikipedia.org/wiki/MD5 "MD5") authentication (option 19) originally designed to protect [BGP](https://en.wikipedia.org/wiki/Border_Gateway_Protocol "Border Gateway Protocol") sessions.[[29]](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#cite_note-32) See RFC [5925](https://www.rfc-editor.org/rfc/rfc5925). |
| 30          | N                     | —               | Multipath TCP (MPTCP)                                                                                                        | See [Multipath TCP](https://en.wikipedia.org/wiki/Multipath_TCP "Multipath TCP") for details.                                                                                                                                                                                                                                                                                           |

The remaining Option-Kind values are historical, obsolete, experimental, not yet standardized, or unassigned. Option number assignments are maintained by the [Internet Assigned Numbers Authority](https://en.wikipedia.org/wiki/Internet_Assigned_Numbers_Authority "Internet Assigned Numbers Authority") (IANA).

Data: Variable

The payload of the TCP packet

### Protocol operation
[![](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f6/Tcp_state_diagram_fixed_new.svg/250px-Tcp_state_diagram_fixed_new.svg.png)](https://en.wikipedia.org/wiki/File:Tcp_state_diagram_fixed_new.svg)

A Simplified TCP State Diagram.

TCP protocol operations may be divided into three phases. _Connection establishment_ is a multi-step handshake process that establishes a connection before entering the _data transfer_ phase. After data transfer is completed, the _connection termination_ closes the connection and releases all allocated resources.

A TCP connection is managed by an operating system through a resource that represents the local end-point for communications, the _[Internet socket](https://en.wikipedia.org/wiki/Internet_socket "Internet socket")_. During the lifetime of a TCP connection, the local end-point undergoes a series of [state](https://en.wikipedia.org/wiki/State_\(computer_science\) "State (computer science)") changes:

#### Connection establishment
Before a client attempts to connect with a server, the server must first bind to and listen at a port to open it up for connections: this is called a passive open. Once the passive open is established, a client may establish a connection by initiating an active open using the three-way (or 3-step) handshake:

1. **SYN**: The active open is performed by the client sending a SYN to the server. The client sets the segment's sequence number to a random value A.
2. **SYN-ACK**: In response, the server replies with a SYN-ACK. The acknowledgment number is set to one more than the received sequence number i.e. A+1, and the sequence number that the server chooses for the packet is another random number, B.
3. **ACK**: Finally, the client sends an ACK back to the server. The sequence number is set to the received acknowledgment value i.e. A+1, and the acknowledgment number is set to one more than the received sequence number i.e. B+1.

Steps 1 and 2 establish and acknowledge the sequence number for one direction (client to server). Steps 2 and 3 establish and acknowledge the sequence number for the other direction (server to client). Following the completion of these steps, both the client and server have received acknowledgments and a full-duplex communication is established.

#### Connection termination
[![](https://upload.wikimedia.org/wikipedia/commons/thumb/5/55/TCP_CLOSE.svg/330px-TCP_CLOSE.svg.png)](https://en.wikipedia.org/wiki/File:TCP_CLOSE.svg)

Connection termination

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/d/de/TCP_close%28%29_-_sequence_diagram.svg/250px-TCP_close%28%29_-_sequence_diagram.svg.png)](https://en.wikipedia.org/wiki/File:TCP_close\(\)_-_sequence_diagram.svg)

Detailed TCP close() sequence diagram

The connection termination phase uses a four-way handshake, with each side of the connection terminating independently. When an endpoint wishes to stop its half of the connection, it transmits a FIN packet, which the other end acknowledges with an ACK. Therefore, a typical tear-down requires a pair of FIN and ACK segments from each TCP endpoint. After the side that sent the first FIN has responded with the final ACK, it waits for a timeout before finally closing the connection, during which time the local port is unavailable for new connections; this state lets the TCP client resend the final acknowledgment to the server in case the ACK is lost in transit. The time duration is implementation-dependent, but some common values are 30 seconds, 1 minute, and 2 minutes. After the timeout, the client enters the CLOSED state and the local port becomes available for new connections.

It is also possible to terminate the connection by a 3-way handshake, when host A sends a FIN and host B replies with a FIN & ACK (combining two steps into one) and host A replies with an ACK.

Some operating systems, such as [Linux](https://en.wikipedia.org/wiki/Linux "Linux")implement a half-duplex close sequence. If the host actively closes a connection, while still having unread incoming data available, the host sends the signal RST (losing any received data) instead of FIN. This assures that a TCP application is aware there was a data loss.

A connection can be in a [half-open](https://en.wikipedia.org/wiki/TCP_half-open "TCP half-open") state, in which case one side has terminated the connection, but the other has not. The side that has terminated can no longer send any data into the connection, but the other side can. The terminating side should continue reading the data until the other side terminates as well.

#### Resource usage
Most implementations allocate an entry in a table that maps a session to a running operating system process. Because TCP packets do not include a session identifier, both endpoints identify the session using the client's address and port. Whenever a packet is received, the TCP implementation must perform a lookup on this table to find the destination process. Each entry in the table is known as a Transmission Control Block or TCB. It contains information about the endpoints (IP and port), status of the connection, running data about the packets that are being exchanged and buffers for sending and receiving data.

The number of sessions in the server side is limited only by memory and can grow as new connections arrive, but the client must allocate an [ephemeral port](https://en.wikipedia.org/wiki/Ephemeral_port "Ephemeral port") before sending the first SYN to the server. This port remains allocated during the whole conversation and effectively limits the number of outgoing connections from each of the client's IP addresses. If an application fails to properly close unrequired connections, a client can run out of resources and become unable to establish new TCP connections, even from other applications.

Both endpoints must also allocate space for unacknowledged packets and received (but unread) data.

#### Data transfer
The Transmission Control Protocol differs in several key features compared to the [User Datagram Protocol](https://en.wikipedia.org/wiki/User_Datagram_Protocol "User Datagram Protocol"):

- Ordered data transfer: the destination host rearranges segments according to a sequence number
- Retransmission of lost packets: any cumulative stream not acknowledged is retransmitted
- Error-free data transfer: corrupted packets are treated as lost and are retransmitted
- Flow control: limits the rate a sender transfers data to guarantee reliable delivery. The receiver continually hints the sender on how much data can be received. When the receiving host's buffer fills, the next acknowledgment suspends the transfer and allows the data in the buffer to be processed.
- Congestion control: lost packets (presumed due to congestion) trigger a reduction in data delivery rate

##### Reliable transmission
TCP uses a _sequence number_ to identify each byte of data. The sequence number identifies the order of the bytes sent from each computer so that the data can be reconstructed in order, regardless of any [out-of-order delivery](https://en.wikipedia.org/wiki/Out-of-order_delivery "Out-of-order delivery") that may occur. The sequence number of the first byte is chosen by the transmitter for the first packet, which is flagged SYN. This number can be arbitrary, and should, in fact, be unpredictable to defend against [TCP sequence prediction attacks](https://en.wikipedia.org/wiki/TCP_sequence_prediction_attack "TCP sequence prediction attack").

Acknowledgments (ACKs) are sent with a sequence number by the receiver of data to tell the sender that data has been received to the specified byte. ACKs do not imply that the data has been delivered to the application, they merely signify that it is now the receiver's responsibility to deliver the data.

Reliability is achieved by the sender detecting lost data and retransmitting it. TCP uses two primary techniques to identify loss. Retransmission timeout (RTO) and duplicate cumulative acknowledgments (DupAcks).

When a TCP segment is retransmitted, it retains the same sequence number as the original delivery attempt. This conflation of delivery and logical data ordering means that, when acknowledgment is received after a retransmission, the sender cannot tell whether the original transmission or the retransmission is being acknowledged, the so-called _retransmission ambiguity_.1) TCP incurs complexity due to retransmission ambiguity.

###### Duplicate-ACK-based retransmission
If a single segment (say segment number 100) in a stream is lost, then the receiver cannot acknowledge packets above that segment number (100) because it uses cumulative ACKs. Hence the receiver acknowledges packet 99 again on the receipt of another data packet. This duplicate acknowledgement is used as a signal for packet loss. That is, if the sender receives three duplicate acknowledgments, it retransmits the last unacknowledged packet. A threshold of three is used because the network may reorder segments causing duplicate acknowledgements. This threshold has been demonstrated to avoid spurious retransmissions due to reordering. Some TCP implementations use [selective acknowledgements](https://en.wikipedia.org/wiki/Selective_acknowledgement "Selective acknowledgement") (SACKs) to provide explicit feedback about the segments that have been received. This greatly improves TCP's ability to retransmit the right segments.

Retransmission ambiguity can cause spurious fast retransmissions and congestion avoidance if there is reordering beyond the duplicate acknowledgment threshold. In the last two decades more packet reordering has been observed over the Internet which led TCP implementations, such as the one in the Linux Kernel to adopt heuristic methods to scale the duplicate acknowledgment threshold. Recently, there have been efforts to completely phase out duplicate-ACK-based fast-retransmissions and replace them with timer based ones. (Not to be confused with the classic RTO discussed below). The time based loss detection algorithm called Recent Acknowledgment (RACK) has been adopted as the default algorithm in Linux and Windows.

###### Timeout-based retransmission
When a sender transmits a segment, it initializes a timer with a conservative estimate of the arrival time of the acknowledgment. The segment is retransmitted if the timer expires, with a new timeout threshold of twice the previous value, resulting in [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff "Exponential backoff") behavior. Typically, the initial timer value is smoothed RTT + max(_G_, 4 × RTT variation), where G is the clock granularity. This guards against excessive transmission traffic due to faulty or malicious actors, such as [man-in-the-middle](https://en.wikipedia.org/wiki/Man-in-the-middle_attack "Man-in-the-middle attack") [denial of service attackers](https://en.wikipedia.org/wiki/Denial_of_service_attack "Denial of service attack").

Accurate RTT estimates are important for loss recovery, as it allows a sender to assume an unacknowledged packet to be lost after sufficient time elapses (i.e., determining the RTO time). Retransmission ambiguity can lead a sender's estimate of RTT to be imprecise. In an environment with variable RTTs, spurious timeouts can occur: if the RTT is under-estimated, then the RTO fires and triggers a needless retransmit and slow-start. After a spurious retransmission, when the acknowledgments for the original transmissions arrive, the sender may believe them to be acknowledging the retransmission and conclude, incorrectly, that segments sent between the original transmission and retransmission have been lost, causing further needless retransmissions to the extent that the link truly becomes congested; selective acknowledgement can reduce this effect.) [RFC 6298](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#CITEREFRFC_6298) specifies that implementations must not use retransmitted segments when estimating RTT. ensures that a good RTT estimate will be produced—eventually—by waiting until there is an unambiguous acknowledgment before adjusting the RTO. After spurious retransmissions, however, it may take significant time before such an unambiguous acknowledgment arrives, degrading performance in the interim. TCP timestamps also resolve the retransmission ambiguity problem in setting the RTO, though they do not necessarily improve the RTT estimate.

##### Error detection
Sequence numbers allow receivers to discard duplicate packets and properly sequence out-of-order packets. Acknowledgments allow senders to determine when to retransmit lost packets.

To assure correctness a checksum field is included; see [§ Checksum computation](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#Checksum_computation) for details. The TCP checksum is a weak check by modern standards and is normally paired with a [CRC](https://en.wikipedia.org/wiki/Cyclic_redundancy_check "Cyclic redundancy check") integrity check at [layer 2](https://en.wikipedia.org/wiki/Layer_2 "Layer 2"), below both TCP and IP, such as is used in [PPP](https://en.wikipedia.org/wiki/Point-to-Point_Protocol "Point-to-Point Protocol") or the [Ethernet](https://en.wikipedia.org/wiki/Ethernet "Ethernet") frame. However, introduction of errors in packets between CRC-protected hops is common and the 16-bit TCP checksum catches most of these.

##### Flow control
TCP uses an end-to-end [flow control](https://en.wikipedia.org/wiki/Flow_control_\(data\) "Flow control (data)") protocol to avoid having the sender send data too fast for the TCP receiver to receive and process it reliably. Having a mechanism for flow control is essential in an environment where machines of diverse network speeds communicate. For example, if a PC sends data to a smartphone that is slowly processing received data, the smartphone must be able to regulate the data flow so as not to be overwhelmed.

TCP uses a [sliding window](https://en.wikipedia.org/wiki/Sliding_window "Sliding window") flow control protocol. In each TCP segment, the receiver specifies in the _receive window_ field the amount of additionally received data (in bytes) that it is willing to buffer for the connection. The sending host can send only up to that amount of data before it must wait for an acknowledgment and receive window update from the receiving host.

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/d/db/Tcp.svg/250px-Tcp.svg.png)](https://en.wikipedia.org/wiki/File:Tcp.svg)

TCP sequence numbers and receive windows behave very much like a clock. The receive window shifts each time the receiver receives and acknowledges a new segment of data. Once it runs out of sequence numbers, the sequence number loops back to 0.

When a receiver advertises a window size of 0, the sender stops sending data and starts its _persist timer_. The persist timer is used to protect TCP from a [deadlock](https://en.wikipedia.org/wiki/Deadlock_\(computer_science\) "Deadlock (computer science)") situation that could arise if a subsequent window size update from the receiver is lost, and the sender cannot send more data until receiving a new window size update from the receiver. When the persist timer expires, the TCP sender attempts recovery by sending a small packet so that the receiver responds by sending another acknowledgment containing the new window size.

If a receiver is processing incoming data in small increments, it may repeatedly advertise a small receive window. This is referred to as the [silly window syndrome](https://en.wikipedia.org/wiki/Silly_window_syndrome "Silly window syndrome"), since it is inefficient to send only a few bytes of data in a TCP segment, given the relatively large overhead of the TCP header.

##### Congestion control
The final main aspect of TCP is [congestion control](https://en.wikipedia.org/wiki/Congestion_control "Congestion control"). TCP uses a number of mechanisms to achieve high performance and avoid [congestive collapse](https://en.wikipedia.org/wiki/Congestive_collapse "Congestive collapse"), a gridlock situation where network performance is severely degraded. These mechanisms control the rate of data entering the network, keeping the data flow below a rate that would trigger collapse. They also yield an approximately [max-min fair](https://en.wikipedia.org/wiki/Max-min_fair "Max-min fair") allocation between flows.

Acknowledgments for data sent, or the lack of acknowledgments, are used by senders to infer network conditions between the TCP sender and receiver. Coupled with timers, TCP senders and receivers can alter the behavior of the flow of data. This is more generally referred to as congestion control or congestion avoidance.

Modern implementations of TCP contain four intertwined algorithms: [slow start](https://en.wikipedia.org/wiki/TCP_congestion_control#Slow_start "TCP congestion control"), [congestion avoidance](https://en.wikipedia.org/wiki/TCP_congestion_avoidance_algorithm "TCP congestion avoidance algorithm"), [fast retransmit](https://en.wikipedia.org/wiki/Fast_retransmit "Fast retransmit"), and [fast recovery](https://en.wikipedia.org/wiki/Fast_recovery "Fast recovery").

In addition, senders employ a _retransmission timeout_ (RTO) that is based on the estimated [round-trip time](https://en.wikipedia.org/wiki/Round-trip_time "Round-trip time") (RTT) between the sender and receiver, as well as the variance in this round-trip time. There are subtleties in the estimation of RTT. For example, senders must be careful when calculating RTT samples for retransmitted packets; typically they use [Karn's Algorithm](https://en.wikipedia.org/wiki/Karn%27s_Algorithm "Karn's Algorithm") or TCP timestamps. These individual RTT samples are then averaged over time to create a smoothed round trip time (SRTT) using [Jacobson's algorithm](https://en.wikipedia.org/w/index.php?title=Jacobson%27s_algorithm&action=edit&redlink=1 "Jacobson's algorithm (page does not exist)"). This SRTT value is what is used as the round-trip time estimate.

Enhancing TCP to reliably handle loss, minimize errors, manage congestion and go fast in very high-speed environments are ongoing areas of research and standards development. As a result, there are a number of [TCP congestion avoidance algorithm](https://en.wikipedia.org/wiki/TCP_congestion_avoidance_algorithm "TCP congestion avoidance algorithm") variations.

#### Maximum segment size
The [maximum segment size](https://en.wikipedia.org/wiki/Maximum_segment_size "Maximum segment size") (MSS) is the largest amount of data, specified in bytes, that TCP is willing to receive in a single segment. For best performance, the MSS should be set small enough to avoid [IP fragmentation](https://en.wikipedia.org/wiki/IP_fragmentation "IP fragmentation"), which can lead to packet loss and excessive retransmissions. To accomplish this, typically the MSS is announced by each side using the MSS option when the TCP connection is established. The option value is derived from the [maximum transmission unit](https://en.wikipedia.org/wiki/MTU_\(networking\) "MTU (networking)") (MTU) size of the data link layer of the networks to which the sender and receiver are directly attached. TCP senders can use [path MTU discovery](https://en.wikipedia.org/wiki/Path_MTU_discovery "Path MTU discovery") to infer the minimum MTU along the network path between the sender and receiver, and use this to dynamically adjust the MSS to avoid IP fragmentation within the network.

MSS announcement may also be called _MSS negotiation_ but, strictly speaking, the MSS is not _negotiated_. Two completely independent values of MSS are permitted for the two directions of data flow in a TCP connection, so there is no need to agree on a common MSS configuration for a bidirectional connection.

#### Selective acknowledgments
Relying purely on the cumulative acknowledgment scheme employed by the original TCP can lead to inefficiencies when packets are lost. For example, suppose bytes with sequence number 1,000 to 10,999 are sent in 10 different TCP segments of equal size, and the second segment (sequence numbers 2,000 to 2,999) is lost during transmission. In a pure cumulative acknowledgment protocol, the receiver can only send a cumulative ACK value of 2,000 (the sequence number immediately following the last sequence number of the received data) and cannot say that it received bytes 3,000 to 10,999 successfully. Thus the sender may then have to resend all data starting with sequence number 2,000.

To alleviate this issue TCP employs the _selective acknowledgment (SACK)_ option, defined in 1996 in [RFC 2018](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#CITEREFRFC_2018), which allows the receiver to acknowledge discontinuous blocks of packets that were received correctly, in addition to the sequence number immediately following the last sequence number of the last contiguous byte received successively, as in the basic TCP acknowledgment. The acknowledgment can include a number of _SACK blocks_, where each SACK block is conveyed by the _Left Edge of Block_ (the first sequence number of the block) and the _Right Edge of Block_ (the sequence number immediately following the last sequence number of the block), with a _Block_ being a contiguous range that the receiver correctly received. In the example above, the receiver would send an ACK segment with a cumulative ACK value of 2,000 and a SACK option header with sequence numbers 3,000 and 11,000. The sender would accordingly retransmit only the second segment with sequence numbers 2,000 to 2,999.

A TCP sender may interpret an out-of-order segment delivery as a lost segment. If it does so, the TCP sender will retransmit the segment previous to the out-of-order packet and slow its data delivery rate for that connection. The duplicate-SACK option, an extension to the SACK option that was defined in May 2000 in [RFC 2883](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#CITEREFRFC_2883), solves this problem. Once the TCP receiver detects a second duplicate packet, it sends a D-ACK to indicate that no segments were lost, allowing the TCP sender to reinstate the higher transmission rate.

The SACK option is not mandatory and comes into operation only if both parties support it. This is negotiated when a connection is established. SACK uses a TCP header option (see [§ TCP segment structure](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#TCP_segment_structure) for details). The use of SACK has become widespread—all popular TCP stacks support it. Selective acknowledgment is also used in [Stream Control Transmission Protocol](https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol "Stream Control Transmission Protocol") (SCTP).

Selective acknowledgements can be 'reneged', where the receiver unilaterally discards the selectively acknowledged data. [RFC 2018](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#CITEREFRFC_2018) discouraged such behavior, but did not prohibit it to allow receivers the option of reneging if they, for example, ran out of buffer space. The possibility of reneging leads to implementation complexity for both senders and receivers, and also imposes memory costs on the sender.

#### Window scaling
For more efficient use of high-bandwidth networks, a larger TCP window size may be used. A 16-bit TCP window size field controls the flow of data and its value is limited to 65,535 bytes. Since the size field cannot be expanded beyond this limit, a scaling factor is used. The [TCP window scale option](https://en.wikipedia.org/wiki/TCP_window_scale_option "TCP window scale option"), as defined in [RFC 1323](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#CITEREFRFC_1323), is an option used to increase the maximum window size to 1 gigabyte. Scaling up to these larger window sizes is necessary for [TCP tuning](https://en.wikipedia.org/wiki/TCP_tuning "TCP tuning").

The window scale option is used only during the TCP 3-way handshake. The window scale value represents the number of bits to left-shift the 16-bit window size field when interpreting it. The window scale value can be set from 0 (no shift) to 14 for each direction independently. Both sides must send the option in their SYN segments to enable window scaling in either direction.

Some routers and packet firewalls rewrite the window scaling factor during a transmission. This causes sending and receiving sides to assume different TCP window sizes. The result is non-stable traffic that may be very slow. The problem is visible on some sites behind a defective router.

#### TCP timestamps
TCP timestamps, defined in [RFC 1323](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#CITEREFRFC_1323) in 1992, can help TCP determine in which order packets were sent. TCP timestamps are not normally aligned to the system clock and start at some random value. Many operating systems will increment the timestamp for every elapsed millisecond; however, the RFC only states that the ticks should be proportional.

There are two timestamp fields:

- a 4-byte sender timestamp value (my timestamp)
- a 4-byte echo reply timestamp value (the most recent timestamp received from you).

TCP timestamps are used in an algorithm known as _Protection Against Wrapped Sequence_ numbers, or _PAWS_. PAWS is used when the receive window crosses the sequence number wraparound boundary. In the case where a packet was potentially retransmitted, it answers the question: "Is this sequence number in the first 4 GB or the second?" And the timestamp is used to break the tie.

Also, the Eifel detection algorithm uses TCP timestamps to determine if retransmissions are occurring because packets are lost or simply out of order.
TCP timestamps are enabled by default in Linux, and disabled by default in Windows Server 2008, 2012 and 2016.

Recent Statistics show that the level of TCP timestamp adoption has stagnated, at ~40%, owing to Windows Server dropping support since Windows Server 2008.

#### Out-of-band data
It is possible to interrupt or abort the queued stream instead of waiting for the stream to finish. This is done by specifying the data as _urgent_. This marks the transmission as [out-of-band data](https://en.wikipedia.org/wiki/Out-of-band_data "Out-of-band data") (OOB) and tells the receiving program to process it immediately. When finished, TCP informs the application and resumes the stream queue. An example is when TCP is used for a remote login session where the user can send a keyboard sequence that interrupts or aborts the remotely running program without waiting for the program to finish its current transfer.

The _urgent_ pointer only alters the processing on the remote host and doesn't expedite any processing on the network itself. The capability is implemented differently or poorly on different systems or may not be supported. Where it is available, it is prudent to assume only single bytes of OOB data will be reliably handled. Since the feature is not frequently used, it is not well tested on some platforms and has been associated with [vulnerabilities](https://en.wikipedia.org/wiki/Vulnerability_\(computing\) "Vulnerability (computing)"), [WinNuke](https://en.wikipedia.org/wiki/WinNuke "WinNuke") for instance.

#### Forcing data delivery
Normally, TCP waits for 200 ms for a full packet of data to send ([Nagle's Algorithm](https://en.wikipedia.org/wiki/Nagle%27s_Algorithm "Nagle's Algorithm") tries to group small messages into a single packet). This wait creates small, but potentially serious delays if repeated constantly during a file transfer. For example, a typical send block would be 4 KB, a typical MSS is 1460, so 2 packets go out on a 10 Mbit/s Ethernet taking ~1.2 ms each followed by a third carrying the remaining 1176 after a 197 ms pause because TCP is waiting for a full buffer. In the case of telnet, each user keystroke is echoed back by the server before the user can see it on the screen. This delay would become very annoying.

Setting the [socket](https://en.wikipedia.org/wiki/Network_socket "Network socket") option `TCP_NODELAY` overrides the default 200 ms send delay. Application programs use this socket option to force output to be sent after writing a character or line of characters.

The [RFC 793](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#CITEREFRFC_793) defines the `PSH` push bit as "a message to the receiving TCP stack to send this data immediately up to the receiving application". There is no way to indicate or control it in [user space](https://en.wikipedia.org/wiki/User_space "User space") using [Berkeley sockets](https://en.wikipedia.org/wiki/Berkeley_sockets "Berkeley sockets"); it is controlled by the [protocol stack](https://en.wikipedia.org/wiki/Protocol_stack "Protocol stack") only.

### Vulnerabilities
TCP may be attacked in a variety of ways. The results of a thorough security assessment of TCP, along with possible mitigations for the identified issues, were published in 2009, and was pursued within the [IETF](https://en.wikipedia.org/wiki/IETF "IETF") through 2012. Notable vulnerabilities include denial of service, connection hijacking, TCP veto and [TCP reset attack](https://en.wikipedia.org/wiki/TCP_reset_attack "TCP reset attack").

#### Denial of service
By using a [spoofed IP address](https://en.wikipedia.org/wiki/IP_address_spoofing "IP address spoofing") and repeatedly sending [purposely assembled](https://en.wikipedia.org/wiki/Mangled_packet "Mangled packet") SYN packets, followed by many ACK packets, attackers can cause the server to consume large amounts of resources keeping track of the bogus connections. This is known as a [SYN flood](https://en.wikipedia.org/wiki/SYN_flood "SYN flood") attack. Proposed solutions to this problem include [SYN cookies](https://en.wikipedia.org/wiki/SYN_cookies "SYN cookies") and cryptographic puzzles, though SYN cookies come with their own set of vulnerabilities. [Sockstress](https://en.wikipedia.org/wiki/Sockstress "Sockstress") is a similar attack, that might be mitigated with system resource management. An advanced DoS attack involving the exploitation of the TCP _persist timer_ was analyzed in [Phrack](https://en.wikipedia.org/wiki/Phrack "Phrack") No. 66. [PUSH and ACK floods](https://en.wikipedia.org/wiki/PUSH_and_ACK_floods "PUSH and ACK floods") are other variants.

#### Connection hijacking
An attacker who is able to eavesdrop on a TCP session and redirect packets can hijack a TCP connection. To do so, the attacker learns the sequence number from the ongoing communication and forges a false segment that looks like the next segment in the stream. A simple hijack can result in one packet being erroneously accepted at one end. When the receiving host acknowledges the false segment, synchronization is lost. Hijacking may be combined with [ARP spoofing](https://en.wikipedia.org/wiki/ARP_spoofing "ARP spoofing") or other routing attacks that allow an attacker to take permanent control of the TCP connection.

Impersonating a different IP address was not difficult prior to [RFC 1948](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#CITEREFRFC_1948) when the initial _sequence number_ was easily guessable. The earlier implementations allowed an attacker to blindly send a sequence of packets that the receiver would believe came from a different IP address, without the need to intercept communication through ARP or routing attacks: it is enough to ensure that the legitimate host of the impersonated IP address is down, or bring it to that condition using [denial-of-service attacks](https://en.wikipedia.org/wiki/Denial-of-service_attack "Denial-of-service attack"). This is why the initial sequence number is now chosen at random.

#### TCP veto
An attacker who can eavesdrop and predict the size of the next packet to be sent can cause the receiver to accept a malicious payload without disrupting the existing connection. The attacker injects a malicious packet with the sequence number and a payload size of the next expected packet. When the legitimate packet is ultimately received, it is found to have the same sequence number and length as a packet already received and is silently dropped as a normal duplicate packet—the legitimate packet is _vetoed_ by the malicious packet. Unlike in connection hijacking, the connection is never desynchronized and communication continues as normal after the malicious payload is accepted. TCP veto gives the attacker less control over the communication but makes the attack particularly resistant to detection. The only evidence to the receiver that something is amiss is a single duplicate packet, a normal occurrence in an IP network. The sender of the vetoed packet never sees any evidence of an attack.[[
### TCP ports
A TCP connection is identified by a four-[tuple](https://en.wikipedia.org/wiki/Tuple "Tuple") of the source address, source [port](https://en.wikipedia.org/wiki/Port_\(computer_networking\) "Port (computer networking)"), destination address, and destination port. Port numbers are used to identify different services, and to allow multiple connections between hosts. TCP uses [16-bit](https://en.wikipedia.org/wiki/16-bit "16-bit") port numbers, providing 65,536 possible values for each of the source and destination ports. The dependency of connection identity on addresses means that TCP connections are bound to a single network path; TCP cannot use other routes that [multihomed hosts](https://en.wikipedia.org/wiki/Multihomed_host "Multihomed host") have available, and connections break if an endpoint's address changes.

Port numbers are categorized into three basic categories: well-known, registered, and dynamic or private. The well-known ports are assigned by the [Internet Assigned Numbers Authority](https://en.wikipedia.org/wiki/Internet_Assigned_Numbers_Authority "Internet Assigned Numbers Authority") (IANA) and are typically used by system-level processes. Well-known applications running as servers and passively listening for connections typically use these ports. Some examples include: [FTP](https://en.wikipedia.org/wiki/File_Transfer_Protocol "File Transfer Protocol") (20 and 21), [SSH](https://en.wikipedia.org/wiki/Secure_Shell "Secure Shell") (22), [TELNET](https://en.wikipedia.org/wiki/TELNET "TELNET") (23), [SMTP](https://en.wikipedia.org/wiki/SMTP "SMTP") (25), [HTTP over SSL/TLS](https://en.wikipedia.org/wiki/HTTPS "HTTPS") (443), and [HTTP](https://en.wikipedia.org/wiki/HTTP "HTTP") (80). Registered ports are typically used by end-user applications as [ephemeral](https://en.wikipedia.org/wiki/Ephemeral_port "Ephemeral port") source ports when contacting servers, but they can also identify named services that have been registered by a third party. Dynamic or private ports can also be used by end-user applications, however, these ports typically do not contain any meaning outside a particular TCP connection.

[Network Address Translation](https://en.wikipedia.org/wiki/Network_Address_Translation "Network Address Translation") (NAT), typically uses dynamic port numbers, on the public-facing side, to [disambiguate](https://en.wikipedia.org/wiki/Disambiguation "Disambiguation") the flow of traffic that is passing between a public network and a private [subnetwork](https://en.wikipedia.org/wiki/Subnetwork "Subnetwork"), thereby allowing many IP addresses (and their ports) on the subnet to be serviced by a single public-facing address.

### Development
TCP is a complex protocol. However, while significant enhancements have been made and proposed over the years, its most basic operation has not changed significantly since its first specification [RFC 675](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#CITEREFRFC_675) in 1974, and the v4 specification [RFC 793](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#CITEREFRFC_793), published in September 1981. [RFC 1122](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#CITEREFRFC_1122), published in October 1989, clarified a number of TCP protocol implementation requirements. A list of the 8 required specifications and over 20 strongly encouraged enhancements is available in [RFC 7414](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#CITEREFRFC_7414). Among this list is [RFC 2581](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#CITEREFRFC_2581), TCP Congestion Control, one of the most important TCP-related RFCs in recent years, describes updated algorithms that avoid undue congestion. In 2001, [RFC 3168](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#CITEREFRFC_3168) was written to describe [Explicit Congestion Notification](https://en.wikipedia.org/wiki/Explicit_Congestion_Notification "Explicit Congestion Notification") (ECN), a congestion avoidance signaling mechanism.

The original TCP congestion avoidance algorithm was known as _TCP Tahoe_, but many alternative algorithms have since been proposed (including [TCP Reno](https://en.wikipedia.org/wiki/TCP_Reno "TCP Reno"), [TCP Vegas](https://en.wikipedia.org/wiki/TCP_Vegas "TCP Vegas"), [FAST TCP](https://en.wikipedia.org/wiki/FAST_TCP "FAST TCP"), [TCP New Reno](https://en.wikipedia.org/wiki/TCP_New_Reno "TCP New Reno"), and [TCP Hybla](https://en.wikipedia.org/wiki/TCP_Hybla "TCP Hybla")).

[Multipath TCP](https://en.wikipedia.org/wiki/Multipath_TCP "Multipath TCP") (MPTCP) is an ongoing effort within the IETF that aims at allowing a TCP connection to use multiple paths to maximize resource usage and increase redundancy. The redundancy offered by Multipath TCP in the context of wireless networks enables the simultaneous use of different networks, which brings higher throughput and better handover capabilities. Multipath TCP also brings performance benefits in datacenter environments. The reference implementation of Multipath TCP was developed in the Linux kernel. Multipath TCP is used to support the Siri voice recognition application on iPhones, iPads and Macs.

[tcpcrypt](https://en.wikipedia.org/wiki/Tcpcrypt "Tcpcrypt") is an extension proposed in July 2010 to provide transport-level encryption directly in TCP itself. It is designed to work transparently and not require any configuration. Unlike [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security") (SSL), tcpcrypt itself does not provide authentication, but provides simple primitives down to the application to do that. The tcpcrypt RFC was published by the IETF in May 2019.

[TCP Fast Open](https://en.wikipedia.org/wiki/TCP_Fast_Open "TCP Fast Open") is an extension to speed up the opening of successive TCP connections between two endpoints. It works by skipping the three-way handshake using a cryptographic _cookie_. It is similar to an earlier proposal called [T/TCP](https://en.wikipedia.org/wiki/T/TCP "T/TCP"), which was not widely adopted due to security issues. TCP Fast Open was published as [RFC 7413](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#CITEREFRFC_7413) in 2014.

(PRR) is a TCP extension developed by Google engineers. PRR ensures that the TCP window size after recovery is as close to the [slow start](https://en.wikipedia.org/wiki/TCP_congestion_control#Slow_start "TCP congestion control") threshold as possible. The algorithm is designed to improve the speed of recovery and is the default congestion control algorithm in Linux 3.2+ kernels.

#### Deprecated proposals
[TCP Cookie Transactions](https://en.wikipedia.org/wiki/TCP_Cookie_Transactions "TCP Cookie Transactions") (TCPCT) is an extension proposed in December 2009 to secure servers against denial-of-service attacks. Unlike SYN cookies, TCPCT does not conflict with other TCP extensions such as [window scaling](https://en.wikipedia.org/wiki/Window_scaling "Window scaling"). TCPCT was designed due to necessities of [DNSSEC](https://en.wikipedia.org/wiki/DNSSEC "DNSSEC"), where servers have to handle large numbers of short-lived TCP connections. In 2016, TCPCT was [deprecated](https://en.wikipedia.org/wiki/Deprecated "Deprecated") in favor of TCP Fast Open. The status of the original RFC was changed to _historic_.

### Hardware implementations
One way to overcome the processing power requirements of TCP is to build hardware implementations of it, widely known as [TCP offload engines](https://en.wikipedia.org/wiki/TCP_offload_engine "TCP offload engine") (TOE). The main problem of TOEs is that they are hard to integrate into computing systems, requiring extensive changes in the operating system of the computer or device.

### Wire image and ossification
The [wire data](https://en.wikipedia.org/wiki/Wire_data "Wire data") of TCP provides significant information-gathering and modification opportunities to on-path observers, as the protocol metadata is transmitted in [cleartext](https://en.wikipedia.org/wiki/Cleartext "Cleartext"). While this transparency is useful to network operators and researchers, information gathered from protocol metadata may reduce the end-user's privacy. This visibility and malleability of metadata has led to TCP being difficult to extend—a case of [protocol ossification](https://en.wikipedia.org/wiki/Protocol_ossification "Protocol ossification")—as any intermediate node (a '[middlebox](https://en.wikipedia.org/wiki/Middlebox "Middlebox")') can make decisions based on that metadata or even modify it, breaking the [end-to-end principle](https://en.wikipedia.org/wiki/End-to-end_principle "End-to-end principle"). One measurement found that a third of paths across the Internet encounter at least one intermediary that modifies TCP metadata, and 6.5% of paths encounter harmful ossifying effects from intermediaries.[[103]](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#cite_note-FOOTNOTEEdelineDonnet2019175-176-108) Avoiding extensibility hazards from intermediaries placed significant constraints on the design of [MPTCP](https://en.wikipedia.org/wiki/MPTCP "MPTCP"), and difficulties caused by intermediaries have hindered the deployment of TCP Fast Open in [web browsers](https://en.wikipedia.org/wiki/Web_browsers "Web browsers"). Another source of ossification is the difficulty of modification of TCP functions at the endpoints, typically in the [operating system kernel](https://en.wikipedia.org/wiki/Operating_system_kernel "Operating system kernel") or in hardware with a [TCP offload engine](https://en.wikipedia.org/wiki/TCP_offload_engine "TCP offload engine").

### Performance
As TCP provides applications with the abstraction of a [reliable byte stream](https://en.wikipedia.org/wiki/Reliable_byte_stream "Reliable byte stream"), it can suffer from [head-of-line blocking](https://en.wikipedia.org/wiki/Head-of-line_blocking "Head-of-line blocking"): if [packets are reordered](https://en.wikipedia.org/wiki/Packet_reordering "Packet reordering") or [lost](https://en.wikipedia.org/wiki/Packet_loss "Packet loss") and need to be retransmitted (and thus are reordered), data from sequentially later parts of the stream may be received before sequentially earlier parts of the stream; however, the later data cannot typically be used until the earlier data has been received, incurring [network latency](https://en.wikipedia.org/wiki/Network_latency "Network latency"). If multiple independent higher-level messages are [encapsulated](https://en.wikipedia.org/wiki/Encapsulation_\(networking\) "Encapsulation (networking)") and [multiplexed](https://en.wikipedia.org/wiki/Time-division_multiplexing "Time-division multiplexing") onto a single TCP connection, then head-of-line blocking can cause processing of a fully-received message that was sent later to wait for delivery of a message that was sent earlier. [Web browsers](https://en.wikipedia.org/wiki/Web_browsers "Web browsers") attempt to mitigate head-of-line blocking by opening multiple parallel connections. This incurs the cost of connection establishment repeatedly, as well as multiplying the resources needed to track those connections at the endpoints.Parallel connections also have congestion control operating independently of each other, rather than being able to pool information together and respond more promptly to observed network conditions; TCP's aggressive initial sending patterns can cause congestion if multiple parallel connections are opened; and the per-connection fairness model leads to a monopolization of resources by applications that take this approach.

Connection establishment is a major contributor to latency as experienced by web users. TCP's three-way handshake introduces one RTT of latency during connection establishment before data can be sent. For short flows, these delays are very significant. [Transport Layer Security](https://en.wikipedia.org/wiki/Transport_Layer_Security "Transport Layer Security") (TLS) requires a handshake of its own for [key exchange](https://en.wikipedia.org/wiki/Key_exchange "Key exchange") at connection establishment. Because of the layered design, the TCP handshake and the TLS handshake proceed serially; the TLS handshake cannot begin until the TCP handshake has concluded. Two RTTs are required for connection establishment with [TLS 1.2](https://en.wikipedia.org/wiki/TLS_1.2 "TLS 1.2") over TCP. [TLS 1.3](https://en.wikipedia.org/wiki/TLS_1.3 "TLS 1.3") allows for zero RTT connection resumption in some circumstances, but, when layered over TCP, one RTT is still required for the TCP handshake, and this cannot assist the initial connection; zero RTT handshakes also present cryptographic challenges, as efficient, [replay-safe](https://en.wikipedia.org/wiki/Replay-safe "Replay-safe") and [forward secure](https://en.wikipedia.org/wiki/Forward_secure "Forward secure") [non-interactive key exchange](https://en.wikipedia.org/wiki/Non-interactive_key_exchange "Non-interactive key exchange") is an open research topic. TCP Fast Open allows the transmission of data in the initial (i.e., SYN and SYN-ACK) packets, removing one RTT of latency during connection establishment. However, TCP Fast Open has been difficult to deploy due to protocol ossification; as of 2020, no [Web browsers](https://en.wikipedia.org/wiki/Web_browser "Web browser") used it by default.

TCP throughput is affected by [packet reordering](https://en.wikipedia.org/wiki/Packet_reordering "Packet reordering"). Reordered packets can cause duplicate acknowledgments to be sent, which, if they cross a threshold, will then trigger a spurious retransmission and congestion control. Transmission behavior can also become bursty, as large ranges are acknowledged all at once when a reordered packet at the range's start is received (in a manner similar to how head-of-line blocking affects applications). [Blanton & Allman (2002)](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#CITEREFBlantonAllman2002) found that throughput was inversely related to the amount of reordering, up to a threshold where all reordering triggers spurious retransmission. Mitigating reordering depends on a sender's ability to determine that it has sent a spurious retransmission, and hence on resolving retransmission ambiguity. Reducing reordering-induced spurious retransmissions may slow recovery from genuine loss.

Selective acknowledgment can provide a significant benefit to throughput; [Bruyeron, Hemon & Zhang (1998)](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#CITEREFBruyeronHemonZhang1998) measured gains of up to 45%. An important factor in the improvement is that selective acknowledgment can more often avoid going into slow start after a loss and can hence better use available bandwidth. However, TCP can only selectively acknowledge a maximum of three blocks of sequence numbers. This can limit the retransmission rate and hence loss recovery or cause needless retransmissions, especially in high-loss environments.

TCP was originally designed for wired networks where packet loss is considered to be the result of [network congestion](https://en.wikipedia.org/wiki/Network_congestion "Network congestion") and the congestion window size is reduced dramatically as a precaution. However, wireless links are known to experience sporadic and usually temporary losses due to [fading](https://en.wikipedia.org/wiki/Fading "Fading"), shadowing, hand off, [interference](https://en.wikipedia.org/wiki/Interference_\(communication\) "Interference (communication)"), and other radio effects, that are not strictly congestion. After the (erroneous) back-off of the congestion window size, due to wireless packet loss, there may be a congestion avoidance phase with a conservative decrease in window size. This causes the radio link to be underused. Extensive research on combating these harmful effects has been conducted. Suggested solutions can be categorized as end-to-end solutions, which require modifications at the client or server, link layer solutions, such as [Radio Link Protocol](https://en.wikipedia.org/wiki/Radio_Link_Protocol "Radio Link Protocol") in cellular networks, or proxy-based solutions which require some changes in the network without modifying end nodes. A number of alternative congestion control algorithms, such as [Vegas](https://en.wikipedia.org/wiki/TCP_Vegas "TCP Vegas"), [Westwood](https://en.wikipedia.org/wiki/TCP_Westwood "TCP Westwood"), Veno, and Santa Cruz, have been proposed to help solve the wireless problem.

### Acceleration
The idea of a TCP accelerator is to terminate TCP connections inside the network processor and then relay the data to a second connection toward the end system. The data packets that originate from the sender are buffered at the accelerator node, which is responsible for performing local retransmissions in the event of packet loss. Thus, in case of losses, the feedback loop between the sender and the receiver is shortened to the one between the acceleration node and the receiver which guarantees a faster delivery of data to the receiver.

Since TCP is a rate-adaptive protocol, the rate at which the TCP sender injects packets into the network is directly proportional to the prevailing load condition within the network as well as the processing capacity of the receiver. The prevalent conditions within the network are judged by the sender on the basis of the acknowledgments received by it. The acceleration node splits the feedback loop between the sender and the receiver and thus guarantees a shorter round trip time (RTT) per packet. A shorter RTT is beneficial as it ensures a quicker response time to any changes in the network and a faster adaptation by the sender to combat these changes.

Disadvantages of the method include the fact that the TCP session has to be directed through the accelerator; this means that if routing changes so that the accelerator is no longer in the path, the connection will be broken. It also destroys the end-to-end property of the TCP ACK mechanism; when the ACK is received by the sender, the packet has been stored by the accelerator, not delivered to the receiver.

### Debugging
A [packet sniffer](https://en.wikipedia.org/wiki/Packet_sniffer "Packet sniffer"), which [taps](https://en.wikipedia.org/wiki/Network_tap "Network tap") TCP traffic on a network link, can be useful in debugging networks, network stacks, and applications that use TCP by showing an engineer what packets are passing through a link. Some networking stacks support the SO_DEBUG socket option, which can be enabled on the socket using setsockopt. That option dumps all the packets, TCP states, and events on that socket, which is helpful in debugging. [Netstat](https://en.wikipedia.org/wiki/Netstat "Netstat") is another utility that can be used for debugging.

### Alternatives
For many applications TCP is not appropriate. The application cannot normally access the packets coming after a lost packet until the retransmitted copy of the lost packet is received. This causes problems for real-time applications such as streaming media, real-time multiplayer games and [voice over IP](https://en.wikipedia.org/wiki/Voice_over_IP "Voice over IP") (VoIP) where it is generally more useful to get most of the data in a timely fashion than it is to get all of the data in order.

For historical and performance reasons, most [storage area networks](https://en.wikipedia.org/wiki/Storage_area_network "Storage area network") (SANs) use [Fibre Channel Protocol](https://en.wikipedia.org/wiki/Fibre_Channel_Protocol "Fibre Channel Protocol") (FCP) over [Fibre Channel](https://en.wikipedia.org/wiki/Fibre_Channel "Fibre Channel") connections. For [embedded systems](https://en.wikipedia.org/wiki/Embedded_system "Embedded system"), [network booting](https://en.wikipedia.org/wiki/Network_booting "Network booting"), and servers that serve simple requests from huge numbers of clients (e.g. [DNS](https://en.wikipedia.org/wiki/Domain_name_system "Domain name system") servers) the complexity of TCP can be a problem. Tricks such as transmitting data between two hosts that are both behind [NAT](https://en.wikipedia.org/wiki/Network_address_translation "Network address translation") (using [STUN](https://en.wikipedia.org/wiki/STUN "STUN") or similar systems) are far simpler without a relatively complex protocol like TCP in the way.

Generally, where TCP is unsuitable, the [User Datagram Protocol](https://en.wikipedia.org/wiki/User_Datagram_Protocol "User Datagram Protocol") (UDP) is used. This provides the same application [multiplexing](https://en.wikipedia.org/wiki/Multiplexing "Multiplexing") and checksums that TCP does, but does not handle streams or retransmission, giving the application developer the ability to code them in a way suitable for the situation, or to replace them with other methods such as [forward error correction](https://en.wikipedia.org/wiki/Forward_error_correction "Forward error correction") or [error concealment](https://en.wikipedia.org/wiki/Error_concealment "Error concealment").

[Stream Control Transmission Protocol](https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol "Stream Control Transmission Protocol") (SCTP) is another protocol that provides reliable stream-oriented services similar to TCP. It is newer and considerably more complex than TCP, and has not yet seen widespread deployment. However, it is especially designed to be used in situations where reliability and near-real-time considerations are important.

[Venturi Transport Protocol](https://en.wikipedia.org/wiki/Venturi_Transport_Protocol "Venturi Transport Protocol") (VTP) is a patented [proprietary protocol](https://en.wikipedia.org/wiki/Proprietary_protocol "Proprietary protocol") that is designed to replace TCP transparently to overcome perceived inefficiencies related to wireless data transport.

The [TCP congestion avoidance algorithm](https://en.wikipedia.org/wiki/TCP_congestion_avoidance_algorithm "TCP congestion avoidance algorithm") works very well for ad-hoc environments where the data sender is not known in advance. If the environment is predictable, a timing-based protocol such as [Asynchronous Transfer Mode](https://en.wikipedia.org/wiki/Asynchronous_Transfer_Mode "Asynchronous Transfer Mode") (ATM) can avoid TCP's retransmission overhead.

[UDP-based Data Transfer Protocol](https://en.wikipedia.org/wiki/UDP-based_Data_Transfer_Protocol "UDP-based Data Transfer Protocol") (UDT) has better efficiency and fairness than TCP in networks that have high [bandwidth-delay product](https://en.wikipedia.org/wiki/Bandwidth-delay_product "Bandwidth-delay product").

[Multipurpose Transaction Protocol](https://en.wikipedia.org/wiki/Multipurpose_Transaction_Protocol "Multipurpose Transaction Protocol") (MTP/IP) is patented proprietary software that is designed to adaptively achieve high throughput and transaction performance in a wide variety of network conditions, particularly those where TCP is perceived to be inefficient.

### Checksum computation
#### TCP checksum for IPv4
When TCP runs over [IPv4](https://en.wikipedia.org/wiki/IPv4 "IPv4"), the method used to compute the checksum is defined as follows:

> _The checksum field is the 16-bit ones' complement of the ones' complement sum of all 16-bit words in the header and text. The checksum computation needs to ensure the 16-bit alignment of the data being summed. If a segment contains an odd number of header and text octets, alignment can be achieved by padding the last octet with zeros on its right to form a 16-bit word for checksum purposes. The pad is not transmitted as part of the segment. While computing the checksum, the checksum field itself is replaced with zeros._

In other words, after appropriate padding, all 16-bit words are added using [ones' complement arithmetic](https://en.wikipedia.org/wiki/End-around_carry "End-around carry"). The sum is then bitwise complemented and inserted as the checksum field. A pseudo-header that mimics the IPv4 packet header used in the checksum computation is as follows:

The checksum is computed over the following fields:

Source address: 32 bits

The source address in the IPv4 header

Destination address: 32 bits

The destination address in the IPv4 header

Zeroes: 8 bits

All zeroes

Protocol: 8 bits

The protocol value for TCP: 6

TCP length: 16 bits

The length of the TCP header and data (measured in octets). For example, let's say we have IPv4 packet with Total Length of 200 bytes and IHL value of 5, which indicates a length of 5 bits × 32 bits = 160 bits = 20 bytes. We can compute the TCP length as (Total Length) − (IPv4 Header Length) i.e. 200 − 20, which results in 180 bytes.

#### TCP checksum for IPv6
When TCP runs over [IPv6](https://en.wikipedia.org/wiki/IPv6 "IPv6"), the method used to compute the checksum is changed:

> _Any transport or other upper-layer protocol that includes the addresses from the IP header in its checksum computation must be modified for use over IPv6, to include the 128-bit IPv6 addresses instead of 32-bit IPv4 addresses._

A pseudo-header that mimics the IPv6 header for computation of the checksum is shown below.


The checksum is computed over the following fields:

Source address: 128 bits

The address in the IPv6 header.

Destination address: 128 bits

The final destination; if the IPv6 packet doesn't contain a Routing header, TCP uses the destination address in the IPv6 header, otherwise, at the originating node, it uses the address in the last element of the Routing header, and, at the receiving node, it uses the destination address in the IPv6 header.

TCP length: 32 bits

The length of the TCP header and data (measured in octets).

Zeroes: 24 bits; `Zeroes == 0`

All zeroes.

Next header: 8 bits

The protocol value for TCP: 6.

### Checksum offload 
Many TCP/IP software stack implementations provide options to use hardware assistance to automatically compute the checksum in the [network adapter](https://en.wikipedia.org/wiki/Network_adapter "Network adapter") prior to transmission onto the network or upon reception from the network for validation. This may relieve the OS from using precious CPU cycles calculating the checksum. Hence, overall network performance is increased.

This feature may cause [packet analyzers](https://en.wikipedia.org/wiki/Packet_analyzer "Packet analyzer") that are unaware or uncertain about the use of checksum offload to report invalid checksums in outbound packets that have not yet reached the network adapter. This will only occur for packets that are intercepted before being transmitted by the network adapter; all packets transmitted by the network adaptor on the wire will have valid checksums. This issue can also occur when monitoring packets being transmitted between virtual machines on the same host, where a virtual device driver may omit the checksum calculation (as an optimization), knowing that the checksum will be calculated later by the VM host kernel or its physical hardware.

## Internet Protocol (IP)
The **Internet Protocol** (**IP**) is the [network layer](https://en.wikipedia.org/wiki/Network_layer "Network layer") [communications protocol](https://en.wikipedia.org/wiki/Communications_protocol "Communications protocol") in the [Internet protocol suite](https://en.wikipedia.org/wiki/Internet_protocol_suite "Internet protocol suite") for relaying [datagrams](https://en.wikipedia.org/wiki/Datagram "Datagram") across network boundaries. Its [routing](https://en.wikipedia.org/wiki/Routing "Routing") function enables [internetworking](https://en.wikipedia.org/wiki/Internetworking "Internetworking"), and essentially establishes the [Internet](https://en.wikipedia.org/wiki/Internet "Internet").

IP has the task of delivering [packets](https://en.wikipedia.org/wiki/Packet_\(information_technology\) "Packet (information technology)") from the source [host](https://en.wikipedia.org/wiki/Host_\(network\) "Host (network)") to the destination host solely based on the [IP addresses](https://en.wikipedia.org/wiki/IP_address "IP address") in the packet [headers](https://en.wikipedia.org/wiki/Header_\(computing\) "Header (computing)"). For this purpose, IP defines packet structures that [encapsulate](https://en.wikipedia.org/wiki/Encapsulation_\(networking\) "Encapsulation (networking)") the data to be delivered. It also defines addressing methods that are used to label the datagram with source and destination information. IP was the [connectionless](https://en.wikipedia.org/wiki/Connectionless "Connectionless") datagram service in the original _[Transmission Control Program](https://en.wikipedia.org/wiki/Transmission_Control_Program "Transmission Control Program")_ introduced by [Vint Cerf](https://en.wikipedia.org/wiki/Vint_Cerf "Vint Cerf") and [Bob Kahn](https://en.wikipedia.org/wiki/Bob_Kahn "Bob Kahn") in 1974, which was complemented by a [connection-oriented](https://en.wikipedia.org/wiki/Connection-oriented "Connection-oriented") service that became the basis for the [Transmission Control Protocol](https://en.wikipedia.org/wiki/Transmission_Control_Protocol "Transmission Control Protocol") (TCP). The Internet protocol suite is therefore often referred to as _TCP/IP_.

The first major version of IP, [Internet Protocol version 4](https://en.wikipedia.org/wiki/Internet_Protocol_version_4 "Internet Protocol version 4") (IPv4), is the dominant protocol of the Internet. Its successor is [Internet Protocol version 6](https://en.wikipedia.org/wiki/Internet_Protocol_version_6 "Internet Protocol version 6") (IPv6), which has been in increasing [deployment](https://en.wikipedia.org/wiki/IPv6_deployment "IPv6 deployment") on the public Internet since around 2006.

### Function[![](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3b/UDP_encapsulation.svg/330px-UDP_encapsulation.svg.png)](https://en.wikipedia.org/wiki/File:UDP_encapsulation.svg)

Encapsulation of application data carried by [UDP](https://en.wikipedia.org/wiki/User_Datagram_Protocol "User Datagram Protocol") to a link protocol frame

The Internet Protocol is responsible for addressing [host interfaces](https://en.wikipedia.org/wiki/Host_interface "Host interface"), encapsulating data into datagrams (including [fragmentation and reassembly](https://en.wikipedia.org/wiki/IP_fragmentation "IP fragmentation")) and routing datagrams from a source host interface to a destination host interface across one or more IP networks. For these purposes, the Internet Protocol defines the format of packets and provides an addressing system.

Each datagram has two components: a [header](https://en.wikipedia.org/wiki/Header_\(computing\) "Header (computing)") and a [payload](https://en.wikipedia.org/wiki/Payload_\(computing\) "Payload (computing)"). The [IP header](https://en.wikipedia.org/wiki/IP_header "IP header") includes a source IP address, a destination IP address, and other metadata needed to route and deliver the datagram. The payload is the data that is transported. This method of nesting the data payload in a packet with a header is called encapsulation.

IP addressing entails the assignment of IP addresses and associated parameters to host interfaces. The address space is divided into [subnets](https://en.wikipedia.org/wiki/Subnet "Subnet"), involving the designation of network prefixes. IP routing is performed by all hosts, as well as [routers](https://en.wikipedia.org/wiki/Router_\(computing\) "Router (computing)"), whose main function is to transport packets across network boundaries. Routers communicate with one another via specially designed [routing protocols](https://en.wikipedia.org/wiki/Routing_protocol "Routing protocol"), either [interior gateway protocols](https://en.wikipedia.org/wiki/Interior_gateway_protocol "Interior gateway protocol") or [exterior gateway protocols](https://en.wikipedia.org/wiki/Exterior_gateway_protocol "Exterior gateway protocol"), as needed for the topology of the network.

### Addressing methods

|[Routing schemes](https://en.wikipedia.org/wiki/Routing#Delivery_schemes "Routing")|
|---|
|[Unicast](https://en.wikipedia.org/wiki/Unicast "Unicast")<br><br>[![](https://upload.wikimedia.org/wikipedia/commons/thumb/7/75/Unicast.svg/120px-Unicast.svg.png)](https://en.wikipedia.org/wiki/Unicast "Unicast")|
|[Broadcast](https://en.wikipedia.org/wiki/Broadcasting_\(networking\) "Broadcasting (networking)")<br><br>[![](https://upload.wikimedia.org/wikipedia/commons/thumb/d/dc/Broadcast.svg/120px-Broadcast.svg.png)](https://en.wikipedia.org/wiki/Broadcasting_\(networking\) "Broadcasting (networking)")|
|[Multicast](https://en.wikipedia.org/wiki/Multicast "Multicast")<br><br>[![](https://upload.wikimedia.org/wikipedia/commons/thumb/3/30/Multicast.svg/120px-Multicast.svg.png)](https://en.wikipedia.org/wiki/Multicast "Multicast")|
|[Anycast](https://en.wikipedia.org/wiki/Anycast "Anycast")<br><br>[![](https://upload.wikimedia.org/wikipedia/en/thumb/1/18/Anycast-BM.svg/120px-Anycast-BM.svg.png)](https://en.wikipedia.org/wiki/Anycast "Anycast")|

There are four principal addressing methods in the Internet Protocol:

- [Unicast](https://en.wikipedia.org/wiki/Unicast "Unicast") delivers a message to a single specific node using a _one-to-one_ association between a sender and destination: each destination address uniquely identifies a single receiver endpoint.
- [Broadcast](https://en.wikipedia.org/wiki/Broadcasting_\(networking\) "Broadcasting (networking)") delivers a message to all nodes in the network using a _one-to-all_ association; a single [datagram](https://en.wikipedia.org/wiki/Datagram "Datagram") (or [packet](https://en.wikipedia.org/wiki/Packet_\(information_technology\) "Packet (information technology)")) from one sender is routed to all of the possibly multiple endpoints associated with the [broadcast address](https://en.wikipedia.org/wiki/Broadcast_address "Broadcast address"). The network automatically replicates datagrams as needed to reach all the recipients within the scope of the broadcast, which is generally an entire network [subnet](https://en.wikipedia.org/wiki/Subnetwork "Subnetwork").
- [Multicast](https://en.wikipedia.org/wiki/Multicast "Multicast") delivers a message to a group of nodes that have expressed interest in receiving the message using a _one-to-many-of-many_ or _many-to-many-of-many_ association; datagrams are routed simultaneously in a single transmission to many recipients. Multicast differs from broadcast in that the destination address designates a subset, not necessarily all, of the accessible nodes.
- [Anycast](https://en.wikipedia.org/wiki/Anycast "Anycast") delivers a message to any one out of a group of nodes, typically the one nearest to the source using a _one-to-one-of-many_ association where datagrams are routed to any single member of a group of potential receivers that are all identified by the same destination address. The routing algorithm selects the single receiver from the group based on which is the nearest according to some distance or cost measure.

### Version history
[![](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3e/TCP_and_IP_protocols_development_timeline-en.svg/250px-TCP_and_IP_protocols_development_timeline-en.svg.png)](https://en.wikipedia.org/wiki/File:TCP_and_IP_protocols_development_timeline-en.svg)

A timeline for the development of the transmission control Protocol TCP and Internet Protocol IP

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/1/13/First_Internet_Demonstration%2C_1977.jpg/250px-First_Internet_Demonstration%2C_1977.jpg)](https://en.wikipedia.org/wiki/File:First_Internet_Demonstration,_1977.jpg)

First Internet demonstration, linking the [ARPANET](https://en.wikipedia.org/wiki/ARPANET "ARPANET"), [PRNET](https://en.wikipedia.org/wiki/PRNET "PRNET"), and [SATNET](https://en.wikipedia.org/wiki/SATNET "SATNET") on November 22, 1977

In May 1974, the [Institute of Electrical and Electronics Engineers](https://en.wikipedia.org/wiki/Institute_of_Electrical_and_Electronics_Engineers "Institute of Electrical and Electronics Engineers") (IEEE) published a paper entitled "A Protocol for Packet Network Intercommunication". The paper's authors, [Vint Cerf](https://en.wikipedia.org/wiki/Vint_Cerf "Vint Cerf") and [Bob Kahn](https://en.wikipedia.org/wiki/Bob_Kahn "Bob Kahn"), described an [internetworking](https://en.wikipedia.org/wiki/Internetworking "Internetworking") protocol for sharing resources using [packet switching](https://en.wikipedia.org/wiki/Packet_switching "Packet switching") among [network nodes](https://en.wikipedia.org/wiki/Network_node "Network node"). A central control component of this model was the Transmission Control Program that incorporated both connection-oriented links and datagram services between hosts. The monolithic Transmission Control Program was later divided into a modular architecture consisting of the [Transmission Control Protocol](https://en.wikipedia.org/wiki/Transmission_Control_Protocol "Transmission Control Protocol") and [User Datagram Protocol](https://en.wikipedia.org/wiki/User_Datagram_Protocol "User Datagram Protocol") at the [transport layer](https://en.wikipedia.org/wiki/Transport_layer "Transport layer") and the Internet Protocol at the [internet layer](https://en.wikipedia.org/wiki/Internet_layer "Internet layer"). The model became known as the _Department of Defense (DoD) Internet Model_ and _[Internet protocol suite](https://en.wikipedia.org/wiki/Internet_protocol_suite "Internet protocol suite")_, and informally as _TCP/IP_.

The following [Internet Experiment Note](https://en.wikipedia.org/wiki/Internet_Experiment_Note "Internet Experiment Note") (IEN) documents describe the evolution of the Internet Protocol into the modern version of IPv4:

- [IEN 2](http://www.rfc-editor.org/ien/ien2.txt) _Comments on Internet Protocol and TCP (_August 1977) describes the need to separate the TCP and Internet Protocol functionalities (which were previously combined). It proposes the first version of the IP header, using 0 for the version field.
- [IEN 26](http://www.rfc-editor.org/ien/ien26.pdf) _A Proposed New Internet Header Format (_February 1978) describes a version of the IP header that uses a 1-bit version field.
- [IEN 28](http://www.rfc-editor.org/ien/ien28.pdf) _Draft Internetwork Protocol Description Version 2 (_February 1978) describes IPv2.
- [IEN 41](http://www.rfc-editor.org/ien/ien41.pdf) _Internetwork Protocol Specification Version 4 (_June 1978) describes the first protocol to be called IPv4. The IP header is different from the modern IPv4 header.
- [IEN 44](http://www.rfc-editor.org/ien/ien44.pdf) _Latest Header Formats (_June 1978) describes another version of IPv4, also with a header different from the modern IPv4 header.
- [IEN 54](http://www.rfc-editor.org/ien/ien54.pdf) _Internetwork Protocol Specification Version 4 (_September 1978) is the first description of IPv4 using the header that would become standardized in 1980 as [RFC](https://en.wikipedia.org/wiki/RFC_\(identifier\) "RFC (identifier)") [760](https://www.rfc-editor.org/rfc/rfc760).
- IEN 80
- IEN 111
- IEN 123
- IEN 128/RFC 760 (1980)

IP versions 1 to 3 were experimental versions, designed between 1973 and 1978. Versions 2 and 3 supported variable-length addresses ranging between 1 and 16 octets (between 8 and 128 bits). An early draft of version 4 supported variable-length addresses of up to 256 octets (up to 2048 bits) but this was later abandoned in favor of a fixed-size 32-bit address in the final version of [IPv4](https://en.wikipedia.org/wiki/IPv4 "IPv4"). This remains the dominant internetworking protocol in use in the [Internet Layer](https://en.wikipedia.org/wiki/Internet_Layer "Internet Layer"); the number 4 identifies the protocol version, carried in every IP datagram. IPv4 is defined in [RFC](https://en.wikipedia.org/wiki/RFC_\(identifier\) "RFC (identifier)") [791](https://www.rfc-editor.org/rfc/rfc791) (1981).

Version number 5 was used by the [Internet Stream Protocol](https://en.wikipedia.org/wiki/Internet_Stream_Protocol "Internet Stream Protocol"), an experimental streaming protocol that was not adopted.

The successor to IPv4 is [IPv6](https://en.wikipedia.org/wiki/IPv6 "IPv6"). IPv6 was a result of several years of experimentation and dialog during which various protocol models were proposed, such as TP/IX ([RFC](https://en.wikipedia.org/wiki/RFC_\(identifier\) "RFC (identifier)") [1475](https://www.rfc-editor.org/rfc/rfc1475)), PIP ([RFC](https://en.wikipedia.org/wiki/RFC_\(identifier\) "RFC (identifier)") [1621](https://www.rfc-editor.org/rfc/rfc1621)) and TUBA (TCP and UDP with Bigger Addresses, [RFC](https://en.wikipedia.org/wiki/RFC_\(identifier\) "RFC (identifier)") [1347](https://www.rfc-editor.org/rfc/rfc1347)). Its most prominent difference from version 4 is the size of the addresses. While IPv4 uses [32 bits](https://en.wikipedia.org/wiki/32_bits "32 bits") for addressing, yielding c. 4.3 [billion](https://en.wikipedia.org/wiki/1,000,000,000_\(number\) "1,000,000,000 (number)") (4.3×109) addresses, IPv6 uses [128-bit](https://en.wikipedia.org/wiki/128-bit "128-bit") addresses providing c. 3.4×1038 addresses. Although adoption of IPv6 has been slow, as of January 2023, most countries in the world show significant adoption of IPv6, with over 41% of Google's traffic being carried over IPv6 connections.

The assignment of the new protocol as IPv6 was uncertain until due diligence assured that IPv6 had not been used previously. Other Internet Layer protocols have been assigned version numbers, such as 7 (_IP/TX_), 8 and 9 (_historic_). Notably, on April 1, 1994, the [IETF](https://en.wikipedia.org/wiki/IETF "IETF") published an [April Fools' Day RfC](https://en.wikipedia.org/wiki/April_Fools%27_Day_RfC "April Fools' Day RfC") about IPv9. IPv9 was also used in an alternate proposed address space expansion called TUBA. A 2004 Chinese proposal for [an IPv9 protocol](https://en.wikipedia.org/wiki/IPv9_\(China\) "IPv9 (China)") appears to be unrelated to all of these, and is not endorsed by the IETF.

#### IP version numbers
As the version number is carried in a 4-bit field, only numbers 0–15 can be assigned.

| IP version                                                                                                                    | Description                                                                                                                   | Year                         | Status                               |
| ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ---------------------------- | ------------------------------------ |
| 0                                                                                                                             | Internet Protocol, pre-v4                                                                                                     | N/A                          | Reserved                             |
| 1                                                                                                                             | Experimental version                                                                                                          | 1973                         | Obsolete                             |
| 2                                                                                                                             | Experimental version                                                                                                          | 1977                         | Obsolete                             |
| 3                                                                                                                             | Experimental version                                                                                                          | 1978                         | Obsolete                             |
| 4                                                                                                                             | [Internet Protocol version 4](https://en.wikipedia.org/wiki/Internet_Protocol_version_4 "Internet Protocol version 4") (IPv4) | 1981                         | Active                               |
| 5                                                                                                                             | [Internet Stream Protocol](https://en.wikipedia.org/wiki/Internet_Stream_Protocol "Internet Stream Protocol") (ST)            | 1979                         | Obsolete; superseded by ST-II or ST2 |
| [Internet Stream Protocol](https://en.wikipedia.org/wiki/Internet_Stream_Protocol "Internet Stream Protocol") (ST-II or ST2)  | 1987                                                                                                                          | Obsolete; superseded by ST2+ |                                      |
| [Internet Stream Protocol](https://en.wikipedia.org/wiki/Internet_Stream_Protocol "Internet Stream Protocol") (ST2+)          | 1995                                                                                                                          | Obsolete                     |                                      |
| 6                                                                                                                             | Simple Internet Protocol (SIP)                                                                                                | N/A                          | Obsolete; merged into IPv6 in 1995   |
| [Internet Protocol version 6](https://en.wikipedia.org/wiki/Internet_Protocol_version_6 "Internet Protocol version 6") (IPv6) | 1995                                                                                                                          | Active                       |                                      |
| 7                                                                                                                             | TP/IX The Next Internet (IPv7)[[20]](https                                                                                    | 1993                         | Obsolete                             |
| 8                                                                                                                             | P Internet Protocol (PIP)                                                                                                     | 1994                         | Obsolete; merged into SIP in 1993    |
| 9                                                                                                                             | TCP and UDP over Bigger Addresses (TUBA)                                                                                      | 1992                         | Obsolete                             |
| IPv9                                                                                                                          | 1994                                                                                                                          |                              |                                      |
| [Chinese IPv9](https://en.wikipedia.org/wiki/Chinese_IPv9 "Chinese IPv9")                                                     | 2004                                                                                                                          | Abandoned                    |                                      |
| 10–14                                                                                                                         | N/A                                                                                                                           | N/A                          | Unassigned                           |
| 15                                                                                                                            | _Version field sentinel value_                                                                                                | N/A                          | Reserved                             |
|                                                                                                                               |                                                                                                                               |                              |                                      |

### Reliability
The design of the Internet protocol suite adheres to the [end-to-end principle](https://en.wikipedia.org/wiki/End-to-end_principle "End-to-end principle"), a concept adapted from the [CYCLADES](https://en.wikipedia.org/wiki/CYCLADES "CYCLADES") project. Under the end-to-end principle, the network infrastructure is considered inherently unreliable at any single network element or transmission medium and is dynamic in terms of the availability of links and nodes. No central monitoring or performance measurement facility exists that tracks or maintains the state of the network. For the benefit of reducing [network complexity](https://en.wikipedia.org/wiki/Network_complexity "Network complexity"), the intelligence in the network is located in the [end nodes](https://en.wikipedia.org/wiki/End_node "End node").

As a consequence of this design, the Internet Protocol only provides [best-effort delivery](https://en.wikipedia.org/wiki/Best-effort_delivery "Best-effort delivery") and its service is characterized as [unreliable](https://en.wikipedia.org/wiki/Reliability_\(computer_networking\) "Reliability (computer networking)"). In network architectural parlance, it is a [connectionless protocol](https://en.wikipedia.org/wiki/Connectionless_protocol "Connectionless protocol"), in contrast to [connection-oriented communication](https://en.wikipedia.org/wiki/Connection-oriented_communication "Connection-oriented communication"). Various fault conditions may occur, such as [data corruption](https://en.wikipedia.org/wiki/Data_corruption "Data corruption"), [packet loss](https://en.wikipedia.org/wiki/Packet_loss "Packet loss") and duplication. Because routing is dynamic, meaning every packet is treated independently, and because the network maintains no state based on the path of prior packets, different packets may be routed to the same destination via different paths, resulting in [out-of-order delivery](https://en.wikipedia.org/wiki/Out-of-order_delivery "Out-of-order delivery") to the receiver.

All fault conditions in the network must be detected and compensated by the participating end nodes. The [upper layer protocols](https://en.wikipedia.org/wiki/Upper_layer_protocol "Upper layer protocol") of the Internet protocol suite are responsible for resolving reliability issues. For example, a host may [buffer](https://en.wikipedia.org/wiki/Data_buffer "Data buffer") network data to ensure correct ordering before the data is delivered to an application.

IPv4 provides safeguards to ensure that the header of an IP packet is error-free. A routing node discards packets that fail a header [checksum](https://en.wikipedia.org/wiki/Checksum "Checksum") test. Although the [Internet Control Message Protocol](https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol "Internet Control Message Protocol") (ICMP) provides notification of errors, a routing node is not required to notify either end node of errors. IPv6, by contrast, operates without header checksums, since current [link layer](https://en.wikipedia.org/wiki/Link_layer "Link layer") technology is assumed to provide sufficient error detection.

### Link capacity and capability
The dynamic nature of the Internet and the diversity of its components provide no guarantee that any particular path is actually capable of, or suitable for, performing the data transmission requested. One of the technical constraints is the size of data packets possible on a given link. Facilities exist to examine the [maximum transmission unit](https://en.wikipedia.org/wiki/Maximum_transmission_unit "Maximum transmission unit") (MTU) size of the local link and [Path MTU Discovery](https://en.wikipedia.org/wiki/Path_MTU_Discovery "Path MTU Discovery") can be used for the entire intended path to the destination.

The IPv4 internetworking layer automatically [fragments](https://en.wikipedia.org/wiki/IP_fragmentation "IP fragmentation") a datagram into smaller units for transmission when the link MTU is exceeded. IP provides re-ordering of fragments received out of order. An IPv6 network does not perform fragmentation in network elements, but requires end hosts and higher-layer protocols to avoid exceeding the path MTU.

The [Transmission Control Protocol](https://en.wikipedia.org/wiki/Transmission_Control_Protocol "Transmission Control Protocol") (TCP) is an example of a protocol that adjusts its segment size to be smaller than the MTU. The [User Datagram Protocol](https://en.wikipedia.org/wiki/User_Datagram_Protocol "User Datagram Protocol") (UDP) and ICMP disregard MTU size, thereby forcing IP to fragment oversized datagrams.

### Security
During the design phase of the [ARPANET](https://en.wikipedia.org/wiki/ARPANET "ARPANET") and the early Internet, the security aspects and needs of a public, international network were not adequately anticipated. Consequently, many Internet protocols exhibited vulnerabilities highlighted by network attacks and later security assessments. In 2008, a thorough security assessment and proposed mitigation of problems was published. The IETF has been pursuing further studies.

## Circular Reference
A **circular reference** (or **reference cycle** is a series of [references](https://en.wikipedia.org/wiki/Reference "Reference") where the last object references the first, resulting in a closed loop.

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b4/Circular_Reference.svg/250px-Circular_Reference.svg.png)](https://en.wikipedia.org/wiki/File:Circular_Reference.svg)

Circular reference (in red)

### Simple example
A newcomer asks a local where the town library is. "Just in front of the post office," says the local. The newcomer nods, and follows up: "But where is the post office?"

"Why, that's simple," replies the local. "It's just behind the library!"

### In language
A circular reference is not to be confused with the [logical fallacy](https://en.wikipedia.org/wiki/Logical_fallacy "Logical fallacy") of a [circular argument](https://en.wikipedia.org/wiki/Circular_argument "Circular argument"). Although a circular reference will often be unhelpful and reveal no information, such as two entries in a book index referring to each other, it is not necessarily so that a circular reference is of no use. Dictionaries, for instance, must always ultimately be a circular reference since all words in a dictionary are defined in terms of other words, but a dictionary nevertheless remains a useful reference. Sentences containing circular references can still be meaningful:

_Her brother gave her a kitten; his sister thanked him for it._

is circular, but not without meaning. Indeed, it can be argued that self-reference is a necessary consequence of Aristotle's [Law of non-contradiction](https://en.wikipedia.org/wiki/Law_of_non-contradiction "Law of non-contradiction"), a fundamental philosophical [axiom](https://en.wikipedia.org/wiki/Axiom "Axiom"). In this view, without self-reference, [logic](https://en.wikipedia.org/wiki/Logic "Logic") and [mathematics](https://en.wikipedia.org/wiki/Mathematics "Mathematics") become impossible, or at least, lack usefulness.

### In computer programming
For circular references between objects or resources, see [Reference counting](https://en.wikipedia.org/wiki/Reference_counting "Reference counting").

Circular references can appear in [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming") when one piece of code requires the result from another, but that code needs the result from the first. For example, the two functions, posn and plus1 in the following Python program comprise a circular reference:

```python
def posn(k: int) -> int:
    if k < 0:
        return plus1(k)
    return k

def plus1(n: int) -> int:
    return posn(n + 1)
```
Circular references like the above example may return valid results if they have a terminating condition. If there is no terminating condition, a circular reference leads to a condition known as [livelock](https://en.wikipedia.org/wiki/Livelock "Livelock") or [infinite loop](https://en.wikipedia.org/wiki/Infinite_loop "Infinite loop"), meaning it theoretically could run forever.

```python
def posn(k: int) -> int:
    return plus1(k)

def plus1(n: int) -> int:
    return posn(n + 1)
```

In ISO Standard, SQL circular integrity constraints are implicitly supported within a single table. Between multiple tables circular constraints (e.g. foreign keys) are permitted by defining the constraints as deferrable (See [CREATE TABLE](http://www.postgresql.org/docs/current/static/sql-createtable.html) for PostgreSQL and [DEFERRABLE Constraint Examples](http://docs.oracle.com/cd/B19306_01/server.102/b14200/clauses002.htm#i1015767) for Oracle). In that case the constraint is checked at the end of the transaction not at the time the DML statement is executed. To update a circular reference, two statements can be issued in a single transaction that will satisfy both references once the transaction is committed.

Circular references can also happen between instances of data of a mutable type, such as in this Python script:

```python
mydict = {
  "this": "that",
  "these": "those"
}

mydict["myself"] = mydict
print(mydict)
```

The `print(mydict)` function will output `{'this': 'that', 'these': 'those', 'myself': {...}}`, where `{...}` indicates a circular reference, in this case, to the `mydict` dictionary.

### In spreadsheets
Circular references also occur in [spreadsheets](https://en.wikipedia.org/wiki/Spreadsheet "Spreadsheet") when two cells require each other's result. For example, if the value in Cell A1 is to be obtained by adding 5 to the value in Cell B1, and the value in Cell B1 is to be obtained by adding 3 to the value in Cell A1, no values can be computed. (Even if the specifications are A1:=B1+5 and B1:=A1-5, there is still a circular reference. It does not help that, for instance, A1=3 and B1=-2 would satisfy both formulae, as there are infinitely many other possible values of A1 and B1 that can satisfy both instances.)

Circular reference in worksheets can be a very useful technique for solving implicit equations such as the [Colebrook equation](https://en.wikipedia.org/wiki/Colebrook_equation "Colebrook equation") and many others, which might otherwise require tedious [Newton-Raphson](https://en.wikipedia.org/wiki/Newton-Raphson "Newton-Raphson") algorithms in VBA or use of macros.

A distinction should be made with processes containing a circular reference between those that are incomputable and those that are an iterative calculation with a final output. The latter may fail in spreadsheets not equipped to handle them but are nevertheless still logically valid.

## Query String
A **query string** is a part of a uniform resource locator ([URL](https://en.wikipedia.org/wiki/URL "URL")) that assigns values to specified parameters. A query string commonly includes fields added to a base URL by a Web browser or other client application, for example as part of an HTML document, choosing the appearance of a page, or jumping to positions in multimedia content.

[![](https://upload.wikimedia.org/wikipedia/commons/0/06/Query_string.png)](https://en.wikipedia.org/wiki/File:Query_string.png)

An [address bar](https://en.wikipedia.org/wiki/Address_bar "Address bar") on [Google Chrome](https://en.wikipedia.org/wiki/Google_Chrome "Google Chrome") showing a URL (Uniform Resource Locator) with the query string `?title=Query_string&action=edit`

A web server can handle a [Hypertext Transfer Protocol](https://en.wikipedia.org/wiki/HTTPS "HTTPS") (HTTP) request either by reading a file from its [file system](https://en.wikipedia.org/wiki/File_system "File system") based on the [URL](https://en.wikipedia.org/wiki/URL "URL") path or by handling the request using logic that is specific to the type of resource. In cases where special logic is invoked, the query string will be available to that logic for use in its processing, along with the path component of the URL.

### Structure
A typical URL containing a query string is as follows:

> `https://example.com/over/there?name=ferret`

When a server receives a request for such a page, it may run a program, passing the query string, which in this case is `name=ferret`, unchanged to the program. The question mark is used as a separator, and is not part of the query string.

[Web frameworks](https://en.wikipedia.org/wiki/Web_Framework "Web Framework") may provide methods for parsing multiple parameters in the query string, separated by some delimiter. In the example URL below, multiple query parameters are separated by the [ampersand](https://en.wikipedia.org/wiki/Ampersand "Ampersand"), "`&`":

> `https://example.com/path/to/page?name=ferret&color=purple`

The exact structure of the query string is not standardized. Methods used to parse the query string may differ between websites.

A link in a web page may have a URL that contains a query string. [HTML](https://en.wikipedia.org/wiki/HTML "HTML") defines three ways a user agent can generate the query string:

- an [HTML form](https://en.wikipedia.org/wiki/Form_\(HTML\) "Form (HTML)") via the `<form>...</form>` element
- a [server-side image map](https://en.wikipedia.org/wiki/Image_map#Server-side "Image map") via the `ismap` attribute on the `<img>` element with an `<img ismap>` construction
- an indexed search via the now deprecated `<isindex>` element

#### Web forms
One of the original uses was to contain the content of an [HTML form](https://en.wikipedia.org/wiki/Form_\(HTML\) "Form (HTML)"), also known as web form. In particular, when a form containing the fields `field1`, `field2`, `field3` is submitted, the content of the fields is encoded as a query string as follows:

> `field1=value1&field2=value2&field3=value3...`

- The query string is composed of a series of field-value pairs.
- Within each pair, the field name and value are separated by an [equals sign](https://en.wikipedia.org/wiki/Equals_sign "Equals sign"), "`=`".
- The series of pairs is separated by the [ampersand](https://en.wikipedia.org/wiki/Ampersand "Ampersand"), "`&`" ([semicolons](https://en.wikipedia.org/wiki/Semicolons "Semicolons") "`;`" are not recommended by the [W3C](https://en.wikipedia.org/wiki/W3C "W3C") anymore, see below).

While there is no definitive standard, most [web frameworks](https://en.wikipedia.org/wiki/Web_framework "Web framework") allow multiple values to be associated with a single field (e.g. `field1=value1&field1=value2&field2=value3`).

For each [field](https://en.wikipedia.org/wiki/Field_\(computer_science\) "Field (computer science)") of the form, the query string contains a pair `field=value`. Web forms may include fields that are not visible to the user; these fields are included in the query string when the form is submitted.

This convention is a [W3C](https://en.wikipedia.org/wiki/W3C "W3C") recommendation. In the recommendations of 1999, W3C recommended that all web servers support [semicolon](https://en.wikipedia.org/wiki/Semicolon "Semicolon") separators in addition to [ampersand](https://en.wikipedia.org/wiki/Ampersand "Ampersand") separators to allow [application/x-www-form-urlencoded](https://en.wikipedia.org/wiki/Application/x-www-form-urlencoded "Application/x-www-form-urlencoded") query strings in URLs within HTML documents without having to entity escape ampersands. Since 2014, W3C recommends to use only [ampersand](https://en.wikipedia.org/wiki/Ampersand "Ampersand") as query separator.

The form content is only encoded in the URL's query string when the form submission method is [GET](https://en.wikipedia.org/wiki/GET_\(HTTP\) "GET (HTTP)"). The same encoding is used by default when the submission method is [POST](https://en.wikipedia.org/wiki/POST_\(HTTP\) "POST (HTTP)"), but the result is submitted as the [HTTP request](https://en.wikipedia.org/wiki/HTTP_request "HTTP request") body rather than being included in a modified URL.

#### Indexed search
Before [forms](https://en.wikipedia.org/wiki/Form_\(HTML\) "Form (HTML)") were added to HTML, browsers rendered the –`<isindex>` element as a single-line text-input control. The text entered into this control was sent to the server as a query string addition to a [GET](https://en.wikipedia.org/wiki/GET_\(HTTP\) "GET (HTTP)") request for the base URL or another URL specified by the `action` attribute. This was intended to allow web servers to use the provided text as query criteria so they could return a list of matching pages.

When the text input into the indexed search control is submitted, it is encoded as a query string as follows:

> `argument1+argument2+argument3...`

- The query string is composed of a series of arguments by parsing the text into words at the spaces.
- The series is separated by the [plus sign](https://en.wikipedia.org/wiki/Plus_sign "Plus sign"), '`+`'.

Though the `<isindex>` element is deprecated and most browsers no longer support or render it, there are still some vestiges of indexed search in existence. For example, this is the source of the special handling of [plus sign](https://en.wikipedia.org/wiki/Plus_sign "Plus sign"), '`+`' within browser URL percent encoding (which today, with the deprecation of indexed search, is all but redundant with `%20`). Also some web servers supporting [CGI](https://en.wikipedia.org/wiki/Common_Gateway_Interface "Common Gateway Interface") (e.g., [Apache](https://en.wikipedia.org/wiki/Apache_HTTP_Server "Apache HTTP Server")) will process the query string into command line arguments if it does not contain an [equals sign](https://en.wikipedia.org/wiki/Equals_sign "Equals sign"), '`=`' (as per section 4.4 of CGI 1.1). Some CGI scripts still depend on and use this historic behavior for URLs embedded in HTML.

### URL encoding
Some [characters](https://en.wikipedia.org/wiki/Character_\(computing\) "Character (computing)") cannot be part of a URL (for example, the space) and some other characters have a special meaning in a URL: for example, the character `#` can be used to further specify a subsection (or [fragment](https://en.wikipedia.org/wiki/Fragment_identifier "Fragment identifier")) of a document. In HTML forms, the character `=` is used to separate a name from a value. The URI generic syntax uses [URL encoding](https://en.wikipedia.org/wiki/Percent-encoding#Percent-encoding_reserved_characters "Percent-encoding") to deal with this problem, while HTML forms make some additional substitutions rather than applying percent encoding for all such characters. SPACE is encoded as '`+`' or "`%20`".

[HTML 5](https://en.wikipedia.org/wiki/HTML_5 "HTML 5") specifies the following transformation for submitting HTML forms with the "GET" method to a web server. The following is a brief summary of the algorithm:

- Characters that cannot be converted to the correct charset are replaced with HTML [numeric character references](https://en.wikipedia.org/wiki/Numeric_character_reference "Numeric character reference")
- SPACE is encoded as '`+`' or '`%20`'
- Letters (`A`–`Z` and `a`–`z`), numbers (`0`–`9`) and the characters '`~`','`-`','`.`' and '`_`' are left as-is
- `+` is encoded by %2B
- All other characters are encoded as a `%HH` [hexadecimal](https://en.wikipedia.org/wiki/Hexadecimal "Hexadecimal") representation with any non-ASCII characters first encoded as UTF-8 (or other specified encoding)

The octet corresponding to the tilde ("`~`") is permitted in query strings by RFC3986 but required to be percent-encoded in HTML forms to "`%7E`".

The encoding of SPACE as '`+`' and the selection of "as-is" characters distinguishes this encoding from RFC 3986.

### Example
If a [form](https://en.wikipedia.org/wiki/Form_\(web\) "Form (web)") is embedded in an [HTML](https://en.wikipedia.org/wiki/HTML "HTML") page as follows:

<form action="/cgi-bin/test.cgi" method="get">
  <input type="text" name="first" />
  <input type="text" name="second" />
  <input type="submit" />
</form>

and the user inserts the strings "this is a field" and "was it clear (already)?" in the two [text fields](https://en.wikipedia.org/wiki/Text_box "Text box") and presses the submit button, the program `test.cgi` (the program specified by the `action` [attribute](https://en.wikipedia.org/wiki/HTML_attribute "HTML attribute") of the `form` [element](https://en.wikipedia.org/wiki/HTML_element "HTML element") in the above example) will receive the following query string: `first=this+is+a+field&second=was+it+clear+%28already%29%3F`.

If the form is processed on the [server](https://en.wikipedia.org/wiki/Web_server "Web server") by a [CGI](https://en.wikipedia.org/wiki/Common_Gateway_Interface "Common Gateway Interface") [script](https://en.wikipedia.org/wiki/Scripting_language "Scripting language"), the script may typically receive the query string as an [environment variable](https://en.wikipedia.org/wiki/Environment_variable "Environment variable") named `QUERY_STRING`.

### Tracking
A program receiving a query string can ignore part or all of it. If the requested URL corresponds to a file and not to a program, the whole query string is ignored. However, regardless of whether the query string is used or not, the whole URL including it is stored in the server [log files](https://en.wikipedia.org/wiki/Computer_data_logging "Computer data logging").

These facts allow query strings to be used to track users in a manner similar to that provided by [HTTP cookies](https://en.wikipedia.org/wiki/HTTP_cookie "HTTP cookie"). For this to work, every time the user downloads a page, a unique identifier must be chosen and added as a query string to the URLs of all links the page contains. As soon as the user follows one of these links, the corresponding URL is requested to the server. This way, the download of this page is linked with the previous one.

For example, when a web page containing the following is requested:

 <a href="foo.html">see my page!</a>
 <a href="bar.html">mine is better</a>

a unique string, such as `e0a72cb2a2c7` is chosen, and the page is modified as follows:

 <a href="foo.html?e0a72cb2a2c7">see my page!</a>
 <a href="bar.html?e0a72cb2a2c7">mine is better</a>

The addition of the query string does not change the way the page is shown to the user. When the user follows, for example, the first link, the browser requests the page `foo.html?e0a72cb2a2c7` to the server, which ignores what follows `?` and sends the page `foo.html` as expected, adding the query string to its links as well.

This way, any subsequent page request from this user will carry the same query string `e0a72cb2a2c7`, making it possible to establish that all these pages have been viewed by the same user. Query strings are often used in association with [web beacons](https://en.wikipedia.org/wiki/Web_beacon "Web beacon").

The main differences between query strings used for tracking and HTTP cookies are that:

1. Query strings form part of the URL, and are therefore included if the user saves or sends the URL to another user; cookies can be maintained across browsing sessions, but are not saved or sent with the URL.
2. If the user arrives at the same web server by two (or more) independent paths, it will be assigned two different query strings, while the stored cookies are the same.
3. The user can disable cookies, in which case using cookies for tracking does not work. However, using query strings for tracking should work in all situations.
4. Different query strings passed by different visits to the page will mean that the pages are never served from the browser (or proxy, if present) cache thereby increasing the load on the web server and slowing down the user experience.

### Compatibility issues
According to the [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol "Hypertext Transfer Protocol") specification:

> Various ad hoc limitations on request-line length are found in practice. It is RECOMMENDED that all HTTP senders and recipients support, at a minimum, request-line lengths of 8000 octets.

If the URL is too long, the web server fails with the [414 Request-URI Too Long](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#414 "List of HTTP status codes") HTTP status code.

The common workaround for these problems is to use [POST](https://en.wikipedia.org/wiki/POST_\(HTTP\) "POST (HTTP)") instead of [GET](https://en.wikipedia.org/wiki/GET_\(HTTP\) "GET (HTTP)") and store the parameters in the request body. The length limits on request bodies are typically much higher than those on URL length. For example, the limit on POST size, by default, is 2 MB on IIS 4.0 and 128 KB on IIS 5.0. The limit is configurable on Apache2 using the `LimitRequestBody` directive, which specifies the number of bytes from 0 (meaning unlimited) to 2147483647 (2 GB) that are allowed in a request body.

## HTTP messages
**HTTP messages** are the mechanism used to exchange data between a server and a client in the HTTP protocol. There are two types of messages: **requests** sent by the client to trigger an action on the server, and **responses**, the answer that the server sends in response to a request.

Developers rarely, if ever, build HTTP messages from scratch. Applications such as a browser, proxy, or web server use software designed to create HTTP messages in a reliable and efficient way. How messages are created or transformed is controlled via APIs in browsers, configuration files for proxies or servers, or other interfaces.

In HTTP protocol versions up to HTTP/2, messages are text-based, and are relatively straightforward to read and understand after you've familiarized yourself with the format. In HTTP/2, messages are wrapped in binary framing, which makes them slightly harder to read without certain tools. However the underlying semantics of the protocol are the same, so you can learn the structure and meaning of HTTP messages based on the text-based format of HTTP/1.x messages, and apply this understanding to HTTP/2 and beyond.

This guide uses HTTP/1.1 messages for readability, and explains the structure of HTTP messages using the HTTP/1.1 format. We highlight some differences that you might need for describing HTTP/2 in the final section.

**Note:** You can see HTTP messages in a browser's **Network** tab in the developer tools, or if you print HTTP messages to the console using CLI tools such as [curl](https://curl.se/), for example.

### Anatomy of an HTTP message
To understand how HTTP messages work, we'll look at HTTP/1.1 messages and examine the structure. The following illustration shows what messages in HTTP/1.1 look like:

![Requests and responses share a common structure in HTTP](https://mdn.github.io/shared-assets/images/diagrams/http/messages/http-message-anatomy.svg)

Both requests and responses share a similar structure:

1. A _start-line_ is a single line that describes the HTTP version along with the request method or the outcome of the request.
2. An optional set of _HTTP headers_ containing metadata that describes the message. For example, a request for a resource might include the allowed formats of that resource, while the response might include headers to indicate the actual format returned.
3. An empty line indicating the metadata of the message is complete.
4. An optional _body_ containing data associated with the message. This might be POST data to send to the server in a request, or some resource returned to the client in a response. Whether a message contains a body or not is determined by the start-line and HTTP headers.

The start-line and headers of the HTTP message are collectively known as the _head_ of the requests, and the part afterwards that contains its content is known as the _body_.

### HTTP requests
Let's look at the following example HTTP `POST` request that's sent after a user submits a form on a web page:

```HTTP
POST /users HTTP/1.1
Host: example.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 49

name=FirstName+LastName&email=bsmth%40example.com
```

The start-line in HTTP/1.x requests (`POST /users HTTP/1.1` in the example above) is called a "request-line" and is made of three parts:

```HTTP
<method> <request-target> <protocol>
```

[`<method>`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Messages#method)

The [HTTP method](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods) (also known as an _HTTP verb_) is one of a set of defined words that describes the meaning of the request and the desired outcome. For example, `GET` indicates that the client would like to receive a resource in return, and `POST` means that the client is sending data to a server.

[`<request-target>`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Messages#request-target)

The request target is usually an absolute or relative [URL](https://developer.mozilla.org/en-US/docs/Glossary/URL), and is characterized by the context of the request. The format of the request target depends on the HTTP method used and the request context. It is described in more detail in the [Request targets](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Messages#request_targets) section below.

[`<protocol>`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Messages#protocol)

The _HTTP version_, which defines the structure of the remaining message, acting as an indicator of the expected version to use for the response. This is almost always `HTTP/1.1`, as `HTTP/0.9` and `HTTP/1.0` are obsolete. In HTTP/2 and above, the protocol version isn't included in messages since it is understood from the connection setup.

#### Request targets

There are a few ways of describing a request target, but by far the most common is the "origin form". Here's a list of the types of targets and when they are used:

1. In _origin form_, the recipient combines an absolute path with the information in the [`Host`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Host) header. A query string can be appended to the path for additional information (usually in `key=value` format). This is used with `GET`, `POST`, `HEAD`, and `OPTIONS` methods:

```http
GET /en-US/docs/Web/HTTP/Guides/Messages HTTP/1.1
```

2. The _absolute form_ is a complete URL, including the authority, and is used with `GET` when connecting to a proxy:

```http
GET https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Messages HTTP/1.1
```

3. The _authority form_ is the authority and port separated by a colon (`:`). It is only used with the [`CONNECT`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/CONNECT) method when setting up an HTTP tunnel:    

```http
CONNECT developer.mozilla.org:443 HTTP/1.1
```

4. The _asterisk form_ is only used with `OPTIONS` when you want to represent the server as a whole (`*`) as opposed to a named resource:

```http
OPTIONS * HTTP/1.1
```  

#### Request headers

Headers are metadata sent with a request after the start line and before the body. In the [form submission example](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Messages#http_requests) above, they are the following lines of the message:

```http
Host: example.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 49
```

In HTTP/1.x, each header is a **case-insensitive** string followed by a colon (`:`) and a value whose format depends on the header. The whole header, including the value, consists of one single line. This line can be quite long in some cases, such as the [`Cookie`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Cookie) header.

![Example of headers in an HTTP request](https://mdn.github.io/shared-assets/images/diagrams/http/messages/request-headers.svg)

Some headers are exclusively used in requests, while others can be sent in both requests and responses, or might have a more specific categorization:

- [Request headers](https://developer.mozilla.org/en-US/docs/Glossary/Request_header) provide additional context to a request or add extra logic to how it should be treated by a server (e.g., [conditional requests](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Conditional_requests)).
- [Representation headers](https://developer.mozilla.org/en-US/docs/Glossary/Representation_header) are sent in a request if the message has a body, and they describe the original form of the message data and any encoding applied. This allows the recipient to understand how to reconstruct the resource as it was before it was transmitted over the network.

#### Request body

The request body is the part of a request that carries information to the server. Only `PATCH`, `POST`, and `PUT` requests have a body. In the [form submission example](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Messages#http_requests), this part is the body:

httpCopy to Clipboard

```http
name=FirstName+LastName&email=bsmth%40example.com
```

The body in the form submission request contains a relatively small amount of information as `key=value` pairs, but a request body could contain other types of data that the server expects:

jsonCopy to Clipboard

```json
{
  "firstName": "Brian",
  "lastName": "Smith",
  "email": "bsmth@example.com",
  "more": "data"
}
```

or data in multiple parts:

```http
--delimiter123
Content-Disposition: form-data; name="field1"

value1
--delimiter123
Content-Disposition: form-data; name="field2"; filename="example.txt"

Text file contents
--delimiter123--
```

### HTTP responses
Responses are the HTTP messages a server sends back in reply to a request. The response lets the client know what the outcome of the request was. Here's an example HTTP/1.1 response to a `POST` request that created a new user:



```http
HTTP/1.1 201 Created
Content-Type: application/json
Location: http://example.com/users/123

{
  "message": "New user created",
  "user": {
    "id": 123,
    "firstName": "Example",
    "lastName": "Person",
    "email": "bsmth@example.com"
  }
}
```

The start-line (`HTTP/1.1 201 Created` above) is called a "status line" in responses, and has three parts:

httpCopy to Clipboard

```http
<protocol> <status-code> <status-text>
```

[`<protocol>`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Messages#protocol_2)

The _HTTP version_ of the remaining message.

[`<status-code>`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Messages#status-code)

A numeric [status code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status) that indicates whether the request succeeded or failed. Common status codes are [`200`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status/200), [`404`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status/404), or [`302`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status/302).

[`<status-text>`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Messages#status-text)

The status text is a brief, purely informational, textual description of the status code to help a human understand the HTTP message.

#### Response headers
Response headers are the metadata sent with a response. In HTTP/1.x, each header is a **case-insensitive** string followed by a colon (`:`) and a value whose format depends upon which header is used.

![Example of headers in an HTTP response](https://mdn.github.io/shared-assets/images/diagrams/http/messages/response-headers.svg)

Like request headers, there are many different headers that can appear in responses, and they are categorized as:

- [Response headers](https://developer.mozilla.org/en-US/docs/Glossary/Response_header) that give additional context about the message or add extra logic to how the client should make subsequent requests. For example, headers like [`Server`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Server) include information about the server software, while [`Date`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Date) includes when the response was generated. There is also information about the resource being returned, such as its content type ([`Content-Type`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Type)), or how it should be cached ([`Cache-Control`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Cache-Control)).
- [Representation headers](https://developer.mozilla.org/en-US/docs/Glossary/Representation_header) if the message has a body, they describe the form of the message data and any encoding applied. For example, the same resource might be formatted in a particular media type such as XML or JSON, localized to a particular written language or geographical region, and/or compressed or otherwise encoded for transmission. This allows a recipient to understand how to reconstruct the resource as it was before it was transmitted over the network.

#### Response body
A response body is included in most messages when responding to a client. In successful requests, the response body contains the data that the client asked for in a `GET` request. If there are problems with the client's request, it's common for the response body to describe why the request failed, and hint as to whether it's permanent or temporary.

Response bodies may be:

- Single-resource bodies defined by the two headers: [`Content-Type`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Type) and [`Content-Length`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Length), or of unknown length and encoded in chunks with [`Transfer-Encoding`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Transfer-Encoding) set to `chunked`.
- [Multiple-resource bodies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/MIME_types#multipartform-data), consisting of a body that contains multiple parts, each containing a different piece of information. Multipart bodies are typically associated with [HTML Forms](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms), but may also be sent in response to [Range requests](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Range_requests).

Responses with a status code that answers the request without the need to include message content, such as [`201 Created`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status/201) or [`204 No Content`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status/204), do not have a body.

### HTTP/2 messages

HTTP/1.x uses text-based messages that are straightforward to read and construct, but as a result have a few downsides. You can compress message bodies using `gzip` or other compression algorithms, but not headers. Headers are often similar or identical in a client-server interaction, but they are repeated in successive messages on a connection. There are many known methods to compress repetitive text that are very efficient, which leaves a large amount of bandwidth savings unutilized.

HTTP/1.x also has a problem called head-of-line (HOL) blocking, where a client has to wait for a response from the server before sending the next request. HTTP [pipelining](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Connection_management_in_HTTP_1.x#http_pipelining) tried to work around this, but poor support and complexity means it's rarely used and difficult to get right. Several connections need to be opened to send requests concurrently; and warm (established and busy) connections are more efficient than cold ones due to TCP slow start.

In HTTP/1.1 if you want to make two requests in parallel, you have to open two connections:

![Making two HTTP requests to a server in parallel](https://mdn.github.io/shared-assets/images/diagrams/http/messages/http-1-connection.png)

This means that browsers are limited in the number of resources that they can download and render at the same time, which has typically been limited to 6 parallel connections.

HTTP/2 allows you to use a single TCP connection for multiple requests and responses at the same time. This is done by wrapping messages into a binary frame and sending the requests and responses in a numbered **stream** on a connection. Data and header frames are handled separately, which allows headers to be compressed via an algorithm called HPACK. Using the same TCP connection to handle multiple requests at the same time is called _multiplexing_.

![Multiplexing requests and responses in HTTP/2 using a single TCP connection.](https://mdn.github.io/shared-assets/images/diagrams/http/messages/http-2-connection.png)

Requests are not necessarily sequential: stream 9 doesn't have to wait for stream 7 to finish, for instance. The data from multiple streams are usually interleaved on the connection, so stream 9 and 7 can be received by the client at the same time. There's a mechanism for the protocol to set a priority for each stream or resource. Low-priority resources take up less bandwidth than higher-priority resources when they're being sent over different streams, or they could effectively be sent sequentially on the same connection if there are critical resources that should be handled first.

In general, despite all of the improvements and abstractions added over HTTP/1.x, virtually no changes are needed in the APIs used by developers to make use of HTTP/2 over HTTP/1.x. When HTTP/2 is available in both the browser and the server, it is switched on and used automatically.

#### Pseudo-headers

One notable change to messages in HTTP/2 are the use of pseudo-headers. Where HTTP/1.x used the message start-line, HTTP/2 uses special pseudo-header fields beginning with `:`. In requests, there are the following pseudo-headers:

- `:method` - the HTTP method.
- `:scheme` - the scheme portion of the target URI, which is often HTTP(S).
- `:authority` - the authority portion of the target URI.
- `:path` - the path and query parts of the target URI.

In responses, there is only one pseudo-header, and that's the `:status` which provides the code of the response.

We can make a HTTP/2 request using [nghttp](https://github.com/nghttp2/nghttp2) to fetch `example.com`, which will print out the request in a form that's more readable. You can make the request using this command where the `-n` option discards the downloaded data and `-v` is for 'verbose' output, showing reception and transmission of frames:

bashCopy to Clipboard

```http
nghttp -nv https://www.example.com
```

If you look down through the output, you'll see the timing for each frame transmitted and received:

```http
[  0.123] <send|recv> <frame-type> <frame-details>
```

We don't have to go into too much detail on this output, but look out for the `HEADERS` frame in the format `[ 0.123] send HEADERS frame `. In the lines after the header transmission, you will see the following lines:

```http
[  0.447] send HEADERS frame ...
          ...
          :method: GET
          :path: /
          :scheme: https
          :authority: www.example.com
          accept: */*
          accept-encoding: gzip, deflate
          user-agent: nghttp2/1.61.0
```

This should look familiar if you're already comfortable working with HTTP/1.x and the concepts covered in the earlier section of this guide still apply. This is the binary frame with the `GET` request for `example.com`, converted into a readable form by `nghttp`. If you look further down the output of the command, you will see the `:status` pseudo-header in one of the streams received from the server:

```http
[  0.433] recv (stream_id=13) :status: 200
[  0.433] recv (stream_id=13) content-encoding: gzip
[  0.433] recv (stream_id=13) age: 112721
[  0.433] recv (stream_id=13) cache-control: max-age=604800
[  0.433] recv (stream_id=13) content-type: text/html; charset=UTF-8
[  0.433] recv (stream_id=13) date: Fri, 13 Sep 2024 12:56:07 GMT
[  0.433] recv (stream_id=13) etag: "3147526947+gzip"
...
```

And if you remove the timing and stream ID from this message, it should be even more familiar:

```http
:status: 200
content-encoding: gzip
age: 112721
```

Digging further into message frames, stream IDs and how the connection is managed is beyond the scope of this guide, but for the purpose of understanding and debugging HTTP/2 messages, you should be well-equipped using the knowledge and tools in this article.

### Conclusion

This guide provides a general overview of the anatomy of HTTP messages, using the HTTP/1.1 format for illustration. We also explored HTTP/2 message framing, which introduces a layer between the HTTP/1.x syntax and the underlying transport protocol without fundamentally modifying HTTP's semantics. HTTP/2 was introduced to solve the [head-of-line blocking](https://developer.mozilla.org/en-US/docs/Glossary/Head_of_line_blocking) issues present in HTTP/1.x by enabling multiplexing of requests.

One issue that remained in HTTP/2 is that even though head-of-line blocking was fixed in the protocol level, there is still a performance bottleneck due to head-of-line blocking within TCP (at the transport level). HTTP/3 addresses this limitation by using QUIC, a protocol built on UDP, instead of TCP. This change improves performance, reduces connection setup time, and enhances stability on degraded or unreliable networks. HTTP/3 retains the same core HTTP semantics, so features like request methods, status codes, and headers remain consistent across all three major HTTP versions.

If you understand HTTP/1.1's semantics, you already have a solid foundation for grasping HTTP/2 and HTTP/3. The main difference lies in **how** these semantics are implemented at the transport level. By following the examples and concepts in this guide, you should now feel equipped to work with HTTP and understand the meaning of messages, and how applications use HTTP to send and receive data.

## HTTP headers
**HTTP headers** let the client and the server pass additional information with a message in a request or response. In HTTP/1.X, a header is a case-insensitive name followed by a colon, then optional whitespace which will be ignored, and finally by its value (for example: `Allow: POST`). In HTTP/2 and above, headers are displayed in lowercase when viewed in developer tools (`accept: */*`), and prefixed with a colon for a special group of [pseudo-headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Messages#pseudo-headers) (`:status: 200`). You can find more information on the syntax in each protocol version in the [HTTP messages](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Messages) page.

Custom proprietary headers have historically been used with an `X-` prefix, but this convention was deprecated in 2012 because of the inconveniences it caused when nonstandard fields became standard in [RFC 6648](https://datatracker.ietf.org/doc/html/rfc6648); others are listed in the [IANA HTTP Field Name Registry](https://www.iana.org/assignments/http-fields/http-fields.xhtml), whose original content was defined in [RFC 4229](https://datatracker.ietf.org/doc/html/rfc4229). The IANA registry lists headers, including [information about their status](https://github.com/protocol-registries/http-fields?tab=readme-ov-file#choosing-the-right-status).

Headers can be grouped according to their contexts:

[Request headers](https://developer.mozilla.org/en-US/docs/Glossary/Request_header)

Contain more information about the resource to be fetched, or about the client requesting the resource.

[Response headers](https://developer.mozilla.org/en-US/docs/Glossary/Response_header)

Hold additional information about the response, like its location or about the server providing it.

[Representation headers](https://developer.mozilla.org/en-US/docs/Glossary/Representation_header)

Contain information about the body of the resource, like its [MIME type](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/MIME_types), or encoding/compression applied.

[Payload headers](https://developer.mozilla.org/en-US/docs/Glossary/Payload_header)

Contain representation-independent information about payload data, including content length and the encoding used for transport.

Headers can also be grouped according to how [proxies](https://developer.mozilla.org/en-US/docs/Glossary/Proxy_server) handle them:

[End-to-end headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers#end-to-end_headers)

These headers _must_ be transmitted to the final recipient of the message: the server for a request, or the client for a response. Intermediate proxies must retransmit these headers unmodified and caches must store them.

[Hop-by-hop headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers#hop-by-hop_headers)

These headers are meaningful only for a single transport-level connection, and _must not_ be retransmitted by proxies or cached. Note that only hop-by-hop headers may be set using the [`Connection`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Connection) header.

### Authentication

[`WWW-Authenticate`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/WWW-Authenticate)

Defines the authentication method that should be used to access a resource.

[`Authorization`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Authorization)

Contains the credentials to authenticate a user-agent with a server.

[`Proxy-Authenticate`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Proxy-Authenticate)

Defines the authentication method that should be used to access a resource behind a proxy server.

[`Proxy-Authorization`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Proxy-Authorization)

Contains the credentials to authenticate a user agent with a proxy server.

### Caching

[`Age`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Age)

The time, in seconds, that the object has been in a proxy cache.

[`Cache-Control`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Cache-Control)

Directives for caching mechanisms in both requests and responses.

[`Clear-Site-Data`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Clear-Site-Data)

Clears browsing data (e.g., cookies, storage, cache) associated with the requesting website.

[`Expires`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Expires)

The date/time after which the response is considered stale.

[`No-Vary-Search`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/No-Vary-Search) Experimental

Specifies a set of rules that define how a URL's query parameters will affect cache matching. These rules dictate whether the same URL with different URL parameters should be saved as separate browser cache entries.

### Conditionals

[`Last-Modified`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Last-Modified)

The last modification date of the resource, used to compare several versions of the same resource. It is less accurate than [`ETag`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/ETag), but easier to calculate in some environments. Conditional requests using [`If-Modified-Since`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/If-Modified-Since) and [`If-Unmodified-Since`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/If-Unmodified-Since) use this value to change the behavior of the request.

[`ETag`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/ETag)

A unique string identifying the version of the resource. Conditional requests using [`If-Match`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/If-Match) and [`If-None-Match`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/If-None-Match) use this value to change the behavior of the request.

[`If-Match`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/If-Match)

Makes the request conditional, and applies the method only if the stored resource matches one of the given ETags.

[`If-None-Match`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/If-None-Match)

Makes the request conditional, and applies the method only if the stored resource _doesn't_ match any of the given ETags. This is used to update caches (for safe requests), or to prevent uploading a new resource when one already exists.

[`If-Modified-Since`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/If-Modified-Since)

Makes the request conditional, and expects the resource to be transmitted only if it has been modified after the given date. This is used to transmit data only when the cache is out of date.

[`If-Unmodified-Since`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/If-Unmodified-Since)

Makes the request conditional, and expects the resource to be transmitted only if it has not been modified after the given date. This ensures the coherence of a new fragment of a specific range with previous ones, or to implement an optimistic concurrency control system when modifying existing documents.

[`Vary`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Vary)

Determines how to match request headers to decide whether a cached response can be used rather than requesting a fresh one from the origin server.

### Connection Management

[`Connection`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Connection)

Controls whether the network connection stays open after the current transaction finishes.

[`Keep-Alive`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Keep-Alive)

Controls how long a persistent connection should stay open.

### Content negotiation

For more details, refer to the [Content negotiation article](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Content_negotiation).

[`Accept`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Accept)

Informs the server about the [types](https://developer.mozilla.org/en-US/docs/Glossary/MIME_type) of data that can be sent back.

[`Accept-Encoding`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Accept-Encoding)

The encoding algorithm, usually a [compression algorithm](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Compression), that can be used on the resource sent back.

[`Accept-Language`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Accept-Language)

Informs the server about the human language the server is expected to send back. This is a hint and is not necessarily under the full control of the user: the server should always pay attention not to override an explicit user choice (like selecting a language from a dropdown).

[`Accept-Patch`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Accept-Patch)

A _request content negotiation_ response header that advertises which [media type](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/MIME_types) the server is able to understand in a [`PATCH`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/PATCH) request.

[`Accept-Post`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Accept-Post)

A _request content negotiation_ response header that advertises which [media type](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/MIME_types) the server is able to understand in a [`POST`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/POST) request.

### Controls

[`Expect`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Expect)

Indicates expectations that need to be fulfilled by the server to properly handle the request.

[`Max-Forwards`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Max-Forwards)

When using [`TRACE`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/TRACE), indicates the maximum number of hops the request can do before being reflected to the sender.

### Cookies

[`Cookie`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Cookie)

Contains stored [HTTP cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Cookies) previously sent by the server with the [`Set-Cookie`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie) header.

[`Set-Cookie`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie)

Send cookies from the server to the user-agent.

### CORS

For more information, refer to the [CORS documentation](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/CORS).

[`Access-Control-Allow-Credentials`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Access-Control-Allow-Credentials)

Indicates whether the response to the request can be exposed when the credentials flag is true.

[`Access-Control-Allow-Headers`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Access-Control-Allow-Headers)

Used in response to a [preflight request](https://developer.mozilla.org/en-US/docs/Glossary/Preflight_request) to indicate which HTTP headers can be used when making the actual request.

[`Access-Control-Allow-Methods`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Access-Control-Allow-Methods)

Specifies the methods allowed when accessing the resource in response to a preflight request.

[`Access-Control-Allow-Origin`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Access-Control-Allow-Origin)

Indicates whether the response can be shared.

[`Access-Control-Expose-Headers`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Access-Control-Expose-Headers)

Indicates which headers can be exposed as part of the response by listing their names.

[`Access-Control-Max-Age`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Access-Control-Max-Age)

Indicates how long the results of a preflight request can be cached.

[`Access-Control-Request-Headers`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Access-Control-Request-Headers)

Used when issuing a preflight request to let the server know which HTTP headers will be used when the actual request is made.

[`Access-Control-Request-Method`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Access-Control-Request-Method)

Used when issuing a preflight request to let the server know which [HTTP method](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods) will be used when the actual request is made.

[`Origin`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Origin)

Indicates where a fetch originates from.

[`Timing-Allow-Origin`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Timing-Allow-Origin)

Specifies origins that are allowed to see values of attributes retrieved via features of the [Resource Timing API](https://developer.mozilla.org/en-US/docs/Web/API/Performance_API/Resource_timing), which would otherwise be reported as zero due to cross-origin restrictions.

### Downloads

[`Content-Disposition`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Disposition)

Indicates if the resource transmitted should be displayed inline (default behavior without the header), or if it should be handled like a download and the browser should present a "Save As" dialog.

### Integrity digests

[`Content-Digest`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Digest) Experimental

Provides a [digest](https://developer.mozilla.org/en-US/docs/Glossary/Hash_function) of the stream of octets framed in an HTTP message (the message content) dependent on [`Content-Encoding`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Encoding) and [`Content-Range`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Range).

[`Repr-Digest`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Repr-Digest) Experimental

Provides a [digest](https://developer.mozilla.org/en-US/docs/Glossary/Hash_function) of the selected representation of the target resource before transmission. Unlike the [`Content-Digest`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Digest), the digest does not consider [`Content-Encoding`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Encoding) or [`Content-Range`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Range).

[`Want-Content-Digest`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Want-Content-Digest) Experimental

States the wish for a [`Content-Digest`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Digest) header. It is the `Content-` analogue of [`Want-Repr-Digest`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Want-Repr-Digest).

[`Want-Repr-Digest`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Want-Repr-Digest) Experimental

States the wish for a [`Repr-Digest`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Repr-Digest) header. It is the `Repr-` analogue of [`Want-Content-Digest`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Want-Content-Digest).

### Integrity policy

[`Integrity-Policy`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Integrity-Policy)

Ensures that all resources the user agent loads (of a certain type) have [Subresource Integrity](https://developer.mozilla.org/en-US/docs/Web/Security/Subresource_Integrity) guarantees.

[`Integrity-Policy-Report-Only`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Integrity-Policy-Report-Only)

Reports on resources that the user agent loads that would violate [Subresource Integrity](https://developer.mozilla.org/en-US/docs/Web/Security/Subresource_Integrity) guarantees if the integrity policy were enforced (using the `Integrity-Policy` header).

### Message body information

[`Content-Length`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Length)

The size of the resource, in decimal number of bytes.

[`Content-Type`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Type)

Indicates the media type of the resource.

[`Content-Encoding`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Encoding)

Used to specify the compression algorithm.

[`Content-Language`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Language)

Describes the human language(s) intended for the audience, so that it allows a user to differentiate according to the users' own preferred language.

[`Content-Location`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Location)

Indicates an alternate location for the returned data.

### Preferences

Preferences can be sent by clients in requests to indicate optional behaviors for requests and responses. The server response may indicate if a preference is applied, in cases where it would otherwise be ambiguous for the client. Browsers have no native handling for sending preferences via these headers; they are used in custom, implementation-specific clients.

[`Prefer`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Prefer)

Indicates preferences for specific server behaviors during request processing. For example, it can request minimal response content (`return=minimal`) or asynchronous processing (`respond-async`). The server processes the request normally if the header is unsupported.

[`Preference-Applied`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Preference-Applied)

Informs the client which preferences specified in the `Prefer` header were applied by the server. It is a response-only header providing transparency about preference handling.

### Proxies

[`Forwarded`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Forwarded)

Contains information from the client-facing side of proxy servers that is altered or lost when a proxy is involved in the path of the request.

[`Via`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Via)

Added by proxies, both forward and reverse proxies, and can appear in the request headers and the response headers.

### Range requests

HTTP [range requests](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Range_requests) allow the client to request a portion of a resource from the server. Range requests are useful for applications like media players that support random access, data tools that know they need only part of a large file, and download managers that let the user pause and resume a download.

[`Accept-Ranges`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Accept-Ranges)

Indicates if the server supports range requests, and if so in which unit the range can be expressed.

[`Range`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Range)

Indicates the part of a document that the server should return.

[`If-Range`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/If-Range)

Creates a conditional range request that is only fulfilled if the given etag or date matches the remote resource. Used to prevent downloading two ranges from incompatible version of the resource.

[`Content-Range`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Range)

Indicates where in a full body message a partial message belongs.

### Redirects

[`Location`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Location)

Indicates the URL to redirect a page to.

[`Refresh`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Refresh)

Directs the browser to reload the page or redirect to another. Takes the same value as the `meta` element with [`http-equiv="refresh"`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/meta#http-equiv).

### Request context

[`From`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/From)

Contains an Internet email address for a human user who controls the requesting user agent.

[`Host`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Host)

Specifies the domain name of the server (for virtual hosting), and (optionally) the TCP port number on which the server is listening.

[`Referer`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Referer)

The address of the previous web page from which a link to the currently requested page was followed.

[`Referrer-Policy`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Referrer-Policy)

Governs which referrer information sent in the [`Referer`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Referer) header should be included with requests made.

[`User-Agent`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/User-Agent)

Contains a characteristic string that allows the network protocol peers to identify the application type, operating system, software vendor or software version of the requesting software user agent.

### Response context

[`Allow`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Allow)

Lists the set of HTTP request methods supported by a resource.

[`Server`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Server)

Contains information about the software used by the origin server to handle the request.

### Security

[`Cross-Origin-Embedder-Policy`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Cross-Origin-Embedder-Policy) (COEP)

Allows a server to declare an embedder policy for a given document.

[`Cross-Origin-Opener-Policy`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Cross-Origin-Opener-Policy) (COOP)

Prevents other domains from opening/controlling a window.

[`Cross-Origin-Resource-Policy`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Cross-Origin-Resource-Policy) (CORP)

Prevents other domains from reading the response of the resources to which this header is applied. See also [CORP explainer article](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Cross-Origin_Resource_Policy).

[`Content-Security-Policy`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy) ([CSP](https://developer.mozilla.org/en-US/docs/Glossary/CSP))

Controls resources the user agent is allowed to load for a given page.

[`Content-Security-Policy-Report-Only`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy-Report-Only)

Allows web developers to experiment with policies by monitoring, but not enforcing, their effects. These violation reports consist of [JSON](https://developer.mozilla.org/en-US/docs/Glossary/JSON) documents sent via an HTTP `POST` request to the specified URI.

[`Expect-CT`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Expect-CT) Deprecated

Lets sites opt in to reporting and enforcement of [Certificate Transparency](https://developer.mozilla.org/en-US/docs/Web/Security/Certificate_Transparency) to detect use of misissued certificates for that site.

[`Permissions-Policy`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy)

Provides a mechanism to allow and deny the use of browser features in a website's own frame, and in [`<iframe>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/iframe)s that it embeds.

[`Reporting-Endpoints`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Reporting-Endpoints) Experimental

Response header that allows website owners to specify one or more endpoints used to receive errors such as CSP violation reports, [`Cross-Origin-Opener-Policy`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Cross-Origin-Opener-Policy) reports, or other generic violations.

[`Strict-Transport-Security`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Strict-Transport-Security) ([HSTS](https://developer.mozilla.org/en-US/docs/Glossary/HSTS))

Force communication using HTTPS instead of HTTP.

[`Upgrade-Insecure-Requests`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Upgrade-Insecure-Requests)

Sends a signal to the server expressing the client's preference for an encrypted and authenticated response, and that it can successfully handle the [`upgrade-insecure-requests`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/upgrade-insecure-requests) directive.

[`X-Content-Type-Options`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/X-Content-Type-Options)

Disables MIME sniffing and forces browser to use the type given in [`Content-Type`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Type).

[`X-Frame-Options`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/X-Frame-Options) (XFO)

Indicates whether a browser should be allowed to render a page in a [`<frame>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/frame), [`<iframe>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/iframe), [`<embed>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/embed) or [`<object>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/object).

[`X-Permitted-Cross-Domain-Policies`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/X-Permitted-Cross-Domain-Policies)

A cross-domain policy file may grant clients, such as Adobe Acrobat or Apache Flex (among others), permission to handle data across domains that would otherwise be restricted due to the [Same-Origin Policy](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy). The `X-Permitted-Cross-Domain-Policies` header overrides such policy files so that clients still block unwanted requests.

[`X-Powered-By`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/X-Powered-By)

May be set by hosting environments or other frameworks and contains information about them while not providing any usefulness to the application or its visitors. Unset this header to avoid exposing potential vulnerabilities.

[`X-XSS-Protection`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/X-XSS-Protection)

Enables cross-site scripting filtering.

#### Fetch metadata request headers

[Fetch metadata request headers](https://developer.mozilla.org/en-US/docs/Glossary/Fetch_metadata_request_header) provide information about the context from which the request originated. A server can use them to make decisions about whether a request should be allowed, based on where the request came from and how the resource will be used.

[`Sec-Fetch-Site`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-Fetch-Site)

Indicates the relationship between a request initiator's origin and its target's origin. It is a Structured Header whose value is a token with possible values `cross-site`, `same-origin`, `same-site`, and `none`.

[`Sec-Fetch-Mode`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-Fetch-Mode)

Indicates the request's mode to a server. It is a Structured Header whose value is a token with possible values `cors`, `navigate`, `no-cors`, `same-origin`, and `websocket`.

[`Sec-Fetch-User`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-Fetch-User)

Indicates whether or not a navigation request was triggered by user activation. It is a Structured Header whose value is a boolean so possible values are `?0` for false and `?1` for true.

[`Sec-Fetch-Dest`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-Fetch-Dest)

Indicates the request's destination. It is a Structured Header whose value is a token with possible values `audio`, `audioworklet`, `document`, `embed`, `empty`, `font`, `image`, `manifest`, `object`, `paintworklet`, `report`, `script`, `serviceworker`, `sharedworker`, `style`, `track`, `video`, `worker`, and `xslt`.

The following request headers are not _strictly_ "fetch metadata request headers", but similarly provide information about the context of how a resource will be used. A server might use them to modify its caching behavior, or the information that is returned:

[`Sec-Purpose`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-Purpose)

Indicates the purpose of the request, when the purpose is something other than immediate use by the user-agent. The header currently has one possible value, `prefetch`, which indicates that the resource is being fetched preemptively for a possible future navigation.

[`Service-Worker-Navigation-Preload`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Service-Worker-Navigation-Preload)

A request header sent in preemptive request to [`fetch()`](https://developer.mozilla.org/en-US/docs/Web/API/Window/fetch "fetch()") a resource during service worker boot. The value, which is set with [`NavigationPreloadManager.setHeaderValue()`](https://developer.mozilla.org/en-US/docs/Web/API/NavigationPreloadManager/setHeaderValue), can be used to inform a server that a different resource should be returned than in a normal `fetch()` operation.

### Server-sent events

[`Reporting-Endpoints`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Reporting-Endpoints)

Response header used to specify server endpoints where the browser should send warning and error reports when using the [Reporting API](https://developer.mozilla.org/en-US/docs/Web/API/Reporting_API).

[`Report-To`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Report-To) Deprecated Non-standard

Response header used to specify server endpoints where the browser should send warning and error reports when using the [Reporting API](https://developer.mozilla.org/en-US/docs/Web/API/Reporting_API).

### Transfer coding

[`Transfer-Encoding`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Transfer-Encoding)

Specifies the form of encoding used to safely transfer the resource to the user.

[`TE`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/TE)

Specifies the transfer encodings the user agent is willing to accept.

[`Trailer`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Trailer)

Allows the sender to include additional fields at the end of chunked message.

### WebSockets

Headers used by the [WebSockets API](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API) in the [WebSocket handshake](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API/Writing_WebSocket_servers#the_websocket_handshake):

[`Sec-WebSocket-Accept`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-WebSocket-Accept)

Response header that indicates that the server is willing to upgrade to a WebSocket connection.

[`Sec-WebSocket-Extensions`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-WebSocket-Extensions)

In requests, this header indicates the WebSocket extensions supported by the client in preferred order. In responses, it indicates the extension selected by the server from the client's preferences.

[`Sec-WebSocket-Key`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-WebSocket-Key)

Request header containing a key that verifies that the client explicitly intends to open a `WebSocket`.

[`Sec-WebSocket-Protocol`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-WebSocket-Protocol)

In requests, this header indicates the sub-protocols supported by the client in preferred order. In responses, it indicates the sub-protocol selected by the server from the client's preferences.

[`Sec-WebSocket-Version`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-WebSocket-Version)

In requests, this header indicates the version of the WebSocket protocol used by the client. In responses, it is sent only if the requested protocol version is not supported by the server, and lists the versions that the server supports.

### Other

[`Alt-Svc`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Alt-Svc)

Used to list alternate ways to reach this service.

[`Alt-Used`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Alt-Used)

Used to identify the alternative service in use.

[`Date`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Date)

Contains the date and time at which the message was originated.

[`Link`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Link)

This entity-header field provides a means for serializing one or more links in HTTP headers. It is semantically equivalent to the HTML [`<link>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/link) element.

[`Retry-After`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Retry-After)

Indicates how long the user agent should wait before making a follow-up request.

[`Server-Timing`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Server-Timing)

Communicates one or more metrics and descriptions for the given request-response cycle.

[`Service-Worker`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Service-Worker)

Included in fetches for a service worker's script resource. This header helps administrators log service worker script requests for monitoring purposes.

[`Service-Worker-Allowed`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Service-Worker-Allowed)

Used to remove the [path restriction](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers#why_is_my_service_worker_failing_to_register) by including this header [in the response of the Service Worker script](https://w3c.github.io/ServiceWorker/#service-worker-script-response).

[`SourceMap`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/SourceMap)

Links to a [source map](https://developer.mozilla.org/en-US/docs/Glossary/Source_map) so that debuggers can step through original source code instead of generated or transformed code.

[`Upgrade`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Upgrade)

This HTTP/1.1 (only) header can be used to upgrade an already established client/server connection to a different protocol (over the same transport protocol). For example, it can be used by a client to upgrade a connection from HTTP 1.1 to HTTP 2.0, or an HTTP or HTTPS connection into a WebSocket.

[`Priority`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Priority)

Provides a hint from about the priority of a particular resource request on a particular connection. The value can be sent in a request to indicate the client priority, or in a response if the server chooses to reprioritize the request.

#### Client hints
HTTP [Client hints](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Client_hints) are a set of request headers that provide useful information about the client such as device type and network conditions, and allow servers to optimize what is served for those conditions.

Servers proactively requests the client hint headers they are interested in from the client using [`Accept-CH`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Accept-CH). The client may then choose to include the requested headers in subsequent requests.

[`Accept-CH`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Accept-CH)

Servers can advertise support for Client Hints using the `Accept-CH` header field or an equivalent HTML `<meta>` element with [`http-equiv`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/meta#http-equiv) attribute.

[`Critical-CH`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Critical-CH) Experimental

Servers use `Critical-CH` along with [`Accept-CH`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Accept-CH) to specify that accepted client hints are also [critical client hints](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Client_hints#critical_client_hints).

The different categories of client hints are listed below.

##### User agent client hints

The [UA client hints](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Client_hints#user_agent_client_hints) are request headers that provide information about the user agent, the platform/architecture it is running on, and user preferences set on the user agent or platform:

[`Sec-CH-UA`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-CH-UA) Experimental

User agent's branding and version.

[`Sec-CH-UA-Arch`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-CH-UA-Arch) Experimental

User agent's underlying platform architecture.

[`Sec-CH-UA-Bitness`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-CH-UA-Bitness) Experimental

User agent's underlying CPU architecture bitness (for example "64" bit).

[`Sec-CH-UA-Form-Factors`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-CH-UA-Form-Factors) Experimental

User agent's form-factors, describing how the user interacts with the user-agent.

[`Sec-CH-UA-Full-Version`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-CH-UA-Full-Version) Deprecated

User agent's full version string.

[`Sec-CH-UA-Full-Version-List`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-CH-UA-Full-Version-List) Experimental

Full version for each brand in the user agent's brand list.

[`Sec-CH-UA-Mobile`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-CH-UA-Mobile) Experimental

User agent is running on a mobile device or, more generally, prefers a "mobile" user experience.

[`Sec-CH-UA-Model`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-CH-UA-Model) Experimental

User agent's device model.

[`Sec-CH-UA-Platform`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-CH-UA-Platform) Experimental

User agent's underlying operation system/platform.

[`Sec-CH-UA-Platform-Version`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-CH-UA-Platform-Version) Experimental

User agent's underlying operation system version.

[`Sec-CH-UA-WoW64`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-CH-UA-WoW64) Experimental

Whether or not the user agent binary is running in 32-bit mode on 64-bit Windows.

[`Sec-CH-Prefers-Color-Scheme`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-CH-Prefers-Color-Scheme) Experimental

User's preference of dark or light color scheme.

[`Sec-CH-Prefers-Reduced-Motion`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-CH-Prefers-Reduced-Motion) Experimental

User's preference to see fewer animations and content layout shifts.

[`Sec-CH-Prefers-Reduced-Transparency`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-CH-Prefers-Reduced-Transparency) Experimental

Request header indicates the user agent's preference for reduced transparency.

**Note:** User-agent client hints are not available inside [fenced frames](https://developer.mozilla.org/en-US/docs/Web/API/Fenced_frame_API) because they rely on [permissions policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Permissions_Policy) delegation, which could be used to leak data.

##### Device client hints

[`Content-DPR`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-DPR) Deprecated Non-standard

Response header used to confirm the image device to pixel ratio (DPR) in requests where the screen [`DPR`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/DPR) client hint was used to select an image resource.

[`Device-Memory`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Device-Memory)

Approximate amount of available client RAM memory. This is part of the [Device Memory API](https://developer.mozilla.org/en-US/docs/Web/API/Device_Memory_API).

[`DPR`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/DPR) Deprecated Non-standard

Request header that provides the client device pixel ratio (the number of physical [device pixels](https://developer.mozilla.org/en-US/docs/Glossary/Device_pixel) for each [CSS pixel](https://developer.mozilla.org/en-US/docs/Glossary/CSS_pixel)).

[`Viewport-Width`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Viewport-Width) Deprecated Non-standard

Request header provides the client's layout viewport width in [CSS pixels](https://developer.mozilla.org/en-US/docs/Glossary/CSS_pixel).

[`Width`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Width) Deprecated Non-standard

Request header indicates the desired resource width in physical pixels (the intrinsic size of an image).

##### Network client hints

Network client hints allow a server to choose what information is sent based on the user choice and network bandwidth and latency.

[`Downlink`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Downlink) Experimental

Approximate bandwidth of the client's connection to the server, in Mbps. This is part of the [Network Information API](https://developer.mozilla.org/en-US/docs/Web/API/Network_Information_API).

[`ECT`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/ECT) Experimental

The [effective connection type](https://developer.mozilla.org/en-US/docs/Glossary/Effective_connection_type) ("network profile") that best matches the connection's latency and bandwidth. This is part of the [Network Information API](https://developer.mozilla.org/en-US/docs/Web/API/Network_Information_API).

[`RTT`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/RTT) Experimental

Application layer round trip time (RTT) in milliseconds, which includes the server processing time. This is part of the [Network Information API](https://developer.mozilla.org/en-US/docs/Web/API/Network_Information_API).

[`Save-Data`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Save-Data) Experimental

A string `on` that indicates the user agent's preference for reduced data usage.

#### Compression Dictionary Transport

[Compression Dictionary Transport](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Compression_dictionary_transport) is a way of using a shared compression dictionary to reduce the transport size of HTTP responses rather than using the standard static dictionary in [Brotli compression](https://developer.mozilla.org/en-US/docs/Glossary/Brotli_compression) or [Zstandard compression](https://developer.mozilla.org/en-US/docs/Glossary/Zstandard_compression).

[`Available-Dictionary`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Available-Dictionary) Experimental

A browser can use this request header to indicate the best dictionary it has available for the server to use for compression.

[`Dictionary-ID`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Dictionary-ID) Experimental

Used when a browser already has a dictionary available for a resource and the server provided an `id` for the dictionary in the `Use-As-Dictionary` header. Requests for resources that can use the dictionary have an `Available-Dictionary` header and the server-provided dictionary `id` in the `Dictionary-ID` header.

[`Use-As-Dictionary`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Use-As-Dictionary) Experimental

Lists the matching criteria that the dictionary can be used for in future requests.

#### Privacy

[`DNT`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/DNT) Deprecated Non-standard

Request header that indicates the user's tracking preference (Do Not Track). Deprecated in favor of Global Privacy Control (GPC), which is communicated to servers using the [`Sec-GPC`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-GPC) header, and accessible to clients via [`navigator.globalPrivacyControl`](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/globalPrivacyControl).

[`Tk`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Tk) Deprecated Non-standard

Response header that indicates the tracking status that applied to the corresponding request. Used in conjunction with DNT.

[`Sec-GPC`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-GPC) Non-standard Experimental

Indicates whether the user consents to a website or service selling or sharing their personal information with third parties.

#### Security

[`Origin-Agent-Cluster`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Origin-Agent-Cluster) Experimental

Response header used to indicate that the associated [`Document`](https://developer.mozilla.org/en-US/docs/Web/API/Document) should be placed in an _origin-keyed [agent cluster](https://tc39.es/ecma262/#sec-agent-clusters)_. This isolation allows user agents to allocate implementation-specific resources for agent clusters, such as processes or threads, more efficiently.

#### Server-sent events

[`NEL`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/NEL) Experimental

Defines a mechanism that enables developers to declare a network error reporting policy.

#### Topics API

The Topics API provides a mechanism for developers to implement use cases such as interest-based advertising (IBA). See the [Topics API](https://developer.mozilla.org/en-US/docs/Web/API/Topics_API) documentation for more information.

[`Observe-Browsing-Topics`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Observe-Browsing-Topics) Experimental Non-standard

Response header used to mark topics of interest inferred from a calling site's URL as observed in the response to a request generated by a [feature that enables the Topics API](https://developer.mozilla.org/en-US/docs/Web/API/Topics_API/Using#what_api_features_enable_the_topics_api).

[`Sec-Browsing-Topics`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-Browsing-Topics) Experimental Non-standard

Request header that sends the selected topics for the current user along with the associated request, which are used by an ad tech platform to choose a personalized ad to display.

#### Other
`Accept-Signature` Experimental

A client can send the [`Accept-Signature`](https://wicg.github.io/webpackage/draft-yasskin-http-origin-signed-responses.html#name-the-accept-signature-header) header field to indicate intention to take advantage of any available signatures and to indicate what kinds of signatures it supports.

[`Early-Data`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Early-Data) Experimental

Indicates that the request has been conveyed in TLS early data.

[`Set-Login`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Set-Login) Experimental

Response header sent by a federated identity provider (IdP) to set its login status, meaning whether any users are logged into the IdP on the current browser or not. This is stored by the browser and used by the [FedCM API](https://developer.mozilla.org/en-US/docs/Web/API/FedCM_API).

`Signature` Experimental

The [`Signature`](https://wicg.github.io/webpackage/draft-yasskin-http-origin-signed-responses.html#name-the-signature-header) header field conveys a list of signatures for an exchange, each one accompanied by information about how to determine the authority of and refresh that signature.

`Signed-Headers` Experimental

The [`Signed-Headers`](https://wicg.github.io/webpackage/draft-yasskin-http-origin-signed-responses.html#name-the-signed-headers-header) header field identifies an ordered list of response header fields to include in a signature.

[`Speculation-Rules`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Speculation-Rules) Experimental

Provides a list of URLs pointing to text resources containing [speculation rule](https://developer.mozilla.org/en-US/docs/Web/API/Speculation_Rules_API) JSON definitions. When the response is an HTML document, these rules will be added to the document's speculation rule set.

[`Sec-Speculation-Tags`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Sec-Speculation-Tags) Experimental

Contains one or more tag values from the speculation rules that resulted in the speculation so a server can identify which rule(s) caused a speculation and potentially block them.

[`Supports-Loading-Mode`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Supports-Loading-Mode) Experimental

Set by a navigation target to opt-in to using various higher-risk loading modes. For example, cross-origin, same-site [prerendering](https://developer.mozilla.org/en-US/docs/Web/API/Speculation_Rules_API#using_prerendering) requires a `Supports-Loading-Mode` value of `credentialed-prerender`.

### Non-standard headers

[`X-Forwarded-For`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/X-Forwarded-For) Non-standard

Identifies the originating IP addresses of a client connecting to a web server through an HTTP proxy or a load balancer.

[`X-Forwarded-Host`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/X-Forwarded-Host) Non-standard

Identifies the original host requested that a client used to connect to your proxy or load balancer.

[`X-Forwarded-Proto`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/X-Forwarded-Proto) Non-standard

Identifies the protocol (HTTP or HTTPS) that a client used to connect to your proxy or load balancer.

[`X-DNS-Prefetch-Control`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/X-DNS-Prefetch-Control) Non-standard

Controls DNS prefetching, a feature by which browsers proactively perform domain name resolution on both links that the user may choose to follow as well as URLs for items referenced by the document, including images, CSS, JavaScript, and so forth.

[`X-Robots-Tag`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/X-Robots-Tag) Non-standard

The [`X-Robots-Tag`](https://developers.google.com/search/docs/crawling-indexing/robots-meta-tag) HTTP header is used to indicate how a web page is to be indexed within public search engine results. The header is equivalent to [`<meta name="robots">`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/meta/name/robots) elements.

## Units Of Information
A **unit of information** is any [unit of measure](https://en.wikipedia.org/wiki/Unit_of_measure "Unit of measure") of [digital data](https://en.wikipedia.org/wiki/Digital_data "Digital data") size. In digital [computing](https://en.wikipedia.org/wiki/Computing "Computing"), a unit of information is used to describe the capacity of a digital [data storage](https://en.wikipedia.org/wiki/Digital_data_storage "Digital data storage") device. In [telecommunications](https://en.wikipedia.org/wiki/Telecommunication "Telecommunication"), a unit of information is used to describe the throughput of a [communication channel](https://en.wikipedia.org/wiki/Communication_channel "Communication channel"). In [information theory](https://en.wikipedia.org/wiki/Information_theory "Information theory"), a unit of information is used to measure [information](https://en.wikipedia.org/wiki/Information "Information") contained in messages and the [entropy](https://en.wikipedia.org/wiki/Entropy_\(information_theory\) "Entropy (information theory)") of random variables.

Due to the need to work with data sizes that range from very small to very large, units of information cover a wide range of data sizes. Units are defined as multiples of a smaller unit except for the smallest unit which is based on convention and hardware design. Multiplier prefixes are used to describe relatively large sizes.

For [binary](https://en.wikipedia.org/wiki/Binary_number "Binary number") [hardware](https://en.wikipedia.org/wiki/Computer_hardware "Computer hardware"), by far the most common hardware today, the smallest unit is the [bit](https://en.wikipedia.org/wiki/Bit "Bit"), a portmanteau of binary digit, which represents a value that is one of two possible values; typically shown as 0 and 1. The [nibble](https://en.wikipedia.org/wiki/Nibble "Nibble"), 4 bits, represents the value of a single [hexadecimal](https://en.wikipedia.org/wiki/Hexadecimal "Hexadecimal") digit. The [byte](https://en.wikipedia.org/wiki/Byte "Byte"), 8 bits, 2 nibbles, is possibly the most commonly known and used base unit to describe data size. The [word](https://en.wikipedia.org/wiki/Word_\(computer_architecture\) "Word (computer architecture)") is a size that varies by and has a special importance for a particular hardware context. On modern hardware, a word is typically 2, 4 or 8 bytes, but the size varies dramatically on older hardware. Larger sizes can be expressed as multiples of a base unit via [SI](https://en.wikipedia.org/wiki/SI "SI") [metric prefixes](https://en.wikipedia.org/wiki/Metric_prefixes "Metric prefixes") (powers of ten) or the newer and generally more accurate [IEC](https://en.wikipedia.org/wiki/IEC "IEC") [binary prefixes](https://en.wikipedia.org/wiki/Binary_prefixes "Binary prefixes") (powers of two).

### Information theory

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5e/Units_of_information.svg/384px-Units_of_information.svg.png)](https://en.wikipedia.org/wiki/File:Units_of_information.svg)

Comparison of units of information: [bit](https://en.wikipedia.org/wiki/Bit "Bit"), [trit](https://en.wikipedia.org/wiki/Ternary_numeral_system "Ternary numeral system"), [nat](https://en.wikipedia.org/wiki/Nat_\(unit\) "Nat (unit)"), [ban](https://en.wikipedia.org/wiki/Ban_\(unit\) "Ban (unit)"). Quantity of information is the height of bars. Dark green level is the "nat" unit.

In 1928, [Ralph Hartley](https://en.wikipedia.org/wiki/Ralph_Hartley "Ralph Hartley") observed a fundamental storage principle, which was further formalized by [Claude Shannon](https://en.wikipedia.org/wiki/Claude_Shannon "Claude Shannon") in 1945: the information that can be stored in a system is proportional to the [logarithm](https://en.wikipedia.org/wiki/Logarithm "Logarithm") of _N_ possible states of that system, denoted log_b_ _N_. Changing the base of the logarithm from _b_ to a different number _c_ has the effect of multiplying the value of the logarithm by a fixed constant, namely log_c_ _N_ = (log_c_ _b_) log_b_ _N_. Therefore, the choice of the base _b_ determines the unit used to measure information. In particular, if _b_ is a [positive](https://en.wikipedia.org/wiki/Positive_and_negative_numbers "Positive and negative numbers") integer, then the unit is the amount of information that can be stored in a system with _b_ possible states.

When _b_ is 2, the unit is the [shannon](https://en.wikipedia.org/wiki/Shannon_\(unit\) "Shannon (unit)"), equal to the [information content](https://en.wikipedia.org/wiki/Information_content "Information content") of one "bit". A system with 8 possible states, for example, can store up to log2 8 = 3 bits of information. Other units that have been named include:

Base _b_ = 3

the unit is called "[trit](https://en.wikipedia.org/wiki/Ternary_numeral_system "Ternary numeral system")", and is equal to log2 3 (≈ 1.585) bits.
Base _b_ = 10

the unit is called _[decimal](https://en.wikipedia.org/wiki/Decimal "Decimal") [digit](https://en.wikipedia.org/wiki/Numerical_digit "Numerical digit")_, _[hartley](https://en.wikipedia.org/wiki/Hartley_\(unit\) "Hartley (unit)")_, _ban_, _decit_, or _dit_, and is equal to log2 10 (≈ 3.322) bits.

Base _b_ = _e_, the [base of natural logarithms](https://en.wikipedia.org/wiki/Base_of_natural_logarithm "Base of natural logarithm")

the unit is called a _[nat](https://en.wikipedia.org/wiki/Nat_\(unit\) "Nat (unit)")_, _nit_, or _nepit_ (from [Neperian](https://en.wikipedia.org/wiki/John_Napier "John Napier")), and is worth log2 _e_ (≈ 1.443) bits.

The trit, ban, and nat are rarely used to measure storage capacity; but the nat, in particular, is often used in information theory, because natural logarithms are mathematically more convenient than logarithms in other bases.

### Units derived from bit

Several conventional names are used for collections or groups of bits.

#### Byte

Historically, a [byte](https://en.wikipedia.org/wiki/Byte "Byte") was the number of bits used to encode a [character](https://en.wikipedia.org/wiki/Character_\(computing\) "Character (computing)") of text in the computer, which depended on computer hardware architecture, but today it almost always means eight bits – that is, an [octet](https://en.wikipedia.org/wiki/Octet_\(computing\) "Octet (computing)"). An 8-bit byte can represent 256 (28) distinct values, such as non-negative integers from 0 to 255, or [signed](https://en.wikipedia.org/wiki/Two%27s_complement "Two's complement") integers from −128 to 127. The [IEEE 1541-2002](https://en.wikipedia.org/wiki/IEEE_1541-2002 "IEEE 1541-2002") standard specifies "B" (upper case) as the symbol for byte ([IEC 80000-13](https://en.wikipedia.org/wiki/IEC_80000-13 "IEC 80000-13") uses "o" for octet in French, but also allows "B" in English). Bytes, or multiples thereof, are almost always used to specify the sizes of computer files and the capacity of storage units. Most modern computers and peripheral devices are designed to manipulate data in whole bytes or groups of bytes, rather than individual bits.

#### Nibble

A group of four bits, or half a byte, is sometimes called a [nibble](https://en.wikipedia.org/wiki/Nibble "Nibble"), nybble or nyble. This unit is most often used in the context of [hexadecimal](https://en.wikipedia.org/wiki/Hexadecimal "Hexadecimal") number representations, since a nibble has the same number of possible values as one hexadecimal digit has.

#### Word, block, and page

Computers usually manipulate bits in groups of a fixed size, conventionally called _[words](https://en.wikipedia.org/wiki/Word_\(computer_architecture\) "Word (computer architecture)")_. The number of bits in a word is usually defined by the size of the [registers](https://en.wikipedia.org/wiki/Register_\(computing\) "Register (computing)") in the computer's [CPU](https://en.wikipedia.org/wiki/CPU "CPU"), or by the number of data bits that are fetched from its [main memory](https://en.wikipedia.org/wiki/Main_memory "Main memory") in a single operation. In the [IA-32](https://en.wikipedia.org/wiki/IA-32 "IA-32") architecture more commonly known as x86-32, a word is 32 bits, but other past and current architectures use words with 4, 8, 9, 12, 13, 16, 18, 20, 21, 22, 24, 25, 29, 30, 31, 32, 33, 35, 36, 38, 39, 40, 42, 44, 48, 50, 52, 54, 56, 60, 64, 72 bits or others.

Some [machine instructions](https://en.wikipedia.org/wiki/Machine_instruction "Machine instruction") and [computer number formats](https://en.wikipedia.org/wiki/Computer_number_format "Computer number format") use two words (a "double word" or "dword"), or four words (a "quad word" or "quad").

Computer [memory caches](https://en.wikipedia.org/wiki/Memory_cache "Memory cache") usually operate on _[blocks](https://en.wikipedia.org/wiki/Block_\(data_storage\) "Block (data storage)")_ of memory that consist of several consecutive words. These units are customarily called _cache blocks_, or, in [CPU caches](https://en.wikipedia.org/wiki/CPU_cache "CPU cache"), _cache lines_.

[Virtual memory](https://en.wikipedia.org/wiki/Virtual_memory "Virtual memory") systems partition the computer's [main storage](https://en.wikipedia.org/wiki/Main_storage "Main storage") into even larger units, traditionally called _[pages](https://en.wikipedia.org/wiki/Page_\(computer_memory\) "Page (computer memory)")_.

#### Multiplicative prefixes

A unit for a large amount of data can be formed using either a metric or binary prefix with a base unit. For storage, the base unit is typically byte. For communication throughput, a base unit of bit is common. For example, using the metric _kilo_ prefix, a [kilobyte](https://en.wikipedia.org/wiki/Kilobyte "Kilobyte") is 1000 bytes and a [kilobit](https://en.wikipedia.org/wiki/Kilobit "Kilobit") is 1000 bits.

Use of metric prefixes is common, but often inaccurate since binary storage hardware is organized with capacity that is a power of 2 – not 10 as the metric prefixes are. In the context of computing, the metric prefixes are often intended to mean something other than their normal meaning. For example, 'kilobyte' often refers to 1024 bytes even though the standard meaning of kilo is 1000. Also, 'mega' normally means one million, but in computing is often used to mean 220 = 1048576. The table below illustrates the differences between normal metric sizes and the intended size – the binary size.

|Symbol|Prefix|Metric size|Binary size|Size difference|
|---|---|---|---|---|
|k|kilo|1000|1024|2.40%|
|M|mega|10002|10242|4.86%|
|G|giga|10003|10243|7.37%|
|T|tera|10004|10244|9.95%|
|P|peta|10005|10245|12.59%|
|E|exa|10006|10246|15.29%|
|Z|zetta|10007|10247|18.06%|
|Y|yotta|10008|10248|20.89%|
|R|ronna|10009|10249|23.79%|
|Q|quetta|100010|102410|26.77%|

The [International Electrotechnical Commission](https://en.wikipedia.org/wiki/International_Electrotechnical_Commission "International Electrotechnical Commission") (IEC) issued a standard that introduces [binary prefixes](https://en.wikipedia.org/wiki/Binary_prefixes "Binary prefixes") that accurately represent binary sizes without changing the meaning of the standard metric terms. Rather than based on powers of 1000, these are based on powers of 1024 which is a power of 2.

|Symbol|Prefix|Example|Size|
|---|---|---|---|
|Ki|kibi|kibibyte (KiB)|210, 1024|
|Mi|mebi|mebibyte (MiB)|220, 10242|
|Gi|gibi|gibibyte (GiB)|230, 10243|
|Ti|tebi|tebibyte (TiB)|240, 10244|
|Pi|pebi|pebibyte (PiB)|250, 10245|
|Ei|exbi|exbibyte (EiB)|260, 10246|
|Zi|zebi|zebibyte (ZiB)|270, 10247|
|Yi|yobi|yobibyte (YiB)|280, 10248|
|Ri|robi|robibyte (RiB)|290, 10249|
|Qi|quebi|quebibyte (QiB)|2100, 102410|

The [JEDEC memory standard](https://en.wikipedia.org/wiki/JEDEC_memory_standards "JEDEC memory standards") JESD88F notes that the definitions of kilo (K), giga (G), and mega (M) based on powers of two are included only to reflect common usage, but are otherwise deprecated.

### Size examples
- 1 bit: Answer to a yes/no question
- 1 byte: A number from 0 to 255
- 90 bytes: Enough to store a typical line of text from a book
- 512 bytes = 0.5 KiB: The typical [sector](https://en.wikipedia.org/wiki/Disk_sector "Disk sector") size of an old style [hard disk drive](https://en.wikipedia.org/wiki/Hard_disk_drive "Hard disk drive") (modern [Advanced Format](https://en.wikipedia.org/wiki/Advanced_Format "Advanced Format") sectors are 4096 bytes).
- 1024 bytes = 1 KiB: A [block](https://en.wikipedia.org/wiki/Block_\(data_storage\) "Block (data storage)") size in some older [UNIX](https://en.wikipedia.org/wiki/UNIX "UNIX") [filesystems](https://en.wikipedia.org/wiki/Filesystem "Filesystem")
- 2048 bytes = 2 KiB: A [CD-ROM](https://en.wikipedia.org/wiki/CD-ROM "CD-ROM") sector
- 4096 bytes = 4 KiB: A [memory page](https://en.wikipedia.org/wiki/Memory_page "Memory page") in [x86](https://en.wikipedia.org/wiki/X86 "X86") (since [Intel 80386](https://en.wikipedia.org/wiki/Intel_80386 "Intel 80386")) and many other architectures, also the modern [Advanced Format](https://en.wikipedia.org/wiki/Advanced_Format "Advanced Format") hard disk drive sector size.
- 4 kB: About one page of text from a [novel](https://en.wikipedia.org/wiki/Novel "Novel")
- 120 kB: The text of a typical pocket book
- 1 MiB: A 1024×1024 pixel [bitmap](https://en.wikipedia.org/wiki/Bitmap "Bitmap") image with 256 colors (8 bpp color depth)
- 3 MB: A three-minute [song](https://en.wikipedia.org/wiki/Song "Song") (133 kbit/s)
- 650–900 MB – a CD-ROM
- 1 GB: 114 minutes of uncompressed CD-quality audio at 1.4 Mbit/s
- 16 GB: DDR5 DRAM laptop memory under $40 (as of early 2024)
- 32/64/128 GB: Three common sizes of [USB flash drives](https://en.wikipedia.org/wiki/USB_flash_drive "USB flash drive")
- 1 TB: The size of a $30 hard disk (as of early 2024)
- 6 TB: The size of a $100 hard disk (as of early 2022)
- 16 TB: The size of a small/cheap $130 (as of early 2024) enterprise SAS hard disk drive
- 24 TB: The size of $440 (as of early 2024) "video" hard disk drive
- 32 TB: Largest [hard disk drive](https://en.wikipedia.org/wiki/Hard_disk_drive "Hard disk drive") (as of mid-2024)
- 100 TB: Largest commercially available [solid-state drive](https://en.wikipedia.org/wiki/Solid-state_drive "Solid-state drive") (as of mid-2024)
- 200 TB: Largest solid-state drive constructed (prediction for mid-2022)
- 1.6 PB (1600 TB): Amount of possible storage in one 2U server (world record as of 2021, using 100 TB solid-states drives).[[11]](https://en.wikipedia.org/wiki/Units_of_information#cite_note-11)
- 1.3 ZB: Prediction of the volume of the whole internet in 2016

### Obsolete and unusual units 

Some notable unit names that are today obsolete or only used in limited contexts.

- 1 bit: unibit[
- 2 bits: dibit, crumb, quartic digit, quad, semi-nibble, nyp
- 3 bits: tribit,triad,) triade
- 4 bits: see [nibble](https://en.wikipedia.org/wiki/Nibble "Nibble")
- 5 bits: pentad, pentade,
- 6 bits: byte (in early [IBM](https://en.wikipedia.org/wiki/IBM "IBM") machines using [BCD alphamerics](https://en.wikipedia.org/wiki/Binary_Coded_Decimal "Binary Coded Decimal")), hexad, hexade, sextet
- 7 bits: heptad, heptade
- 8 bits: [octad](https://en.wikipedia.org/wiki/Octad_\(computing\) "Octad (computing)"),
- 9 bits: nonet, rarely used
- 10 bits: declet, decle

- 12 bits: slab
- 15 bits: parcel (on [CDC 6600](https://en.wikipedia.org/wiki/CDC_6600 "CDC 6600") and [CDC 7600](https://en.wikipedia.org/wiki/CDC_7600 "CDC 7600"))
- 16 bits: doublet, wyde, parcel (on [Cray-1](https://en.wikipedia.org/wiki/Cray-1 "Cray-1")), chawmp (on a 32-bit machine)
- 18 bits: chomp, chawmp (on a 36-bit machine)
- 32 bits: quadlet, tetra
- 64 bits: octlet, octa
- 96 bits: bentobox (in [ITRON OS](https://en.wikipedia.org/wiki/ITRON_project "ITRON project"))
- 128 bits: hexlet
- 256 bytes: [page](https://en.wikipedia.org/wiki/Page_\(computer_memory\) "Page (computer memory)") (on Intel 4004, [8080](https://en.wikipedia.org/wiki/Intel_8080 "Intel 8080") and 8086 processors,) also many other 8-bit processors – typically much larger on many 16-bit/32-bit processors)
- 6 trits: [tryte](https://en.wikipedia.org/wiki/Tryte "Tryte"), combit, comword