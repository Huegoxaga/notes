# ``C#``

## Introduction
* In 2000, Microsoft announced the C# programming language.
* C# has roots in the C, C++ and Java programming language
* C# is an object-oriented language that run on the .NET Framework.
* C# graphical user interfaces (GUIs) are event driven. It waits to responds users input.
* Microsoft’s Visual Studio enables you to use C# as a visual programming language.
* C# can be used to create Windows, mobile, database application and Web services etc.
* The source code for programs that are executed and managed by the Common Language Runtime (CLR) is called managed code. It is firstly compiled into Microsoft Intermediate Language (MSIL), then translated the code in executable file by the just-in-time compiler or Just-In-Time (JIT) compiler into machine language.
.NET Framework consists of the Common Language Runtime(CLR) and the .NET Framework class library.
* When user creates a new project in Visual Studio A solution and a folder are created at the same time with the same name as the project.
* The project belongs to the solution
* Multiple projects can be included in a solution
* The folder stores files related to the project including:
  * A solution file (.sln)
  * A project file (.csproj)
* C# is case-sensitive.
* C# requires ``;`` at the end of each line.
* The apps have extension of .cs.
* Console apps input and output text in a console window, which in Windows is known as the Command Prompt.

## Basic Syntax

### Comments
* ``//`` single-line comment.
* ``/*   */`` multi-line comment.
* XML-style comment. It is used to describe classes and methods at the beginning of a class or method definition.
```c
///<summary>
///
///</summary>
///<param name="value"></param>
///<returns></returns>
```
### Region
region lets you specify a block of code that you can expand or collapse when using the outlining feature of the Visual Studio Code Editor.
```c
#region MyClass definition  
public class MyClass   
{  
    static void Main()   
    {  
    }  
}  
#endregion
```

the using directive is used to import namespaces in the app.

the System namespace contains the predefined Console class.

namespace is a collection of pre-defined classes, without the using directive class method from other namespace can only be used in namespace.class.method format.
//if using System is absent.
System.Console.WriteLine("abc");

———————————————————————————————
### Variables
Declare and assign a new variable.
modifier type name = value;

access modifier for variables can be either:
public     //default when modifier is not used in declaration.
private
protected  // this type of variable can be accessible from its derived class.

For implicitly typed variables, using keyword var, a value is mandatory. the compiler will determine the type automatically.
var x = 6; //x will be int

var num = 12;
var let the compiler to determine the value type.
This is called an implicitly typed variables. a value must be assigned to it.

const double PI = 3.1415926;
const keyword is for constant, must assign a value, name needs all-cap.
constants are all static.


C# use stack to store static value, like primitive type data and address reference for objects. It uses heap to store object information.

### Type
Instance variables of types char, byte, sbyte, short, ushort, int, uint, long, ulong, float, double, and decimal are all given the value 0 by default.
Instance variables of type bool are given the value false by default.
Reference-type instance variables are initialized by default to the value null.
null object cannot be accessed for its methods and properties.
If any type might be assigned a null value, it is then a nullable type. denoted as typeName?
nullable type has property HasValue, returns true if it is not null.

float x = 0.0f; //it is represented by 0.0f, can store 7 numbers after decimal point.
double x = 0.0d; //it is represented by 0.0d, can store 15 numbers after decimal point.
decimal x = 0.0m;  //it is represented by 0.0m, can store 28 numbers after decimal point.
		     //decimal work with price

### Operator
standard operator can all be used in C#.
int divide int will get a int result.

&& and
|| or
! not

is
object A is object B
is operator return true if A if of type B.

as
object A as object B
explicitly convert type A to B, if not successful, A become null.

conditional operator
  condition ? value1   : value2 ;    if true returns value1.

null conditional operator ?.
exampleObject?.Dispose();
It calls Dispose only if exampleObject is not null

decimal? salary = employee?.BaseSalary;
typeName?
this specify that the type is nullable.

null coalescing operator (??)
decimal salary = employee?.BaseSalary ?? 0M;
if employee is not null, salary is assigned the employee’s BaseSalary; otherwise, salary is assigned 0M.

————————————————————————————————————————
### Array

int[] arrayName = new int[5]   //an array of int with 5 elements.
or
int[] arrayName = new int[5] {1,2,3,4,5}; //assign values during instantiation.
or
int[] arrayName = new int[] {1,2,3,4,5};
or
int[] arrayName = {1,2,3,4,5};

arrayName[0] = 5  //assign 5 to the first element of this array.

Multidimensional Array
All of its element have the same length and type.

int[,] x = new int[4,4]; //a new 4 by 4 integer array.  
// the [,] indicates two dimensional array. for three dimensional array using [, ,]
int[,] x = { {1,2,3,4},{5,6,7,8},{9,10,11,12},{13,14,15,16} };
//x[1][1] is 6 from the above array.

Jagged array
It is an array of any array.

