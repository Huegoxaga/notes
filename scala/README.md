# Scala

## Introduction

- Scala is an acronym for Scalable Language
- Scala is a general-purpose programming language providing support for both object-oriented programming and functional programming
- The language has a strong static type system
  - type error can be caught by the compiler, not during runtime
- Designed to be concise
- aimed to replace Java
  - compared to Java, Scala has the same speed, 50% less code, more flexible, less errors
  - more object-oriented than Java
- It runs on Java Virutal Machine
- It can work with Java code(Java libraries, Java Tools, Java IDEs), Scala code can also be used in a Java program
- developed by Martin Odersky at EPFL
- source files have a `.scala` extension

## SBT

- Scala Build Tool(formerly known as Simple Build Tool)
- It is a CLI tool
- It is included in the `IntelliJ IDE`
- A general purpose build tool written in Scala
- The standard build tool for compile, run, test and package Scala projects
- It uses Apache Ivy for dependency management
- It only updates on request
- It launches REPL(Read-Eval-Print-Loop) inside each project by runing `sbt console` command
  - nice to have as Scala does not use an interpreter, and Scala code need to be compiled everytime to run
  - Will result temp variable after the execution of each line, the variable starting from `res0` to `res1`, `res2`...

## IDEs

- Scala IDE for Eclipse
- IntelliJ IDE with Scala Plugin
- Netbean with Scala Plugin

## Installation

- Install Java `SDK` by running `brew cask install java`, run `java -version` to check
- run `brew install scala` to install Scala, for other OS [click here](https://www.scala-lang.org/download/)
- run `brew install sbt` to install SBT, for other OS [click here](https://www.scala-sbt.org/download.html)

## Syntax

- works with or without semicolon at the end of each line
- Multi-expression acts like nested codes that wrapped in curly brackets, semicolon or newline is used to seperate each expression inside
- `//` single line comment
- `/* abc */` multi-line comment

### Variables

#### Data Types

- `Byte`: 8 bit signed value. Range from -128 to 127
- `Short`: 16 bit signed value. Range -32768 to 32767 Int : 32 bit signed value. Range -2147483648 to 2147483647
- `Long`: 64 bit signed value. -9223372036854775808 to 9223372036854775807
- `Float`: 32 bit IEEE 754 single-precision float
- `Double`: 64 bit IEEE 754 double-precision float Char : 16 bit signed Unicode character. Range from U+0000 to U+FFFF
- `String`: A sequence of Chars
- `Boolean`: Either the literal true or the literal false
- `Unit`: Corresponds to no value : void
- `Null`: null or empty reference
- `Nothing`: The subtype of every other type; includes no values Any: The supertype of any type; any object is of type
- `Any`: Java's Object class
- `AnyRef`: The supertype of any reference type

#### Declear variables

- `var x : Int = 100` declear mutable variables
- `val y : Int = 100` declear immutable constant variables
- `var z = false` Scala auto deduces the data type from the assigned value
- `var m = {val a = 1; val b = 2; a + b}` declear `m` with nested multi-expression, the `m` value is equals the the last expression in curly brackets
- `lazy var l = 20` declear using lazy loading, memory will be used to assigned values only when compiler has to access it

#### String

- Concatenation - `"Hello " + "World"`
- `s` string interpolation - `s"$variableX, $variableY"` `$` is followed by variable name, it will replace the variable with its actual value.
- `F` string interpolation - `F"$variableX%s, $variableY%d"`, this requires a type identifier which
  - `%s` is for `string` varialbes
  - `%d` is for integer variables
  - `%f` is for double variables
- `raw` interploation - `raw"abc\n"`, it will ignore all excape characters and print `abc\n` from the example

### Operators

- `&&`, logic `and`
- `||`, logic `or`
- `x+=1`, same as `x = x + 1`

### Structures

- if...else
  ```java
  if(condition){
    //code
  }else {
    //code
  }
  ```
- If expression, `if(condition) value1 else value2` if condition it will return `value1`, else return `value2`
- while loop, `while (condition) {}`
- do...while loop,
  ```java
    do{
      //code
    } while(condition)
  ```
- for...loop
  ```java
    for (i <- range){
      println(i);
    }
  ```
  - range can be replaced by `x to y`(the same as `x.to(y)`) for range `[x, y]`, or `x until y` for range `[x, y)`
  - range can be replaced by a list
- for...loop with multiple variables, will run `i*j` times with all combination of `i` and `j`
  ```java
    for (i <- rangeA; j <-rangeB){
      println(i);
    }
  ```
- for...loop with condition, `for (i <- 1 to 10; if i < 5){}`
- for...loop as expression, `for {i <- 2 until 6; if i%2==1} yield { i*i }`. It returns a list of values
- match(switch case)
  ```java
  variableName match {
    case value1 => println("match case1");
    case value2 => println("match case2");
    case value3 => println("match case3");
    // Default case
    case _ => println("default");
  }
  ```
  - use `case value1 | value2 | value3` to match multiple values in one case
- match as expression - returns the match value
  ```java
  val x = variableName match {
    case value1 => println("match case1");
    case value2 => println("match case2");
    case value3 => println("match case3");
    // Default case
    case _ => println("default");
  }
  ```

### Functions

- Define a function
  ```java
  def add(x: Int, y: Int): Int = {
    return x + y;
  }
  ```
- Define a function in short `def add(x: Int, y: Int): Int = { x + y; }` or `def add(x: Int, y: Int): Int = x + y;` or `def add(x: Int, y: Int) = x + y;`
- `functionName()` call a function

### Objects

- Defined by the keyword `object`, e.g. `object Name{}`. Then functions and variables can be put inside
- An object can have an object

#### Singleton Object

- It is a `staic` object, one can't create an instance of singleton object or pass parameter in the primary constructor of singleton object
- It provides an entry point to your program execution
- The method in the singleton object is globally accessible, through `ObjectName.methodName()`
  - If the function has one argument, can use `ObjectName methodName parameter` to call
- After the definition the Singleton Object will be initilized
- a singleton object can extend class and traits
- One source file can have multiple singleton object, but one of them must have a main method which acts as the entry point of the program
  - main method `def main(args: Array[String]) {}`
- The singleton object with main function usually has the same name as the file name

#### Companion object

- It is a object that has names same as a class name
  - object is known as the companion object and the class is known as companion class
- A companion object is defined in the same source file in which the class is defined
- A companion object is allowed to access both private methods and private fields of the class
