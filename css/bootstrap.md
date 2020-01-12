# Bootstrap

## Introduction
* It is a Front-end framework
* Developed at Twitter in 2011.
* It has css libraries with predefined classes.
* It contains JavaScript-based design templates for typography, forms, buttons, navigation and other interface component.
* It makes responsive website easily on all major browsers.
* [Click](https://getbootstrap.com/docs/4.3/getting-started/introduction/) to see documents
* Bootstrap 4 is the current version in 2020.


## Setup
There are many options:
* In project folder, run ``npm i bootstrap`` to get the modules.
* Or, Use CDN link in script tag with jQuery, popper.js, bootstrap.js and font files.
* Or, Download ready-to-use compiled code.

## Grid System
A responsive grid system that scales up to 12 columns of information to the appropriate device size
A row is used to define a horizontal group of columns
Content is places inside the columns•Only columns may be immediate children of rows
Pre-defined grid classes like .col-xs-4 let us quickly make grid layouts, but we can customize our own
The 4 part of the pre-defined class tell us that the column using this class will span 4 of the 12 column

## Containers
Bootstrap contents, including grid systems, require a containing element:•<div class=“container”> ... </div>
Bootstrap containers can be either fixed with (as above) or fluid:
<div class=“container-fluid”> ... </div>
Fluid width containers won’t necessarily stack, columns will just get smaller.

## predefined components
https://getbootstrap.com/docs/4.4/components/alerts/
Typically a set of CSS classes, maybe supported by JavaScript code, along with associated expectations around how they are to be used in HTML tags•E.g.: drop-down lists, navigation bars, pagination•Extensive example code and tutorials make it easy to integrate into our own applications

page-header
m-2 margin 2
badge
badge-primary
btn
btn-secondary
btn-sm
btn-lg
btn-default
btn-info    change color
btn-success    change color
btn-danger    change color
