Now, for some explanations about the program itself. A C program, whatever its size, consists of functions and variables. A function contains statements that specify the computing operations to be done, and variables store values used during the computation. C functions are like the subroutines and functions in Fortran or the procedures and functions of Pascal. Our example is a function named `main`. Normally you are at liberty to give functions whatever names you like, but `main` is special - your program begins executing at the beginning of `main`. This means that every program must have a main somewhere. 

`main` will usually call other functions to help perform its job, some that you wrote, and others
from libraries that are provided for you. The first line of the program,



## Functions
One method of communicating data between functions is for the calling function to provide a list of values, called **arguments**, to the function it calls. The parentheses after the function name surround the argument list. In this example, main is defined to be a function that expects no arguments, which is indicated by the empty list ( ).

The statements of a function are enclosed in braces { }.
A function is called by naming it, followed by a parenthesized list of arguments, so this calls the function `printf` with the argument `"hello, world\n"`. `printf` is a library function that
prints output, in this case the string of characters between the quotes.



## Notations
The sequence `\n` in the string is **C notation** for the newline character, which when printed advances the output to the left margin on the next line.

Notice that `\n` represents only a single character. An escape sequence like `\n` provides a general and extensible mechanism for representing hard-to-type or invisible characters. Among the others that C provides are `\t` for tab, `\b` for backspace, `\` for the double quote
and `\\` for the backslash itself.


## Variables
In C, all variables must be declared before they are used, usually at the beginning of the function before any executable statements. A declaration announces the properties of variables; it consists of a name and a list of variables, such as
```c
int fahr, celsius;
int lower, upper, step;
```

The type int means that the variables listed are integers; by contrast with float, which means floating point, i.e., numbers that may have a fractional part. The range of both int and float depends on the machine you are using; 16-bits `ints`, which lie between -32768 and +32767, are common, as are 32-bit `ints`. A float number is typically a 32-bit quantity, with at least six significant digits and magnitude generally between about 10-38 and 1038.

## Data Types
### String
A sequence of characters in double quotes, like `"hello, world\n"`, is called a character string or string constant. Format for String is `%s`.

### Integer/int
Just a variable type, which holds/stores a number, integer. Format for int is `%d/%0...d`

### Float
Floating Point, which is a variable type, which  stores numbers that have a fractional part. Format for float is `%f/%0...f`.

### Char
Data Type used to store a Single Character. Forma for char is `%c`.

### Long
The character counting program accumulates its count in a long variable instead of an int. long integers are at least 32 bits. Although on some machines, int and long are the same size, on others an int is 16 bits, with a maximum value of 32767, and it would take relatively little input to overflow an int counter. The conversion specification `%ld` tells printf that the corresponding argument is a long integer.

### Double
It may be possible to cope with even bigger numbers by using a double (double precision float). Format for double is `%f/%0...f`.

## While Loop
The while loop operates as follows: The condition in parentheses is tested. If it is true (fahr is less than or equal to upper), the body of the loop (the three statements enclosed in braces) is executed. Then the condition is re-tested, and if true, the body is executed again. When the test becomes false (fahr exceeds upper) the loop ends, and execution continues at the statement that follows the loop. There are no further statements in this program, so it terminates. The body of a while can be one or more statements enclosed in braces, as in the temperature
converter, or a single statement without braces, as in

```c
while (i < j)
i = 2 * i;
```

## printf
`printf` is a general-purpose output formatting function. 

Its first argument is a string of characters to be printed, with each `%` indicating where one of the other (second, third, ...) arguments is to be substituted, and in what form it is to be printed. For instance, `%d` specifies an integer argument, so the statement 

```c
printf("%d\t%d\n", fahr, celsius);
```

Each % construction in the first argument of `printf` is paired with the corresponding second argument, third argument, etc.; they must match up properly by number and type, or you will get wrong answers.

```c
printf("%3.0f %6.1f\n", fahr, celsius);
```

The `printf` conversion specification `%3.0f` says that a floating-point number (here fahr) is to be printed at least three characters wide, with no decimal point and no fraction digits. `%6.1f` describes another number (celsius) that is to be printed at least six characters wide, with 1 digit after the decimal point. The output looks like this:

Width and precision may be omitted from a specification: `%6f` says that the number is to be at least six characters wide; `%.2f` specifies two characters after the decimal point, but the width is not constrained; and `%f` merely says to print the number as floating point.


## Arithmetic Operations
If an arithmetic operator has integer operands, an integer operation is performed. If an arithmetic operator has one floating-point operand and one integer operand, however, the integer will be converted to floating point before the operation is done.

`+` -> Increment Value.
`-` -> Decrement Value.
`*` -> Multiple Value.
`/` -> Divide Value.
`++` -> Increment By One(1).
`--` -> Decrement By One(1).
`==` -> Is Equal To.

## Operators
Expressions connected by && or || are evaluated left to right, and it is guaranteed that evaluation will stop as soon as the truth or falsehood is known.

**`||`** -> This Operator Means **OR**.
**`&&`** -> This Operator Means **ANDhe nature of the variable is stated but no storage is allocated.**
**`!`** -> The unary negation operator ! converts a non-zero operand into 0, and a zero operand in 1. A common use of ! is in constructions like.

C provides two unusual operators for incrementing and decrementing variables. The increment operator **`++`** adds 1 to its operand, while the decrement operator **`--`** subtracts 1.

## For Loop/Statement
The for statement is a loop, a generalization of the while. If you compare it to the earlier while, its operation should be clear. Within the parentheses, there are three parts, separated by semicolons. The first part, the initialization

`fahr = 017`

is done once, before the loop proper is entered. The second part is the test or condition that controls the loop:

`fahr <= 300`

This condition is evaluated; if it is true, the body of the loop (here a single `ptintf`) is executed. Then the increment step

`fahr = fahr + 20`

is executed, and the condition re-evaluated. The loop terminates if the condition has become false. As with the while, the body of the loop can be a single statement or a group of statements enclosed in braces. The initialization, condition and increment can be any expressions. The choice between while and for is arbitrary, based on which seems clearer. 

The for is usually appropriate for loops in which the initialization and increment are single statements
and logically related, since it is more compact than while and it keeps the loop control
statements together in one place.

## if, else if and else statements/Conditionals
```c
if (condition){
	// CODE
	n++;
} else if(condition){ //IF First if Condition doesn't work, then this will be checked and it is satisfies the condition the Code will be run.
	// CODE
	 n--;
} else { // IF none of them satisfies the Condition this will be run 100%; this is the last resort.
	// CODE
	n;
}
```

The `if` Statement tests the **parenthesized condition**, and if the condition is true, it **Executes the Statement (or Group Of Statements in Braces) that follows.

The pattern:
```c
if (condition1)
	statement1
