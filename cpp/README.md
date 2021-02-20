# `C++`

## Introduction

- It is a general-purpose programming language.
- It was derived from `C`, and is largely based on it.
- It needs the installation of a compiler to run.
  - `GNU GCC` is one of the popular compilers available for `C++`
- `C++` source files have `.cpp`, `.cp` or `.c` extensions.
- Source file need to be complied to run.

## Syntax

- Whitespace, such as spaces, tabs, and newlines, is also ignored,
- In general, blank lines serve to improve the code's readability and structure.
- The `C++` compiler ignores blank lines.
- Each statement must end with a semicolon.
- The `C++` programming language is case-sensitive,
- Single-line comments `//`
  - It tells the compiler to ignore everything that follows, until the end of the line.
- Multi-line comments
  ```cpp
  /*
   * Multi-line comments
   */
  ```
- A block is a set of logically connected statements, surrounded by curly braces (`{}`).
- `#include <iostream>`, this is the header file included files that imports function.
- `using namespace std`, inform the compiler, the selection of namespace.
- main function is the entry point of the program
  ```cpp
  int main() {
    cout << "Hello world!"
    return 0;
  }
  ```
  - main function return 0 to the calling process after execution.
  - The line return 0; terminates the main() function and causes it to return the value 0 to the calling process. A non-zero value (usually of 1) signals abnormal termination.
  - If the return statement is left off, the `C++` compiler implicitly inserts `return 0;` to the end of the `main()` function.

## Data Types

- The operating system allocates memory and selects what will be stored in the reserved memory based on the variable's data type.
- The data type defines the proper use of a variable identifier, what kind of data can be stored, and which types of operations can be performed.
- `int`: integer, a whole number.
  - Minimum size: 2 byte
  - It has the following type modifiers:
    - signed: A signed integer can hold both negative and positive numbers.
    - unsigned: An unsigned integer can hold only positive values. Ex, `unsigned long int a;`
    - short: Half of the default size. Minimum size: 1 byte
    - long: Twice the default size, Minimum size: 4 byte
- `float`: floating point, a number with a fractional part.
  - Floating point data types are always signed, which means that they have the capability to hold both positive and negative values. `double temp = 4.21;`
  - Minimum size: 4 byte
- `double`: double-precision floating point value.
  - Minimum size: 8 byte
- `long double`:
  - Minimum size: 8 byte
- `char`: A character, such as `'b'`, is a single letter or symbol, and must be enclosed between single quotes.
  - A char variable holds a 1-byte integer. and typically interpreted as an ASCII character.
  - Minimum size: 1 byte
- `string`: A string is composed of numbers, characters, or symbols. String literals are placed in double quotation
  - the `<string>` library is required to use the string data type.
  - The `<string>` library is included in the `<iostream>` library,
  - It is part of the Standard Library.
- `bool`: The Boolean data type returns just two possible values: true (1) and false (0). `bool online = false;`
  - Minimum size: 1 byte
  - If a Boolean value is assigned to an integer, true becomes 1 and false becomes 0.
  - If an integer value is assigned to a Boolean, 0 becomes false and any value that has a non-zero value becomes true.

### Related Functions

- `sizeof(typename)` The sizeof operator determines and returns the actual size of either a type or a variable in bytes.
  - The storage space required by each type varies by operating system,
  - returns number of bytes required by a certain type.
  - Ex, `sizeof(int)`
- Type casting
  - Implicit Type Conversion
    - compiler automatically convert types in the same numerical operation.
  - Explice Type Conversion
    - use `(typeName)variablesName;`
    - `(float) 1 / 2;`

## Variables

- `C++` requires that you specify the type and the identifier for each variable defined.
- An identifier is a name for a variable, function, class, module, or any other user-defined item.
- An identifier starts with a letter (`A-Z` or `a-z`) or an underscore (`_`), followed by additional letters, underscores, and digits (`0` to `9`).
- `C++` keyword (reserved word) cannot be used as variable names.
- Popular naming conventions is using lowercase letters with an underscore to separate words (snake_case).
- Variables must be declared as a data type
  - `int my_var;`
  - `int a, b;` declares multiple variables at once.
- `my_var = 42;` value assignment after declaration.
  - the assigned value should match the declared data type.
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
  - If the size of the array is omitted, an array just big enough to hold the initialization is created. `int b[] = {11, 45, 62, 70, 88};`
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

#### Arithmetic Operators

