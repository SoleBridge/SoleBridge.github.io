# C Concepts

---

# Intro to Programming
## Intro to Code and The Need for Programming Languages
- In general, code represents:
	- A series of instructions for a computer (i.e. what it does).
	- Data for the computer to process (i.e. what to do it with).
- Computers work off a large list of numbers (_bytes_), represented by a _binary_ or _executable_ file.
- Entering these numbers directly is hard, time-consuming, and error-prone.
- Therefore, we want to instruct the computer in a more human-readable format.
- This is the idea of a _programming language_, that is more human-friendly.
- _Languages_ come in many forms and can have a specific purpose or be general purpose.
- _Languages_ are also translated into the bytes a computer can execute.
	- This translation can happen _before the code is ran_, with a _compiler_.
 	- Or translation can happen _as the code runs_, with an _interpreter_.
	- Or with a mix of these two.
## What is C?
- C is a low level (considered more machine-friendly than human-friendly), general purpose, compiled programming language.
- C was created by Dennis Ritchie at Bell Labs in 1972.
- C is a fundamental language to modern software.
- Originally developed for for Unix.
	- Previous languages depended heavily on the computer it was ran on, so software had to be re-written for _every_ computer.
- C has a very sussinct and a somewhat mathematics inspired syntax.
	- This is something many languages take from C.
## Concepts behind C
- C has _variables_ and _functions_.
 	- Variables hold a _value_.
	- Functions hold a section of code or series of instructions, and can have input or output.
	- Variables and functions have _identifiers_, or names that can be used to refer to them.
- Variables also have a _type_, which tells the compiler _how_ to look at the value.
	- i.e. `int` only stores integers (whole numbers), and `float` stores real numbers (with a decimal point).
	- Types determine the `sizeof` the variable (how much memory, in bytes, it takes), and what can be done with the variable.
## C Built-in Data Types
- The following are some built-in types in C:

| Type     | Interpretation (use)   |              Range                                | Size (bytes) |
| :---     | :---                   |              :---:                                 |          ---: |
| `int`    | Integer (whole number) | -2,147,483,648 to 2,147,483,647                    |             4 |
| `char`   | Character (letter)     | -128 to 127                                        |             1 |
| `float`  | Real number            | 1.175494351E-38 to 3.402823466E+38                 |             4 |
| `double` | Real number            | 2.2250738585072014E-308 to 1.7976931348623158E+308 |             8 |
| `void`   | No type**                | NA                                                 |             1 |
- Note:  These values are typical for a common and modern desktop computer.
- Size, and therefore range, of types can vary between compilers and build targets (computers).

- `void` is used to show that a function _doesn't return a result_, or _doesn't take a parameter_.
- `void` is used to show _pointers that don't point to a type_ (advanced topic).

- `int` and `char` are _integral_ datatypes, meaning they are integers and can be used in conditions.
- There are more types, particularly these mixed with `long` and `short`; `signed` and `unsigned`.
	- These affect the size and range of the type.

- The following are standard types in C, from `stdint.h`:

| Type       | Interpretation (use) | Size (bytes) | Size (bits) | Range |
| :---       | :---                 |         ---: |        ---: |  ---: |
| `int8_t`   | Signed integer       |            1 |           8 | −128 to 127 |
| `int16_t`  | Signed integer       |            2 |          16 | –32768 to 32767 |
| `int32_t`  | Signed integer       |            4 |          32 | -2,147,483,648 to 2,147,483,647 |
| `int64_t`  | Signed integer       |            8 |          64 | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 |
| `uint8_t`  | Unsigned integer     |            1 |           8 | 0 to 255 |
| `uint16_t` | Unsigned integer     |            2 |          16 | 0 to 65,535 |
| `uint32_t` | Unsigned integer     |            4 |          32 | 0 to 4,294,967,295 |
| `uint64_t` | Unsigned integer     |            8 |          64 | 0 to 18,446,744,073,709,551,615 |


- The following is a standard type in C, from `stdbool.h`

