# Go Programming Language

## Introduction

- The language is often referred to as `Golang` because of the official site's domain name, `golang.org`
- Go is an open source programming language
- Go is syntactically similar to `C`
- Go is a statically(strong) typed, compiled programming language designed at Google by Robert Griesemer, Rob Pike, and Ken Thompson
- It enforces garbage collection
- It has built-in supports for concurrency
- Go code can be compiled to standalone binaries
- It has fast compile time than `C/C++`
- Code files have `.go` extension
- It only uses double quotes

## Setup

- [Click Here](https://golang.org/dl/) to download
  - For Mac, run `brew install golang`
- create local package folder `mkdir -p $HOME/<go_package_path>/{bin,src,pkg}`
- add the following to `PATH` in dot files(`.bashrc` or `.zshrc`)
  ```bash
  export GOPATH=$HOME/<go_package_path>
  export GOROOT="$(brew --prefix golang)/libexec"
  export PATH="$PATH:${GOPATH}/bin:${GOROOT}/bin"
  ```
- To install additional packages run `go get <PackageURL>` to install, the packages will be installed at `$HOME/<go_package_path>`
- In terminal, run `go run filename.go` to compile and run the go code
- Know more about a function or element, run `godoc <packageName> <functionName>`

## Basics Syntax

- Does not need to end to semicolon
- Compile will prompt errors for any declared packages or variables that are not in use

### Comment

- `//` single line comment
- `/* abc */` multi-line comment

## Variables

### Built-in Types

```go
bool
string
int // 32 or 64 bits
int8 // Signed 8-bit integers (-128 to 127)
int16 // Signed 16-bit integers (-32768 to 32767)
int32 // Signed 32-bit integers (-2147483648 to 2147483647)
int64 // Signed 64-bit integers (-9223372036854775808 to 9223372036854775807)
uint // 32 or 64 bits
uint8 // Unsigned 8-bit integers (0 to 255)
uint16 // Unsigned 16-bit integers (0 to 65535)
uint32 // Unsigned 32-bit integers (0 to 4294967295)
uint64 // Unsigned 64-bit integers (0 to 18446744073709551615)
uintptr // an unsigned integer to store the uninterpreted bits of a pointer value
byte // alias for uint8
rune // alias for int32
     // represents a Unicode code point
float32 // IEEE-754 32-bit floating-point numbers
float64 // IEEE-754 64-bit floating-point numbers
complex64 // Complex numbers with float32 real and imaginary parts
complex128 // Complex numbers with float64 real and imaginary parts
nil //for null value
```

- The `int`, `uint`, and `uintptr` types are usually 32 bits wide on 32-bit systems and 64 bits wide on 64-bit systems
- use `int` unless there is a specific reason to use a sized or unsigned integer type.

### Declaration

- Declare a varialbe, `var name type = value`, e.g. `var x int = 3`
  - `var x,y,z int = 5` declare multiple variables in one line
  - When inside a function, type is not mandatory as the compiler can deduce the type, e.g. `x,y := 5`
    - compiler always assign a type of `float64` when type is not specifed
- Type cannot be changed after declaration
- Compiler will generate an error when a variable is declared but not used in code
- Declare a constant, `const name type = value`
- `x := y` will declare `x` that will be exactly the same as `y`(same type and value)
- use `_` as placeholder for variables return from a function that will not be used, `x, _ := funcName()`

### Conversion

- `var y float64 = float64(x)` convert `x` to `float64` and assign it to `y`
- `s := string(bytesData)` convert bytes to string

### Pointers

- `&variableName` return the pointer which contains the memory address of the variable
- `*addressVariable` access the value of the pointer

## Functions

- Function has syntax as `func name(){}` or `func name(x typeForX, y typeForY) returnType { return z }`
  - `func name(x,y type) returnType { return z }` if `x` and `y` have the same data type
  - when return multiple variables `func name(x,y type) (returnType1, returnType2) { return z }` the number return type in the bracket must match the number of variables the function returns
- `name()` will call the function
- Main function is the entry point of a go program, `func main(){}`
- Function can have pointer as parameter, the value pointer points to can be changed in the function
  ```go
  // type pointer as an parameter
  func ptf(x *int) {
      // dereferencing
      *x = 100
  }
  ```

## Struct

- It defines a customized class or type

```go
package main
import "fmt"
// Definition
type Person struct {
  X int
  Y int
}
func main() {
  // initialize an new variable of type Person
  x := Person{name: "Harry", age: 30}
  //or
  x := Person{"Harry", 30}
  // access value of x
  fmt.Println(x.name)
}
```

### Receivers

- They are methods that take a type defined as struct as input arguments
- Value Receiver - add `(variableName StructType)` before function name in the definition, the function will not modify the original value of the variable
  ```go
  func (variableName StructType) receiverName(argumentName type){
    variableName = argumentName
  }
  ```
- Point Receiver - add `(variableName *StructType)` before function name in the definition will change the values the pointer points to, permanently

## Packages

- Every Go program is a part of a package. In most cases programs start with `package main` in the very first line
- Go packages or libraries can be imported using keyword `import` followed by package name wrapped in a set of double qoutes.
  - import one package `import "packageName"`
  - import multiple packages
  ```go
  import ("packA"
          "PackB")
  ```
  - import subpackages(a package inside a package), `import packageName/subpackageName`
- Go export any thing with Camel case(words with capitalized first letter)
- Unused import will generate errors

### Standard Libraries

- [Click Here](https://golang.org/pkg/#other) to view the docs for all Go built-in packages

### fmt

- `fmt.Println(string)` print string in a new line
  - `fmt.Println(string, value)` will append the value after the string with a space in between
- `fmt.Fprintf(w, "<p>%s %s</p>", "Hello", "World")` write formatted strings to `w`
  - `%s` is the placeholder for strings
  - use a set of `` ` `` instead of `"` for multiline text

### math

- `math.Sqrt(x)` square root

#### math/rand

- `rand.Intn(x)` generate number in range `[0, x)`, seed has to be changed in order to generate different numbers

### net

#### net/http

- `http.HandleFunc("/", index_handler)` redirect request made to root path to the `index_handler`
  - In the following example `index_handler` directs all requests `*http.Request` as input, and takes an variable of type `http.ResponseWriter` to output.
    ```go
    func index_handler(w http.ResponseWriter, r *http.Request) {
      //write text into the response writer
      fmt.Fprintf(w, "<h1>Hello World!</h1>")
      fmt.Fprintf(w, "<p>welcome</p>")
    }
    ```
- `http.ListenAndServe(":8000", nil)` let the server listen to request at `localhost:8000`
- `response, error := http.Get(url)` send a Get request
  - use `ioutil` package to read data
  - use `response.Body.Close()` to release the resource

### io

#### io/ioutil

- `bytes, error := ioutil.ReadAll(data)` read data as bytes
  - to read bytes, use `string(bytes)` to convert it into string
