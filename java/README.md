# Java

## Introduction:

- Java is a high level, modern programming language designed in 1990s by Sun Microsystems, and currently owned by Oracle.
- javac is the complier executable that is used compile .java(source code) file into .class(byte code) file.
- java executable is used to run complied byte code. It creates an instance of a Java Virtual Machine(JVM) with an area in the node’s memory.
- Java Runtime Environment (JRE) contains java executable.
- Java Development Kit (JDK) contains java and javac.
- Standard Edition(SE) is the regular JDK for developing applications.
- Enterprise Edition(EE) contains SE plus the application server and more.
- A redistributable package is used to deploy applications.
- `*.jar` is for Java Application.
- `*.war` is for Java Web Application.
- Java guarantees "Write Once, Run Anywhere."
- All programs in Java is object-oriented.

## Setup

- run `/usr/libexec/java_home -V` to see the location of java
- run `/usr/libexec/java_home -v11` to see the location of a specific java version installed in the system
- run `export JAVA_HOME=<JAVA_LIB_LOCATION>` assign the Java location to the envirionment variable to let the system work on a specific Java version,
  - change and reload the dot file for a permanent change
- The system Java wrappers can't find the Java library if it is not installed inside the system default folder, create a symbolic link into the `JavaVirtualMachines` so the `java_home` command can find it
- To complete remove java, run the following command after removing the content inside the Java home folder
  - `sudo rm -rf "/Library/Internet Plug-Ins/JavaAppletPlugin.plugin"`
  - `sudo rm -rf "/Library/PreferencePanes/JavaControlPanel.prefPane"`
  - `sudo rm -rf "~/Library/Application Support/Java"`

## IDE

There are many great IDE for Java.

- NetBeans:
  - Auto indentation with ALT+SHIFT+F.
- Eclipse

## Basic Syntax:

- Every statement ends with `;`.
- Every block is surrounded by curly braces.

### Comments

```java
// single-line comment to the end of the line.
/* Thie is a multi-line comment or
    a block comment.
*/
/** This is a java doc style comment.
*/
```

- Documentation comments can become external documentation in HTML format using Javadoc
  for doc comments any asterisks beyond two will be ignored.
- Requirement:
  - Every class has descriptions with `@author` tag
  - Every method has description start with `@param variablesName` and `@return` tags
  - Main method uses `@param args` unused
  - Every variable needs an `/** **/` block of explanation.
  - Section of codes should be marked with //comments on empty lines.
  - // explaining local variables.
- JavaDoc HTML page is formatted. comments will be made by tools inside IDE.

## Variables

- In Java, there are 8 primitive types and reference types(object).
- Primitive types represent single values with no attributes and methods.
- Primitive types has a table for memory sizes.
- `_` can be added to int for readability.
- boolean has values `true` or `false`.
  - default value that initialized without value is false.
- auto type casting from int to double only.
- final is the keyword used for assign constant, and the name is always all_caps, all_caps is also shown in UML.
- final can also be used on method(final method cant be overridden) and class(final classes don’t have subclasses)
- other are referred as reference type.
- They use function to make conversion. (Interger.toString(intx))
- They use function to test equality(no == sign) (a.equals(b) for Strings)
- null? relation to reference type with no memory reference. 0 for some float initialization default when they are not assigned with any number.

### Type casting

- type casting(conversion) put type name in front of the expression within a bracket.
  (int)x;
- int / int is int
- Java supports automatic type casting of integers to floating points,
- For class upcasting is to instantiate a subclass object as a superclass object. It is done automatically. `Animal a = new Cat();`
- The other way around is called down-casting. It is done manually.
  ```java
  Animal a = new Animal();
  ((Cat)a).makeSound();
  ```
- reference types stores a reference(their value is just a reference) to the memory location. It includes arrays, strings and all objects.

### Scope of Variables

- Java has block level scope:
- All variables are local to the block in which they are declared, and even for blocks inside that block.
- If the variables need to be used outside the block, They are required to be initialized outside of the block with an assigned value.
- If the variables need to be used inside another block, the value should be initialized and assign an actual value.

## Operators

### Condition

- `<,>,!=,==,<=,>=`

### Membership

- `x instanceof ClassName`
- this gives true if x is a instance of ClassName

### logical operators

- && and
- || or
- ! not
- the operands must be compatible.

### Ternary operators

- result = testCondition ? value1 : value2
- If testCondition is true, assign the value of value1 to result; otherwise, assign the value of value2 to result."

### Assignment

```java
int y;
String name = "";
int a = 42, b = 11;
```

- in Java the variable name is associate with one type.
- Variable names start with lower case letter.
  `x +=y -> x = x +y`

### Math Operators

- `+, -, *, /`
- long division happens between integer operand
- operand need to be in the same type.
- `%` modulo(remainder)

### Short Forms

- `x=x+1 -> ++x`
- `x=x-1 -> —x`
- `++x` vs `x++`
  - for both prefix and postfix form x=x+1.
  - for the whole expression, ++x use the value x+1, x++ uses the value x.

## Conditional Structures

### if Condition

- if
  ```java
  if(condition) {
  }
  ```
- either a {…} block or a single statement line can be used after the (…) part. However, {…} is always recommended.
- if…else
  ```java
  if(condition){
  } else{
  }
  ```
- It can be nested.

- else if statement

