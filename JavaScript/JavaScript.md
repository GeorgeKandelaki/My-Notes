JavaScript is a Static, low level, object oriented, Just in time compiled, Multi-paradigm, Single threaded  programming language. 
```javascript
console.log("FizzBuzz");
```

### What Is JavaScript
JavaScript, often abbreviated JS, is a programming language that is one of the ore technologies of the World Wide Web, alongside HTML and CSS. It lets us add interactivity to pages e.g. you might have seen sliders, alerts, click interactions, popups, etc on different websites - all of that is built using JavaScript. Apart from being used in the browser, it is also used in other non-browser environments as well such as Node.js for writing sever-side code in JavaScript, Electron for writing desktop applications, React Native for mobile applications and so on.

### History of JavaScript
JavaScript was initially created by Brendan Eich of NetScape and was first announced in a press release by NetScape in 1995. It has a bizarre history of naming; initially, it was name  Mocha by the creator, which was later renamed LiveScript. In 1996, about a year later after the release, NetScape decided to rename it to JavaScript with hopes of capitalizing on the Java community(although JavaScript did no have any relationship with Java) and released NetScape 2.0 with the official support of JavaScript.

### JavaScript Version
JavaScript, invented by Brendan Eich, achieved the status of an ECMA standard in 1997 and adopted the official name ECMAScript. This language has evolved through several versions, namely ES 1, ES 2, ES 3, ES 5, and the transformative ES 6. These update have played a crucial role in improving and standardizing JavaScript, making it widely used and valuable in the ever-changing field of web development.

### How to run JavaScript
JavaScript can be run in the browser by including the external script file suing the ***script*** tag, writing it within the HTML page using the ***script*** tag again, running it in the browser console or you can also user REPL.

### All about JavaScript Variables
Most of the time, a JavaScript application need to work with information. To store and represent this information in the JavaScript codebase, we use variables. A variable is a container for a value.

### Variable Declarations
To use variables in JavaScript, we first need to create it i,e declare a variable. To declare variables, we use on of the ***var***,  ***let***, or ***const***  keywords.

### Var
The ***var*** statement declares a function-scoped or globally-scoped variable, optionally initializing it to a value.

### Let Keyword
The ***let*** declaration declares a block-scoped local variable, optionally initializing it to a value.

### Const  Keyword
Constant are block-scoped, much like variables declare using the ***let*** keyword. The value of a constant can't be changed through reassignment(i.e by using the assignment operator), and it can't be redeclared (i.e through a variable declaration). However, if a constant is an object or array its properties or items an be updated or removed.



### Hoisting
JavaScript Hoisting refers to the process whereby the interpreter appears to move the declaration of function, variables, or classes to the top of their scope, prior to execution of the code

### Variable Naming Rules
A variable name should accurately identify your variable. When you create good variable names, your JavaScript code becomes easier to understand and easier to work with.
Properly naming variables is really important. JavaScript also has some rules when it comes to naming variables.

 * The first character must be a letter or and underscore (_). You can't use a number as the first character.
* The rest of the variable name can include any letter, any number, or the underscore. You can't use any other characters, including spaces, symbols, and punctuation marks.
* As with the rest if the JavaScript, variable names are case sensitive. That is, a variable named ***Interest_Rate***  is treated as an entirely different variable than one named ***interest_rate***.
* There is no limit to the length of the variable name.
* you can't use one of JavaScript's reserved words as a variable name. All programming languages have a supply of words that are used internally by the language and that can't be used for a variable names because doing so would cause confusion (or worse). Note, too, that JavaScript also has many keywords that should be avoided as well.

### Scopes
In JavaScript, scope refers to the visibility of a variable or how it can be used after it is declare. The scope of a variable depends on the keyword that was used to declare it.

The three types of Scope are Global Scope, Function Scope, and Block Scope, Before ES 6(2015), JavaScript had only Global Scope and Function Scope with the ***var*** keyword. ES 6 introduced ***let*** and ***const*** which allow Block Scope in JavaScript.