- `+` addition
- `-` subtraction
- `*` multiplication
- `/` division
  - Integer division - Integers dividing integers will get integers.
  - If one or both of the operands are floating point values, the division operator performs floating point division.
- `%` modulus division
  - Modulus division only works on integers.
- Using parentheses `( )` to indicate which operations are to be performed first.

#### Assignment Operators

- Apply numerical operation with itself by using the following:
  - `+=`
  - `-=`
  - `*=`
  - `/=`
  - `%=`
- Increment and Decrement
  - increment operator `++`
  - decrement operator `--`
- Prefix and Postfix
  - `++i`, the prefix form increments/decrements the variable and then uses it in the assignment statement.
  - `i++`, the postfix form uses the value of the variable first, before incrementing/decrementing it.

#### Relational Operators

- it can be used to form a Boolean expression, which returns true or false:
  - `<` less than
  - `<=` less than or equal to
  - `>` greater than
  - `>=` greater than or equal to
  - `==` equal to
  - `!=` not equal to

#### Logical Operators

- `&&` and
- `||` or
- `!` not
- A compound Boolean expression is evaluated from left to right.
- precedence, `!` > `&&` > `||`
- Use `()` to change precedence
- Ternary operator, `(a < b ? a : b);`

## Conditionals and Loops

- If statements
  ```c++
  if (expression)
    //statements;
  ```
  - statements can be a single statement or a code block enclosed by curly braces `{ }`.
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
- `C++` provides the option of nesting an unlimited number of if/else statements.
- If there is only one statement, the curly braces can be removed.
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
  - Without the break statement, program execution falls through to the next case statement until a break statement is met.
  - The default case must appear at the end of the switch.
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
  - Semicolons are still mandatory.
- Loops can also be nested.

## Function

- Declarations appear above the main() function.
- Function definitions appear after the main() function.
  ```c++
  #include <iostream>
  using namespace std;
  //Function declaration
  void printSomething();
  int main() {
    printSomething();
    return 0;
  }
  //Function definition
  void printSomething() {
    cout << "Hi there!";
  }
  ```
- Declaration and definition can be done together before main.
  ```cpp
  void printSomething(int x)
  {
    cout << x;
  }
  int main() {
  printSomething();
  return 0;
  }
  ```
- A function is not required to return a value, in this case use void.
  - void is a basic data type that defines a valueless state.
- Variables declared outside all functions are global to the entire program.
- Parameters inside a function are local
  - Function destroys its local variables and parameters upon exiting.
- Static variables
  - It is declared in a function.
  - It has a local scope but are not destroyed when a function is exited.
  - When a variable need to be passed out of a function, it should be static.
  - `static int num_calls = 1;`
- specify a default value for each of the last parameters. If the corresponding argument is missing when you call a function, it uses the default value.
  ```cpp
  int sum(int a, int b=42) {
    int result = a + b;
    return (result);
  }
  ```
- Function overloading allows to create multiple functions with the same name, so long as they have different parameters.
  ```cpp
  void printNumber(int a) {
    cout << a;
  }
  void printNumber(float a) {
    cout << a;
  }
  ```
  - You can not overload function declarations that differ only by return type.
- An array can also be passed to a function as an argument.
  ```cpp
  void printArray(int arr[], int size) {
    for(int x=0; x<size; x++) {
      cout <<arr[x];
    }
  }
  ```
- By default, arguments in `C++` are passed by value. When passed by value, a copy of the argument is passed to the function. the original argument is not modified by the function.
- To pass the value by reference, argument pointers are passed to the functions. the original argument is modified by the function.
  ```cpp
  void myFunc(int *x) {
    *x = 100;
  }
  int main() {
    int var = 20;
    myFunc(&var);
    cout << var;
  }
  ```
