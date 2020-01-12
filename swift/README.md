Swift history
launched at the Worldwide Develop Conference in 2014.
Swift 2 was released in June, 2015 and became open source.
Swift 3 and Xcode 8 was released in 2016, APIs were renamed, projects were rebuilt and adaption was needed.
Swift 4 and Xcode9 was released in 2017, backward compatibility was supported.
Swift 4.2 was released as a minor update in 2018. and later Xcode 10


Swift introduction
a "fast, modern, safe, interactive" language are used to replace Objective-C language.
Swift code works side-by-side with Objective-C.
Swift combines the best of C and Objective-C.
Swift is a type-safe(sensitive) language, but it can deduce the data type when assign values.
Semi-colon is fully optional in Swift, unless you wish to place several independent statements on a single line, in which case the semi-colon is required.
one file per class.


Comments
Single line comments is //
Multiline comment is /*...*/ it can be nested.

Basic Syntax
let keyword for constants
var keyword for variables.




Variable name rules
Variables name can be anything including Unicode characters but no blank spaces, mathematical symbols, arrows, private-use (or invalid) Unicode code points, or line and box-drawing characters. Or duplicated name.
Cannot starts with a number.
Multiple variables can be declared on a single line, separated with commas
Code   let x = 0.0, y = 0.0, z = 0.0


Type annotations:
Type is used to initialize specific types
Code         var x: Int    //initialize an integer x.
Or everything in one line.
Code var red, green, blue: Double
Swift auto deduce data type when assign a value
Code var x=1  //x is an integer.
Swift always chooses Double For floating point.


Operators

range operator (…) left must be smaller than or equal to the right part.
The closed range operator
x. . .                         all numbers greater than and equals to x
. . .x                         numbers smaller than and equals
x. . y                        numbers in between x and y including x and y.
The half-open range operator
a..<b b is not included

Logic operator are in standard C-based format and left-associative for operator "and", "or".



\n new line

logic operator
==  equals
!=   not equals
>=
<=
&& and

All standard plus identity operators, === and !==, which test whether two object references both refer to the same object instance.



An operator is a special symbol or phrase used to check, change, or combine values.
-Unary Operator: Has a single target (-a). A unary prefix operator is placed before the target (!b).
-Binary Operator: Has two targets (4 + 5) and is infixed, appearing between the two targets.

+concatenation (no auto-casting)(cannot auto convert other types into string when connected by + )

-Ternary Operator: Has three targets. Like C, Swift has one ternary operator, the ternary conditional operator (a ? b : c).

question ? answer1 : answer2
If question true return answer1 else return 2.
Ex:  gender == 0 ? print("male") : print("female")

The values targeted by operators are called operands.

Operator in swift is identical with java mostly, except % is called remainder not module since different treatment for negative values.

+= is also used as x = x +



Types:
Placeholder constant?????


Int (auto cast from int to double in a one double and one int operation and double-int mixed array)
Double
Float
Bool(true/false)
String (it is a basic type in Swift using "")

empty String creation:
Code
var name =""
or
var name = String()

Type casting:  
type(varname)
Ex:   String(sum)
or
String([Character])

String interpolation
auto convert other types in one string
"strings \(othertypes)"

Optional type
Code var myCode: Int? = 404  // variable myCode is an optional integer with default value 404.
must set type for optional types
? means the variable can have a int value or nothing.
! means 100% sure that it should have a value somehow before access its value.
You set an optional variable to a valueless state by assigning it the special value nil
An optional variable with no default value is automatically set to nil for you
all optional type need to be checked before use or use it followed by the ? sign.

coalescing operator: ??
x ?? ""
?? check if an optional type has a value and set a default value after ??.


Checking optional:
Force unwrapping
if condition is often used. After making sure there is a value add ! after the variable, show you are sure.
Code
if x!=nil{
    print(x!)
}

