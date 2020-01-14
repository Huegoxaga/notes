# PHP

## Introduction
* PHP are scripts can only be executed by the server.
* PHP is compatible with almost any modern server and many databases.
* PHP is free.
* PHP scripts can be HTML files with PHP tags or a single PHP script file that returns data, they have a php extension.
* PHP code execution from top to bottom, as it is embedded inside HTML code. variable initialization, class definition, object instantiation and global function codes for php are generally places before <html>. Some constant can be declared in the head tag with all capitalized name. Other php code can be placed at anywhere in the php file if necessary.
* When it is placed before <!DOCTYPE>, PHP tag and <!DOCTYPE> should be in the same line and have no space in between.
* The output of php code is the html content that to be shown on the user's screen.
* PHP statements end with semicolons(;).
* For a folder has the same name of the php file name it contains when enter the folder address the php file will be opened.
* For file name like index.html or index.php in a folder on the server will be auto-loaded.
* PHP uses ``/``/ or ``#`` for single-line comment and ``/*`` plus ``*/`` for multi-line comment.
* In order to practice PHP, Tools like XAMPP(using the Apache web server component) can be installed so a local server can be hosted on the personal device\(http://localhost:8080/\), PHP files can be added in the htdocs folder which is mapped to the local server.


## Implements PHP in HTML

### PHP code tags

```
<?php  //PHP code;    
?>	//This is supported by most servers.

<? //PHP code;
?>    // This is also supported by some servers.
```

* Some php code block can be divided into two groups of <?php ?> tags and put HTML code in between.
```
if (condition) {
            ?>
            <h1>ABC</h1>
            <?php
        }
        ?>
```

### PHP expression tag
```
<?=    ?>
```

* It is used to show the result of an expression.
* It can only be followed by expression not php code blocks.
* PHP code can be placed anywhere in the HTML and CSS style sheet code, even inside a link:
"www.<?= $domain ?>.com"

### Use Script Tag
``<script>`` tag can also hold PHP code.
```php
<script language="php">
//PHP code;
</script>
```

## Variables
* variable starts with $ sign.
* $variable_name = value;
* variable name can only contain alpha-numeric characters and underscores.
* variable name cannot start with a number.
* variable names are case-sensitive.
* variable is created when the value is assigned, no need to declare the type.
* variable name uses all lower-cases.


### Constant
constant cannot be changed or undefined after it has been defined.

#### user define function to create constant
```php
define("CONSTANTNAME", value, case-insensitive(true or false(default)))
//the name should be in a set of quotations.
```

### Variable Variables
* Their names start with ``$$``.
* A variable variables use the value of another variable as its name.

```php
$a = ‘b’
$b = ‘hello’
echo $$a -> ‘hello’
```
### Scope
* A variable declared outside a function has a global scope.
* A local variable (declared inside a function) must use global keyword to get access of the global variable.
```php
global $local_variable;
echo $local_variable;
```

## Data type

#### Primitive Data Types:
* int
* float
* bool(TRUE, FALSE)
* null(NULL)

#### Type Casting
* PHP automatically converts variables to the current data type during operations.
* To cast a type into another type explicitly use brackets: ``(int)"12"``This cast "12" into integer 12.
* In PHP any value can be cast to boolean, Ex, null always cast false, not null casts true.
* A Boolean value TRUE is converted to string "1" whereas Boolean FALSE is converted to an empty string ""

#### Non-primitive Data Types:
Array, String, and Object.

### Array
It stores a list of values.

#### Numeric Arrays(indexed arrays)
* It has an index that starts at 0.
* It can contains mixed data types in one array.

##### Create New Array
```php
$array1 = array(‘a’, ‘b’, ‘c’);
//alternatively
$array1 = [‘a’, ’b’, ’c’];
//alternatively
$array1[0] = ‘a’;
$array1[1] = ‘b’;
$array1[2] = ‘c’;
echo $array1[1];
//output: ‘b’
```

#### Associative Arrays
* They are arrays that use named keys for each values.
* Keys can only be strings, values can be of any types.
* Associative arrays can also be accessed using index integer([0] represents the first value.)
```php
$array2 = array(‘first’ => ‘a’, ‘second’ => ‘b’, ‘third’ => ‘c’);
//or
$array2 = [‘first’ => ‘a’, ‘second’ => ‘b’, ‘third’ => ‘c’];
//alternatively,
$array2 = [ ];
$array2[‘first’] = ‘a’;
$array2[‘second’] = ‘b’;
$array2[‘third’] = ‘c’;
echo $array2[‘second’];
//Output ‘b’
```

* { and ‘ can be ignored in the PHP string
```php
echo "<p>$array2[second]</p>"
```
* need the braces if the array subscript is an expression
```php
echo "<p>Your Userid: {$user[$a . $b]}</p>";
```


#### Multi-Dimensional Arrays
* They contains one or more arrays.

* two-dimensional array has one array inside one array. It can be accessed using two indices.
```php
echo $arr[index1][index2];
```
* three-dimensional array has one more array inside two-dimensional array. It can be accessed using three indices.
```php
echo $arr[index1][index2][index3];
```
* Multi-Dimensional arrays can have a mix of both numeric and associative arrays.

#### Helper Functions
```php
count($array)    //return the length of $array.
array_pust($array, $newElement)	//append $newElement to $array.
```

### String
* String is an array of single-character string in PHP.
* For strings, both single(raw) or double(richly-interpreted) quotation marks work. However only double quotation mark can embed variables.
```php
"<li>$i</li>"
```
* If this string use "", inside the string "" for html should be changed to ‘’.
```php
"<div class=‘$class'>$die</div>"
```
* To embed expressions or embed variables for string with singe quotation, use {}.
```php
"<div><h1>{$user->get_name()}</h1></div>"
‘{$x+$y}’
```


#### String Concatenation
a period can be a String Operator that concatenate two strings.

#### string helper Functions
* strlen($string)	return string length
* echo function, it is a built-in functions, a language construct. It does not need parentheses.
Is is used to output text. HTML tags can be used in the echo text. So the browser will take this output and display content accordingly.
```php
echo "Hello World!";
echo "<h1>Hello World!</h1>";
```


## Operators

### Arithmetic Operators
* ``+``	Addition
* ``-``	Subtraction
* ``*``	Multiplication
* ``/``	Division
* ``%``	Modulus(remainder)

### Increment operator
It is used to increase the value of the variable.
* ``x++`` post-increment return original value, then increment the value by 1.
* ``++x`` pre-increment increment the value by 1, then return the value.

### Decrement operator
It is used to decrease the value of the variable.
* ``x--`` post-decrement return original value, then decrement the value by 1.
* ``--x`` pre-decrement decrement by 1, then return the value.

### Assignment operators
It is used to write values to variables.
* ``$a = 1;``
* ``$b = a;``
It can also be used with arithmetic operator.
* ``x+=y``   ->   ``x = x+y``

### Comparison operators
they are used inside conditional statements, and return boolean values.
```php
$a == $b
```

* ``==``	Equal, true if the values of two variables are the same.
* ``===``	Identical, true if the values and types of two variables are the same.
* ``!=``	Not equal
* ``<>``	Not equal
* ``!==``	Not identical
* ``>``	Greater than
* ``<``	Less than
* ``>=``	Greater than or equal to
* ``<=``	Less than or equal to

### Logical operators
They are used to combine conditional statements.
* ``and``	And
* ``or``	Or
* ``xor``	Exclusively or
* ``||``	Or
* ``!``   Not

### Precedence
Precedence for all operators are generally the same as many other languages. use parentheses ( ) for precedence if the precedence is not sure.


## Control Structures

### Conditional statements

#### If statements
Curly braces can be omitted if there is only one statement.

```php
if(condition) {
}

if(condition) {
} else {
}

if (condition) {
} elseif (condition) {
} else {
}
```

#### Switch Cases
```php
switch (x) {
	case value 1:
		//code if n == value1
		break;
	case value2:
		//code if n == value2
		break;
	…
	default:
		//optional, this line will be executed if all values don’t match x.
}
```

##### Break/Continue statement
* If there is no break statement in switch structure, code will keep running when there is a match.
break statement can be used in all other control structures.
* A single break statement will terminate the current PHP script.

##### Continue statement
* It will make the program skip the following code in a loop structure.


### Loops
#### While Loop
```php
while (condition) {
}
```

#### Do Loop
```php
do {
// the code will be executed at least once.
} while (condition)
```

#### For Loop
```php
for (init; test; increment) {
}

//Ex.
for( $a = 0; $a < 6; $a++) {
}
```

#### Foreach Loop
```php
foreach ($arrayName as $randomValueName) {
}

foreach ($arrayName as $key => $value){
	//$key and $value will be set in each iteration.
}
```



## include and require statements
* They allow for the insertion of the content of the PHP file by appending the file path to the keyword include or require.
* Both absolute and relative path work in these statements.
* There is only one difference between include and require statement. When using require, if the PHP file is not found, the script will cease execution and produce an error.


## Functions

```php
function functionName() {
	//code that will be executed when the function is called.
}

functionName( );  //call the function
// function name can not start with a number or a special symbol
// function name are not case-sensitive.

//parameters can be defined in parentheses.
function functionName(parameter1, parameter2, …) {

}

//default argument can be defined in the following way.
function xValue($x=1) {
	echo $x
}

xValue();	//Output is 1.

xValue(2)	//Output is 2.

//default argument should be on the right side of other regular arguments.
function xValue($y, $z, $x=1) {}

//return statement
return $variableX;
//It stop functions’ execution and return values
//If a function has no return statement, it will return NULL when it is called.
```


## Predefined Variables
They are superglobal. They can be accessed all the time regardless of scope.

In PHP, superglobal variables are
``$_SERVER``, ``$GLOBALS``, ``$_REQUEST``, ``$_POST``, ``$_GET``, ``$_FILES``, ``$_ENV``, ``$_COOKIE``, ``$_SESSION``.
### ``$_SERVER``
* ``$_SERVER`` is an associative array that holds information.
```php
$_SERVER[‘SCRIPT_NAME’] // returns the path of the current script.

$_SERVER[‘HTTP_HOST’]     // returns the host header(the folder that contain the entire host files) name.
```

### ``$_POST`` and ``$_GET``
* ``$_POST`` is an associative array that holds form data in the action file when the method is post.

* ``$_GET`` is an associative array that holds form data in the action file when the method is get.

* The form information can be accessed in the action php file using ``$_POST["inputTagName"]`` or ``$_GET["inputTagName"]``

### ``$_SESSION``
* ``$_SESSION`` is an associative array that store customized variables on the server that can be accessed by multiple pages.
* Session variables last until the browser is closed or the session is explicitly closed in the scripts. The data will persist on server until a certain time has collapsed according to the setting.

#### Start a Session
A session is started using the following function.
```php
session_start();
//It must be the first line of code before <!DOCTYPE>. Same in other pages if session variable will be accessed.
```
When new session is created, A ```$_SESSION[‘PHPSESSID’]``` is assigned as a user session identifier for the server. It is stored in the client’s cookies.
a variable is stored using the following way. ``$_SESSION[‘username’] = "Tom"``;
#### End a Session
```php
session_unset();	//It is used to clear session variables.
session_destory()	//It is used to end the session, the data still exists on server. (a session_start() is needed for any session to be terminated.)
```

### ``$_COOKEI``
* ``$_COOKEI`` is an associative array that the server creates on the user computer.

* The setcookie() function must appear before the <html> tag.

* Cookies are created using the following function.
```php
setcookie(cookieName(only required parameter), cookieValue, expireTimeInSecond(0 make the cookie expire when session ends), cookiePath(where the cookie is available), domainName, secure(Whether the cookie should only be transmitted through HTTPS connection, default FALSE.), httpOnly(TRUE if HTTP protocol is required, default FALSE.))
setcookie("user", $value, time() + (86400 * 30), '/');
//The cookie will expire after 30 days.
//‘/‘ this means the cookie is available for the entire website.
Function time(); //returns the current time.
$_COOKIE[‘user’]="username"; //Create cookie value.
isset($_COOKIE['user']) //returns true if the the key ‘user’ exists in the $_COOKIE variable.
//It is used to perform checking.
```


## Classes
* PHP class can have member variables called properties and functions called methods.
* class name starts with a letter or underscore.
* public states the content can be accessed from anywhere in the code.
* private content can only be seen in the class.
* protected content is only visible to its parent and subclass.

### Definition
```php
class ClassName {
	public $variable;  //property
	public function funcName () {
	//method
	}
}
```

### Instantiation
```php
$newObject = new ClassName();
```

### Access Properties
```php
echo $newObject -> $variable;
```

### Access Methods
```php
$newObject -> funcName();
```

* Method call can be embedded in a string using braces {}.
```php
echo "Welcome to {$object->get_location( )}"
```

### Assign Properties
```php
$newObject -> $variable = 100;
```

``$this`` it is used to refer the current class. It is used for method definition to access property from the same class.

### constructor method
```php
__construct(){}
//or
__construct($x, $y){}	so for new object $newObject = new ClassName(1 , 2)
```
* It is called upon instantiation
* There can be only one constructor in one class definition.

### destructor method
```php
__destruct(){}
//It is called when object is destroyed.
//PHP releases all resources when the a script finishes its execution.

unset() function
//It is used to destroy objects.
unset($objectName);
```

### Getter Methods
It can have name like get_name( )
### setter methods
It can have name like set_name( )




### Inheritance
* keyword extends is used for creating subclass.
* when subclass does not explicitly define constructor, the parent class’s constructor is called, given that this constructor is not private.

* interface are a group of methods that required for a class.
* multiple methods can be declared together, separated with comma.
* All of the methods should be public in a interface.
* For a class to implements interface use keyword implements.

### Abstract class
* it can not be instantiated.
* it has abstract method.
* other class inherit abstract class must define all the abstract method.
* abstract method can only appear in abstract class.
* keyword abstract is used in front of keyword class and function.

### Static property and method.
* They are accessible without instantiation.
* They are accessed by ClassName::$propertyName or ClassName::methodName()
* self::$property is used to access property form a static method in the class definition.

### Final Keyword
* final class cannot be inherited.
* final method cannot be override in child classes.


## Helpful function

### filter_input function
When form data is sent to the php file, filter_input function is used to get and filter form input.
```php
filter_input(INPUT_GET/INPUT_POST, "dataName", FILTER_TYPE);
```

#### Filter type
* ``FILTER_VALIDATE_INT``, ``FILTER_VALIDATE_FLOAT``, ``FILTER_VALIDATE_EMAIL``, ``FILTER_VALIDATE_URL``
  * null if parameter is not found
  * false if the parameter was found but is not an integer.
  * an int value if past the test.
* ``FILTER_SANITIZE_SPECIAL_CHARS``
  * return null if parameter is not found
  * return a string with all special character replaced with html entity like &#50.
* ``FILTER_SANITIZE_STRING``
  * return null if parameter is not found
  * return a string. All special characters are removed.

* null and false are always used for error handling for these functions.

#### Random
```php
rand($min, $max)
```
* returns a random integer $min to $max

#### Date
```php
date($format)
date("M d Y")
date("m/d/y")
date("h:i:s A")
date("l dS \of F Y h:i:s A")
```
* return current date/time string
* To avoid a warning, one must set the timezone
```php
date_default_timezone_set("Canada/Eastern");
```

#### ``var_dump($var)``
* prints the type and content of $var or &object
* In HTML, using ``<pre>`` tag to hold space for the ``var_dump()`` output. It is not mandatory.
```html
<pre><?= var_dump($varName)?></pre>
```
* or directly use ``var_dump($var)`` in PHP to print object info in console.
* ``var_dump($_GET)`` and ``var_dump($_POST)`` can be used to check form content.

#### phpversion()
return the PHP version string

#### Formatting Number
```php
//round $n to $p decimal places
number_format($n, $p)
$owing = number_format($user->get_owing(), 2);
```
#### Send Email
```php
mail($addr, $subj, $msg)
//send email when email server is configured.
```

#### Hashing Password:
```php
password_hash($user_pwd, PASSWORD_DEFAULT) //return hashed password
password_verify($user_pwd, $hash) //return true if raw password $user_pwd. hashed password $hash.
```
## Files I/O

### Open Files
* The fopen() function creates or opens a file.
* If you use fopen() with w or a mode to open a file that does not exist, the file will be created, in the current folder.
```php
$myfile = fopen("file.txt", "w");
```

### File Modes
Use one of the following modes to open the file.
* r: Opens file for read only.
* w: Opens file for write only. Erases the contents of the file or creates a new file if it doesn't exist.
* a: Opens file for write only.
* x: Creates new file for write only.
* r+: Opens file for read/write.  
* w+: Opens file for read/write. Erases the contents of the file or creates a new file if it doesn't exist.
* a+: Opens file for read/write. Creates a new file if the file doesn't exist
* x+: Creates new file for read/write.

### Write Files
When writing to a file, use the fwrite() function.
```php
fwrite("filename","text");
```

### Read Files
The file() function reads the entire file into an array. Each element within the array corresponds to a line in the file:
```php
$read = file('names.txt');
foreach ($read as $line) {
  echo $line .", ";
}
```

### Close Files
* the fclose() function to close the file.
```php
fclose("fileName")
```
* It returns TRUE on success or FALSE on failure.
* Write content from user input
```html
<?php
if(isset($_POST['text'])) {
  $name = $_POST['text'];
  $handle = fopen('names.txt', 'a');
  fwrite($handle, $name."\n");
  fclose($handle);
}
?>
<form method="post">
  Name: <input type="text" name="text" />
  <input type="submit" name="submit" />
</form>
//The isset() function determined whether the form had been submitted, as well as whether the text contained a value.
```


## Database Connection
There are two ways to connect: Mysqli and PDO.


### PDO(PHP Data Objects)

1. connect the database by instantiating a new PDO object.
```php
try {
	$dbh = new PDO("mysql:host=localhost;dbname=MYID","MYID","MYPASSWORD");
}catch (Exception $e) {
	die("ERROR: Couldn’t connect. {$e ->getMessage()}");
}
```
  * die function stops execution and output a message and abort the script.
  * for XAMPP, the login id is "root", and password is empty string ""

2. Prepare the statement
```php
$command = "INSERT into grades (firstname, lastname) VALUES (?,?)";
$stmt = $dbh->prepare($command);
```
  * get the complied statement using prepare method of PDO objects.
  * ``?`` is the placeholder that to be placed by an info array in next step.

3. execution
```php
$params = ["sdfk", "sdlkfjs"];
$success = $stmt->execute($params);
```
  * using execute method of PDO objects, replace ``?`` with an array of arguments in corresponding order.
  * ``$success`` is true if success, otherwise, it is false.

4. check results
```php
if($success){
	echo "<p>{$stmt->rowCount()} rows were affected.</p>"
}
```
  * the rowCount() method returns the number of affected rows in the operation.

5. For select statement there is one more step.
```php
while($row = $stmt->fetch()) {
	// each iteration will provide $row as data in each row from the query
}
// if there is only one row, use if
if($row = $stmt->fetch()) {
	// get the data here.
} else {
	// get empty result.
}
```
  * the fetch method of the compiled statement returns data one row at a time, and returns null eventually.
  * the row data received is an associative array, with keys identical to column names.
  * database returns all string. int or floats need to be cast for use using (int).
  * the expression after while returns false when there is no more new row.


* It is a good idea to establish a class for the table, to store each row of the data into an array of objects.
* When access data using SQL remember that SQL is not case sensitive, PHP is.
* With PHP, HTML or other files can be edited using data from the database.
* filter_input validation is mandatory for getting input from forms for database operation. also, POST method should always be used to avoid duplicated operation.



#### encode data to JSON
PHP needs to encode data into JSON in order to response to JavaScripts calls, using Ajax.

* JSON encoding
```php
json_encode($data)
```
* JSON decoding
```php
json_decode($s)
```
* Fetch an array of object from database and encode into JSON for JavaScript using json_encode() directly will omit all private variables of an object. The following interface should be implemented in the object's class definition.
```PHP
// Class Definition
class User implements JsonSerializable
{
	private $firstname;
	private $lastname;
	function __construct(…){…}
	public function jsonSerialize()
	{
		//json_encode calls this method and get all private variables.
		return get_object_vars($this);	}
}
//to use json_encode:
$userlist = [];
while ($row=$stmt->fetch()) {
	$user = new User($row["firstname"], $row["lastname"]);
	array_push($userlist, $user);
}
echo json_encode($userlist);
```
* One may use an array of associative arrays to store objects directly.
```php
 $userlist = [];
while ($row=$stmt->fetch()) {
	$user=["firstname"=>$row["firstname"], "lastname"=>$row["lastname"]];
	array_push($userlist, $user);
}
echo json_encode($userlist);
```
