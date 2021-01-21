# HTML

## Introduction

- Hypertext Markup Language (HTML) is the standard markup language for documents designed to be displayed in a web browser.
- HTML file runs from top to bottom.

## Comment Tag

- `<!-- This is a multiline comment -->`

## `<!DOCTYPE html>`

It indicates the document is a HTML file, usually placed in the very first line.

## `html` Tag

- <html>tag wrap everything inside a HTML document. It is composed of one head tag and one body tag.

## `head` Tag

- `<head> </head>` It stores the basic information about the web page.
- the following tags are placed in the head tag

### `title` tag

- `<title>abc</title>`
- title of the page shown in tab bar.

### `meta` tag

- `<meta charset="UTF-8">`, charset usually set to UTF-8
- Viewport info - part of the page that’s currently shown on-screen. The user may scroll to change the part of the page he sees, or zoom to change the size of the viewport.
  _ `<meta name="viewport" content="width=device-width, initial-scale=1.0">` setting the screen for the web page to fit the device.
  _ `<meta name="viewport" content="width=320">`–sets viewport width to be 320px.
  _ `<meta name="viewport" content="width=device-width, initial-scale=2">` zoom in by a factor of 2
  _ `<meta name="viewport" content="width=device-width, initial-scale=.5">` zoom out by a factor of 2
  _ `<meta name="viewport" content="width=320, user-scalable=no">`zooming is disable
  _ `<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">` shrinking is disabled.
- `<meta name="theme-color" content="#000000" />` provides an app theme color for apps works as Progressive Web Apps
  - Progressive Web Apps are web apps that use emerging web browser APIs and features along with traditional progressive enhancement strategy to bring a native app-like user experience to cross-platform web applications
- `<meta name="description" content="Web site created using create-react-app" />` The meta description tag in HTML is the 160 character snippet used to summarize a web page’s content.
  - Search engines sometimes use these snippets in search results to let visitors know what a page is about before they click on it

### Link Tag

