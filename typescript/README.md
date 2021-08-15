# TypeScript

## Introduction

* It is an open-source programming language which is a superset of JavaScript.
* It is developed and maintained by Microsoft.
* Compare to JavaScript the differences are:
  * Strong Typing
  * It can catch compiling errors.
* All JavaScript codes works as TypeScript codes.
* It has an extension as `.ts`.

## Installation

1. Install node latest stable version [here](https://nodejs.org/en/)
2. run `npm i -g typescript` to instal Angular CLI. Prepend `sudo` for Mac.
3. run `tsc fileName.ts` to compile any TypeScript codes into JavaScript codes. `fileName.js` will be created in the same folder.

## Type

* TypeScript has the following types.
  * `any` - a type that can be any type.
  * `number`
  * `string`
  * `boolean`
  * `typeName[]`
    * `any[]` is an any type array that can hold a mix of types of elements.
  * enum

    ```typescript
    enum EnumName {
      Enum1,
      Enum2,
      Enum3,
      Enum4
    } //Enum automatically get a value of 0, Enum2=1 etc.
    let x = EnumName.Enum1;
    //explicitly assign value.
    enum EnumName {
      Enum1 = 0,
      Enum2 = 1,
      Enum3 = 2,
      Enum4 = 3
    }
    ```

    * Use interface to create customized type.

      ```typescript
      interface NewType {
        a: boolean;
        b: string;
      }
      ```
* Declare a valuable with certain type:

  ```typescript
  let x: boolean;
  ```

* If the type is not specified during declaration, the variable will have type `any`.
* In order to make an `any` type variable to be of certain type explicitly when use it. Use type assertion.
  * `(<number>x)`
  * `(x as number)`

## Functions

* Create functions with certain type as parameters

  ```typescript
  let functionName = (x: number, y: number) => {
    // ...
  };
  ```

## Class

* Define a new Class

  ```typescript
  class ClassName {
    variableOne: string;
    variableTwo: number;
    functionName() {
      // function codes
    }
  }
  ```

  * By default, without access modifier, variables and functions are public.
  * Use private to make them not accessible.
  * Use protected to make them only accessible by inherited class objects.

* Initiate an instance of the class, access its variable and call its method.

  ```typescript
  let newObject = new ClassName();
  newObject.variableOne = "Hello";
  newObject.functionName();
  ```

* Constructor, one could add the following constructor in class definition.

  ```typescript
  constructor(variableOne: string, variableTwo: number) {
    this.variableOne = variableOne;
    this.variableTwo = variableTwo;
  }
  ```

  * When constructor is set, initial value must be entered for the constructor during instantiation.

    ```typescript
    let newObject = new ClassName("Hello", 1);
    ```

  * TypeScript only supports one constructor. `?` can be added beside the parameter name to make the argument optional. `constructor(variableOne?: string, variableTwo?: number){//...}`
  * Constructor are able to declare class variables. Using access modifier `constructor(private variableOne?: string, public variableTwo?: number){//...}`

* Class properties can be created by using set keyword and access by using get keyword.

  ```typescript
  //In the class definition
  get PropertyName {
    return this.variableOne
  }
  set PropertyName(value) {
    this.variableName = value;
  }
  //Set the property using:
  objectName.PropertyName = "Hi"
  ```

