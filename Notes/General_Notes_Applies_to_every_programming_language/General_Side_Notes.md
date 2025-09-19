## Classes OOP
**`__init__`** is same as constructor function in JavaScript. Both of them create instances of the class and give them same keys but unique or different values. 

We should remember that constructor functions are called **every time we instantiate an object**.
##### Python
```python

class PlayerCharacter(ParentClass):
	def __init__(self, name, age):
		self.name = name
		self.age = age
		
	say_hello(name):
		print("Hello" + name,  self.age)


z = PlayerCharacter("George", 15)
z.say_hello(z.name)
```

#### JavaScript
```javascript
class PlayerCharacter extends ParentClass: 
	constructor(name,age):
		this.name = name;
		this.age = age

// Constructor Functions || Real Classes

const Child = function(x,y){
	this.x = x;
	this.y = y
};

const z = new Child(1,2);

// Adding Functions
Child.prototype.add = function(x,y){
	console.log(this.x, this.y);
	return x + y;
};

z.add(z.x, z.y); // 3

// Inheritance -> Legacy
Child.prototype = Object.create(PlayerCharacter.prototype);

// Not Legacy 
Object.setPrototypeOf(Child.prototype, PlayerCharacter.prototype);

```

## this and self
**`this`** and **`self`** keywords are similar, because the both are reference to the current instance of the class. this has other meanings depending on the place and surroundings where it is used, it refers to the current object.

## State
**State** -> State simply refers to a piece of data in the application that might change over time. 
For Example, whether a certain user is logged in, or on a page with a list with several pages what the current page is.  


## Function
**Function** -> A Function is a reusable block of code, Which can be invoked/called anytime and anywhere we want. 

**Parameters** -> Functions have parameters, which are local variables, placeholders for incoming/provided/given/passed value/data. Parameters can be any Data Type or Any Expression. 

**Arguments** -> When we call/invoke a function it accepts arguments. In other words we give/pass value/data to an function, which we then can use as a local variables in function code. Arguments can be any Data Type or Even an Expression.

**Return Value** -> Function can also return value/data using `return` keyword.

**Function:** A function is a reusable block of code that is defined once and can be executed whenever needed. This process is known as invoking or calling the function.
- **Parameters:** Functions can have parameters, which act as placeholders for the values or data that will be provided/passed/given into the function when it is called/invoked. These parameters can be of any data type or expression.
    
- **Arguments:** When a function is called, you provide/pass/give arguments, which are the actual values or data that correspond to the function's parameters. These arguments can also be of any data type or expression.
    
- **Return Value:** A function can return a value using the `return` keyword. This returned value can be used by the code that called the function.

```javascript
// Function Declaration
function func(parameter1, parameter2, parameters){ // <- Parameters
	// Function Body
	return [parameter1, parameter2, parameters];
};

// Calling/Invoking a Function
func(argument1, argument2, arguments)  // <- Arguments
// Storing Data
const value = func(1, 2, 3) // <- Storing returned value
```

When a function is called, the **control** (the point where the program is running) moves to the function body, and when the function ends, it moves back to where the function was called.
The program jumps to the function, initializes its parameters with the arguments, and runs the body within a separate stack frame. After it’s done, it returns the result and clears the frame.
When you call the function, the program's execution **jumps** to that location in memory (the function definition), executes the code with the **arguments** you passed, and then returns back to where the function was called.

## Pure Functions
**Pure Functions** -> A pure function is a fundamental concept in functional programming and refers to a function that adheres to two main principles.
1. Deterministic Output:
	* A pure function always produces the same output given the same input. This mean that the function's return value is solely determined by its local variables input parameters and nothing else.
2.  No Observable Side Effects:
	* A pure function does not cause any observable side effects. This implies that the function's execution does not alter any state or interact with the outside world(such as modifying a global variable, changing the state of an object, writing to a file, or printing to a console).


**Pure Functions**: Functions that produce the same output for the same input and do not cause any observable side effects.

A Function that has **no** side effects.
- Does **not** change any variables outside its scope
- Given the **same input**, a pure function always returns the **same output**

## Side Effects
**Side Effects** ->  A side effect refers to any change in the system's state or any observable interaction with external systems that occurs during the execution of a function or expression.

Dependency on or modification of any data outside the function scope. _"Interaction with the outside world"_. **Examples**: Mutating external variables, HTTP requests, writing to DOM.

Basically Outside Variable Mutation, and Unpredictable Output.

#### Summary:
- **Pure Functions**: Functions that produce the same output for the same input and do not cause any observable side effects.
- **Side Effects**: Any changes to the state or interactions with external systems that occur during the execution of a function, making the function's behavior dependent on contexts beyond its input parameters.

## Higher Order Function
**Higher Order Function** -> A Higher order function is a function that accepts inside of its parameters another function or returns a function.

**Higher Order Function** -> A higher-order function is a function that either takes one or more functions as arguments or returns a function as a result. This concept is fundamental in functional programming and is prevalent in many programming languages like JavaScript, Python, and Haskell. By accepting functions as parameters, higher-order functions allow for more abstract and flexible code. For instance, the `map` function in JavaScript takes a callback function that it applies to each element in an array, thereby transforming the array based on the logic defined in the callback.

Similarly, higher-order functions can return other functions, enabling the creation of function generators or utilities that produce specialized functions. An example of this is a function that creates a multiplier function. When you call this generator function with a specific multiplier value, it returns a new function that multiplies its input by that value. This is particularly useful for creating reusable and modular code components.