```java
if(condition) {
} else if(condition) {
} else if(condition) {
} else {
}
```

- switch statement

```java
switch (expression) {
   case value1 :  //test if the value equals to the expression
   //statements
   break; //optional jump to the end
   case value2 :
   //statements
   break; //optional
   default: //Optional run if no case matches.
   //Statements
}
```

### Loop

- control statements
  - break; stop the loop.
  - continue; skip to the next loop.
- while loop

```java
while(condition) {
	//statements;
}
```

- do…while loops

```java
do {
} while(condition);
```

- This makes sure the loop run at least once, inside the do block.
- Be careful about the different scope for codes after while and after do
- for loop

```java
for (initialization; condition; increment/decrement) {
  statements;
}
for(int x = 1; x<=5; x++){
}
for(int a = 1 , int b = 4; a<b ; a++, a—){
  //not recommend not detail enough
}
```

- enhanced for loop
- the loop declares new temperate variable i and assign the values of the newArray to i on each iteration.

```java
for(int i: newArray){
}
//or
for(int x=0; x<arrayInt.length; x++){
    int i;
    i=arrayInt[x];
    // ……….
  }
```

- Because i is an independent temperate value.the value of a primitive type(and Strings because it’s immutable(the object cannot be changed after initialization))array can’t be change using i variable in the for loop, only the methods(setter) for an array of an objects can be used to change the object values. and assignment for public variable of an object array will work.(the assignment trace the memory location of the object through i, and change the actual value inside the object.)
- For loops, variables should all have a value before it goes in the loop block, or it may have not to get the chance to contain any value.

## Classes and Methods

### Classes

- Every code in Java must be inside a class. class name usually start with capital letter.
- class name capitalized, and must match file name.
- In Java, all statements (except variable declarations) must be inside a method, and all methods must be inside a class.
- One class per file.
- Class is a blueprint for creating a type of object.
- Each class is used to define attributes and behavior.
- Class Access Modifier is used to set the level of access
  - `public`: The class is accessible by any other class.
  - default(empty): The class is accessible only by classes in the same package.
- The "." operator "dereferences" the variable to get to the current object, with format objectName.instanceVariableorMethod
- As a reference type, for object `c`, `System.out.println(c);` will show the memory address.
- Objects with no active reference are automatically disposed of by Java’s "Garbage Collection" mechanism.
- Usually all instances variables private and most instance methods public.
- Accessor(get) method are a standard way to access a private instance variable
- Mutator(set) method are a standard way to set a private instance variable
- In other words, an object is an instance of a class.

#### Inheritance

- Inheritance is the process that one class can acquire the properties of another by being its subclass(derived class, or child class)(all public and protected methods and variables.).
- The class that are inherited is the superclass(base class, or parent class)
- Java class can only inherit one class.
- The extends keyword is used to create a subclass.
- all class is inherited from object class by default.

```java
class Subclass extends Superclass {
}
```

- subclass has all superclass’s non-private variables and methods.
- Constructors won’t inherit from parent class. However, all parent class default
- constructors(if no super method to ask a specific constructor of its parent.) will be call upon subclass instantiation at first from grandparent to parent.
- By rules, constructor only handles its class’s own variables.
- `super.methodorvariable` is used to access contents from superclass.(refer to the closet applicable class’s method)
- equals method in object class is the same as ==, by default. to auto create an equals method override for semantical comparison right click on the class file Go to source -> Generate hashCode() and equals()
- super() can be used in constructor in the first line.(refers exactly its parent’s constructor)

#### Override

- subclass can redefine a specific method that its parent class has, this is called overriding(runtime polymorphism).
- `@override` tag is optional for readability.
- has same name return type and arguments
- overriding method can not have less access control(public->private).
- methods with static and final can not be overridden.
- constructor can not be overridden.
- if a method can not be inherited, it cannot be overridden.

#### Method Overloading

- also called compile-time polymorphism
- methods with same functionality, but take different(must) types of variable.
- auto casting always happens right away form int to double during overloading in parameter.
- one method, with different implementations.
- polymorphism(method executed differently, based on the type of objects that calls it)

#### Object Polymorphism

- when initialize new object, the type declare earlier is the declare type. the type follow `new` keyword is the actual type. actual type could be a subclass of the declare type.
- the new class has all direct access of class methods and field in declared type.
- to get actual type property access use (type) casting.
- Some times a parent class type is used to represent all the subclass object type, casting is made case be case, making the program or manageable.

Code

```java
class Shape {
  public void whatShape() {
    System.out.println("AnyShape");
  }
}
class Circle extends Shape {
  public void whatShape() {
    System.out.println("Circle");
  }
}
class Square extends Shape {
  public void whatShape() {
    System.out.println("Square");
  }
}
public static void main(String[ ] args) {
  Shape a = new Circle();
  Shape b = new Square();
/***create reference type Shape using subclass’s objects.***important here***/
//declared type is Shape, actual type is Circle or Square
}
a.whatShape();
//Outputs "Circle"

b.whatShape();
//Outputs "Square"
```

- When both actual type and the declared type have a same method. the method in belongs to actual type is called.
- boolean operator `instanceof` works with polymorphism.
- For unknowns object type parameters, `instanceof` is used to check type and new object need to be created and casted with target type for further manipulation.

#### Abstraction

