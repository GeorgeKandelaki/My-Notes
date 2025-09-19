## Data Types
### Strings
**String** -> String is an ordered sequence of characters. Strings underneath the hood are stored in memory as an ordered sequence of characters. These ordered characters are called **indexes**. 

We can access different part of the string using its index.  
`print("Pleas enter a number")`

### String Slicing
We can grab different part of the strings using indexes in square brackets  and then the index string([index]). The index is starting from 0 and ending at the strings length. We can choose different part of strings by backwards too. We just have to start index from negative like this [-1], [-2]. We will get the first character from the end of the string in other words the last character if we type [-1] and so on.

We can also choose where we want to start grabbing our string and where to stop it. If we want to just grab one character we just type index and it will stop on one character, but If we want multiple characters we need to specify where to stop grabbing. The syntax is for this is same as normal grabbing of string. square brackets starting index colon(:) and then stopping index ([start index:stop index]).

We also can stepover  the syntax is  square brackets starting index colon(:) and then stopping index and then colon (:) and after that stepover value  ([start index:stop index:stepover index]).

```python
text = "me me me"
	  # 01234567 <- index
print(text[0]) # <- grab the variable text and then from that variable text grab whatever is an index of 0 <- m

print(text[1:7:2]) 
print(text[-1])
print(text[::-1]) # <- for reversing string
```


### Boolean
**Boolean** -> Boolean in python is `bool`, There is only two options a bool can either be `true`  or `false`. 

Booleans represent the idea of true and false. It is kinda saying **0** and **1**. They are logical values, there is some logic that we can use.
We can use booleans to control the flow of our program.

In Boolean **1** means/equals **True**, while **0** equals/means to **False**.

Boolean can be **1** (True) or **0** (False).

### None
**None** -> None is a special data type, It represents the absence of the value. 

## Data Structures

**Data Structure** -> Data Structure it is way for us to organize information and data into  a let's say: box, folder or a cupboard, so that these data structures can be used with different advantages and disadvantages. 

In simple words we can think of Data Structures as a container around our data, that has different advantages and disadvantages of accessing data, removing data. writing data.  
### Lists === Arrays
### Lists 
**List** -> List is an ordered sequence of objects that can be of any type. It is a collection of items.

We create lists with square brackets ([]). We access the elements of an list using indexes, which starts from 0 and ends at the last element. 

We can grab different elements in lists using indexes. square brackets and then the index of an element.

```python
li = [1,"hello",3] # <- We created list
grabbed_value = li[0] # Output <- 1
```

We can also change the list. when we access a value at any index then we can change that to any data. Lists are mutable.

```python
li = [1,2,3]
li[0] = 5 # <- We mutated the list

```

### List Slicing
List slicing is same as strings we slice them with colons(:) inside of an square brackets ([]). We have start stop and stepover ([1:1:1]).

With list slicing we are creating new copy of the list. So we are creating entirely different list. When we slice the list it will create entirely new copy of an the actual list, we can then assign that list to a variable and use it as we like.

```python
li = [1,2,3]
new_li = sliced_list = li[1:1:1] # <- We created entirely different list
```

### Matrix
Matrix is a two dimensional list or multidimensional list. Which has the main list and the sub lists, In other words we have main array and the sub arrays. We can have another array/list inside of an sub list/array. We can have as much arrays/lists as we want inside of an the main array/list and sub arrays/list. We can access multi dimensional arrays/lists with normal list syntax. After we grabbed first list and we want to grab element in that array we will add another square brackets after the first ones and we can do this as many times as want. E.g `list[0][1]`.

```python
li = [ # <- Main List/Main Array
[1,2,3], # <- Sub List/Sub Array
[4,5,6], # <- Sub List/Sub Array
[7,8,9]  # <- Sub List/Sub Array
[[10],20,[30,[23]]] # <- Sub List/Sub Array and another array/list inside of an sub list/array
] 

li[0][1] # <- Accessing multi dimensional lists/arrays
```


### Dictionaries

**Dictionary** -> Dictionary is a collection/set of key value pairs, with the requirement that the keys are unique(within one dictionary). Unlike sequences, which are indexed by a range of numbers, dictionaries are indexed by keys, which can be immutable type. 

A Dictionary is an set/collection of unordered key value pair.

A pair of curly braces ({}) creates an empty dictionary.
Placing a comma separated list of key value pairs within the braces adds initial key value pairs to the dictionary;

We access dictionary value with the name of the dictionary and the square brackets (["key"]) next to it, In square brackets we write the key of the value we want to grab.

Dictionary Key needs to be immutable, keys can not change.
A key in a dictionary has to be unique, because there can only be one key, because that key is going to represent a value in that memory space. Key has to be something that only exists once, otherwise we overwrite it.

In Dictionaries the key/value pairs are called attributes or properties of that Dictionary.

