# TITLE

# C intro

## What is C?
- C is a low level, general purpose programming language.
- C was created by Dennis Ritchie at Bell Labs in 1972.
- Fundamental language to modern software.
- Originally developed for for Unix.
# Building / running code
- TODO 
# Syntax
- **_Syntax_** describes the basic rules for writing programs for a C compiler.
- _Source code_ contains, among others, _comments_, _variables_, _functions_, _preprocessor macros_, _reserved keywords_, and _(string) literals_.
- Note: I mention _data types_, _describe statements_, etc. These terms will be defined later. 
## Comments
- **_Comments_** are ignored by the compiler.
- Note: comments are used to document code, or temporarily "disable" a portion of the code.
- _Inline comments_ are ignored for the rest of the line **after `//`**:
	- `// I am a comment!`.
	- Code can be on the same line *before* the `//`.
- *Multi-line comments* are ignored **between `/*` and `*/`**:
```C
/*
I am a multi-
line comment!
*/
```
## Variables
- **_Variables_** store values during computation.
	- Variables have _types_, which define their size (in bytes) and the operations that can be done with them.
	- Note: Think of them as "chunks of memory" or some bytes.
	- Variables are declared with the syntax:
		- `var_type var_name;`.
	- Multiple variables with the same type are defined with the syntax:
		- `var_type var1_name, var2_name;`
	- Note: A variable can be assigned to when it is defined:
		- `var_type var_name = value;`
		- `var_type var1_name = value1, var2_name = value2;`
## Functions
- **_Functions_** are named sections of code.
	- Declaration syntax:
		- `return_type name(arg_type arg_name, ...);`.
	- Definition syntax:
		- `return_type name(arg_type arg_name, ...) { ... }`.
	- The definition contains the declaration, with a series of _statements_ between curly brackets: `{ ... }`. 
	- The declaration isn't always needed.
	- The definition tells the compiler _this function **exists**_, with it's inputs and outputs.
	- The declaration tells the compiler what _this function **does**_, as a series of _statements_.
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