* ***Global Scope***: Variables declared outside any function or curly braces "***{}***" have Global Scope, and can be accessed from anywhere within the same JavaScript code. ***var***, ***let*** and ***const*** all provide this scope.

* ***Function Scope***: Variables declared within a function can only be used within that same function. Outside that function, they are undefined. ***var***, ***let*** and ***const*** all provide this Scope.

* ***Block Scope***: A block is any part of JavaScript code bounded by "***{}***". Variables declared within a block can not be accessed outside that block. This Scope is only provided by the ***let*** and ***const*** keywords. if you declare a variable within a block using var keyword. it will NOT have Block Scope.

* ***Local Scope***: Local Variables are only recognized inside their functions, variables with the same name can be used in different  functions. Local variables are created when a function starts, and deleted when the function is completed. ***var***, ***let*** and ***const*** all provide this Scope.

### Global Scope
Variables declared Globally (outside any function) have Global Scope. Global variables can be accessed from anywhere in a JavaScript program. Variables declared with ***var***, ***let*** and ***const*** are quite similar when declared outside a block.

### Function Scope
When a variable is declared inside a function, it is only accessible within that function and cannot be used outside that function.

### Block Scope
This cope restricts the variable that is declared inside a specific block, from access by the outside of the block. The ***let*** & ***const*** keyword facilitates the variable to be block scoped. In order to access the variables of that specific block, we need to create and object for it. Variables declared with the ***var*** keyword, do no have block scope.

### Primitive Types
In JavaScript, a primitive(primitive value, primitive data types) is a data that is not an object and has no methods or properties. There are 7 primitive data types:
* ***string***
* ***number***
* ***bigint***
* ***boolean***
* ***undefined***
* ***Symbol***
* ***null***
Most of the time, a primitive value is represented directly at the lowest level of the language implementations.

### Object
JavaScript object is a data structure that allows us to have key-value pairs; so we can have distinct keys and each key is mapped to a value that can be of any JavaScript data type. Comparing it to a real-world object, a pen is an object with several properties such as color, design, the material it is made of, etc. In the same way, JavaScript objects can have properties that define their characteristics.

### TypeOf Operator
You can use ***typeOf*** operator to find the data type of a JavaScript variable.


### Built-in objects
Built-in objects, or "global objects", are those built into the language specification itself. There are numberous bult-in objects with the JavaScript language, all of which are accessble at the global scope. Some examples are:
* ***Number***
* ***Math***
* ***Date***
* ***String***
* ***Error***
* ***Function***
* ***Boolean***


### Datatypes
Data type refers to the type of data that a JavaScript variable can hold. There are seven primitive data types in JavaScript (Number, Bigint, String, Boolean, Null, Undefined and Symbol).Objects are non-primitives.

### Type Casting
Type conversion(or typecasting) means the transfer of data from one data type to another. Implicit conversion happens when the compiler(for compiled languages) or runtime (for script languages like JavaScript) automatically converts data types. The source code can also explicitly require a conversion to take place.

### Type Conversion/Coercion
Type coercion is the automatic or implicit conversion of values from one data type to another (such as strings to numbers). Type conversion is similar to type coercion because they convert values from one data type to another with one key difference - type coercion is implicit. In contrast, type conversion can be either implicit or explicit.

### Implicit Type Casting
Implicit type conversion happens when the compiler or runtime automatically converts data types. JavaScript is loosely typed language and most of the time operators automatically convert a value to the right type

### Explicit Type Casting
Type casting means transferring data from one data type to another by explicitly specifying the type to convert the given data to. Explicit type casting is normally done to make data compatible with other variables. Examples of typecasting methods are ***parseInt()***, ***parseFloat()***, ***toString()***.