```python
dictionary = {
"a": [1,2,3],
"b": "Hello",
"x": True,
}

my_list = [{
"a": [1,2,3],
"b": "Hello",
"x": True,
},
{
"a": [4,5,6],
"b": "Hello",
"x": True,
}]

print(dictionary["a"]) # <- We are accessing values of the dictionary using its keys
print(my_list[1]["a"][1]) # <- We are accessing values of dicitonary in the list with square brackets
```

### Tuples
**Tuples** -> A tuples is like lists, but unlike lists we can not modify them. We can think of them as immutable lists.

Tuples elements and tuple itself can not be mutated, Other than that we can do everything with tuple what we could do in lists.

we create tuples with parenthesis (). We access tuple values using indexes inside of the square brackets `[]`.

```python
my_tuple = (1,2,3,4,5)
my_tuple[1] = "z" # <- Not possible to mutate the element of the tuple and we can't mutate the whole tuple too
```

### Sets
**Set** -> Sets are simply an unordered collections of unique objects. 

In a set there is no duplicates, everything there should be unique.

We create sets with curly brackets, but instead of having key value pairs we have only values.

We access set values by using the square brackets, but set doesn't support indexing, so we have to grab the value using the item it holds.

```python
my_set = {1,2,3,4,5,5} # <- The second 5 will never get added to a set.
my_set.add(100) # <- .add() methods adds values to the set
my_set.add(2) # <- This won't get added because there is already a 2
```
## Expressions Vs Statements
An Expression is a piece of code that produces a value.

```python
iq = 100
user_age = iq / 5 # iq / 5 <- Expression
```

A Statement is an entire line of code, that performs some sort of action. 

```python
iq = 100 # iq = 100 <- Statement
user_age = iq / 5 # user_age = iq / 5 <- Statem ent
```

## Type Conversion

 
## Escape Sequence
Escape Sequence means that we want to make next coming string/character or anything count as a string, In short it means whatever come after that slash (Escape Sequence) It will mean that it is a string. And we do it by adding slash (\\). 

\\t -> Slash t Meant that whatever comes after that, tab will be added.
\\n -> Slash n moves string to a new line/next line
\\ -> Escape Sequence whatever comes after this slash it will mean that it counts as a string.

```python
weather = "It's \"kind of\" sunny"
tabbed = "\t It's \"kind of\" sunny
next_line = "\t It's \"kind of\" \n sunny"
```

## Formatted Strings
We define Formatted String with `f` and then string. We can type variables with curly braces ({variable_name}). In formatted string we can concatenate strings and variables without pluses or anything else, We just have to type variable names and expressions in curly braces (`{}`)

```python 
name = "George"
age = 15
print(f"hi {name}. You are {age} years old.")
```

## Mutability & Immutability
Immutability is when we can't change/reassign the value of an variable. Once created it exists like that in that form. 

In strings the only way to change it is to create something new.
String are immutable they can only be destroyed or created. They can't be changed, we can overwrite them if we want.

## Methods
Methods are a functions which are owned by something(any object). It is called with the dot (.) in front of them instead of the name only. Methods have to be owned.

```python
function() # <- Normal Function
something.function() # <- Method Function, It is invoked with the dot
```

## Conditional Logic

We define conditional logic using **`if`** Keyword, after the if keyword we write the condition and colon (:), then we do some indentation and write the instructions/actions we want python to do, in short whatever we want to do if that condition is true or false. 

indentation is needed for python to understands what code it should run.

We can also test for the second condition or even more using **`elif`** keyword, after that we write the condition we want to be true and colon(:), then we write the code we want to run with indentation.

We can also test for the false value of that condition using **`else`** keyword and then colons (:). 
It doesn't need any condition because it is meant for only if condition false.

else only runs if the **`if`** block of code evaluates to false.

If we want to test for two or more conditions together, we use the **`and`** keyword. first condition and keyword second condition. 
It checks if the all of the conditions are true, If one of the conditions come out to be false the whole if block will not run and go to else block code.

```python 
if condition:
	# Whatever we want to do if that condition is true
	print("Something")
elif condition:
	# Whatever we want to do if that condition is true
	print("Anything")
else: 
	# Whatever we want to do if that condition is false
	print("Nothing")

if condition1 and condition2 and condition3:
	print("Both are true")
```


## Truthy and Falsey Values
**Truthy** -> truthy value is a value, which will evaluate(come out) True If we run boolean type conversion on it. 

**Falsey** -> Falsey value is a value, Which will evaluate(come out) False If we run boolean type conversion on it.

Al value are considered "Truthy" except for the following, which are "Falsey":

```python
None
False
0
0.0
[] - an empty list
{} - an empty dict
() - an empty tuple
"" - an empty str
b"" - an empty bytes
set() - an empty set
an empty range, like range(0)
objects for which
	obj.__bool__() returns False
	obj.__len__() returns 0
```


## Ternary Operator

