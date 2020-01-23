# HTML
The following notes follows the order of a standard HTML file.
Because HTML file runs from top to bottom.


Comment Tag
<!-- This is a comment -->
multiline comment, it is used to insert file and author information.


<!DOCTYPE html>
It indicates the document is a HTML file, usually placed in the first line.

html tag
<html>tag wrap everything inside a HTML document. It is composed of one head tag and one body tag.

head tag
<head>
the following tags are placed in the head tag

	<title>abc</title>
	title of the page shown in tab bar.

	<meta charset="UTF-8">
	charset usually set to UTF-8

	<meta name="viewport" content="width=device-width, initial-scale=1.0”>
	setting the screen for the web page to fit the device.

	<link rel="stylesheet" type="text/css" href=“mystyle.css">
	external style sheet link

	<link rel="stylesheet" href="css/example.css">		
	 style sheet link in css folder in short

	<link rel="stylesheet" type="text/css" href="print.css" media=“print">
	style used for printing

	<style></style> or <style type="text/css"></style>
	This tag can be used to include the css setting inside directly.

	<script src="demo_defer.js" defer></script>
	With defer attribute. A script that will not run until after the page has loaded.

	Viewport - part of the page that’s currently shown on-screen. The user may scroll to change the part of the page he sees, or zoom to change the size of the viewport.

	<meta name="viewport" content="width=320">–sets viewport width to be 320px
	<meta name="viewport" content="width=device-width">
	sets viewport width to be equal to the device width
	on Galaxy Nexus, screen is 720px, so viewport will now be 720px
	this is the recommended way
	<meta name="viewport" content="width=device-width, initial-scale=2">
	zoom in by a factor of 2
	<meta name="viewport" content="width=device-width, initial-scale=.5">
	zoom out by a factor of 2
	on Galaxy Nexus, screen is 720px, so viewport will be 360px
	<meta name="viewport" content="width=320, user-scalable=no">
	zooming is disable

<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

body tag
It contains main body of the website.

Attributes
body tag can contain a background attributes.
<body background="bgimage.jpg">


all Tags can have class and id.
The difference between an ID and a class is that an ID can be used to identify one element, whereas a class can be used to identify more than one.

<div class=“”> </div>
<div id=""> </div> 	id is more specific than class


all Tags can apply embedded CSS styles.
<tagname style=“property:value;"></tagname>


body tag can have following tags.

	<div>tag

	<p>tag		a paragraph

	<img src="images/lorem-ipsum.png" alt=“alternate text” height="" width="" >

	figure tag,	it can be used to contain a img tag with caption.
	<figure>
  	<img src="img_pulpit.jpg" alt="The Pulpit Rock" width="304" height="228">
	 <figcaption>Fig1. - A view of the pulpit rock in Norway.</figcaption>
	</figure>





	<h1> <h2> <h3> <h4><h5><h6> 	heading text

 	<br>	an empty line

	<hr> horizontal line

	<strong> <em>	Emphasized text

	<p><b></b></p>  b tag defines bold tag inside other tags.

	<pre>
	<blockquote>
	<cite>
	<sub>
	<sup>
	<a href="URL">Link-text goes here</a>
	<a href=“mailto:emailaddress">Text</a>
	<a href="URL" target="_blank">Link-text goes here</a> openlink in new tab



	<h1 id="tips">Tips Section</h1>
	<a href="#tips">Jump to the Tips Section</a>

	<ul>  <li>Item</li>  <li>Item</li></ul>     unordered list
	<ol>  <li>Item</li>  <li>Item</li></ol>    ordered list

	``&lt; &gt; &copy; &deg;`` 	entities, special symbols.
	&entity_name;OR&#entity_number;

	<span></span> it can be used to color a part of a text:
	<p>My mother has <span style="color:blue">blue</span> eyes.</p>

	<article>, <aside>, <footer>, <header>, or <nav>
	They represent the distinguish parts of the webpages.

	<detail><summary></summary></detail>
	The <summary> tag defines a visible heading inside the <details> element. The heading can be clicked to view/hide the details.

	<section>	it is used to represent a section within an article.

	<main>  the container for the pages core content. There must not be more than one 		
		<main> element in a document. The <main> element must NOT be a
		descendant of an <article>, <aside>, <footer>, <header>, or <nav> element.