Optional binding (recommended way)
It is done by making temp constant variables. Using if let statement to test if the optional var has a value.
if let newx = x {print(newx)}   //you can use x instead of newx.
or
if let ….. else

as! or as? is used for downcasting a type into s subclass’s object. use as! if it is clear the downcasting can perform correctly.


for all non-optional value(no ?) they have to assign an initial value when they are created.

weak var
means it can have no value.

Lazy var
A lazy stored property's initial value is not calculated until the first time it is used.
Only var can be lazy.



___________________________________________________________________________________
Array
All variables in array should be in the same type.
It can be written as Array[T] or [T].

Empty array:
var name = [Int]()

Initializer:        
var name = Array(repeating:value, count: 4)   
//repeating is the initial value and count is the length.

Literal:         
var name:[String] = [1,2,3,4,5]       
or   
var name = [1,2,3,4,5]

can use + for concatenation  or  += for append
index starts at 0   
range operator can be used as a index
_____________________________________________________________________________________
Set
Unordered, same type, faster than array.
It can be written as Set<T>

Empty set:
var name = Set<Type>()

Literal:
var name: Set<Type> = [1,2,3]
or
var name: Set = [1.2.3]

_____________________________________________________________________________________
Dictionary
Unordered, with keys as index.
key or value should be in same type.
It can be written as Dictionary<KeyT,ValueT>   or [KeyT:ValueT]

Empty:
var name = [Type:Type]()

Literal:
var name: [Type:Type] = [1:1,2:2,3:3] 			
or 		
var name = [1:1,2:2,3:3]

name[key] = value   //add new item    
assign nil to a key value will remove this key and value pair.           

x = [key1:value1, key2:value2, ….]
name[keyX]           returns valueX

to print all items in the dictionary.
for (key,value) in dictionaryName {
	print(\(key) : \(value))
}

access only key or value using for loop
for key in name.keys{
}

for value in name.values{
}
//keys and values are keywords for this type of accessing.

Method:
dictionaryName.updateValue("new value", forKey: "X")
//It updates new value and returns the old value.
dictionaryName.removeValue("new value", forKey: "X")
//It removes old value and returns the old value.

nil is returned if no value is found when accesses dictionaries.


Tuples
Tuples (Type, Type) or more elements.
Tuples group multiple values into a single, compound value.

Initializing tuples:
let tuplesName = (100, "OK")

Naming tuples:
let (score, comment) = tuplesName

Accessing tuples:
print(score)
//Output: 100

the content is accessible using variable name and index numbers
let name = (x, y)
name.0   
//get x
name.1
//get y

Can define tuples value with names using following way.
let name = (name1: value1, name2: value2)
name.name1  
//get value1
name.name2
//get value2

Decomposing Tuples
var person = (firstName: "John", lastName: "Doe")
var (firstName, lastName) = person
print(firstName)
//Output: John

Multiple Assignment:
var (x, y, z) = (1, 2, 3)
//the same as
var x = 1
var y = 2
var z = 3


______________________________________________________________________________
Enumeration
Enumeration is value type(primitive variable)
An enumeration defines a brand new common type for a group of related values.
All the values that are defined within the enumeration.

enum Name {
  case Name1
  case Name2
  case Name3
  case Name4
}

Or
enum Name{
case Name1, Name2, Name3, Name4
}

Access through Name.Name1
.Name1 is its number.


For some input if the type is already known, the name can be shorthanded to .something,
_____________________________________________________________________________________
if structures

if….else

if condition {
} else if condition{
}else{
}

if let can be use to check the value existence.

switch structures

