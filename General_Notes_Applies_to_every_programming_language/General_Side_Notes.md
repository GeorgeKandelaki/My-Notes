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

**Parameters** -> Function has parameters, which is a placeholder for incoming/given value/data. Parameters can be any Data Type or Any Expression. 

**Arguments** -> When we call/invoke a function it accepts arguments. In other words we give value/data to an function, which we then can use as a local variables in function code. Arguments can be any Data Type or Even an Expression.

**Return Value** -> Function can also return value/data using `return` keyword.

**Function:** A function is a reusable block of code that is defined once and can be executed whenever needed. This process is known as invoking or calling the function.
- **Parameters:** Functions can have parameters, which act as placeholders for the values or data that will be passed into the function when it is called. These parameters can be of any data type or expression.
    
- **Arguments:** When a function is called, you provide arguments, which are the actual values or data that correspond to the function's parameters. These arguments can also be of any data type or expression.
    
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

## Pure Functions
**Pure Functions** ->  A pure functions is a fundamental concept in functional programming and refers to a function that adheres to two main principles.
1. Deterministic Output:
	* A pure function always produces the same output given the same input. This mean that the function's return value is solely determined by its input parameters and nothing else.
2.  No Observable Side Effects:
	* A pure function does not cause any observable side effects. This implies that the function's execution does not alter any state or interact with the outside world(such as modifying a global variable, changing the state of an object, writing to a file, or printing to a console).

### Side Effects
**Side Effects** ->  A side effect refers to any change in the system's state or any observable interaction with external systems that occurs during the execution of a function or expression.
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