**Ternary Operator** ->  is still the same as the if/else statements, but it is a shortcut, so we can only use this on certain conditional logic. 

This can also be called conditional expressions. It is a expression, because it evaluates to a value. 
Conditional expression is an operation that evaluates to something based on the condition being true or not.

First we write the code we want to run if the condition is true, after that we write **`if`** keyword and then the condition we want to be true. Then we write the **`else`** keyword and the code we want to run if that first condition is false.
##### Syntax

```python
# condition_if_true if condition else conditino_if_false # <- Syntax
is_friend = True
can_message = "Message allowed" if is_friend else "Not allowed to message" # <- usiing ternary operator
```

## Short Circuiting
**Short Circuiting** -> Short Circuiting happens when the interpreter is smart enough to say: I already did enough work, I don't care what the next value is, this is just wasted work if I do it, so I'm going to short circuit it, and say: I'm going to just ignore this, and I'm going to start running the code. 

In Short whenever the interpreter finds the first true of false values (depends on what we want), it will stop looking at other value to see if it satisfies the condition(ignores the next conditions), it will just run the given code.

If we need to check if all values are true, we have to use **`and`** keyword. if any of the values are false it will get short circuited.

If we want to check if one of the values are true, we need to use **`or`** keyword. If it sees that one of the values are true then it will short circuit.

##### Syntax
```python
is_friend = True
is_User = True

# if condition2 or/and condition2 <- It will short circuit based on what the keywords do
if is_friend or is_user:
	print("Best friends forever")
```

## Logical Operators
**Logical Operator** is a keyword/something that allows us to perform logic between two things.

**`and`** -> We use and, when we want to check if the all values are true.
**`or`** -> We use or, when we want to check if at least one of the values from all is true.
**`not`** -> Not is the opposite of the boolean. If we write not true that means we want it to be false, on other hand if we write not false, it means we want it to be true.
 

```python
# Logical Operators
1. >
2. <
3. >=
4. <= 
5. == # <- Equal to
6. and # <- All values are true
7. or # <- Only One value of all is true
8. not # <- Not, Is the opposite of the boolean
9. ! # <-  Not Equal to
```


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


## Iterator
An Iterator is **an object that can be used to loop through collections**, like **ArrayList** and **HashSet**. It is called an "iterator" because "iterating" is the technical term for looping.

In computer programming, an **iterator** is an object that enables a programmer to traverse a container, particularly lists.

## Loops
**Loop** -> Loop allows us to run lines of code over and over again. That is really powerful because we can run code 1000 times even 1 million times. In short we use loops to repeatedly run same code how many times we want.

We define loops(for loops) writing the **`for`** keyword, after that we create a variable, and then we write the **`in`** keyword, next, we write the item we want to iterate over, then colon(:) and indentation on the next line, following with what code we want to run iterate. 

We call the item next to the **`in`** keyword an **iterable**.

An iterable allows us to use this notation of `for`, `variable`, `in` and iterable, to iterate over each item.  

Variable is created for each item after the in keyword(iterable), We are using that variable to iterate over the iterable. Also the created variable is iterating over each item in the given item. 

So for loops allow us to iterate over anything that has a collection of items. 
#### Syntax

```python 
for create_variable  in "item to loop over": # <- Iterating over string
	# Code We want to iterate
	print(create_variable)
	
for create_variable  in [1,2,3,4,5]: # <- Iterating over list
	# Code We want to iterate
	print(create_variable)
	
for create_variable  in (1,2,3,4,5): # <- Iterating over tupple
	# Code We want to iterate
	print(create_variable)
	
for create_variable  in [1,2,3,4,5]:
	# Code We want to iterate
	print(create_variable)
	
```

## What is NESTING in programming? -> GENERAL
In computer science and informatics, **nesting** is where information is organized in layers, or where objects contain other similar objects. It almost always refers to self-similar or recursive structures in some sense.

Nesting occurs when one programming construct is included within another. Nesting allows for powerful, yet simple programming. It reduces the amount of code needed, while making it simple for a programmer to debug and edit.

Different types of construct can be nested within another. For example, selection can be nested within a condition-controlled loop.

Nesting of code block, Means there are one code block inside the another code block .. The outer code block is also called parent block and inner code block is called child code block

## Functions
**Functions** -> A function is a fundamental construct in programming that represents a reusable block of code designed to perform a specific task or a related group of tasks. Functions help in organizing and structuring code by breaking down complex problems into smaller, manageable, and reusable sections. 

A function is a fundamental programming construct that encapsulates a block of code designed to perform a specific task. The key idea behind a function is **reusability**. Instead of writing the same code multiple times, you can write it once inside a function and then call that function whenever you need to perform that task.

A function is a fundamental construct in programming that encapsulates a block of code, which is designed to perform a specific task. The primary purpose of a function is to promote **reusability** and **modularity** in code. Instead of repeating the same code multiple times, you can write it once inside a function and then invoke that function whenever you need to perform that task.
### Reusability in Detail