else if (condition2)
	statement2
	...
	...
else
	statement3
```

The conditions are evaluated in order from the top until some condition is satisfied; at that point the corresponding statement part is executed, and the entire construction is finished. (Any statement can be several statements enclosed in braces.) If none of the conditions is satisfied, the statement after the final `else` is executed if it is present. If the final `else` and `statement` are omitted, as in the word count program, no action takes place. There can be any number of 

```c
else if(condition)
	statement
```

groups between the initial `if` and the final `else`.

## Symbolic Constants
It is bad practice to bury "magic numbers" like 300 and 20 in a program; they convey little information to someone who might have to read the program later, and they are hard to change in a systemic way. One way to deal with magic numbers is to give them meaningful names. A `#define` line defines a symbolic name or symbolic constant to be a particular string of characters.

`#define name replacment list`

Thereafter, any occurrence  of name (not in quotes and not part of another name) will be replaced by the corresponding replacement text. The name has the same form as a variable name: a sequence of letters and digits that begins with a letter. The replacement text can be any sequence of characters; it is not limited to numbers.

```c
#include <stdio.h>

#define LOWER 0
#define UPPER 300
#define STEP 20

main()
{
int fahr;

for (fahr = LOWER; fahr <= UPPER; fahr = fahr + STEP)
	printf("%3d %6.1f\n", fahr, (5.0/9.0)*(fahr-32));
	
}
```

