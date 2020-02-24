# CSS

## Introduction
* CSS - Cascading Style Sheets is a style sheet language used for describing the presentation of a document written in a markup language like HTML.
* A CSS file ends with ``.css``.


## Syntax
```css
selector {
  propertyName: Value;
  /*... more */
}
```

## Comments
* It supports multiline comments ``/* abc */``.

## Implementation

### Inline CSS
```html
<p style = "color: blue;"> this is the blue text </p>
```
### Embedded or Internal CSS
```html
<style>
  p {color: blue;
    }
</style>
```
* The style tag is placed inside the head tag of the HTML file.

### External CSS
```html
<link href="style.css" rel="stylesheet" />
```
* place the link tag inside the head tag of the HTML file.


## Units
* For width and height:
  * ``pt`` point
  * ``px`` pixel
  * ``%`` percentage
  * ``cm`` centimeter
  * ``mm``	millimeter Try it
  * ``in`` inch
  * ``vw`` Relative to 1% of the width of the viewport
  * ``vh`` Relative to 1% of the height of the viewport
* For font size:
  * ``em`` 1em is 100%, relate to the current font size.
* For color:
  * ``#ff0000`` HEX color
  * ``red`` color in plain words
  * ``rgb(255,0,0)`` RGB

## Override Rules
* add ``!important`` at the end of the attribute value to make it overrides other rules.
* Ex, ``border-width: 5px !important;``.

## Selector
* To select elements for style editing the element tag can be used directly.
```css
p {
}
```
* For HTML elements with class identifier.
```css
.className {
}
```
* For HTML elements with id identifier.
```css
#idName {
}
```
* Use a combination of tag, id, and class selectors.
  * ``tagA tagB`` select all the tagB in tagA.
  * ``tagA>tagB`` select the tagB who is directly inside tagA(tagA is the parent of tagB)
  * ``tagA, tagB`` select both tagA and tagB.
  * ``tagName[attribute=value]`` select certain tag with certain attribute.
  * ``tagA#idName`` select the tag with id name idName that is placed inside tagA
  * ``tagA.className`` select the tag with class name className that is placed inside tagA.
  * ``p:first-child`` Selects every ``<p>`` element that is the first child of its parent.
  * ``p:last-child`` Selects every ``<p>`` element that is the last child of its parent.
  * ``p:nth-child(2)`` Selects every ``<p>`` element that is the second child of its parent.
  * ``*`` Select all tags inside the html body.
* Link Colors
  * By default, a link will appear like this (in all browsers):
    *	An unvisited link is underlined and blue
    *	A visited link is underlined and purple
    *	An active link is underlined and red
  * The default colors can be changed, by using styles:
  ```css
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
  ```
    * ``a`` can be replaced be other tag.

## Responsive Design
* It can be done by using a special selector for different screen size.
  * should arrange from small to big.
  ```css
  /* Extra small devices (phones, 600px and down) */
  @media only screen and (max-width: 600px) {}
  /* Small devices (portrait tablets and large phones, 600px and up) */
  @media only screen and (min-width: 600px) {}
  /* Medium devices (landscape tablets, 768px and up) */
  @media only screen and (min-width: 768px) {}
  /* Large devices (laptops/desktops, 992px and up) */
  @media only screen and (min-width: 992px) {}
  /* Extra large devices (large laptops and desktops, 1200px and up) */
  @media only screen and (min-width: 1200px) {}
  ```
  * Media Features, structures like ``(min-width: 1200px)`` are known as media features, there are many others.
    * ``max-height``
    * ``min-height``
  * Media Types, the keyword screen in the example can be replaced by the following Media Types.
    * ``all``	Default. Used for all media type devices
    * ``print``	Used for printers
    * ``screen``	Used for computer screens, tablets, smart-phones etc.
    * ``speech``	Used for screenreaders that "reads" the page out loud
  * The keyword ``only`` can be replaced by other keywords like:
    * ``and`` it is used to combine media types and media Features.
    * ``not`` not mediaType the Styling will not work on the mediaType that follows.
    * ``only``

## CSS Reset Rule
* It is used to override default browser styles. It is recommended so the website will have the same look on all browser.
* The following block of css rules is usually used.
```css
* {
	margin: 0;
	border: 0;
	padding: 0;
	text-decoration: none;
	font-family: Arial, Helvetica, sans-serif;
}
```

## CSS attributes
### Sizing and Spacing
```css
.Sizing {
  width:100px;
  /* height cannot use with 100% it is infinite, and acquired by the web app */
  height:100px;
  font-size:80px;
  margin:10px;
  margin:auto;
  padding:10px;
  margin-left: 5px;
  margin-top: 5px;
  padding-left: 5px;
  padding-top: 5px;
  /* margin: top right bottom left;  */
  margin: 3px 3px 3px 3px;
  /* padding: top right bottom left; */
  padding: 2px 3px 4px 5px;
}
/* image auto sizing */
img {
  width: 100%;
  height: auto;
}
```
### Alignment
```css
.alignment {
  float: left;
  text-align: center;
  overflow: auto;
  clear: both;
}
```
### Coloring
```css
.coloring {
  background-color:lightgrey;
  background-color: RGB(128,0,0);
  background-image: url("paper.gif");
  background-color: #cccccc;
  background-color: yellow;
  color: red;
  color: green;
  border-color: blue;
  vertical-align:middle;
  opacity: 0.5;
}
```
### Decoration
```css
.decoration {
  font-weight:bold;
  font-family:sans-serif;
  border:3px solid black;
  border-radius:5px;
  text-decoration: none;
  text-decoration: underline;
  text-align: left;
  text-align: right;
  text-align: center;
  font-weight: 300;
  text-decoration: underline;
  text-transform: lowercase;
  cursor: pointer;
  cursor: default;
  list-style-type: none;
  /* horizontal vertical color */
  box-shadow: 5px 10px #888888;
  /* simple animation */
  transition: 5s ease;
  transition: width 2s, height 4s;
  background: url(../img/img.jpg) no-repeat right top
}
```
### Positioning
```css
.positioning {
  position: static;	/* Default */
  position: relative;	/* positioned relative to its normal position. */
  position: fixed; /* positioned relative to the viewport, even if the page is scrolled. */
  position: absolute; /* positioned relative to the parent element that has any non-static position style. */
  position: sticky;
  div.fixedClass {
    position: fixed;
    bottom: 0;
    right: 0;
    width: 300px;
    border: 3px solid #73AD21;
  }
}
```

