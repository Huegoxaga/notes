# C

## Introduction

- It is a low-level language that relates closely to the way machines work
- It is used to write operating systems and other languages.

## Syntax

- Each statement must end with a semicolon.
- The C programming language is case-sensitive,
- Single-line comments `//`
  - It is introduced in `C++` and adopted by some of the C compiler.
- Multi-line comments
  ```c
  /*
   * Multi-line comments
   */
  ```
- `#include <stdio.h>`, this is the header file included files that imports function.
- main function is the entry point of the program
  ```c++
  int main() {
    printf("Hello, World!\n");
    return 0;
  }
  ```
  - main function return 0 to the calling process after execution.
  - 0 means the program executed successfully, other number indicates the program has failed.

## Data Types

- int: integer, a whole number.
- float: floating point, a number with a fractional part.
- double: double-precision floating point value.
- char: single character.
  - A string is stored in a char array.
  - A character, such as `'b'`, is indicated by single quotation marks and cannot be treated as a string.

> Notes:
> C has no Boolean Type.

### Related Functions

- `sizeof(typename)` can be used to show the memory required by each type
  - The storage space required by each type varies by platform
  - returns number of bytes required by a certain type.
  - Ex, `sizeof(int)`
- Type casting
  - Implicit Type Conversion
    - compiler automatically convert types in the same numerical operation.
  - Explice Type Conversion
    - use `(typeName)variablesName;`
    - `(float) 1 / 2;`

## Variables

- Variable name must begin with either a letter or an underscore and can be composed of letters, digits, and the underscore character.
- Popular naming conventions is using lowercase letters with an underscore to separate words (snake_case).
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
  - `int a[2][3] = {{3, 2, 6}, {4, 5, 20}};`
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
    - `\t` horizontal tab
    - `\\` backslash
    - `\b` backspace
    - `\'` single quote
    - `\"` double quote
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
  char info[100];
  char dept[ ] = "HR";
  int emp = 75;
  sprintf(info, "The %s dept has %d employees.", dept, emp);
  ```

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

### `stdlib.h`

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

## Operators

#### Arithmetic Operators

- `+` addition
- `-` subtraction
- `*` multiplication
- `/` division
  - Integer division - Integers dividing integers will get integers.
- `%` modulus division
  - Modulus division only works on integers.
- C may not evaluate a numeric expression from left to right among operators with the same precedence.
- Using parentheses `( )` to indicate which operations are to be performed first.

#### Assignment Operators

- Apply numerical operation with itself by using the following:
  - `+=`
  - `-=`
  - `*=`
  - `/=`
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
  - Use () to change precedence
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

- Declarations usually appear above the main() function.
- Function definitions usually appear after the main() function.
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
- A function is not required to return a value, in this case use void.
- Variables declared outside all functions are global to the entire program.
- Function destroys its local variables and parameters upon exiting.
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
  - If pointer point to an integer (4 bytes) `x++` will make the hexadecimal value goes up by 4.
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
