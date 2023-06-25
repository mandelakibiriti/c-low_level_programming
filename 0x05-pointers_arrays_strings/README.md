## Pointers

### [Pointers Explainer Playlist](https://www.youtube.com/playlist?list=PL2_aWCzGMAwLZp6LMUKI3cc7pgGsasm2_)

Every time you declare a variable, the computer will reserve memory for this variable. The memory reserved will then store the value of the variable. A pointer in this case stores the address where the variable is stored and in essences points to a location in memory.

| Variable | Description |
| -------- | ----------- |
| `int a = 7, b;` | Two variables `a` with value of 7 and variable `b`. 
| `int *p , *c;` | Un-initialized Pointer `p` and `c`. Note they are both type `int`
| `int **q = &p;`| Un-initialized Pointer `q` which will pointer to another pointer `p` where the address of pointer `p` is stored.
| `p = &a;` | Stores address of `a` in ptr `p`.
| `b = *p;` | Put value at ptr `p` in `b` where `p` has been deferenced to get the value in `a` which is `7`.
| `c = (char*)p; `| Typecasting where the address of type `char` is assigned to pointer `c`. When you dereference pointer `*c` you shall get the value of `sizeof(char)`.

> Dereferencing is used to access or manipulate data contained in memory location pointed to by a pointer.

> Pointers are strongly type where a pointer `int` can only point to a variable type `int`. However, in the case of type setting you are simply assigning the address of a certain address to a pointer even though its a different type.

# Example 1

```c
#include <stdio.h>

void increment(int *x) {
    (*x)++;
}

int main() {
    int a = 5;
    increment(&a);
    printf("a = %d\n", a);  // prints "a = 6"
    return 0;
}
```

In this example, we have a variable **`a`** with the value of 5, and a function increment that takes an *` address(&)`* to an int as an argument. 

> Inside the `increment` function, we use **`*`** to access **`the value`** stored at the memory address pointed to by the pointer **`*x`**, and increment it by 1. 

By passing the address of `a` to the function using the & operator, we allow the function to directly modify the value of a. As a result, when we print the value of a after calling increment, it will be 6.

# Example 2
```c
void cisfun(int *n1, int *n2)
{
    int z;

    z = 0;
    printf("value of z is: %d\n", z);

    *n1 = *n2 = z;
    printf("x is now: %d and y is now: %d\n", *n1, *n2);
}

int main(void)
{
int x, y;
    x = 1;
    y = 2;
    printf("x is: %d and y is: %d\n", x, y);
    cisfun(&x,&y);

    return (0);
}
```
We have a function `cisfun` which takes in 2 variables which are pointers `*n1` and `*n2`. The function is called in main by taking the **`address(&)`** of 2 other variables `x` and `y`.

In the function `cisfun` another variable `z` has a value of 0. This value is assigned to pointer `*n1` which points to the `address(&)` of variable `x` where the value of `x` is stored. Same goes for the pointer `*n2` which points to the `address(&)` of variable `y`.

> **This will change the value from 1 to 0 for variable x and change the value from 2 to 0 for variable y**

# Example 3 - Pointers to Pointers
You can point a pointer to another pointer and get the address to another pointer or the value stored at that address.

By dereferencing the pointers you shall print out the same value across all the pointers that pointer to each others memory addresses.
```c
int main()
{
    int a = 5;
    int *b = &a; 
    *b = 6; 
    int **c = &b;
    int ***d = &c;

    printf("%d\n", *b); 
    printf("%d\n", **c); 
    printf("%d\n", ***d); 
}
```

# Example 4 - Pointers and Arrays
Since pointers store the memory address of a variable we can use them to point to the memory store of an array and iterate over that array.

```c
#include <stdio.h>

void print(char* C)
{
    while (*C != '\0')
    {
        printf("%c", *C);
        C++;
    }
    printf("\n");
}
int main()
{
    char C[20] = "Hello";
    print(C);
}
```

## [Multi dimensional array](https://www.youtube.com/watch?v=_j5lhHWkbnQ&list=PL2_aWCzGMAwLZp6LMUKI3cc7pgGsasm2_&index=12)
Multidimension array which has 3 blocks of 2 arrays within it ie. `C[3]` with those 2 array blocks ie. `C[0][2]` having an additional 2 values in each block ie. `C[0][0][2]`
>```c
>int C[3][2][2] = {
>        {
>
>        [0]   {2, 5}, ==> Has 2 values in position 0,1 
>[0]
>        [1]   {7, 9}
>
>        },
>
>        {
>
>        [0]   {3, 4}, 
>[1]
>        [1]   {6, 1}
>
>        },
>        {
>
>        [0]   {0, 8}, 
>[2]
>        [1]   {11, 13}
>
>        }
>    };
> ```   
> So `C[0][0][1]` will return a value of `5` as shown below
```c
printf("%d,%d\n", C[0][0][1], *(C[0][0]+1)); 
```
>Below the various prints will return the `memory address of array C`.
```c
printf("%d,%d,%d,%d\n", C, *C, C[0], &C[0][0]); 
```    


