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

### Comment

- `//` single line comment
- `/* abc */` multi-line comment

## Variables

### Built-in Types

- `int`
- `string`
- `bool`
- `float32`
- `float64`

### Declaration

- Declare a varialbe, `var name type = value`, e.g. `var x int = 3`
  - `var x,y,z int = 5` declare multiple variables in one line
  - When inside a function, type is not mandatory as the compiler can deduce the type, e.g. `x,y := 5`
    - compiler always assign a type of `float64` when type is not specifed
- Type cannot be changed after declaration
- Compiler will generate an error when a variable is declared but not used in code
- Declare a constant, `const name type = value`
- `x := y` will declare `x` that will be exactly the same as `y`(same type and value)

### Conversion

- `var y float64 = float64(x)` convert `x` to `float64` and assign it to `y`

## Functions

- Function has syntax as `func name(){}` or `func name(x typeForX, y typeForY) returnType { return z }`
  - `func name(x,y type) returnType { return z }` if `x` and `y` have the same data type
  - when return multiple variables `func name(x,y type) (returnType1, returnType2) { return z }` the number return type in the bracket must match the number of variables the function returns
- `name()` will call the function
- Main function is the entry point of a go program, `func main(){}`

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

### math

- `math.Sqrt(x)` square root

#### math/rand

- `rand.Intn(x)` generate number in range `[0, x)`, seed has to be changed in order to generate different numbers