- Import files use the link tag externally.
- `<link rel="stylesheet" type="text/css" href="mystyle.css">` or `<link rel="stylesheet" href="css/example.css">` \* external style sheet link
- `<link rel="stylesheet" type="text/css" href="print.css" media="print">` style used for printing
- `<link rel="apple-touch-icon" href="" />` specify the path of a `57 x 57` png file when the web app is added to the home screen of an Apple device. [Click Here](https://developer.apple.com/library/archive/documentation/AppleApplications/Reference/SafariWebContent/ConfiguringWebApplications/ConfiguringWebApplications.html) to see more info about Apple device web app launch screen and more
- `<link rel="manifest" href="/manifest.webmanifest">`
  - The purpose of the manifest is to install web applications to the homescreen of a device(it process is called supporting Progressive Web Apps), providing users with quicker access and a richer experience
  - The web app manifest provides information about an application (such as name, author, icon, and description) in a JSON text file.
  - The link tag loads to the `manifest.json`
- Different stylesheets can associate with different media, in the following external CSS style:
  ```html
  <!-- css for screen size <= 600px -->
  <link
    rel="stylesheet"
    media="screen and (max-width: 600px)"
    href="smallscreen.css"
  />
  <!-- css for screen size >= 900px -->
  <link
    rel="stylesheet"
    media="screen and (min-width: 900px)"
    href="widescreen.css"
  />
  ```

### Style Tag

- Place Css content inside the style tag.
- `<style></style>` or `<style type="text/css"></style>`.

### Script Tag

- Import JavaScript file into the HTML file.
- `<script src="demo_defer.js" defer></script>`
  - With defer attribute. A script that will not run until after the page has loaded.
- The `async` attribute is a boolean attribute.
  - The async attribute is only for external scripts (and should only be used if the src attribute is present).
  - When present, it specifies that the script will be executed asynchronously as soon as it is available.
    - If async is present: The script is executed asynchronously with the rest of the page (the script will be executed while the page continues the parsing)
    - If async is not present and defer is present: The script is executed when the page has finished parsing
    - If neither async or defer is present: The script is fetched and executed immediately, before the browser continues parsing the page

## `body` tag

- It contains main content of the website.

### Attributes

- body tag can contain a background attributes.
- `<body background="bgimage.jpg">`

### Class and ID

- all Tags can have class and id.

```html
<div class=""></div>
<div id=""></div>
```

- The difference between an ID and a class is that an ID can be used to identify one element, whereas a class can be used to identify more than one. ID is more specific than class

### Inline Styling

- all Tags can apply embedded CSS styles.
- `<tagname style="property:value;"></tagname>`

### HTML Tags

- body tag can have following tags.

#### HTML Block

- `<div></div>` a container.
- The following tags represent the distinguish parts of the webpages. \* `<article>, <aside>, <footer>, <header>, or <nav>`
- `<section></section>` a section within an article.
- The following tags represent the distinguish parts of the webpages. \* `<article>, <aside>, <footer>, <header>, or <nav>`
- `<summary>` tag defines a visible heading inside the <details> element. The heading can be clicked to view/hide the details. `<detail><summary></summary></detail>`
- `<main>` the container for the pages core content. There must not be more than one \* The <main> element must NOT be a descendant of an `<article><aside><footer><header><nav>` element.

#### Paragraphs

- every `p` tag will starts at a new line.

#### images

- `<img src="images/lorem-ipsum.png" alt="alternate text" height="" width="" >`

#### Figure and Caption

- it can be used to contain an img tag with caption.
  `html <figure> <img src="img_pulpit.jpg" alt="The Pulpit Rock" width="304" height="228"> <figcaption>Fig1. - A view of the pulpit rock in Norway.</figcaption> </figure>`

#### Heading Text

- `<h1><h2><h3><h4><h5><h6></h6></h5></h4></h3></h2></h1>`

#### Empty Line

- `<br>`

#### Horizontal Line

- `<hr>`

#### Emphasized text

- `<strong></string>`
- `<em></em>`
- `<p><b></b></p>` b tag defines bold tag inside other tags.

#### Other Text Tags

- `<pre></pre>`, it defines preformatted text. The text will be displayed exactly as written in the HTML source code
- `<blockquote></blockquote>`
- `<cite></cite>`
- `<sub></sub>`
- `<sup></sup>`

#### Links

- `<a href="URL">Link-text goes here</a>`
- `<a href="mailto:emailaddress">Text</a>` email link
- `<a href="URL" target="_blank">Link-text goes here</a>` openlink in new tab
  - use attribute `rel="noreferrer noopener"` in order to conceal infomation during redirection and add a layer of security
- `<a href="URL" download="filename">Link-text goes here</a>` The download attribute specifies that the target will be downloaded when a user clicks on the hyperlink
  - The optional value of the download attribute will be the new name of the file after it is downloaded
  - `<a href="URL" download>Link-text goes here</a>` If the value is omitted, the original filename is used
- Anchor Links
  ```html
  <h1 id="tips">Tips Section</h1>
  <a href="#tips">Jump to the Tips Section</a>
  ```

#### Lists

- unordered list

````html
<ul>
  <li>Item</li>
  <li>Item</li>
</ul>
``` * ordered list ```html
<ol>
  <li>Item</li>
  <li>Item</li>
</ol>
````

#### special symbols

- `&lt; &gt; &copy; &deg;` for &lt; &gt; &copy; &deg;
- Using the following syntax.`&entity_name;OR&#entity_number;`

#### Span

- `<span></span>` it can be used to decorate a part of a text:
- `<p>My mother has <span style="color:blue">blue</span> eyes.</p>`

#### Tables

- Attributes:
  _ `summary` This is a summary of the table, it can not be seen by the users.
  _ `caption` This tag is the caption for the table, it should be placed right after the table tag.
  `html <table> <caption></caption> </table>`
- `colgroup` Tags: \* It is used to group columns for styling purpose. It should be after the caption tag.
  `html <colgroup> <col id="firstgroup"> <!--This refers to the first column from left.--> <col id="secondgroup" span="4"><!--This refers to the columns 2,3,4,5 --> <col id="thirdgroup"> <!-- This refers to the sixth column.--> </colgroup>`
- `thead`, `tbody`, `tfoot` tags: \* It is used to group rows in the table for styling purpose. The order matters.
- `tr` tags:
  _ They are the rows of the table. `th` and `td` tags are placed inside.
  _ th tags
  _ header cell, bold font by default.
  _ td tags
  _ regular data cell
  _ Attributes - rowspan, colspan. They are used for spanning cells along different rows and columns.
  `html <thead> <tr> <th>…</th> … <th colspan="3">…</th> </tr> </thead> <tbody> <tr> <td>…</td> … <td rowspan="2">…</td> </tr> <tr> … </tr > </tbody> <tfoot> … </tfoot>`

#### Forms

- Example:

```html
<form id="login_form" method="post" action="game.php">
  <h2 id="subtitle">Account Login</h2>
  <p id="mininote">
    New User? <a href="register.html">click here</a> to register
  </p>
  <!--This form has four fieldsets-->
  <fieldset>
    <legend>Enter your Nickname:</legend>
    <!--each section if the fieldset is set to flex type.-->
    <section>
      <input
        type="text"
        id="username"
        name="username"
        placeholder="Username"
        required
      />
    </section>
  </fieldset>
  <fieldset>
    <legend>Enter your Password:</legend>
    <!--each section if the fieldset is set to flex type.-->
    <section>
      <input
        type="password"
        id="password"
        name="password"
        placeholder="Password"
        required
      />
    </section>
  </fieldset>
  <input type="submit" value="Login & Start!" />
</form>
```

```html
<form>
  <label for="fname">First name:</label><br />
  <input type="text" id="fname" name="fname" /><br />
  <label for="lname">Last name:</label><br />
  <input type="text" id="lname" name="lname" />
</form>
```

- Form Attributes:
  _ `method`
  _ For POST method, the form data is invisible to others. There is no limits for the input data. It also support advanced functionality like multi-part binary input. Hence, it is the preferred method.
  _ The value for this attribute means sending data sent through HTTP transaction.
  _ For GET method, the input value are visible in the URL, the page can be bookmarked so the input data can also be saved. There is a 2000 characters limits for all information sent in the form.
  _ GET the value for this attribute means sending data by appending it after URL.
  Appended after ? and separate data with \$.
  _ Ex: `index.php?name=value&name=value`
  _ `action`
  _ the file location for the form to submit. \* URL like: `result.php?row=$r&col=$c` can be used to pass GET form info to the next page.
- fieldset \* It is the boxes inside the form.
- legend \* It is the title for the boxes.
- input
  _ It gets users input.
  _ Attributes
  _ `type`
  _ `password` for getting masked text strings
  _ `number` and range for getting integers and floats
  _ max
  _ min
  _ step
  _ `url` it validate url
  _ `date` or time(date format YYYY-MM-DD, time format HH:MM)
  _ `color`
  _ `button`
  _ `text` It provide an empty line for users.
  _ `email` It provide an empty line for users and it validate input as an email address.
  _ `checkbox` It provide small square checkbox for users to check.
  _ `checkbox` has additional attribute `checked`
  _ `radio` It provide small circle for users to select.
  _ `submit` It is a submit button. open the action file when complete if there is no action file, refresh the page.
  `reset` It is a reset button.
  _ `hidden` The content is not shown by the users. Hardcoded data is sent directly. When the form is submitted, the value also gets sent to the next page.
  _ `name` the value can be retrieved from the input tag’s name attributes in PHP.
  _ `value` the value of the input.
  _ `size = "5"` The character size for the empty line.
  _ `maxlength` the max lengths for the input line.
  _ `minlength` the min lengths for the input line.
  _ `placeholder` place holder of the input.
  _ `title`
  _ `required` the input is required for validation.
  _ `autofocus`
- `select` A drop-down list.
  _ `option` tags are placed inside for users to select.
  _ `multiple` multiple options can be selected \* `selected` It is the default value in the select tag.
- `textarea` It provides a block for users to input texts. `<textarea>Enter something</textarea>`
  _ `rows` The height of the textarea
  _ `cols` The width of the textarea.
  _ `placeholder` It present a default input in grey color.
  _ `value` It is these input data a value when they are submitted. \* `name` It is the title for the input values when they are submitted.
- `label` It is the title for items in the form. \* `for`Associate the label with the input items’ names in the form.

#### Canvas Tag

#### Media

- Audio and Video Tag
  _ Attributes
  _ `controls` includes a control panel
  _ `autoplay` autoplay
  _ `loop` looping after it ends
  _ `src` provide the file location.
  _ Ex: `<audio controls autoplay loop src="media/chopin.mp3"></audio>`
  _ `width` set the width of the item.
  _ `type` `audio/mpeg` for mp3 files, `audio/ogg` for ogg files, `video/mp4` for mp4.
  _ For Video tag, `poster` specifies an image to be shown while the video is downloading, or until the user hits the play button
  _ embed styles
  `HTML <p> <embed src = "media/chopin.mp3" type = "audio/mpeg" autoplay = "false"> </p> <p> <embed src = "media/example.mp4" autoplay = "false" > </p>`
  _ Source Tags
  _ Audio or Video Tags can have a source tag inside.
  _ It has `src` and `type` attributes.
  _ insert audio in the web page. multiple item can be place but they are executed from top. If the top line is not applicable then try the next line. text in the end when none of above work
  `html <audio controls> <source src="media/beethoven.mp3" type="audio/mpeg"> <source src="media/beethoven.ogg" type="audio/ogg"> <embed src="media/beethoven.mp3" type="audio/mpeg"> Your browser does not support the audio element </audio>`
  _ `track` tag
  _ Videos can have track tag, can host subtitles.
  `html <video controls autoplay loop width="480"> <source src="media/FransLanting_2014-light.mp4" type="video/mp4"> <source src = "media/FransLanting_2014-light.mp4" width = "1000" height = "800" > <track label="English" kind="subtitles" srclang="en" src="media/franslanting.vtt"> </video>`
  _ Attributes:
  _ `label` language label,
  _ `kind` set to `subtitles`
  _ `srclang` source language type. \* `src` vtt file location
- iFrame

```html
<iframe
  width="560"
  height="315"
  src=""
  allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
  allowfullscreen
>
</iframe>
* Youtube videos can auto generate iframe elements.
```

- Interactive Maps

```html
<img src="images/example.gif" alt="" width="500" height="300" usemap="#Map" />
<map name="Map">
  <area
    shape="rect"
    coords="6,156,131,243"
    href="http://www.google.com"
    alt="Google"
  />
  <area
    shape="circle"
    coords="388,64,62"
    href="http://www.yahoo.com"
    alt="Yahoo"
  />
  <area
    shape="poly"
    coords="244,185,331,229,327,260,246,245,246,245"
    href="link"
    alt="Alt Text"
  />
  <area shape="default" href="url" alt="alt text" />
</map>
```

- `object` Tags

```html
<object type = "application/x-shockwave-flash"
data = "url" controller = "controller" />
<param name = "movie" value = "url" />
<param name = "allowFullScreen" value = "true" />
<param name = "allowscriptaccess" value = "always" />
</object>
```
