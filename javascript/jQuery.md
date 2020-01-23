# jQuery

## Introduction
* jQuery is a JavaScript library that makes many features of JavaScript simpler.
* jQuery is a single js file that can be downloaded from ``www.jquery.com``, then embedded in the script tag.
* jQuery can also be set up by putting its CDN link as the src for the script tag inside the head tag.
  ```html
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
  ```
* It runs in all major browsers.

## Syatax
* ``$("selector").jQueryAction()``
* The ``$`` accesses jQuery.
* The selector finds HTML elements, using CSS selector in double quotes.
  * ``$(p:first)`` selects the first ``p`` tag.
  * ``$(p:last)`` selects the last ``p`` tag.
  * ``$(p:2)`` selects the third ``p`` tag. 2 acts like an index starting at 0.
* node or nodelist variable can be used with jQuery action methods directly, like ``$(node).jQueryAction()``
* The jQuery action method performs on all elements the selector selects.

## Create new element
* Using jQuery assign new node to a variable with certain property.
```
var txt = $("<tagName></tagName>").text("textInside");
let node = $("<p>").html("Hello, World!").css("color", "aqua").attr("title","Quit Hovering!");
```
* When creating new element the selector ``"<div><p>"`` means a new p tag under div tag.

## Changing Elements' Properties with jQuery Methods
* Methods can be chained together.
* All of the element selected will be set, or the first element of all will be accessed for value.
```js
.html(); //Get the inner String. or html code.
.html("Text");   //Change text inside selected tag.
.text(); //Get the inner text, filter all tags inside.
.text("Text");   //Change text, ignore tags
.hide();   //Hide the element(s)
.show(); //Show the element(s)
.attr("attributeName"); //Get the value of a HTML attribute.
.attr("attributeName", "newValue"); //Set the attribute to a new value.
.removeAttr("attributeName")  //Remove an attribute.
.val(); //Get the value of a form field.
.val("newValue"); //Set the value of a form field.
.append()  //adds a node as the last child of each selected element
.prepend() //adds a node as the first child of each selected element
.before() //inserts a node as the previous sibling of each selected element
.after() //inserts a node as the next sibling of each selected element
//multiple elements can be specified as arguments by the before(), after(), append(), prepend() methods by separating them using commas.
// Use HTML code with tags as Text to insert new nodes.
.addClass("className") //assigns one or more className to the selected element.
.removeClass("className") //removes one or more class names from the selected elements.(more classes can be added and separated by spaces)
.toggleClass("className") //toggles between adding/removing classes from the selected elements.
.hasClass("name")   //return true if found
.css("propertyName") //get the CSS property values.
.css("propertyName","newValue") //set the CSS property values.Use JSON syntax to set multiple CSS properties.
.css({"property1":"value1","property2":"value2",...});
.width(); //Get a int value for element’s width in px.
.width(newWidth); //Set width in px. Same for height.
//The width() and height() methods get and set the dimensions without the padding, borders and margins.
//The innerWidth() and innerHeight() methods also include the padding.
//The outerWidth() and outerHeight() methods include the padding and borders.
$(document).width() //Page Width, width of the document
$(window).width()  //Viewport is the width of the browser window
parent() //method returns the direct parent element object of the selected element.
parents() //returns all ancestors of the selected element.
.first();  //first item from the nodelist.
.last();  //last item from the nodelist.
.eq(index) //method can be used to select a specific element from multiple selected elements. It can be chained after a method that selects multiple elements.
.remove(); //Remove the selected elements.
.empty(); //method is used to remove the child elements of the selected element(s)
.appendTo("tagName"); //The appendTo() method inserts HTML elements at the end of the selected elements.
//Example
$("<span>Hello World!</span>").appendTo("p");

```

## Event Handling
* Event object is still available. When pass a variables into the anonymous function.

```js
.EventName(function(){
//$(this) can be used here to represent the current node that send the event.
}); //Add event handler of certain event for the selected element.
```

### List of Event Names
#### Mouse Events:
* click occurs when an element is clicked.
* dblclick occurs when an element is double-clicked.
* mouseenter occurs when the mouse pointer is over (enters) the selected element.
* mouseleave occurs when the mouse pointer leaves the selected element.
* mouseover occurs when the mouse pointer is over the selected element.

#### Keyboard Events:
* keydown occurs when a keyboard key is pressed down.
* keyup occurs when a keyboard key is released.

#### Input Events:
* change - when its value changed.

#### Form Events:
* submit occurs when a form is submitted.
* change occurs when the value of an element has been changed.
* focus occurs when an element gets focus.
* blur occurs when an element loses focus.

#### Document Events:
* ready occurs when the DOM has been loaded.
* resize occurs when the browser window changes size.
* scroll occurs when the user scrolls in the specified element.

##### Ready Method
* it is called when the entire page is loaded.
* It works with the document node which represents all elements from the entire page.
```js
$(document).ready(function() {
   // jQuery code goes here, recommended earlier that window load which waits for image and other content to load.
});
```
* It has a short form.
```js
$(function() {
   // jQuery code goes here
});
```

### Handling Events with on-off-trigger Methods
```js
.on("EventName", function(){}) //attach an event to the selected element.
//multiple event names can be added, separated by spaces
.off("EventName"); //remove event handlers.
.off();   //disable all events.

.trigger("EventName"); //trigger events
```