switch value {
case value1:

case value2:

case value3, value4, value5:  (can use range operators here, )

default:(if nothing matches)
in switch only the codes in one situation(first) block gets run.


Where evaluate outcomes with conditions.

let myPoint = (1, -1)
switch myPoint {
   case let (x, y) where x == y:
      print("(\(x), \(y)) is on the line x == y")
   case let (x, y) where x == -y:
     print("(\(x), \(y)) is on the line x == -y")
   case let (x, y):
     print("(\(x), \(y)) is just some arbitrary point")
}


for loop
for i in x..y(or arrayname) {
   print(i)
}


while loop
while a < b {
   print(a)
   a+=1
}

Repeat-While
repeat {
   x -= 1
} while x > 0
Repeat block run at least once

control transfer
break                     //exit
continue                //starts from begin
fall through in switch, move the code to next case without check condition.

basic statements
print(variables)   //print with a new line.


function(methods)
every function is a type.
if no return no -> and it return a Void type.
tuple type can be used to return two values ->(a:Type, b:Type)  and retrieve by dot format
let bounds = minMax(array: [4, -4, 1, 88, 7, 42])
print("min is \(bounds.min) and max is \(bounds.max)")
// prints "min is -4 and max is 88"

func functionName(paraName: Type) ->returnType{
//use empty bracket if no para or comma between two or more para.
statement
return returnName
}



func someFunc(externalName localName: Int) {
    //use localName here
}
external is the name outside, local name is used inside.


functionName(argumentLabel paraName: value)
argumentLabel is used when call the function with parameters like functionName(argument: 123)
paraName is used inside the function block
uses _ to explicit remove the argument label so you can call function without using it
like functionName(123)


Function has types like (Int, Int) -> Int or () -> Void
Function with same types can be reassigned accordingly.
var aNewFunction: (Int, Int) -> Int = addInts

Function type can be used as other function’s parameters type or return type
Or nested

func chooseFunc(flag: Bool) -> (Int) -> Int {           //(Int) -> Int here is a function type
   func plus(input: Int) -> Int { return input + 1 }
   func minus(input: Int) -> Int { return input - 1 }
   if(flag) {
     return plus
   }
   else {
     return minus
   }
}

Function calls itself is recursion

func factorial(n: Int) -> Int {
  return n == 0 ? 1 : n * factorial(n: n-1)
}
print(factorial(n: 5)) //prints 120

Function default value
func someFunction(p1: Int = 12) {
   // the default value of p1 is 12
}
someFunction(p1: 6) // p1 is 6
someFunction() // p1 is 12
Place parameters with default values at the end of a function's parameter list.

Variadic Parameters
Function take 0...more parameters of the same type as an array. One variadic parameter is allowed per function.
func arithmeticMean(numbers: Double...) -> Double {
   var total: Double = 0
   for number in numbers {
     total += number
   }
   return (total / Double(numbers.count))
}
Placed after parameters with default value in the parameters list.

Function parameters are constants by default.
inout parameters are used if changes are needed
func swapInts(a: inout  Int, b: inout  Int) {
   let tempA = a
   a = b
   b = tempA
}
//when you call the function
var someInt = 3
var anotherInt = 107
swapInts(a: &someInt, b: &anotherInt)
Inout cannot has default value or be as a variadic


Closure
A Closure is a self-contained block of functionality that can be passed around and used in your code.

general form:

{ (parameters) -> return type in
   statements
}

can use constant parameters, variable parameters, variadic and inout parameters, but no default values.

Inline Closures (like lambda in python)

let names = ["Cc", "Aa", "Ee", "Bb", "Dd"]
var reversed = names.sorted(by: { (s1: String, s2: String) -> Bool in
   return s1 > s2
})

Or (for short)

reversed = names.sorted(by: { s1, s2 in return s1 > s2 } )

Or if closure is a single statement it must return so, for short:

reversed = names.sorted(by: { s1, s2 in s1 > s2 } )

Or shorthand argument names $0,$1,$2
reversed = names.sorted(by: { $0 > $1 } )

Or use Operator Functions like <, for string

reversed = names.sorted(by: >)



Class
Swift uses the word instance instead of object.

Class and Structures’s implementation and interface are created in a single file
When a new class or structure is defined, a brand new Swift type is defined.
Keyword struct or class
struct Resolution {
   var width = 0
   var height = 0
}

class VideoMode {
   var resolution = Resolution()//create a new instance
   var interlaced = false
   var frameRate = 0.0
}
This is a class contains a new structure instance.

Class has the same initializer syntax.
var name = Classname()

. is used to access instance’ content.

Structures have memberwise initializer
It is used to set initial values.

let vga = resolution(name1: 640, name2: 480)

Structures are Value Types(like primitive type in Java, value is copied no assigned to a mutual reference)
Class is reference type.
Constant class can change its value. It is only the reference that’s constant.
=== is used to check if two have same reference.
Swift's String, Array, and Dictionary types are implemented as structures.

Stored property is a constant or variable that is stored as part of an instance.

class DataManager {
   lazy var importer = DataImporter()
   var data = [String]()
}
Computed property (getter setter)

struct Point {
   var x = 0.0, y = 0.0
}
struct Shape {
   var origin = Point()   
   var center: Point {
     get {
       return Point(x: origin.x/2 , y: origin.y/2)
     }
     set(newCenter) {
       origin.x = newCenter.x/2
       origin.y = newCenter.y/2
     }
   }
}

Or if setter don’t define var name newValue is used.
struct Point {
   var x = 0.0, y = 0.0
}
struct Shape {
   var origin = Point()   
   var center: Point {
     get {
      return Point(x: origin.x/2, y: origin.y/2)
     }
     set {
      origin.x = newValue.x/2
      origin.y = newValue.y/2
     }
  }
}

Property observer
Not work with lazy variables

willSet is called just before the value is stored.
- didSet is called immediately after the new value is stored.

Auto name newValue is no name in willSet
oldValue for didSet.

class StepCounter {
 var totalSteps: Int = 0 {
   willSet(newSteps) {
     print("About to set totalSteps to \(newSteps)")
   }
   didSet {
     if totalSteps > oldValue  {
       print("Added \(totalSteps - oldValue) steps")
     }
   }
 }
}
let stepCounter = StepCounter()
stepCounter.totalSteps = 50
// About to set totalSteps to 50
// Added 50 steps
stepCounter.totalSteps = 150
// About to set totalSteps to 150
// Added 100 steps
stepCounter.totalSteps = 420
// About to set totalSteps to 420
// Added 270 steps

Type property
Static is used and it belongs to a type(like class) and access through Classname.name
It must have a default value

Methods are functions that are associated with a particular type.
It use self like this in other languages
func increment() {
   self.count+=1
}

The mutating keyword is added to the method's definition so it can modify property(var or let) of a structures and enumeration type.
struct Point {
   var x = 0.0, y = 0.0
   mutating func moveByX(dX: Double, dY: Double) {
     x += dX
     y += dY
   }
}
Static method the self refer the type(class)




Subscript
subscripts, which are shortcuts for accessing the member elements of a collection, list, or sequence.

struct TimesTable {
   let multiplier: Int
   subscript(index: Int) -> Int {
      return multiplier * index
   }
}
let threeTimesTable = TimesTable(multiplier: 3)
print(threeTimesTable[5])
// prints "15"

Many subscript can be made with different parameters to overload.

struct Matrix {
  let rows: Int, columns: Int
  var grid: [Double]
  init(rows: Int, columns: Int) {
     self.rows = rows
     self.columns = columns
     grid = Array(repeating: 0.0, count: rows * columns)
  }
  subscript(row: Int, column: Int) -> Double {
     get {
        return grid[(row * columns) + column]
     }
     set {
        grid[(row * columns) + column] = newValue
     }
  }
}

var matrix = Matrix(rows: 2, columns: 2)

matrix[0, 1] = 1.5
matrix[1, 0] = 3.2

in a function definition use:
guard booleanX else {
	//additional operation here
	return  	
//ignore this block if the booleanX is true, run code in this block if the boolean is false. one return here if no action needed
}


Inheritance
Only class can
Any class that does not inherit from another class is known as a base class.
The inheriting class is a subclass.
the class from which it inherits from is its superclass.

class Subclass: Superclass {

}

Subclass can have subclass with all property inhered from both parent and grand parent classes accessed directly after "."

Subclass can override any property it inherited. New Definition start with keyword override.
The superclass version of a method, property, or subscript is accessed by using the super prefix.
super.method() for methods
super[someIndex] for subscripts
Prevent overriding by marking it as final (such as final var, final func, final class func, and final subscript even final class).

Classes and structures must set all of their stored properties to an appropriate initial value prior to creation of an instance.

Initializer
Initializer is like a constructor that sets type values
struct Fahrenheit {
   var temp: Double
   init() {
     temp = 32.0
   }
}
var f = Fahrenheit()

It can has different initializer within same class depends on the var name
Init can also be overridden.

self means the class or struct itself.

convenience init(){
	self.init(x:1.0,y:2.0)
}//this is used to override the default init for empty new object.
//it is called in the following manner.
ClassName()


struct Celsius {
  var tempInCelsius: Double
  init(fromFahrenheit fahrenheit: Double) {
    tempInCelsius = (fahrenheit - 32.0) / 1.8
  }
  init(fromKelvin kelvin: Double) {
    tempInCelsius = kelvin - 273.15
  }
}
let boilingPoint = Celsius(fromFahrenheit: 212.0)
let freezingPoint = Celsius(fromKelvin: 273.15)

There is a default memberwise initializer

For structure
struct Size {
  var width = 0.0, height = 0.0
}
let twoByTwo = Size(width: 2.0, height: 2.0)

For class
class Size {
  var width:Double, height:Double
  init(w:Double, h:Double) {
    width = w
    height = h
  }
}
let twoByTwo = Size(w: 2.0, h: 2.0)

Write the required modifier before the definition of a class initializer to indicate that every subclass of the class must implement that initializer:

class SomeClass {
   required init() {
     // initializer implementation goes here
   }
}

You must also insert the required modifier before every subclass init

A deinitializer is called immediately before a class instance is deallocated.
Class only
Auto called before instance deallocation, or for superclass after subclass deinit
Superclass inherits the deinit from subclass, and auto called all the time.
deinit {
   // perform the deinitialization
}
It is used to save resource.




@Class before method declaration is used to expose the method to a certain class.



Exception
do {
	try …
} catch {
	print(error)
}

Basic Class method
String()
print()
stringname.isEmpty        return Bool true if empty.
name.hasPrefix("abc")    return Bool
name.hasSuffix("abc")    return Bool
stringname.uppercased()      convert whole sentence into uppercase.
stringname.lowercased()
stringname.count                  return the number of characters in Int.

array
name.count        return number of elements
name.isEmpty      return Bool true if array length is 0.
arrayname.append(newitem)        add new element at the end of this array.
arrayname.count                           return array length in int
arrayname.last		       return the last element
arrayname.lastIndex		       return the index of the last element
name.insert(item, at: index)
name.remove(at:index)                 return the item
name.removeLast()
name.removeAtIndex()
name.enumerated()
for (index,value) in shoppingList.enumerated(){
	print("Item \(index+1): \(value)")

set
count
isEmpty
name.insert(item)
name.remove(item)          return item or nil if item not found
name.removeAll()
name.contains(item)             return Bool if contain
 ==   for equal
a.intersection(b)
a.symmetricDifference(b)
a.union(b)
a.subtract(b)
isSubset()
isSuperset()
isStrictSubset()
isStrictSuperset()
isDisjoint()

sorted iteration
for name in name.sorted(){
}

Dictionary
count and isEmpty
name.updateValue(newkey,forKey:oldkey)         update key value   returns the old kay value  or nil if not found
name.removeValue(forKey:key)  		return oldvalue or nil if not found
