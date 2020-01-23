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
* Run code to view pages in Broswer. VS offers 2 ways to run your site
  * F5 offers full debugging which allows interactive breakpoints
  * Ctrl+F5 runs without debugging, which runs faster
  * Both approaches permit making changes and refreshing browser without relaunching
  * Run by IIS Express can choose a ``http`` port and a ``https`` when right click IIS Service Icon in OS Task Bar.
* Select Browse With… from toolbar to view page with any installed browser.
* Switch between Design view or Code view, by clicking buttons at the bottom left of the editor. Or right click on the file and click View Code/View Design.
* Uses cookies by default, Can be overridden in Web.config file
* ASP.NET simplifies web programming by automatically maintaining state on page when posting back to the same page known as a postback. Any events or data change will reload the page.
* Implemented using a hidden HTML field: ``__VIEWSTATE``
* Any components have a task button, accessed by hover over the beginning tag and click on the arrow button


## Create new project
* select ``ASP.NET Web Application (.NET Framework)`` to create a ASP.NET Web Forms using .NET Framework and C#.

### Create ``.aspx`` Page File
* To create a ``default.aspx`` file as the home page, right-click the project choose Add / Web Form, set name to default.
* Drag any components into the ``pageName.aspx`` file then add event to it by double clicking in Design View.
* Select the Controls code and press F4 to edit its property in the right panel.
* Methods or Events are edited in the ``pageName.aspx.cs`` file.
* For styling, Right-click the project, select Add / Add New Item... From the list, select Style Sheet, name it.
* Drag the css file into the ``<head>`` tag of the aspx file for asscociation.
* Classes and Ids still need to be set in the aspx for the css to work


### ``.aspx.cs`` File
* It stores all the event handlers for the component in ``.aspx`` file.
* It has an ``IsPostBack`` variable that is False the first time a page loads, True any subsequent time the page loads.
* It has access to Session data, ``Session["var_name"] = data``.
  * Read Session data: ``String name = Session["name"].ToString();``, ``int cnt = (int)Session["item_count"];``, ``List<Movie> movies = (List<Movie>)Session["movies"];``.

## Database
### Connection
1. Open the database server.
2. Add the ``.sql`` script into the project in the Solution Explorer.
3. open the ``.sql`` file. click the ``Execute`` button.
4. set Server Name,  ``localhost\serverName`` or any other server address and name, click ``Connect``.
5. The ``sql`` script should be run in the target database.
### Access Through Components
1. In ``.aspx`` file, click the task button of a component, select ``Choose Data Source``.
2. Select ``New Data Source``.
3. Choose the Database and set its ID.
4. Establish New Connection by following the steps to select the corresponding database table.
5. Connection String will be set in ``Web.config`` file in the project folder.
6. Select the corresponding columns to display.

### Access in ``.aspx.cs``
* Requires following directive
  * ``using System.Data;``
  * ``using System.Web.Configuration;``
  * ``using System.Data.SqlClient;``
* Use the following code to add data to database
```cs
try
{
  var connectionString = WebConfigurationManager.ConnectionStrings["movie_trackerConnectionString"].ConnectionString;

  using (SqlConnection connection = new SqlConnection(connectionString))
  {
    var command = new SqlCommand("INSERT INTO movies VALUES(@title, @date, @genre, @rating)", connection);
    command.Parameters.Add("@title", SqlDbType.VarChar);
    command.Parameters["@title"].Value = titleTextBox.Text;
    command.Parameters.Add("@date", SqlDbType.Date).Value = date.ToShortDateString();
    command.Parameters.AddWithValue("@genre", genreDropDownList.SelectedValue);
    command.Parameters.Add("@rating", SqlDbType.Int).Value = rating;
    connection.Open();
    command.ExecuteNonQuery();
  }
}
catch (Exception ex)
{
  outputLiteral.Text += $"<p style=\"color:red;\">{ex.Message}</p>";
}
```
* Use the following code to read data from database
```cs
try
{
  var connectionString = WebConfigurationManager.ConnectionStrings["movie_trackerConnectionString"].ConnectionString;

  using (SqlConnection connection = new SqlConnection(connectionString))
  {
      var command = new SqlCommand(@"SELECT title, date_seen, genre_description, rating
                                     FROM movies m
                                     JOIN genres g
                                     ON m.genre_id = g.genre_id",
                                     connection);
      connection.Open();
      var reader = command.ExecuteReader();

      while (reader.Read())
      {
          outputLiteral.Text += $@"<tr>
                                     <td>{reader["title"].ToString()}</td>
                                     <td>{reader.GetDateTime(1).ToShortDateString()}</td>
                                     <td>{reader["genre_description"].ToString()}</td>
                                     <td style=""text-align:center;"">{(int)reader["rating"]}</td>
                                   </tr>";
      }

      reader.Close();
  }
}
catch (Exception ex)
{
  outputLiteral.Text += $"<p style=\"color:red;\">{ex.Message}</p>";
}
```

## Web Form Controls
* Many Standard .NET Controls Work here.
* Buttons
  * has ``CausesValidation="false"`` property.
* labels
* DropDownList
  * Click task button to edit items. Codes will be auto generated when the items are added.
  * Has value property to set its initial selection, set ``Value="none"`` if it need initial no selected value.
  * ``.SelectedIndex`` are still used in the ``.aspx.cs`` file.
* TextBox - used to get user input
  * has attribute ``TextMode="Date"`` to control input type. Text boxes have multiple modes of operation
    * SingleLine (normal)
    * MultiLine(Can specify number of rows and/or columns)
    * Password
    * Color
    * Date
    * Number
  * has MaxLength property
* Rich
* Calendars, wizards, …
* Validation
  * Validator has the following types:
    * RangeValidator
    * RequiredValidator
    * ValidationSummary - Return the ErrorMessage
    * CompareValidator
    * RegularExpressionValidator - Email address, phone number
    * CustomValidator - required server side code in OnServerValidate and client side code in ClientValidationFunction written in JavaScript.
  * Used to Validation a control's data, and present messages and adjust focus if validation fails.
  * Associate related controls for validation, type the target control's id after the ControlToValidate property.
  * Need to run ``Install-Package AspNet.ScriptManager.jQuery`` in the Tools/NuGet Package Manager / Package Manager Console.
  * IsValid variable can be used in ``.aspx.cs`` file. It returns true if validation is successful.
  * Can use image as output Text ``Text="<img src='images/error.png' alt='Date is required.' title='Required.' />"``.
  * Dynamic property can make it auto adjust. If a control has more than one validation, set display to dynamic.
  * InitialValue is used to inform the validator about its initial value.
* Client-side validation
* Data
* Literal control It can be used to display text or HTML. When content is assigned to its Text property.

### Page Object
It has the following Events:
* PreInit
* Init
* InitComplete
* PreLoad
* Load - Used with IsPostBack to set the initial state for the page.
* LoadComplete
* Control Events
* PreRender - It is used to pass data before the page is shown.
* PreRenderComplete
* SaveStateComplete
* Unload
