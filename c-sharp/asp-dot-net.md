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
* Run code to view the current pages in browser. VS offers 2 ways to run your site
  * F5 offers full debugging which allows interactive breakpoints
  * Ctrl+F5 runs without debugging, which runs faster
  * Both approaches permit making changes and refreshing browser without relaunching
  * Run by IIS Express can choose a ``http`` port and a ``https`` when right click IIS Service Icon in OS Task Bar.
* Select Browse With… from toolbar to view page with any installed browser.
* Switch between Design view or Code view, by clicking buttons at the bottom left of the editor. Or right click on the file and click View Code/View Design.
* Uses cookies by default, Can be overridden in Web.config file
* ASP.NET simplifies web programming by automatically maintaining state on page when posting back to the same page known as a postback. Any events or data change will reload the page.
* Implemented using a hidden HTML field: ``__VIEWSTATE``
* Any components have a task button, accessed by hover over the beginning tag and click on the arrow button at the right side of the component.
* All media files, data files should be dragged into the Solution Explorer, in order to access them for the project.
* In Design mode. Select any components, press F4 to access its properties
* can Add a try/catch block by typing try and inserting the snippet by hitting tab twice.
* Press ``Ctrl+.`` will add directive automatically to the top of the file.


## Create new project
* select ``ASP.NET Web Application (.NET Framework)`` to create a ASP.NET Web Forms using .NET Framework and C#.

### Create ``.aspx`` Page File
* To create a ``default.aspx`` file as the home page, right-click the project choose Add / Web Form, set its name.
* Has Source View and Design View, one can toggle it by click the Source/Design button at the bottom left.
* All settings for the controls which are done by using IDE will have some auto generated codes in the ``.aspx``.
* Drag any components into the ``pageName.aspx`` file in Source View, then add event to it by double clicking in Design View.
* Select the Controls code and press F4 to edit its property in the right panel.
* press F5 to run this page in a browser.
* Methods or Events are edited in the ``pageName.aspx.cs`` file.
* can bind data in this way, ``<%: Title %>``.

### ``.aspx.cs`` File
* It stores all the event handlers for the component in ``.aspx`` file.
* It has an ``IsPostBack`` variable that is False the first time a page loads, True any subsequent time the page loads.
* Most control has ``AutoPostBack="True"`` attribute that allows it to reload the page or update data.
* It has access to Session data, ``Session["var_name"] = data``.
  * Read Session data: ``String name = Session["name"].ToString();``, ``int cnt = (int)Session["item_count"];``, ``List<Movie> movies = (List<Movie>)Session["movies"];``.

### ``.Master`` File
* It is a template for ``.aspx`` file.
* It usually has the navigation, menu, and style of the entire site.
* Multiple ``.aspx`` can asscotiate with the master page.
* Master page cannot run by itself, it is meant to used and associated by other pages.
* Right click on the project in the Solution explorer, the select master page to create.
* Right click on the project in the Solution explorer, then select Web form with master page to associate new ``.aspx`` page with the master page.
* Master can be used to set the title for the entire site dynamically using ``<%: Page.Title %> - SiteName``.
* A web site my have multiple master page.
* Master pages can be nested.
* ContentPlaceHolders controls define regions for content in an ASP.NET master page.
* By default each master page will have one ContentPlaceHolder in the <head> section and one in the <body> section.

### ``.css`` File
* For styling, Right-click the project, select Add / Add New Item... From the list, select Style Sheet, name it.
* Drag the css file into the ``<head>`` tag of the aspx file for association.
* Classes and Ids still need to be set in the ``.aspx`` for the css to work.
* One can add inline style in the asp tag in the style attribute, ``style=""text-align:center;""``.
* can create grid in css for components to located in corresponding grid column
```css
.column1 {
    grid-column: 1;
}
.column2 {
    grid-column: 2;
}
.column3 {
    grid-column: 3;
}
```
* all components has a ``CssClass`` attribute.

### ``.cs`` custom class File
* Right-click the project, select Add / Add New Item... From the list, select the Code group, select Class, name it.
* Define a class in the file, then it can be used in the ``.aspx.cs`` file as a custom object.
```cs

public class ClassName
{
    public string PropertyOne { get; set; }
    public DateTime PropertyTwo { get; set; }
    public int PropertyThree { get; set; }
}
```

## Database
### Connection
* Using Server Explorer
  1. click server explorer in the bottom left corner.
  2. click on the ``Connect to Database`` icon.
  3. enter server name, Ex: ``localhost\serverName``.
  4. select the database name to connect or select a database file that will be created in the server then connect.