Using higher-order functions promotes code reuse and enhances abstraction. Instead of writing repetitive code blocks, you can define a general higher-order function and pass specific behaviors as functions. This approach not only makes your code cleaner but also more expressive, capturing the essence of the operations being performed.

In functional programming, higher-order functions are essential because they align with the principles of immutability and stateless functions. They enable the composition of complex operations from simpler ones, facilitating a declarative coding style. This can lead to more predictable and maintainable code, as the functions operate without side effects, relying solely on their inputs and producing consistent outputs.

To summarize, higher-order functions are powerful tools that enhance the expressiveness and modularity of code by allowing functions to accept and return other functions. This capability is a cornerstone of functional programming, enabling developers to write more abstract, reusable, and maintainable code.

```python
def greet(func):
	func()
def greet2(
	def func():
		return 5
	return func
)
```

## Identifier
An identifier in JavaScript is a sequence of characters used in the code to uniquely identify a variable, function, or property. Identifiers are essential in programming as they serve as the names for these entities, allowing developers to reference and manipulate them within their code.

An identifier is a sequence of characters used in programming to uniquely name and refer to variables, functions, properties, or other entities within the code. Think of an identifier as a label or a tag that you attach to something in your code so that you can easily identify and use it later. Identifiers are crucial because they allow programmers to create readable and maintainable code, enabling them to reference and manipulate data and functions efficiently.

An identifier is a sequence of characters used in programming to uniquely name variables, functions, and properties. It serves as a label, allowing programmers to reference and manipulate these entities within the code.

In essence, identifiers are a fundamental aspect of programming, providing a means to name and organize the various elements within a codebase.

An identifier in programming is a sequence of characters used to name and refer to variables, functions, properties, and other entities within a program. Identifiers are fundamental because they enable developers to label and reference various components of their code in a meaningful and organized way. This organization is crucial for writing readable, maintainable, and efficient code.

An identifier in programming is a sequence of characters used to name and refer to various elements within a program, such as variables, functions, and properties. Think of identifiers as labels or tags that you attach to different parts of your code so you can identify and use them later.

### Sequence of Characters
An identifier is made up of a series of individual characters, which can include letters (both uppercase and lowercase), digits, and special characters like the underscore (_) and the dollar sign ($). The characters in an identifier must follow specific rules to be valid within the programming language, ensuring that the code is interpreted correctly by the computer.

In summary, identifiers in JavaScript are essential naming constructs within the code that allow developers to define and reference variables, functions, and properties.

## Regular Expressions
**Regular Expressions** -> A regular expression, is a sequence of characters that specifies a match pattern in text. Usually such patterns are used by string-searching algorithms for "find" or "find and replace" operations on strings, or for input validation. Regular expression techniques are developed in theoretical computer science and formal language theory.

## Core Function of every application
The core function of every application is its ability to manage, store, and manipulate data created within it or received from an external source.

This data can be in the form of variables, objects, booleans, etc. It can be of any data type supported by the language used. This data has to be stored, modified, and used in whatever way the application needs it.

## Aggregation
**Aggregation** -> Aggregation operations process data records and return computed results. Aggregation operations group values from multiple documents together, and can perform a variety of operations on ht grouped data to return a single result. 

## Compile
**Compile** -> Compile is, when **Code** is **Converted** into **Binary Code**.

## Initialization
**Initialization occurs when one assigns an initial value to a variable**.

**Initialization** -> Initializing is the the term used to describe the process of assignment of a value to a variable (i.e Storing the Value, Piece of Data) in the Location in Memory, which the Variable "Points" to.

## Parse
**Parse** -> Essentially means to **Read** the code.
**Parse** -> Parsing basically means to just read the code, but without executing it.

## Pipeline
In software engineering a **pipeline** consists of a chain of processing elements (processes, threads, coroutines, functions, _etc._), arranged so that the output of each element is the input of the next. The concept is analogous to a physical pipeline. Usually some amount of buffering is provided between consecutive elements. The information that flows in these pipelines is often a stream of records, bytes, or bits, and the elements of a pipeline may be called filters. This is also called the **pipe(s) and filters** filter design which is monolithic. Its advantages are simplicity and low cost while its disadvantages are lack of elasticity, fault tolerance and scalability. Connecting elements into a pipeline is analogous to function composition.

Narrowly speaking, a pipeline is linear and one-directional, though sometimes the term is applied to more general flows. For example, a primarily one-directional pipeline may have some communication in the other direction, known as a return channel or _backchannel_, as in the lexer hack, or a pipeline may be fully bi-directional. Flows with one-directional trees and directed acyclic graph topologies behave similarly to linear pipelines. The lack of cycles in such flows makes them simple, and thus they may be loosely referred to as "pipelines".