**Reusability** means that a function can be used multiple times throughout a program without duplicating code. This concept not only saves time and effort but also ensures that your code is more manageable, maintainable, and less prone to errors.

We create function by writing **`def`** keyword, that lets the python interpreter know that we are about to define a function. def is short for define. 

At its core, a function is a reusable block of code designed to perform a specific task. This fundamental programming construct helps in organizing, structuring, and optimizing code by encapsulating a set of instructions that can be executed whenever needed.

### Reusability in Functions (Low-Level)

**Reusability** means that a function can be executed multiple times without rewriting the same code. This not only saves time and reduces errors but also makes the code more maintainable and easier to understand.

##### How Reusability Works

1. **Function Definition**: When you define a function, you are essentially creating a named block of code that can be invoked whenever required. This block of code is written once but can be executed many times.

2. **Function Invocation**: To execute the code inside the function, you call or invoke the function by its name, passing any necessary arguments.

3. **Parameters and Arguments**: Functions can accept input values known as parameters. These parameters act as placeholders for the actual values, called arguments, that will be passed when the function is invoked.
 
4. **Return Value**: Functions can return a value after execution, which can be used by the calling code. This returned value can be any data type, depending on what the function is designed to output.
 
////////////////////////////////////////////////////////////////////

### A Function Should Do One Thing Really Well.(For Good Practices and Performance.)


After that we give it a name and then we also add brackets to let the interpreter know, that this is something we are going to take an action on, or this is going to perform an action on a data type. At last colon (:) and we can write any instructions/code we want to do in that function block.

So we have created a function, we have defined it and now it is living somewhere in the memory on our machine, however in order to use a function we have to **Call** it with the brackets ( () ). 

So after the definition of an function, we write the name of the function that we gave it and after that write brackets next to the name of that function E.g.(**`name()`**) to run it. We grab a function from memory using the name we gave it, and then run it using the brackets( () ).

Functions allow us to keep our code DRY(Do Not Repeat Yourself) and reuse things that our machines can do over and over. 

We can have our custom action that we can take.

We need to make sure that we define functions at the beginning. If we call a function before it is written, Python will throw an error saying the function is not defined. This happens because the Python interpreter processes the code line by line. When it reaches the line with the function call, the function will not be defined yet if it appears later in the code. In other words, the function doesn't exist until the interpreter reaches its definition.
### Parameters
**Parameters** -> Parameters are variables that are defined as part of a function's definition. They act as placeholders for the values that will be passed to the function when it is called. Parameters are listed inside the parentheses following the function name and can be of any type (e.g., integer, string, list, dict)

For Example: 
```python
def greet(name):
	print(f"Hello {name}")
```

In this case `name` is a parameter.

**Defining Parameters** -> When we define a function, we specify its parameters within the parentheses. This allows the function to accept inputs. You can define as many parameters as you need, separated by commas.

**Using Parameters** -> Within the function, these parameters can be used like any other variable. They hold the values that are passed to the function when it is called.

```python
def add_numbers(a,b):
	return a + b
```

Here, `a` and `b` are parameters.
### Arguments 
**Arguments** -> Arguments are the actual values that are passed to the function when it is called. These values are supplied in the same order as the parameters defined in the function.

For Example:
```python
greet("Alice)
```

Here, `"Alice"` is an argument.

**Passing Arguments** -> When calling a function, you provide the arguments in the parentheses. These arguments replace the function's parameters, allowing the function to execute using these specific values.

**Types of Arguments** -> Arguments can be literals, variables, expressions, or even other function calls.
```python
result = add_numbers(5,3)
```
Here, `5` and `4` are arguments.

### Example Combining Both

Consider a function that calculates the area of a rectangle:
```python
def calculate_area(length, width):     return length * width
```

 **Parameters**: `length` and `width` are parameters defined when the function is created.
 
 **Arguments**: When calling the function, you might use: `calculate_area(10, 5)`, where `10` and `5` are arguments.

In this example:

- The function `calculate_area` is defined with two parameters, `length` and `width`.
- When the function is called with `calculate_area(10, 5)`, the values `10` and `5` are passed as arguments to the function, replacing the parameters `length` and `width`.
### Syntax
**Invoke** === **Call** 
```python
# name() <- Not like this the functin is not defined yet
def name (parameters): # <- As many parameters as we want and any type(list,dict)
	print("Code We want to run" parameters)
name(arguments) # <- Function Call <- We give arguments when we call the function
```


## return 
**return** -> return keyword returns whatever expression we give it.
We can assign the returned value to a variable and use it as we like it.

```python 
def sum(a,b):
	return a + b
total = sum(10,5)) # <- Output: 15	 
print(sum(10,total))

```

## What is Scope? GENERAL

Scope -> What variables do I have access to?

