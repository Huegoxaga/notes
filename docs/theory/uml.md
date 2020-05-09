Step for programming
define(IPO Chart)
Design(Pseudo Code or Flow Chart) <->Test
Implement(programming) <->Test

3 main logic
sequence
selection
repetition

IPO
INPUT Read Get Obtain
PROCESS Compute calculate set
OUTPUT print display show write

Pseudocode
Get calculate set display assume

IF condition THEN
block
ENDIF condition THEN

ENDIF

for loop WHILE condition
….
ENDWHILE

for x=x to y
block
endfor

Flowchart
use draw.io
circle for start and end
rectangle for instructions
diamond for condition
rectangle with two border for function
For looping structure.

UML Class diagram show the class name, instance variable name: type, and instance methods info.

In UML the Arrow(—>) points to the object. (instant variables for another object.) (read as has a)
The number under the arrow is the multiplicity(the number of this object type), it can be a number or a range. Ex: for 0..2 when there is 0 object, it means the two object are both null. If no number for the arrow is means exactly one.
sign means 1 or more.
sign means 0 or more.

In UML diagrams
Class name in the first row.

- is private + is public.
  Data types are placed after : (same after methods if return ex: method(name:int))
  Parameters are placed in () for method as usual
  add return type void if the method has no return.
  add name into the diagrams only when it is necessary.

Hollowed triangle head is used to represent inheritance relationship read as "is a".

- In object oriented programming, each object has three dimensions: identity, attributes, and behavior. For java object instance variables are the attributes and instance methods are the behaviors.
- Interface is what can be seen by the user. they are public instance variables + public method headers+JavaDoc comments (also called the API)
- Implementation is the solution for the function that is done and hidden from the user. they are private stuff+method bodies+comments inside methods.
  encapsulate means to make some instance variables and methods inaccessible from outside a class.
  inheritance relationship for interface is shown in dotted hollow triangle arrow in UML and name in italics after a `<<interface>>` tag. also read as "is a”
  In a UML diagram, underlining indicates static variables and methods.