- Abstraction is a way of focusing on the essential qualities rather than specific characteristics.
- It is done by abstract class and interfaces.
- It is a superclass that summarize common features of its subclasses.
- using keyword abstract at the beginning.
- cannot be used to create objects.
- must have subclasses to use it.
- abstract class and methods are denoted in UML in italics font.
- method can also be abstract with only headline end with ;
- abstract method use keyword abstract and also shown in italics font.
- It it mandatory for subclass to implement abstract method.
- Any class with abstract method should be defined as abstract classes.
- An abstract method use abstract keyword and has no {}, it ended with ;

```java
public abstract class ClassName{
	public abstract void methodName();
}
```

#### Interface

- An interface is a completely abstract class that contains only abstract methods.
- Some specifications for interfaces:
  - Defined using the interface keyword instead of class.
  - May contain only static public final variables with a given value.
  - Cannot contain a constructor because interfaces cannot be instantiated.
  - Interfaces can extend many other interfaces.
  - A class can implement any number of interfaces(seperated by comma). But only inherited one superclass.
  - Methods in an interface are implicitly public and abstract, so no abstract keyword is needed.
- Keyword `implements` is used to implement interfaces.
- public class ABC extends A inplements B,C,D{…} //extends goes before implements.
- When you implement an interface, you need to override all of its methods.

  ```java
  interface Animal {
    public void eat();
    public void makeSound();
  }

  class Cat implements Animal {
    public void makeSound() {
      System.out.println("Meow");
    }
    public void eat() {
      System.out.println("omnomnom");
    }
  }
  ```

#### Comparable Interface

- This interface is implemented by classes that need to compare their objects according to some natural (internal) order.
- Then comparsion can be used by the compareTo() method.

```java
class Employee implements Comparable<Employee>
{
   private int rank;
   private String name;
   public int compareTo(Employee e)
   {
       return this.rank - e.rank;
   }
   public Employee(String n, int r)
   {
       rank = r;
       name = n;
   }
   public String toString()
   {
       return name + " : " + rank;
   }
}
public class Test
{
   public static void main(String [ ] args)
    {
        Employee bigShot = new Employee("Joe Manager", 10);
        Employee littleShot = new Employee("Homer Simpson", 1);
        if (bigShot.compareTo(littleShot) > 0)
        {
            System.out.println(bigShot);
            System.out.println(littleShot);
        }
        else
        {
            System.out.println(littleShot);
            System.out.println(bigShot);
        }
    }
}
```

#### Anonymous classes

- Anonymous classes are used to override other class method in the main method in braces follow the constructor.
- This modification is done on the object but not the classes.
  ```java
  class Machine {
    public void start() {
      System.out.println("Starting...");
    }
  }
  public static void main(String[ ] args) {
    Machine m = new Machine() {
      @Override public void start() {
        System.out.println("Wooooo");
      }
    };
    m.start();
  }
  //Outputs "Wooooo";
  ```

#### Inner class

- a class that is within a class.
- inner class can be private, outside classes won’t be able to access private inner class.
  ```java
  public class Example {
  	public Example(){
  		Inner x = new Inner();
  	}
  	private class Inner {
  		//some code
  	}
  }
  ```

### Methods

- Methods define behavior.
- it can be nested and it is very useful, when u call a nested method u can run also run method inside of it.
- access modifier for attributes and methods:
  - default: It is available to any other class in the same package.
  - public: Accessible from any other class.
  - protected: Within the same package plus subclasses access.
  - private: Accessible only within the declared class itself.

#### Static Methods

- `static` keyword is used for static variables and methods, otherwise, they are called instance variables and instance methods.
- it states the attributes and methods belong to the class and share by all objects under the class.
- Instance variables belong to the object. no object, no instance variables.
- static method and variables are created at compile time.
- When outside the class, always access static variables and methods using the class name, not an object variable.
- static method has access on only static variables. Unless initialize new variables inside static methods.

```java
public static void main(String[] args) {
}
```

- the main method takes an array of string as its parameters, and does not return a value.
- `The currentObject.toString()` get call every time the object get to print or concatenated. By default, toString print the memory’s hashcode values. However, it is often define specifically to print its formatted variable values.(overriding)

```java
class MyClass {
  // declared Method sayHello
  static void sayHello() {
    System.out.println("Hello World!");
  }
  public static void main(String[ ] args) {
    sayHello();
  }
}
class MyClass {
  static void sayHello(String name) {
    System.out.println("Hello " + name);
  }
  public static void main(String[ ] args) {
    sayHello("David");
    sayHello("Amy");
  }
}
// Method with a parameter
class MyClass {
static int sum(int val1, int val2) {
  return val1 + val2;
}
  public static void main(String[ ] args) {
    int x = sum(2, 5);
    System.out.println(x);
  }
}
// Method returns values
public class Animal {
  int legs;  //attributes
  void bark() {
    System.out.println("Woof-Woof");
  }//methods
}// This create new class for generating Animal object
class MyClass {
  public static void main(String[ ] args) {
    Animal dog = new Animal();
    dog.legs=4;
    dog.bark();
  }
}
// This create object, assign attributes and call its method
//when methods are declared with no static keywords, new instance of the object must be declared, in order to use this method.
```

#### Getter and Setter

- For each variable, the get method returns its value, while the set method sets the value.
- Getters start with get, followed by the variable name, with the first letter of the variable name capitalized.
- Setters start with set, followed by the variable name, with the first letter of the variable name capitalized. (a boolean type return is recommended for a better implementation.)

