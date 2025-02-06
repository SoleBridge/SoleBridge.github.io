# C Concepts

---

# Intro to Programming
## Intro to Code and The Need for Languages
- In general, code represents:
	- A series of instructions for a computer (i.e. what it does).
	- Data for the computer to process (i.e. what to do it with).
- Computers work off a large list of numbers (_bytes_), called a _binary_ or _executable_ file.
- Entering these numbers directly is hard, time-consuming, and error-prone.
- Therefore, we want to instruct the computer in a more human-readable format.
- This is the idea of a _programming language_.
- _Languages_ come in many forms and can have a specific purpose.
- _Languages_ are also translated into the bytes a computer can execute.
	- This translation can happen _before the code is ran_, with a _compiler_.
 	- Or translation can happen _as the code runs_, with an _interpreter_.
## What is C?
- C is a low level (considered more machine friendly than human friendly), general purpose, compiled programming language.
- C was created by Dennis Ritchie at Bell Labs in 1972.
- C is a fundamental language to modern software.
- Originally developed for for Unix.
	- Previous languages depended heavily on the computer it was ran on, so software had to be re-written for _every_ computer.
- C has a very sussinct and a somewhat math inspired syntax.
	- This is something many languages take from C.
## Concepts behind C
- C has _variables_ and _functions_.
 	- Variables hold a _value_.
	- Functions hold a section of code or series of instructions, and can have input or output.
	- Variables and functions have _identifiers_, or names that can be used to refer to them.
 	- Variables also have a _type_, which is tells the program _how_ to look at the value.
		- i.e. `int` only stores whole numbers, and `float` stores real numbers.
	- Types determine the _sizeof_ the variable and what can be done with the variable.
## C Built-in Data Types
- The following are all built-in types in C:

| Left-aligned | Center-aligned | Right-aligned |
| :---         |     :---:      |          ---: |
| git status   | git status     | git status    |
| git diff     | git diff       | git diff      |


---

# Basic C Syntax
- **_Syntax_** describes the basic rules for writing programs for a C compiler (or other comilers or interpreters).
- _Source code_ contains _comments_, _variables_, _functions_, _preprocessor directives_, _reserved keywords_, _literals_, etc.
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
- Functions can have any number of parameters, but 
- The definition tells the compiler _this function **exists**_, with it's inputs and outputs.
- The declaration tells the compiler what _this function **does**_, as a series of _statements_.
### Declaration and Definition
- Declaration syntax:
	- `return_type name(type name, ...);`.
  	- 
- Definition syntax:
	- `return_type name(type name, ...) { ... }`.
- The definition contains the declaration, with a series of _statements_ between curly brackets: `{ ... }`. 
- The declaration isn't always needed.
	
## Statements
- **_Statements_** can include declarations, assignments, conditional execution, arithmetic, etc.
	- Statements are executed in order, from top to bottom.
	- Statements end with `;`.
	- Statements are generally on a new line, but can be separated by any white-space.
- The following are equally valid:
```C
x = 0; x += 1;
```
```C
x = 0;
x += 1;
```
## Preprocessor macros
- **_Preprocessor macros_** define operations that happen before the code is compiled.
	- Start with `#`.
	- Note: This is commonly used to bring in external code (`#include <stdio.h>`).
	- Note: This is also used to replace text in the code (`#define CONSTANT 5`).
	- Note: This is also used for _guard code_ (`#pragma once`).
## Keywords
- **_Keywords_** are used by the C language, and you cannot name any _identifier_ the same as any keyword.
	- Keywords, generally, have a special function such as conditional execution, repeating code, or leaving a function.
	- Some keywords are `if`, `else`, `for`, `while`, `break`, `continue`, `return`, etc.
## Literals
- **_Literals_** are values within the code.
- _String literals_ are a sequence of characters between quotation marks: `"Something."`.
	- TODO: Escape sequences.
- _Integer literals_ are integers: `42`, _floating-point literals_ are real numbers: `123.456`.
- Literals can be defined for other types, depending on their _definitions_.
## ex: Hello world (basic syntax)
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

# Statements
- **_Statements_** 
## ex: Temperature converter (basic arithmetic)