- Function Template(Generic Function)
  - To define a function template, use the keyword `template`, followed by the template type definition:
  - `C++` provides us with the capability of defining functions using placeholder types, called template type parameters. which is a generic data type.
  ```cpp
  #include <iostream>
  using namespace std;
  template <class T>
  T sum(T a, T b) {
    return a+b;
  }
  int main () {
    int x=7, y=15;
    cout << sum(x, y) << endl;
  }
  ```
  - Optionally, use `template <typename T>`.
  - Function templates also make it possible to work with multiple generic data types.
    ```cpp
    template <class T, class U>
    T smaller(T a, U b) {
      return (a < b ? a : b);
    }
    int main () {
      int x=72;
      double y=15.34;
      cout << smaller(x, y) << endl;
    }
    // Outputs 15
    ```
    - the function template's return type to be of the same type as the first parameter (`T`)

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
  //also
  double *dp;   // pointer to a double
  float *fp;  // pointer to a float
  char *ch;  // pointer to a character
  ```
  - Data type is required for a point to know where the next available address is, based on the amount of data required for the type.
  - The asterisk sign here is not the dereferencing operator, it simply indicate this is a pointer.
  - The asterisk sign can be placed next to the data type, or the variable name, or in the middle.
  - Pointers can be initialized to NULL until they are assigned a valid location.
  - A pointer assigned NULL is called a null pointer. For example: `int *ptr = NULL;`
- Pointer can be used to point another pointer.
  - Prepend `**` to the pointer that point to another pointer
  ```c++
  int x = 12;
  int *p = NULL
  int **ptr = NULL;
  p = &x;
  ptr = &p;
  ```
- Dereferencing, prepend dereference operator `*` to the pointer variable will get the value it points to. It is opposite to `&`. Ex, `x = *p;` will assign the value p is referencing to `x`.
- In a `C++` program, memory is divided into two parts:
  - The stack: All of your local variables take up memory from the stack. Pointers are stored in stack
    - For local variables on the stack, managing memory is carried out automatically.
  - The heap: Unused program memory that can be used when the program runs to dynamically allocate the memory. A pool of memory used for dynamic memory allocation.
    - On the heap, it's necessary to manually handle the dynamically allocated memory,
- `new` operator
  - it returns the address of the space allocated. `new int;`
  - The allocated address can be stored in a pointer, which can then be dereferenced to access the variable.
    ```cpp
    int *p = new int;
    *p = 5;
    ```
- `delete` operator
- use the delete operator to free up the memory when it's no longer needed. `delete pointer;`
  - This statement releases the memory pointed to by pointer.
  - Forgetting to free up memory that has been allocated with the new keyword will result in memory leaks, because that memory will stay allocated until the program shuts down.
- Pointers that are left pointing to non-existent memory locations are called dangling pointers.
  - It can be reused without declaring
- memory allocation for arrays.
  ```cpp
  int *p = NULL; // Pointer initialized with null
  p = new int[20]; // Request memory
  delete [] p; // Delete array pointed to by p
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

## Class

#### Declaration

- A class definition must be followed by a semicolon.
- access specifier
  - multiple members can follow a single access modifier.
  - If no access specifier is defined, all members of a class are set to private by default.
  - Public
    - A public member is accessible from outside the class, and anywhere within the scope of the class object.
  - private
    - A private member cannot be accessed, or even viewed, from outside the class; it can be accessed only from within the class.
  - protected
    - A protected member variable or function can be accessed in the derived classes.
  - Example private with getter and sette
    ```cpp
    class myClass {
      public:
        void setName(string x) {
        name = x;
        }
        string getName() {
        return name;
        }
      private:
        string name;
      };
    ```

#### Instantiation

- A class must be declared before using it,
  ```cpp
  int main()
  {
  BankAccount test;
  test.sayHi();
  }
  ```

#### Constructors

```cpp
class myClass {
public:
  myClass(string nm) {
    setName(nm);
  }
  void setName(string x) {
    name = x;
  }
  string getName() {
    return name;
  }
private:
    string name;
  };
```

- Class constructors are special member functions of a class. They are executed whenever new objects are created within that class.
- The constructor's name is identical to that of the class. It has no return type, not even void.
- It's possible to have multiple constructors that take different numbers of parameters.

#### Destructors

```cpp
class MyClass {
public:
  ~MyClass() {
    // some code
  }
};
```

- Destructors are special functions, as well. They're called when an object is destroyed or deleted.
- Objects are destroyed when they go out of scope, or whenever the delete expression is applied to a pointer directed at an object of a class.
- The name of a destructor will be exactly the same as the class, only prefixed with a tilde (~).
- A destructor can't return a value or take any parameters.
- Destructors can be very useful for releasing resources before coming out of the program. This can include closing files, releasing memory, and so on.

#### Header Files and Source Files