table
This HTML tag makes tables.

attributes.
	summary This is a summary of the table, it can not be seen by the users.

caption
This tag is the caption for the table, it should be placed right after the table tag.
<table>
	<caption>…</caption>
	…
</table>


colgroup
	it is used to group columns for styling purpose. It should be after the caption tag.
<colgroup>
	<col id=“firstgroup”> <!- -This refers to the first column from left.- ->
	<col id=“secondgroup” span=“4”><!- -This refers to the columns 2,3,4,5 - ->
	<col id=“thirdgroup><!- - This refers to the sixth column.- ->
</colgroup>


thead, tbody, tfoot
	it is used to group rows in the table for styling purpose. The order matters.
tr
	They are the rows of the table. th and td tags are placed inside.
th  	
	header cell,  bold font by default.
td
	regular data cell

	Attributes
	rowspan, colspan
		They are used for spanning cells along different rows and columns.
<thead>
	<tr>
		<th>…</th>
		…
		<th colspan=“3”>…</th>
	</tr>
</thead>
<tbody>
	<tr>
		<td>…</td>
		…
		<td rowspan=“2”>…</td>
	</tr>
	<tr>
		…
	</tr >
</tbody>
<tfoot>
	…
</tfoot>



Form
This HTML tag makes forms.


<form id="login_form" method='post' action='game.php'>
            <h2 id="subtitle">Account Login</h2>
            <p id="mininote">New User? <a href="register.html">click here</a> to register</p>
            <!--This form has four fieldsets-->
            <fieldset>
                <legend>Enter your Nickname:</legend>
                <!--each section if the fieldset is set to flex type.-->
                <section>
                    <input type='text' id='username' name='username' placeholder='Username' required>
                </section>
            </fieldset>
            <fieldset>
                <legend>Enter your Password:</legend>
                <!--each section if the fieldset is set to flex type.-->
                <section>
                    <input type='password' id='password' name='password' placeholder='Password' required>
                </section>
            </fieldset>

            <input type='submit' value='Login & Start!'>
        </form>

	Attributes:
	method

For POST method, the form data is invisible to others. There is no limits for the input data. It also support advanced functionality like multi-part binary input. Hence, it is the preferred method.

For GET method, the input value are visible in the URL, the page can be bookmarked so the input data can also be saved. There is a 2000 characters limits for all information sent in the form.

URL like: result.php?row=$r&col=$c can be used to pass GET form info to the next page.

		POST the value for this attribute means sending data through HTTP transaction.
		GET the value for this attribute means sending data by appending it after URL.
		Appended after ? and separate data with $.
		Ex .com/index.php?name=value&name=value
	action
		the URL for form to submit. it can be any php file, even the current php file itself.


fieldset
	It is the boxes inside the form.
legend
	It is the title for the boxes.
input
	It gets users input.

	Attributes
	type=“
		password for getting masked text strings
		number and range for getting integers and floats
		url it validate url
		date or time(date format YYYY-MM-DD, time format HH:MM)
		color
		button
		hidden The content is not shown by the users. Hardcoded data is sent directly.
			When the form is submitted, the value also gets sent to the next page.
			the value can be retrieved from the input tag’s name attributes in PHP.
		text It provide an empty line for users.
		email It provide an empty line for users and it validate input as an email address.
		checkbox It provide small square checkbox for users to check.
		checkbox has additional attribute checked
		radio It provide small circle for users to select.
		submit
		It is a submit button. open the action file when complete if there is no action file,
		refresh the page.
		reset It is a reset button.
		”

	name
	value
	size = “5”
		The character size for the empty line.

	maxlength
		the max lengths for the input line.
	minlength the min lengths for the input line.
	placeholder
	max
	min
	step
	title
	required
	autofocus
	checked
select
	option tags are placed inside for users to select. A drop-down list.
	multiple multiple options can be selected

option
	selected It is the default value in the select tag.
	attributes
	<select><option value="" selected>
textarea
	It provides a block for users to input texts.
            <textarea>Enter something/<textarea>
	rows
		The height of the textarea
	cols
		The width of the textarea.

