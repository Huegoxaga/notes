CSS Styles

CSS codes end with ;

multiline comments:
``/* abc */``


To add CSS into HTML, there are ways.


inline CSS:
<p style = “color: blue;”> this is the blue text </p>

embedded or internal CSS:
<style>
  p {color: blue;
    }
</style>

External CSS
<link href="style.css" rel="stylesheet" />

in the head tag.

A CSS file ends with .css

size units = em, pt, px, %, cm, in

color representation:
#ff0000
red
rgb(255,0,0)


To select elements for style editing the element tag can be used directly.

p {

}

For HTML elements with id and class identifier.
use class selector
.className {
}

use ID selector
#idName {
}

To select elements in other cases:
tagA tagB 	select all the tagB in tagA.
tagA>tagB 	 select the tagB who is directly inside tagA(tagA is the parent of tagB)
tagA, tagB 	select both tagA and tagB.
tagName[attribute=value] 	select certain tag with certain attribute.
tagA#idName 		select the tag with id name idName that is placed inside tagA
tagA.className 	select the tag with class name className that is placed inside tagA
p:first selector


Link Colors

By default, a link will appear like this (in all browsers):
•	An unvisited link is underlined and blue
•	A visited link is underlined and purple
•	An active link is underlined and red
You can change the default colors, by using styles:


a:link {
    color: green;
    background-color: transparent;
    text-decoration: none;
}

a:visited {
    color: pink;
    background-color: transparent;
    text-decoration: none;
}

a:hover {
    color: red;
    background-color: transparent;
    text-decoration: underline;
}

a:active {
    color: yellow;
    background-color: transparent;
    text-decoration: underline;
}

a can be replaced be other element type.

the selector for screen size bigger that 481px		
@media only screen and (min-width: 481px) {
/* ---- tablet ---- minimum width 481px
*	style for tablet goes there
*/
}

the selector for screen size smaller that 480px			
@media only screen and (max-width: 480px) {
/* ---- cell phone ---- maximum width 480px
*	style for phone goes there
*/
}


should arrange from small to big;
/* Extra small devices (phones, 600px and down) */
@media only screen and (max-width: 600px) {...}

/* Small devices (portrait tablets and large phones, 600px and up) */
@media only screen and (min-width: 600px) {...}

/* Medium devices (landscape tablets, 768px and up) */
@media only screen and (min-width: 768px) {...}

/* Large devices (laptops/desktops, 992px and up) */
@media only screen and (min-width: 992px) {...}

/* Extra large devices (large laptops and desktops, 1200px and up) */
@media only screen and (min-width: 1200px) {...}

a HTML tag inside its body tag can be either block element or inline element.

A block-level element always starts on a new line and takes up the full width available (stretches out to the left and right as far as it can)

By default:
<address><article><aside><blockquote><canvas><dd><div><dl><dt><fieldset><figcaption><figure><footer><form><h1>-<h6><header><hr><li><main><nav><noscript><ol><p><pre><section><table><tfoot><ul><video>
are block elements.


An inline element does not start on a new line and only takes up as much width as necessary.


By default:
<a><abbr><acronym><b><bdo><big><br><button><cite><code><dfn><em><i><img><input><kbd><label><map><object><output><q><samp><script><select><small><span><strong><sub><sup><textarea><time><tt><var>
are inline elements.




CSS attributes

width:100px;
height:100px;
background-color:lightgrey;
border:3px solid black;
border-radius:5px;
float:left;
margin:10px;
font-size:80px;
text-align:center;
color:green;
padding:10px;
font-family:sans-serif;
background-color:rgb(128,0,0);
font-weight:bold;
margin:auto;
background-image: url("paper.gif");
background-color: #cccccc;
background-color: yellow;
color:  background-colorl
border-color: blue;
margin: top right bottom left;  ->  margin: 3px 3px 3px 3px;
margin-left:   	horizontal alignment
margin-top:
padding: top right bottom left;
padding-left:  
padding-top:
border: style color width;
text-decoration: none/underline  
text-align: left right or center
font-family: font-size:
font-weight: font-style:
text-decoration:bold;
vertical-align:middle;
color:rgb(0,128,0);

cursor: pointer / default

Control the alignment of an element.
float: left / right ;
overflow: auto;
clear: both;

opacity: 0.5;
list-style-type: none;
border-radius: size;
box-shadow: hor vert blur color;

transition: 5s ease;		this is used to make simple animation.

display : non/ inline / block /flex /grid / inline-grid		control the style of elements in a container.

The position property specifies the type of positioning method used for an element.
position: static(default) / relative / fixed / absolute / sticky		
static is default
relative is positioned relative to its normal position.
div.relative {
  position: relative;
  left: 30px;
  border: 3px solid #73AD21;
}
absolute is positioned relative to the nearest positioned ancestor(parent element that has any non-static position style.)
fixed is positioned relative to the viewport, which means it always stays in the same place even if the page is scrolled.
div.fixed {
  position: fixed;
  bottom: 0;
  right: 0;
  width: 300px;
  border: 3px solid #73AD21;
}


image auto sizing
img {
  width: 100%;
  height: auto;
}

CSS Reset Rule
It is used to override default browser styles. It is recommended so the website will have the same look on all browser.
* {
	margin: 0;
	border: 0;
	padding: 0;
	text-decoration: none;
	font-family: Arial, Helvetica, sans-serif;
}


https://css-tricks.com/snippets/css/a-guide-to-flexbox/


flex
Elements in the flex container will transform its length and width accordingly.

for the container
	flex-wrap: wrap is wrap the sections inside the container (default nowrap)
	justify-content: space-between, space-around,…. adjust wrap content horizontally.
	align-items:stretch(default). flex-start,center…..adjust wrap content vertically.
	flex-direction row row-reverse column column-reverse
for the sections inside
	flex-grow: the rate to grow
	flex-shrink; the rate to shrink
	flex-basis: the initial size
	flex: grow shrink basis(for short)

grid
display as a table of block elements, base on the current size of the browser.
for the container
	grid-gap, grid-row-gap, grid-column-gap the gap between the elements inside.
	grid-template indicating elements size
	rows / columns
	grid-template-rows: 200px 100px 300px or 2fr 1fr 3fr
	grid-template-columns: 30% 20% 50%
	justify-content: horizontal alignment.
	align-content: vertical alignment.
            grid-template-columns: auto auto;  
	grid-gap: 50px 100px;
for the item
	grid-column: 1 / span 3: starts at 1 span 3 (short for grid-column-start and end)
	grid-row: 1 / 5 start on line 1 and end on line 5



inline-grid
display as a table of inline elements


properties:
padding: value in px
flexDirection: "row" / "column" / "row-reverse" / "column-reverse"
justifyContent: "space-between"
alignItems: 'center'
flex: 1  // the ratio of the element compares to others in a contains.



height cannot use with 100% it is infinite, and acquired by the web app
