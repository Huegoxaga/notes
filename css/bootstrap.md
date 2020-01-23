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
```HTML
<!-- In <head> tag-->
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
<!-- At the end of the <body> tag-->
<script src="https://code.jquery.com/jquery-3.3.1.min.js" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
```
* Or, [Download](https://getbootstrap.com/docs/4.4/getting-started/download/) ready-to-use compiled code.

## Containers
* Bootstrap contents, including grid systems, require a containing element: ``<div class=“container”> ... </div>``
* Bootstrap containers can be either fixed with (as above) or fluid: ``<div class=“container-fluid”> ... </div>``
  * Fluid width containers won’t necessarily stack, columns will just get smaller.


## Grid System
* A responsive grid system that scales up to 12 columns of information to the appropriate device size.
* There are two types of classes, ``row`` class contains multiple ``col`` class items in one row.
* Pre-defined grid classes like ``.col-lg`` let us quickly make grid layout sizes. ``.col-xs-4`` indicates the column using this class will span 4 of the 12 column.
* [Click](https://getbootstrap.com/docs/4.1/layout/grid/) to see more.


## Predefined Components
* [Click](https://getbootstrap.com/docs/4.4/components/alerts/) to see full docs.
* Typically a set of CSS classes, maybe supported by JavaScript code, along with associated expectations around how they are to be used in HTML tags.

## Utilities
* They provide shortcuts for styling web components. For example: margin, border, height, width.
* [Click](https://getbootstrap.com/docs/4.4/utilities/borders/) to see details.