**Scope** -> Scope refers to the region of the code where a particular variable of function is accessible. It determines the visibility and lifetime of a variable or function. There are different types of scopes, including global scope, function scope, and block scope. 

**Scope** -> In programming, **scope** refers to the region of the program where a variable or a function is accessible. It determines the visibility and lifetime of a variable, function, or object. Scopes help manage the namespace in a program, ensuring that variables and functions do not conflict with each other and can be accessed appropriately.

## Types of Scopes
### 1. Global Scope

**Meaning:** Variables defined in the global scope are accessible throughout the entire program, including inside functions and blocks, unless shadowed by a local variable with the same name.

**How it Works:**

- In Python, a variable defined outside any function or block is in the global scope.
- In JavaScript, a variable declared with `var`, `let`, or `const` outside any function or block is in the global scope.
### 2. Function Scope

**Meaning:** Variables declared inside a function are accessible only within that function. They are not visible outside the function.

**How it Works:**

- In Python, variables declared inside a function are local to that function.
- In JavaScript, variables declared with `var` inside a function are local to that function.
### 3. Block Scope

**Meaning:** Variables declared inside a block (e.g., within `{}`) are only accessible within that block. This is specific to certain languages and keywords.

**How it Works:**

- In Python, there is no true block scope for variables declared with `var`; only function and module-level scopes exist. However, comprehensions and exception handling can introduce some block-like behavior.
- In JavaScript, variables declared with `let` or `const` inside a block are block-scoped.
### Detailed Explanation of How Scopes Work

1. **Scope Chain and Resolution:**
    
    - When a variable is referenced, the language runtime searches for the variable starting from the innermost scope and moves outward to the outer scopes until it finds the variable or reaches the global scope.
    - If the variable is not found in any scope, an error is thrown (e.g., `NameError` in Python or `ReferenceError` in JavaScript).
2. **Variable Shadowing:**
    
    - If a variable declared in an inner scope has the same name as a variable in an outer scope, the inner variable shadows the outer one within its scope.
    - The outer variable remains accessible outside the inner scope.
3. **Lexical Scoping (Static Scoping):**
    - Lexical scoping means that the scope of a variable is determined by its location within the source code, and nested functions have access to variables declared in their outer scope.
### Summary
- **Global Scope:** Variables are accessible everywhere in the code.
- **Function Scope:** Variables are accessible only within the function they are declared in.
- **Block Scope:** Variables declared within a block are accessible only within that block (specific to `let` and `const` in JavaScript).

Understanding scope is essential for writing robust and maintainable code, as it helps in managing variable visibility and lifetimes effectively.
## Types of Scopes in Python

### 1. Global Scope

**Definition:** The global scope refers to variables defined at the top level of a script or module, outside of any functions or classes. Variables in the global scope are accessible from any part of the code after their declaration, including inside functions and classes, unless shadowed by a local declaration.

**Characteristics:**

- Accessible throughout the entire script or module.
- Remain in memory for the lifetime of the program.
- Can be accessed and modified using the `global` keyword within functions.

### 2. Local Scope

**Definition:** Local scope refers to variables defined within a function or a method. These variables are only accessible within the function or method in which they are defined and do not exist outside of it.

**Characteristics:**

- Created when the function is called and destroyed when the function exits.
- Not accessible outside the function.
- Typically used for temporary data.

### 3. Enclosing Scope (Nonlocal Scope)

**Definition:** Enclosing scope refers to the scope of a function that contains another nested function. The nested function can access variables from its enclosing function's scope using the `nonlocal` keyword.

**Characteristics:**

- Useful for nested functions.
- The nested function can access and modify variables from its enclosing scope using `nonlocal`.

### 4. Built-in Scope

**Definition:** The built-in scope contains Python's built-in functions and names such as `len`, `print`, and `range`. These are always available in any part of the code.

**Characteristics:**

- Accessible from any scope within the program.
- Defined as part of the Python standard library.
### Scope Chain and Resolution
When a variable is referenced, Python searches for it in the following order (known as the LEGB rule):

1. **Local Scope**: The innermost scope, within the function where the variable is referenced.
2. **Enclosing Scope**: Any enclosing function's scope (in case of nested functions).
3. **Global Scope**: The module-level scope.
4. **Built-in Scope**: The outermost scope containing built-in functions and names.

If the variable is not found in any of these scopes, a `NameError` is raised.

### Variable Shadowing
Variable shadowing occurs when a variable declared in an inner scope has the same name as a variable in an outer scope. The inner variable shadows the outer one within its scope, making the outer variable inaccessible in that context.
### Lexical Scoping (Static Scoping)

Lexical scoping means that the scope of a variable is determined by its position in the source code, and nested functions have access to variables declared in their enclosing functions.
### Summary

- **Global Scope**: Variables are accessible throughout the entire script or module.
- **Local Scope**: Variables are accessible only within the function they are declared in.
- **Enclosing Scope**: Variables in an enclosing function are accessible to nested functions.
- **Built-in Scope**: Contains Python's built-in functions and names.