The quantities `LOWER`, `UPPER` and `STEP` are symbolic constants, not variables, so they do not appear in declarations. Symbolic constant names are conventionally written in upper case so they can be readily distinguished from lower case variable names. Notice that there is no semicolon at the end of a `#define` line.

**Constant Expressions** -> A constant expression is an expression that involves only constants. Such expressions may be evaluated at during compilation rather than run-time, and accordingly may be used in any place that a constant can occur.

**String Constant** -> A string constant, or string literal, is a sequence of zero or more characters surrounded by
double quotes. 
The quotes are not part of the string, but serve only to delimit it. The same escape sequences used in character constants apply in strings; `\"` represents the double-quote character. String constants can be concatenated at compile time.

**Enumeration Constant** -> An enumeration is a list of constant integer values, as in: `enum boolean { NO, YES };`
The first name in an `enum` has value 0, the next 1, and so on, unless explicit values are specified. If not all values are specified, unspecified values continue the progression from the last specified value.
Names in different enumerations must be distinct. Values need not be distinct in the same enumeration.

## Character Input and Output
The model of input and output supported by the standard library is very simple. Text input or output, regardless of where it originates or where it goes to, is dealt with as streams of characters.

**Text Stream** -> A **Text Stream** is a sequence of characters divided into lines; each line consists of zero or more characters followed by a newline character.

It is the responsibility of the library to make each input or output stream confirm this  model; the C programmer using the library need not worry about how lines are represented outside the program.

The Standard Library Provides several functions for reading or writing one character at a time of which `getchar` and `putchar` are the simplest. Each time it is called, `getchar` reads the next input character from a text stream and returns that as its value. That is after

`c = getchar();`

the variable `c` contains the next character of input. The Characters normally come from keyboard.

The function `putchar` prints a character each time it is called:

`putchar(c)`

Prints the contents of the integer variable `c` as a character, usually on the screen. Calls to `putchar` and `printf` may be interleaved; the output will appear in the order in which calls are made.

### File Copying
Given `getchar` and `putchar`, you can write a surprising amount of useful code without knowing anything more about input and output. The Simplest example is a program copies its input to its output one character at a time:

`EOF` -> End Of Line.

```
read a character
	while (charater is not end-of-file indicator)
		output the character just read
		read a character
```

Converting this into C gives:

```c
#include <stdio.h>
/* copy input to output; 1st version */

int main()
{
	int c;

	c = getchar();
	while (c != EOF) {
		putchar(c);
		c = getchar();
	}
}
```

The relational operator != means "not equal to".

What appears to be a character on the keyboard or screen is of course, like everything else, stored internally just as a bit pattern. The type `char` is specifically meant for storing such character data, but any integer type can be used. We used `int` for a subtle but important reason.

The problem is distinguishing the end of input from valid data. The solution is that `getchar` returns a distinctive value when there is no more input, a value that cannot be confused with any real character. This value is called `EOF`, for end of **file**. We must declare `c` to be a type big enough to hold any value that `getchar` returns. We can't use char since `c` must be big enough to hold `EOF` in addition to any possible char. Therefore we use int.

`EOF` is an integer defined in `<stdio.h>`, but the specific numeric value doesn't matter as long as it is not the same as any `char` value. By using the symbolic constant, we are assured that nothing in the program depends on the specific numeric value. 

The program for copying would be written more concisely by experienced C programmers. In C, any assignment, such as

`c = getchar();`

is an expression and has a value, which is the value of the left hand side after the assignment. This means that a assignment can appear as part of a larger expression. If the assignment of a character to `c` is put inside the test part of a while loop, the copy program can be written this way:

```c
#include <stdio.h>
/* copy input to output; 2nd version */
main()
{
	int c;

	while ((c = getchar()) != EOF)
		putchar(c);
}		
```

The `while` gets a character, assigns it to `c`, and then tests whether the character was the End-Of-File signal. If it was not, the body of the `wile` is executed, printing the character. The `while` then repeats. When the end of the input is finally reached, the `while` terminates and does `main`.

This version centralizes the input - there is now only one reference to `getchar` - and shrinks the program. The resulting program is more compact, and, once the idiom is mastered, easier to read. You'll see this style often. (It's possible to get carried away and create impenetrable code, however, a tendency that we will try to curb.) The parentheses around the assignment, within the condition are necessary. The precedence of != is higher than that of =, which means that in the absence of parentheses the relational test != would be done before the assignment =. So the statement

`c = getchar() != EOF`

is equivalent to: 

`c = (getchar() != EOF)`

This has the undesired effect of setting `c` to 0 or 1, depending on whether or not the call of `getchar` returned end of file.

### Character Counting
```c
#include <stdio.h>
/* count characters in input; 1st version */
main()
{
	long nc;

	nc = 0;
	while (getchar() != EOF)
		++nc;
	printf("%ld\n")
}
```

The statement
`++nc;` presents a new operator, ++, which means increment by one. You could instead write `nc = nc + 1` but `++nc` is more concise and often more efficient. There is a corresponding operator `--` to decrement by 1. The operators `++` and `--` can be either prefix operators (++nc) or postfix operators (nc++); these two forms have different values in expressions, as will be shown in
Chapter 2, but ++nc and nc++ both increment nc. For the moment we will will stick to the prefix form.

The character counting program accumulates its count in a long variable instead of an int. long integers are at least 32 bits. Although on some machines, int and long are the same size, on others an int is 16 bits, with a maximum value of 32767, and it would take relatively little input to overflow an int counter. The conversion specification %ld tells printf that the corresponding argument is a long integer.

It may be possible to cope with even bigger numbers by using a double (double precision float). We will also use a for statement instead of a while, to illustrate another way to write
the loop.

```c
#include <stdio.h>
/* count characters in input; 2nd version */
main()
{
	double nc;

	for (nc = 0; gechar() != EOF; ++nc)
		;
	printf("%.0f\n", nc);
}
```

printf uses `%f` for both float and `double`; `%.0f` suppresses the printing of the decimal point and the fraction part, which is zero. The body of this for loop is empty, because all the work is done in the test and increment parts. But the grammatical rules of C require that a for statement have a body. The isolated semicolon, called a null statement, is there to satisfy that requirement. We put it on a separate line to make it visible.

Before we leave the character counting program, observe that if the input contains no characters, the while or for test fails on the very first call to `getchar`, and the program produces zero, the right answer. This is important. One of the nice things about while and for is that they test at the top of the loop, before proceeding with the body. If there is nothing to do, nothing is done, even if that means never going through the loop body. Programs should act intelligently when given zero-length input. The while and for statements help ensure that programs do reasonable things with boundary conditions.

### Line Counting
The next program counts input lines. As we mentioned above, the standard library ensures that an input text stream appears as a sequence of lines, each terminated by a newline. Hence,
counting lines is just counting newlines:

```c
#include <stdio.h>
/* count lines in input */
main()
{
	int c, nl;

	nl = 0;
	while ((c = getchar()) != EOF)
		if (c == '\n')
			++nl;
	printf("%d\n", nl);
}
```

The body of the while now consists of an if, which in turn controls the increment `++nl`. The if statement tests the parenthesized condition, and if the condition is true, executes the statement (or group of statements in braces) that follows. 