## Decomposition
**Decomposition** -> **Decomposition** in [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), also known as **factoring**, is breaking a complex [problem](https://en.wikipedia.org/wiki/Computational_problem "Computational problem") or [system](https://en.wikipedia.org/wiki/System "System") into parts that are easier to conceive, understand, program, and maintain.

### Decomposition Paradigm
A decomposition paradigm in computer programming is a strategy for organizing a program as a number of parts, and usually implies a specific way to organize a program text. Typically the aim of using a decomposition paradigm is to optimize some metric related to program complexity, for example a program's modularity or its maintainability.

Most decomposition paradigms suggest breaking down a program into parts to minimize the static dependencies between those parts, and to maximize each part's [cohesiveness](https://en.wikipedia.org/wiki/Cohesion_(computer_science) "Cohesion (computer science)"). Popular decomposition paradigms include the procedural, modules, [abstract data type](https://en.wikipedia.org/wiki/Abstract_data_type "Abstract data type"), and [object oriented](https://en.wikipedia.org/wiki/Object_oriented "Object oriented") paradigms.

Though the concept of decomposition paradigm is entirely distinct from that of [model of computation](https://en.wikipedia.org/wiki/Model_of_computation "Model of computation"), they are often confused. For example, the [functional model](https://en.wikipedia.org/wiki/Functional_model "Functional model") of computation is often confused with procedural decomposition, and the [actor model](https://en.wikipedia.org/wiki/Actor_model "Actor model") of computation is often confused with [object oriented](https://en.wikipedia.org/wiki/Object_oriented "Object oriented") decomposition.

### Decomposition Diagram
![[Pasted image 20241012124244.png]]
Decomposition Structure.

![[Pasted image 20241012124318.png]]
Negative Node-Numbered Context.

![[Pasted image 20241012124333.png]]
Static, Dynamic, and Requirements Models for Systems Partition.

![[Pasted image 20241012124355.png]]
Functions and Use Scenarios Mapping to Requirements and Goals.

A decomposition diagram shows a complex, process, organization, data subject area, or other type of object broken down into lower level, more detailed components. For example, decomposition diagrams may represent organizational structure or functional decomposition into processes. Decomposition diagrams provide a logical hierarchical decomposition of a system.

## Nesting
**Nesting** -> In **computer science** and **informatics**, **nesting** refers to organizing information or structures in layers, where one object is contained within another similar object. This concept is common in programming, where it often refers to **self-similar** or **recursive** structures. For example, in code, nesting can occur when functions, loops, or conditionals are placed inside one another, or when **data structures** (like arrays or objects) contain other arrays or objects. Nesting allows for more complex and hierarchical designs, enabling better organization and more flexible manipulation of data or logic.

## Iterator
An Iterator is **an object that can be used to loop through collections**, like **ArrayList** and **HashSet**. It is called an "iterator" because "iterating" is the technical term for looping.

In computer programming, an **iterator** is an object that enables a programmer to traverse a container, particularly lists.

## Iterable
An **iterable** is a collection that is able to get iterated over.

**iterate** -> iterate means we can go one by one to check each item in the collection.

**Iterables** are objects that can be iterated in iterations.

Iterable is an object which can be looped over or iterated over with the help of a for loop.

Objects like lists, tuples, sets, dictionaries, strings, etc. are called iterables. **In short and simpler terms, iterable is anything that you can iterate/loop over.**

In simpler words, iterable is a container that has data or values and we perform an iteration over it to get element one by one. (Can traverse through all the given values one by one).

We are iterating over a iterable.

```python
iterable
	list,
	dict,
	tuple,
	set,
	str,
```

## Declaration Vs. Definition: Know What is the Difference Between Declaration and Definition

If you are new to the world of programming, then these two terms- Declaration and Definition are very confusing. They both are somewhat different because, in _definition_, we assign memories to the variables. On the other hand, we do not allocate memory in the case of _declaration_. You can declare an entity more than once, but you can’t define it multiple times in a program. Definition automatically becomes a declaration in a majority of scenarios. Let us now dive deeper into the difference between definition and declaration in detail.

### What is a Definition?

A definition basically identifies the data or code associated with the name of class, function, variable, etc. A compiler necessarily requires the definition for allocating the storage space for an entity that is declared. When we define a variable, it holds memory consisting of many bytes (for that particular variable). The function definition provides the code for any function. One can only define a program element in a given program once because the definition is a program element’s unique specification. There can be one or many relationships between declaration and definition.

In some situations, one cannot define a program element but can declare it. For instance, it happens in some cases when we don’t invoke a function or when we don’t use an address even if we declare it. One more example can be when we don’t use the class definition but ultimately declare it.

### What is a Declaration?

We basically use declarations for specifying the particular names of a given program- like the name of a class, namespace, function, variable, etc. You cannot use any name in a program without declaring it. Unlike definition, one can easily declare the elements of a program multiple times. But you can only achieve multiple declarations by making these multiple declarations using an identical format. You can use the declaration as a medium to provide visibility to the elements of a program from a compiler’s perspective.

Declaration basically serves a definition’s purpose. But it does imply some conditions in certain cases, such as:

- When the declaration becomes a typed statement.
- When the class name declaration occurs without including its definition (like the class T).
- We declare a variable without the function body or an initializer, but it includes the external specifiers. It means that the definition may be for another function- thus, it provides an external linkage name.
- A declaration usually takes place in the scope. This scope defines the overall visibility of a declared name and the object duration (defined).
- When declaring a static data member inside a class declaration- we do not consider it a declaration. It is because it produces a single copy for all the objects in a class. The static data members form the components of the various objects in a provided class type.

### Difference Between Definition and Declaration

|                      |                                                                                              |                                                                                                           |
| -------------------- | -------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| **Parameters**       | **Definition**                                                                               | **Declaration**                                                                                           |
| Basics               | It aims at determining the overall values stored in a class, a function, or a variable.      | It aims at specifying the name of any given class, function, variable, etc.                               |
| Allocation of Memory | Definition allocates memory to an entity.                                                    | A declaration does not allocate memory to the entities.                                                   |
| Repetition           | Once you define an entity, you cannot keep repeating the definition process again and again. | Even if you declare an entity, the process of redeclaration can always be possible at any given instance. |
| Scope                | It is determined.                                                                            | It has well-defined visibility.                                                                           |
### Summary
**Definition** -> refers to the place where the variable is created or assigned storage.

**Declaration** -> refers to places where the nature of the variable is stated but no storage is allocated.

## What is Routing
The process of choosing a path across one or more networks is known as Network Routing. Nowadays, individuals are more connected on the internet and hence, the need to use Routing Communication is essential.

Routing chooses the routes along which Internet Protocol (IP) packets get from their source to their destination in packet-switching networks. This article will discuss the details of the Routing Process along with its different types and working principles.

### What is a Router?

Routers are specialized pieces of network hardware that make these judgments about Internet routing. It is a networking device that forwards data packets between computer networks. Also, it helps to direct traffic based on the destination [IP address](https://www.geeksforgeeks.org/what-is-an-ip-address/). It ensures that data reaches its intended destination.

As the router connects different networks, it manages data traffic between them. The Router operates at Layer 3 (the network layer) of the [OSI Model](https://www.geeksforgeeks.org/open-systems-interconnection-model-osi/). It is also responsible for determining the best path for data to travel from one network to another.

### What is Routing?

Routing refers to the process of directing a data packet from one node to another. It is an autonomous process handled by the network devices to direct a data packet to its intended destination. Note that, the node here refers to a [network device](https://www.geeksforgeeks.org/network-devices-hub-repeater-bridge-switch-router-gateways/) called - '[Router](https://www.geeksforgeeks.org/introduction-of-a-router/)'.

Routing is a crucial mechanism that transmits data from one location to another across a network (Network type could be any like [LAN, WAN, or MAN](https://www.geeksforgeeks.org/types-of-area-networks-lan-man-and-wan/)). The process of routing involves making various routing decisions to ensure reliable & efficient delivery of the data packet by finding the shortest path using various routing metrics which we will be discussing in this article.

Routing of a data packet is done by analyzing the destination IP Address of the packet. Look at the below image:

![Packet-1](https://media.geeksforgeeks.org/wp-content/uploads/20231127222035/Packet-1.png)

Routing of packets

- The Source Node (Sender) sends the data packet on the network, embedding the IP in the header of the data packet.
- The nearest router receives the data packet, and based on some metrics, further routes the data packet to other routers.
- Step 2 occurs recursively till the data packet reaches its intended destination.

**Note** There are limits to how many hop counts a packet can do if it is exceeded, the packet is considered to be lost.

### What are Different Types of Routing?

Routing is typically of 3 types, each serving its purpose and offering different functionalities.

![Types-of-Routing](https://media.geeksforgeeks.org/wp-content/uploads/20231130224032/Types-of-Routing.png)

Types of Routing:

#### 1. Static Routing

Static routing is also called as "non-adaptive routing". In this, routing configuration is done manually by the network administrator. Let's say for example, we have 5 different routes to transmit data from one node to another, so the network administrator will have to manually enter the routing information by assessing all the routes.

- A network administrator has full control over the network, routing the data packets to their concerned destinations
- Routers will route packets to the destination configured manually by the network administrator.
- Although this type of routing gives fine-grained control over the routes, it may not be suitable for large-scale enterprise networks.

#### 2. Dynamic Routing

Dynamic Routing is another type of routing in which routing is an autonomous procedure without any human intervention. Packets are transmitted over a network using various shortest-path algorithms and pre-determined metrics. This type of routing is majorly preferred in modern networks as it offers more flexibility and versatile functionality.

- It is also known as adaptive routing.
- In this, the router adds new routes to the routing table based on any changes made in the topology of the network.
- The autonomous procedure of routing helps in automating every routing operation from adding to removing a route upon updates or any changes made to the network.

#### 3. Default Routing

Default Routing is a routing technique in which a router is configured to transmit packets to a default route that is, a [gateway](https://www.geeksforgeeks.org/default-gateway-in-networking/) or next-hop device if no specific path is defined or found. It is commonly used when the network has a single exit point. The IP Router has the following address as the default route: 0.0.0.0/0.

### What is the Working Principle of Routing?

Routing works by finding the shortest path from the source node to the destination node across a network. Here's the step-by-step working of routing:

#### Step 1: Communication initiation

The first step that typically happens is, one node (client or server) initiates a communication across a network using [HTTP](https://www.geeksforgeeks.org/http-full-form/) protocols.

#### Step 2: Data Packets

The source device now breaks a big chunk of information into small data packets for reliable and efficient transmission. This process is called de-assembling and encapsulating the data payload. Then each data packet is labeled with the destination node's IP address.

#### Step 3: Routing Table

The [Routing table](https://www.geeksforgeeks.org/routing-tables-in-computer-network/) is a logical [data structure](https://www.geeksforgeeks.org/data-structure-meaning/) used to store the IP addresses and relevant information regarding the nearest routers. The source node then looks up the IP addresses of all the nodes that can transmit the packet to its destination selects the shortest path using the shortest path algorithm and then routes accordingly.

The Routing Table is stored in a router, a network device that determines the shortest path and routes the data packet.

#### Step 4: Hopping procedure

In the procedure or routing, the data packet will undergo many hops across various nodes in a network till it reaches its final destination node. Hop count is defined as the number of nodes required to traverse through to finally reach the intended destination node.

This hopping procedure has certain criteria defined for every data packet, there's a limited number of hops a packet can take if the packet exceeds that, then it's considered to be lost and is retransmitted.

#### Step 5: Reaching the destination node

Once all the data packets reach their intended destination node, they re-assemble and transform into complete information that was sent by the sender (source node). The receiver will perform various [error-checking](https://www.geeksforgeeks.org/error-detection-in-computer-networks/) mechanisms to verify the authenticity of the data packets.

Overall, the data packet will be transmitted over the least hop-count path as well as the path on which there is less traffic to prevent packet loss.

![Routing-Working](https://media.geeksforgeeks.org/wp-content/uploads/20231130220555/Routing-Working.png)

Working of Routing

In the above image, we have 3 major components

- Sender
- Receiver
- Routers

The shortest path is highlighted in red, the path with the least hop count. As we can see, there are multiple paths from source to node but if all the appropriate metrics are satisfied, the data packets will be transmitted through the shortest path (highlighted in red).

### What are the Main Routing Protocols?

- ****RIP (Routing Information Protocol):**** It is a distance-vector protocol that uses hop count as a metric.
- ****OSPF (Open Shortest Path First):**** OSPF is a link-state protocol that finds the shortest path using the Dijkstra algorithm.
- ****EIGRP (Enhanced Interior Gateway Routing Protocol):**** It is a hybrid protocol that combines features of distance-vector and link-state.
- ****BGP (Border Gateway Protocol):**** It is a path-vector protocol that is used for routing between different autonomous systems on the internet.
- ****IS-IS (Intermediate System to Intermediate System):**** It is a link-state protocol that is primarily used in large networks like ISPs.

### What are Different Routing Metrics?

The purpose of routing protocols is to learn about all the available paths to route data packets, build routing tables, and make routing decisions based on specified metrics. There are two primary types of routing protocols rest of them ideate from these two only.

#### 1. Distance Vector Routing

In this type of routing protocol, all the nodes that are a part of the network advertise their routing table to their adjacent nodes (nodes that are directly connected) at regular intervals. With each router getting updated at regular intervals, it may take time for all the nodes to have the same accurate network view.

- Uses fixed length sub-net, not suitable for scaling.
- Algorithm used: [Bellman Ford Algorithm](https://www.geeksforgeeks.org/bellman-ford-algorithm-dp-23/) to find the shortest path.

#### 2. Link State Routing

Link State Routing is another type of dynamic routing protocol in which routes advertise their updated routing tables only when some new updates are added. This results in the effective use of bandwidth. All the routers keep exchanging information dynamically regarding different links such as cost and hop count to find the best possible path.

- Uses a variable length subnet mask, which is scalable and uses addressing more effectively.
- The algorithm used: [Dijkstra's Algorithm](https://www.geeksforgeeks.org/introduction-to-dijkstras-shortest-path-algorithm/) to find the shortest path.

Let's look at the metrics used to measure the cost of travel from one node to another:-

1. ****Hop Count:**** Hop count refers to the number of nodes a data packet has to traverse to reach its intended destination. Transmitting from one node to another node counts as 1 - hop count. The goal is to minimize the hop count and find the shortest path.
2. ****Bandwidth Consumption:**** Bandwidth is the ability of a network to transmit data typically measured in [Kbps (Kilobits per second)](https://www.geeksforgeeks.org/what-is-kilobytes-per-secondkbps/), [Mbps (Megabits per second)](https://www.geeksforgeeks.org/what-are-megabits-per-second-mbps/), or [Gbps (Gigabits per second)](https://www.geeksforgeeks.org/what-is-gbps/). The bandwidth depends on several factors such as - the volume of data, traffic on a network, network speed, etc. Routing decision is made in a way to ensure efficient bandwidth consumption.
3. ****Delay:**** Delay is the time it takes for a data packet to travel from the source node to its destination node. There are different types of delay such as - propagation delay, transmission delay, and queuing delay.
4. ****Load:**** Load refers to the network traffic on a certain path in the context of routing. A data packet will be routed to the path with a lesser load so that it reaches its destination in the specified time.
5. ****Reliability:**** Reliability refers to the assured delivery of the data packet to its intended destination although there are certain other factors, the data packet is routed in such a way that it reaches its destination. The stability and availability of the link in the network are looked over before routing the data packet from a specific path.

### What are the Advantages of Routing?

- Overall routing can be done in various ways its important to know the requirements and use the one that fits right for our specific needs, hence automated routing is typically preferred as the routing of packets is done by the algorithms defined and the manually configurable routing can give us a fine-grained control over the network.
- Routing is a highly scalable operation for transmitting data that is, in a large-scale enterprise network it becomes crucial to manage information related to all the nodes that may be sharing sensitive and confidential information regarding the organization.
- Load Balancing is also one of the crucial aspects taken care of by routing data packets off the routes that are generally busy as sending data through those routes will only put our data at risk of getting lost.

### What are the Disadvantages of Routing?

Every type of routing comes with some pros and cons here are some of the disadvantages for specific types of routing :

- Static Routing: This type of routing is appropriate only for smaller networks where the network administrator has an accurate view of the network & good knowledge of topology else it might raise some security concerns and complex configuration issues.
- Dynamic Routing: Everything is done automatically by the algorithms, providing less control over the network that may not be suitable for every kind of network. It is also computationally expensive and consumes more bandwidth.
- Default Routing: The path on which the packets are to be transmitted by default is configurable but can be a complex procedure if not defined clearly.

### Conclusion

Routing is a fundamental concept in computer science that allows every network device across the world to share data across the internet. Here, the shortest path is selected by the routing algorithms when routing a data packet. So, the Routing Algorithms select the shortest path based on metrics like - hop count, delay, bandwidth, etc.
### What are routing examples?

> Traffic in a road system is an example of routing, in which driver picks a selected path that reduces their travel time.

### How does a router work?

> Routes examine the IP in the header of every data packet received and if it belongs to it then it keeps the data packet else it re-routes it to another router based on some metrics.

### What is a Default Gateway?

> The default gateway is simply a router or another network device that allows the host to connect with other networks outside its local network. It is a crucial component of internetwork communication.

## Types of Routing
Routing is the process of determining paths through a network for sending data packets. It ensures that data moves effectively from source to destination, making the best use of network resources and ensuring consistent communication. Routing performed by layer 3 (or network layer) devices to deliver the packet by choosing an optimal path from one network to another. It is an autonomous process handled by the network devices to direct a data packet to its intended destination. The node here refers to a network device called Router.

Routing is classified into Static Routing, Default Routing, and Dynamic Routing. In this article, we will see types of routing in detail.

### Types of Routing

[Routing](https://www.geeksforgeeks.org/what-is-routing/) is typically of 3 types, each serving its purpose and offering different functionalities.

![Types-of-Routing](https://media.geeksforgeeks.org/wp-content/uploads/20240713185448/Types-of-Routing.jpg)

Types of Routing

### 1. Static Routing

[Static routing](https://www.geeksforgeeks.org/difference-between-static-and-dynamic-routing/) is also called as “non-adaptive routing”. In this, routing configuration is done manually by the network administrator. Let’s say for example, we have 5 different routes to transmit data from one node to another, so the network administrator will have to manually enter the routing information by assessing all the routes.

### Advantages of Static Routing

- No routing overhead for the router [CPU](https://www.geeksforgeeks.org/difference-between-cpu-and-gpu/) which means a cheaper router can be used to do routing.
- It adds security because only an only administrator can allow routing to particular networks only.
- No [bandwidth](https://www.geeksforgeeks.org/introduction-to-bandwidth/) usage between [routers](https://www.geeksforgeeks.org/introduction-of-a-router/).

### Disadvantage of Static Routing

- For a large network, it is a hectic task for administrators to manually add each route for the network in the [routing table](https://www.geeksforgeeks.org/routing-tables-in-computer-network/) on each router.
- The administrator should have good knowledge of the topology. If a new administrator comes, then he has to manually add each route so he should have very good knowledge of the routes of the topology.

### Configuration of Static Routing

![static-routing](https://media.geeksforgeeks.org/wp-content/uploads/20241120114334240383/static-routing.jpg)

```
R1 having IP address 172.16.10.6/30 on s0/0/1, 192.168.20.1/24 on fa0/0.   
R2 having IP address 172.16.10.2/30 on s0/0/0, 192.168.10.1/24 on fa0/0.   
R3 having IP address 172.16.10.5/30 on s0/1, 172.16.10.1/30 on s0/0, 10.10.10.1/24 on fa0/0. 
```

Now because only static routes for router R3: 

```
R3(config)#ip route 192.168.10.0 255.255.255.0 172.16.10.2
R3(config)#ip route 192.168.20.0 255.255.255.0 172.16.10.6
```

Here, provided the route for the 192.168.10.0 network where 192.168.10.0 is its network I’d and 172.16.10.2 and 172.16.10.6 are the next-hop address.   
Now, configuring for R2: 

```
R2(config)#ip route 192.168.10.0 255.255.255.0 172.16.10.1
R2(config)#ip route 10.10.10.0 255.255.255.0 172.16.10.1
R2(config)#ip route 172.16.10.0 255.255.255.0 172.16.10.1
```

Similarly for R1: 

```
R1(config)#ip route 192.168.20.0 255.255.255.0 172.16.10.5
R1(config)#ip route 10.10.10.0 255.255.255.0 172.16.10.5
R1(config)#ip route 172.16.10.0 255.255.255.0 172.16.10.5
```

### 2. Default Routing

This is the method where the router is configured to send all packets toward a single router (next hop). It doesn’t matter to which network the packet belongs, it is forwarded out to the router which is configured for default routing. It is generally used with stub routers. A stub router is a router that has only one route to reach all other networks. 

#### Advantages of Default Routing

- Default routing provides a “last resort” route for packets that don’t match any specific route in the routing table. It ensures that packets are not dropped and can reach their intended destination.
- It simplifies network configuration by reducing the need for complex routing tables.
- Default routing improves network reliability and reduces packet loss.

#### Disadvantages of Default Routing

- Relying solely on default routes can lead to inefficient routing, as it doesn’t consider specific paths.
- Using default routes may introduce additional [network latency](https://www.geeksforgeeks.org/what-is-latency/).

#### Configuration of Dynamic Routing

Using the same topology which we have used for static routing before.

![dynamic-routing](https://media.geeksforgeeks.org/wp-content/uploads/20241120114423291323/dynamic-routing.jpg)

In this topology, R1 and R2 are stub routers so we can configure default routing for both these routers.  Configuring default routing for R1: 

`R1(config)#ip route 0.0.0.0 0.0.0.0  172.16.10.5`

Now configuring default routing for R2: 

`R2(config)#ip route 0.0.0.0 0.0.0.0  172.16.10.1`

### 3. Dynamic Routing

Dynamic routing makes automatic adjustments of the routes according to the current state of the route in the routing table. Dynamic routing uses protocols to discover network destinations and the routes to reach them. [RIP](https://www.geeksforgeeks.org/computer-network-routing-vs-routed-protocols/) and [OSPF](https://www.geeksforgeeks.org/computer-network-open-shortest-path-first-ospf-protocol-fundamentals/) are the best examples of dynamic routing protocols. Automatic adjustments will be made to reach the network destination if one route goes down. A dynamic protocol has the following features: 

- The routers should have the same dynamic protocol running in order to exchange routes.
- When a router finds a change in the topology then the router advertises it to all other routers.

#### Advantages of Dynamic Routing

- Easy to configure.
- More effective at selecting the best route to a destination remote network and also for discovering remote networks.

#### Disadvantage of Dynamic Routing

- Consumes more [bandwidth](https://www.geeksforgeeks.org/what-is-bandwidth-definition-working-importance-uses/) for communicating with other neighbors.
- Less secure than static routing.

### Conclusion

Routing is an important concept that allows every network device across the world to share data with each other across internet. Shortest path is selected by the routing algorithms when routing a data packet. [Routing Algorithms](https://www.geeksforgeeks.org/classification-of-routing-algorithms/) select the shortest path based on metrics like – hop count, delay, bandwidth etc. The core network device used in routing is router. Routes are stored in a logical data structure called – ‘****Routing Table****‘. Static routing is a process in which we have to manually add routes to the routing table , In Dynamic Routing packets are transmitted over a network using various shortest path algorithms and pre-determined metrics, Default Routing is a routing technique in which a router is configured to transmit packets to a default route that is, a gateway or next hop device if no specific path is defined or found.


## What is Dynamic Routing in Computer Science
**Routing** is a procedure of making decisions in which the router (_which is a hardware device used in networking to receive and send data in the form of packets on a network_) selects the best path to make data transfer from source to destination. A router exists in the network layer in the OSI as well as TCP/IP model. Some functions of a router are:

1. Building an optimal path on a network to reach its destination (in which static and dynamic routing take place).
2. Taking routing decisions.
3. Balancing load.

### **Types of Routing:**

1. **Static routing**
2. **Default routing**
3. **Dynamic routing**

Static and [Default routing](https://www.geeksforgeeks.org/types-of-routing/) has some drawbacks, due to which Dynamic Routing was introduced.

#### **Drawbacks of Static Routing:**

- It is a burdensome task to sum up or add-on each route manually to the routing map in a large network.
- Managing its ordering is time-consuming.
- It cannot reroute traffic in case some link fails.

#### **Drawbacks of Default routing was:**

- If the network is complex then it is more difficult to set up.

To overcome the shortcomings of static and default routing, Back in the 1980s, the first-ever Dynamic routing was used in a computer and the protocol which was used in it was the RIP(routing information protocol). 

### Dynamic Routing

**Dynamic routing** is known as a technique of finding the best path for the data to travel over a network in this process a router can transmit data through various different routes and reach its destination on the basis of conditions at that time of communication circuits.

![Dynamic Routing](https://media.geeksforgeeks.org/wp-content/uploads/20211207133356/DynamicRouting-660x594.png)

Dynamic Routing

Dynamic routers are smart enough to take the best path for data based on the condition of the present scenario at that time of the network. In case one section fails in the network to transfer data forward dynamic router will use its algorithm (in which they use routing protocols to gather and share information of the current path among them) and it will re-route the previous network over another network in real-time. And this amazing capability and functionality to change paths in real-time over the network by sharing status among them is the key functionality of Dynamic Routing. [OSPF](https://www.geeksforgeeks.org/open-shortest-path-first-ospf-protocol-fundamentals/) (open shortest path first) and [RIP](https://www.geeksforgeeks.org/routing-information-protocol-rip/) are some protocols used for dynamic routing.

In the image above the upper image depicts the path _R1->R2->R5->R9->R10_ to take data from **R1** (source) to **R10** (destination) but, then due to some reason **R9** fails to process its work then it dynamically builds a new path which is _R1->R2->R5->R8->R10_.

Unlike the static routers in which the admin was there to reconfigure the change in the router, here it itself changes the route and finds the best network/path.

### **Working of Dynamic Routing**

![Working of Dynamic Routing](https://media.geeksforgeeks.org/wp-content/uploads/20211207133259/Workingofdynamicrouting-660x480.png)

**Working of Dynamic Routing**

**First,** A routing protocol (_a protocol that states how the information is going to share between routers and how are they going to communicate with each other to share/distribute information between nodes on a network_) must be installed in each router in the network to share information among each other.   
**Second,** it is started manually to go to the first routing table of the router with router information, and then after that it goes on automatically with the help of a dynamic routing algorithm and dynamically forms the routing table for the rest of the routers in the network.   
**Third,** then the routing information is exchanged among the routers so in case if the network goes down or the router fails to work and share information with its connected routers then the routing table of each router is modified correctly to that present condition so that it never fails to deliver information to the destination.   
**Fourth,** hosts are present to check or match the default gateway address to the IP addresses of the local router.

### Purpose 

Dynamic protocols were introduced to:

1. Explore every single path and choose the best path.
2. Sharing of information about the network with each other router present in the network.
3. Updating the path on its own and rerouting the best possible path.

### Components

There are three main components that were used in dynamic routing:

1. Data structure ( to structure information )
2. Algorithm ( to construct or re-update path )
3. The routing protocol ( to share information about the network )

### **Advantages**

1. Beneficial in Performance as well as scalable networking with a high frequency of data on nodes.
2. Makes fewer mistakes as it reroutes itself compared to other routing protocols.
3. No need to be manually configured by the admin.
4. Shares information about the network with each other makes them more reliable to work efficiently.

### **Disadvantages**

1. Requires more heavy and reliable powerful hardware.
2. Higher maintenance compared to static protocol

## Difference between Static and Dynamic Routing
Routing is a vital communication mechanism that governs how data packets travel from source to destination. Effective routing ensures that data is transferred across networks in an efficient, reliable, and timely manner. There are two main forms of routing: static and dynamic. In this article, we will discuss the differences between static and dynamic routing.

### What is Static Routing

[Static Routing](https://www.geeksforgeeks.org/types-of-routing/) is also known as ****non-adaptive**** routing which doesn’t change the routing table unless the network administrator changes or modifies them manually. Static routing does not use complex routing algorithms and It provides higher or more security than dynamic routing.   

![Static routing](https://media.geeksforgeeks.org/wp-content/uploads/20190517214641/Untitled-Diagram-103.png)

#### Advantages of Static Routing

- No routing overhead for the router [CPU](https://www.geeksforgeeks.org/difference-between-cpu-and-gpu/) which means a cheaper router can be used to do routing.
- It adds security because only an only administrator can allow routing to particular networks only.
- No bandwidth usage between routers.

#### Disadvantage of Static Routing

- For a large network, it is a hectic task for administrators to manually add each route for the network in the [routing table](https://www.geeksforgeeks.org/routing-tables-in-computer-network/) on each router.
- The administrator should have good knowledge of the topology. If a new administrator comes, then he has to manually add each route so he should have very good knowledge of the routes of the topology.

### What is Dynamic Routing

Dynamic routing is also known as ****adaptive**** routing which changes the routing table according to the change in topology. [Dynamic routing](https://www.geeksforgeeks.org/what-is-dynamic-routing-in-computer-network/) uses complex routing algorithms and it does not provide high security like static routing. When the network change(topology) occurs, it sends the message to the router to ensure that changes then the routes are recalculated for sending updated routing information.   

![Dynamic Routing](https://media.geeksforgeeks.org/wp-content/uploads/20190517214708/Untitled-Diagram-1110.png)

#### Advantages of Dynamic Routing

- Easy to configure.
- More effective at selecting the best route to a destination remote network and also for discovering remote networks.

#### Disadvantage of Dynamic Routing

- Consumes more [bandwidth](https://www.geeksforgeeks.org/what-is-bandwidth-definition-working-importance-uses/) for communicating with other neighbors.
- Less secure than static routing.

### Difference between Static and Dynamic Routing

| Static Routing                                                                                                                       | Dynamic Routing                                                           |
| ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------- |
| In static routing routes are user-defined.                                                                                           | In dynamic routing, routes are updated according to the topology.         |
| Static routing does not use complex routing algorithms.                                                                              | Dynamic routing uses complex routing algorithms.                          |
| Static routing provides high or more security.                                                                                       | Dynamic routing provides less security.                                   |
| Static routing is manual.                                                                                                            | Dynamic routing is automated.                                             |
| Static routing is implemented in small networks.                                                                                     | Dynamic routing is implemented in large networks.                         |
| In static routing, additional resources are not required.                                                                            | In dynamic routing, additional resources are required.                    |
| In static routing, failure of the link disrupts the rerouting.                                                                       | In dynamic routing, failure of the link does not interrupt the rerouting. |
| Less [Bandwidth](https://www.geeksforgeeks.org/what-is-bandwidth-definition-working-importance-uses/) is required in Static Routing. | More Bandwidth is required in Dynamic Routing.                            |
| Static Routing is difficult to configure.                                                                                            | Dynamic Routing is easy to configure.                                     |
| Another name for static routing is non-adaptive routing.                                                                             | Another name for dynamic routing is adaptive routing.                     |

### Conclusion
Routing is crucial that allows every network device across the world to share data with each other across internet. Shortest path is selected by the routing algorithms when routing a data packet. Routing Algorithms select the shortest path based on metrics like – hop count, delay, bandwidth etc. The core network device used in routing is router. Routes are stored in a logical data structure called – _**Routing Table**_ Static routing is a process in which we have to manually add routes to the routing table while In Dynamic Routing packets are transmitted over a network using various shortest path algorithms and pre-determined metrics.

## Abstraction
**Abstraction** -> Basically means to create something new in order to hide the implementation details of that thing.

## Objects
An **object** is a fundamental data structure used to store collections of data in the form of **key-value pairs**.
- The **key** (also called a property or field) is a unique identifier within the object. It's like a label for the data and is always a string (though in JavaScript, it can be written without quotes in most cases). The key is used to access the corresponding value associated with it.
- The **value** is the data or information that is stored in the object, and it can be any valid data type, including other objects, arrays, functions, strings, numbers, booleans, etc. This flexibility allows objects to be extremely versatile in how they are used.

For example in JavaScript:
```js
let person = {name: "John", age: 30, isEmployed: true };
```

In this object:
- `name`, `age`, and `isEmployed` are the **keys** (also known as properties).
- `"John"`, `30`, and `true` are the corresponding **values**.

Objects allow you to group related data together, making it easier to organize and manage. You can access and modify the values by referring to the keys. For example, `person.name` will give you `"John"`, and you can update `person.age = 31` to change the age.

Objects are crucial for representing complex data structures. For instance, a user profile might be represented as an object with properties like `username`, `email`, and `address`, where `address` itself might be an object with properties like `street`, `city`, and `zipCode`.

Objects are central, especially when working with more complex data structures like **JSON**, which is widely used to exchange data between a server and a client."