Understanding scope is essential for writing robust and maintainable code, as it helps manage variable visibility and lifetimes effectively, avoiding conflicts and unintended behaviors.

## Scope Chain
**Scope Chain** -> The scope chain refers to the process Python uses to resolve variable names in nested scopes. When a variable is referenced, Python follows a specific order to look up the variable's value. This order is known as the LEGB rule.

**Scope Chain** -> The **scope chain** is a fundamental concept in programming that describes the mechanism by which a program resolves variable names in nested scopes. It determines the order in which variable names are looked up and resolved when they are referenced in different parts of the code. This concept helps in understanding how a program manages the visibility and accessibility of variables across different levels of nested functions and blocks.
### Detailed Explanation of the Scope Chain

When you refer to a variable in your code, the programming language needs to determine what that variable refers to. The scope chain is the sequence of scopes that the language's interpreter or compiler searches through to find the variable's value. The search begins from the innermost scope and proceeds outward to the outer scopes, following a specific order.

#### LEGB stands for:
1. **Local Scope (L)**: The innermost scope, which is the scope within the current function.
2. **Enclosing Scope (E)**: The scope of any enclosing functions, which come into play for nested functions.
3. **Global Scope (G)**: The top-level scope of the current module or script.
4. **Built-in Scope (B)**: The outermost scope, which includes built-in functions and exceptions.

If a variable is not found in the local scope, Python moves outward to the enclosing scope, then to the global scope, and finally to the built-in scope. If the variable is not found in any of these scopes, Python raises a `NameError`.
### Summary

The scope chain is a crucial concept for understanding how variables are resolved in nested functions. The LEGB rule (Local, Enclosing, Global, Built-in) dictates the order in which Python searches for variable names. Understanding this rule helps in writing clear and bug-free code by ensuring that variables are accessed and modified in the intended scope.

### Scope Rules
 1. Start Checking with The Local Scope.
 2. Then Check The Parent Local Scope.
 3. After that, Check The Global Scope.
 4. At Last, Check Built In Python Functions.

## What is OOP (Object Oriented Programming)
**Everything in python is an Object**. 
This is possible because of **classes**.

**OOP (Object Oriented Programming)** -> Paradigm, Which is a way for us to think about our code and structure our code in a way, that is easier to maintain, extend, change and write. Well we break it up into small pieces, into little objects, that represents the real world.

**OOP** -> Is a paradigm, a way to think about our code, a way for us to structure our code, so that as it gets bigger and bigger, we are able to be organized, because we are not writing silly 10 line code, we are writing million lines of code.

Objects have methods and attributes, that you can access with the dot(.) method.

We are breaking up functionality and data into different pieces, that model the real world into separate objects. So, that different people could work on different parts and then we can just combine them afterwards. 

In python we can create our own data type(class) by simple writing **`class`** keyword, afterwards we can name it whatever we want, then at last we write colon (:), then we write code which should be indented.

class is like a blueprint, and from the **blueprint** we create actual objects, in other words we create **instances** of that class.

**Class** ->

**Instance** -> 

**Instantiate** -> 

we create objects  by writing class name and calling(invoking) it like a function **`Class()`**.

```python
class BigObject: # Defining class
# Add our Code
	pass 

obj1 = BigObject() # Instantiate
obj2 = BigObject() # Instantiate
obj3 = BigObject() # Instantiate
```

In OOP there is this idea of an class and then  an object.
Class is the blueprint, the blueprint of what we want to create, what are the basics attributes, that is properties that our class had, what are some basic methods or actions that our class can take.

From this blueprint, we are able to create different objects(instances) over and over, using class as an building block.

So this blueprint is what we call **class**, which we define with the **`class`** keyword. This class can be **Instantiated**, that is the action of creating different **instances**. 

All **instances** are objects.

## self keyword/parameter
**`self`** ->  parameter/keyword is a reference to the current instance of the class.


## 4 Pillars of OOP
* **Encapsulation** ->
* **Abstraction** ->
* **Inheritance** ->
* **Polymorphism** ->
### Encapsulation
**Encapsulation** -> Encapsulation is the binding of data and functions that manipulate that data, and we encapsulate into one big object, so that we keep everything in this box, that users or code or other machines can interact with. This data and functions are what we call attributes and methods. 

**Encapsulation** -> Encapsulation is the concept of bundling the data(attributes) and the methods(functions) that operate on that data into a single unit, known as an object. This principle helps to protect the internal state of the object from unintended interference and misuse by restricting direct access to some of the object's components. Instead, access to this data is controlled through well-defined interfaces (methods). By doing so, encapsulation promotes modularity and maintainability in code, allowing the internal implementation of an object to be changed without affecting other parts of the program that rely on the object.

