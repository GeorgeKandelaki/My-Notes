### The Intersection Observer API
To use the intersection observer API, we need to start by creating a new intersection observer.

```javascript
new IntersectionObserver(callback, options)
```

```javascript
const observer = IntersectionObserver(obsCallback, obsOptions);
```

Here, we will have to pass in a callback function and an object of options.

We have to use this observer to basically observe a certain target.
```javascript
observer.observe(element);
```
element is the target.
#### observer callback function
```javascript
const obsCallback = function(entries, observer){};
```

```JavaScript
// Examples
const obsCallback = function(entries,observer){
	entries.forEach(entry => {
	console.log(entry)
  })
}
```

This callback function will get called each time that the observed element, our target element, is intersecting the root element at the threshold that we defined.

Whenever the element, our target, is intersecting the viewport at 10%, viewport, because that is the root, and 10% because that is the threshold. So whenever that happens, then this function will get called and that does not matter if we are scrolling down or up.

function will get called with two arguments, and that is the entries and the observer object itself.
* **`entries`** are actually an array of the threshold entries.
* **`observer`** is the observer object

#### observer options

```javascript
const obsOptions = {
	root: null,
	threshold: [0, 0.2], // Can be any %. for example 10%
	rootMargin: "-90px" // Must be in pixels
}
```

In Options object:
* **First** we need `root` property. root is the element that the target is intersecting. we could select an element or as an alternative, we can write `null`, and then we will be able to observe our target element intersecting the entire viewport. 
* **Second** we can define `threshold`. This is basically the percentage of intersection at which the observer callback function will be called. We can have actually multiple thresholds. we can have an array. We can think of the **`threshold`** as the percentage of visibility we want to achieve in our root. (We can think of **`threshold`** at the percentage that we want to have visible in our root.)
* **`rootMargin`** is a box of any number you write(in this situation 90 pixels) that will be applied outside of our target element.

Callback will trigger each time that the target element moves completely out of the view, and also as soon as it enter the view.
That is because the callback function will be called when the `threshold`is passed when moving into the view and when moving out of the view.

### Object-Oriented Programming 
Object-oriented programming(OOP) is a programming paradigm based on the concept of objects;
* Paradigm is Style of code, "How" we write and organize code.
* We use objects to **model** (describe) real-world or abstract features;
  *  Real-world: E.g. user or to do list item
  * Abstract: E.g. HTML component or data structure
* Objects may contain data (properties) and code (methods). By using objects, we pack the **data and the corresponding behavior** into the block;
* In OOP, objects are **self-contained** pieces/blocks of code;
* Objects are **building blocks** of applications, and **interact** with one another;
* Interactions happen through a **public interface** (API): methods that the code **outside** of the object can access and use to communicate with the object;
* OOP was developed with the goal of **organizing** code, to make it **more flexible and easier to maintain** (avoid "spaghetti code")
#### Classes and Instances (Traditions OOP)
Class is like a blueprint from which we can create **new objects**. Class itself is not an object.

An Instance is a real object that we can use in our code, which was created from a class. Instance is **New Object created from the class. Like a real house created from an abstract blueprint.

The 4 fundamental principles of Object-Oriented Programming:

* Abstraction => Ignoring or hiding details that **don't matter**, allowing us to get an **overview** perspective of the thing we're implementing, instead of messing with details that don't really matter to our implementation.
* Encapsulation => Keeping properties and methods **private** inside the class, so they are **not accessible from outside the class**. Some methods can be **exposed** as a public interface (API).
  * Private properties and methods are NOT accessible from **outside** the class
  * Private properties and methods are STILL accessible from **within** the class!
