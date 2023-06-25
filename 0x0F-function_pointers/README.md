
# Function pointers

Below is code for the main *calling function* that calls the *called functions* **Add and Sum**.

[1. Using Malloc](https://www.youtube.com/watch?v=E8Yh4dw6Diw&list=PL2_aWCzGMAwLZp6LMUKI3cc7pgGsasm2_&index=14)
```c
int main(void) {

	int  vala = 2, valb = 4;
	int *z = (int*)malloc(sizeof(int));
	int *ptrfunc = Add(&vala, &valb, z);
	printf("Sum of Add function is = %d\n", *ptrfunc);
	free(z);
	
	return(0);
}
```
For the above the variables `vala` and `valb` have their addresses pointed and thus their values can be dereferenced in the Add function. A pointer `z` is created for memory allocation of size int which will be dereferenced and its value will be the addition of `vala` and `valb`.
```c
int *Add(int *vala, int *valb, int *mallocMem){

	*mallocMem = (*vala) + (*valb);
	return  mallocMem;
}
``` 

[2. Using Pointer functions](https://www.youtube.com/watch?v=ynYtgGUNelE&list=PL2_aWCzGMAwLZp6LMUKI3cc7pgGsasm2_&index=15)

Here we have a function `Sum` whose address in memory is pointed to by pointer `sumptr` which has 2 arguments of type int. 
```c
int main(void) {
	int val;
	int (*sumptr)(int, int);
	sumptr = Sum;
	val = sumptr(2,3);
	printf("Result of Sum Pointer function = %d\n",val); 
	return (0);
}
```
We can equate the pointer `sumptr` to the function `Sum`. Thus the values 2 and 3 and parsed to the Sum function and returns the sum of these values as `val3` which we can print later.
```c
int  Sum(int  val1, int  val2) {
	int  val3;
	val3 = val1 + val2;
	return(val3);
}
```

[3. Use Cases for Function Pointers](https://www.youtube.com/watch?v=sxTFSDAZM8s&list=PL2_aWCzGMAwLZp6LMUKI3cc7pgGsasm2_&index=16)

A function pointer is a pointer that points to the function. A function pointer is an address of the function. You can pass the function pointer as an argument in another function so that the function is called to run a specific operation. [This makes the code clean and less bulky](https://qr.ae/prULXv).

In this case, the compare & absolute compare are `pointer function` that are passed as argument in the BubbleSort function.


> A. Callback function for running comparisons of values

These compare and absolute compare functions are pointed to as argurments in the BubbleSort function as function pointers.

> Sorts in descending order by returning 1, 0 or -1 based on the if comparator
```c
int compare(int a, int b){ 
    if(a > b) return -1;
    else return 1;
}
```
> Sorts in ascending order based on absolute values (disregards negative "-" sign in int)
```c
int absolute_compare(int a, int b){ 
    if(abs(a) > abs(b)) return 1;
    else return -1;
}
```
> B. BubbleSort function using Bubble sort algorithim

In the BubbleSort function depending on what way we would like to sort the array (descending or ascending) we don't want to keep calling the compare or absoulte compare functions over and over again.

We can simply point to the compare and absolute functions when we pass the either compare or absolute compare as an argument in the Bubble Sort function.
```c
void BubbleSort(int *A, int n, int(*compare)(int, int)){
	int i,j,temp;

    printf(
        "\n/*Callback function*/\n"
    );

    // Print before sort
    for (i=0; i<6; i++) printf("%d",A[i]);
    printf("\n");
	
    for(i=0; i<n; i++){
		for(j=0; j<n-1; j++){
            if(compare(A[j], A[j+1]) > 0) { // Compare values in array and SWAP
                temp = A[j];
                A[j] = A[j+1];
                A[j+1] = temp;
            }
		}
    }
}
```
> Main function

We have two calls to Bubble Sort using both compare and absolute compare as pointer functions without calling both functions in the BubbleSort function itself.
```c
int main() {
	// Array A
	int i, A[] = {3,2,1,5,6,4};

	BubbleSort(A,6,compare);
    
	for (i=0; i<6; i++) printf("%d",A[i]);
    printf("\n");
	
	// Array B
	int j, B[] = {3,2,-1,5,6,-4};
	
	BubbleSort(B,6,absolute_compare);

	for (j=0; j<6; j++) printf("%d",A[j]);
    printf("\n");
}
```