### Abstraction
**Abstraction** -> An Abstraction means hiding of information or abstracting away information and giving access to only what's necessary. So whatever the user or the programmer or the machine is interested in, that's the only thing we give access to, everything else we king of hide it in a blanket underneath the hood, because our users don't have to worry about it. 

**Abstraction** ->

### Inheritance
**Inheritance** -> An Inheritance allows new objects to take on the properties of existing objects So we can inherit classes.

**Inheritance** ->

### Polymorphism
**Polymorphism** -> Polymorphism refers to a way in which object classes can share the same method name, but those method names can act differently based on what objects calls them.

**Polymorphism** ->


## MRO Method Resolution Order
**MRO Method Resolution Order** -> MRO is a rule, that python follows to determine which method to run. 

**MRO Method Resolution Order** -> The Method Resolution Order(MRO) is a crucial concept in Python, particularly in the context of multiple inheritance. It defines the order in which base classes are searched when invoking a method. This order determines which method is called if multiple classes in the inheritance hierarchy define a method with the same name. 
The MRO in Python applies not just to methods but to **all attributes**.
This means that when you access any attribute (methods, properties, variables, etc.) on an object, Python follows the MRO to determine where to look for that attribute.

## Functional Programming
**Functional Programming** -> Functional Programming is all about separation of concerns, which OOP does as well, it is all about packaging our code into separate chunks, so, that everything is well organized in each part of our code. Each part is organized in a way that makes sense, based on functionality. 

**Separation of Concerns** -> We mean, each part concerns itself with one thing that it is good at. 

Functional Programming also separates **data and functions**.

Functions operate on well defined data structures like lists and dictionaries, rather than belonging that data structure to an object.