## Animation
* All methods here accept duration parameter and callback function.
* When the order matters use callback function.
```js
.fadeOut().fadeIn(1000, function(){
  //something happens next
});
//fade methods work with elements that has absolute position.
.fadeOut();
.fadeIn();
.fadeOut(1000); //duration 1000ms.
.fadeIn(2000); //duration 2000ms.
.fadeTo(2000,0.5);  //fade to opacity 0.5 in 2000ms
.slideUp();
.slideDown();
.hide(1000);  //Hide in 1000ms, when no value for argument, default speed 0ms,
.show();
//animate methods is used to change numeric CSS property in an animated motion.
.animate({//properties to be changed to
}, duration(optional), function(){
$(this).methodscallafteranimation()
});
//animate only works on changing numeric css values.
$("#instructions").animate({borderWidth:"10px"});
$("#instructions").animate({fontSize:"30px", width:"600px"}, 2000);
$("#instructions").animate({width:"300px"}, 1000, function() {$(this).css("background-color":"white");});
```

## Ajax

### Load Method
The load method loads data from any files(txt, html, php) on server and puts the returned data into the selected element.
* load a file to a tag.
```js
$('#id').load('filename.txt');
```
* Load a tag with certain id from files.
```js
$("#div1").load("demo_test.txt #id");
```
* Load method has callback function with the following callback.
  * ``responseTxt`` - contains the resulting content if the call succeeds
  * ``statusTxt`` - contains the status of the call
  * ``xhr`` - contains the XMLHttpRequest object
```js
$("#div1").load("demo_test.txt", function(responseTxt, statusTxt, xhr){
  if(statusTxt == "success")
    //statusText returns "success" when load method succeed.
  if(statusTxt == "error")
    //statusText returns "error" when load method failed.
    //xhr.status  show status
    //xhr.statusText   show additional info text
});
```
* Load method can send data with the request to server as an optional parameter.
* On the server the request data is accessed by ``$_REQUEST[dataName]``.
```js
$('#id').load('filename.php', {'dataName':'data'});
```

### Serialize Method
* The serialize() method creates a URL encoded text string by serializing form values.
* One can select one or more form elements (like input and/or text area), or the form element itself. For example: ``$("#form1").serialize();``
* The serialized values can be used in the URL query string when making an AJAX request.
* Form elements can also be converted to a serialized array ``var fields = $("#form1").serializeArray();``. Each element of the array has a name key and a value key.
* Example of serialized values: ``lname=LastName+&fname=+FirstName+&phone=123-456-7890+&email=emailaddress%40example.com```



### Get Method
* The get method requests data from the server with an HTTP GET request.
```js
$.get("filename.php", {'dataName': 'data'},function(callbackData){ $('#resultTag').html(callbackData) })
```
* Get request with Serialized string
```js
$.get('filename.php?dataName=data',
  function(data){
    //Process data here
    }
     )
```

### GetJSON Method
* The getJSON method requests JSON data from the server with an HTTP GET request.
```js
$.getJSON(	'filename.php?dataName=data',
  function(data){
    //Process data here
    }
     )
```



### Post Method
* The post method requests data from the server using an HTTP POST request.
```js
$.post('filename.php',{dataName : 'data'}, callbackFunction)});
//result data will be automatically passed into the callback function's parameter.
```
* Use a fourth parameter to indicate returned data are json objects.
```js
$.post(	'file.php',
  { dataName : 'data'},
  function(data){
    //process data here
    },
    'json')	 			   
       });
```

### ajax Method
* The ajax() method is used to perform an AJAX (asynchronous HTTP) request.
* All jQuery AJAX methods above use the ajax() method. This method is mostly used for requests where the other methods cannot be used.
```js			   
$.ajax({
	type: "GET",
	url: "09xml.xml",
	dataType: "xml",
	success: function(xml) {
    //process data here.
	}
});
```

## Utility Function
* Each - iterate over an array
```js
jQuery.each(arrayName,function (key,val)
  {//Access array elements here.
  }
)
```
* Find - The find() method returns an array of descendant elements of the selected element.
```js
$(node).find('target').each(function(){
  //Process data here
});
```

## Templates
jQuery can be used to construct templates of convert html layout.
```html
//Create a template in html
<script id="employerList" type="text/x-jquery-tmpl">            
           {{tmpl(employer) "#employerTemplate"}}
</script>
<script id="employerTemplate" type="text/x-jquery-tmpl">
   <h1>${businessName}</h1>
   <table>
       <caption>Employees</caption>
       {{each(i, employee) employees}}{{tmpl(employee) "#employeeTemplate"}}{{/each}}
   </table>
</script>
 <script id="employeeTemplate" type="text/x-jquery-tmpl">
     <tr>
         <td>${firstName}</td>
     </tr>        
 </script>   
```
```js
//Use templates with different data.
$(document).ready(
  function() {
    $("#ajax-trigger").click(
      function(event) {
        $.getJSON("10templates.php", { 'employerId' : 1},
          function(data) {
            $("#employerList").tmpl(data).appendTo("#ajax-target");
          });
      });
  });
```
