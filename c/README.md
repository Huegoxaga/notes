# C

## Introduction

- It is a low-level language that relates closely to the way machines work
- It is used to write operating systems and other languages
- The C programming language was initially developed in AT&T labs by Professor Brian W. Kernighan and Dennis Ritchie, known as `K&R C`
- During the year 1970, `C` programming became very popular but without any serious startdardization to the language
- The non-official standard was called `K&R C`, which led to many ambiguities among different compiler programmers, and that led to non-portable codes
  - `K&R C` was the first non-official `C` standard
- In 1989 American National Standard Institute designed and approved first official `C` standard called `X3.159-1989`, and in 1990 it was approved by ISO as an international standard for C programming language: `ISO/IEC 9899:1990`
  - This is also called `ANSI C` or `C89` or `C90` standard in short
- The language underwent few more changes (addition of new features, syntaxes, data types, etc.) and newly updated standard released in 1999 under the ISO tag `ISO/IEC 9899:1999`
  - It is also called `C99` standard in short
- `C11` is an informal name for `ISO/IEC 9899:2011`, which is a new standard approved in December 2011. `C11` supersedes the C99 standard
- Official standards have backward compatibility

## Compiler

- MacOS can use `GCC` compiler
- Windows machine uses WinGW to compile
- run `brew install gcc` to install
- run `gcc <filename>` to compile
- Native compilation compile code for execution on the same machine:
- Cross compiler compiling code from one machine for another machine:
- Compiler can generates the following intermediate files
  - Preprocessed file, `.i` - a complete version of the source code include imported source code
  - Assembly instruction file, `.s` - parses and converts pre-processed file into assembly language
  - Machine Code file, `.o` - converts assembly language into opcodes
  - `.elf` - linker merges multiple `.o` files and `.a` files from imported library to form a executable file used for debugging
  - `.bin`, `.exe` or `.hex` - post process `.elf` file into pure binary for production
    - use tools like `objcopy`

### Compiler Flags

- `-save-temps` Save intermediate compilation results
- `-std` Compiling standard
  - `gnu11` - ISO C11 + gnu extension
  - `gnu99` - ISO C99 + gnu extension
  - `gnu90` - ISO C90 + gnu extension

## IDE

### Online IDE

