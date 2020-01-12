# ASP.NET

## Background

* ASP
  * Active Server Pages released by Microsoft in 1996
  * A technology for generating dynamic web pages
  * A mixture of HTML tags, ASP tags and VBscript
  * Pages were interpreted at run time and HTML was rendered and delivered to client
  * Often referred to as “Classic” ASP

* ASP.NET
  * It belongs to the .NET Framework.
  * Improved from ASP. A complete re-design, released in 2002.
  * It makes use of .NET Framework  
  * ASP.NET is a framework to develop web applications and web services
  * It has many supported languages and tools, main languages include C#, VB.NET and JavaScript, Perl, Python, Ruby.


* ASP.NET Core
  * It belongs to the .NET Core.
  * Open source, cross platform framework released in 2016
  * Can develop and run on Windows, macOS or Linux
  * Higher performance than ASP.NET
  * Core has fewer features than "Full" ASP.NET Framework, but will catch up in the future.



* Version History
  * ASP.NET 1.0 – 2002
  * ASP.NET 2.0 – 2005
    * Master pages (Templates)
  * ASP.NET 3.0 – 2006
  * ASP.NET 3.5 – 2007
    * LINQ
    * ASP.NET AJAX
  * ASP.NET 4.0 – 2010
  * ASP.NET 4.5 – 2012
    * MVC
  * ASP.NET Core 1.0 – 2016
  * ASP.NET Core 2.0 – 2017
  * ASP.NET 4.8 – 2019
    * Last version with full .NET Framework
  * ASP.NET Core 3.0 – 2019
  * ASP.NET 5.0 – Scheduled for 2020

## Programming Models
* Web Forms
* Control and event-based programming model similar to Windows Forms
* Controls encapsulate HTML, JavaScript and CSS
* Rich UI controls included – datagrids, charts, AJAX, …
* Browser differences handled for you
* We will be using Web Forms to start
* ASP.NET uses the concept of the “web form”, similar to Windows Forms
* On the form, we place controls
* Server-side technology
* The ASP.NET engine renders standards-based HTML and JavaScript code
* Can also edit in HTML mode
  * Some changes can only be made this way


* MVC
* Model View Controller
* Total control of HTML markup
* Supports unit testing
* Extremely flexible and extensible
* Emerging as preferred development technique

* Web API
  * Application Programming Interface (API)
  * REpresentational State Transfer (REST)
  * Program to program calls across the Internet
  * Allows passing complex objects back and forth
  * Content is typically JavaScript Object Notation (JSON), can also be eXtensible Markup Language (XML) or other schemes

* Web Application
  * Better known as Razor Pages
  * Similar to MVC
    * Total control of HTML markup
    * Supports unit testing
    * Extremely flexible and extensible
  * Alternative to MVC

* Blazor
  * Blazor is a framework for building interactive client-side web UI with .NET
  * Blazor depends on WebAssembly, supported by most major browsers
    * Create rich interactive UIs using C# instead of JavaScript
    * Render the UI as HTML and CSS for wide browser support, including mobile browsers

## ASP.NET Controls
* HTML Controls
  * Ordinary HTML
  * Still useful
  * Lightweight
  * Not processed by server, sent “as is”
* Web Form Controls
  * Denoted by asp:
  * Richer functionality
  * Can be manipulated in code
  * Similar to Windows Form controls
  * run on server

## VS IDE
View in Broswer
Select Browse With… from toolbar to view page with any installed browser
Default can be changed here

VS offers 2 ways to run your site
F5 offers full debugging which allows interactive breakpoints
Ctrl+F5 runs without debugging, which runs faster
Both approaches permit making changes and refreshing browser without relaunching
XML comments are the preferred technique for documenting code in .NET
Type /// on the line before any routine and VS will create the XML comment structure



## HTML Controls



## Web Form Controls
Standard
Buttons, text boxes, labels, …
Rich
Calendars, wizards, …
Validation
Client-side validation
Data
Literal control can be used to display text or HTML
Many more



### Page Object
Events

PreInit
Init
InitComplete
PreLoad
Load
LoadComplete
Control Events
PreRender
PreRenderComplete
SaveStateComplete
Unload




### State
ASP.NET simplifies web programming by automatically maintaining state on page when posting back to the same page
Known as a postback
Most other web development environments force you to manage state yourself
Non-trivial
State is not stored on the server
Good for scalability
Implemented using a hidden HTML field: ``__VIEWSTATE``

Page.IsPostBack
False the first time a page loads
True any subsequent time the page loads
Use to do any one-time tasks


ASP.NET Sessions

In web development, we must use session state to move information around from one page to another and between round-trips
Uses cookies by default
  Can be overridden in Web.config file
  If overridden, it is seamless to programmer
ASP.NET provides a Session[" "] container
Save any object in a Session
  i.e. Session["var_name"] = <object>

Putting something into a session variable
Session["name"] = "Bob Loblaw";
Session["item_count"] = items.Count;
Reading a session variable
String name = Session["name"].ToString();
int cnt = (int)Session["item_count"];
Strings can be pulled out of session variables using the ToString method, almost anything else will need to be cast
