# Template for learning a new programming language: Golang
- Note, this page can be seen [in HTML](https://solebridge.github.io/), but viewing Githhub markdown looks much better.
## Entry Point and Simple I/O
### Running Go 
- `go run .` to compile and run the code.
- `go build` to build a binary.
- [A Tour Of Go](https://go.dev/tour/welcome/1) online environment.
#### "Hello world" program
- Declare `package main` to mark this as the package with the `main()` entry point.
- `import "fmt"`, standard IO library.
- Call `fmt.Println()` to print.
```Go
package main
import "fmt"

func main() {
	fmt.Println("Hello, World!")
}
```
#### Input and output - echo program
- The `"bufio"` package provides buffered IO, useful for input/output strings.
```Go
package main
import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	reader := bufio.NewReader(os.Stdin)
	fmt.Print("> ")
	text, _ := reader.ReadString('\n')
	fmt.Println(text)
}
```
#### Standard library
- [Standard library reference](https://pkg.go.dev/std).
## Syntax
- Expressions separated by newline or by `;`.
### Comments
- Single line comments after `//`.
- Multi-line comments between `/*` and `*/`.
### Variable Declarations
1. `var variablename type = value`
	- This syntax improves readability compared to C syntax, see [this article](https://go.dev/blog/declaration-syntax).
2. `variablename := value`
	- This syntax is not always available, the type is inferred.
- `var` can be scoped to a package or a function.
	- With an initial value, type can be omitted (inferred from value).
	- **Inside a function**, short assignment (`:=`) can be used instead of `var` This can't be done at the package scope.
## Primitive Types  
- Primitive types:  
	- `bool`
	- `string`
	- `int`, `int8`, `int16`, `int32`, `int64`
	- `uint`, `uint8`, `uint16`, `uint32`, `uint64`, `uintptr`
	- `byte` (`uint8`)
	- `rune` (`int32`)
	- `float32`, `float64`
	- `complex64`, `complex128`
### Zero values:
- `0` for numeric types.
- `false` for boolean
- `""` for strings.
### Constants:
- Constants are **values** of character, string, boolean, or numeric types.
 - Constants cannot be declared with `:=`.
- Constants are declared with `const`: `const Truth = true`.
- When a variable is assigned from a numeric constant, it may be an `int`, `float64`, or `complex128` depending on the constant value:
```Go
i := 12         // int
f := 2.714      // float64
g := 1.0 + 0.5i // complex128
```
### Primitive Operations
#### Arithmetic Operators
| Operator | Arity  | Function       |
| -------- | ------ | -------------- |
| +        | binary | addition       |
| -        | binary | subtraction    |
| *        | binary | multiplication |
| /        | binary | division       |
| %        | binary | modulus        |
| ++       | unary  | increment      |
| --       | unary  | decrement      |
#### Relational operators

| Operator | Arity  | Function              |
| -------- | ------ | --------------------- |
| ==       | binary | Equal To              |
| !=       | binary | Not Equal To          |
| >        | binary | Greater Than          |
| <        | binary | Less Than             |
| >=       | binary | Greater Than Equal To |
| <=       | binary | Less Than Equal To    |
#### Logical operators
| Operator | Arity  | Function    |
| -------- | ------ | ----------- |
| &&       | binary | Logical And |
| \|\|     | binary | Logical Or  |
| !        | unary  | Logical Not |
#### Bitwise Operators
| Operator | Arity  | Function                       |
| -------- | ------ | ------------------------------ |
| &        | binary | Bitwise And                    |
| \|       | binary | Bitwise Or                     |
| ^        | binary | Bitwise Xor                    |
| <<       | binary | Left Shift                     |
| >>       | binary | Right Shift                    |
| &^       | binary | And Not: Used for bit clearing |
#### Assignment Operators
| Operator | Arity  | Function                       |
| -------- | ------ | ------------------------------ |
| =        | binary | Simple Assignment              |
| +=       | binary | Add Assignment                 |
| -=       | binary | Subtract Assignment            |
| *=       | binary | Multiply Assignment            |
| /=       | binary | Division Assignment            |
| %=       | binary | Modulus Assignment             |
| &=       | binary | Bitwise And Assignment         |
| ^=       | binary | Bitwise Xor Assignment         |
| \|=      | binary | Bitwise Or Assignment          |
| <<=      | binary | Bitwise Left Shift Assignment  |
| >>=      | binary | Bitwise Right Shift Assignment |
#### Misc
- Note: Go does not have pointer arithmetic.
## Type System
### Type Checking: **Statically Typed**
- Go checks types at compile time.
### Type Strength: **Strongly Typed**
- Go enforces strict type conversions.
- Does not allow implicit coercion between types.
### Type Inference
- When declaring an un-typed variable (with `:=`  or `var =` ), the variable's type is inferred from the value.
## Functions
```Go
func add(x, y int) int {
	return x + y
}
```
- Functions are defined with the `func` keyword.
- The return type comes after the function name and arguments.
- Functions can take 0 or more arguments.
- When multiple arguments have the same type, only the last needs to have the type.
	- In the example, `x` and `y` are both `int`.
```Go
func swap(x, y string) (string, string) {
	return y, x
}
```
- Functions can return multiple values.
- Functions can have named return values.
	- Variables declared at beginning of scope, and automatically returned with a "naked return".
	- Naked returns are only recommended for short functions.
```Go
func add_sub(a, b int) (x, y int) {
	x = a + b
	y = a - b
	return
}
```
- Go supports Variadic functions, with `args ... tpye` syntax.
	- A variadic argument must be last in the list, and can be the only argument.
	- Any non-negative number of elements can be used in a variadic function call.
```Go
func func_name(non_variadic int, args ...type) return_type {
	...
}
```
- You return from a function with `return return_value(s)`. There can be no values, multiple values, or a naked return.

- Functions are values, and can be passed like other values:
```Go
func f2(fn func(float64, float64) float64) float64 {
	return fn(3, 4)
}
func main() {
	f1 := func(x, y float64) float64 {
		return x + y
	}
	fmt.Println(f1(1,2))

	fmt.Println(f2(f1))
	fmt.Println(f2(math.Pow))
}
```
- Go supports closures:
```Go
func next_num() func() int {
    i := 0
    return func() int {
        i++; return i
    }
}
func main() {
    next := next_num()
    fmt.Println(next())
    fmt.Println(next())
    new_nums := next_num() // uses new 'i' variable
    fmt.Println(new_nums())
}
```
## In-Built (Standard) Data Structures 
### `struct`
- A `struct` is a collection of it's fields; each field is accessed with a dot.
- Struct pointers can be automatically dereferenced.
- Structs can be returned from a function, similar to C.
```Go
type Person struct {
	age int
	name string
}

func main() {
	a := Person{21, "Aden"}
	b := &a
	b.age = 22
	fmt.Println(a)
}
```
#### `struct` literals
- Structs can be initialized using struct literals,  with named values and zero values:
```Go
type My_struct struct {
	X, Y int
}
var (
	v1 = My_struct{1, 2}  // My_struct
	v2 = My_struct{X: 1}  // implicit Y:0
	v3 = My_struct{}      // implicit X:0, Y:0
	p  = &My_struct{1, 2} // *My_struct
)
```
### `array`
- Declared with: `var var_name [n]var_type`, where `n` is the size of the array.
- Cannot be resized.
### `slice`
- Declared with: `var var_name [low:high]var_type` or `var var_name []var_type`.
- The `n` from array deceleration is missing; as `low` and `high` are optional.
- Note: `low` bound index included, but `high` bound index is not.
- slices have `length` and `capacity` properties.
- Slices can be appended to: `var s []int;` `s = append(s, 0);` `s = append(s, 1, 2)` 
- `range` can be used with slices:
```Go
func main() {
	var nums = []int{1, 2, 3, 4}
	for i, n := range nums {
		fmt.Printf("nums[%d] : %d\n", i, n)
	}
}
```
### `map`
- Maps are used for key-value pairs. The `make()` function is used to initialize a usable map.
- Map literals require keys.
```Go
type My_struct struct {
	X, Y int
}

var m map[string]My_struct

func main() {
	m = make(map[string]My_struct)
	m["Entry 0"] = My_struct {
		0, 1,
	}
	fmt.Println(m["Entry 0"])
}
```
#### `map` operations (for map `m`):
- Insert or update an element : `m[key] = elem`
- Retrieve an element: `elem = m[key]`
- Delete an element: `delete(m, key)`
- Test if a key is present: `elem, ok = m[key]`
	- If `key` is in `m`, `ok` is `true`. If not, `ok` is `false`.
	- If `key` is not in the map, then `elem` is it's zero value.
## Conditional statements
### `if` statements
- Braces `{ }` are always required.
- `if` can have a "short statement" that executes before the condition is evaluated, using `for`-like syntax:
```Go
if v := 10.0; v < n {
	return v
}
```
### `if` + `else` statements
- Variables declared inside an `if` short statement are also available inside any of the `else` blocks.
```Go
if v := 10.0; v < n {
	return v
} else {
	fmt.Printf("n >= v!\n")
}
```
### `switch` statements
- Meant to be more compact `if`+`else`
- Runs the first case with a true condition, in order, and no `break` statements are needed.
- The cases do **not** need to be constants or integers.
- Switch cases evaluate cases from top to bottom, stopping when a case succeeds.
```Go
import (
	"fmt"
	"runtime"
)
	
func main() {
	switch os := runtime.GOOS; os {
	case "darwin":
		fmt.Println("OS X.")
	case "linux":
		fmt.Println("Linux.")
	default:
		fmt.Printf("%s.\n", os)
	}
}

```
- switch statements can omit the condition, to automatically evaluate to `true`.
```Go
t := time.Now()
switch {
case t.Hour() < 12:
	fmt.Println("Good morning!");
case t.Hour() < 17:
	fmt.Println("Good afternoon.");
default:
	fmt.Println("Good evening.");
}
```
### No ternary operator
- Go does not have a ternary operator. `if`+`else` or `switch` statements must be used.
## Loops
### `for` loop
- the init statement (optional): executed before the first iteration
- the condition expression: evaluated before every iteration
- the post statement (optional): executed at the end of every iteration
```Go
sum := 0
for i := 0; i < 10; i++ {
	sum += i
}
```
- the braces `{ }` are always required.
- Go uses `for` for `while` loops:
	- If init and post statements are not present, the semicolons can be dropped, effectively making a `while` loop:
```Go
for sum < 1000 {
	sum += sum
}
```
- infinite loops also use `for`, without a condition:
```Go
for {
}
```
## `defer` statements
- A defer statement defers the execution of a function until the surrounding function returns.
- The deferred call's arguments are evaluated immediately, but the function call is not executed until the surrounding function returns.
- Deferred function calls are pushed onto a stack. When a function returns, its deferred calls are executed in last-in-first-out order.
```Go
for i := 0; i < 10; i++ {
	defer fmt.Println(i)
}
// prints in order: "9 8 7 6 5 4 3 2 1 0" when outer scope exited
```
## User-Defined Types
- Users can define types using structs.
## Modularization  
- The language uses modules, defined at the start of every file.