input, textarea
	placeholder It present a default input in grey color.
input, textarea, option
	value It is these input data a value when they are submitted.
input, textarea, select
	name It is the title for the input values when they are submitted.
label
	It is the tittle for items in the form.
	for
		Associate the label with the input items’ names in the form.

Canvas Tag

Media
audio, video
insert audio in the web page. multiple item can be place but they are executed from top. If the top line is not applicable then try the next line. text in the end when none of above work
	controls includes a control panel
	autoplay autoplay
	loop looping after it ends
	src provide the file location.
	width set the width of the item.
	source
		placed inside audio tag.
		src indicate the file location
		type audio/mpeg for mp3 files, audio/ogg for ogg files video/mp4 for mp4
	track
	for subtitles of the video
		label language label
		kind subtitles
		srclang source language
		src vtt file location


embed
placed inside audio tag or independently in embed form.
	src indicate the file location
	type audio/mpeg for mp3 files, audio/ogg for ogg files


<audio controls autoplay loop src="media/chopin.mp3">
		</audio>

		<audio controls>
			<source src="media/beethoven.mp3" type="audio/mpeg">
			<source src="media/beethoven.ogg" type="audio/ogg">
			<embed src="media/beethoven.mp3" type="audio/mpeg">
			Your browser does not support the audio element
		</audio>
		<p>Beethoven</p>

		<h2>Embed</h2>
		<embed src="media/chopin.mp3" type="audio/mpeg" autoplay="0">

		<h2>Video</h2>
		<video controls autoplay loop width="480">
			<source src="media/FransLanting_2014-light.mp4" type="video/mp4">
			<track label="English" kind="subtitles" srclang="en" src="media/franslanting.vtt">
		</video>

		<iframe width="560" height="315"
			src="https://www.youtube.com/embed/BgM_-0RgGAw"
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
			allowfullscreen>
		</iframe>


<img src="images/museumfloorplan.gif" alt="" width="500" height="300" usemap="#Map"/>
		  <map name="Map">
			<area shape="rect" coords="6,156,131,243" href="http://www.google.com" alt="Google">
			<area shape="circle" coords="388,64,62" href="http://www.yahoo.com" alt="Yahoo">
			<area shape="poly" coords="244,185,331,229,327,260,246,245,246,245" href="http://www.mohawkcollege.ca" alt="Mohawk College">
			<area shape = "default" href = "http://www.hamilton.ca" alt = "city of Hamilton">
		 </map>

		 <h2>Media</h2>

		 <h3>Audio</h3>

		 <h4>Audio Element</h4>

		 <audio controls>
			<source src = "media/chopin.mp3" type = "audio/mpeg">
			Your browser does not support the audio element
		 </audio>

		 <h4>Embed</h4>

		 <p>
			<embed src = "media/chopin.mp3" type = "audio/mpeg" autoplay = "false">
		 </p>

		 <h4>Audio with embed</h4>

		 <audio controls>
			<source src = "media/chopin.mp3" type = "audio/mpeg">
			<embed src = "media/chopin.mp3" type = "audio/mpeg">
			Your browser does not support the audio element
		 </audio>

		 <h3>Video</h3>

		 <h4>Video element</h4>

		 <video controls>
			<source src = "media/FransLanting_2014-light.mp4"
			width = "1000" height = "800" >
			Your browser does not support the video element
		 </video>

		 <h4>Embed</h4>

		 <p>
			<embed src = "media/FransLanting_2014-light.mp4"
			 autoplay = "false" >
		 </p>

		 <h4>YouTube</h4>
		 <!-- <iframe width="560" height="315" src="//www.youtube.com/embed/AmlEekTuAZI?list=UU4e0hMc3DMMdQ47dkoP0zVQ" frameborder="0" allowfullscreen></iframe>
		 -->

		 <object type = "application/x-shockwave-flash"
data = "http://www.youtube.com/v/FWFqJOJ2jqo?color2=FBE9EC&amp;version=3" controller = "controller" />
<param name = "movie" value = "http://www.youtube.com/v/FWFqJOJ2jqo?color2=FBE9EC&amp;version=3" />
<param name = "allowFullScreen" value = "true" />
<param name = "allowscriptaccess" value = "always" />

</object>
