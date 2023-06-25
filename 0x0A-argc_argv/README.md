## Command Line Arguments in C

- It is possible to [pass some values from the command line to your C programs](https://www.tutorialspoint.com/cprogramming/c_command_line_arguments.htm) when they are executed. These values are called command line arguments and many times they are important for your program especially when you want to control your program from outside instead of hard coding those values inside the code.

```c
#include <stdio.h>

int main( int argc, char *argv[] )  {

   if( argc == 2 ) {
      printf("The argument supplied is %s\n", argv[1]);
   }
   else if( argc > 2 ) {
      printf("Too many arguments supplied.\n");
   }
   else {
      printf("One argument expected.\n");
   }
}
```
> As you can see, main now has arguments. 
> - The name of the variable ``` argc stands for "argument count".``` which contains the number of arguments passed to the program. 
>- The name of the variable ``` argv stands for "argument vector".``` A vector is a one-dimensional array, and argv is a one-dimensional array of strings.
> Each string is one of the arguments that was passed to the program.

```__attribute__((__unused__))``` is added when argc or argv is not used on c program compilation

```int atoi (const char * str);``` is a function that convert a string to an interger in [this example.](https://cplusplus.com/reference/cstdlib/atoi/)

[For example](http://crasseux.com/books/ctutorial/argc-and-argv.html), the command line
```shell
foo@bar:~ gcc -o myprog myprog.c
```
would result in the following values internal to GCC:

```shell
argc
    4
argv[0]
    gcc
argv[1]
    -o
argv[2]
    myprog
argv[3]
    myprog.c
```