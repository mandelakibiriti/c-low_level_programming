# c structures and typedef

## Structures

A structure is a user defined data type available in C that allows to combine data items of different kinds (str, int, float) or different mixed type records eg. (name, address, age).

[To understand the syntax and initizilation of struct](https://en.wikipedia.org/wiki/Struct_(C_programming_language))

1. Declaration / definition of a structure in the global scope of your program (outside of all your functions, just like the functions prototypes). You can declare elements / members of your structure in its scope.
```c
struct User
{
    char *name;
    char *email;
    int age;
};

int main(void){
    struct User user;

    return(0);
}
```
2. You can access the elements in your structure using the '.' symbol and assign a value to a specific element in the structure.
```c
int main(void){
    struct User user;
    user.name = "Foo Bar";
    user.email = "foo@foo.com";
    user.age = 28;

    return(0);
}
```

3. [Structure pointer](https://www.scaler.com/topics/c/pointers-and-structures-in-c/) points to the address of the structure variable in the memory block to which it points. This pointer can be used to access and change the value of structure members. This way, structures and pointers in C can be used to create and access user-defined data types conveniently.

4. Struct size needs to be known to the compiler since the struct is stored as a contiguous block in memory. 
> A sole [contiguous segment](https://byjus.com/gate/difference-between-contiguous-and-noncontiguous-memory-allocation/#:~:text=In%20contiguous%20memory%20allocation%2C%20a%20sole%20contiguous%20segment%20of%20memory,2.&text=The%20execution%20is%20slower%20in%20In%20non%2Dcontiguous%20memory%20allocation.) of memory is assigned to execute the process. In non-contiguous memory allocation, the process is allowed to various memory sections at multiple memory locations in the memory. 2. The execution is slower in In non-contiguous memory allocation.

## Complete example
> *`User`* structure is created with **name, email and age** as members of the structure. 

```c
struct User
{
    char *name;
    char *email;
    int age;
};
```
> A pointer structure to the *`User`* structure (*`new_user`*) creates a memory allocation that will point to the memory addresses of the *`User`* structure members where the respective values will be created and accessed.

> Derefencing is done in the *`new_user`* pointer structure using the `*(struct_name).struct_member` syntax or using the `->` operator to access the values of the members in the structure.
```c
struct User *new_user(char *name, char *email, int age)
{
    struct User *user;

    user = malloc(sizeof(struct User));

    if(user == NULL)
        return (NULL);

    // Dereferencing to access the values in the members    
    user -> name = name; // (*user).name = name; is an equivalent
    user -> email = email; // (*user).email = email; is an equivalent
    user -> age = age; // (*user).age = age; is an equivalent

    return user;
}
```
> In the main function the *`new_user`* is called to add values to the *`User`* structure member memory addresses 
```c
int main(void){
    struct User *user1, *user2;

    // create new user using the pointer structure
    user1 = new_user("Foo", "foo@foo.com", 28); 
    user2 = new_user("Bar", "bar@bar.com", 29);

    if(user == NULL)
        return(1);

    printf("User1 %s and User2 %s\n", user1.name, user2.name);
    return(0);
}
```

## [Typedef]


> Typedef (type definition) allows you to create a new name for a data structure type. For example you can create a `unsigned char` type which can be defined or identified by the name `byte`.

```c
typedef unsigned char byte;

int main(void)
{
    byte c;
    c = 200;
    return(0);
}
```
> Typedef can also be used to [create a new data type.](https://www.tutorialspoint.com/cprogramming/c_typedef.htm)

```c
typedef struct book
{
    /* data */
    char *book_title;
    char *author;
    int book_id;
}book;
```


```c
typedef struct book
{
    /* data */
    char *book_title;
    char *author;
    int book_id;
}book;

int main(void){
    book book1, book2;

    book1.author = "Shakespear James";
    book1.book_title = "Macbeth";
    book1.book_id = 101;

    book2.author = "Shakespear Smith";
    book2.book_title = "Hamlet";
    book2.book_id = 102;

    printf("The book %s is written by %s with a book id %d\n", book1 book_title, book1.author, book1.book_id);
    printf("The book %s is written by %s with a book id %d\n", book2.book_title, book2.author, book2.book_id);

    return(0);
}
```