* Inheritance => Making all properties and methods of a certain class **available to a child class**, forming a hierarchical relationship between classes. This allows us to **reuse common logic** and to model real-world relationships.  
* Polymorphism  => A child class can **overwrite** a method it inherited from a parent class [it's more complex that that, but enough for our purposes].
#### OOP In JavaScript
* Prototype =>  Contains methods and object can access that methods.
* Objects are linked to a prototype object;
* Prototypal inheritance: The prototype contains methods (behavior) that are **accessible to all objects linked to that prototype**
* Behavior is **delegated** to the linked prototype object.

### Asynchronous JavaScript, AJAX and APIs

#### Synchronous Code
Synchronous code means that  the code is executed line by line, in the exact order of execution that we defined in our code. 
* Code lines are executed in sequence. 
* Each line of code always **waits** for previous line to finish.
* Long-running operations **block** code execution.

#### Execution thread
Execution thread is part of the execution context, which does actually execute the code in the computer's processor.

#### Asynchronous code
Asynchronous code is executed **after a task that runs in the "background" finishes** execution. Coordinating behavior of a program over a period of time. Instead of blocking execution, it moves on right to the next line of the code immediately. So task will basically keep running in the background while performing the code that is inside of it;
* Asynchronous code is non-blocking;
* Execution doesn't wait for an asynchronous task  to finish its work;
* Callback functions alone do **NOT** make code asynchronous;
* `addEventListener` alone does **NOT** automatically make code asynchronous;

#### What are AJAX calls?
**A**synchronous **J**avaScript **A**nd **X**ML: Allows us to communicate with remote web servers in as **asynchronous way**. With AJAX calls, we can **request data** from web servers dynamically.

* With AJAX we can do an HTTP **request** which has data(Asking for some data)
* Server will set back a **response** containing that data that we requested(Sending data back).
* Everything happens **asynchronously** in the **background**. 
* When we are asking a server to send us some data the server usually contains a web **API** and this API is the one that has the data that we are asking for.

##### Request Type:
* GET: to **Receive** the data to a server.
* POST: to **Send** data to a server.
* etc.

#### What is an API?
**A**pplication **P**rogramming **I**nterface: Piece of software that can be used by another piece of software, in order to allow **applications to talk to each other**.
* There are many types of APIs in web development:
	* DOM API
	* Geolocation API
	* Own Class API
	* "Online" API  => Just "API" || Web API
* Objects made from a class can be seen as self contained encapsulated pieces of software that other pieces of software can interact with.

"Online" API: Application running on a server, that receives requests for data, and sends data back as response;

### What are Promises?
Promise: An object that is used as a placeholder for the future result of an asynchronous operation. => Less formal: Promise is a container for an asynchronously delivered value. => More less formal: Promise is a container for a future value.
##### Advantages
* We no longer need to rely on events and callbacks passed into asynchronous functions to handle asynchronous results.
* Instead of nesting callbacks, we can **chain promises** for a sequence of asynchronous operations: **escaping callback hell**.

#### The promise lifecycle
In the beginning we say that the promise is **pending** this is before any value resulting from the asynchronous task is available, during this time the asynchronous task is still doing its work in the background. 

Then, when the task finally finishes, we say that the promise is **settled**. In simple words settled means that a value and result from asynchronous operation is available. The Promise Is only settled **once**.

So from there the state will remain unchanged forever. Promise is either **fulfilled** or **rejected** but it is impossible to change that state.

When we use a promise to handle the result of an asynchronous operation, it is called **consuming a promise**. We consume a promise when we handle the result or error of the promise once it has been settler (resolved or rejected). For example, consuming a promise returned from the fetch API/

In order for a promise to exist first place, it must first be build, so it must be created. 
In a case of a fetch API, it is the fetch function that builds the promise and returns it for us to consume.

We are able **handle** these different states in our code.

There are 2 different types of settled promises: 1. Fulfilled Promises 2. Rejected Promises
* Pending => **Before** the future value is available.
* Settled => Asynchronous task **has finished**.
	1. Fulfilled Promises => A Fulfilled promise is a promise that has successfully resulted in a value. => Success! The value is now **available**.
	2. Rejected Promises => A Rejected promise means that there has been an error during the asynchronous task. => An **error** happened

* Consume Promise => When we already have a resolved value and we use it. E.g promise returned from Fetch API.


### JavaScript Runtime
**JavaScript Runtime** is basically a "Container" which includes all the different pieces that are necessary to execute JavaScript code.

* "Heart" of the every JavaScript Runtime is the **Engine**. This is Where code is actually executed and where objects are stored in memory. This two things happen in the **Call Stack** and in the **Heap**. 

* JavaScript has only one **thread** of execution and so it can only do **one** thing at a time. There is absolutely no multitasking happening in JavaScript itself.

* **Web APIs** Environment this are some APIs provided to the engine, but which are actually not part of the JavaScript language itself. E.g: DOM, Timers, fetch API, geolocation API and etc.

* **Callback Queue** is a data structure that holds all the ready to be executed callback functions that are attached to some event that has occurred. Callback Queue is basically an ordered list of all the callback functions that are in line to be executed.

* Finally, Whenever the Call Stack is empty the **Event Loop** takes Callbacks from the Callback queue and puts them in the Call Stack, So that they can be executed. So the **Event Loop** Is the essential piece that makes asynchronous behavior possible in JavaScript. It is the reason why we can have a non-blocking concurrency model. It decides when each callback function is executed.
  Event Loop looks into the Call Stack and determines whether its empty or not except global execution context, then if the stack indeed empty, which means that there is currently no code being executed, then it will take the first callback function from the callback queue and put it on the call stack to be executed. This is called event loop tick.
  
* **Callback Functions of Promises and related to Promises** will not be moved into the Callback queue, Instead callback functions of promises have a spacial queue for themselves, Which is so called **Microtasks Queue**.

* **Microtasks Queue** => Microtasks Queue is similar to the callback queue. Microtasks queue basically has priority over the callback queue. So at the end of event loop tick, after a callback function has been taken from the callback queue the event loop will check if there are any callback functions in the microtasks queue, If there are, it will run all of them before it will run anymore callback functions from the regular callback queue.
 
**Concurrency Model** Is how JavaScript handles multiple tasks happening at the same time.

This asynchronous tasks will all run in Web APIs environment of the browser.

### An Overview of Modules
**Module** is a reusable piece of code that **encapsulates** implementation details;

Modules are Usually a **standalone file**, but it doesn't have to be.

* Module can have **imports** and **exports**.
	* **export** => we can export values out of a module. E.g: Simple values or even entire functions. Whatever we export from a module is called a **Public API**.
	
* In the case of modules, this Public APIs are actually consumed by importing values into a module.
	* In modules we can usually also import values from other modules. 
	* This other modules which we import are the called **dependencies** of the importing module. Because the code that is in the module that is importing can not work without the code that it is importing from the external module
	
* **Compose Software** => Modules are small building blocks that we put together to build complex applications.

* **Isolate Components** => Modules can be developed in isolation without thinking about the entire codebase.
	* Each of the modules can be developed in entire isolation. Each engineer can actually work on different modules and on their own module without even understanding what the other engineers are doing and so without understanding how the entire final project works itself.

* **Abstract Code** => Implement low-level code in modules and import these abstractions into other modules

* **Organize Code** => Modules naturally lead to a more organized codebase.

* **Reuse Code** => Modules allow us to easily reuse the same code, even across multiple projects.

**ES6 Modules** are Modules which are stored in files, **exactly one module per file**.
* All **Top Level Variables** => are scoped to module. Basically variables are private to the module.
* **Default Mode** => ES6 Modules are always executed in **strict mode**.
* **Top-level this** => The **`this`** keyword is always undefined at the top-level.
* **Imports and Exports** => In modules we can import and export values between them, Using this  ES6  import and export syntax.
* **File Downloading** => Downloading modules files themselves this always automatically happens in an asynchronous way. This is true for an module loaded from HTML, as well as for modules that are loaded by importing one module into another using the import syntax.

Old School Script.
* All **Top Level Variables** => are always Global. This can lead to problems like global namespace pollution, where multiple scripts try to declare variables with the same name and then this variables collide.
* **Default Mode** => Script are always by default executed in "Sloppy" mode.
* **Top-level this** => In script **`this`** keyword points at the **window** object.
* **Imports and Exports** => In regular scripts importing and exporting values is just completely impossible.
* **File Downloading** => Regular Scripts are downloaded by default in an blocking(Synchronous) way, Unless we use a async or defer attributes on the script tag. 

Imports and exports Can **ONLY** happen at **Top-Level**. So outside of any function or any if block. 

Also all Imports are hoisted. No matter where in the code you are importing values, it is like the import statement will be move to the top of file. 

Importing values are the first thing that happens in modules.

To link a module to a HTML File we need to use the **script** tag with the **type** attribute set to **"module"**. Instead of just a plain script tag.

##### Importing modules before execution
Modules are **Imported synchronously**. 

Possible thanks to top-level("static") imports and exports, which make **imports and exports known before execution**.

This makes **bundling** and **dead code elimination** possible.

```html
<script type="module"></script>
```

#### How ES6 modules are Imported

##### Example
```javascript
import {rand} from './math.js';
import {showDice} from './dom.js';
const dice = rand(1,6,2);
showDice(dice);
```
index.js

So here we are importing a value called `rand` from math.js module and `showDice` from dom.js module. Now as always when a piece of code is executed the first step is to parse that code. This is the moment in which imports are hoisted. 

In fact the whole process of importing modules happens before the code in the main module is actually executed. 
 
So in this example index.js module imports the dom and the math modules in a synchronous way. What that means is that only after all imported modules have been downloaded and executed the main index.js module will finally be executed as well.

This is only possible because of top-level imports and exports, that's because if we only export and import values outside of any code that needs to be executed, then the engine can know all the imports and exports during the parsing phase. 
 
**Parse** => Parsing basically means to just read the code, but without executing it.

So after the parsing process has figured out which modules it needs to import, then this modules are actually downloaded from the server. After a module arrives it is also parsed and then the modules exports are linked to the imports in index.js. 

E.g: Math module exports a function called rand and this export is then connected to the rand import in the index.js module.

This connection is actually a live connection, so exported values **NOT** copied to imports. Instead the import is basically just a reference to the exported value, like a pointer.

When the value changes the exporting module then the same value also changes in the importing module. This unique to the ES6 JavaScript Modules, No other modules system, they don't work like this. 

The code in the imported modules is executed. With this the process of importing modules is finally finished, So now it is time for the importing module to be finally executed as well.(index.js) <= In this example.

Downloading actually happens in an asynchronous way, it is only the importing operation itself that happens in a synchronous way. 

### Writing Clean and Modern JavaScript
#### Readable Code
One of the most important things when we write code, is that we should write readable code, which basically means that you should write code so that others can understand it, and also, so that you can understand it yourself in the future.

Also we should try to avoid writing too clever and maybe over complicated solutions, that might make you feel really smart as a developer, but which also might make your code very confusing and unreadable. In many situations it is best to simply write the most straightforward solutions.

Another thing that is very important for readable code is to give functions and variable, very descriptive names.

For variables you should name them according to what they contain, and for functions you should name them according to what they do.

* Write code so that **others** can understand it.
* Write code so that **you** can understand it in 1 year.
* Avoid too "Clever" and over complicated solutions.
* Use descriptive variable names: **What they Contain**.
* Use descriptive function name: **What they Do**. 

#### General
There are some more general rules that we should follow in order to write modern and clean code, which are to use they DRY(Don't Repeat Yourself) principle. Which means that we should essentially refactor our code whenever we can.

Also, we should not pollute the global namespace, and instead, encapsulate our data into functions or classes or modules.

Also we shouldn't use var for declaring variables.We should always use strong type checks.

* Use DRY(Don't Repeat Yourself) principle (refactor your code)
* Don't pollute global namespace, encapsulate instead.
* Don't use var.
* Use strong type checks ( === and !== )

#### Functions
Writing functions, which is one of the most important things that we do as JavaScript developers, and the main rule that we should follow by writing functions is that each function should usually only do one thing.

Now many times of course we will want to break that rule, but in general it is good to keep this rule in mind, so that we always write like small functions, which only do one thing, but do it really well.

Next, we shouldn't use more than three parameters in a function. Also use default parameters in your functions whenever that is possible, and in general return the same data type as you received. E.g: if we receive two or three numbers as an input to a function, then probably you will want to return a number as well. That then makes more sense for when you use the function later. this is a rule that you can of course break.

We can and should use arrow functions whenever they make the code more readable.

* Generally, functions should do **only one thing**.
* Don't use more than 3 function parameters.
* Use default parameters whenever possible.
* Generally, return same data type as received.
* Use Arrow functions when they make code more readable.

#### OOP
In order to implement OOP in JavaScript, we should now use ES6 classes. 

When we design our classes we should encapsulate any data that shouldn't be accessible from the outside, so that you don't mutate that data from outside the class. 

Now probably we will still need to at least manipulate some data that is in the class, but for that we should then implement a public API. So basically a couple of methods that can then manipulate that data exactly as we want that to happen.

As we implement our methods in our classes, we should make sure that we implement chaining in all the methods where it will actually make sense. Because this can make your methods way easier to use, not only for you, but maybe also for other developers on your team. 

In regular objects when you are writing methods, then please don't use the arrow functions there. because by doing that, you will not get access to the this keyword of that object. 

* Use ES6 Classes.
* Encapsulate data and **don't mutate** it from outside the class.
* Implement method chaining.
* Do **not** use arrow functions as methods (in regular objects).

#### Avoid Nested Code
Writing nested code which basically means writing code inside of blocks inside of other blocks is really bad for readable code. We should avoid nested code at all costs.

One great way of avoiding nested code is to use guard clauses. Guard clauses basically, simply means to use an early return in case some condition is not met.

Also we can use ternary operator or even logical operators instead of an if statement, because the ternary operator of course doesn't create a new code block, while the if statement does. 

If we really do need if statement, then instead of an if/else-if statement you should use multiple if's instead, because this will make code a lot more readable than having to go through all this if and else if and else blocks.

Next, we should completely avoid any kind of loops, with that I mean any for loops, So the for and also the for...of loops should be avoided if you want to avoid the nested code. So instead we can use array methods like .map(), .filter() and .reduce().

We should avoid callback-based asynchronous APIs whenever you can.

* Use early **return** (guard clauses).
* Use ternary (conditional) or logical operators instead of **if**.
* Use multiple **if** instead of **if/else-if**.
* Avoid **for** loops, use array methods instead.
* Avoid callback-based asynchronous APIs.

#### Asynchronous Code
So for best readability always consume promises using async/await and not using the .then() and the .catch() methods. because this methods actually require callback functions, which then will introduce even more nested code, that is something we really want to avoid.

Something that is very important is that whenever we can we should run promises in parallel using the Promise.all() combinator function. So when we have two or more promises that can run at the same time, so promises that do not depend on each other, then we should run them in parallel.

We should always handle errors and promise rejections, this is simple the best practice for clean code.

* Consume promises with async/await for best readability.
* Whenever possible, run promises in **parallel** (Promise.all).
* Handle errors and promise rejections.

### Declarative and Functional JavaScript Principles


There are two fundamentally different ways of writing code (paradigms) in programming. Which we call paradigms.

These two paradigms are called imperative code and declarative code.
#### Imperative
Imperative -> Whenever we write imperative code, we basically need to explain to the computer how to do a certain things. So, basically, we need to explain every single step, that the compute need to follow in order to achieve a certain result. 

 * Programmer explains "**HOW to do things**".
 * We explain the computer every single step it has to follow to achieve a result.
 * **Example**: Step-by-Step recipe of a cake.
 
```javascript
const arr = [2,4,6,8];
const doubled = [];
for (let i = 0; i < arr.length; i++) 
	doubled[i] = arr[i] * 2;
```

#### Declarative 
On the other hand we have declarative programming, where the programmer tells the computer only what to do. When we write declarative code, we simply describe the way the the computer should achieve a certain result. But the how it should do it, so basically, the step  by step instructions, they get abstracted away, so we do not care about them. So simply describing the task, and the result that should be achieved is the declarative way of doing it.

 * Programmer tells "**WHAT to do**".
 * We simply describe the way the computer should achieve the result.
 * The **HOW** (Step-by-Step instructions) gets abstracted away.
 * **Example**: Description of a cake.

```javascript
const arr = [2,4,6,8];
const doubled = arr.map(n => n * 2);
```

#### Functional Programming Principles
Functional programming is basically a declarative paradigm, which is based on the idea of writing software, simply by combining multiple so called pure functions, while avoiding side effects and mutating data. Actually, functional, programming and writing declarative code, has now basically become the modern way of writing code in the JavaScript world.

* **Declarative** Programming paradigm
* Based on the idea of writing software by combining many **pure functions**, avoiding **side effects** and **mutating** data.
* 
**Side Effect** -> So, a side effect is basically simply a modification of any data that is outside of a function.  E.g mutating any variable that is external to the function is causing a side effect. So basically, any variable that is outside of the scope of the functions. 

Data does not only refer to variables, E.g logging stuff to the console, or also changing something in the DOM, is also causing side effects. 

**Pure Function** -> Pure function is a function without side effects. So, basically a function that does not mutate any external variables, and that does also not depend on any external variables. So basically, if we give the same inputs to a pure function, it will always return the same output and again, that is because it does not depend on any external variables, and it also does not manipulate them. 

Functional programming is about avoiding mutating data, and we do that by using something called immutability. 

In functional programming, state, which also means basically data is never modified. So in functional programming that state is never modified, Instead what we will do is to copy that object, so that state, and then it is that copy that is mutated, and can then be returned, but the original state is never touched. So that is what it means for the state being immutable, and the big upside of immutability is that, it makes it so much easier to keep track of how the data flows through our entire application. So ultimately, that will allow us to write better code, with less bugs, and code that is also more readable.  

**state** -> **data**.

* Side effect -> Modification (mutation) of any data **outside** of the function (mutating external variables, logging to console, writing to DOM, etc.)
* Pure Functions -> Functions without side effects. Does not depend on external variables. **Given the same inputs, always returns the same outputs**.
* Immutability -> State (data) is **never** modified! Instead, state is **copied** and the copy is mutated and returned.
* **Examples** -> React or Redux, are actually built around all of these principles. E.g: In react, the state is also completely immutable.

We can actually mix imperative and declarative programming in our own code, we don't have to go 100% declarative, or in other words, we don't have to go 100% in the direction of making our code completely functional. We can already start using, some of the functional programming techniques in our own code base.

So for examples, we can try to avoid data mutations as often as possible. And of course, this will not always be possible. 

Another thing we can do is to always prefer, built in methods or functions that do not produce side effects over the ones that do, and this i really important for data transformations.

So whenever you want to do that, you should use a method such as .map(), .filter(), and .reduce().

We Should try to avoid side effects into functions that you write yourself. and again, this is of course, not always possible, and also not always necessary. 

Declarative syntax -> functional programming is only a part of using and writing declarative code. In order to write code that is more declarative, we should use array and object destructuring whenever that is possible.

We should also use spread operator, the ternary operator and also template literals, whenever that is possible. So this operators are more about telling the code what to do and not exactly the steps that it should take. 

#### Functional Programming Techniques
*  Try to avoid data mutations.
* Use built-in methods that don't produce side effects.
* Do data transformations with methods such as .map(), .filter() and .reduce).
* Try to avoid side effects in functions this is of course not always possible.

#### Declarative Syntax
* Use array and object destructuring.
* Use the spread operator (...).
* Use the ternary (conditional) operator.
* Use template literals.


## Classes OOP
constructor function in JavaScript creates instances of the class and give them same keys but unique or different values. 

We should remember that constructor functions are called **every time we instantiate an object**.
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