```java
public class Vehicle {
  private String color;
  // Getter
  public String getColor() {
    return color;
  }
 // Setter
  public void setColor(String c) {
    this.color = c;
    //data validation can be done here.
  }
}
```

- The getter method returns the value of the attribute.
- The setter method takes a parameter and assigns it to the attribute.
- The keyword this is used to refer to the current object. Basically, this.color is the color attribute of the current object.
- Sometimes methodName(class other) -> other.variable refers to the object’s variable that input from the parameters, different from this.variables
- other can be replaced by other words like that
- Then it can be used in main to manipulate private variables.

```java
public static void main(String[ ] args) {
  Vehicle v1 = new Vehicle();
  v1.setColor("Red");
  System.out.println(v1.getColor());
}
```

#### Constructor

- Constructor is used to set a default value for instance variable when creating new objects. It is called when new object is initialized using new keyword, it can have parameters, entered after new in the brackets. It can also be used with setter.
- A constructor name must be same as its class name.(same capital letter)
- A constructor must have no explicit return type
- A constructor is not responsible to create variable, it only assign value for created variable under the class declaration line.
- There is also a default constructor in all java classes, it is empty inside bracket. It only initialize the instant variable initialization part(the first few lines for variables before the first method.)
- a private constructor can be created and called using a static create() method, this create method is also called static factory methods.

```java
public class Vehicle {
  private String color;
  Vehicle() {
    this.setColor("Red");
  }
}
 //it is overloaded with different parameters.
  Vehicle(String c) {
    this.setColor(c);
  }
  // Setter
  public void setColor(String c) {
    this.color = c;
  }
}
//color will be "Red"
Vehicle v1 = new Vehicle();
//color will be "Green"
Vehicle v2 = new Vehicle("Green");
```

- `this()` can be used in the first line inside a constructor to save codes. It must be the first line of the constructor.

```java
public Circle6() {
this(10.0, 100.0, 100.0);
}
public Circle6(double radius) {
this(radius, 100.0, 100.0);
}
public Circle6(double x, double y) {
this(10.0, x, y);
}
public Circle6(double radius,
double x, double y) {
this.radius = radius;
this.x = x;
this.y = y;
}
```

#### Association

- Directed association(one-way association): It is basically object from other class is inside this class. The class has reference to the object.
- class.object.method() is used for object access.
- Privacy leak happens when a private variable or method’s value in the memory is accessed from a public place.
- It happens mostly when assign a reference type to a new name.
- duplicate the referenced value is a good way to avoid it.

#### Lambda

```java
name = (parameter) -> statement or {} block;       //-> read as become
```

#### Main Method

- Every Java program starts from the main method.
- Main method is identical in each program.
- It is the view for the user(interface) and class is the model(implementation that never get input or output for the users).
- In the main method declarations:
  - public or private: the accessibility of the code block.
  - static: method can run without creating an instance of the class containing the main method.
  - void: method doesn't return any value.
  - main: the name of the method.
  - String[] args is the parameter for the main method.
  - void test() // it is a test method with no returning value and no parameters.

### Generic Class

- A generic class is one whose definition uses a placeholder for one or more of the type arguments that are passed as parameters.
- The type is denoted as a capitalized variable. Ex `T`.
  - `T` Used for a generic type.
  - `S` Used for a generic type (usually for the second type if used)
  - `E` Used to represent generic type of an element in a collection.
  - `K` Used to represent generic type of a key for a collection that maintains key/value pairs.
  - `V` Used to represent generic type of a value for collection that maintains key/value pairs.

```java
class Point<T>     // T represents a type parameter
{
  private T x, y;
  public Point(T x, T y)           //  Constructor
  {
    set(x, y);
  }
  public void set(T x, T y)
  {
    this.x = x;   this.y = y;
  }
  T getX(){ return x;}
  T getY(){ return y;}
  public String toString()
  {
    return "("+x.toString() +","+ y.toString() + ")";
  }
}
//during instantiation
public class Test
{
  public static void main(String [] s)
  {
    Point<String> strPoint = new Point<String>("Anna", "Banana");
    System.out.println(strPoint);
    Point<Double> pie = new Point<Double>(3.14, 2.71);
    System.out.println(pie);
  }
}
//Program Output:
//(Anna,Banana)
//(3.14,2.71)
```

- Autoboxing is the automatic conversion of a primitive type to the corresponding wrapper type when it is used in a context where a reference type is required.
- Unboxing is the automatic unwrapping of a wrapper type to give the corresponding primitive type when the wrapper type is used in a context that requires a primitive type.

```java
// Unboxing converts Integer to int
int i = new Integer(34);
// AutoBoxing converts doubles 3.14, 2.71 to Double
Point<Double> p = new Point<Double>(3.14, 2.71);
// p.getX() returns Double which is unboxed to double
double pi = p.getX();
```