| Type   | Interpretation (use) | Size (bytes) | Size (bits) |             Range |
| :---   | :---                 |         ---: |        ---: |              ---: |
| `bool` | Boolean              |            1 |           8 | `true` or `false` |

- `bool` is meant to be used in condition expressions.
- Note: Boolean values need only be `true` or `false`, taking 1 bit. But modern computers address memory by bytes (8 bits).
	- Multiple boolean values can be stored into the bits of an integer (intermediate topic).


---

# Basic C Syntax
- **_Syntax_** describes the basic rules for writing programs for a C compiler (or other comilers or interpreters).
- Source code contains _comments_, _variables_, _functions_, _preprocessor directives_, _reserved keywords_, _literals_, _control sequences_, etc.

## ex: Hello world (some basic syntax)
- The following C code shows basic syntax and output:
```C
#include <stdio.h> // Use standard io library (stdio.h).

// main() is a special function.
int main() {                // This is where execution starts!
  printf("Hello World!");	// Print a message.
  return 0;					// Leave main().
}                           // This is where execution ends.
```
- This outputs:
```bash
Hello, world!
```

## Comments
- **_Comments_** are ignored by the compiler.
- Comments are used to document code, or temporarily "disable" a portion of the code.
- _Inline comments_ are ignored for the rest of the line **after `//`**:
	- `// I am a comment!`.
	- A code _statement_ can be on the same line *before* the `//`.
- *Multi-line comments* are ignored **between `/*` and `*/`**:
```C
/*
I am a multi-line comment!
Anything in here is ignored.
*/
```
## Variables
- **_Variables_** store values. They are a chunk of memory.
- Variables have _types_, which define their size (in bytes) and the operations that can be done with them.
- Variables also have names or _identifiers_,which you can use to refer to the variable later.
- Note: Think of variables as "chunks of memory" or some bytes.
- Note: Think of the type as "what the memory holds.
	- i.e. it hold an integer, real (floating-point) number, picture, audio, a memory address (_pointer_), or something else.
	- This is what determines the _sizeof_ the variable or it's type.
- When a variable's identifier is used (after it is declared), it is "replaced" by it's value.
### Declaration and Definition
- Variables are declared with the syntax `type name;`.
	- This tells the compiler `name` exists and has a type `type`.
- Variables are defined by assigning a value to the variable.
	- This can be done assigning a value: `name = value;`.
	- This tells the compiler `name` has a value of `value`.
- Multiple variables with the same type are declared with the syntax:
	- `type name1, name2;`
- Note: A variable can be assigned to (declared) when it is defined:
	- For one variable: `type name = value;`
 	- This tells the compiler `name` exists and has a type of `type` and a value of `value`.
  	- For multiple variables: `type name1 = value1, name2 = value2;`
## Functions
- **_Functions_** are named sections of code.
- Functions take in _parameters_ (input), and _return_ a value (output).
- Functions can have 0 or more parameters.
	- When a function has no parameters, the parameter list can be omitted or replaced with `void`.
- Functions can have _variadic parameters_ (advanced topic).
	- 
- Functions can return a value or return without a value.


### Declaration and Definition
- Declaration syntax:
	- `return_type name(type name, ...);`.
	- The declaration tells the compiler what _this function **does**_, as a series of _statements_.
- Definition syntax:
	- `return_type name(type name, ...) { ... }`.
	- The definition tells the compiler _this function **exists**_, with it's inputs and outputs.
- The definition contains the declaration, with a series of _statements_ between curly brackets: `{ ... }`. 
- The declaration isn't always needed, i.e. if the definition is compiled before the function is called.
	
## Statements
- **_Statements_** can include declarations, assignments, conditional execution, arithmetic, etc.
- Statements are executed in order, from top to bottom*.
- Statements end with `;`.

- Statements are generally on a new line, but can be separated by any white-space.
	- The following are both valid sequences of statements:
```C
int x = 0; x = 1; // On one line, seperated with ;
```
```C
int x = 0;	// On multiple lines
x = 1;		// seperated with ; and arbitrary white space
```

- * Compilers can actually change the order of statements, as long as the result produces the same output (very advanced topic, _compiler optimization_).

