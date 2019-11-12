# Maple
This document collects information on products from Maplesoft and DigitalED.

## Maple
* It is the flagship product of Maplesoft.
* It is a software that make use of a powerful mathematics engine.
* It can be used to solve mathematical problems.
* Help document for Maple can be found [here](https://www.maplesoft.com/support/help/index.aspx).



### Maple Code Syntax
* Each line of code should end with a ```;```.

### Operators


#### Assignment
```
r := x^3;
```
* The expression ```x^3``` is assigned to the variable ```r```.


### Types
* Name
 * Maple has a type name denoted by a pair of left single quotes, ``` `x` ```. Variable names are of type Name.
* String
 * String are enclosed by double quotes.
* Rational
* Fraction

[Click here](https://www.maplesoft.com/support/help/Maple/view.aspx?path=type&term=type#bkmrk2) to see a complete lists of defined type in Maple.

#### Convert to String
```
"$x"
```
* Expression $x is converted to plain text string.

#### Type Conversion
```
convert(expression, type)
```
* The second argument of the convert function is the type for the expression to convert to.
* If the type is ```rational```, the expression is converted to the rational form.
* ```convert(expresion, float, 3)``` converts the expression to a float number with 3 decimal places.
* Type can also be ```binary```, ```degrees```, ```radians```, ```string``` etc.
* parse(string, option)   //convert string into expression, auto evaluation.

```
parse(s);
```
* Parse function convert the string s into an expression or a statement.
* If statement is specified as the second argument, ```parse(s, statement);```, the statement in the first argument will be evaluated.

#### Type checking
```
type(x,'float');
```
* Returns true is x is of the type that is indicated by the type name.
* ```'float'``` could be replace by any type name.

```
whattype(x);
```
* Returns the type name of x.


### Flow Control
#### If condition
```
if (a > b) then a else b end if;
```
* Returns a if a > b. Returns b if a < b.
* Condition can be ```'Fail'``` which means false, then the second value will be returned.

```
if a < b then
  if a < c then d := a*b else d := a*c end if
end if;
```
* Nested if statement

```
a := 3;
s := String(a, if a = 1 then "st"
               elif a = 2 then "nd"
               elif a = 3 then "rd"
               else "th" end if);
```
* if-elif-else structure.
* The example code is equivalent to  ```s := "3rd"```.

### Functions

#### String Concatenation
```
String(a,b,c,....);
```
* The String function concatenates zero or more expressions into a single string.

```
cat(a,b,c,....);
```
* The cat function is commonly used to concatenate strings and names together.



#### Root
```
root(x,n);
```
* Returns the nth root of x.

#### Simplify
```
simplify(x);
```
* x can be any expression.
* Returns a simplified expression for x.

#### Evaluation
```
evalb(x)
```
* Evaluates a comparison expression and returns a boolean value of either true, false, and FAIL.
* If evaluation is not possible, an unevaluated expression is returned.

#### Factorize
```
“factor($q)");
```
* Factorize the expression q.



### Packages
* Maple has many packages that add additional functions to the Maple engine.
* Packages can be accessed by using the following ways.
 * Long form: Use function directly with ```	PackageName[CommandName](arguments)``` syntax.
 * Short form: place ```with(PackageName)``` at the beginning of the code to import the package.
 * Module Members: Use function directly with ```PackageName:-commandName(arguments)``` syntax.


#### StringTools
The StringTools package is a collection of optimized string manipulation utilities.
* [Click here](https://www.maplesoft.com/support/help/Maple/view.aspx?path=StringTools&term=stringtools#bkmrk0) to see a list of StringTools Package Commands.

#### InertForm

The InertForm package provides a collection of commands for obtaining and working with inert-form expressions.
* The inert form of an expression is a representation that avoids evaluation and automatic simplification by changing operators and function names to unassigned symbols prefixed with a % character.  For general information on inert functions, see value.
* [Click here](https://www.maplesoft.com/support/help/Maple/view.aspx?path=InertForm&term=InertForm#bkmrk0) to see a list of InvertForm Package Commands.



## Möbius
* It is formerly known as Maple T.A.
* It is a web-based, e-learning platform provided by DigitalED, a spin-off of Maplesoft.
* It can be used to present course content and provide online testing and assessment.
* It utilizes the Maple's math engine.
* Help document for Möbius can be found [here](https://www.digitaled.com/support/help).
* Help document for older versions can be found [here](https://www.maplesoft.com/support/help/MapleTA2017/index.aspx).

### Using the Algorithm Editor
Codes can be written in the editor, in order to add random variables for the questions, and calculate the result for the questions.
* Each line of code should end with a ```;```.
* Strings are enclosed by double quotes.
* expressions which are enclosed by single quotes will not be evaluated.
* Click ```Button``` to run the code once, and see the outputs for all the variables.

The following syntax should be adopted for the algorithm editor.

#### Assignment
```
$x = 5;
```
* Variable names are started with ```$``` sign.
* Variables can be accessed in the question editing area, feedback editing area and the grading code for maple-graded questions.

#### Comments
```
#This is the comment.
```
* Any codes after ```#``` will be ignored.

#### Built-in Functions
The following built-in functions can be used in the algorithm editor.

##### Factorial
```
fact(n)
```
* Returns factorial n.
* If n is not an integer returns fact(int(n)).
* If n is negative, returns 1

##### If Condition
```
if(a, b, c)
```
* If a is nonzero, it returns b. Otherwise, it returns c.

##### Convert to Integer
```
int(x)
```
* Returns the integer part of x.

##### Round Decimals
```
decimal(n, x)
```
* Rounds x to n decimal places.

##### Round for Sig Dig
```
sig(n, x)
```
* Rounds x to n significant digits.

##### Random Integer Starting at 1
```
range(x, y, n)
```
* x and y are integers.
* Returns random values from x to y inclusively, in steps of n.
* ```range(x,y)``` is equivalent to ```range(x,y,1)```
* ```range(x)``` is equivalent to ```range(1,x,1)```

##### Random Integer Starting at 0
```
rint(x, y, n)
```
* Returns random values from x to **y-1** inclusively, in steps of n.
* ```rint(x,y)``` is equivalent to ```rint(x,y,1)```
* ```rint(x)``` is equivalent to ```rint(0,x,1)```

#### rand(x, y, k)
```
rand(x, y, k)
```
* Returns a random real number between x and y (inclusive), expressed to k significant figures
* If parameter k is ignored, any random real number between x and y could be generated.

##### Compare Not
```
not(a)
```
* Returns 1.0 if a is equal to 0.0. Otherwise, it returns 0.0.

##### Compare Equal
```
eq(a, b)
```
* Returns 1.0 if a and b are equal. Otherwise, it returns 0.0.

##### Compare Greater or Equal
```
ge(a,b)
```
* Returns 1.0 if a is greater than, or equal to b. Otherwise, it returns 0.

##### Compare Less or Equal
```
le(a,b)
```
* Returns 1.0 if a is less than, or equal to b. Otherwise, it returns 0.0.

##### Compare Not Equal
```
ne(a,b)
```
* Returns 1.0 if a and b are not equal. Otherwise, it returns 0.0.

##### Compare Greater
```
gt(a, b)
```
* Returns 1.0 if a is greater than b, that is (a > b). Otherwise, it returns 0.0.

##### Compare Less
```
lt(a, b)
```
* Returns 1.0 if a is less than b, that is (a < b). Otherwise, it returns 0.0.

##### Add Condition
```
$x = range(a,b);
condition: ne($x,c);
```
* Imposes the condition defined by any comparison statement.
* The example returns a random integer between a and b that is not equal to c.

##### Greatest Common Divisor
```
gcd(a, b)
```
* Returns the greatest common divisor of a and b.

##### Using Maple Code
```
maple("ithprime(12)")
```
* Pass text to the MapleTM kernel and return the value of the last line processed.
* The example returns the result of maple code ```ithprime(12)```.

##### Formatted Number
```
numfmt("#.00", a)
```
* Returns the value of a, formatted according to the template fmt.
* The format in the example code print a with 2 decimal places.

##### String Concatenation
```
strcat("Hello", " World", "!")
```
* Returns the concatenation of the strings in the list.
* The example returns ```Hello World!```

##### Select Element from a List
```
$n = 0;
switch($n,23,14,21,18);
```
* Returns an element of the list of parameters after $n, $n is the index of the element to be returns, starting from 0.
* The example returns the first element after ```$n``` which is ```23```, when ```$n=0```.
* ```$n``` in the switch function could be replace by functions like ```rint(4)```, in order to return the list element randomly.

##### Render Expression Using MathML
```
mathml("x^(1/3)")
```
* The expression will be displayed as cubic root of x.
* ```mathml(expresion, "nosimplify")``` will displayed the expression without simplification.

### Get Response
* Response can be received for different question types.
* Click the Response button to select the question types.

#### Mutiple Chioces
* The correct answer for the question can be set to a certain choice using the checkbox.
* The correct answer can be represented by a variable, when variable equals 1, the first choice is correct. When variables 2, the second choice is correct and so on.
* For multiple choice that has two or more answers use ```$AnsA, $AnsB``` as the algorithmic value in Answers field.
* Set the correct answer with checkbox still works if algorithmic value is set.

#### Maple Graded questions
* The grading code for maple-graded questions uses Maple codes.
* When the expression for correct answer is placed in the answer input field, the auto-generated code check if the response equals the answer value.
* Change the ```ANSWER``` variable to any other expression for maple-graded question to compare student response with.
* To display symbolic expressions as answer for graded questions. go to the MathML tab, copy and paste the markup syntax inside ```print(``)``` function, and place the function in the answer input field.
* $RESPONSE stores the expression received from student response.
* Both of the ```evalb(e)``` and ```is(e)``` functions can be used to evaluate the student response.
* "$RESPONSE" converts the expression to string, and it can be placed in the answer input field to check the actual response interpreted by symbolic entry.
* StringTools are helpful when certain coefficient in required in the response string. Here are some examples.
 ```
 evalb(($ans)=($RESPONSE) and not StringTools:-Search("$coefX","$RESPONSE")=0 and not StringTools:-Search("$coefY","$RESPONSE")=0);
 ```
 ```"$coefX"``` and ```"$coefY"``` must be in the ``` "$RESPONSE" ``` string.
 ```
 evalb(($ans)=($RESPONSE) and not StringTools:-Search(["$coefX","$coefY"],"$RESPONSE")=[0,0]);
 ```
 Either ```"$coefX"``` or ```"$coefY"``` must be in the ``` "$RESPONSE" ``` string.
 ```
 evalb(($ans)=($RESPONSE) and StringTools:-CountCharacterOccurrences("$RESPONSE","^")=3 );
 ```
 There must be ```3``` ```"^"``` in the ```"$RESPONSE"``` string.


 ### Symbolic Entry
 It can be used to construct complex math expressions for display or get student responses.
 * Variables can be put inside the symbolic expressions, always add a space after the variable names or the following values will be treated as a part of variable names.
 * When getting response with symbolic entry, currently, * need to be placed between variable with exponents.