- [OnlineGBD](https://www.onlinegdb.com) is a convenient online IDE for practicing and debugging C Code

## Syntax

- It is consisted of functions
- Each statement must end with a semicolon.
- The C programming language is case-sensitive,
- Single-line comments `//`
  - It is introduced in `C++` and adopted by some of the `C` compiler.
- Multi-line comments
  ```c
  /*
   * Multi-line comments
   */
  ```
- `#include <stdio.h>`, make functions from the `stdio` library available in `main()`
- main function is the entry point of the program
  ```c++
  int main() {
    printf("Hello, World!\n");
    return 0;
  }
  ```
  - main function return `0` to the calling process after execution.
  - `0` means the program executed successfully, other number indicates the program didn't execute successfully.

## Data Types

- `int`: integer, a whole number.
  - `0x` represents the number followed is hexadecimal
  - `0b` represents the number followed is binary
  - `uint8_t` - unsigned 8-bit integer
- `float`: floating point, a number with a fractional part.
- `double`: double-precision floating point value.
- `char`: single character.
  - It is signed
  - It has 1 byte storage size with value range from -128 to 127
  - A string is stored in a char array.
  - A character, such as `'b'`, is indicated by single quotation marks and cannot be treated as a string.

> Notes:
> C has no Boolean Type.

### Related Functions

- `sizeof(typename)` can be used to show the memory required by each type
  - The storage space required by each type varies by platform
  - returns number of bytes required by a certain type
  - Ex, `sizeof(int)`
- Type casting
  - Implicit Type Conversion
    - compiler automatically convert types in the same numerical operation
  - Explice Type Conversion
    - use `(typeName)variablesName;`
    - `(float) 1 / 2;`

## Variables

- Variable name must begin with either a letter or an underscore and can be composed of letters, digits, and the underscore character.
- Popular naming conventions is using lowercase letters with an underscore to separate words (`snake_case`).
- Variables must be declared as a data type
  - `int my_var;`
  - `int a, b;` declares multiple variables at once.
- `my_var = 42;` value assignment after declaration.
  - `int my_var = 42;`, optionally declaration and assignment can be written in one line.
- A constant stores a value that cannot be changed from its initial assignment.
  - Constant use uppercase identifiers.
  - `const double PI = 3.14;` constant declaration and assignment
  - Constants must be initialized with a value when declared.
  - `#define PI 3.1415` optionally one can define a constant using the #define preprocessor directive.
    - `#define` is a macro identifer that replace all `PI` in the code with its value before compiling.
    - This way of definine constants saves memory.
  - In a function declaration, pass in variable as constant can make sure its value is unchanged.
- A `volatile` keyword declares variables which will not be optimized by the compiler, the compiled code will always do what the instruction code ask to do, even if the logic is redundant

## Array

- Declaration and Initialization
  - `int array_name[25];` an array of init with 25 elements
  - `float prices[5] = {3.2, 6.55, 10.49, 1.25, 0.99};`
  - An array can be partially initialized, missing values will be set to 0
    - `float prices[5] = {3.2, 6.55};`
- Index starts at 0
- `x[0]` access array element,
- `x[1] = 260;` assign a value to an element.
- two-dimensional array
  - `int a[2][3];` 2 x 3 array
  - `{%raw%}int a[2][3] = {{3, 2, 6}, {4, 5, 20}};{%endraw%}`
  - More dimensions are supported.
- An array of pointers
  - `char *a[] = {"aaa", "bbb", "ccc"};`
  - This is the recommanded way to create an array of string. Optionally, use 2-D array for `char`.

## String

- A string in C is an array of characters that ends with a NULL character '\0'.
- Declaration
  ```c++
  char str1[6] = "hello";
  char str2[ ] = "world"; /* size 6 */
  char str3[6] = {'h', 'e', 'l', 'l', 'o', '\0'};
  char str4[ ] = {'h', 'e', 'l', 'l', 'o', '\0'}; /* size 6 */
  ```
  - During declaration, array size can be optionally stated. The size is the string length plus one for the NULL character.
  - `\0` has to included explicitly
  - A string literal is a text enclosed in double quotation marks.
  - `char *str = "hello";` is the string pointer declaration, it is considered a constant and cannot be changed from its initial value.

## Operators

### Arithmetic Operators

- `+` addition
- `-` subtraction
- `*` multiplication
- `/` division
  - Integer division - Integers dividing integers will get integers.
- `%` modulus division
  - Modulus division only works on integers.
- C may not evaluate a numeric expression from left to right among operators with the same precedence.
- Using parentheses `( )` to indicate which operations are to be performed first.

### Bitwise Operators

- `|` or
- `&` and
- `>>` right shift, move all values to the right to a certain position and fill the left with `0`
- `<<` left shift
- `~` not
- `^` xor
- Changing values on bits involves using the above oprator with a mask
  - A mask has either `0` or `1` on a certain position
- bit extraction uses right shift then use a mask to get the portion needed
- left shift to a number of position with a target value can quickly generate a mask
  - use `~` accordingly to generate mask with most value as `1`
- When overwrite a value to a certain position use `&` and a mask to reset all values in that position to zero, then use `|` to write new value to it

### Assignment Operators

- Apply numerical operation with itself by using the following:
  - `+=`
  - `-=`
  - `*=`
  - `/=`
  - `|=` can be used to add bit to an existing value
  - `&=` can be used to reset bit to an existing value with a mask
    - a mask has the reset position as `0` and all other positions as `1`
- Increment and Decrement
  - increment operator `++`
  - decrement operator `--`
- Prefix and Postfix
  - `++i`, the prefix form increments/decrements the variable and then uses it in the assignment statement.
  - `i++`, the postfix form uses the value of the variable first, before incrementing/decrementing it.

## Conditionals and Loops

- If statements
  ```c++
  if (expression)
    //statements;
  ```
  - statements can be a single statement or a code block enclosed by curly braces { }.
- relational operators
  - it can be used to form a Boolean expression, which returns true or false:
    - `<` less than
    - `<=` less than or equal to
    - `>` greater than
    - `>=` greater than or equal to
    - `==` equal to
    - `!=` not equal to
  - An expression that evaluates to a non-zero value is considered true.
    ```c++
    int in_stock = 20;
    if (in_stock)
      printf("Order received.\n");
    ```
- if-else statements
  ```c++
  if (condition)
    //statement
  else
    //statement
  ```
- If statements can be nested.
- conditional expression.
  - `x = (condition) ? statement1 : statement2;`
  - If true statement1 is returned, if false statement2 is returned
- Switch statement
  ```c++
  switch (expression) {
  case val1:
    //statements
  break;
  case val2:
    //statements
  break;
  default:
    //statements
  }
  ```
  - Without the break statement, program execution falls through to the next case statement.
- Logical operators
  - `&&` and
  - `||` or
  - `!` not
  - A compound Boolean expression is evaluated from left to right.
  - precedence, `!` > `&&` > `||`
  - Use `()` to change precedence
- While loop
  ```c++
  while (expression) {
    //statements
  }
  ```
- do-while loop
  ```c++
  do {
    //statements
  } while (expression);
  ```
  - The do-while loop always executes at least once
- `break;` exit loop
- `continue;` skip the rest code of this iteration.
- for loop
  ```c++
  int i;
  int max = 10;
  for (i = 0; i < max; i++) {
    printf("%d\n", i);
  }
  ```
- The for loop can contain multiple expressions separated by commas in each part.
  ```c++
  for (x = 0, y = num; x < y; i++, y--) {
    //statements;
  }
  ```
- Also, you can skip the initvalue, condition and/or increment.
  ```c++
  int i=0;
  int max = 10;
  for (; i < max; i++) {
    printf("%d\n", i);
  }
  ```
- Loops can also be nested.

## Function

- Declarations usually appear above the `main()` function, or in the header files
- Function definitions usually appear after the `main()` function, or in the source files
  ```c++
  #include <stdio.h>
  /* declaration */
  int square (int num);
  int main() {
    int x, result;
    x = 5;
    result = square(x);
    printf("%d squared is %d\n", x, result);
    return 0;
  }
  /* definition */
  int square (int num) {
    int y;
    y = num * num;
    return(y);
  }
  ```
- A function is not required to return a value, it will return `void` if not stated
- Variables declared outside all functions are global to the entire program.
- Function destroys its local variables and parameters upon exiting.
- `exit` function
  - `exit()` immediately stops the execution of a program and sends an exit code back to the calling process.
  - it closes any open file connections and processes.
  - return any value through an exit statement, but `0` for success and `-1` for failure are typical. The predefined `stdlib.h` macros `EXIT_SUCCESS` and `EXIT_FAILURE` are also commonly used. Ex, `exit(EXIT_FAILURE);`
- Static variables
  - It is declared in a function.
  - It has a local scope but are not destroyed when a function is exited.
  - When a variable need to be passed out of a function, it should be static.
  - `static int num_calls = 1;`
- A recursive function is one that calls itself and includes a base case, or exit condition, for ending the recursive calls.
  ```c++
  #include <stdio.h>
  //function declaration
  int factorial(int num);
  int main() {
    int x = 5;
    printf("The factorial of %d is %d\n", x, factorial(x));
    return 0;
  }
  //function definition
  int factorial(int num) {
    if (num == 1)
      return (1);
    else
      return (num * factorial(num - 1));
  }
  ```

## Pointers

- Memory Addresses
  - Assigned randomly whenever the program is executed.
  - The address value is an 8 digit hexadecimal.
  - Each address value stores 1 byte value.
- Get Memory Addresses of Variables
  - The `&` sign before the variable name is the address operator. It gives the memory address of a variable.
- A pointer is a variable that contains the address of another variable.
  - The address location is random every time the program is executed.
- Variable names for strings and arrays act as a pointer.
- Declaration
  ```c++
  int j = 8;
  int *p = NULL;
  p = &j;
  ```
  - Data type is required for a point to know where the next available address is, based on the amount of data required for the type.
  - Pointers should be initialized to NULL until they are assigned a valid location.
  - dereferencing, prepend dereference operator `*` to the pointer variable will get the value it points to. It is opposite to `&`.
- Pointer can be used to point another pointer.
  - Prepend `**` to the pointer that point to another pointer
  ```c++
  int x = 12;
  int *p = NULL
  int **ptr = NULL;
  p = &x;
  ptr = &p;
  ```
- Arithmetic operators can be applied to whatever the pointer is pointing to.
  - `y = *p + 2;`
  - `(*p)++;` parentheses are required for increments and decrements
- Pointer of an array
  - Array and string names are pointers, it points to the first element of the array.
- Address Arithmetic, for pointer `x`:
  - `x+1` or `x++` returns the memory location for the next element.
  - `x-1` or `x--` returns the memory location for the previous element.
  - If pointer point to an integer (4 bytes) `x++` will make the memory address value goes up by 4.
  - pointer addresses can also be compared by using `>`, `==` etc.
- Using pointer as parameters of a function to change the actual variables' values.
  ```c++
  void swap (int *num1, int *num2);
  int main() {
  int x = 25;
  int y = 100;
  printf("x is %d, y is %d\n", x, y);
  swap(&x, &y);
  printf("x is %d, y is %d\n", x, y);
  return 0;
  }
  void swap (int *num1, int *num2) {
  int temp;
  temp = *num1;
  *num1 = *num2;
  *num2 = temp;
  }
  ```
- A pointer can be returned in a function
  ```c++
  int * get_evens();
  int main() {
    int *a;
    int k;
    a = get_evens(); /* get first 5 even numbers */
    for (k = 0; k < 5; k++)
      printf("%d\n", a[k]);
    return 0;
  }
  int * get_evens() {
    static int nums[5];
    int k;
    int even = 0;
    for (k = 0; k < 5; k++) {
      nums[k] = even += 2;
    }
    return (nums);
  }
  ```
- Function Pointers
  - It points to executable code for a function in memory.
  - A function name points to the start of executable code.
    ```c++
    #include <stdio.h>
    void say_hello(int num_times); /* function */
    int main() {
      void (*funptr)(int);  /* function pointer */
      funptr = say_hello;  /* pointer assignment */
      funptr(3);  /* function call */
      return 0;
    }
    void say_hello(int num_times) {
      int k;
      for (k = 0; k < num_times; k++)
        printf("Hello\n");
    }
    ```
  - Function pointers can be stored in an array.
    - `int (*op[4])(int, int);` declares the array of function pointers
    - Each array element must have the same parameters and return type.
    - The statement `result = op[index](x, y);` executes the appropriate function
  - Function pointers can be passed as arguments to other functions.
    - A function pointer used as an argument is sometimes referred to as a callback function.
- the void pointer for variables
  - When the type for a pointer is unknown use the void pointer.
    - `void *ptr;`
    - It can be used for different types of data's memory location.
  - When dereferencing a void pointer, type casting is required for the pointer to the appropriate data type before dereferencing with `*`.
    - `* ((int *)ptr)`
  - cannot perform pointer arithmetic with void pointers, because the data size is unknown.
- the void pointer for functions
  - Using a `void *` return type allows for any return type. Similarly, parameters that are `void *` accept any argument type.
    - Input argument need to be cast when dereferencing with `*` before use.
  - `void * example (void *);`
  - It makes the function generic.

## Structures

- It is a user-defined data type that contains variables(members) of different data types.
  - The member of astructure can be of all basic types, strings, arrays, pointers, and other sturctures.
- The name of the structure is defined by the struct tag after keyword `struct`.
- Declaration
  ```c++
  struct sample {
      int id;
      char name[12];
      float value;
  };
  struct sample s1;
  struct sample s2;
  ```
- All members stores in a contiguous block of memery. The memory size of a structure can be determined by using `sizeof()`
- Initialization
  ```c++
  struct sample s3 = {1, "John", 23.32};
  //or
  struct sample s4;
  s4 = (struct sample) {1, "John", 23.32};
  //or
  struct sample s5 = {.name = "John", .id = 1, .value = 23.32};
  //or
  struct sample s6 = s5;
  ```
- Access Members using dot operator `.`, `s1.value = 77.7`.
  - Assign new string value to a member use `strcpy(s1.name, "new name")`
- `typydef` keyword
  - It can be used to declare structures, and keyword `struct` can be ignored in future when declaring variables.
    ```c++
    typedef struct {
      int id;
      char title[40];
      float hours;
    } course;
    course cs1;
    course cs2;
    ```
- The members of a structure may also be structures.
  - `c.center.x`
  - Nested curly braces are used to initialize members that are structs. `circle c = {4.5, {1, 3}};`
  - A struct definition must appear before it can be used inside another struct
- defines a pointer for structure. `struct myStruct *struct_ptr;`
- stores the address of the structure variable in the pointer. `struct_ptr = &struct_var;`
- accesses the value of the structure member `struct_ptr -> struct_mem;`
- Structures can be as function parameters
- Structures can be the elements of an array.

## Unions

- A union allows to store different data types in the same memory location among all of its members.
- Union members can be of any data type, including basic types, strings, arrays, pointers, and structures.
- The largest member data type is used to determine the size of the memory to share and then all members use this one location. This process also helps limit memory fragmentation
- Define unions
  ```cpp
  union val {
  int int_num;
  float fl_num;
  char str[20];
  };
  ```
- Declare unions
  ```cpp
  union val u1;
  union val u2;
  u2 = u1;
  ```
  - One union can be assigned to another of the same type.
- assignment
  ```cpp
  union val test;
  test.int_num = 123;
  test.fl_num = 98.76;
  strcpy(test.str, "hello")
  ```
  - The last assignment always overwrite the value
- Unions are often used within structures
  ```cpp
  typedef struct {
    char make[20];
    int model_year;
    int id_type; /* 0 for id_num, 1 for VIN */
    union {
      int id_num;
      char VIN[20];
    } id;
  } vehicle;
  vehicle car1;
  strcpy(car1.make, "Ford");
  car1.model_year = 2017;
  car1.id_type = 0;
  car1.id.id_num = 123098;
  ```
- A union can also contain a structure.
- A union pointer
  ```cpp
  union val {
    int int_num;
    float fl_num;
    char str[20];
  };
  union val info;
  union val *ptr = NULL;
  ptr = &info;
  ptr->int_num = 10;
  printf("info.int_num is %d", info.int_num);
  ```
  - When you want to access the union members through a pointer, the `->` operator is required.
    - `(*ptr).int_num` is the same as `ptr->int_num`
- Use union variable for a function that is read only, it won't change the original value of the union.
  ```cpp
  union id {
    int id_num;
    char name[20];
  };
  void show_id(union id item) {
    printf("ID is %d", item.id_num);
  }
  ```
- Use pointer parameters is used for a function to change the actual value in a union memory location,
  ```cpp
  union id {
    int id_num;
    char name[20];
  };
  void set_id(union id *item) {
    item->id_num = 42;
  }
  ```
- An array can store unions. Ex, `union union_name nums[10];`
  - Arrays of unions allow storing values of different types.

## Preprocessor

- The C preprocessor uses the `#` directives to make substitutions in program source code before compilation.
- `#` must be the first character on each line. There can be any amount of white space before `#` , between the `#` and the directive.
- No semicolons needed for the directives

### `#include` Directives

- It is used to include header files.
  - A header file declares a collection of functions and macros for a library
- The compile will replace the `#include` line by all the content of the included header file
- If any of the function declaration are used in `main()`, the compiler will find the implementation of the function in the source file in project folder or libraries
- If the `#include` directive is followed by header filename surrounded by brackets `<>`, the file will be searched for in the compiler include paths. `#include <stdio.h>`
  - The list of directories for header files is often referred to as the include path
  - The list of directories for libraries as the library search path or link path
- A user-defined header file is also given the `.h` extension, but is referred to with quotation marks, as in `"myutil.h"`. When quotation marks are used, the file is searched for in the source code directory. `#include "myutil.h"`

### `#define` Directives

- define directive is used to create object-like macros for constants based on values or expressions. `#define PI 3.14`
- It can also create function-like macros with arguments that will be replaced by the preprocessor. `#define AREA(r) (PI*r*r)`
- Enclose each parameter in parentheses to obtain the correct order of operations.
- If a `#` directive is lengthy, you can use the `\` continuation character to extend the definition over more than one line.
  ```cpp
    #define VERY_LONG_CONSTANT \
  23.678901
  #define MAX 100
  #define MIN 0
  #    define SQUARE(x) \
      x*x
  ```
- there are several standard predefined macros that are always available in a C program without requiring the `#define` directive:
  - `__DATE__` it stores The current date as a string in the format Mm dd yyyy
  - `__TIME__` it stores The current time as a string in the format hh:mm:ss
  - `__FILE__` it stores The current filename as a string
  - `__LINE__` it shows The current line number as an int value
  - `__STDC__` 1 its 1.

### `#undef` Directives

- It it used to undefining macros.

### Directives for Conditional Compilation

- Conditional Compilation of macros, it works with `#define`
  - `#ifdef`, check if a certain macros is defined.
  - `#ifndef`, check if a certain macros is not defined.
    ```cpp
    #include <stdio.h>
    #define RATE 0.08
    #ifndef TERM
      #define TERM 24
    #endif
    int main() {
      #ifdef RATE  /* this branch will be compiled */
        #undef RATE
        printf("Redefining RATE\n");
        #define RATE 0.068
      #else  /* this branch will not be compiled */
        #define RATE 0.068
      #endif
      printf("%f  %d\n", RATE, TERM);
      return 0;
    }
    ```
- Conditional compilation of segments of code
  - `#if`, `#else`, `#elif`, `#endif`
    ```cpp
    #define LEVEL 4
    int main() {
      #if LEVEL > 6
        /* do something */
      #elif LEVEL > 5
        /* else if branch */
      #elif LEVEL > 4
        /* another else if */
      #else
        /* last option here */
      #endif
      return 0;
    }
    ```
- The `defined()` preprocessor operator can be used with `#if`,
  ```cpp
  #if !defined(LEVEL)
    /* statements */
  #endif
  ```

### `#pragma` Directives

- Implementation and compiler specific.

### Directives for Errors

- `#error`, `#warning` Output an error or warning message An error halts compilation.

### Preprocessor Operators

- stringification operator
  - The `#` macro operator, also known as the stringizing operator. It tells the preprocessor to convert a parameter to a string constant.
  ```cpp
  #define TO_STR(x) #x
  printf("%s\n", TO_STR( 123\\12 ));
  ```
  - `#` of the `#x` is the stringification operator
  - `TO_STR( 123\\12 )` will be read by the compiler as string `"123\\12"` before compilation.
- Token pasting operator
  - The `##` operator appends, or "pastes", tokens together.
  ```cpp
  #define VAR(name, num) name##num
  int x1 = 125;
  int x2 = 250;
  int x3 = 500;
  printf("%d\n", VAR(x, 3));
  ```
  - `VAR(x, 3)` will be read by the compiler as `x3`.

## Standard Library

- import function with `#include <package_name.h>`

### `stdio.h`

- It defines function related input and output.
- `#include <stdio.h>`

##### Output

- `printf()` generates output
  - printf(“formatted string with format specifier (%d)”,variablesXToReplace%d);, Formatted output
  - Escape sequences begin with a backslash `\`:
    - `\n` new line
    - `\t` horizontal tab, four white spaces
    - `\\` backslash
    - `\b` backspace
    - `\r` carriage return, move cursor back to the beginning of the line and start to replace existing characters
    - `\v` vertical tab
    - `\'` single quote
    - `\"` double quote
    - `\0` null
  - `%[-][width].[precision]conversion_character`, Format specifier for printf
    - The optional `-` specifies left alignment of the data in the string.
    - The optional width gives the minimum number of characters for the data.
    - The period `.` separates the width from the precision.
    - The optional precision gives the number of decimal places for numeric data.
      - If `s` is used as the conversion character, then precision determines the number of characters to print.
    - The conversion character converts the argument, if necessary, to the indicated type:
      - `d` decimal
      - `ld` long decimal
      - `c`character
      - `s` string
      - `f` float
      - `e` scientific notation
      - `x` hexadecimal
    - To print the `%` symbol, use `%%` in the format string.
    - Example:
      ```c++
      printf("Color: %s, Number: %d, float: %5.2f \n", "red", 42, 3.14159);
      /* Color: red, Number: 42, float:  3.14  */
      printf("Pi = %3.2f", 3.14159);
      /* Pi = 3.14 */
      printf("Pi = %8.5f", 3.14159);
      /* Pi =   3.14159 */
      printf("Pi = %-8.5f", 3.14159);
      /* Pi = 3.14159 */
      printf("There are %d %s in the tree.", 22, "apples");
      /* There are 22 apples in the tree. */
      ```
- `putchar()` Outputs a single character.
- `fputs()`
  - `fputs(stringName, stdout);`
  - `stdout` means standard output
- The `puts()` function add a new line after each output.
  - `puts(stringName);`
- `putf()`
- `sprintf()` creates formatted strings. auto convert data types for output string.
  ```c++
  char output[100];
  char dept[ ] = "HR";
  int emp = 75;
  sprintf(output, "The %s dept has %d employees.", dept, emp);
  ```
  - It returns the output string length

##### Input

- `getchar()` Returns the value of the next single character input.
  - `char x = getxhar()`
- The gets() function is used to read a string.
  ```c++
  char a[100];
  gets(a);
  printf("You entered: %s", a);
  ```
- `scanf()` scans input that matches format specifiers.
  ```c++
  int a, b;
  scanf("%d %d", &a, &b);
  printf("You entered: %d and %d", a, b);
  ```
  - stops read input when a space is entered.
  - `scanf()` read variable addresses(pointers).
  - if type does not match, it automatically convert input type, it cannot read when the convertion cannot be made.
  - For format specifiers, Blanks, tabs, and newlines are ignored.
  - `%[*][max_field]conversion character` - The optional `*` will skip the input field. - The optional max_width gives the maximum number of characters to assign to an input field. - The conversion character converts the argument to the defined type, it uses the following letters as specifier:
    - `%d` for double
    - `%f` for float
    - `%c` for character
    - `%s` for string
    - `%x` for hexadecimal
    - Ex, `%*3f` It will take or convert input to a float with 3 digit and it will be ignored.
- `gets()` stop read input after newline(enter key).
  ```c++
  char input[10];
  int num;
  printf("Enter a number: ");
  gets(input);
  num = atoi(input);
  ```
- `fgets()` similar with `gets()` but limit max input size
  - it stores newline characters.
  - it prevents buffer overflow, which happens when the string array size is smaller than the input size.
  ```c++
  char full_name[50];
  printf("Enter your full name: ");
  fgets(full_name, 50, stdin);
  ```
  - `stdin` is the pointer for keyboard inputs
  - It read a input with 49 character(lat one is\0)
- `sscanf()` for scanning a string for values.
  ```c++
  char info[ ] = "Snoqualmie WA 13190";
  char city[50];
  char state[50];
  int population;
  sscanf(info, "%s %s %d", city, state, &population);
  ```

##### Parse Strings

- `int atoi(str)` Stands for ASCII to integer. Converts string numbers to the equivalent int value. 0 is returned if the first character is not a number or no numbers are encountered.
- `double atof(str)` Stands for ASCII to float. Converts string numbers to the equivalent double value. 0.0 is returned if the first character is not a number or no numbers are encountered.
- `long int atol(str)` Stands for ASCII to long int. Converts str to the equivalent long integer value. 0 is returned if the first character is not a number or no numbers are encountered.
- `strtol()` is similar with `atol()` but have error handling.

##### File I/O

- open and close a file:
  - `filePointer = fopen(filename, mode)` Returns a pointer of type FILE
    - It opens files using the following modes.
      - `r` open for reading (file must exist)
      - `w` open for writing (file need not exist)
      - `a`open for append (file need not exist)
      - `r+` open for reading and writing from beginning
      - `w+` open for reading and writing, overwriting file
      - `a+` open for reading and writing, appending to file
      - add `b` for binary files
    - If a file cannot be opened, NULL is returned.
    - If there is an error when opening the file, a `-1` error code is returned to the system.
  - `fclose(filePointer)` Closes file opened with FILE pointer
    - returning `0` if close was successful.
    - EOF (end of file) is returned if there is an error in closing.
  - For example:
    ```cpp
    #include <stdio.h>
    int main() {
      FILE *fptr;
      fptr = fopen("myfile.txt", "w");
      if (fptr == NULL) {
        printf("Error opening file.");
        return -1;
      }
      fclose(fptr);
      return 0;
    }
    ```
    - When a string literal is used to specify a filename, the escape sequence `\\` indicates a single backslash.
- read a file
  - fgetc(fp) Returns the next character from the file pointed to by fp. If the end of the file has been reached, then EOF is returned.
  - fgets(buff, n, fp) Reads n-1 characters from the file pointed to by fp and stores the string in buff. A NULL character '\0' is appended as the last character in buff. If fgets encounters a newline character or the end of file before n-1 characters is reached, then only the characters up to that point are stored in buff.
  - fscanf(fp, conversion_specifiers, vars) Reads characters from the file pointed to by fp and assigns input to a list of variable pointers vars using conversion_specifiers. As with scanf, fscanf stops reading a string when a space or newline is encountered.
  - For example:
    ```cpp
    #include <stdio.h>
    int main() {
      FILE *fptr;
      int c, stock;
      char buffer[200], item[10];
      float price;
      /* myfile.txt: Inventory\n100 Widget 0.29\nEnd of List */
      fptr = fopen("myfile.txt", "r");
      fgets(buffer, 20, fptr); /* read a line */
      printf("%s\n", buffer);
      fscanf(fptr, "%d%s%f", &stock, item, &price); /* read data */
      printf("%d %s %4.2f\n", stock, item, price);
      while ((c = getc(fptr)) != EOF) /* read the rest of the file */
        printf("%c", c);
      fclose(fptr);
      return 0;
    }
    ```
- write a file
  - When writing to a file, newline characters `\n` must be explicitly added.
  - `fputc(char, fp)` Writes character char to the file pointed to by fp.
  - `fputs(str, fp)` Writes string str to the file pointed to by fp.
  - `fprintf(fp, str, vars)` Prints string str to the file pointed to by fp. str can optionally include format specifiers and a list of variables vars.
  - For example:
  ```cpp
  FILE *fptr;
  char filename[50];
  printf("Enter the filename of the file to create: ");
  gets(filename);
  fptr = fopen(filename, "w");
  /* write to file */
  fprintf(fptr, "Inventory\n");
  fprintf(fptr, "%d %s %f\n", 100, "Widget", 0.29);
  fputs("End of List", fptr);
  ```
- Binary Files I/O - To write entire blocks of memory to a file
  - fwrite(ptr, item_size, num_items, fp) Writes num_items items of item_size size from pointer ptr to the file pointed to by file pointer fp.
  - fread(ptr, item_size, num_items, fp) Reads num_items items of item_size size from the file pointed to by file pointer fp into memory pointed to by ptr.
  - fclose(fp) Closes file opened with file fp, returning 0 if close was successful. EOF is returned if there is an error in closing.
  - feof(fp) Returns 0 when the end of the file stream has been reached.
  - For example:
    ```cpp
    FILE *fptr;
    int arr[10];
    int x[10];
    int k;
    /* generate array of numbers */
    for (k = 0; k < 10; k++)
    arr[k] = k;
    /* write array to file */
    fptr = fopen("datafile.bin", "wb");
    fwrite(arr, sizeof(arr[0]), sizeof(arr)/sizeof(arr[0]), fptr);
    fclose(fptr);
    /* read array from file */
    fptr = fopen("datafile.bin", "rb");
    fread(x, sizeof(arr[0]), sizeof(arr)/sizeof(arr[0]), fptr);
    fclose(fptr);
    /* print array */
    for (k = 0; k < 10; k++)
    printf("%d", x[k]);
    ```
- Control pointer for binary file
  - `ftell(fp)` Returns a long int value corresponding to the fp file pointer position in number of bytes from the start of the file.
  - `fseek(fp, num_bytes, from_pos)` Moves the fp file pointer position by num_bytes bytes relative to position from_pos, which can be one of the following constants:
    - `SEEK_SET` start of file
    - `SEEK_CUR` current position
    - `SEEK_END` end of file
  - For example:
    ```cpp
    typedef struct {
    int id;
    char name[20];
    } item;
    int main() {
      FILE *fptr;
      item first, second, secondf;
      /* create records */
      first.id = 10276;
      strcpy(first.name, "Widget");
      second.id = 11786;
      strcpy(second.name, "Gadget");
      /* write records to a file */
      fptr = fopen("info.dat", "wb");
      fwrite(&first, 1, sizeof(first), fptr);
      fwrite(&second, 1, sizeof(second), fptr);
      fclose(fptr);
      /* file contains 2 records of type item */
      fptr = fopen("info.dat", "rb");
      /* seek second record */
      fseek(fptr, 1\*sizeof(item), SEEK_SET);
      fread(&secondf, 1, sizeof(item), fptr);
      printf("%d %s\n", secondf.id, secondf.name);
      fclose(fptr);
      return 0;
    }
    ```

##### Error Handling

- `feof(fp)` Returns a nonzero value if the end of stream has been reached, 0 otherwise. `feof` also sets EOF.
- `ferror(fp)` Returns a nonzero value if there is an error, 0 for no error.
  ```cpp
  FILE *fptr;
  int c;
  errno = 0;
  fptr = fopen("myfile.txt", "r");
  if (fptr == NULL) {
    fprintf(stderr, "Error opening file. %s\n", strerror(errno));
    exit(EXIT_FAILURE);
  }
  while ((c = getc(fptr)) != EOF) /* read the rest of the file */
    printf("%c", c);
  if (ferror(fptr)) {
    printf("I/O error reading file.");
    exit(EXIT_FAILURE);
  }
  else if (feof(fptr)) {
    printf("End of file reached.");
  }
  ```

### `string.h`

- string functions
- `#include <string.h>`
- `strlen(str)` - get length of a string not include `\0`
- `strcat(str1, str2)` - merge two strings returns a pointer to str1.
- `strcpy(str1, str2)` - Copies str2 to str1.
- `strlwr(str)` - convert string to lower case
- `strupr(str)` - conver string to upper case
- `strrev(str)` - reverse string
- `strcmp(str1, str2)` - compare two strings
- `strncat(str1, str2, n)` Appends (concatenates) first n characters of str2 to the end of str1 and returns a pointer to str1.
- `strncpy(str1, str2, n)` Copies the first n characters of str2 to str1.
- `strcmp(str1, str2)` Returns 0 when str1 is equal to str2, less than 0 when str1 < str2, and greater than 0 when str1 > str2.
- `strncmp(str1, str2, n)` Returns 0 when the first n characters of str1 is equal to the first n characters of str2, less than 0 when str1 < str2, and greater than 0 when str1 > str2.
- `strchr(str1, c)` Returns a pointer to the first occurrence of char c in str1, or NULL if character not found.
- `strrchr(str1, c)` Searches str1 in reverse and returns a pointer to the position of char c in str1, or NULL if character not found.
- `strstr(str1, str2)` Returns a pointer to the first occurrence of str2 in str1, or NULL if str2 not found.

##### Error handling

- `strerror()` returns a pointer to the error message text according to the argument `errno`.
  ```cpp
  FILE *fptr;
  errno = 0;
  fptr = fopen("file.txt", "r");
  if (fptr == NULL) {
    fprintf(stderr, "%s\n", strerror(errno));
    exit(EXIT_FAILURE);
  }
  ```
- Use the following code can print out message for all error codes
  ```cpp
  for (int x = 0; x < 135; x++)
    fprintf(stderr, "%d: %s\n", x, strerror(x));
  ```

### `stdlib.h`

##### Sort

- `qsort()` Quick Sort
  - Declaration, `void qsort(void *base, size_t num, size_t width, int (*compare)(const void *, const void *))`
  - `void *base` A void pointer to the array.
  - `size_t num` The number of elements in the array.
  - `size_t` width The size of an element.
  - `int (*compare (const void *, const void *)` A function pointer which has two arguments and returns:
    - `0` when the arguments have the same value.
    - `<0` when arg1 comes before arg2.
    - `>0` when arg1 comes after arg2.
  - Example:
    ```c++
    #include <stdio.h>
    #include <stdlib.h>
    int compare (const void *, const void *);
    int main() {
      int arr[5] = {52, 23, 56, 19, 4};
      int num, width, i;
      num = sizeof(arr)/sizeof(arr[0]);
      width = sizeof(arr[0]);
      qsort((void *)arr, num, width, compare);
      for (i = 0; i < 5; i++)
        printf("%d ", arr[ i ]);
      return 0;
    }
    int compare (const void *elem1, const void *elem2) {
      if ((*(int *)elem1) == (*(int *)elem2))
        return 0;
      else if ((*(int *)elem1) < (*(int *)elem2))
        return -1;
      else
        return 1;
    }
    ```

##### Memory Management

- Types of memory allocation
  - Stack Allocation
    - All data types with known sizes is auto managed by CPU
    - They are allocated in contiguous blocks of memory.
    - Ex, basic data types, array.
    - When the stack memory is full, it causes stack overflow exception.
  - Static Allocation
    - It is initilzed by the compiler and exists throughout the entire life of the program.
    - global and static variables are allocated here.
  - Heap Allocation
    - It is a dynamic memory managed with pointers that point to newly allocated blocks of memory.
    - Need to be managed by the programmer.
      - C has no garbage collection, not releasing memory when no pointer points the memory will cause memory leak.
      - A space leak occurs when a computer program uses more memory than necessary.
- `stdlib.h` library provides the following function for memory management.
  - `malloc(bytes)` Returns a pointer to a contiguous block of memory that is of size bytes.
    ```cpp
    int *ptr;
    /* a block of 10 ints */
    ptr = malloc(10 * sizeof(*ptr));
    if (ptr != NULL) {
      *(ptr + 2) = 50;  /* assign 50 to third int */
    }
    ```
    - If the allocation is unsuccessful, NULL is returned. Because of this, you should include code to check for a NULL pointer.
  - `calloc(num_items, item_size)` Returns a pointer to a contiguous block of memory that has `num_items` items, each of size `item_size` bytes. Typically used for arrays, structures, and other derived data types. The allocated memory is initialized to `0`.
    ```cpp
    typedef struct {
      int num;
      char *info;
    } record;
    record *recs;
    int num_recs = 2;
    int k;
    char str[ ] = "This is information";
    recs = calloc(num_recs, sizeof(record));
    if (recs != NULL) {
      for (k = 0; k < num_recs; k++) {
        (recs+k)->num = k;
        (recs+k)->info = malloc(sizeof(str));
        strcpy((recs+k)->info, str);
      }
    }
    ```
  - `realloc(ptr, bytes)` Resizes the memory pointed to by ptr to size bytes. The newly allocated memory is not initialized.
    ```cpp
    int *ptr;
    ptr = malloc(10 * sizeof(*ptr));
    if (ptr != NULL) {
      *(ptr + 2) = 50;  /* assign 50 to third int */
    }
    ptr = realloc(ptr, 100 * sizeof(*ptr));
    *(ptr + 30) = 75;
    ```
  - `free(ptr)` Releases the block of memory pointed to by `ptr`. to make the block available to be allocated again. Ex, `free(ptr);`
- When allocating memory for a string pointer, you may want to use string length rather than the sizeof operator
  - otherwise, be sure to include one extra byte for the NULL character `\0`.

### `errno.h`

- It defines the error code as a global variable named `errno`.
- Optionally it can be declared with the statement `extern int errno;`
- It need to be set to `0` before calling a library function.
- To output the error code stored in errno, It is suggested to use `fprintf` to print to the `stderr` file stream.
  ```cpp
  #include <stdio.h>
  #include <stdlib.h>
  #include <errno.h>
  // extern int errno;
  int main() {
    FILE *fptr;
    errno = 0;
    fptr = fopen("nonexistantfile.txt", "r");
    if (fptr == NULL) {
      fprintf(stderr, "Error opening file. Error code: %d\n", errno);
      exit(EXIT_FAILURE);
    }
    fclose(fptr);
    return 0;
  }
  ```
- use `perror()` for a more descriptive error message
  - `perror()` must include a string that will precede the actual error message.
  - Example:
    ```c
    FILE *fptr;
    errno = 0;
    fptr = fopen("nonexistantfile.txt", "r");
    if (fptr == NULL) {
      perror("Error");
      exit(EXIT_FAILURE);
    }
    ```
    - The argument for `perror()` is the error message title.

### `math.h`

##### Error handling

- Some of the mathematical functions set `errno` to pre-defined macro value automatically.
  - It will be `EDOM` when a domain is out of range.
  - It will be `ERANGE` when there is a range error.