int[][] x = new int[3][] //an array of three array. these three array have unknown length.
int[][] x = new int[3][,]//an array of three two-dimensional array.
int[][] x = new int[][] {new int[] {1,2}, new int[] {1,2,3}, new int[] {1,2,3,4} }

Array Properties
arrayName.Length //return array length.
arrayName.Rank   //return the number of dimension.
arrayName.Max
arrayName.Min
arrayName.Sum

Array Class Methods
Array.Sort(arrayName);
Array.Reverse(arrayName);

———————————————————————————————————
### String
String type is similar to a one dimensional array it can be accessed using index in [].
Strings use double quotation.
String can be compared directly using comparison operators. Characters of each string are compared one by one until a difference is found.



\r\n will start a new line.

String indexer
s[index]  return the chat on the index.

String properties
s.Length returns the length of the string.

String methods
s.IndexOf(value) returns the index of the first occurrence of the value within the string.
if not found returns 0. value can be a string or character.
s.IndexOf(value, startPosition) search from start position.
s.IndexOf(value, startPosition, endPosition) search the value from start to end position.
s.Insert(index, value) inserts the value into the string starting from the specified index.
s.Remove(index) removes all characters in the string after the specified index.
s.Replace(oldValue, newValue)  replaces the specified value in the string.
s.Substring(index, length) returns a substring of the specified length, starting from the specified index. If length is not specified, the operation continues to the end of the string.
s.Contains(value) returns true if the string contains the specified value.
s.ToUpper()	//convert all to uppercase
s.ToLower()	//convert all to lowercase
s.ToTitleCase()  //convert the first letter to upper
s.StartsWith("stringX")	//return true if s string starts with stringX
s.EndsWith
s.Empty			//represents an empty string.
s.TrimStart() 		//removes leading spaces
s.TrimEnd()   		//removes trailing spaces
s.Trim()          		//removes leading and trailing space
s.Substring(Start)	//Returns the characters from the Start position to the end of the string, first position is 0.
s.Substring(Start, Length)	//Returns the characters from the Start position to specified Length
s.ToCharArray();
s.Split(char[]);  //uses all chars in the char[] as separator, separator the s into an array of strings.
s.CopyTo (int sourceBeginIndex, char[] destination, int destinationBeginIndex, int charCount);
String class method
String.Concat(s1,s2);
String.Equals(s1,s2);	//return true if s1 s2 have same context.
String class constructor
new string(character, number)   this repeatedly prints a character for a number of time.
new String("0",5); get a string with five "a" in a row
new string(charArray); //convert an array of char into string.
new string(charArray, index, length); //convert part of an array of char into string.


Formatted String
String interpolation allows the creation of formatted strings.

string person = "Jack";
Console.WriteLine($"Welcome to C# Programming, {person}!");

In {} variable names can be followed by a format specifier and alignment number like {variableName,alignment:format}

alignment number is a place holder.
,10 mean 10 space align to the right
,-10 means 10 space align to the left

C or c is for currency symbol
D or d is for whole number
N or n is for number has thousand separator and a default of two decimal places.
E or e using scientific notation and 6 decimal places.
F or f using certain number of decimal places(default 2)  //F1 represents one decimal place.

$ indicates the start of an interpolated string.
{} is the place holder for the value.

Substitution parameters can also be used, starting at {0}
string s = "World!"
Console.WriteLine("{0} {1}", "Hello", s);

Verbatim strings do not require \ to escape special characters. It is indicated by @
string s1 = @"\a\b\c"   //If s1 get printed, it will have output \a\b\c

