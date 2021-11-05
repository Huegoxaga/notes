# Python

## Introduction

- Python is a high-level, interpreted programming language.
- Interpreted language has an interpreter processing the scripts at runtimes line by line from top to bottom, the compiling process is done by the interpreter during code execution
  - `Cpython` is the official interpreter. It is written in `C` and `Python`
  - Interpreted language doesn’t have machine code file which is created by the compiler.
- Python 3 is the current version.
- IDLE is the integrated development environment for Python. It is available for all platform. Python code can be executed in IDLE line by line using Python Shell(immediate mode) or written and run in source code files and execute by running `python <filename>` in the terminal
- Source files have an extension of `.py`.
- It is a case sensitive language.

## Basic Syntax

Python Syntax is generally consisted of comments, statements, methods, functions and modules.

### Comments

- Single line comment is followed by `#`, everything after # in one line will be ignored.

```python
# Single line comment goes here.
```

- Three sets of double quotation marks is called doctrings. Doctrings contains multi-lines comments and explains the following code after the first line. It is retained through runtime.

```python
"""
Summary or Description of the Function
Parameters:
argument1 (int): Description of arg1
Returns:
int:Returning value
"""
```

### Statements

- It is recognized by one keyword in the entire line, or sometimes followed by a variables after a singe space.

```python
del x
break
```

### Methods

- It is used to access and manipulate objects.
- It is recognized by a dot and a method name immediately after a variable name.

```py
x.count(y)
x.upper()
```

### Functions

- There are many built-in functions or it can be defined in codes.
- It is recognized by brackets after function names.

> #### Basic Useful Functions

```py
print(x)              #It prints variable x with a new line, x can be any data type.
print(x, y)           #It prints any two data types with a space in between.
input("Prompt: ")     #It prompts, get and returns user input as a string. The string that input() returns is automatically escaped.
```

### Modules

- Modules provide additional methods or functions for the programming. They are imported using keyword `import` at the very beginning.

## Variables

They are customized name for storing data.

### Naming Conventions

- Variable name is usually oneTwoThree or one_two_three
- Variable name can use only letter number and underscore
- Variable name can not begin with number
- Variable name can not use reserved words in python
- Variable name abbreviation often needs comments as explanation.

### Variable Scope

- Variables introduced inside functions are local(only available) to that function.

## Operators

Operators are special symbols that placed in between objects.

### Operators and Precedence

When operator are chained together, The operation order is determined from top to bottom in the following order.

- String Operators:
  - Slicing `x[n]`
  - concatenation `+`
- Arithmetic Operators:
  - exponent `**`
  - Bitwise not `~`
  - negation `-`
  - multiply `*`
  - divide `/`
  - integer division `//`
  - remainder `%`
  - string repetition `*`
  - addition `+`
  - subtraction `-`
  - Bitwise and `&`
  - Bitwise xor `^`
  - Bitwise or `|`
- Relational Operators
  - greater `>`
  - greater or equal `>=`
  - great `<`
  - smaller or equal `<=`
  - equal `==`
  - not equal `!=`
  - string membership `in`
  - refer to the same object `is`
- Binary Boolean Operators
  - `not`
  - `and`
  - `or`
- Assignment
  - It is used to assign value to a variable name. `=`
  - Multiple assignment: `x = y = 10`