### Data Structures
A Data structure is a format to organize, manage and store data in a way that allows efficient access and modification. JavaScript has primitive (built-in) and non-primitive (not built-in) data structures. Primitive data structures come by default with the programming language and you can implement them out the box (like arrays and objects). Non=primitive data structures don't come by default and you have to code them up if you want to use them.

### Indexed collections
Indexed Collections are collection that have numeric indices i.e. the collections of data that are ordered by an index value. In JavaScript, an array is an indexed collection. An array is an ordered set of values that has a numeric index.

### Arrays
Arrays are objects that store a collection of items and can be assigned to a variable. They have their methods that can perform operations on the array.

### Structured data
Structured data is used by search-engines, like Google, to understand the content of the page, as well as to gather information about the web and the world in general. It is also code using in-page markup on the page that the information applies to.

### JSON
JavaScript Object Notation (JSON) is a standard text-based format for representing structured data based on JavaScript object syntax. It is commonly used for transmitting data in web application (e.g. sending some data from server to the client, so it can be displayed on a web page, or vice versa).


### Equality Comparisons
Comparison operators are used in logical statements to determine equality or difference between variables or values. Comparison operators can be used in condition statements to compare values and take action depending on the result.

### Value Comparison Operators
In JavaScript == operator does the type conversion of the operands before comparison, whereas the === operator compares the values and the data types of the operands. The ***Object.is()*** method determines whether two values are the same value: ***Object.is(value1, values2)***. 

***Object.is()*** is not equivalent to the == operator. The == operator applies various coercion to both sides (if they are not the same type) before testing for equality (resulting in such behavior as ***"" == false*** being true), but ***Object.is()*** doesn't coerce either value.

***Object.is()*** is also not equivalent to the === operator. The only difference between ***Object.is()*** and === is in their treatment of signed zeroes and ***NaN*** values. The === operator (and the == operator) treats the number values ***-0*** and ***+0*** as equal but treats ***NaN*** as not equal to each other.

### Loops and Iterations
Loops offer a quick easy way to do something repeatedly.

You can think of a loop as a computerized version of the game where you tell someone to take X steps in one direction, then Y steps in another. For example, the idea "Go five steps to the east" could be expressed this way as a loop:
```javascript
for(let step = 0; step < 5; stepp++){
// Runs 5 times, with values of step - throught 4.
console.log("Walking east one step);
}
```


### The for loop
he ***for*** loop is a standard control-flow construct in many programming languages, including JavaScript. It's commonly used to iterate over given sequence or iterate a known number of times and execute a piece of code for each iteration.

### do... while statement
The ***do... while*** statement creates a loop that executes a specified statement until the test condition evaluates to ***false***. The condition is evaluated after executing the statement, resulting in the specified statement executing at least once.

### while statement
The ***while*** statement creates a loop that executes a specified statement as long as the test condition evaluates to ***true***. The condition is evaluated before executing the statement.

### for... in statement
The ***for... in*** statement iterates over all enumerable properties of an object that are keyed by strings (ignoring ones keyed by Symbols), including inherited enumerable properties. 

### for... of statement
The ***for... of*** statement executes a loop that operates on a sequence of values sourced from an iterable object. Iterable objects include instances of built-ins such as Array, String, TypedArray, Map, Set, NodeList(and other DOM Collections), and the arguments object, generators produced by generator functions, and user-defined iterables.

### Break Continue
***break*** statement, without a label reference, can only be used to jump out of a loop or a switch block. 

***continue*** statement, with or without a label reference, can only be used too skip one loop iteration.


### Labeled Statements
JavaScript label statements are used to prefix a label to an identifier. It can be used with ***break*** and ***continue*** statement to control the flow more precisely.

A label is simply an identifier followed by a colon ***(:)*** that is applied to a block of code.

### Control Flow
In JavaScript, the ***Control Flow*** is a way of how your computer runs code from top to bottom. It starts from the first line and ends at the last line unless it hits any statement that changes the control flow of the program such as loop, conditionals,etc.