We have again indented to show what is controlled by what. The double equals sign == is the C notation for "is equal to" (like Pascal's single = or Fortran's .EQ.). This symbol is used to distinguish the equality test from the single = that C uses for assignment. A word of caution: newcomers to C occasionally write `=` when they mean `==`. the result is usually a legal expression, so you will get no warning.

A character written between single quotes represents an integer value equal to the numerical value of the character in the machine's character set. This is called a character constant, although it is just another way to write a small integer. So, for example, 'A' is a character constant; in the ASCII character set its value is 65, the internal representation of the character

A. Of course, 'A' is to be preferred over 65: its meaning is obvious, and it is independent of a particular character set.  The escape sequences used in string constants are also legal in character constants, so '\n' stands for the value of the newline character, which is 10 in ASCII. You should note carefully that `\n` is a single character, and in expressions is just an integer; on the other hand, `\n` is a string constant that happens to contain only one character.

### Word Counting

```c
#include <stdio.h>
#define IN 1
#define OUT 0

/* inside a word */
/* outside a word */
/* count lines, words, and characters in input */
main()
{
	int c, nl, nw, nc, state;

	state = OUT;
	nl = nw = nc = 0;

	while ((c = getchar()) != EOF) {
	++nc;
	if (c == '\n')
		++nl;
	if (c == ' ' || c == '\n' || c = '\t')
		state = OUT;
	else if (state == OUT) {
		state = IN;
		++nw;
		}
	}

	printf("%d %d %d\n", nl, nw, nc);
}
```

Every time the program encounters the first character of a word, it counts one more word. The variable state records whether the program is currently in a word or not; initially it is "not in a word", which is assigned the value OUT. We prefer the symbolic constants IN and OUT to the literal values 1 and 0 because they make the program more readable. In a program as tiny as this, it makes little difference, but in larger programs, the increase in clarity is well worth the modest extra effort to write it this way from the beginning. You'll also find that it's easier to make extensive changes in programs where magic numbers appear only as symbolic
constants.

The line: `nl = nw = nc = 0;` sets all three variables to zero. This is not a special case, but a consequence of the fact that an assignment is an expression with the value and assignments associated from right to left. 

