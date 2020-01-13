# C
* It is a low-level language that relates closely to the way machines work

#include <stdio.h>
The header file package defines function related to input and output

This is the main function, the entry point of the program.
int main() {
  printf("Hello, World!\n");
  return 0;
}
Escape sequences begin with a backslash \:
\n new line
\t horizontal tab
\\ backslash
\b backspace
\' single quote
\" double quote

Format specifier for printf
The optional - specifies left alignment of the data in the string.
The optional width gives the minimum number of characters for the data.
The period . separates the width from the precision.
The optional precision gives the number of decimal places for numeric data. If s is used as the conversion character, then precision determines the number of characters to print.
The conversion character converts the argument, if necessary, to the indicated type:
d decimal
c character
s string
f float
e scientific notation
x hexadecimal

To print the % symbol, use %% in the format string.
```
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

%[-][width].[precision]conversion character


Each statement must end with a semicolon.
The C programming language is case-sensitive,
Single-line comments//
Multi-line comments``/*  */``

return 0;
This statement terminates the main() function and returns the value 0 to the calling process.


data types:
int: integer, a whole number.
float: floating point, a number with a fractional part.
double: double-precision floating point value.
char: single character.
A string is stored in a char array.

Note: C has no Boolean Type.

amount of storage required for each type varies by platforms use built-in sizeof operator to check details.

sizeof(int);
sizeof(float);
sizeof(double);
sizeof(char);
return size in bytes for each data type.

Formatted output

printf(“formatted string with format specifier (%d)”,variablesXToReplace%d);

%d for double
%f for float
%c for character
%s for string
%x for hexadecimal

Variable name must begin with either a letter or an underscore and can be composed of letters, digits, and the underscore character.

Common naming conventions is using lowercase letters with an underscore to separate words (snake_case).

int my_var;  declared as a data type
my_var = 42; initialize (assign an initial value) a variable

  int a, b;  declares multiple at once.

A constant stores a value that cannot be changed from its initial assignment.
Constant use uppercase identifiers.
const double PI = 3.14;
Constants must be initialized with a value when declared.

Another way to define a constant is with the #define preprocessor directive.
#include <stdio.h>

#define PI 3.14

# is the macro Identifier?
Before compilation, the preprocessor replaces every macro identifier in the code with its corresponding value from the directive. In this case, every occurrence of PI is replaced with 3.14.
The second method doesn’t use memory.

getchar() Returns the value of the next single character input.
The gets() function is used to read a string.
char a[100];
gets(a);
printf("You entered: %s", a);

scanf() scans input and convert input that matches format specifiers.
  int a;
  scanf("%d. ", &a);

  Input: 12.3.

  printf("You entered: %d", a);

  Output: You entered: 12

For format specifiers
Blanks, tabs, and newlines are ignored.

%[*][max_field]conversion character
The optional * will skip the input field.
The optional max_width gives the maximum number of characters to assign to an input field.
The conversion character converts the argument, if necessary, to the indicated type:
d decimal
c character
s string
f float
x hexadecimal

int x, y;
char text[20];

scanf("%2d %d %*f %5s", &x, &y, text);
/* input: 1234  5.7  elephant */
printf("%d  %d  %s", x, y, text);
/* output: 12  34  eleph */

The & sign before the variable name is the address operator. It gives the address, or location in memory, of a variable. This is needed because scanf places an input value at a variable address.
Memory addresses are represented by an 8 digit hexadecimal number.
string variable name acts as a pointer, it doesn’t need &.

Multiple inputs with scanf
  scanf("%d %d", &a, &b);
scanf() stops reading as soon as it encounters a space

putchar() Outputs a single character.
The puts() function is used to display output as a string.

C supports arithmetic operators + (addition), - (subtraction), * (multiplication), / (division), and % (modulus division).

Integer division:
Integers dividing integers will get integers.

Modulus division only works on integers.

C may not evaluate a numeric expression as desired when the associative property allows any order.
using parentheses ( ) to indicate which operations are to be performed first.

type casting
(typeName)variablesName
(float) 1 / 2;

assignment operator
=
+=
-=
*=
/=

Increment & Decrement
increment operator ++
decrement operator --
++i
The prefix form increments/decrements the variable and then uses it in the assignment statement.
i++
The postfix form uses the value of the variable first, before incrementing/decrementing it.

If statements
if (expression)
  statements
statements can be a single statement or a code block enclosed by curly braces { }.

relational operators
it can be used to form a Boolean expression, which returns true or false:
<    less than
<=  less than or equal to
>    greater than
>=  greater than or equal to
==  equal to
!=   not equal to


An expression that evaluates to a non-zero value is considered true.

int in_stock = 20;
if (in_stock)
  printf("Order received.\n");

if - else if statements
if (condition)
    //statement
 else if
    //statement
   else
     //statement
 If statements can be nested.

conditional expression.
The ?: operator
It can have only one statement associated with the if and the else.

 x = (condition) ?  statement1 : statement2;
If true statement1 is returned, if false statement2 is returned

switch statement
switch (expression) {
  case val1:
    statements
  break;
  case val2:
    statements
  break;
  default:
    statements
}

Without the break statement, program execution falls through to the next case statement.

Logical operators
&& and
||    or
!     not

A compound Boolean expression is evaluated from left to right.
precedence
! > && > ||
Use () to change precedence

While loop
while (expression) {
  statements
}

do-while loop
do {
  statements
} while (expression);

The do-while loop always executes at least once

break; exit loop
continue; skip the rest code of this iteration.

for loop

for (initvalue; condition; increment) {
  statements;
}


int i;
int max = 10;

for (i = 0; i < max; i++) {
  printf("%d\n", i);
}

The for loop can contain multiple expressions separated by commas in each part.

for (x = 0, y = num; x < y; i++, y--) {
  statements;
}

Also, you can skip the initvalue, condition and/or increment.

int i=0;
int max = 10;
for (; i < max; i++) {
  printf("%d\n", i);
}

Loops can also be nested.


Function
A function is not required to return a value, in this case use void.



Declarations usually appear above the main() function.
Function definitions usually appear after the main() function.

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

Variables declared outside all functions are global to the entire program.
function destroys its local variables and parameters upon exiting.

Static variables have a local scope but are not destroyed when a function is exited.

static int num_calls = 1;

A recursive function is one that calls itself and includes a base case, or exit condition, for ending the recursive calls.

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

  if (num == 1)  /* base case */
    return (1);
  else
    return (num * factorial(num - 1));
}


Array

int array_name[25];  //an array of init with 25 elements

or

float prices[5] = {3.2, 6.55, 10.49, 1.25, 0.99};
An array can be partially initialized, missing values will be set to 0
float prices[5] = {3.2, 6.55};

Index starts at 0
To access array element
printf("The second element is %d\n", x[1]); /* 45 */
To change array element
x[1] = 260;
two-dimensional array

int a[2][3]; /* A 2 x 3 array */

int a[2][3] = {
  {3, 2, 6},
  {4, 5, 20}
};
More dimensions are supported.



Pointers


A pointer is a variable that contains the address of another variable.
The address value is an 8 digit hexadecimal.

Declaration
int j = 8;
int *p = NULL;
p = &j;

Pointers should be initialized to NULL until they are assigned a valid location.

dereferencing
Print *p will get the value it points to, which is 8.

Pointer can be used to point another pointer.
This type of variable declaration uses **, and can be assigned the address of another pointer, as in:
int x = 12;
int *p = NULL
int **ptr = NULL;
p = &x;
ptr = &p;

Arithmetic operators can be applied to whatever the pointer is pointing to.

y = *p + 2;

(*p)++;    //parentheses are required for increments and decrements

For a pointer of array x
x is the first element of a
*(x+1) or *(x++) is the second element and so on.

If pointer point to an integer (4 bytes) x++ will make the hexadecimal value goes up by 4.
Using pointer can change the actual values of functions.

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

Array and string names are pointers wu need  to passing an array name to a function is passing a pointer to the array.

Pointer c can be returned in a function

String
A string in C is an array of characters that ends with a NULL character '\0'.

char str1[6] = "hello";
char str2[ ] = "world";  /* size 6 */
During declaration, array size can be optionally stated. The size is the string length plus one for the NULL character.

Or

char str3[6] = {'h', 'e', 'l', 'l', 'o', '\0'};

char str4[ ] = {'h', 'e', 'l', 'l', 'o', '\0'}; /* size 6 */
// \0 has to included explicitly
A string literal is a text enclosed in double quotation marks.

A string pointer declaration such as char *str = "stuff"; is considered a constant and cannot be changed from its initial value.


#include <string.h>
strlen() - get length of a string not include \0

strcat() - merge two strings returns a pointer to str1.
strcpy() - Copies str2 to str1.
strlwr() - convert string to lower case
strupr() - conver string to upper case
strrev() - reverse string
strcmp() - compare two strings
strncat(str1, str2, n) Appends (concatenates) first n characters of str2 to the end of str1 and returns a pointer to str1.
strncpy(str1, str2, n) Copies the first n characters of str2 to str1.
strcmp(str1, str2) Returns 0 when str1 is equal to str2, less than 0 when str1 < str2, and greater than 0 when str1 > str2.
strncmp(str1, str2, n) Returns 0 when the first n characters of str1 is equal to the first n characters of str2, less than 0 when str1 < str2, and greater than 0 when str1 > str2.
strchr(str1, c) Returns a pointer to the first occurrence of char c in str1, or NULL if character not found.
strrchr(str1, c) Searches str1 in reverse and returns a pointer to the position of char c in str1, or NULL if character not found.
strstr(str1, str2) Returns a pointer to the first occurrence of str2 in str1, or NULL if str2 not found.
strtol()



The stdio.h library contains the following functions for converting a string to a number:
int atoi(str) Stands for ASCII to integer. Converts str to the equivalent int value. 0 is returned if the first character is not a number or no numbers are encountered.
double atof(str) Stands for ASCII to float. Converts str to the equivalent double value. 0.0 is returned if the first character is not a number or no numbers are encountered.
long int atol(str) Stands for ASCII to long int. Converts str to the equivalent long integer value. 0 is returned if the first character is not a number or no numbers are encountered.

  char input[10];
  int num;

  printf("Enter a number: ");
  gets(input);
  num = atoi(input);




Input
scanf(), gets(), and fgets() functions.


fgets()
char full_name[50];
printf("Enter your full name: ");
fgets(full_name, 50, stdin);
stdin is the pointer for keyboard inputs

It read a input with 49 character(lat one is\0)


fputs()
fputs(stringName, stdout);
stdout means standard output

The puts() function takes only a string argument and add a new line.
puts(stringName);

Others output function
fputs(), putf(), and printf() functions.

sprintf()
A formatted string can be created with the sprintf() function.

  char info[100];
  char dept[ ] = "HR";
  int emp = 75;
  sprintf(info, "The %s dept has %d employees.", dept, emp);


sscanf() for scanning a string for values.

  char info[ ] = "Snoqualmie WA 13190";
  char city[50];
  char state[50];
  int population;
  sscanf(info, "%s %s %d", city, state, &population);


Character
A character, such as 'b', is indicated by single quotation marks and cannot be treated as a string.