We can control the flow of the program though any of these control structures: 
* Sequential (default mode)
* Conditional Statements
* Exception Handling
* Loops and Iterations

### Conditional Statements
When you write code, you often want to perform different actions for different decisions. You can use conditional statements in your code to do this. In JavaScript, we have three conditional statements: ***if***, ***if...else***, and ***switch***.

### if else
The ***if*** statement executes a statement if a specified condition is ***truthy***. If the condition is ***falsy***, another statement in the optional ***else*** clause will be executed.

#### Example 
```javascript
if(condition){
	statement1;
} else {
	statement2;
}
```

### Switch Case
The ***switch*** statement evaluates an expression, matching the expression's value against a series of ***case*** clauses, and executes statements after the first ***case*** clause with a matching value, until a ***break*** statement is encountered. The ***default*** clause of a ***switch*** statement will be jumped to if no ***case*** matches the expression's value.

#### Example
```javascript
switch(expressions){
	case value1:
	// Statements executed when the result of experssion matches
	break;
	
	case value2:
	// Statements executed when the result of experssion matches
	break;

	...
	case valueN:
	// Statements executed when the result of experssion matches
	break;
	
	default:
	//Statements executed when none of the values match the value of the 
	//expression
	break;
	
}
```


### Exception Handling 
In JavaScript, all exceptions are simply objects. While the majority of exceptions are implementations of the global Error class, any old object can be thrown. With this in mind, there are two ways to throw an exception: directly via an Error object, and through a custom object.