- The wildcard type symbol `?` stands for any generic type. `Point<?>` references will accept a `Point<T>` object for any type T.
  - T will require casting when using wild card without constrain.
  ```java
  static double sqLength(Point<?> p)
  {
    // Needs cast to Number
    Number n1 = (Number)p.getX();
    Number n2 = (Number)p.getY();
    double x = n1.doubleValue();
    double y = n2.doubleValue();
    return x*x + y*y;
  }
  ```
  - `Point <? extends Number> p2;` Constrained wild card `p2` can accept a `Point<T>` object, where T is any type that extends Number
  - In class definition `class Point<T extends Number>` constrains to a subclass of Number.
  - A type parameter can be constrained to a type implementing an interface
  ```java
  public static <T extends Comparable<T>>
  T greatest(T arg1, T arg2)
  {
    if (arg1.compareTo(arg2) > 0)
    return arg1;
    else
    return arg2;
  }
  public static void main(String [ ] args)
  {
    Employee bigShot = new Employee("Joe Manager", 10);
    Employee littleShot = new Employee("Homer Simpson", 1);
    Employee great = greatest(bigShot, littleShot);
    System.out.println(great);
  }
  ```
- Interfaces, like classes, can be generic.

#### Generic Methods

- Generic methods are declared as follows

```java
public static <T> void methodName(ClassName<T> t){
}
```

- The `<T>` is the generic type the method is taking as a parameter.
- Generic methods are called in the following way.

```java
<TypeName>methodName(t);
```

## Exception Handling

- There are three types of error
  1. Syntax Error:Error that prevents compilation. (caused by some checked exception)
  2. Run-time Error:Program compiles, but execution halts unexpectedly.(caused by some unchecked exception)
  3. Logic Error:Program compiles and runs to completion, but does something unexpected or wrong due to bad logic in the code.
- All exceptions are objects, they are a hierarchy relationship. the exception type Exception is at the top of the hierarchy and it represents all exception.
- Custom exception class can be made by extends an Exception class(RuntimeException class) with your now defined parameters. custom methods for the exception can be added inside. A thrower class can be used to take argument and judge exception condition and throw exception object. exception handling clan then be made in main with new thrower object.
- A try/catch blocks is used to attempt the execution of some code in the try block, if there is an exception. The corresponding catch block for the specific exception will be executed and the exception object will be passed into the block.
- When there is an error, an exception is thrown to outside of the method. or throw keyword can be used to manually generate a specific exception in a method. Then the program continues to run codes that follows try/catch. When it is not handled, the program stops.
- Exceptions have two types: checked, unchecked. Checked exceptions are checked before compiled and will not run if not handle like InterruptedException for Thread. Unchecked are checked at run time(extends RuntimeException).

### try/catch block

```java
try {
	//some lines of code
} catch (ExceptionTypeA e) {
	//code for exception type A
} catch (Exception e) {
			// get general exception.
}
```

### throw exception

```java
void methodName() throws ExceptionType {
	throw new ExceptionType("some message");
	//or
	ExceptionType e = new ExceptionType("error message");
	throw e;

}
```

### Methods

- get stack trace info `e.printStackTrace();`
- get error message `e.getMessage()`
- specifying checked exception to avoid Syntax error before compile.

```java
public static void main (String[] args) throws CheckedExceptionType{
…
}
```

- create ones own exception types

```java
public class ExampleException extends RuntimeException {
	public ExampleException() {
		super("set message here");
	}
}
```

- create exception thrower

```java
public class ExampleThrower {
	public ExampleThrower(int x) {
		if (x<0) {
			throw new OutOfRangeException();
		}
	}
}
```

- main testing class exception handling

```java
ExampleThrower x;
try{
	ExampleThrower = new ExampleThrower(-5);
} catch (ExampleException e) {
	System.out.println(e.getMessage());
}
```

- finally block always run.
- one try block can have many catch block, the exceptions for those catch block should be arranged from the most specific one to the most general one, since they are checked from top to bottom.
- whenever there is an exception in the try block, the try block stops running. When the catch block finishes, the code in try block will continue.
- Throws keyword defines the exception that can be thrown in this method. More exception types can be defined after throws in the method definition line, separate them with comma.
  For InputMismatchException, scannerName.next() is often used in the catch block to clear the wrong user input stored in the buffer.
- IllegalArgumentException is the exception for wrong argument input for a method.
  For custom exception super() in constructor is for getMessage().

## Packages