- A class has two files
  - MyClass.h is the header file.
  - MyClass.cpp is the source file.
  - The header file (`.h`) holds the function declarations (prototypes) and variable declarations.
  - Example Header file
    ```cpp
    #ifndef MYCLASS_H
    #define MYCLASS_H
    class MyClass
    {
      public:
        MyClass();
        void myPrint();
      protected:
      private:
    };
    #endif // MYCLASS_H
    ```
  - Example source file
    ```cpp
    #include "MyClass.h"
    MyClass::MyClass()
    {
      //
    }
    void MyClass::myPrint()
    {
      cout <<"Hello"<<endl;
    }
    ```
- Preprocessors
  - `#ifndefine`
    - This prevents a header file from being included more than once within one file.
  - `#include "MyClass.h"`
    - double quotes are used to include customized header file
    - Some developers use `.hpp` extension for header files
- `MyClass::MyClass()` means MyClass class has a contractor function, then write the constructor definition in the corresponding code blocks

#### Class Object

- The arrow member selection operator (->) is used to access an object's members with a pointer.
  ```cpp
  MyClass obj;
  MyClass *ptr = &obj;
  ptr->myPrint();
  ```
- Constant Objects, `const MyClass obj;`
  - Must have constructors for initialization
- Constant Functions
  - Const obj can only call by const functions
  - Declaration
    ```cpp
    class MyClass
    {
    public:
      void myPrint() const;
    };
    ```
  - Definition
    ```cpp
    #include "MyClass.h"
    #include <iostream>
    using namespace std;
    void MyClass::myPrint() const {
    cout <<"Hello"<<endl;
    }
    ```
- `this` pointer
  - Every object in C++ has access to its own address through an important pointer called the this pointer.
  - Inside a member function this refer to the invoking object.
    ```cpp
    class MyClass {
      public:
      MyClass(int a) : var(a){ }
      void printInfo() {
        cout << var<<endl;
        cout << this->var<<endl;
        cout << (\*this).var<<endl;
      }
    private:
      int var;
    };
    ```
    - All three alternatives will produce the same result.

#### Member Initialization List

- It must be used for constant.

```cpp
#include <iostream>
using namespace std;
class MyClass {
  public:
    MyClass(int a, int b);
  private:
    int regVar;
    const int constVar;
};
MyClass::MyClass(int a, int b)
: regVar(a), constVar(b)
{
  cout << regVar << endl;
  cout << constVar << endl;
}
int main() {
MyClass obj(42, 33);
}
```

#### Friends

- Declaring a non-member function as a friend of a class allows it to access the class's private members

```cpp
#include <iostream>
using namespace std;
class MyClass {
  public:
    MyClass() {
      regVar = 0;
    }
  private:
    int regVar;
    friend void someFunc(MyClass &obj);
};

void someFunc(MyClass &obj) {
  obj.regVar = 42;
  cout << obj.regVar;
}

int main() {
  MyClass obj;
  someFunc(obj);
}
```

- Similar to friend functions, you can define a friend class, which has access to the private members of another class.
- Friend functions do not have a `this` pointer, because friends are not members of a class.

#### Operator Overloading

- Most of the `C++` built-in operators can be redefined or overloaded
- Operators that can't be overloaded include `:: | .\* | . | ?:`
- it's not possible to alter the operators' precedence, grouping, or number of operands.
- Overloaded operators are functions, defined by the keyword operator followed by the symbol for the operator being defined.
- An overloaded operator is similar to other functions in that it has a return type and a parameter list.
  ```cpp
  #include <iostream>
  using namespace std;
  class MyClass {
  public:
    int var;
    MyClass() { }
    MyClass(int a): var(a) { }
    MyClass operator+(MyClass &obj) {
      MyClass res;
      res.var= this->var+obj.var;
      return res;
    }
  };
  int main() {
    MyClass obj1(12), obj2(55);
    MyClass res = obj1+obj2;
    cout << res.var;
  }
  ```

#### Composition

- Classes can have classes

```cpp
#include <iostream>
using namespace std;

class Birthday {
 public:
  Birthday(int m, int d, int y)
  : month(m), day(d), year(y)
  {  }
  void printDate()
  {
   cout<<month<<"/"<<day <<"/"<<year<<endl;
  }
 private:
  int month;
  int day;
  int year;
};

class Person {
 public:
  Person(string n, Birthday b)
  : name(n), bd(b)
  {  }
  void printInfo()
  {
   cout << name << endl;
   bd.printDate();
  }
 private:
  string name;
  Birthday bd;
};

int main() {
 Birthday bd(2, 21, 1985);
 Person p("David", bd);
 p.printInfo();
}
```

#### Inheritance