- Two or more physical lines may be joined into logical lines using backslash characters (`\`)

### Bitwise Operators

It is performed bit by bit.

- and `&`
- or `|`
- not `~`
- XOR, it is an "or" operations that doesn’t include "and", `^`

```py
a=1101101
~a=0010010
```

> ##### Hint:

- `del x`, this statement remove one reference count from the name to the value in memory.
- `a+=b` is treated as `a=a+b`
- `a**b**c` is same as `a**(b**c)`. This is called right associative.

## Basic Data Types

### Boolean

- A Boolean value is either `True` or `False`
- In Python `3.x`, `True` and `False` are keywords and will always be equal to `1` and `0` respectively
- In arithmetic operation `True` is `1`, `False` is `0`

### Integer

- Whole number

### Float

- It can be any number with a decimal point. It is produced after any division or implicitly transfer after an operation between float and integer.
- Computer has limited memory space for floats. Also, any zero at the end will be ignored.

> #### Useful Math Functions

```py
round(value, toHowManyDigitAfterDecimal) #Rounding to specific decimal place
abs(value) #Get the absolute value of a number.
```

### Character

- It can be any single character.

> #### Character Conversion

```py
ord(character)  #Transforming a character to its ASCII code number. Character can be Unicode like u’\u1234’
chr(number)   # transform ASCII (a number from 0 to 255) to character.
unichr(number)   # transform UCS2 (a number from 0 to 65535) to character.
```

### String

- String is like list type for character, but can not change(immutable).
- \ is used to escape special characters, the characters are then called escape characters. E.g. `"abc\"def\\g"`, Output: `abc"def\g`
- `\n` represents a newline.
- `\t` represents a new tab.

#### String Operators

- Concatenation uses `+`.
- Integer repetition uses `*`.

#### Membership Operator

It returns membership relationship between two objects as boolean.

```py
a in b
a not in b
not a in b
```

#### Relational Operators

It can be used on strings for lexicographical(alphabetical order) comparison.

#### String Methods

```py
stringX[n]  #Get the character of stringX at nth index.

stringX[m:n]  #Get the character of stringX at index from m to n-1, max or min if m or n is missing.
"""
There could be a third parameter that represents the step.
-1 means backward from its left or right end.
"""
str.upper()
str.lower()
str.isalpha()         # Return boolean
str.isdecimal()
str.isnumeric() # check if contains only 0-9
str.islower()
str.isspace()
str.isupper()
str.find(substring) # Find the lowest index of the substring.
str.strip(string)   # Strip all the characters in the argument of the str from the beginning and the end. (if no argument, remove empty spaces by default)
",".join(["a","b","c"])
#Output:’a,b,c’
"Hello ME".replace("ME","world")
#Output:’Hello world’
"This is a sentence".startswith("This")
#Output:True
"Hello World!".endswith("world!")
#Output:False
"x,y,z".split(",")
#Output:[‘x’,’y’,’z’]
"test.jpg".endswith('.jpg', '.jpeg')
#Return True if a string ends with a string in the argument
```

#### String Function

```py
len(string)    #Return the number of characters of this string.
```

#### String Formatting

`"formatedStringUsing{}".format(x,y,z)`

- String is formatted in a set of double quotation marks.
- The location, order, and content of data is indicated by `{}`.
- The argument of `.format` is the value of data in the `{}`.
- Use double curly bracket to escape `{}`

```py
"{x},{y}".format(x=5,y=12)
#Output:5,12
"{} {}".format(100,50)
#Output:100 50
"{1}abc{0}".format(100,50)
#Output:50abc100
"{:04d}".format(1)
#Output:0001
"{:06.2f}".format(1.2)
#Output:001.20     #decimal point counts
"{:_<10}".format("left")
#Output:left______
"{:>10}".format("right")
#Output:     right
```

- Optionally, use `f"Formatted: {variable:.2f}"`
  - Use `()` for expression containing variables.

### Type Casting

Explicitly convert types.

```py
str(x)    #To  string
int(x)    #To  integer
float(x) #To   float
list(x)   #To   list
eval(x) # parse and evaluation a string to other types
eval('[1]') #string to list
eval('1') #string to int
bool(x) #  when convert string to boolean any thing other than empty string will return True
```

### Type Validation

- `isinstance(x, list)` returns `True` is `x` is a list
- `type(x)` returns the type object of `x`

## Basic Structures

### If Condition

The execution of a certain code block is determined by conditions. Conditions are a boolean expression. When the condition is true the codes after will be executed.

```py
if condition:
	#…
elif condition:
	#…
else:
	#…
```

- Ternary: `x = a if condition else b`, `return x if condition else y`
- Chained Ternary: `x = 1 if condition1 else 2 if condition2 else 3`

### All and Any

It can be used to test the condition among multiple values in an object.

```py
x = [1,2,3,4,5]
if all([i<6 for i in x]):
	print("all smaller than 6")
if any([i==5 for i in x]):
	print("At least one 5 in the array")
```

### While Condition

This block of code is executed when the condition is true.

```py
while condition:
	#….
```

### For Loop

- Every elements of an object is assigned to the variable x.
  ```py
  for x in objects:
    print(x)
  for x in enumerate([1,3,5,7]):
    print(x)
  """
  Output:
  (0,1)
  (1,3)
  (2,5)
  (3,7)
  """
  # Enumerate(x) casts other types into enumerate.
  for x in range(6): #from 0 - 5
  print(x)
  ```
- Shorthand For loop, `[i.x for i in list]` return a list of `i.x`.

> **Notes:**

- Flag is a condition for the loops which can be tested and modified in the loop.
- Sentinel value is a value in the loop condition, it is used to determine the exit of a loop.
- break statement in the loop can stop looping immediately.
  - For nested loop, the inner break only break the inner loop
- continue statement restart the loop from the top.

## List

- It is a mutable object. Its content can be changed. This index starts at 0.
  ```py
  list=['a','b','c','d']
  print(list[0])
  #Output:’a’
  ```
- 2-D List
  ```py
  list=[[1,2],[3,4],[5,6]]
  print(list[1][0])
  #Output:3
  ```

#### List Methods

```py
mylist.append(value) # This will append a value at its end. The method doesn't return any value
mylist.sort() # Sorts the list ascending by default
mylist.sort(reverse=True) # Sorts the list in desending order
# When sort a list of tuples, sort by the first element of the tuples
mylist.sort(key=lambda listItem: listItem.get('group_name')) #sort based on the key value of the element
mylist.remove(value) # It will remove certain value in the list regardless of its location (using ==).
mylist.reverse() # It will reverse the order, print(list.sort()) will not work
mylist.insert(index, element) # It will insert an element at certain index location. (raise ValueError exception if element is not found)
mylist.count(object) # It returns how many times an item occurs in the list
mylist.index(object) # It returns the first index of the item, ValueError if not find.
mylist.pop(index) # It returns the element according the index and remove the element from the existing list.
mylist.copy() # It return a new copy of the list, instead of a reference
mylist.extend(b) # Adds all elements from list b to the end of mylist
mylist.insert(i, e) # Inserts e into mylist at index i
```

#### List Operators

- Unpacking assignment:
  - `x, y = [1, 2]` as a result `x = 1`, `y = 2`
  - `first, *rest = [1, 2, 3, 4]` as a result `first = 1, rest = [2, 3, 4]`
- join `+`, `listC =listA + listB` append `listB` to `listA`.
- repeat `*`
- existence(return Boolean) `in`
- slicing - It modifies the original list.
  - `a[n:m]`, slice list `a` from index `n` to `m-1`.
  - `a[n:m:k]`, slice list `a` from index `n` to `m-1` with step `k`.
  - `a[::-1]`, reverse list `a` by getting elements from left to right.
  - If the starting index is missing, it is first one by default.
  - If the ending index is miss, it will take all elements to the end.
  - A negative index counts from the end of the list. Ex: `a[-5:]` it take the last 5 elements of list a.

#### List Function

```py
len(list)
min(list)
max(list)
sum(list)
```

#### List Comprehension

- It is the shortcut for creating lists.
  ```py
  squareList = [i**2 for i in range(5)]
  evenSquareList = [i**2 for i in range(10) if i**2%2 ==0]
  dictListValues = [d['key'] for d in dictList]
  ```

## Dictionary

- It is mutable.
  ```py
  x = {key1:value1, key2:value2, key3:value3, …}
  print(x[key1])
  x[key1] = newValue
  ```
- To add a new key/value pair to a dictionay, simply assign the value to a new key.

### Related Operations

- Membership Operator - in

  ```py
  keyName in dictionaryName # return a bool
  keyName not in dictionaryName
  ```

- `del` keyword, `del d[key]` Removes the selected key from dictionary `d`

### Methods

```py
# The list functions len, sum, min, max, and sortedcan be passed dictarguments. They perform their operations on the keys, not the values.
dictionary.get(key, default_value)  #It returns the key’s value and None if key is not found. or display specific default value. None type can have this method without error
dictionay.pop(key,default)  # It returns and remove the value that match the key. Return the default value if not found.
dictionay.values() # Return a list of values, it returns an object of type dict_values which can be cast into a list
dictionay.keys() # Return a list of keys.
dictionay.items() # Return a list of dictionay elements.
dictionay.clear() # empties the dictionary
dictionay.copy() # Return a copy of the dictionary instead of passing a reference
```

### Iteration

- Generate a dictionary from a list of tuples `damage_rate = {xVar: yVar for (xVar, yVar) in tupleList}`.
- Generate a dictionary from a list of objects `city_dict = {x.id: x.name for x in objectList}}`.
- To loop every key and value from a dictionary:
  ```py
  for k, v in dict.items():
        print(k,v)
  ```

### Subclass

#### OrderedDict

- A special dictonary that remembers the order entries were added

```py
from collections import OrderedDict

od = OrderedDict()
od['a'] = 1
od['b'] = 2
od['c'] = 3
od['d'] = 4

for key, value in od.items():
    print(key, value)
```

## Tuples

- It is an immutable list with or without parentheses(use comma for separation).
- It is faster than list, because it can not be changed or there will be a typeError.
- Tuple unpacking:
  - `x,y = 1,2` is equivalent as `x = 1` and `y = 2`
  - it is also equivalent as `x,y = (1,2)` or `(x,y) = 1,2` or `(x,y) = (1,2)`

```py
#Creates an empty tuples.
x = ()
#tuples declaration 1
x = (8,'a',"sdfs",(2,4))
#tuples declaration 2
x = 8,'a',"sdfs",(2,4)
#access tuples
print(x[0])
#Output: 8
```

### Methods

```py
a = ('1', '2', '3')
b = ('a', 'b', 'c')
x = zip(a, b)
# return nested tuple that each element is a tuple with nth element of a and nth element of b
# e.g. (('1', 'a'), ('2', 'b'), ('3', 'c'))
```

## Set

- It is a mutable, unordered list, it uses hash table and does not accept duplicated elements
- A set is like a dict with keys but no values
- It is surrounded by curly bracket `{}`.
- Empty set is `set()`. `{}` is reserved for dictionary.

### Operators

- union `|`
- intersection `&`
- difference `-`
- symmetric difference: items in either set, but not both. `^`

### Methods

```py
set.add(x)  #It adds new element
set.remove(x)  #It removes x from set
set.pop()  #It removes a random element from the list
```

### Functions

```py
len(set) # get length
```

## Bytes

- It stores a serials of byte, each byte contains 8 bits of information
  - when print bytes object, it will be display as `b'\x00\x00`
  - each byte is valid from `\x00` to `\xFF`
- Bytes objects are immutable, it cannot be changed after creation

### Bytes Methods

- `empty_bytes = bytes(2)` create a bytes object that has 8 empty bytes
- `new_bytes = bytes(b'\xAA\xBB')` create a bytes object from bytes value

## Bytes Array

- It is similar to Bytes object but it is mutable
- Using index to access and modify byte data inside
  - `new_bytes_array = bytearray(b'\x00\xFF')`, then `new_bytes_array[1] = 0`, `new_bytes_array` will then contain bytes data `b'\x00\x00'`
- All methods used by list, also works for bytearray, e.g. `new_bytes_array.append(255)`, will update the `new_bytes_array` with bytes value `b'\x00\x00\xFF'`

## Other Basic Objects

### Range Object

- A sequential list of numbers.
- Created by range function.

```py
range(5) # It represents number from 0 to 4.
list(range(5))=[0,1,2,3,4]
range(2,5) # It represents number from 2 to 4.
range(5,20,x) # It creates a range from 5 to 19 with certain interval x.
reversed(range(5)) # It represents number from 4 to 0.
```

### None object

- It is a False when converted to boolean type.
- It is the default output for user defined function.
- It is used to represent the absence of a value.

### Map Object

```py
map(function,oldlist)
```

- It returns a map object that manipulate the old list(or other iterables) according to the function.
- The map object needs to be transferred into a list(or other iterables).

### Filter Object

```py
filter(function,iterables)
```

- It returns a filter object that has elements removed according to the function as the first argument.

## Modules

- Modules can be installed using package manager
- Modules can be the folder name in the working directory
- It is recognized by the keyword `import`. For example, a module called `module` can imported in the following ways
  - Two modules cannot import each other, there will be a circular import, except will be raised

```py
import module
import module as md
from module import *
from module import function as func
from module import function
from module import functionA, functionB
from module import (functionA, functionB)
from folder import file
from folder.file import function
from folder.file import classA, classB
from .folder import file # . represent the current folder of the running python script
from ..folder import file # .. represent the parent folder of the running python script
```

### Show Module Info

- `print(package.__version__)` show module version
- `print(package.__file__)` show module path

### `__name__` variable

- Each python file has a `__name__` within its scope
- When a python script is interpreted, by default `__name__` is set to `__main__`.
- when a python script is imported as a module, when interpreting script that import the module, the `__name__` variable inside the module will be set to the module name.
- Use the following code, if `myFunction()` is not intended to run, when the script will be imported as a module.
  ```py
  def main():
    myFunction()
  if __name__ == '__main__':
    main()
  ```

### Sources of Modules

1. Some of them are preinstalled in the standard Library
2. Third-party Python modules. Installed using libraries management tools like `pip` or `conda`
   - A collection of third-party modules can be pre-installed and managed by a certain Python distribution
3. Your own module. Most modules are available on all platforms, but some of them are Windows or Unix specific. Some are using exe file.

## Distributions

### Anaconda

- Most popular packages are included in one Python distribution called .
- It manages libraries, dependencies, and environments with Conda, instead of Python Package Index (PyPI).

#### Installation

- [Click](https://www.anaconda.com/distribution/) to download Anaconda.
- Follow the instructions to install. For Linux OS, [Click Here](https://docs.anaconda.com/anaconda/install/linux/).
- Once complete, the following libraries, dependencies, and environments are ready to use.

## Lambda

- It is used to create anonymous function with has no variable name.
- It can be assigned to a variable to become a normal function.

```py
print(lambda  x: 2*x*x(10))  # Output: 200
```

## User Defined Functions

```py
def functionName(variable):
  # function code here
functionName(variable)
```

- parameters are variables that a function accepts.
- arguments are specific values that are substituted into the parameters.
- the scope of a variable is the sections of codes where the variable is accessible.
- variables within a function, has an independent scope within the function.
- functions can be assigned to a variable names.
- The variable can be called.
- function can be argument of other function.
- Functions can have variables name starts with `*`, it enable the function to take a list of itratable variable with any length, generally it is called `*args`.
  - `func(x=3, y=4)` or `func(3, 4)` is the same as `func(*[3, 4])`
- Functions can have variables name starts with `**`, it enable the function to take a dictionary of itratable keys and values with any length as its parameters, generally it is called `**kwargs`.
  - `func(x=3, y=4)` or `func(3, 4)` is the same as `func(**{'x': 3, 'y': 4})`
  - Always put the `**` argument as the last parameter, `func(x=3, **kwargs)`, key `x` will be added to the `kwargs` dictionary

#### return statement

Once a value is returned from a function, it immediately stops being executed.

#### yield statement

The yield statement suspends function’s execution and sends a value back to the caller, but retains enough state to enable function to resume where it is left off. When resumed, the function continues execution immediately after the last yield run. This allows its code to produce a series of values over time, rather than computing them at once and sending them back like a list.

#### pass statement

The pass statement is used as a placeholder for future code. When the pass statement is executed, nothing happens, but you avoid getting an error when empty code is not allowed. Empty code is not allowed in loops, function definitions, class definitions, or in if statements.

```py
def simpleGeneratorFun():
    yield 1
    yield 2
    yield 3

for value in simpleGeneratorFun():
    print(value)

# output will be 1 then 2 then 3.
```

#### global variable

- In order to access and modify variables defined outside the function definition, Prepend the keyword `global`. For example, `global X = 100`.
- `global` is not mandatory when the name from the outside is unique

#### Types Hints

One can specify expected input and return types and raise errors when type does not match, The Python runtime does not enforce function and variable type annotations

```py
def example(l: list, index: int = 0) -> int:
    if not isinstance(l, list):
        raise TypeError
    return l[index]
```

## Generator

```py
def count():
	i=5
	while i>0:
		yield i
		i-=1
for i in count():
	print(i)  # output 5 4 3 2 1
```

- It is a type of iterable, it doesn’t contain indices.
- It is a user defined function with loop that contain yield statement to iterate multiple output by using for loop.
- It can be infinite.

### Convert to List

```py
def number(x):
	for i in range(x):
		if i%2 ==0:
			yield i
print(list(number(11)))
```

finite generator can be transfer to list using `list()`.

## Decorators

It is a user defined function that take old function as argument, declare a new function. manipulate old function by putting it inside and then return the new defined function.

```py
def decor(func):
	def wrap():
		print("===================")
		func()
		print("==================")
	return wrap
#Then, newly defined function could be decorated by adding @decorfunction before def statement.
@decor
def rawfunction():
	print("Hello world!")
```

## Recursion

- Functions that repeatedly calls themselves is called recursion.
- The last step is called the base case, it’s an exit point of recursion.
- Multiple functions can get involved in on recursion.

```py
def factorial(x):
	if x == 1:
		return 1
	else:
		return x * factorial(x-1)
```

## Class

- the name should be Capital letters for each word like OneTwoThree.
- It is the blueprint for creating objects.
- An instance is an object which is being called.

### Object methods

- They are functions defined within the class block.
- It must have `self` as its first parameter. When calling functions, `self` parameter can be ignored.

### `__init__` method

- It is called to create object, using class name as a function
- It is used to set the initial environment of an object.
- It is also called the class constructor.
- `__new__` method is executed before `__init__` for special cases.

### Instance’s attributes

They are placed in the `__init__` method

### Class attributes

They are placed in the first line of the class block without using `self`, they are the `static` variables and shared by all instance of the class.

```py
class Dog:
	legs = 4
	def __init__(self,name,color):
		self.name = name
		self.color = color
	def bark(self):
		print("Woof!")
fido = Dog("Fido","brown")
fido.bark() # Woof!
fido.name # 4, instance variable
Dog.legs # 4, class variable
```

- `hasattr(object, attributeName)` check if one object has certain attribute.
  - The `hasattr()` is called by `getattr()` to check to see if `AttributeError` is to be raised or not.

## Superclass

- It is used to share common attributes among classes called subclasses.
- A class can inherit a class from the superclass by putting superclass name at the end of the class statement for the subclass.
- Attributes for subclass can override attributes for superclass if they have the same name.
- Superclass can have superclass, subclass can have subclass.
- super function `super()` refers to the parent class

```py
class Animal:
  def __init__(self, name, color):
    self.name = name
    self.color = color

class Cat(Animal):
  def purr(self):
    print("Purr...")

class Dog(Animal):
  def bark(self):
    print("Woof!")

fido = Dog("Fido", "brown")
print(fido.color)
fido.bark()
```

## Magic methods

- Magic methods has double underscores at two ends called dunders.
- It is a special method for operator overloading(defines `+`,`*`,`\`, and`-`between objects) or others.
- It takes parameters `self` and `other`

#### Operators

- `__sub__` for `-`
- `__mul__` for `*`
- `__truediv__` for `/`
- `__floordiv__` for `//`
- `__mod__` for `%`
- `__pow__` for `**`
- `__and__` for `&`
- `__xor__` for `^`
- `__or__` for `|`

```py
class Vector2D:
  def __init__(self, x, y):
    self.x = x
    self.y = y
  def __add__(self, other):
    return Vector2D(self.x + other.x, self.y + other.y)

first = Vector2D(5, 7)
second = Vector2D(3, 9)
result = first + second
print(result.x)
print(result.y)
```

- It simply translate x+y into `x.__add__(y)`
- If x hasn't implemented `__add__`, and x and y are of different types, `x.__radd__(y)` is called.

#### Comparison

- `__lt__` for `<`
- `__le__` for `<=`
- `__eq__` for `==`
- `__ne__` for `!=`
- `__gt__` for `>`
- `__ge__` for `>=`
- `__ne__` could be translate to `__eq__` if it has not been implemented.

```py
class SpecialString:
  def __init__(self, cont):
    self.cont = cont

  def __gt__(self, other):
    for index in range(len(other.cont)+1):
      result = other.cont[:index] + ">" + self.cont
      result += ">" + other.cont[index:]
      print(result)

spam = SpecialString("spam")
eggs = SpecialString("eggs")
spam > eggs
```

#### Container

- `__len__` for overriding `len()`
- `__repr__` for overriding `print()` with format
- `__getitem__` for indexing
- `__setitem__` for assigning to indexed values
- `__delitem__` for deleting indexed values
- `__iter__` for iteration over objects (e.g., in for loops)
- `__contains__` for in
- `__call__` for calling objects as functions
- `__int__` for converting objects to integer value.
- `__str__` convert object to string when print

```py
import random

class VagueList:
  def __init__(self, cont):
    self.cont = cont

  def __getitem__(self, index):
    return self.cont[index + random.randint(-1, 1)]

  def __len__(self):
    return random.randint(0, len(self.cont)*2)

vague_list = VagueList(["A", "B", "C", "D", "E"])
print(len(vague_list))
print(len(vague_list))
print(vague_list[2])
print(vague_list[2])
```

- `__del__` is used for del statement and it is called garbage collection(automatic deletion process).

## Class Methods

- They all have `cls` as the first parameter
- They return new object of the newly defined class.
- add `@classmethod` decorator before `def` statement

```py
class Rectangle:
  def __init__(self, width, height):
    self.width = width
    self.height = height

  def calculate_area(self):
    return self.width * self.height

  @classmethod
  def new_square(cls, side_length):
    return cls(side_length, side_length)

square = Rectangle.new_square(5)
print(square.calculate_area())
```

## Static Methods

- It starts with `@staticmethod`.
- They don't take new arguments.
- They are identical.
- They don't have self parameter.
- Accessed using dot after class name

```py
class Pizza:
  def __init__(self, toppings):
    self.toppings = toppings

  @staticmethod
  def validate_topping(topping):
    if topping == "pineapple":
      raise ValueError("No pineapples!")
    else:
      return True

ingredients = ["cheese", "onions", "spam"]
if all(Pizza.validate_topping(i) for i in ingredients):
  pizza = Pizza(ingredients)
```

## Property

`@property` is placed above the `def` statement to make a method read-only

```py
class Pizza:
  def __init__(self, toppings):
    self.toppings = toppings

  @property
  def pineapple_allowed(self):
    return False

pizza = Pizza(["cheese", "tomato"])
print(pizza.pineapple_allowed)
pizza.pineapple_allowed = True
```

## Setter or Getter

- It set or get the property’s value.
- the decorator has property name followed by `.` and `setter` or `getter`.

```py
class Pizza:
  def __init__(self, toppings):
    self.toppings = toppings
    self._pineapple_allowed = False

  @property
  def pineapple_allowed(self):
    return self._pineapple_allowed

  @pineapple_allowed.setter
  def pineapple_allowed(self, value):
    if value:
      password = input("Enter the password: ")
      if password == "Sw0rdf1sh!":
        self._pineapple_allowed = value
      else:
        raise ValueError("Alert! Intruder!")

pizza = Pizza(["cheese", "tomato"])
print(pizza.pineapple_allowed)
pizza.pineapple_allowed = True
print(pizza.pineapple_allowed)
```

## Error Handling

When an exception occurs, the program immediately stops.

### Error Types

- `ImportError`: an import fails;
- `IndexError`: a list is indexed with an out-of-range number;
- `NameError`: an unknown variable is used;
- `IOError`: unable to load file;
- `SyntaxError`: the code can't be parsed properly;
- `TypeError`: a function is called on a value of an inappropriate type;
- `ValueError`: a function is called on a value of the correct type, but with an inappropriate value.
- `KeyError`: trying to index a key that isn’t part of the dictionary.
- `MemoryError`: trying to create a list in a very extensive range.
- `AttributeError`: Trying to access an attribute of an instance that isn't defined or call an undefined method.

### Handling Error

```py
try: #try some code
except ZeroDivisionError: #run if there is a ZeroDivisionError
except (ValueError, TypeError): #or two different error#
except:#and all other errors#
# or
except Exception as e: # work on python 3.x
    logger.error('Failed to upload to ftp: '+ str(e))
finally: #it will run no matter what
```

### Raise an Error

- Raise statement is used to raise an error

```py
raise ValueError("display some other details")
raise IOError('Unable to load the file')
```

- It can be used in except block alone to reraise errors.

```py
except:
   print("An error occurred")
   raise
```

### Assert

- Assert statement is used to assume a condition then raise an error if condition is evaluated as `False`.

```py
assert 1==2
# AssertionError will be raised in runtime
```

- It can has an argument to display details

```py
temp = -10
assert (temp >= 0), "Colder than absolute zero!"
# AssertionError will be raised with the specified message
```

## File

### Open a File

```py
newfile = open("localfile.txt", 'r+')
# specify encoding
newfile = open("filename.txt", encoding="latin-1")
```

### File Mode

- `r`: read mode, it is the default mode
- `w`: write mode that can create new files and will overwrite old content
- `b`: binary mode for non-text files
- `a`: append mode for adding new content to the end of the file.
- `r+`: read and write mode

### File Method

```py
newfile.close()   # close file after done manipulation.
x = newfile.read()    # read all file
newfile,read(x)    # read x byte
newfile.read(y)    # read next y byte
newfile.read() #read rest all.
newfile.read(negativeValue) #read rest all.
newfile.readlines()    #return a list of lines
newfile.write(stringS)     #write content into the file and return the byte written.
```

### Read File Line by Line

```py
for line in file:
	print(line)      #print one line at a time
```

### Apply Error Handling

```py
try:
	newfile = open("localfile.txt")
	print(newfile.read())
finally:
	newfile.close()
```

```py
with open("localfile.txt") as newfile:
	print(newfile.read())    #This create a temperate variable newfile within the block. It will also make sure the file closure.
```