- API are packages that is written and ready to be used. see [Oracle website](https://docs.oracle.com/javase/8/docs/api/) for Java SE 8 API references.
- packages are often used as a folder for classes and sub-packages.
- packages folders are under the src folders.
- java files for classes will have a first line indicates which package it belongs.
- in order for other package to use a class which is outside the package: `import packageName.classNAME`; or `import packageName.*;` is needed.
- All functions in Java exists within a class object, some of them are built in and does not need to import, many others does.

### System class

- `System.currentTimeMillis();`
- `System.current.nanoTime();` current time in ns.
- `System.nanoTime()` measures difference in nano second by substract values from two of these method. It does not return real time value.

### Random Class

- `java.util.Random;`
- `Random name = new Random();`
- `name.nextInt(x);` generate int from 0 to `x-1`
- `name.nextDouble(x);` generate double from 0 to `x-1`
- `name.nextBoolean(x);`

### Math class

it contains all static methods, so can be called without creating math objects.

- `Math.pow(base,exp);` returns a double
- `Math.round()` round to nearest int
- `Math.abs()` find abs for all number type
- `Math.max()` return the largest among its parameters.
- `Math.min()` return the smallest among its parameters.
- `Math.ceil()` return the next int value as a double.
- `Math.floor()` return the int value as a double
- `Math.pow(x,y)` power of x to the power of y as a double.
- `Math.random();` random number from 0 to 1.
- `Math.sqrt()`
- `Math,sin()`
- `Math.cos()`

### Scanner Class

- It is used to get User input or read files.

```java
import java.util.Scanner;  //import the Scanner class
Scanner myVar = new Scanner(System.in);  //Create a Scanner object(instance of this class).
```

- run the following scanner methods for different data types.

```java
nextByte() //Read a byte
nextShort() //Read a short
nextInt() //Read an int
nextLong() //Read a long
nextFloat() //Read a float
nextDouble() //Read a double
nextBoolean() //Read a boolean
nextLine() //Read a complete line
next() //Read a word
hasNext() //Return bool, work with while loop as its condition.
//Example:
System.out.println(myVar.nextLine());  //get user input
```

- sometimes scanner can cause error if the lines is mismatched.

### Interger

- `Interger.toString(intx)`
- `Interger.parseInt(String)` string to Int

### Double

- `Double.parseDouble(String)`string to double
- `Integer.MAX_VALUE` A constant holding the maximum value an int can have, 2^31-1.
- `Integer.MIN_VALUE` A constant holding the minimum value an int can have, -2^31.

### String

- `stringx.valueOf(intx)`
- `stringx.trim()` remove the leading and trailing white space of the string.
- `stringx.startsWith(string)` return true is the stringx start with the method argument.
- `stringx.endsWith(string)`
- `string.indexOf("sam")` return index and -1 if not exist.
- `string.toUpperCase`
- `str.charAt(i)` return the character at position i.
- `str.substring(a, b)` only take string from charact with index `a` to `b - 1`.

### StringBuilder class

## Character

- `Character.getNumericValue(myString.charAt(0));` return ACSII value of a char in string to real integer value.

## Color

- `Color.web("colorName");`

### String Class

#### String Functions

- `System.out.println("");` println is the method. System is the class and out is the stream to access the println method. the method creates a new line at the end, print() does not.
- `printf()` //This is the formatting output method.
- `System.out.printf("%s(this is the formatting string) %f" , aString, aDouble);`
- `String.format()` can also be used to generate formatted string and save it into a variable.
- `printf()` is only good with System.out
- String is an object, a reference type.
- `+` concatenation (auto casting)
- no `*` operation for strings in Java

#### Formatting String:

- Format Specifier
  - `%f` Decimal number.
  - `%s` String or Object `toString()`.
  - `%d` Interger.
  - `%n` new line.
- Width
  - width.decimal(default 6 decimal place, precision can be used for %s %b %h as well)(decimal point is 1 space)
- alignment.
  - place `-` after `%` sign means left alignment. Ex: `%-6s`,"good" ->good\_ \_ (default right justified).
- divider
  - `,` use `,` to divide thousand, million position for a number.
- leading zero
  - `0` 0 will be used to fill the leading space. Ex: `%010d`.

### Enums

- enum is a special type used to define a group of constants
- It increases the performance of codes for some method only take a set of values. Often used for days of week, cards etc.

#### define Enum

```java
enum Sample {
	SAMPLEA,
	SAMPLEB,
	SAMPLEC
}
```

#### Access Enum

```java
Sample x = Sample.SAMPLEA;
```

#### Usage

```java
switch statement example:
switch(x){
	case SAMPLEA:
			//some code
			break;
	case SAMPLEB:
			//some code
			break;
	case SAMPLEC:
			//some code
			break;
}
```

## Array

- It is an object.
- Array name is just a reference of the array object.
- It is an ordered list of the same type of values
- It is fixed in length.
- index number starts at 0
- `import java.util.Arrays;`.

### Create an Array

- create array with fixed length.

```java
//The following statement declare new int array called newArray with 5 elements from [0] to [4]
int[] newArray;
newArray = new int[5];
//or
int[] newArray = new int[5];
```

- array literal

```java
//instantiating array for the first time.
String[] newWithValue = {"A","B","C","D"};
//at any time
String[] newWithValue;
newWithValue = new String[]{"A","B","C","D"};
```

- Create an array of objects

```java
Obj[] name;
name = new Obj[5];
//Initialize an object in array
name[0] = new Obj();
```

- after creating an array of objects, all objects have a default value null(or an array of nulls) with no value in memory. Before initialize each object in the array, be aware of null exceptions(error).
- Array is a good way to handle large amount of objects using array of objects

### Access an Array

```java
// This assign a value of 10 to the 3rd position of the array
newArray[2] = 10;
```

- `.` Can be used to access an object in the array: `array[0].method()`;

### Length

- `newArray.length` - returns the length of the array

### Multidimensional arrays

- Multidimensional arrays are nested arrays
- first index represents the row, the second index represents the column.
- Multidimensional array must also be in the same type.
- Java supports int[][][] and more.
- Nested loop works with multidimensional arrays.
- Ragged array is a 2D array with various row lengths. `int [][] arrayName = new int [4][];`

```java
int[][] sample = { {1,2},{3,4},{5,6} };
//access 2D array
int x = sample[0][1];  //x==2
//get the length of the first row.
int y = sample[0].length;
```

### Arrays class

- `Arrays.toString(arrayX);` //print out the array content
- `Arrays.copyOf(arrayX, lengthX);` //get the first lenthX element of arrayX
- `Arrays.equals(arrayX, arrayY);` //return if arrayX and arrayY are equal.

### Comparable interface

- `Arrays.sort`, `Arrays.binarySearch` works with comparable interface.
- comparable interface has an abstract `compareTo()` method, it compare the current object to the passed parameter return int.(negative when smaller, positive when bigger and zero if equal.)
- All arrays of strings have already implemented the comparable interface. can use Array. method directly.
  ```java
  compareTo (ClassName objectName) {
  }
  ```
- After implement the definition, the array of objects of MyClass can be sorted and searched using the methods above.
- Sort can be done with Lambda express, `collectionName.sort( (Object o1, Object o2) -> o1.getName().compareTo(o2.getName()));` or `collectionName.sort( (o1, o2) -> o1.getName().compareTo(o2.getName()));`
- For integer values, `collectionName.sort( (o1, o2) -> o1.getAge()-o2.getAge());`
- It can be done with Comparator `Comparator<Object> comparatorName = (Object o1, Object o2)->o1.getName().compareTo(o2.getName());`. then use `collectionName.sort(comparatorName)`.

## Collections

- The Java Collections Framework is a library of classes and interfaces for working with collections of objects.
- It has a List interface and a Set interface.
- The AbstractCollection class provides a skeleton implementation for a Collection class by implementing many of the methods of the Collection interface.
- Programmer defined data types (class objects) can fit into collection frameworks by supplying the following methods
  - `equals` – used by contains to find an instance of an object
  - `compareTo` – used by sorting methods to provide ordering within a collection.
  - `hashCode` – used to provide fast lookup in hashed based collections
  - `toString` – used to provide a String representation of the class – not strictly needed, but useful

### Collection Interface Methods

for all collections have static abstract methods:

- collectionsName.sort(collectionName)
- collectionsName.max(collectionName)
- collectionsName.min(collectionName)
- Collections.reverse(listName)
- Collections.shuffle(listName)
- collectionsName.add(element)
- collectionsName.clear()
- collectionsName.contains(element)
- collectionsName.isEmpty()
- collectionsName.remove(element) return true if successful.
- collectionsName.size()
- Collections.binarySearch(collectionName, element); for sorted collection in ascending order only, return the index of the element, return values <0 if not found
- Collections.binarySearch(collectionName, element, comparator); can use Lambda expression as a comparator. can be in ascending or descending order.

### List

- These are some special classes provided by Java API in java.util.ListType (import this before use).
- List is just like array which is also okay with insert and remove element. List is slower than array. ArrayList and LinkedList are some commonly used List type.
- ArrayList is a generic class. It need to associate to other classes to work. association is denoted by `< >`.
- ArrayList only accept objects as its element. For primitive types use its wrapper class. Once declared using wrapper, auto transformation can be done by autoboxing.
- List’s index start at 0.
- LinkedList can’t set size when initialize, it got all others syntax the same as ArrayList. It stores additional memory address about the neighbouring elements, make it suitable for large amount of insertion and deletion. ArrayList is faster for accessing data.
- `ArrayList<String>` is the type of the arraylist, Ex, `public void method(ArrayList<String> x){////}`
- Lists work well with enhanced for loop.

### new wrapper class

```java
Integer x = new integer(1);
//it can be printed as int 1.
```

### create arraylist object

```java
ArrayList x = new ArrayList();
```

- create arraylist for String with 10 entries.

```java
ArrayList<String> x = new ArrayList<String>(10);
```

- create arraylist based on an array.

```java
ArrayList<Integer> numbers = new ArrayList<>(Arrays.asList(10, 20, 30, 40, 30, 50, 10, 20, 30, 90));
```

### create linkedlist object

```java
LinkedList<Integer> x = new LinkedList<Integer>();
//LinkedList<Integer> is the complete type as an argument for a function.
```

### Access Elements

- set element

```java
set(int index, "something")      //might throw type error.
get(int index);
```

- remove element

```java
arrayListName.remove("something");
arrayListName.remove(int index);
//return true when successful.
```

### ArrayList Methods

- add a new object to the end of the ArrayList

```java
arrayListName.add("something");
arrayListName.add(int index, "something");
```

- return true if contain specific element. `arrayX.contains(Object s)`
- get first index of an item `indexOf("Something"); //-1 if not found,`
- get last index of an item `lastIndexOf("Something");`
- get the element on at specific index position `.get(int index)`
- return the length `.size()`
- remove all elements `.clear()`
- convert to array `.toArray()`
- for remove(). indexOf(). lastIndexOf(), or contains(). they make the use of equals(), so . equals method needs to be overridden for your own object in the List.
- Wrapper classes have already defined the proper equals method.

### Stack

- `Stack<T> stack = new Stack<T>();`
- `Stack<Integer> intStack = new Stack<Integer>();`
- `stack.empty()` check if the stack is empty.
- `stack.push(x)` add new element on top
- `stack.pop()` remove and return the top element
- `stack.peek()` return the top element

### Queue

- `Queue<T> stack = new Queue<T>();`
- `Queue<Integer> intQueue = new Queue<Integer>();`
- `queue.empty()` check if the stack is empty.
- `queue.enqueue(x)` add new element to the last.
- `queue.dequeue()` remove and return the first element
- `queue.peek()` return the first element that will be dequeued.

### HashMap

- It is used to store data using key and value pairs.
- need to `import java.util.HashMap`
- cannot contain duplicated keys, will overwrites old value for this key.

#### Create HashMap

```java
HashMap<String,Integer> x = new HashMap<String,Integer>();
```

#### Methods:

- insert value `x.put("A",1);`
- get value `get("A");`
- remove value `remove("A");`
- check existence of a key `containsKey(key)` return null if this key is not found
- check existence of a value `containsValue(value)`
- `get(key)` returns value for the key.
- `keySet()` returns the set of all keys.

### Hashset

- Hashset cannot contain duplicated values. It does not order the element. like set in math. \* They have other features similar to lists.
- The HashSet is a collection of buckets, and each bucket is a collection of elements.
- The collection of buckets can be implemented as an Array or an ArrayList.
- Each bucket may also be a list of elements, usually a LinkedList

#### create

```java
HashSet<String> name = new HashSet<Sting>();
```

#### Methods:

- add `.add("StingA");`
- length: `.size();`

### LinkedHashSet

- similar to Hashset but It orders the elements.

### HashCode methods

- Built-in data classes override the hashCode in java to ensure that equal objects return the same hashcodes.
- By default java uses the object memory location as the hashCode. This can't be used if you override the equals method in your class.
- When override hashcode Methods
  1. Objects that are equal according to their equals method MUST be assigned the same hash code.
  2. Because of 1), whenever you override a class’s equals() method, you MUST also override hashCode().
  3. Try to minimize collisions. Different objects that generate the same hashCode.