- The class whose properties are inherited by another class is called the Base class. - The class which inherits the properties is called the Derived class.
- The Base class is specified using a colon and an access specifier:
  - `public` public members of the base class become public members of the derived class `class Daughter: protected Mother`
  - `protected` public and protected members of the base class become protected members of the derived class.`class Daughter: protected Mother`
  - `private` public and protected members of the base class become private members of the derived class. `class Daughter: private Mother`
  - If no access specifier is used when inheriting classes, the type becomes private by default.
- Derived class inherits all base class methods with the following exceptions:
  - Constructors, destructor - they are being called when an object of the derived class is created or deleted.
    - The base class' constructor is called first, and the derived class' constructor is called next.
    - When the object is destroyed, the derived class's destructor is called, and then the base class' destructor is called.
  - Overloaded operators
  - The friend functions
  ```cpp
  #include <iostream>
  using namespace std;
  class Mother
  {
  public:
    Mother() {};
    void sayHi() {
      cout << "Hi";
    }
  };
  class Daughter: public Mother
  {
  public:
    Daughter() {};
  };
  int main() {
    Daughter d;
    d.sayHi();
  //Outputs "Hi"
  }
  ```
- A class can be derived from multiple classes by specifying the base classes in a comma-separated list. For example: `class Daughter: public Mother, public Father`
- C++ polymorphism means that a call to a member function will cause a different implementation to be executed depending on the type of object that invokes the function.
  ```cpp
  #include <iostream>
  using namespace std;
  class Enemy {
    protected:
      int attackPower;
  public:
    void setAttackPower(int a){
      attackPower = a;
    }
  };
  class Ninja: public Enemy {
  public:
    void attack() {
      cout << "Ninja! - "<<attackPower<<endl;
    }
  };
  class Monster: public Enemy {
  public:
    void attack() {
      cout << "Monster! - "<<attackPower<<endl;
    }
  };
  int main() {
    Ninja n;
    Monster m;
    Enemy *e1 = &n;
    Enemy *e2 = &m;
    e1->setAttackPower(20);
    e2->setAttackPower(80);
    n.attack();
    m.attack();
  }
  ```
  - created two pointers of type Enemy, pointing them to the Ninja and Monster objects.

#### Virtual Function

- A virtual function is a base class function that is declared using the keyword virtual. It can be either defined or empty. It can be overridden by it’s derived class.
  ```cpp
  class Enemy {
    public:
      virtual void attack() {
    }
  };
  class Ninja: public Enemy {
    public:
      void attack() {
        cout << "Ninja!"<<endl;
      }
  };
  class Monster: public Enemy {
    public:
      void attack() {
        cout << "Monster!"<<endl;
      }
  };
  ```
- A class that declares or inherits a virtual function is called a polymorphic class.
- pure virtual functions
  - The virtual member functions without definition are known as pure virtual functions.
  - The syntax is to replace their definition by =0 (an equal sign and a zero):
    ```cpp
    class Enemy {
    public:
    virtual void attack() = 0;
    };
    ```
  - The `= 0` tells the compiler that the function has no body.
  - Every derived class inheriting from a class with a pure virtual function must override that function.
  - Objects cannot be created from the base class with a pure virtual function.
  - These classes are called abstract.
  - It can be used to create pointers
    ```cpp
    Ninja n;
    Monster m;
    Enemy *e1 = &n;
    Enemy *e2 = &m;
    e1->attack();
    e2->attack();
    ```

#### Class Template

- Generic Class
  ```cpp
  template <class T>
  class Pair {
    private:
      T first, second;
    public:
      Pair (T a, T b):
      first(a), second(b) {
      }
  };
  ```
- When define member functions outside of the class
  ```cpp
  template <class T>
  class Pair {
    private:
      T first, second;
    public:
      Pair (T a, T b):
      first(a), second(b){
      }
      T bigger();
  };
  template <class T>
  T Pair<T>::bigger() {
    // some code
  }
  ```
- To create objects of the template class for different types, specify the data type in angle brackets,
  ```cpp
  Pair <int> obj(11, 22);
  cout << obj.bigger();
  // Outputs 22
  ```
- template specialization - It enables a different behavior for a certain data type
  ```cpp
  template <class T>
  class MyClass {
    public:
      MyClass (T x) {
      cout <<x<<" - not a char"<<endl;
    }
  };
  template < >
  class MyClass<char> {
    public:
      MyClass (char x) {
        cout <<x<<" is a char!"<<endl;
      }
  };
  ```
