# Variadic / Varargs Function

This is a [function that can take `n` number of arguments](youtube.com/watch?v=FgvrnYScdH8) without specifying or defining the number `n` of arguments themselves.

An example is the `printf` function which can take a vast number of arguments.

```c
printf("%s\n", str); // Prints a string

printf("x is: %d and y is: %d\n", x, y); // Prints 2 variables x and y

printf("%d + %d + %d = %d\n", t[0], t[1], t[2], sum); // Prints variable numbers including the sum of those numbers
```


For [varidiac functions](https://www.geeksforgeeks.org/variadic-functions-in-c/) you would have to use a specific syntax to create it.

```c
double add_float(float count, ...){

    // *va_list* will be the pointer to the 
    // list of arguments in the variadic function
    va_list args;

    // Initialize variables that will be iterated in list
    float next = count;
    double total = 0;

    // Initializing argument to the list pointer 
    // having access to the arguments in the variadic function
    va_start(args, count);

    // accesses the next variadic function argument
    for(int i = 0; i < count; i++)
    {
        total += next;
        next = va_arg(args, double);
    }

    // Ending argument list traversal
    va_end(args);

    return (total);
}
```

For [further explanation](https://azrael.digipen.edu/~mmead/www/Courses/CS120/VariadicFunctions.html) of the syntax and structure of variadic functions.