### TreeSet

- A TreeSet stores elements based on a natural order defined on those elements.
- The natural order is based on the values of the objects being stored .
- By internally organizing the storage of its elements according to this order, a TreeSet allows fast search for any element in the collection.
- A TreeSet requires a mechanism to sort
  1. The elements being stored must implement the Comparable Interface – Internal order.
  2. The TreeSet uses a class that implements the Comparator Interface – External order.

### TreeMap

- TreeMap stores mappings according to the natural order of the keys, or according to an order specified by a Comparator.

### Iterator

- It is an object created to retrieve elements from a collection.
- hasNext(): Returns true if there is at least one more element; otherwise, it returns false.
- next(): Returns the next object and advances the iterator.
- remove(): Removes the last object that was returned by next from the collection.
- It can be used in a loop.
- The Use of the iterator of the Scanner object is often practiced.

```java
Iterator<String> it = animals.iterator();
while(it.hasNext()) {
  String value = it.next();
  System.out.println(value);
 }
```

### File Class

- It makes you work with files.
- exception handling are needed for file class.
- import `import java.io.File;`.

#### Open File

- Use File class to open a file.

```java
try {
  File fileName = new File("C:\\folderName\\test.txt");
}
 catch (FileNotFoundException e) {
}
```

- if use relative path, the path is in the same folder as the `src` folder.
- we used double backslashes in the path, as one backslash should be escaped in the path String.
- `exists()` method, determine whether a file exists. //return boolean
- The `getName()` method returns the name of the file.