### Throw Statement
The throw statement throws a user-defined exception. Execution of the current function will stop (the statements after throw won't be executed), and control will be passed to the first catch block in the call stack. If no catch block exists among caller functions, the program will terminate.

### Try, Catch, Finally
These are ways of handling errors in your JavaScript code. Inside the try code block we have the code to run, inside the catch block we handle the errors, and inside the finally block we have code that runs after the execution of the previous code blocks, regardless of the result.

### Utilizing error objects
When a runtime error occurs, a new ***Error*** object is created and thrown. With this ***Error*** object, we can determine the type of the Error and handle it according to its type.

#### Types of Errors:
Besides error constructors, JavaScript also has other core Error constructors.

* AggregateError
* EvalError
* InternalError
* RangeError
* ReferenceError
* SyntaxError

#### Example
```JavaScript
try {
	willGiveErrorSometime();
} catch (error) {
	if(error instanceof RangeError){
	rangeErrorHandler(error);
	} else if (error instanceof ReferenceError){
		referenceErrorHandle(error);
	} else {
		errorHandler(error);
	}
} 
```

### Expressions and Operators

At a high level, an expression is a valid unit of code that resolves to a value. There are two types of expressions those that have side effects (such as assigning values) and those that purely evaluate. The expression ***x = 7*** is an example of the first type. This expression uses the ***=*** operator to assign the value seven to the variable x. The expression itself evaluates to 7. The expression ***3 + 4*** is an example of the second type. This expressions uses the ***+*** operator to add ***3*** and ***4*** together and produces a value, ***7***. However, if it's not eventually part of a bigger construct (for example, a variable declaration like ***const z = 3 + 4*** ), its result will be immediately discarded ***—*** this is usually a programmer mistake because the evaluation does not produce any effects. As the examples above also illustrate, all complex expressions are joined by operators, such as ***=*** and ***+***. 

### Assignment Operators

An assignment operator assign a value to its left operand based on the value of its right operand. The simple assignment operator is equal (***=***), Which assigns the value of its right operand to its left operand. That is, ***x = f()*** assignment expression that assigns the value of ***f()*** to ***x***.


### Comparison Operators

Comparison operators are the operators that compare values and return ***true*** or ***false***. The operator include: ***>***, ***<***, ***>=***, ***<=***, == , === , ***!=***, and !== .

### Arithmetic Operators

The Arithmetic operators perform addition, subtraction, multiplication, division, exponentiation, and remainder operations. 

Arithmetic operators in JavaScript are as follows:
*  ***+*** - (addition)
*  ***-*** _ (Subtraction)
*  * - (Multiplication)
*  Double_Asterisks(**)-(Exponentiation) 
*  ***/*** - (Division)
*  ***%*** - (Modules i.e Remainder)
*  ***++*** - (Increment)
*  ***--*** _ (Decrement)

### Logical Operators
There are four logical operators in JavaScript: **||**(OR), **&&**(AND), **!**(NOT), **??**(Nullish Coalescing).

### String Operators
In addition to the comparison operators, which can be used on string values, the concatenation operator (**+**) concatenates two string values together, returning another string that is the union of the two operand string. 

The Shorthand assignment operator **+=** can also be used to concatenate string.

### Conditional Operators (Ternary Operator)
Conditional operator also known as Ternary Operator is the only JS operator that takes three operands.

The operator can have one of two values based on a condition.

##### Syntax
**condition ? val_for_true : val_for_false

### Comma operators
The comma operator (**,**) evaluates of its operands (from left to right) and returns the value of the last operand. This lets you create a compound expression in which multiple expressions are evaluated, with the compound expression's final value being the value of the rightmost of it's member expressions. This is commonly used to provide multiple parameters to a **for** loop.

### Unary Operators
JavaScript Unary Operators are the special operators that consider a single operand and perform all the types of operation on that single operand. These operators include unary plus, unary minus, prefix increments, postfix increments, prefix decrements, and postfix decrements.

### Functions
Functions exist so we can reuse code. They are blocks of code that execute whenever they are invoked. Each function is typically written to perform a particular task, like an addition function used to find the sum of two or more numbers. When numbers need to be added anywhere within your code, the addition function can be invoked as many times as necessary. Collectively, this whole group of code that defines a function in JavaScript is referred to as the ***function's definition***.

### Defining and Calling Functions

**Defining:**
* JavaScript function declarations are made by using the **function** keyword
* Functions can also be defined by saving function expressions to a variable. "Arrow" functions are commonly used in this way.
Collectively, this whole group of code that defines a function in JavaScript is referred to as the ***function's definition***.

 **Calling:** 
 * When a function is defined, it is not yet executed.
 * To call and invoke a function's code, use the function's name followed by parentheses: **functionName()**.

### Function Parameters
The parameter is the name given to the variable declared inside the definition of a function. There are two special kinds of syntax: default and rest parameters.

### Default Parameters
Default function parameters allow named parameters to be initialized with default values if no value or **undefined** is passed.

### Rest Parameters
The rest parameter syntax allows a function to accept an indefinite number of arguments as an array, providing a way to represent <u>variadic functions</u> in JavaScript.

### Arrow Functions
Arrow Function is a new way of creating functions with the '**=>**' operator with a shorter syntax.

### Built In Functions
* A JavaScript **method** is a property containing a **function definition** In  other words, when the data stored on an object is a function we call that a method.
* To differentiate between properties and methods, we can think of it this way: **A property is what an object has, while a method is what an object does.**
* Since JavaScript methods are actions that can be performed on objects, we first need to have objects to start with. There are several objects built into JavaScript which we can use.
### setTimeout
The setTimeout runs a function after the specified period expires. Times are declared in milliseconds.

### setInterval
The **setInterval()** method helps us to repeatedly execute a function after a fixed delay. It returns a unique interval ID which can later be used by the **clearInteval()** method, which stops further repeated execution of the function.

**setInterval()** is similar to setTimeout, with a difference. Instead of running the callback function once, it will run it forever, at the specific time interval you specify(in milliseconds):

### XMLHttpRequest
**XMLHttpRequest** (XHR) is a built-in browser object that can be used to interact with server. XHR allows you to update data without having to reload a web page. Despite the word XML in its name, XHR not only used to retrieve data with XML format, we can use it with any type of data, like JSON, file(s), and much more.

### Fetch
The fetch() method in JavaScript is used to request to the server and load the information on the webpages. The request can be of any APIs that return the data of the format JSON or XML. This method returns a promise.

### Prototypes
JavaScript is an object-oriented language built around a prototype model. In JavaScript, every object inherits properties from its prototype, if there are any. A prototype is simply an object from which another object inherits properties. To create complex programs using JavaScript, one has to be proficient in working with prototypes -- they form the very core of OOP in the language.

### Prototypal Inheritance
The Prototypal Inheritance is a feature in JavaScript used to add methods and properties in objects. It is a method by which an object can inherit the properties and methods of another object. Traditionally, in order to get and set the Prototype of an object, we use Object.getPrototypeOf and Object.setPrototypeOf.

### Keyed Collections
Keyed collections are data collections that are ordered by key not index. They are associative in nature. Map and set objects are keyed collections and are iterable in the order of insertion.

### Map
<u>Map</u> Is a collection of keyed data items, just like an **Object**. But the main difference is that **Map** allows keys of any type.

### Weak map
<u>WeakMap</u> is a Map-like collection of key/value pairs whose keys must be objects, it removes them once they become inaccessible by other means.

### Set
The **Set** object lets you store unique values of any type, whether <u>primitive</u> values or object references. A value in the **Set** may only occur once; It is unique in the **Set**'s collection.

### WeakSet
**WeakSet** objects are collection of objects. Just as with **Sets**, each object in a **WeakSet** may occur only once; all objects in a **WeakSet**'s collection are unique.

### Bitwise Operators
Bitwise operators treat arguments as 32-bits (zeros & ones) and work on the level of their binary representation. Ex. Decimal number **9** has a binary representation of **1001**. Bitwise operators perform their operations on such binary representations, but they return standard JavaScript numerical values.

Bitwise operators in JavaScript are as follows:
* **&** (AND)
* **|** (OR)
* **^** (XOR)
* **~** (NOT)
* **<<** (Left SHIFT)
* **>>** (Right SHIFT)
* **>>>** (Zero-Fill SHIFT)

### BigInt Operators
Most operators that can be used with the **Number** data type will also work with **BigInt** values (e.g. arithmetic, comparison, etc.). However, the unsigned right shift **>>>** operator is an exception and is not supported. Similarly, some operators may have slight differences in behavior (for example, division with **BigInt** will round towards zero).

### Relational Operators
Relational operators are also known as comparison operators. They are used to find the relationship between two values or compare the relationship between them; on the comparison, they yield the result true or false.

### IIFE
Immediately-Invoked Function Expression is a function that is executed immediately after it is created.

### Arguments object
The arguments object is an Array-like object accessible inside functions that contains the values of the arguments passed to that function, available within all non-arrow functions. You can refer to a function's arguments inside that function by using its arguments object. It has entries for each argument the function was called with, with the first entry's index at 0. But, in modern code, rest parameters should be preferred.

### Scope and function stack
#### Scope
A space or environment in which a particular variable or function can be accessed or used, Accessibility of this variable or function depends on where it is defined.

JavaScript has the following kinds of scopes:

* **Global Scope**: The default scope for all code running in script mode.
* **Module Scope**: The scope for code running in module mode.
* **Function Scope**: The scope created with a function.
* **Block Scope**: The scope created with a pair of curly braces (a block).

#### Function Stack (Call Stack)
The function stack is how the interpreter keeps track of its place in a script that calls multiple functions, like which function is currently executing and which function within that function are being called.

### Recursion
One of the most powerful and elegant concept of functions, recursion is when a function invokes itself. Such a function called a ***recursive function***. As recursion happens, the underlying code of the recursive function gets executed again and again until a terminating condition, called the base case, gets fulfilled. As you dive into the world of algorithms, you'll come across recursion in many many instances.

### Lexical Scoping
Before one can make an intuition of closures in JavaScript, it's important to first get the hang of the term '***lexical environment***'. In simple words, the lexical environment for a function **f** simply refers to the environment of enclosing that function's definition in the source code. Collectively, this whole group of code that defines a function in JavaScript is referred to as the ***function's definition***.

### Closures
Function closures are one of the most powerful, yet most misunderstood, concepts of JavaScript that are actually really simple to understand, A closure refers to a function along with its lexical environment. It is essentially what allows us to return a function **A**, from another function **B**, that remembers the local variables defined in **B**, even after **B**exits. The idea of closures is employed in nearly every other JavaScript program, hence it's paramount for a JavaScript developer to know it really well.

### Strict Mode
JavaScript's strict mode is a way to opt-in to a restricted variant of JavaScript, thereby implicitly opting out of "sloppy mode". Strict mode isn't just a subset: it intentionally has different semantics from regular code. Browsers not supporting strict mode will run strict mode code with different behavior from browsers that do, so don't rely on strict mode without feature-testing for support for the relevant aspects of strict mode. Strict mode code and non-strict mode code can coexist so that scripts can opt into strict mode incrementally. 

Strict mode makes several changes to normal JavaScript semantics:
* Eliminates some JavaScript silent errors by changing them to throw errors.
* Fixes mistakes that make it difficult for JavaScript engines to perform optimizations: strict mode code can sometimes run faster that identical code that's not strict mode.
* Prohibits some syntax likely to be defined in future versions of ECMAScript.
### This Keyword
In JavaScript, the **this** keyword is a little different compared to other languages. It refers to an object, but it depends on how or where it is being invoked. It also has some differences between strict mode and non-strict mode.

* In an object method, **this** refers to the object.
* Alone, **this** refers to the global object.
* In a function, **this** refers to the global object.
* In a function, in strict mode, **this** is undefined.
* In an event, **this** refers to the element that received the event.
* Methods like call(), apply(), and bind() can refer **this** to any object.

### this in a method
Methods are properties of an object which are function. This value of this inside a method is equal to the calling object. In simple words, this value in the object "before dot", the one used to call the method.

### this in a function
The keyword **`this`**  when used in a function refers to the global object. Note: in a browser window the global object is the **`window`** object.

### Using this alone
The keyword **`this`** when used alone refers to the global object. Note: In a browser window the global object is the **`window`** object.

### this in event handlers
The keyword **`this`** when used in an event handler refers to the element that received the event.

### this in arrow functions
The keyword **`this`** when used in an arrow function refers to the parent object.

### Function Borrowing
Function borrowing allows us to use the methods of one object on a different object without having to make a copy of that method and maintain it in two separate places. It is accomplished trough the use of **.call()**, **.apply()**, or **.bind()**, all of which exist to explicitly set this on the method we are borrowing.

### Explicit binding
Explicit binding is when you use the **call** or **apply** methods to explicitly set the value of **this** in a function. Explicit Binding can be applied using **call()**, **apply()**, and **bind()**. 


### Asynchronous JavaScript
Asynchronous programming is a technique that enables your program to start a potentially long-running task and still be able to be responsive to other events while that task runs, rather than having to wait until that task has finished. Once that task ha finished, your program is presented with the result.

Many functions provided by browsers, especially the most interesting ones, can potentially take a long time, and therefore, are asynchronous. For example:
* Making HTTP requests using **`fetch()`** 
* Accessing a user's camera or microphone using **`getUserMedia()`** 
* Asking a user to select files using **`showOpenFilePicker()`**

So even though you may not have to implement your own asynchronous functions very often, you are very likely to need to use them correctly.

### Callbacks
A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action.

### Promises 
Promises are a much better way to work with asynchronous code in JavaScript than the old and error-prone callback approach. They were introduced into JavaScript with ECMAScript 6. Using promises, we can manage extremely complex asynchronous code with rigorous error-handling setup, write code in a more or less synchronous style, and keep ourselves from running into the so-called callback hell.

### Callback Hell
The callback hell is when we try to write asynchronous JavaScript in a way where execution happens visually from top to bottom, creating a code that has a pyramid shape with many }) at the end.

### Async/Await

**`async.await`** is a special syntax to work promises in a more comfortable fashion. We use **`async`** keyword to declare a async function that return a promise, and the **`await`** keyword makes a function wait for a Promise.

### Working with APIs
When working with remote APIs, you need a way to interact with those APIs. Modern JavaScript provides two native ways to send HTTP requests to remote servers, **`XMLHttpRequest`** and **`Fetch`**.

### Classes
Classes are a template for creating objects. They encapsulate data with code to work on that data. Classes in JS are built on prototypes but have some syntax and semantics that are not shared with ES5 class-like semantics.

### Modules
Modules encapsulate all sorts of code like functions and variables and expose all this to other files. Generally, we use it to break our code into separate files to make it more maintainable. They were introduced into JavaScript with ECMAScript 6.

### CommonJS
CommonJS modules are the original way to package JavaScript code for Node.js. Node.js also supports the ESModules standard used by browsers and other JavaScript runtimes, but CJS is still widely used in backend Node.js applications. Sometimes these modules will be written with a .cjs extension.

### ECMAScript Modules
ESModules is a standard that was introduced with ES6 (2015). The idea was to standardize how JS modules work and implement these features in browsers. This standard is widely used with frontend frameworks such as react and can also be used in the backend with Node.js. Sometimes these modules will be written with a .mjs extension.

### Typed Arrays
In JavaScript, a typed array is an array-like buffer of binary data. There is no JavaScript property or object named TypedArray, but properties and methods can be used with typed array objects.

### Equality Algorithms
Equality Algorithms are used to perform equality comparisons of values or variables in JavaScript. Each equality algorithm works slightly differently, and the one you use depends on the type of comparison you want to make. 


### isLooselyEqual ( == )
<u>isLooselyEqual</u> ( == ) checks whether its two operands are equal, returning a **`Boolean`** result. It attempts to convert and compare operands that are of different types.

### isStrictlyEqual ( === )
<u>isStrictlyEqual</u> ( === ) checks whether its two operands are equal, returning a **`Boolean`** result. It always considers operands of different types to be different.

### Same value zero
<u>SameValueZero</u> equality determines whether two values are functionally identical in all contexts with +0 and -0 are also considered equal.

### Same value
<u>SameValue</u> equality determines whether two values are functionally identical in all contexts.

### Event Loop
The Event Loop is one of the most important aspects to understand about Node.js. Why is this so important? Because it explains how Node.js can be asynchronous and have no-blocking I/O, It explains the "killer feature" of Node.js, which made it this successful.

### JavaScript Iterators and Generators 
Iterators and generators, Introduced into JavaScript with ECMAScript 6, represent an extremely useful concept related to iteration in the language. Iterators are objects, abiding by the iterator protocol, that allows us to easily iterate over a given sequence in various ways, such as using the **`for...of`** loop. Generators, on the other hand, allow us to use functions and the **`yield`** keyword to easily define iterable sequences that are iterators as well.

### Memory Management
Low-level languages like C, have manual memory management primitives such as mallloc() and free(). In contrast, JavaScript automatically allocates memory when objects are created and frees it when they are not used anymore (garbage collection). This automaticity is a potential source of confusion: it can give developers the false impression that they don't need to worry about memory management.

### Memory lifecycle
Regardless of the programming language, the memory life cycle is pretty much always the same: 
* Allocate the memory you need
* Use the allocated memory (read,write)
* Release the allocated memory when it is not needed anymore

The second part is explicit in all languages. The first and last parts are explicit in low-level languages but are mostly implicit in high-level languages like JavaScript.


### Garbage Collection
Memory management in JavaScript is performed automatically and invisibly to us. We create primitives, objects, functions... All that takes memory. The main concept of memory management in JavaScript is reachability.