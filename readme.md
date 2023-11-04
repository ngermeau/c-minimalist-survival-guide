# C Minimalist Survival Guide

  * [Comments](#comments)
  * [Literals](#literals)
  * [Data Types And Modifiers](#data-types-and-modifiers)
  * [Variables](#variables)
  * [Variable Storage Classes](#variable-storage-classes)
  * [Constants](#constants)
  * [Operators](#operators)
  * [Control flow](#control-flow)
  * [Pointers](#pointers)
  * [User Data Types](#user-data-types)
    + [Enumeration](#enumeration)
    + [Structure](#structure)
    + [Union](#union)
    + [Typedef](#typedef)
  * [Functions](#functions)
  * [Arrays](#arrays)
    + [Static Arrays](#static-arrays)
    + [Dynamic Array](#dynamic-array)


## Comments 

Comment your code.

```c
/* 
  * Using Multi-line comment 
  */ 
int counter;                              //Single line comment
```

## Literals

Represent fixed values not altered during execution.

```c
3,03,0x3,0X3                              //integer decimal,octal,hexadecimal,hexadecimal
3l,3u,3ul,3ull                            //integer long,unsigned,unsigned long, unsigned long long
3.14,3.5e-2                               //floating point double, with scientific notation
3.1f,3.1e2f                               //floating point float, with scientific notation 
3.1l,3.1e2l                               //floating point long double, with scientific notation 
'a'                                       //character
"Hello"                                   //string 
"Multi\                                   //multiline string
  line"
```

## Data Types And Modifiers 

Describes the size of variables memory location and type of data to be stored into that location.

```c
char ltr;                                 //integer : 1 byte
signed char;                             
unsigned char;                          

int cnt;                                  //integer : 2/4 bytes (default signed)
signed int;                             
unsigned int;

short cnt;                                //integer : 2 bytes   (default signed)
short int cnt;                            //same as above 
signed short;
unsigned short;

long cnt;                                 //integer : 4/8 bytes (default signed)
long int cnt;                             //same as above 
signed long;
unsigned long;

long long cnt;                            //integer : 8 bytes (default signed)
signed long long;
unsigned long long;

float phi;                                //floating-point : 4 bytes  
double phi;                               //floating-point : 8/4 bytes  
long double;                              
```

## Variables 

Store value into memory address.

```c
int c_nt;                                 //naming convention, no special symbols other than _ 
int cnt,Cnt;                              //is case sensitive cnt != Cnt
int cnt;                                  //declare 
int cnt = 0;                              //declare and initialize 
int cnt,cnt1,cnt2;                        //multi declare 
int cnt,cnt1=10,cnt2;                     //multi declare and initialize 
```

## Variables Storage Classes 

Defines the scope and lifetime of variables.

```c
//local variables
auto int a;                               //block scope (default)
register int b;                           //block scope,stored in a register not in ram 
static int c;                             //keep variable in existence during the program lifetime 

// global variables
static int c;                             //restrict access from another object file
extern int d;                             //reference a global variable in another object file    
```  

## Constants 

Store value into memory address once and forbid modifications (at compile time).

```c
const double phi = 1.6;                   //compiler forbid variable assignement after definition
```

## Operators

Perfom mathematical or logical function based on the values provided to the operator.

```c
// Arithmetic
c = a+b;                                  //add a and b 
c = a-b;                                  //substract b to a
c = a*b;                                  //a multiply by b
c = a/b;                                  //a divided by b
c = a%b;                                  //a modolo b (rest of the division)
c = a++;                                  //increment a 
c = ++a;                                  //increment a 
c = a--;                                  //decrement a
c = --a;                                  //decrement a

// Relational 
if (a==b)                                 //true if a equal b
if (a!=b)                                 //true if a different from b 
if (a>b)                                  //true if a greater than b
if (a<b)                                  //true if a smaller than b
if (a>=b)                                 //true if a greater or equal than b
if (a<=b)                                 //true if a smaller or equal than b 

// Logical 
if (a && b)                               //logical and between a,b 
if (a || b)                               //logical or between a,b
if (!a)                                   //not a 

// Bitwise
c = a & b;                                //bitwise and 
c = a | b;                                //bitwise or
c = a ˆ b;                                //bitwise xor
c = ~a;                                   //bitwise not 
c = a>>2;                                 //shift right 2 bits of a 
c = a<<2;                                 //shift left 2 bits of a 

// Assignement
a = 3;                                    //assign 3 to a 
a += 3;                                   //a = a + 3
a -= 3;                                   //a = a - 3
a *= 3;                                   //a = a * 3
a /= 3;                                   //a = a / 3
a %= 3;                                   //a = a % 3

// Ternary 
c = (a == b) ? 0 : 1                      //c = 0 if (a == b) otherwise c = 1

//Special 
sizeof(a);                                //return size of datatype 
&a;                                       //the memory address of a 
*ptr                                      //the value stored at address pointed by a pointer

location.x = 1;                           //access to user datatype member
locptr->x = 1;                            //access to user datatype member through pointer
arr[3];                                   //array subscripting

```

## Control flow 

Influence the order of execution of the statements.


```c
if (a == b){}                             //if 
if (a == b){}else{}                       //if..else
if (a == b){}else if (b ==c) {}           //if..else ladder

for (int a=0; a<3;a++){}                  //for loop

do {++a;} while (a<3);                    //do..while
while (a<3){++a;}                         //while

switch (a){                               //switch (string not supported)
  case 0: printf("%d",0); break;
  case 1: printf("%d",1); break;
  default: break;
}

break;                                    //exit from most inner loop or switch
continue;                                 //skip one iteration of most inner loop
return;                                   //return from a function 
```

## Pointers 

Variable that holds a memory location.

```c                          

int *iptr;                                //pointer to an int data type
void *vptr;                               //pointer not associated to any data type 
int (*fptr) (int,int);                    //pointer to a function 
int **pptr;                               //pointer to another pointer (not limited to two)

iptr = &cnt;                              //assign address of int variable to ptr
pptr = &iptr;                             //pptr points to pointer iptr which points to an int

ptr                                       //the memory address of the variable 
*ptr                                      //the value stored at that address
*ptr = 0;                                 //int variable pointed by ptr = 0
**pptr = 1;                               //int variable pointed by ptr = 1
```

## User Data Types 
### Enumeration 

Create a user datatype with a defined set of named integral constants.

```c
enum httpstatus {ok,created}              //httpstatus is a type with possible values 0 or 1
enum httpstatus {ok,created} response     //with response variable declaration
enum httpstatus {ok=200,created=201}      //explicit assignement of int values
enum {ok,created}                         //unnamed type, only values can be used  

enum httpstatus response = ok             //variable of type httpstatus with value 0
enum httpstatus error = 500               //value range not enforced at compile time 
int response = ok                         //enum values are int
```

### Structure 

Create a user datatype composed of other datatypes (compound datatype).

```c
struct coord {int x; int y;};             //coord is a coordinate type containing two ints
struct coord {int x, int y;} home         //with home variable declaration
struct coord {int x=1; int y=2;};         //error, no initialization in struct 
struct {int x; int y;} location           //unnamed struct, only location variable exist

struct coord location                     //variable of type coord 
struct coord location = {1,2}             //variable of type coord with initialization  
struct coord location = {.y=2,.x=1}       //with designated initializer

location.x = 1                            //access struct member 
locptr->x = 1                             //access struct member through pointer 
```

### Union 

Create a user datatype with only one member stored at a time.

```c
union ascii{char ch; int code;}           //ascii is a type of max size between char and int
union ascii{char ch; int code;} ascii_a   //with ascii_a variable declaration
union {char ch; int code;} ascii_a        //unnamed union, only ascii_a variable exist 

union ascii ascii_a                       //variable of type ascii
union ascii ascii_a = {'a'}               //variable of type ascii with initialization
union ascii ascii_a = {.ch= 'a'};         //with designated initializer 

ascii_a.ch = 'a';                         //access union member
asciiptr->ch = 'a';                       //access union member through pointer 
```

### Typedef 

Alias for existing types (basic,enum,struct,union).

```c
typedef unsigned char byte                //type byte = type unsigned char
typedef enum {ok,created} httpstatus      //type httpstatus = enum
typedef struct {int x; int y;} coord      //type coord = struct
typedef union {char ch; int code;} ascii  //type ascii = union

byte opcode                               //variable of type byte
coord location                            //variable of type coord 
httstatus response                        //variable of type htstat
ascii a                                   //variable of type asc
```

## Functions

Self-contained block of statements that can be executed repeatedly.

```c
void fib(void){}                          //declare a function with no parameter, no return
int fib(int a){}                          //declare a function which takes an int, return an int 
int res = fib(3);                         //calling fib function

//passing arguments to function is always by value 
int fib(int a){}                          //receive a copy of the int value
int fib(struct item it){}                 //receive a copy of the struct value
int fib(enum status st){}                 //receive a copy of the int value
int fib(union item it){}                  //receive a copy of the union value
int fib(int *ptr)(){}                     //receive a copy of the pointer value (an address)
int fib(int arr[])(){}                    //due to array decaying, same as above 

//returning value from a function is always by value
return a;                                 //return a copy of the value of a
struct item it; return it;                //return a complete copy of struct 
int* ptr; return ptr;                     //return a copy of the address 
```


## Arrays
### Static Arrays 

Size if fixed once defined, storage time is automatically managed by scope.

```c                          
int ops[3];                               //fixed array (immutable size defined at compile-time)
int ops[size];                            //variable array (immutable size defined at runtime)

int ops[3] = {1,2,3};                     //with initializer  
int ops[2] = {1,2,3};                     //error: size of array must > initializer list 
int ops[] = {1,2,3};                      //size defined by only initializer list 

char name[5] = "peter";                   //with string initializer
char name[] = "peter";                    //size defined by string size

int matrix[2][2] = {{0,1},{2,3}};         //multi-dimensional 

sizeof(ops)/sizeof(ops[0]);               //size of the array

//Decay: 
//Compiler replace array expression with a pointer to the first element (&a[0])
ops;                                      //decay to pointer int* = &ops[0]
ops[i];                                   //decay and subscript = *(ops + i elements) 

//Decay exceptions (&, sizeof, string literal)
&(ops);                                   //address of the array, not the one of the pointer
sizeof(ops);                              //sizeof of the array, not the one of the pointer
char[] name = "peter";                    //contains address of the array, not the pointer
```

### Dynamic Array 

Size is not fixed, storage is held until free is called.

```c
int size = 3;
int *ops = malloc(3*sizeof(int));         //request storage creation
int *rops = realloc(ops,4*sizeof(int));   //request reallocation with bigger size  
free(rops)                                //free memory

sizeof(ops);                              //not possible, responsibility of developer to store it 
ops[i];                                   //subscript = *(ops + i elements) 
```

## Preprocessind directives

```c
#define PI 3.14                         //Replace PI with 3.14 everywhere in the code 

//The include directive will replace the #include line with content of the file  
#include <stdio.h>                      //include standard lib (/usr/local/lib for library)
#include <cc34.h>                       //include external lib (gcc -lcc34 )
#include "my_file.h"                    //include header file
```

