# C preprocessor

## [Compilation Process](https://www.youtube.com/watch?v=VDslRumKvRA)
- From source code `.c file` written by a developer the compiler has several components that will convert the source code to machine binary code for execution.

> `Preprocessor` 

- Will remove comments from the source code and include the header file code in the source code. Lastly if any macro is used, the macro name will be replaced by its value.  

> `Compiler`

- Compiler will convert the processed source code into assembly code.

> `Assembler`

- Assembler will convert the assembly code to the machine readable binary / object code.

> `Linker`

- A linker will merge all the binary object code from different .c source codes ie. dynamically or statically from libraries or other .c files and merge all of them into a single executable file `.exe file`  

## [Purpose of C Preprocessor](https://www.cprogramming.com/tutorial/cpreprocessor.html)

- There are essentially three uses of the preprocessor--directives, constants, and macros so as to `prevent multiple definition of the same headers, objects, functions on complie time.`

### 1. Directives
`Directives` are commands that tell the preprocessor to skip part of a file, include another file, or define a constant or macro. Directives always begin with a sharp sign (#) and for readability should be placed flush to the left of the page.

Directive has the identifer name - name of the directive and value of the directive
> `#define [identifier name] [value]`

Below is an example of a directive `PI_PLUS_ONE` that has a value of 4.14 placed in paranthesis.
> `#define PI_PLUS_ONE (3.14 + 1)`

### 2. [Guards](https://en.wikipedia.org/wiki/Include_guard)
Guards is used in defining header files that are utilized multiple times in source files but we wish to ensure that any given header file is included once and only once.

By using the `#ifndef directive`, you can include a block of text only if a particular expression is undefined; then, within the header file, you can define the expression. This ensures that the code in the `#ifndef` is included only the first time the file is loaded. Note that there is an n in `#ifndef` -- it stands for "if not defined")

```c
#ifndef _FILE_NAME_H_
#define _FILE_NAME_H_
 
/* code */ - function prototypes and structs
 
#endif // #ifndef _FILE_NAME_H_
```

[Function Prototypes](https://www.programiz.com/c-programming/c-user-defined-functions) can be defined in the header file that will contain the functions needed in the main source code. 

A function prototype is simply the declaration of a function that specifies function's name, parameters and return type. It doesn't contain function body.

A function prototype gives information to the compiler that the function may later be used in the program. Syntax of the function prototype is as below.

> `returnType functionName(type1 argument1, type2 argument2, ...);`

### 3. [Macros](https://www.youtube.com/watch?v=X6HiYbY3Uak)
Macro is a name given to a piece of code, so whenever the compiler encounters a macro in a program, it will replace it with the macro value. In the macro definition, the macros are not terminated by the semicolon(;).

A macro definition is usually of the following form:

> `#define MACRO_NAME(arg1, arg2, ...) [code to expand to]`

For instance, a simple increment macro might look like this:
> `#define MULT(x, y) (x) * (y)` 
>
>`// now MULT(3 + 2, 4 + 2) will expand to (3 + 2) * (4 + 2)`