* Add ``.sql`` file first.
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
5. Connection String will be set in ``Web.config`` file in the project folder. Accessed by using the WebConfigurationManager.  ``var connectionString = WebConfigurationManager.ConnectionStrings["movie_trackerConnectionString"].ConnectionString;``
6. Select the corresponding columns of the table to display. Ex: index is used for value of a DropDownList.

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
    connection.Close();//need restart connections for each command.ExecuteNonQuery() method.

  }
}
catch (Exception ex)
{
  outputLiteral.Text += $"<p style=\"color:red;\">{ex.Message}</p>";
}
* keywords like ``@email`` and ``@id`` are predefined.
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
                                   //reader.GetString(0) returns 1st column as string
      }

      reader.Close();
  }
}
catch (Exception ex)
{
  outputLiteral.Text += $"<p style=\"color:red;\">{ex.Message}</p>";
}
```
* SQL Command Object, The SQL Command Object has 3 main modes of operation
  * ExecuteNonQuery – Executes an INSERT, UPDATE or DELETE statement and returns an integer indicating the number of rows affected
  * ExecuteReader – Executes a SELECT statement and returns a multi-row, multi-column result set
  * ExecuteScalar – Executes a SELECT statement and returns the first column of the first row of the result set, additional columns or rows are ignored.

## Web Form Controls
* Many Standard .NET Controls Work here.
* Buttons
  * has ``CausesValidation="false"`` property. will ignore validator and reset all validators when the button is clicked.
  * has Text attribute.
* Labels
  * its text is defined in the Text attribute.
* DropDownList
  * Click task button to edit items. Codes will be auto generated when the items are added.
  * Has value property to set its initial selection, set ``Value="none"`` if it need initial no selected value.
  * ``.SelectedIndex`` are still used in the ``.aspx.cs`` file.
  * has property ``selectedValue``, ``selectedIndex``.
  * Its listItem can have a ``Value`` attribute, it can be set to ``none`` for the first choice.
* TextBox - used to get user input
  * has attribute ``TextMode="Date"`` to control input type. Text boxes have multiple modes. of operation
    * SingleLine (normal)
    * MultiLine(Can specify number of rows and/or columns)
    * Password
    * Color
    * Date
    * Number
  * has MaxLength property
  * has placeholder attribute.
  * can ``TextBox.Focus()``
* Rich
* Calendars, wizards, …
* Validation
  * Adding by dragging it from the left panel below the related component for validation.
  * Used to Validation a control's data, and present messages and adjust focus if validation fails.
  * all validators have attribute ``Text="Must be from 1 to 10."`` The message shown when validation failed. It can be a link to a image. ``Text="<img src='images/error.png' alt='Date is required.' title='Required.' />"``(The image needs to be dragged into solution explorer first.)
  * all validators have attribute ``SetFocusOnError="True"``.
  * all validators have attribute ``ControlToValidate="controlID"``. This is used to associate it with certain input component.
  * Validator has the following types:
    * RangeValidator
      * has attribute ``MaximumValue="10"``
      * has attribute ``MinimumValue="1"``
      * has attribute ``Type="Integer"``
    * RequiredValidator
      * ``InitialValue`` is used to inform the RequiredValidator knows and ignores its initial value.
    * ValidationSummary - a control that returns the ErrorMessages from all Validator in a point lists.
    * CompareValidator
    * RegularExpressionValidator
      * For email validation add attribute ``ValidationExpression="^([\w-\.]+)@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.)|(([\w-]+\.)+))([a-zA-Z]{2,4}|[0-9]{1,3})(\]?)$"``.
    * CustomValidator - required server side code in OnServerValidate and client side code in ClientValidationFunction written in JavaScript.
  * Associate related controls for validation, type the target control's id in the ControlToValidate attribute.
  * Need to run ``Install-Package AspNet.ScriptManager.jQuery`` in the Tools/NuGet Package Manager / Package Manager Console.
  * ``IsValid`` variable can be used in ``.aspx.cs`` file. It returns true if validation is successful.
  * Dynamic property can make it auto adjust. If a control has more than one validation, add a display attribute as dynamic. ``Display="Dynamic"``. This will prevent multiple validator of one control take extra blank space even when not Text message is shown.
* Client-side validation
* Data
* Literal control
  * It can be used to display text or HTML. When content is assigned to its Text property.
  * ``outputLiteral.Text += $"<p style=\"color:red;\">{ex.Message}</p>";``.
* Page Object
  * It has the following Events:
    * PreInit
    * Init
    * InitComplete
    * PreLoad
    * Load - has a variable ``IsPostBack``, ``IsPostBack`` returns false when first loaded, is true with page is reloaded.
    * LoadComplete
    * Control Events
    * PreRender - It is used to pass data before the page is shown, is called when button is clicked.
    * PreRenderComplete
    * SaveStateComplete
    * Unload
* GridView
  * A table, created by dragging GridView from toolbox the add data source, or drag a table from the server explorer.
  * Click the grid view's task button and click Edit Columns to change the table's content and format, and make certain column not editable(read only).
  * Click the grid view's task button to enable Auto Format, Enable Paging, Enable Sorting and Enable Editing.
  * in the ``.aspx.cs`` file the gridview object has ``.Row.RowType``, ``e.Row.DataItem``, ``.Row.BackColor`` properties.
  * can enable selection to make it an interactive control. like a dropdownlist, a selectable table can return a selected value.
  * Common DataFormatString values
    * ``{0:c}`` Currency
    * ``{0:d}`` Short date
    * ``{0:n2}`` Numeric with 2 decimal place
  * Use RowDataBound event hanler to highlight certain row.
  ```cs
  protected void productsGridView_RowDataBound(object sender, GridViewRowEventArgs e)
  {
      if (e.Row.RowType == DataControlRowType.DataRow)
      {
          var inStock = (intshort)DataBinder.Eval(e.Row.DataItem, "UnitsInStock");

          if (inStock < 10)
          {
              e.Row.BackColor = System.Drawing.Color.Yellow;
          } // (inStock < 10)
      } // (e.Row.RowType == DataControlRowType.DataRow)
  }
  ```

* SqlDataSource
  * usually automatically generated when a data source is created for a control.
  * has the ability to filter and sort data using SQL command.
  * can Generate INSERT, UPDATE and DELETE statements for the data source, in the advanced setting.
  * When write custom SQL statement surround everything with ``[]``. Ex: ``JOIN [orders] [o1] ON [o1].[id] = [sales].[id]``.
* DetailsView
  * it is used to show detail, has a default width attribute which is 125px.
  * It can ``Enable Editing`` in the task button options. for edit details.
