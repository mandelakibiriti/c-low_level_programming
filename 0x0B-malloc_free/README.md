# [Malloc, free](https://www.youtube.com/watch?v=_8-ht2AKyH4&list=PL2_aWCzGMAwLZp6LMUKI3cc7pgGsasm2_&index=12)

What happens when we do not know in advance how much memory you need and we will only know this at runtime, after compilation? 

>  The `malloc` function is used to `allocate a certain amount of memory from heap memory during the execution of a program`. This memory will have read and write permissions.

As we write programs variables can be stored in memory either automatically or dynamically.

## Automatic memory allocation
Variables once initiated are stored in memory automatically in the stack memory and the variable can only be `read` from memory. `Stack memory` is fixed and when  program executed overuns the Stack Memory there is `Stack overflow` when a program runs beyond the amount of memory fixed in the stack.

By attempting to change the string pointer variable (which points to the memory address of the variable) below from `H` to `s` you will get a `Segmentation fault (core dumped)` error. 
> This because the memory that stores the string is only readable.
```c
    char *str;

    str = "Holberton";
    str[0] = 's';
```

However, for the code below the variable is an type `string` and not a pointer and **`does not hold the memory address of the string "Holberton"`**, but a **`copy of it as an array`**. 
```c
    char str[] = "Holberton";

    str[0] = 's';
    printf("%s\n", str);
```
> The string “Holberton” is copied into this array and can therefore be manipulated accordingly.

## Dynamic memory allocation
The malloc function allocates a specific number of bytes in memory and returns a pointer to the allocated memory. This memory will have read and write permissions.

> It will request a block of memory from the `heap memory`. If the request is granted, the operating system will reserve the requested amount of memory and malloc will return a pointer to the reserved space.

```c
    str = malloc(sizeof(char) * 3);
    str[0] = 'O';
    str[1] = 'K';
    str[2] = '\0';
    printf("%s\n", str);
    free(t);
```
In the above example we use malloc to create a 3 byte allocated space in memory, and we fill this space with characters. 

Note the use the operator sizeof. It is very important because as you know, the size of the different types will be different on different machines: we want 3 times the size of a char (which happens to be 3 times 1 byte on our 64-bit machine). Always use sizeof for a better portability.

> You can also dynamically allocate memory based on a specific structure ie. int, char etc since malloc assigns a `void pointer`. **[More details here.](https://csnotes.medium.com/malloc-in-c-for-int-and-char-c3677b857b65)**
```c
char *mystring;
mystring = (char *)malloc(sizeof(char) * (size + 1))
```


## Valgrind
Example where memory is assigned with malloc and freed late with the `free` function. `Valgrind` is used in the terminal to keep track of memory allocation.

Simply run in the terminal.
```shell
valgrind ./c-program-executable
```
```c
    int sum;

    t = malloc(sizeof(*t) * 3); // sizeof(int) is 4 * 3 =  12
    t[0] = n0;
    t[1] = n1;
    t[2] = n2;
    sum = t[0] + t[1] + t[2];
    printf("%d + %d + %d = %d\n", t[0], t[1], t[2], sum);
    free(t);
```

> When the amount of memory is not needed anymore, you must return it to the operating system by calling the function `free`.
```shell
// BEFORE FREE FUNCTION EXECUTED
==119339== HEAP SUMMARY:
==119339==     in use at exit: 12 bytes in 1 blocks
==119339==   total heap usage: 2 allocs, 1 frees, 1,036 bytes allocated
==119339== 
==119339== LEAK SUMMARY:
==119339==    definitely lost: 12 bytes in 1 blocks
```

```shell
// AFTER FREE FUNCTION EXECUTED
==119389== HEAP SUMMARY:
==119389==     in use at exit: 0 bytes in 0 blocks
==119389==   total heap usage: 2 allocs, 2 frees, 1,036 bytes allocated
==119389== 
==119389== All heap blocks were freed -- no leaks are possible
```