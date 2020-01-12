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
* The $ accesses jQuery.
* The selector finds HTML elements, using CSS selector in double quotes.
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
parent() //method returns the direct parent element object of the selected element.
parents() //returns all ancestors of the selected element.
.first();  //first item from the nodelist.
.last();  //last item from the nodelist.
.eq(index) //method can be used to select a specific element from multiple selected elements. It can be chained after a method that selects multiple elements.
.remove(); //Remove the selected elements.
.empty() //method is used to remove the child elements of the selected element(s)
```

## Event Handling
* Event object is still available. When pass a variables into the anonymous function.

```js
.EventName(function(){
//$(this) can be used here to represent the current node that send the event.
}); //Add event handler of certain event for the selected element.
.each(function(){ //this is the node in each iteration, like foreach loop
})
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