The goal of functional programming paradigm is:
* Clear + Understandable Code
* Easy to extend
* Easy to maintain
* Memory Efficient
* DRY(Don't repeat yourself)

#### Pure Functions
**Pure Functions** ->  A pure functions is a fundamental concept in functional programming and refers to a function that adheres to two main principles.
1. Deterministic Output:
	* A pure function always produces the same output given the same input. This mean that the function's return value is solely determined by its input parameters and nothing else.
2.  No Observable Side Effects:
	* A pure function does not cause any observable side effects. This implies that the function's execution does not alter any state or interact with the outside world(such as modifying a global variable, changing the state of an object, writing to a file, or printing to a console).

#### Side Effects
**Side Effects** ->  A side effect refers to any change in the system's state or any observable interaction with external systems that occurs during the execution of a function or expression.
##### Summary:
- **Pure Functions**: Functions that produce the same output for the same input and do not cause any observable side effects.
- **Side Effects**: Any changes to the state or interactions with external systems that occur during the execution of a function, making the function's behavior dependent on contexts beyond its input parameters.
## Higher Order Function
**Higher Order Function** -> A Higher order function is a any function that accepts inside of its parameters another function or returns a function.

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

## Decorators
**Decorator** -> decorator is a function, that wraps another function and enhances it.

```python
# 154 Decorators PT2
def my_decorator(func):
	def wrap_func():
		print("**********")
		func()
		print("**********")
	return wrap_func

@my_decorator
def hello():
	print("hellloooo")

@my_decorator
def bye():
	print("see ya later")
  
hello()
bye()

hello2 = my_decorator(hello)
hello2()
```

## Generators
**Generator** -> A generator is a special type of thing in python, that allows us to use a special keyword called yield, and it can pause and resume functions.

**`yield`** Keyword pauses the function and the **`next(func)`** resumes the function.

```python
def gen_func(num):
	for i in range(num):
		yield i

next(gen_func) 

for item in gen_func(100):
	print(item)
```

## Regular Expressions
**Regular Expressions** -> A regular expression, is a sequence of characters that specifies a match pattern in text. Usually such patterns are used by string-searching algorithms for "find" or "find and replace" operations on strings, or for input validation. Regular expression techniques are developed in theoretical computer science and formal language theory.

```python
import re

# pattern = re.compile("this")
pattern = re.compile(r"([a-zA-Z]).([a])")
string = "search this inside of this text please"

a = pattern.search(string)
b = pattern.findall(string)
c = pattern.fullmatch(string)
d = pattern.match(string)

print(d)
```

## Machine Learning Model (ML)
**Machine Learning** -> Machine Learning is simply about predicting results based on the incoming data.

### Types Of Machine Learning
* **Supervised Learning** 
* **Unsupervised Learning** 
* **Reinforcement**

**Supervised Learning** -> Supervised learning is a type of machine learning where an algorithm from labeled training data to make predictions or decisions. It involves a teacher or supervisor (hence the term "supervised) that provide the algorithm with the correct output for given input during the training phase.

#### Key Components of Supervised Learning

1. **Labeled Data**:
    
    - Labeled data consists of input-output pairs, where each input (also known as a feature) is associated with a known output (label or target).
    - Example: In a dataset of house prices, the inputs might be features like the number of bedrooms, square footage, and location, while the output is the price of the house.
2. **Training Phase**:
    
    - During training, the algorithm is presented with labeled data and uses this data to learn the relationship between inputs and outputs.
    - The goal is to find a function fff that maps inputs XXX to outputs YYY, such that Y=f(X)Y = f(X)Y=f(X).
3. **Model**:
    
    - A model is the result of the training process, consisting of the learned parameters or structure that best captures the relationship between inputs and outputs.
    - Common types of models include linear regression, decision trees, and neural networks.
4. **Loss Function**:
    
    - The loss function measures the difference between the predicted output of the model and the actual output in the training data.
    - The objective of the training process is to minimize this loss function.
5. **Optimization Algorithm**:
    
    - An optimization algorithm adjusts the model parameters to minimize the loss function. Common optimization techniques include gradient descent and stochastic gradient descent.

#### Types of Supervised Learning

1. **Regression**:
    
    - Used when the output variable is continuous.
    - Example: Predicting house prices, where the output is a real number.
2. **Classification**:
    
    - Used when the output variable is categorical.
    - Example: Classifying emails as spam or not spam, where the output is a discrete label.

**Unsupervised Learning** -> Unsupervised learning is a type of machine learning where the algorithm learns patterns from unlabeled data. Unlike supervised learning, there are no explicit output labels provided to the algorithm. Instead, the algorithm tries to infer the underlying structure, patterns, or distribution in the data.

#### Key Components of Unsupervised Learning

1. **Unlabeled Data**:
    
    - The dataset consists of input data without corresponding output labels.
    - Example: A dataset of images without any labels indicating what each image contains.
2. **Learning Phase**:
    
    - During this phase, the algorithm analyzes the data to identify patterns, groupings, or structures within the data.
3. **Model**:
    
    - A model in unsupervised learning represents the learned structure or patterns from the data.
    - Common models include clustering algorithms, dimensionality reduction techniques, and association rule learning.
4. **Objective**:
    
    - The goal is not to predict specific outcomes but to explore the data and find interesting insights, groupings, or representations.

#### Types of Unsupervised Learning

1. **Clustering**:
    
    - Grouping data points into clusters where points in the same cluster are more similar to each other than to those in other clusters.
    - Example: Grouping customers into segments based on purchasing behavior.
2. **Dimensionality Reduction**:
    
    - Reducing the number of features in the data while preserving as much information as possible.
    - Example: Principal Component Analysis (PCA) reduces the dimensionality of data for visualization or preprocessing.
3. **Association Rule Learning**:
    
    - Finding interesting relationships or associations between variables in a dataset.
    - Example: Market basket analysis identifies products that frequently co-occur in transactions.

**Reinforcement** -> Reinforcement learning (RL) is a type of machine learning where a agent learns to make decision by performing actions in an environment to maximize cumulative rewards. Unlike supervised learning, where the model learns from labeled data, or unsupervised learning, where the model identifies patterns in unlabeled data, reinforcement learning is based on trial and error. The agent receives feedback in the form of rewards or penalties based on the actions it takes, which helps it learn the optimal strategy over time. 

#### Key Components of Reinforcement Learning

1. **Agent**:
    
    - The learner or decision-maker that interacts with the environment and takes actions.
2. **Environment**:
    
    - The external system the agent interacts with, which provides feedback in the form of rewards or penalties.
3. **State**:
    
    - A representation of the current situation of the environment. The state provides the necessary information for the agent to make decisions.
4. **Action**:
    
    - The set of all possible moves the agent can make in the environment.
5. **Reward**:
    
    - A scalar feedback signal received after taking an action. It indicates the immediate benefit of the action taken.
6. **Policy (π\piπ)**:
    
    - A strategy or mapping from states to actions that defines the agent's behavior. The policy can be deterministic or stochastic.
7. **Value Function**:
    
    - A function that estimates the expected cumulative reward of states (state value function) or state-action pairs (action value function, often called Q-value).
8. **Model (optional)**:
    
    - Some RL methods use a model of the environment to predict the next state and reward given a current state and action. This is known as model-based RL. In contrast, model-free RL methods do not use such models.

#### Types of Reinforcement Learning

1. **Model-Based vs. Model-Free**:
    
    - **Model-Based RL**: Uses a model of the environment to predict future states and rewards.
    - **Model-Free RL**: Learns the value function or policy directly from interactions with the environment without an explicit model.
2. **Value-Based vs. Policy-Based vs. Actor-Critic**:
    
    - **Value-Based Methods**: Focus on learning the value function (e.g., Q-learning).
    - **Policy-Based Methods**: Learn the policy directly without learning the value function (e.g., REINFORCE).
    - **Actor-Critic Methods**: Combine value-based and policy-based methods, where the actor updates the policy and the critic updates the value function.

## History Of Data
