# Scala

## Introduction

- Scala is an acronym for Scalable Language
- Scala is a general-purpose programming language providing support for both object-oriented programming and functional programming
- The language has a strong static type system
  - type error can be caught by the compiler, not during runtime
- Designed to be concise
- aimed to replace Java
  - compared to Java, Scala has the same speed, 50% less code, more flexible, less errors
- It runs on Java Virutal Machine
- It can work with Java code(Java libraries, Java Tools, Java IDEs), Scala code can also be used in a Java program
- developed by Martin Odersky at EPFL

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

## Installation

- Install Java `SDK` by running `brew cask install java`, run `java -version` to check
- run `brew install scala` to install Scala, for other OS [click here](https://www.scala-lang.org/download/)
- run `brew install sbt` to install SBT, for other OS [click here](https://www.scala-sbt.org/download.html)

## Syntax

- works with or without semicolon at the end of each line
- Multi-expression acts like nested codes that wrapped in curly brackets, semicolon or newline is used to seperate each expression inside

### Variables

- Data Types
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
- Declear variables
  - `var x : Int = 100` declear mutable variables
  - `let y : Int = 100` declear immutable constant variables
  - `var z = false` Scala auto deduces the data type from the assigned value
  - `var m = {val a = 1; val b = 2; a + b}` declear `m` with nested multi-expression, the `m` value is equals the the last expression in curly brackets
  - `lazy var l = 20` declear using lazy loading, memory will be used to assigned values only when compiler has to access it
