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


## Breakpoints
* Most utilities works with breakpoints. It attach the utility settings with specific screen size, and make the design responsive.
* Every single breakpoint for the utilities allows the setting to take effect on screen that is wider than the breakpoint size.
* By default, the breakpoint represents the following screen size.
  * ``xl``, > 1200px.
  * ``lg``, > 992px.
  * ``md``, > 768px.
  * ``sm``, > 576px.
  * If no breakpoint is specified, the ultilty will work on all screen size greater than 0px. This can be seen as ``xs``.


## Grid System
* A responsive grid system that scales up to 12 columns of information to the appropriate device size.
* It works with breakpoints.
* There are two types of classes, ``row`` class contains multiple ``col`` class items in one row.
* Pre-defined grid classes like ``col`` let us quickly make grid layout sizes. ``.col-4`` indicates the column using this class will span 4 of the 12 column.
* [Click](https://getbootstrap.com/docs/4.1/layout/grid/) to see more.


## Predefined Components
* [Click](https://getbootstrap.com/docs/4.4/components/alerts/) to see full docs.
* Typically a set of CSS classes, maybe supported by JavaScript code, along with associated expectations around how they are to be used in HTML tags.
* Classes for the following tags are listed as follows.
### ``img`` Tags
* ``rounded`` a rounded corner.
* ``rounded-circle``
* ``img-thumbnail`` bordered images.
* ``float-left``
* ``float-right``
* ``mx-auto d-block`` centered as a block element.
* ``img-fluid`` responsive images with 100 width and auto height.
### ``table`` Tags
* ``table`` add basic styling for a table.
* ``table-striped`` add zebra-stripes.
* ``table-bordered``
* ``table-hover``
* ``table-dark``
* ``table-borderless``
* ``table-sm`` table with smaller padding.
* ``table-responsive`` when screen less than 992px, add a horizontal scroll bar.
* For adding colors for ``table``, ``row`` and ``thead``, see [here](https://getbootstrap.com/docs/4.0/content/tables/#contextual-classes).
  * For ``thead``, there are ``thead-dark`` and ``thead-light``.

## Utilities
* They provide shortcuts for styling web components. For example: margin, border, height, width.
* [Click](https://getbootstrap.com/docs/4.4/utilities/borders/) to see details.
* If one component needs two or more utility classes, separate them by an empty space.


### Display
* has classes as ``.d-values``.
* works with breakpoints.
* change the breakpoint value to ``print`` to apply the display setting when printing.
* The value can have the following options.
  * ``none``, hidden
    * ``d-none d-md-block d-xl-none`` This will show the element on ``md`` screen only.
  * ``inline``
  * ``inline-block``
  * ``block``
  * ``table``
  * ``table-cell``
  * ``table-row``
  * ``flex``
  * ``inline-flex``

### Sizing
* ``w`` for width, ``h``for height, ``mw`` for max width, ``mh`` for max height.
* not all number works, mainly 25, 50, 75, 100.
```HTML
<div class="w-25" style="background-color: #eee;">Width 25%</div>
```
### Spacing
* The classes are named using the format {property}{sides}-{size} for xs and {property}{sides}-{breakpoint}-{size} for sm, md, lg, and xl.
* For example, ``m-2``, ``mb-3`` means margin-botton at level 5.
* Where property is one of:
  * ``m`` - for classes that set margin
  * ``p`` - for classes that set padding
* Where sides is one of:
  * ``t`` - for classes that set ``margin-top`` or ``padding-top``
  * ``b`` - for classes that set ``margin-bottom`` or ``padding-bottom``
  * ``l`` - for classes that set ``margin-left`` or ``padding-left``
  * ``r`` - for classes that set ``margin-right`` or ``padding-right``
  * ``x`` - for classes that set both ``*-left`` and ``*-right``
  * ``y`` - for classes that set both ``*-top`` and ``*-bottom``
  * ``blank`` - for classes that set a margin or padding on all 4 sides of the element
* Where size is one of:
  * ``0`` - for classes that eliminate the margin or padding by setting it to 0
  * ``1`` - (by default) for classes that set the margin or padding to $spacer * .25
  * ``2`` - (by default) for classes that set the margin or padding to $spacer * .5
  * ``3`` - (by default) for classes that set the margin or padding to $spacer
  * ``4`` - (by default) for classes that set the margin or padding to $spacer * 1.5
  * ``5`` - (by default) for classes that set the margin or padding to $spacer * 3
  * ``auto`` - for classes that set the margin to auto

### Border
* ``border`` 1px width border.
* ``border-top-0`` border that has no top border.
* ``rounded`` rounded border.
* ``rounded-sm`` rounded on small screen.
* ``rounded-circle`` circular border.
* ``rounded-0`` not rounded border.
* ``border-primary`` border color, [see](https://getbootstrap.com/docs/4.4/utilities/borders/#border-color) for a full list.
### Embed
* Works for ``<iframe>``, ``<embed>``, ``<video>``, and ``<object>``
* Make tags responsive with certain aspect ration.
* ``embed-responsive`` class and ``embed-responsive-16by9`` class should be used for the container of the embed type tags.
* ``16by9`` can be replaced by the following default aspect ratios.
  * ``21by9``
  * ``16by9``
  * ``4by3``
  * ``1by1``
* Each embed tags are suggested to have a ``embed-responsive-item`` class.
* Example:
```html
<div class="embed-responsive embed-responsive-4by3">
  <iframe class="embed-responsive-item" src="..."></iframe>
</div>
```