## Display Property
* The display property specifies the display behavior
* a HTML tag inside its body tag can be either block element or inline element by default.

### Block Elements
* A block-level element always starts on a new line and takes up the full width available (stretches out to the left and right as far as it can)
* By default, the following tags are block elements.
```html
<address><article><aside><blockquote><canvas><dd><div><dl><dt><fieldset>
<figcaption><figure><footer><form><h1><h6><header><hr><li><main><nav>
<noscript><ol><p><pre><section><table><tfoot><ul><video>
```
* An element can be explicitly set to block element by using ``display : block``.
### Inline Elements
* An inline element does not start on a new line and only takes up as much width as necessary.
* By default, the following tags are inline elements.
```xml
<a><abbr><acronym><b><bdo><big><br><button><cite><code><dfn><em><i><img>
<input><kbd><label><map><object><output><q><samp><script><select><small>
<span><strong><sub><sup><textarea><time><tt><var>
```
* An element can be explicitly set to inline element by using ``display : inline``.
### Inline block
* An inline element that can apply height and width values to it.
* set by using ``display : inline-block``
### Flex
* Elements in the flex container will transform its length and width accordingly.
* set by using ``display : flex``.
* for the flex container
```css
.container{
  /*  allow the items to wrap as needed with this property, default nowrap */
  flex-wrap: wrap;
  flex-wrap: wrap-reverse;
  /* adjust wrap content horizontally, default flex-start  */
  justify-content: space-between;
  justify-content: space-around;
  justify-content: center;
  justify-content: flex-end;
  /* adjust wrap content vertically, default stretch */
  align-items:flex-start;
  align-items: center;
  /* control the arrangement of the flex boxes in vertical or horizontal direction. */
  flex-direction: row;
  flex-direction: row-reverse;
  flex-direction: column;
  flex-direction: column-reverse;
  /* aligns a flex container's lines within when there is extra space in the cross-axis, default stretch */
  align-content: flex-start;
  align-content: flex-end;
  align-content: space-around;
  align-content: center;
}
```
* for the sections inside flex container
```css
.childItems {
  /* the rate for size change relative to other elements */
  flex-grow: 1;
	flex-shrink: 1;
  /* the initial size */
	flex-basis: 1;
  /* flex: grow shrink basis for short; */
	flex: 1 1 1;
  min-width: 5px;
  /* items with lower order number comes first */
  order: -1;
}
```
### Grid
* display as a table of block elements, base on the current size of the browser.
* set by using ``display : grid``.
* for the container
```css
.container{
  grid-row-gap: 50px;
  grid-column-gap: 50px;
  /* shorthand property for the grid-column-gap and the grid-row-gap properties */
  grid-gap: 50px 50px;
  /* Make a grid with 4 columns */
  grid-template-columns: auto auto auto auto;
  grid-template-columns: 80px 200px auto 40px;
  grid-template-rows: 2fr 1fr 3fr;
  grid-template-columns: 30% 20% 50%;
  /* vertical alignment relative to the grid container */
  align-content: center;
  align-content: space-around;
  align-content: space-between;
  align-content: start;
  align-content: end;
  /* horizontal alignment relative to the grid container */
  justify-content: space-evenly;
  justify-content: space-between;
  justify-content: start;
  justify-content: end;
  /* horizontal alignment for all items inside grid container, default stretch */
  justify-items: start;
  justify-items: end;
  justify-items: center;
  justify-items: stretch;
  /* vertical alignment for all items inside grid container, default stretch */
  align-items: start;
  align-items: end;
  align-items: center;
  align-items: stretch;
}
```
* for the item
```css
.childItems {
  /* Place a grid item at column line 1, and let it end on column line 3: */
  grid-column-start: 1;
  grid-column-end: 3;
  /* Make the item start on column 1 and end before column 5 */
  grid-column: 1 / 5;
  /* Make "item1" start on column 1 and span 3 columns */
  grid-column: 1 / span 3;
  /* Place a grid item at row line 1, and let it end on row line 3 */
  grid-row-start: 1;
  grid-row-end: 3;
  /* Make the item start on row 1 and end before row 5 */
  grid-row: 1 / 5
  /* shorthand property for the grid-row-start, grid-column-start, grid-row-end and the grid-column-end properties. */
  grid-area: 1 / 2 / 5 / 6;
  /* start on row-line 2 and column-line 1, and span 2 rows and 3 columns */
  grid-area: 2 / 1 / span 2 / span 3;
}
```

### Inline Grid
* display as a table of inline elements
* set by using ``display : inline-grid``.
