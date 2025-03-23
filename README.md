# C_programming
C is a general-purpose procedural programming language that provides low-level access to system resources and hardware and can be used for system programming, embedded systems, and software development. It has key unique features such as pointers that can directly manipulates memory and preprocessor directives, which allow programmers to modify the source code before it is compiled.

|Table Contents|
|-----------------------------------------------------------------------------------|
|1. [Malloc](0x0B-malloc_free/README.md)| 
|2. [Pointers](0x05-pointers_arrays_strings/README.md)|
|3. [Function Pointers](0x0F-function_pointers/README.md)|
|4. [Static Libraries](0x09-static_libraries/README.md)|
|5. [Command Line Arguments](0x0A-argc_argv/README.md)|
|6. [C Preprocessor](0x0D-preprocessor/README.md)
|7. [Variadic Functions](0x10-variadic_functions/README.md)|
|8. [Structures and TypeDef](0x0E-structures_typedef/README.md)|
|9. [File I/O](0x15-file_io/README.md)|
## Betty linter 

Used Betty Linter to check for syntax errors noted indentation resulted in errors - (indentation is not recognized by compiler however indentation is important for readability as well as to comply with ASCI Standards)

## C Compiler
- Scripts written are aimed at key basic functions on running GCC compiler. C compilation process is explained [here](https://www.scaler.com/topics/c/compilation-process-in-c/)

- You can find a list of different compilers [here](https://github.com/fffaraz/awesome-cpp)

- GNU  man gcc flags can be found [here](https://man7.org/linux/man-pages/man1/gcc.1.html)

- Make code executable with gcc on ubuntu

```shell
foo@bar:~ gcc -Wall -pedantic -Werror -Wextra -std=gnu89 main.c c-file.c -o exec_file_name
```

## Format Specifiers in C
Format specifiers define the type of data to be printed on standard output. More info [here](https://www.freecodecamp.org/news/format-specifiers-in-c/)

## Putchar
putchar is a function in the C programming language that writes a single character to the standard output stream, stdout. Its prototype is as follows:
```c
int putchar (int character)
```
The character to be printed is fed into the function as an argument, and if the writing is successful, the argument character is returned. 

Print long int using _putchar requires to have recursion to be add those numbers to string as shown [here](https://www.techcrashcourse.com/2016/02/c-program-to-print-long-variable-using-putchar-only.html). Excercises that used this is > ```5-more_numbers.c```


