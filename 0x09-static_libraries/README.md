# Libraries in C
- A library is a file containing several object files, that can be used as a single entity in a linking phase of a program. 

- A library in C is a collection of header files, exposed for use by other programs. The library therefore consists of an interface expressed in a .h file (named the "header") and an implementation expressed in a .c file.

## Purpose of libraries in C
- Normally the library is indexed, so it is easy to find symbols (functions, variables and so on) in them. For this reason, linking a program whose object files are ordered in libraries is faster than linking a program whose object files are separate on the disk. Also, when using a library, we have fewer files to look for and open, which even further speeds up linking.

## Types of libraries
- There are 2 types of library files static and dynamic.

    >  ```Static libraries``` are just collections of object files that are linked into the program during the linking phase of compilation, and are not relevant during runtime.

- Static linking or the linking of static libraries creates larger files because of the creation of the standalone (executable file) files.


    > ```Shared / Dynamic libraries``` are linked into the program in two stages with specific functions launched during the execution of a program and contribute to “reduced memory consumption”

    ## More information on static and dynamic libraries
    - [More information on static libraries](https://medium.com/@704/static-libraries-in-c-378e837c6a52#:~:text=Two%20types%20of%20libraries%20in,are%20linked%20in%20two%20stages.)

    - [More information on dynamic libraries](https://www.linkedin.com/pulse/creating-using-dynamic-libraries-c-jhojan-david-cera-restrepo/?trk=public_profile_article_view)

## Creating a Static file
Creating a static file requires all source files to be created and header functions added to the main.h. All source files are then convereted into object files. 

```shell
foo@bar:~$ gcc -c *.c
```

Once the object files are aquired you can create a static file using the archive 'ar' command.

```shell
foo@bar:~$ ar -rc libmy.a *.o
```

To index the static file you can use the ranlib command.

```shell
foo@bar:~$ ranlib libmy.a
```

You can use the nm and ar -t commands to view the symbols of the static library and contents of the static library respectively.

```shell
foo@bar:~$ nm libmy.a 
foo@bar:~$ ar -t libmy.a
```