## Preprocessor directives
- **_Preprocessor directives_** happen before the code is compiled, or as the first stage of the compilation process.
	- They start with `#`.
	- Note: This is commonly used to bring in external code (`#include <stdio.h>`).
	- Note: This is also used to replace text in the code, i.e. a constant (`#define CONSTANT 5`).
	- Note: This is also used for _guard code_ (`#pragma once`) (moderate topic).

## Keywords
- **_Keywords_** are used by the C language, and you cannot name any _identifier_ (function or variable name) the same as any keyword.
	- Keywords, generally, have a special purpose such as _conditionals_, _loops_, etc.
	- Some keywords are `if`, `else`, `for`, `while`, `break`, `continue`, and `return`.

## Literals
- **_Literals_** are values within the code.
- _String literals_ are a sequence of characters between quotation marks: `"Something."`.
	- They may have escape sequences, denoted with `'\'`. Here are a few:

| Character | Interpretation (use)    |
| :---      | :---                    |
| `'\0'`    | Null character*         |
| `'\n'`    | Newline                 |
| `'\b'`    | Backspace               |
| `'\t'`    | (Horizontal) Tab        |
| `'\v'`    | (Vertical) Tab          |
| `'\\'`    | Backslash (just "\")    |
| `'\''`    | Apostrophe (just "'")   |
| `'\"'`    | Quotation mark (just ") |

- * The null character ('\0') is used to denote the end of a string.

- _Integer literals_ are integers: `42`, _floating-point literals_ are real numbers: `123.456`.
- Literals can be defined for other types, depending on their _definitions_.

## Control Sequences
- **_Control sequences_** provide a nice way to control the order of instructions.
- They allow control "if" statements are executed and how many times they are executed ("looped" through).
### Conditionals
- **_Conditional execution_** executes statements "if" their condition is nonzero.
- Note: This shows some weird aspects of C.
	- A value of 0 means `false`, and _anything else_ means `true`.
 	- Conditions are expressions composed of _Boolean algabra_ with _logic operators_ and _bitwaise operators_, and _integral datatypes_.
#### ex: if, else, else if
```C
int cond = 0, cond2 = 0;
 
if (cond) {...} // if cond is nonzero, ... is executed
// Then execution resumes from here. Jumps here if cond is 0

if (cond) {...}	// only do this if cond is nonzero
else      {...}	// only do this if cond is 0

if (cond) {...} // only do this if cond is nonzero
else if(cond2) {...}	// only do this if cond2 is nonzero
else     {...}	// only do this if cond is 0, then cond2 is zero

```
### Loops (repetition)
- **_Loops_** execute statements repetitively, based on a condition.
- `while` loops execute statements "while" a condition is `true`.
- `for` loops function as `while` loops, but give you an _initialization expression_ (that happens before the repetition), condition expression (that determines if the code is repeated), and itteration expression (that happens at the end of every loop).
- `do`-`while` loops function like `while` loops, but the statements within the loop are executed _at least once_.
#### ex: `while`, `for`, and `do`-`while` loops
```C
// WHILE LOOP example
bool do_loop = true;
int i = 0;
printf("About to go into while loop!\n");
while(do_loop) {
	printf("\tIn while loop, step %d.\n", i);
	i = i + 1;
	if(i >= 10) do_while_loop = false;
}
printf("While loop over!\n\n");

// FOR LOOP example
printf("About to go into for loop!\n");
for(int j = 0; j < 10; j++) // "repeat 10 times, putting the current step in j"
	printf("\tIn for loop, step %d.\n", j);
printf("For loop over!\n\n");

// See that the for loop combines many lines into one when itterating through numbers like this.
// Because the body of the loop only contains one expression, the {} can be omitted.


// DO-WHILE LOOP example
do_loop = false;
printf("About to go into do-while loop!\n  do_loop is %b.\n", do_loop);
do {
	printf("\tIn do-while loop!\n");
} while(do_loop);
printf("Do-while loop over!\n\n");

// This shows the loop being executed once, and only once, as the condition is checked before the second itteration
```