- Use `template<>`, if all types are known and no template arguments are required for this specialization

## Exceptions Handling

- throw is used to throw an exception when a problem shows up.
- A try block identifies a block of code that will activate specific exceptions. It's followed by one or more catch blocks.
  - specify what type of exception you want to catch in parentheses following the keyword catch.
  - Multiple catch statements may be listed to handle various exceptions in case multiple exceptions are thrown by the try block.
  ```cpp
  try {
    int motherAge = 29;
    int sonAge = 36;
    if (sonAge > motherAge) {
      throw 99;
    }
  }
  catch (int x) {
    cout<<"Wrong age values - Error "<<x;
  }
  //Outputs "Wrong age values - Error 99"
  ```
  - The error code 99, which is an integer, appears in the throw statement, so it results in an exception of type int.
- Catch All - It's possible to specify that your catch block handles any type of exception thrown in a try block. To accomplish this, add an ellipsis (...) between the parentheses of catch

## Standard Library

- import function with `#include <package_name.h>`
- `using namespace std`

### `cstdlib`

- `#include <cstdlib>`

##### Ramdon number

- `rand()` return an integer
  - Use the modulo (%) operator to generate random numbers within a specific range. `1 + (rand() % 6)` will generate an integer from 1 to 6.
- `srand()` assign a seend for `rand()`. Ex: `srand(98);`
  - the same seed will result in the same output from `rand()`.
  - A solution to generate truly random numbers, is to use the current time as a seed value for the `srand()` function. `srand(time(0));`

### `ctime`

- `#include <ctime>`
- `time()` function to get the number of seconds on your system time
  - `time(0)` will return the current second count,

### `iostream`

- It defines the standard stream objects that input and output data.
- `#include <iostream>`

##### Output

- `cout`
  - Output content should follow the insertion operator `<<`. For example, `cout << "Hi!";`
  - You can add multiple insertion operators after cout. Output will be in one line. `cout << "This " << "is " << "awesome!";`
  - NewLine
  - One way to print two lines is to use the endl manipulator, `cout << "Hello world!" << endl;`
  - The new line character `\n` can be used as an alternative to `endl`.
  - Two newline characters (`\n\n`) placed together result in a blank line.

##### Input

- `cin`
  - Input content is indicated by the extraction operator (`>>`). For example, `int num; cin >> num;`.
  - extractions on cin can be chained to request more than one input in a single statement: `cin >> a >> b;`

### `fstream`

- `#include <fstream>`
- Three new data types are defined in fstream:
  - `ofstream`: Output file stream that creates and writes information to files.
  - `ifstream`: Input file stream that reads information from files.
  - `fstream`: General file stream, with both ofstream and ifstream capabilities that allow it to create, read, and write information to files.

##### Open and Write a File

```cpp
#include <iostream>
#include <fstream>
using namespace std;
int main() {
  ofstream MyFile;
  MyFile.open("path/to/test.txt");
  MyFile << "Some text. \n";
}
```

- If the specified file does not exist, the open function will create it automatically.
- file path can also be specified using the `ofstream` objects constructor, instead of calling the open function.
  ```cpp
  #include <fstream>
  using namespace std;
  int main() {
    ofstream MyFile("test.txt");
    MyFile << "This is awesome! \n";
    MyFile.close();
  }
  ```
- The `is_open()` member function checks whether the file is open and ready to be accessed. `MyFile.is_open()` returns a Boolean.
- An optional second parameter of the open function defines the mode in which the file is opened. This list shows the supported modes.
  - `ios::app` append to end of file
  - `ios::ate` go to end of file on opening
  - `ios::binary` file open in binary mode
  - `ios::in` open file for reading only
  - `ios::out` open file for writing only
  - `ios::trunc` delete the contents of the file if it exists
  - All these flags can be combined using the bitwise operator OR (`|`).
    ```cpp
    ofstream outfile;
    outfile.open("file.dat", ios::out | ios::trunc );
    ```

##### Read a File

- The getline function reads characters from an input stream and places them into a string.
  ```cpp
  #include <iostream>
  #include <fstream>
  using namespace std;
  int main () {
    string line;
    ifstream MyFile("test.txt");
    while ( getline (MyFile, line) ) {
      cout << line << '\n';
    }
    MyFile.close();
  }
  ```

##### Closing a File

- `MyFile.close();`