Composite formatting of parameters
more information can added in {} after index for formatted substitution.
{index(starts from 0)[[,alignment][:formatString]}


### Character
Chars use single quotation.

Character Methods
char.IsDigit(‘a’);	//returns true if the character in the bracket is an integer.

### Type Conversion

Type casting
(double)19; //gets 19.0
((objType)i).Property;  //cast an object into a specific object when applying polymorphism.

Any type can be converted to its string representation explicitly by using that type’s .ToString() method:
double d1 = 3.14159;   string s3 = d1.ToString();
A string can be converted to any type by using that type’s .Parse() method:
string s4 = "3.14159";  double d2 = double.Parse(s4);

Each numeric variable type has a TryParse method
if(TryParse(StringX, out int valueX)){}
or
int valueX = 0;
if(TryParse(StringX, out valueX)){}
 //returns true(succeed) or false(failed), if true valueX is assigned.
DateTime & Boolean types include the TryParse method as well.

There is a Convert class that convert argument x into any type, specified in the method name.
Convert.ToDouble(x);
Convert.ToBoolean(x);
Convert.ToInt16(x);
Convert.ToInt32(x);
Convert.ToInt64(x);

### Generic Type
<T>, it is a form of representing all type as one. It only cares about reference relationship.

Generic Methods
static void Swap<T>(ref T a, ref T b) {
  T temp = a;
  a = b;
  b = temp;
}

<T> represents a generic type variable T

T then can be replaced by any other type

In Main method:
  int a = 4, b = 9;
  Swap<int>(ref a, ref b);
  //Now b is 4, a is 9

  string x = "Hello";
  string y = "World";
  Swap<string>(ref x, ref y);

Type can even be omitted

Multiple generic parameters can be used with a single method.
For example: Func<T, U> takes two different generic types

Generic Class
Generic type can be used in classes

class StackExample<T> {
}

It’s object and method also works like in the old way
Stack<int> intStack = new Stack<int>();
intStack.Push(3);


### Collections
Collections can change size.
All elements in collection have to be the same type.

Generic collection
using Systems.Collections.Generic;
 - List<T>
 - Dictionary<TKey, TValue>
 - SortedList<TKey, TValue>
 - Stack<T>
 - Queue<T>
 - Hashset<T>

Non-Generic Collections
using System.Collections
It can store objects, and it is slower
ArrayList
 - SortedList
 - Stack
 - Queue
 - Hashtable
 - BitArray


Collections can all be created using following format.
Collection<T> name = new Collection<T>();
and initializer
var name = new Collection<T> {element1, element2, element 3, ... };


List
List is a collection
List<int> li = new List<int>();

List<int>  This is the type identifier for a list of integer.

Use initializer
var items = new List<string>  {"a","b","c"};
List<T> properties and methods include:
Count A property that gets the number of elements contained in the list.
Item[int i] Gets or sets the element in the list at the index i. Item is the indexer and is not required when accessing an element. You only need to use the brackets [] and the index value inside the brackets.
Add(T t) Adds an element t to the end of the list.
RemoveAt(int index) Removes the element at the specified position (index) from the list.
Sort() Sorts elements in the list.
Capacity - A property that gets the number of elements the list can hold before needing to be resized.
Clear() - Removes all the elements from the list.
TrimExcess() - Sets the capacity to the actual number of elements in the list. This is useful when trying to reduce memory overhead.
AddRange(IEnumerable coll) - Adds the elements of collection coll with elements of the same type as List<T> to the end of the list. IEnumerable is the collections interface that supports simple iteration over the collection.
Insert(int i, T t) - Inserts an element t at a specific index i in the list.
InsertRange(int i, IEnumerable coll) - Inserts the elements of a collection coll at a specified index i in the list. IEnumerable is the collections interface that supports simple iteration over the collection.
Remove(T t) - Removes the first occurrence of the object t from the list.
RemoveRange(int i, int count) - Removes a specified number of elements count from the list starting at a specified index i.
Contains(T t) - Returns true if the specified element t is present in the list.
IndexOf(T t) - Returns the index of the first occurrence of the element t in the list.
Reverse() - Reverses the order of the elements in the list.
ToArray() - Copies the elements of the list into a new array.

Sorted list
A sorted list is a collection of key/value pairs
Duplicated keys are not allowed in the sorted keys
SortedList<string, int> sl = new SortedList<string, int>();

SortedList<K, V>
properties include:
Count - Gets the number of key/value pairs contained in the sorted list.
Item[K key] - Gets or sets the value associated the specified key contained in the sorted list. Item is the indexer and is not required when accessing an element. You only need to use the brackets [] and the key, value.
Keys - Gets a sorted and indexed collection containing only the keys in the sorted list.
SortedList<K, V> methods include:
Add(K key, V value) - Adds an element with a specific key, value pair into the sorted list.
Remove(K key) - Removes the element with the specific key, value pair associated with the specified key from the sorted list.
SortedList<K, V> properties and methods:
Values - Gets a sorted and indexed collection of the values in the sorted list.
Clear() - Removes all the elements from the sorted list.
ContainsKey(K key) - Returns true when the specified key is present in the sorted list.
ContainsValue(V value) - Returns true when a specified value is present in the sorted list.
IndexOfKey(K key) - Returns the index of the specified key within the sorted list.
IndexOfValue(V value) - Returns the index of the specified value within the sorted list.

Bit Array
A bit array is a collection of bits
BitArray ba1 = new BitArray(4);

BitArray properties include:
Count -  Gets the number of bits in the bit array.
IsReadOnly - Gets a value indicating if the bit array is read only or not.

BitArray methods include:
Get(int i) - Gets the value of the bit at a specified position i in the bit array.
Set(int i, bool value) - Sets the bit at a specified position i to a specified value in the bit array.
SetAll(bool value) - Sets all the bits to a specified value in the bit array.
And(BitArray ba) - Performs the bitwise AND operation on the elements of the bit array object with a specified bit array ba.
Or(BitArray ba) - Performs the bitwise OR operation on the elements of the bit array and the specified bit array ba.
Not() - Inverts the bit values of the bit array.
Xor(BitArray ba) - Performs the bitwise XOR operation on the elements of the current bit array object and the elements in the specified bit array ba.

Stack
A stack is a Last In, First Out (LIFO) collection of elements
Stack<int> s = new Stack<int>();

Stack<T> properties include:
Count - Returns the number of elements in the stack.

Stack<T> methods include:
Peek() - Returns the element at the top of the stack without removing it.
Pop() - Returns the element at the top of the stack and removes it from the stack.
Push(T t) - Inserts an element t at the top of the stack.
Clear() - Removes all the elements from the stack.
Contains(T t) - Returns true when the element t is present in the stack.
ToArray() - Copies the stack into a new array.

Queue
A queue is a First In, First Out (FIFO) collection of elements
Queue<int> q = new Queue<int>();

Queue<T> properties include:
Count - Gets the number of elements in the queue.

And methods include:
Dequeue() - Returns the object at the beginning of the queue and also removes it.
Enqueue(T t) - Adds the object t to the end of the queue.
Clear() - Removes all objects from the queue.
Contains(T t) - Returns true when the element t is present in the queue.
Peek() - Returns the object at the beginning of the queue without removing it.
ToArray() - Copies the queue into a new array.

Dictionary
Duplicate keys are not permitted
Dictionary<string, int> d = new Dictionary<string, int>();

Dictionary<K, V> properties include:
Count - Gets the number of key/value pairs contained in the dictionary.
Item[K key] - Gets the value associated with the specified key in the dictionary. Item is the indexer and is not required when accessing an element. You only need to use the brackets [] and key value.
Keys - Gets an indexed collection containing only the keys contained in the dictionary.

Dictionary<K, V> methods include:
Add(K key, V value) - Adds the key, value pair to the dictionary.
Remove(K key) - Removes the key/value pair related to the specified key from the dictionary.

Here are the additional Dictionary<K, V> properties and methods:
Values - Gets an indexed collection containing only the values in the dictionary.
Clear() - Removes all the key/value pairs from the dictionary.
ContainsKey(K key) - Returns true if the specified key is present in the dictionary.
ContainsValue(V value) - Returns true if the specified value is present in the dictionary.

Hash set
A hash set is a set of unique values where duplicates are not allowed.
They do not have index positions and elements cannot be ordered.
HashSet<int> hs = new HashSet<int>();

Count Returns the number of values in the hash set.

And methods include:
Add(T t) Adds a value (t) to the hash set.
IsSubsetOf(ICollection c) Returns true if the hash set is a subset of the specified collection (c).
Remove(T t) Removes the value (t) from the hash set.
Clear() Removes all the elements form the hash set.
Contains(T t) Returns true when a value (t) is present in the hash set.
ToString() Creates a string from the hash set.
IsSupersetOf(ICollection c) Returns true if the hash set is a superset of the specified collection.
UnionWith(ICollection c) Applies set union operation on the hash set and the specified collection (c).
IntersectWith(ICollection c) Applies set intersection operation on the hash set and the specified collection (c).
ExceptWith(ICollection c) Applies set difference operation on the hash set and the specified collection (c).


Most the collection type has the following methods
Add (item As Object)		Method: adds item to the collection, returning its index position
Clear (  )			Method: removes all items in the collection. No return value
Contains (value As Object)	Method: returns True if value is found at least once in the collection.
Count				Property: returns the number of items in the collection. Read-only
IndexOf (value As Object)	Method: returns the Integer index position of the first occurrence of value in the collection. If value is not found, the return value is   –1

Insert (index As Integer, item As Object)
				Method: insert item in the collection at position index. No return
value
Item (index As Integer)	Property: returns the object located at position index
Remove (value As Object)	Method: removes value from the collection. No return value
RemoveAt(index As Integer)	Method: removes the item at the specified index. No return value


Control Structure

if(condition){
   //a
  //b
}

if(condition) //code goes here if only one line.

if(con){}else{}

if(con1){}else if(con2){}else{}

int x = 3;
switch(x)
{
   case 1:
                       //code1
                      break;
   case 2:
                      //code2
 
                    break;
   default:  
                  //code if none matches
                 break;
}//C# require all case and default code must end with a break statement.

while(condition) {}

It can be shorten like using the following format:
int x = 0;
while(++x < 6)
    Console.WriteLine(x);


for(init; condition ; increment expression) {}

init parameter can be defined before for loop:
int init=0;
for(;con;in){}

Increment parameter can be defined in the loop code:
for(init; con; ){i++;}

for(;;){} is an infinite loop

do{}while(con);
assign array element to varName in each loop.
foreach(type varName in arrayName) {

}

————————————————————————————————————

Method
modifier [static] <return type> methodName(type1 par1, type2 par2, ... , typeN parN)   {  }

Access modifier for methods:
public
private
protected   this type of variable can be accessible from its derived class.
sealed - not available for inheritance.

Return type should be void if no value is returned from the method.

Keyword static can be added before return type so Main method can access it without creating an instance of the method's class. because, static method can access only static methods.

In method definition, the default value of a par can be set at the end of parameter list
static int Sum(int x, int y = 10 ){}

Named arguments
It can give arguments a name in method
static int Vol(int h, int w, int l){
return h*w*l
}
In main method method can be called in the following ways
int v = Vol(w:2, h:9, l:3);

ref keyword can be used to pass the reference of a value. it will change the original value during operation. when use ref for method the keyword should be used in method definition and in method call
static void Method(ref int x){}
Method(ref a);

like ref, keyword out can be used to output value from a method.

static void GetValues(out int x, out int y)
{
   x = 3;
   y= 12;
}
static void Main (string[] args)
{
   int a, b;
   GetValues(out a, out b);
   // now a = 3, b = 12

Variable-length argument lists allow you to create methods that receive an arbitrary number of arguments.It uses params modifier and exists as the last parameter among all parameters of the method.
It usually works with array
static void Method(params int[] x){
}
when call
Method(1,2)   -> x = [1,2]
Method(1,2,3,4) -> x = [1,2,3,4]

Method Overloading
Method overloading also works for methods have same name but different parameters.

//method override
public override void Method1()
{               
	Console.WriteLine("Derived - Method1");           
}  

Delegate
It helps using method as a parameter of other methods.
public bool RunTheMethod(Func<string, int> myMethodName)
{
    // ... do stuff
    int i = myMethodName("My String");
    // ... do more stuff
    return true;
}

Extension Method
Extension method are available from various classes in C#
it can be called by objects using . in between or use ClassName.ExtensionName(objectName)
extension methods are static methods from static class
example for define extension class:

static class TimeExtensions
{
   // display the Time2 object in console
   public static void DisplayTime(this Time2 aTime)
   {
      Console.WriteLine(aTime.ToString());
   }

   // add the specified number of hours to the time
   // and return a new Time2 object
   public static Time2 AddHours(this Time2 aTime, int hours)
   {
      // create a new Time object
      var newTime = new Time2() {
         Minute = aTime.Minute, Second = aTime.Second};

      // add the specified number of hours to the given time
      newTime.Hour = (aTime.Hour + hours) % 24;

      return newTime; // return the new Time2 object
   }
}

//this keyword before a method’s first parameter notifies the compiler that the method extends an existing class

Recursion
a method can call itself in the method definition. an exit condition should exist for recursive function.

Expression Bodied Methods
static int Cube(int x) {
                      return x * x * x;
}
can be written as.
static int Cube(int x) => x * x * x;

—————————————————————————————————
Class
Classes can have property and method
Public property and method can be accessed by class object using dot.
A class can be sealed. It makes the class not available for inheritance.
C# enables nested class, a class definition contains within another class’s definition.

Simple Class example
class Account
{
	private string name;

	public void SetName(string accountName)
	{
		name = accountName;
	}

	public string GetName( )
	{
		return name;
	}
}

readonly keyword can be added to indicated that the variable can only be edited in declaration or from within a constructor.
readonly variable names use Pascal case by convention.
private readonly string name;  //it can be declared without initialization(without assigning a value.)
a class can be static, once it is static all of its method and variable should be static. It can not be instantiated.

Class Properties
Property name has its first letter capitalized.
Properties are accessed by using objectName.Property.
The set accessor uses the keyword value as its parameter.
a property can also be private.
accessors of a property can be omitted.


Simple Class example using properties

class Account
{
	private string name;
	public string Name
	{
		get
		{
			return name;
		}
		set
		{
			name = value;
		}
	}
}// the private name, can now be accessed using property Name.



Example in Main class:
using System;
class AccountTest
{
	static void Main( )
	{
		Account myAccount = new Account( );

		Console.WriteLine($”Initial name is: {myAccount.Name}”);

		Console.Write(“Please enter the name: ”);
		string theName = Console.ReadLine();
		myAccount.Name = theName;

		Console.WriteLine($”myAccount’s name is: {myAccount.Name}”);
	}
}



Using auto-implemented property to shorten the code with simple getter and setter.
these accessors only read or write the original value of the private property.
public string Name {get; set;}
//keyword private can be used before both set / get, or before any one of them.

Using auto-property initializers shorten the code in the declaration
public type propertyName { get; set; } = value;
public int x ( get; set; } = 0;

In UML, a property is represented in guillemets.
Ex,
+<<property>> Name: string

Constructor
constructor can also be used as public. It can also be overloaded. It can have default values.
public ClassName(parm1,…){ }

Constructor Chaining
public ClassName(x):this(){}
the ClassName(x) constructor is chained with the ClassName() constructor. When ClassName(x) is called ClassName() will be call first, then ClassName(x) will be called.

Define constructor for a derived class.
public CommissionEmployee(string firstName, string lastName,
      string socialSecurityNumber, decimal grossSales,
      decimal commissionRate)
      : base(firstName, lastName, socialSecurityNumber)
   {
	GrossSales = grossSales; // additional properties in the current constructor.
      CommissionRate = commissionRate;
   }
base keyword is used to borrow property assignment from the base constructor.

If the base class does not have a default constructor, every derived constructor must explicitly invoke one of the base class constructors using base

public Account(string accountName)
{
	Name = accountName;
}

constructor can be static, when a static variable is accessed, the static method will be called.
In UML, it can be
<<constructor>> Account(accountName: string)


Partial class????

Destructor
it is called when an object is deleted or destroyed.
it does not take modifiers or have parameters.
the name of the destructor is the class name with a ~ prefix.
~ClassName()
{
//code for releasing resources in a destructor.
}

Operator Overloading
Operator overloading can be used to define custom actions for operators. Then, these operator can be used in between two object variables.

public static Box operator+ (Box a, Box b) {
	int h = a.Height + b.Height;
	int w = a.Width + b.Width;
	Box res = new Box(h,w);
	return res;  //return type is also Box
}
//all arithmetic operator can be define, for comparison operator they return bool, also < and > should be defined together. Same for <= and >=, == and !=(object .Equal()method works better with many other language in .NET it is more recommended than ==)

Conversion operator overloading
public static implicit operator TypeConvertToName(TypeToConvert variableName){}
If the operation is guarantee to succeed with no data lost, use implicit keyword. Otherwise, use explicit.
#########################
Indexers
Indexers can be used to create index for a class objects.
class Clients {
	private string[] names = new string[10];
	public string this [int index] {
	get{ return names[index];}
	set{ names[index] =value; }
	}
}}

In main;
Client c = new Client();
c[0] = “Dave”;
c[1] = “Bob”;
Console.WriteLine(c[1]);
//Output Bob

Inheritance
In C# the child class is called derived class, the parent class is called the base class.
One derived class can have only one base class.

class DerivedClass : BaseClass {
}

When an object of the derived class is instantiated, the base class constructor will be called first, then the derived class constructor will be called if it has one.
When an object of the derived class is deleted, the derived class destructor will be called first, then the base class destructor will be called if it has one.

A object can be created as a base type and used as a specific derived type.
DerivedType x = new BaseType();

A method can be defined as a virtual method in base class, then overridden in different derived class.
class BaseClass {
	public virtual void MethodName() {
	}
}
class DerivedClass : BaseClass {
	public override void MethodName() {
	}
}


new keyword in the derived class can be use to hide base.method, it works even the base method is not a virtual method.
Keyword base can be used to represent the method from base class.
base.methodName();

In a derived class:
public new void methodName()
{
	base.methodName();
	//additional changes goes here.
}

Abstract class
If method or property does not need to be defined in the base class, the method can be an abstract method or property, the class itself also need to be abstract to hold an abstract method and property. abstract class cannot be instantiated. non-abstract class are described as concrete class.
abstract class BaseClass {
	public abstract PropertyType MyProperty { get; set; }

	public abstract void MethodName();
}
class DerivedClass : BaseClass {
	public override void MethodName(){
	//implementation for the abstract method is mandatory.
	}
}

Interface
If a class has only abstract members, it is an interface.
All members of an interface are always public.
public interface IShapes	//interface name usually starts with an ‘I’
{
	void AbstractMethodName();
}

Interface can contain properties and method, however it cannot contain variables.
Interface can implement one or more other interfaces. It called extending or combining an interface.
A class can implement multiple interfaces, separated by , after :
class Name : Ione, Itwo, Three {
	public void AbstractMethod(){
	//keyword override is not needed in this case.
	}
}

A class can have a reference to its interface class.
Interface object can not be used created, but an interface reference can be created.
To use a method from interface reference, an implemented class can be instantiated and assign this object to the interface reference.

If a Document class implements IPrintable  
IPrintable myPrintable = new Document();
IStorable[] myStorableArray = new IStorable[3];  

Document myDoc = new Document(…);  
IStorable myStorable = myDoc;  

myStorable.method();


Interface IEnumerable<T>
Implements this interface enable a data/object type to be used for iteration like foreach loop and linq queries.
Arrays and Collections already implement the IEnumerable<T>

Interface IComparable<T>
Implements this interface enable a data/object type to be comparable. like orderby in linq
All built-in types have implemented IComparable.

Interface IComponent<T>
Implemented by classes that represents a component
Interface IDisposable<T>
Implemented by classes that must provide an explicit mechanism for releasing resources.
——————————————————————————————————————
Delegate
It is declared as a reference of methods with the same parameters and return types.
It can be instantiate and assigned with an method of certain class.
It can be then pass to a class method which take this delegate as a parameter.

In the class that declare and use the delegate:
//Declare delegate in DelegateClass
public delegate returnType DelegateName();
//Declare method take the delegate
public void DelegateMethodName(DelegateName DelegateVariableName){
	//use delegate method here as DelegateVariableName()
}

Assume that there is a method called SomeMethod in OtherClass.

In main:
DelegateClass newDelegateClass = new DelegateClass();

OtherClass newOtherClass = new OtherClass();

DelegateClass.DelegateName newDelegate = new DelegateClass.DelegateName(newOtherClass.SomeMethod);

//then the SomeMethod can be called by the delegate.
newDelegateClass.DelegateMethodName(newDelegate);




——————————————————————————————————————
Struct
It is a customized type which can store multiple value inside.

struct Quality {
	public string body;
	public string aroma;
	public double score;
}
In Main class
Quality x;
x.body = “good”;
b.score = 100.0;

struct can have constructor. new keyword is required to use struct constructor.
struct Quality {
	public string body;
	public string aroma;
	public double score;
	public Quality(string x, string y, double z) {
		this.body = x;
		this.aroma = y;
		this.score = z;
	}
}

in main:
Quality s = new Quality(“good”, “nice”, 100.0);

types like int and double in C# are struct.
——————————————————————————————————
Enum
It is a list of names as value.
enum Days {Mon, Tue, Wed, Thu, Fri };
Now enum days has 5 constant, Days.Mon, Days.Tue, Days.Wed, Days.Thu, Days.Fri
the enum now has type Days.
Ex:
Days x;
x = Days.Mon;


enum elements can have a value starts from 0, increased by 1 to the right
int x = (int)Days.Mon;  //x = 0
The value can be assigned specifically
enum Days {Mon, Tue = 10, Wed, Thu, Fri };
Then Days.Mon is 0, Days.Tue is 10, Days.Wed is 11, Days.Thu is 12.

enums can be used with switch cases
switch (x) {
	case Days.Mon:
		//code
		break;
	case Days.Tue:
		//code
		break;
}

—————————————————————————————————
Random class
Random randomObject = new Random( );

int newNumber = randomObject.Next(1,7)  //generates random number from 1 to 6.
randomObject.Next()		//generates random integer from 0 to 2,147,483,647
randomObject.Next(100)	//generates random integer from 0 to 99
randomObject.NextDouble()	//generates random floating-point number in range [0.0,1.0)

A seed value is used by the random number generation algorithm. It produces a repeated series of number as “random” numbers.
Seed value can be assigned in the random object constructor.

Random randomObject = new Random( seed:int );

By default, C# uses a current time value as the seed value as it keeps changing.
—————————————————————————————————————
DateTime class

DateTime.Now; 	//return the current date & time
DateTime.Today; 	//return the current day
DateTime.DaysInMonth(2016,2); 	//return the number of days in the specified month
DateTime date1 = new DateTime(2017, 8, 30);
DateTime date2 = new DateTime(2017, 8, 30, 2, 25, 30);
DateTime.AddYears(18);  //get date 18 years later.
.ToShortDateString() method


can be converted to string
string s1 = date5.ToString();

convert a string to datetime object
string s2 = "30/08/2017 12:00:00 AM”;
DateTime date6 = DateTime.Parse(s2);
—————————————————————————————————————
Math class
It is static class.
Math.PI;   //return pi
Math.E
Math.Max()
Min
Abs
Sin
Cos
Pow
Round
Sqrt

———————————————————————————————————————
Object class
If a class does not specify that it inherits from another class, it implicitly inherits from object class.

Class object’s default (empty) constructor does nothing.

Class Object Methods
Equals()
Finalize()
GetHashCode()
GetValueOrDefault()
GetType()	returns the object type in a string
Memberwise-Clone()
Reference-Equals(): static method returns true if two objects are the same instance or are both null.otherwise returns false
ToString method returns a string that describes the class object when called.


Exception Class

Try & Catch
The exception in the try block will be caught in the catch block as its parameter
if there are many catch block the catch all exception block should be the last one.
Exception object has the following properties.
Message contains the exception message.
HelpLink specifies the location of a help file that describes the problem.
Source specifies the name of the app or object that caused the exception.
TargetSite specifies the method where the exception originated.
the InnerException property stores the original exception object of a newly defined exception object.
StackTrace property trace the exception, show file location and line numbers for the exception.
ToString method of exception presents the error message.

A finally block can be added in the last, for codes that will be executed for sure.
Finally block is usually used to close a file in the end.
try{
}
catch(Exception e) {
}
finally {
}
//This is the catch all error try-catch block with finally block.


static void CodeWithCleanup()
{
    System.IO.FileStream file = null;
    System.IO.FileInfo fileInfo = null;

    try
    {
        fileInfo = new System.IO.FileInfo("C:\\file.txt");

        file = fileInfo.OpenWrite();
        file.WriteByte(0xF);
    }
    catch(System.UnauthorizedAccessException e)
    {
        System.Console.WriteLine(e.Message);
    }
    finally
    {
        if (file != null)
        {
            file.Close();
        }
    }
}

catch(ExceptionType name) when(condition)
a certain exception can be only caught under certain condition

catch when(condition)
an general exception can be only caught under certain condition

Exception type
DivideByZeroException
FileNotFoundException
FormationException
IndexOutOfRangeException
InvalidOperationException
OutOfMemoryException

Exceptions can be thrown using throw keyword.
throw new ExceptionType(“message”,InnerExceptionType); //the inner exception stores info.

To create user defined exception class

public class NegativeNumberException : Exception
{
   // default constructor                                
   public NegativeNumberException()
      : base("Illegal operation for a negative number")
   {
      // empty body                                      
   }

   // constructor for customizing error message         
   public NegativeNumberException(string messageValue)
      : base(messageValue)
   {
      // empty body                                     
   }

   // constructor for customizing the exception's error
   // message and specifying the InnerException object
   public NegativeNumberException(string messageValue, Exception inner)
      : base(messageValue, inner)
   {
      // empty body                                    
   }
}



The using statement simplifies writing code in which you obtain a resource.
It is possible to nest multiple using statements one after another.
using (var exampleObject = new ExampleClass())
{
   exampleObject.SomeMethod();
}


The using statement code is equivalent to
 {
   var exampleObject = new ExampleClass();
   try
   {
      exampleObject.SomeMethod();
   }
   finally
   {
      if (exampleObject != null)
      {
         ((IDisposable) exampleObject).Dispose();
      }
   }
}



———————————————————————————————————————
File I/O
file I/O requires library System.IO
using System.IO

To open a file use FileStream class
FileStream file = new FileStream(“path.txt”, FileMode.option, FileAccess.option);
FileMode.option can be:
Append, Create, CreateNew, Open, OpenOrCreate, Truncate
FileAccess.open can be:
Read, ReadWrite, Write

To write a file use StreamWriter class
Object Instantiation:
StreamWriter data = new StreamWriter(file);
Write methods
data.Write(“abc”);
data.WriteLine(“abc”);

To read from a file, use StreamReader class
Object Instantiation:
StreamReader data = new StreamReader(file);
string s = data.ReadToEnd(); //read entire file
string s = data.Read(); 	//read file character by character
string s = data.ReadBlock();
string s = data.ReadLine();    //read file line by line, if there is no more data in the file return null.

When file I/O is over, close the stream and the file.
close stream
data.Close();
close file
file.Close();

view file information
use FileInfo class
Object Instantiation
FileInfo properties = new FileInfo(“path.txt”);
properties.FullName; //return file name.
properties.CreationTime; //return file creation time
properties.LastAccessTime;
properties.LastWriteTime;
properties.Length; //return file size.
properties.Attributes;
properties.DirectoryName;
properties.Exists;
properties.Extension;
properties.IsReadOnly;

To get information about the directory, uses directory class
Object Instantiation:
string[] drives = Directory.GetLogialDrives();//drives would be an array of logical drives.
string[] dirs = Directory.GetDirectories(“c:\\”); //return an array of directory names under c drive.
string[] file = Directory.GetFiles(“c:\\”); //return an array of file names under c drive.


LINQ
System.Linq namespace is a library that allows programmer using LINQ to Objects provider to write SQL in the code.
LINQ uses deferred execution—the query executes only when you access the results, not when you define the query.


var sortedValue =
	from value in arrayName
	where value > 10
	orderby value descending  //delete descending for ascending result.
	select value;

select clause can create new object type using:
var names =
	from e in employees
	select new {e.FirstName, e.LastName}

This can be used to generate new data according to the original data, It is called transformation.

where clause adopts syntax from SQL like
where (e.MonthlySalary >= 4000M) && (e.MonthlySalay <= 6000M)
orderby clause can have more than one data enties.
orderby e.Lastname, e,FirstName

let clause can be used to create a new range variable to store atemporary result for use later in the LINQ query
var convertUpper =
	from item in items
	let uppercaseString = item.ToUpper()
	select upperString;


Methods
Any	returns true if there is at least one element, false if not.
First	returns the first result.
Count 	returns the number of results.
Distrinct 	removes duplicate elements.




Linq has extesion method ToArray and ToList
These methods immediately execute the query on which they are called. the query is only executed once.

SQL
            try
            {
                string connectionString = @"Data Source=.\SQLEXPRESS;Initial Catalog=COMP10204_Lab5;Integrated Security=True";
                using (SqlConnection sqlConnection = new SqlConnection(connectionString))
                {
                    sqlConnection.Open();
                    string doctorQuery = "SELECT * FROM DOCTOR";
                    SqlCommand doctorCommand = new SqlCommand(doctorQuery, sqlConnection);
                    SqlDataReader doctorReader = doctorCommand.ExecuteReader();
                    while (doctorReader.Read())
                    {
                        int doctorId = int.Parse(doctorReader["DOCTORID"].ToString());
                        string actor = doctorReader["ACTOR"].ToString();
                        int series = int.Parse(doctorReader["SERIES"].ToString());
                        int age = int.Parse(doctorReader["AGE"].ToString());
                        int debut = int.Parse(doctorReader["DEBUT"].ToString());

                        byte[] photo = (byte[])doctorReader["PICTURE"];
                        MemoryStream stream = new MemoryStream(photo);
                        Image image = Image.FromStream(stream);

                        doctorsList.Add(new Doctor(doctorId, actor, series, age, debut, image));
                    }
                    sqlConnection.Close();
	}

Partial indicates that the class is specified in multiple files
movie.DateSeen.ToShortDateString();  

DateTime.Today