#### Read File

- Scanner class can be used to read files

```java
try {
  File x = new File("C:\\folderName\\test.txt");
  Scanner sc = new Scanner(x);
}
 catch (FileNotFoundException e) {
}
```

- Scanner's close() method is used to close the file
- Scanner class in a sub class of Interator it hs next and has method that can be used in a loop

```java
try {
  File x = new File("C:\\folderName\\test.txt");
  Scanner sc = new Scanner(x);
  while(sc.hasNext()) {
    System.out.println(sc.next());
  }
  sc.close();
} catch (FileNotFoundException e) {
  System.out.println("Error");
}
```

#### Write File

- Formatter class is used to create content and write or overwrite it to files

```java
 try {
    Formatter f = new Formatter("C:\\sololearn\\test.txt");
  } catch (Exception e) {
      System.out.println("Error");
  }
```

- Format method is used to write content
- it also has close method.

```java
Formatter f = new Formatter("C:\\sololearn\\test.txt");
    f.format("%s %s %s", "1","John", "Smith \r\n");
    f.format("%s %s %s", "2","Amy", "Brown");
    f.close();
```

- PrintWriter class can also be used to write content.

```java
//write Hello World into file.txt
PrintWriter outputFile = new PrintWriter ("file.txt");
outputFile.println("Hello World");
outputFile.close();
```

## Thread

- Java is a multi-threaded programming language.
- The life-cycle of a thread is shown below:

  - First way to run code in a new Thread, create a subclass of Thread class as your own class, override your own code in the run() method, then create an instant of your class object and run the start() method of the new object.
  - All thread has priorities range from 1 to 10, can be set with the set Priority() method.

  - Second way to create a Thread(preferred way, make extends available for use), implements the Runnable interface for your own class, and write your own run() method in your class. Later create a new Thread object with(new youClass()) as argument for its constructor. Lastly, run the thread object start() method.

### pause a thread

- Method

```java
Tread.sleep(int numberofMS); //it throws InterruptedException
```

- Example

```java
public static void main(String[] args) throws InterruptedException {  //exception handling for it
Thread.sleep(500);} //make it stops for 500ms
//or use the following pause method instead of Thread.sleep
public static void pause(int duration) {
    try {
        Thread.sleep(duration);
    } catch (InterruptedException ex) {
    }
}
```

### Create a Thread

```java
Thread name = new Thread();
//Or new thread that runs a method.
Thread t = new Thread(() -> animate(gc));
```