It's as if we had written `nl = (nw = (nc = 0));` The operator `||` means OR, so the line `if (c == ' ' || c == '\n' || c = '\t')` says "if c is a blank or c is a newline or c is a tab'. (Recall that the escape sequence `\t` is a" visible representation of the tab character.) There is a corresponding operator `&&` for AND; its precedence is just higher than ||. Expressions connected by `&&` or `||` are evaluated left to right, and it is guaranteed that evaluation will stop as soon as the truth or falsehood is known.

If c is a blank, there is no need to test whether it is a newline or tab, so these tests are not made. This isn't particularly important here, but is significant in more complicated situations, as we will soon see. The example also shows an else, which specifies an alternative action if the condition part of an if statement is false. The general form is
```c
if (expression)
	statement1
else
	statement2
```

One and only one of the two statements associated with an if-else is performed. If the expression is true, `statement1` is executed; if not, `statement2` is executed. Each statement can be a single statement or several in braces. In the word count program, the one after the else is an if that controls two statements in braces.

## Loops
```c
for (i = 0; i != 10; i++)
	;
```

The body of this for loop is empty, because all the work is done in the test and increment
parts. But the grammatical rules of C require that a for statement have a body. The isolated semicolon, called a **`null` statement**, is there to satisfy that requirement. We put it on a separate line to make it visible.

## Arrays
**Array** -> 

Array subscripts always start at zero in C.

## Function
**Function** -> A function provides a convenient way to encapsulate some computation, which can then be used without worrying about its implementation.

We declare the parameter types and names, and the type of the result that the function returns. 

A function definition has this form:

```c
return-type function-name(parameter declarations, if any)
{
	BODY...
	declarations
	statements
}
```

Function definitions can appear in any order, and in one source file or several, although no function can be split between files. If the source program appears in several files, you may have to say more to compile and load it than if it all appears in one, but that is an operating system matter, not a language attribute. For the moment, we will assume that both functions are in the same file, so whatever you have learned about running C programs will still work.

There is a return type `void`, which states explicitly that no value is returned.

Any expression may follow return:

`return expression;`

**Body** -> A Body of a Function is the Code Written between Curly Braces({}). The Function Body Contains all Code that is Written in it, and Statements, Expressions, Loops, Declarations Definitions and Everything.

**Parameter** -> 
	Functions can have parameters, which act as placeholders for the Incoming values or data that will be provided/passed/given into the function when it is called/invoked.These parameters can be of any data type or expression. 
	The names used by function for its parameters are local to the Function, and are not visible to any other function: other routines can use the same names without conflict.
	The parameters are named between the parentheses, and their types are declared before opening the left brace; undeclared parameters are taken as int. (The body of the function is the same as before.)
	Parameters can be treated as conveniently initialized local variables in the called routine.

**Argument** -> When a function is called, you provide/pass/give arguments, which are the actual values or data that correspond to the function's parameters. These arguments can also be of any data type or expression.

**Return Value**	-> A function need not return a value; a return statement with no expression causes control, but no useful value, to be returned to the caller, as does `falling off the end` of a function by reaching the terminating right brace. And the calling function can ignore a value returned by a function.

### Arguments Call By Value
One aspect of C functions may be unfamiliar to programmers who are used to some other languages, particularly Fortran. In C, all function arguments are passed **by value**. This means that the called function is given the values of its arguments in temporary variables rather than the originals. 

This leads to some different properties than are seen with **call by reference** languages like Fortran or with var parameters in Pascal, in which the called routine has access to the original argument, not a local copy.

Call by value is an asset, however, not a liability. It usually leads to more compact programs with fewer extraneous variables, because parameters can be treated as conveniently initialized local variables in the called routine. For example, here is a version of power that makes use of this property.

```c
/* power: raise base to n-th power; n >= 0; version 2 */
int power(int base, int n)
{
	int p;

	for (p = 1; n > 0; --n)
		p = p * base;
	return p;
}
```

The parameter `n` is used as a temporary variable, and is counted down (a for loop that runs backwards) until it becomes zero; there is no longer a need for the variable `i`. Whatever is done to `n` inside power has no effect on the argument that power was originally called with. When necessary, it is possible to arrange for a function to modify a variable in a calling routine. The caller must provide the address of the variable to be set (technically a pointer to the variable), and the called function must declare the parameter to be a pointer and access the
variable indirectly through it.

The story is different for arrays. When the name of an array is used as an argument, the value passed to the function is the location or address of the beginning of the array - there is no copying of array elements. By subscripting this value, the function can access and alter any argument of the array. This is the topic of the next section.

## External Variables and Scope
The variables in main, such as line, longest, etc., are private or local to main. Because they are declared within `main`, no other function can have direct access to them. The same is true of the variables in other functions; for example, the variable i in `getline` is unrelated to the `i32` in copy. 

**Automatic Variables** -> Each local variable in a function comes into existence only when the function is called, and disappears when the function is exited. This is why such variables are usually known as automatic variables, following terminology in other languages.

We will use the term automatic henceforth to refer to these local variables. Because automatic variables come and go with function invocation, they do not retain their values from one call to the next, and must be explicitly set upon each entry. If they are not set, they will contain garbage.

As an alternative to automatic variables, it is possible to define variables that are external to all functions, that is, variables that can be accessed by name by any function. (This mechanism is rather like Fortran COMMON or Pascal variables declared in the outermost block.) Because external variables are globally accessible, they can be used instead of argument lists to communicate data between functions. Furthermore, because external variables remain in existence permanently, rather than appearing and disappearing as functions are called and exited, they retain their values even after the functions that set them
have returned. An external variable must be defined, exactly once, outside of any function; this sets aside storage for it. 

The variable must also be declared in each function that wants to access it; this states the type of the variable. The declaration may be an explicit `extern` statement or may be implicit from context. To make the discussion concrete, let us rewrite the longest-line program with line, longest, and max as external variables. This requires changing the calls, declarations, and bodies of all three functions.
```c
#include <stdio.h>

#define MAXLINE 1000

int max;
char line[MAXLINE];
char longest[MAXLINE];

int get_line(void)
{
	int c, i;
	extern char line[];

	for (i = 0; i < MAXLINE - 1 && (c = getchar()) != EOF && c != '\n'; ++i)
		line[i] = c;

	if (c == '\n')
	{
		line[i] == c;
		++i;
	}
	line[i] = '\0';
	return i;
}

void copy(void)
{
	int i;
	extern char line[], longest[];

	i = 0;
	while ((longest[i] = line[i]) != '\0')
		++i;
}

int main()
{
	int len;
	extern int max;
	extern char longest[];

	max = 0;
	while ((len = get_line()) > 0)
		if (len > max)
		{
			max = len;
			copy();
		}

	if (max > 0)
		printf("%s", longest);

	return 0;
}
```

The external variables in main, `getline` and copy are defined by the first lines of the example above, which state their type and cause storage to be allocated for them. Syntactically, external definitions are just like definitions of local variables, but since they occur outside of functions, the variables are external. Before a function can use an external variable, the name of the variable must be made known to the function; the declaration is the same as before except for the added keyword `extern`.

In certain circumstances, the `extern` declaration can be omitted. If the definition of the external variable occurs in the source file before its use in a particular function, then there is no need for an `extern` declaration in the function. The `extern` declarations in main, `getline` and copy are thus redundant. In fact, common practice is to place definitions of all external variables at the beginning of the source file, and then omit all `extern` declarations. If the program is in several source files, and a variable is defined in `file1` and used in `file2` and `file3`, then `extern` declarations are needed in `file2` and `file3` to connect the occurrences of the variable. 

The usual practice is to collect `extern` declarations of variables and functions in a separate file, historically called a header, that is included by `#include` at the front of each source file. The suffix .h is conventional for header names. The functions of the standard library, for example, are declared in headers like <stdio.h>. 

Since the specialized versions of `getline` and copy have no arguments, logic would suggest that their prototypes at the beginning of the file should be `getline()` and `copy()`. But for compatibility with older C programs the standard takes an empty list as an old-style declaration, and turns off all argument list checking; the word void must be used for an explicitly empty list. 

You should note that we are using the words definition and declaration carefully when we refer to external variables in this section. **Definition** refers to the place where the variable is created or assigned storage; **declaration** refers to places where the nature of the variable is stated but no storage is allocated.

By the way, there is a tendency to make everything in sight an `extern` variable because it appears to simplify communications - argument lists are short and variables are always there when you want them. But external variables are always there even when you don't want them. Relying too heavily on external variables is fraught with peril since it leads to programs whose data connections are not all obvious - variables can be changed in unexpected and even inadvertent ways, and the program is hard to modify. 

The second version of the longest-line program is inferior to the first, partly for these reasons, and partly because it destroys the generality of two useful functions by writing into them the names of the variables they
manipulate.

## Expressions

## Enumeration
**Enumeration Constant** -> An enumeration is a list of constant integer values, as in: `enum boolean { NO, YES };`
The first name in an `enum` has value 0, the next 1, and so on, unless explicit values are specified. If not all values are specified, unspecified values continue the progression from the last specified value.

Names in different enumerations must be distinct. Values need not be distinct in the same enumeration.

Enumerations provide a convenient way to associate constant values with names, an alternative to `#define` with the advantage that the values can be generated for you. Although variables of `enum` types may be declared, compilers need not check that what you store in such a variable is a valid value for the enumeration. Nevertheless, enumeration variables offer the chance of checking and so are often better than `#defines`. In addition, a debugger may be able to print values of enumeration variables in their symbolic form.

## Declarations
All variables must be declared before use, although certain declarations can be made implicitly by content. A declaration specifies a type, and contains a list of one or more
variables of that type, as in
```c
int lower, upper, step;
char c, line[1000];
```

Variables can be distributed among declarations in any fashion; the lists above could well be written as
```c
int lower;
int upper;
int step;
char c;
char line[1000];
```

The latter form takes more space, but is convenient for adding a comment to each declaration for subsequent modifications. A variable may also be initialized in its declaration. If the name is followed by an equals sign and an expression, the expression serves as an initializer, as in
```c
char esc = '\\';
int
i = 0;
int
limit = MAXLINE+1;
float eps = 1.0e-5;
```

If the variable in question is not automatic, the initialization is done once only, conceptionally before the program starts executing, and the initializer must be a constant expression. An explicitly initialized automatic variable is initialized each time the function or block it is in is entered; the initializer may be any expression. External and static variables are initialized to zero by default. Automatic variables for which is no explicit initializer have undefined (i.e., garbage) values. 

The qualifier const can be applied to the declaration of any variable to specify that its value will not be changed. For an array, the const qualifier says that the elements will not be
altered.
```c
const double e = 2.71828182845905;
const char msg[] = "warning: ";
```

The `const` declaration can also be used with array arguments, to indicate that the function does not change that array:
`int strlen(const char[]);40`

The result is implementation-defined if an attempt is made to change a const.

## Type Conversion
**Type Conversion** -> When an operator has operands of different types, they are converted to a common type according to a small number of rules.

In general, the only automatic conversions are those that convert a "narrower" operand into a "wider" one without losing information, such as converting an integer into floating point in an expression like f + i. Expressions that don't make sense, like using a float as a subscript, are disallowed. Expressions that might lose information, like assigning a longer integer type to a shorter, or a floating-point type to an integer, may draw a warning, but they are not illegal.

A char is just a small integer, so chars may be freely used in arithmetic expressions. This permits considerable flexibility in certain kinds of character transformations.

There is one subtle point about the conversion of characters to integers. The language does not specify whether variables of type char are signed or unsigned quantities. When a char is converted to an int, can it ever produce a negative integer? The answer varies from machine to machine, reflecting differences in architecture. On some machines a char whose leftmost bit is 1 will be converted to a negative integer ("sign extension"). On others, a char is promoted to an int by adding zeros at the left end, and thus is always positive. 

The definition of C guarantees that any character in the machine's standard printing character set will never be negative, so these characters will always be positive quantities in expressions. But arbitrary bit patterns stored in character variables may appear to be negative on some machines, yet positive on others. For portability, specify signed or unsigned if non-character data is to be stored in char variables.

Implicit arithmetic conversions work much as expected. In general, if an operator like + or * that takes two operands (a binary operator) has operands of different types, the "lower" type is promoted to the "higher" type before the operation proceeds. The result is of the integer type.

If there are no **`unsigned`** operands, however, the following informal set of rules will suffice:

* If either operand is long double, convert the other to long double.
* Otherwise, if either operand is double, convert the other to double.
* Otherwise, if either operand is float, convert the other to float.
* Otherwise, convert char and short to int.
* Then, if either operand is long, convert the other to long.

Conversion rules are more complicated when unsigned operands are involved. The problem is that comparisons between signed and `unsigned` values are machine-dependent, because they depend on the sizes of the various integer types. For example, suppose that int is 16 bits and long is 32 bits. Then -1L < 1U, because 1U, which is an unsigned int, is promoted to a signed long. But -1L > 1UL because -1L is promoted to unsigned long and thus appears to be a large positive number. Conversions take place across assignments; the value of the right side is converted to the type of the left, which is the type of the result. A character is converted to an integer, either by sign extension or not, as described above. Longer integers are converted to shorter ones or to chars by dropping the excess high-order bits.

Finally, explicit type conversions can be forced ("coerced") in any expression, with a unary operator called a cast. In the construction