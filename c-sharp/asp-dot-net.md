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
  * It has many supported languages and tools, main languages include C\#, VB.NET and JavaScript, Perl, Python, Ruby.
* ASP.NET Core
  * It belongs to the .NET Core.
  * Open source, cross platform framework released in 2016
  * Can develop and run on Windows, macOS or Linux
  * Higher performance than ASP.NET
  * Core has fewer features than "Full" ASP.NET Framework, but will catch up in the future.
* Version History
  * ASP.NET 1.0 – 2002
  * ASP.NET 2.0 – 2005
    * Master pages \(Templates\)
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
  * Application Programming Interface \(API\)
  * Representational State Transfer \(REST\)
  * Program to program calls across the Internet
  * Allows passing complex objects back and forth
  * Content is typically JavaScript Object Notation \(JSON\), can also be eXtensible Markup Language \(XML\) or other schemes
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
    * Create rich interactive UIs using C\# instead of JavaScript
    * Render the UI as HTML and CSS for wide browser support, including mobile browsers

### VS IDE

* Run code to view the current pages in browser. VS offers 2 ways to run your site
  * F5 offers full debugging which allows interactive breakpoints
  * Ctrl+F5 runs without debugging, which runs faster
  * Both approaches permit making changes and refreshing browser without relaunching
  * Run by IIS Express can choose a `http` port and a `https` when right click IIS Service Icon in OS Task Bar.
* Select Browse With… from toolbar to view page with any installed browser.
* Switch between Design view or Code view, by clicking buttons at the bottom left of the editor. Or right click on the file and click View Code/View Design.
* Uses cookies by default, Can be overridden in Web.config file
* ASP.NET simplifies web programming by automatically maintaining state on page when posting back to the same page known as a postback. Any events or data change will reload the page.
* Implemented using a hidden HTML field: `__VIEWSTATE`
* Any components have a task button, accessed by hover over the beginning tag and click on the arrow button at the right side of the component.
* All media files, data files should be dragged into the Solution Explorer, in order to access them for the project.
* In Design mode. Select any components, press F4 to access its properties
* can Add a try/catch block by typing try and inserting the snippet by hitting tab twice.
* Press `Ctrl+.` will add directive automatically to the top of the file.
* To change a ASP.NET project to Production mode, In Solution Explorer, right-click the project and select `Properties`. Click the `Debug` tab. Change the `ASPNETCORE_ENVIRONMENT` environment variable to `Production`. Close the `Properties` page.
* Enable Browser Reload on Save
  1. From the `Extensions` menu, select `Manage Extensions`.
  2. On the left, click `Online`. In the Search box, enter `browser`.
  3. In the results, locate `Browser Reload on Save`.
  4. Select it and click `Download`. Click `Close`.
  5. Close Visual Studio, the install will start. Click `Modify`.
  6. Allow the VSIX installer to complete, click `Close`.
  7. Start Visual Studio, reopen the project.
  8. Right-click the project in solution explorer and select `Manage NuGet Packages...`
  9. Click the `Browse` tab. In the Search box, enter `browser`.
  10. Select `Microsoft.VisualStudio.Web.BrowserLink` and click `Install`, accept the license.
  11. Add `app.UseBrowserLink();` in the development section of the Configure method.
  12. Re-launch the site.
* Press `Ctrl+Shift+T` to open the all-purpose Go to tool.

## Web Form Model

### Create new project

* select `ASP.NET Web Application (.NET Framework)` to create a ASP.NET Web Forms using .NET Framework and C\#.

#### Create `.aspx` Page File

* To create a `default.aspx` file as the home page, right-click the project choose Add / Web Form, set its name.
* Has Source View and Design View, one can toggle it by click the Source/Design button at the bottom left.
* All settings for the controls which are done by using IDE will have some auto generated codes in the `.aspx`.
* Drag any components into the `pageName.aspx` file in Source View, then add event to it by double clicking in Design View.
* Select the Controls code and press F4 to edit its property in the right panel.
* press F5 to run this page in a browser.
* Methods or Events are edited in the `pageName.aspx.cs` file.
* can bind data in this way, `<%: Title %>`.

#### `.aspx.cs` File

* It stores all the event handlers for the component in `.aspx` file.
* It has an `IsPostBack` variable that is False the first time a page loads, True any subsequent time the page loads.
* Most control has `AutoPostBack="True"` attribute that allows it to reload the page or update data.
* It has access to Session data, `Session["var_name"] = data`.
  * Read Session data: `String name = Session["name"].ToString();`, `int cnt = (int)Session["item_count"];`, `List<Movie> movies = (List<Movie>)Session["movies"];`.

#### `.Master` File

* It is a template for `.aspx` file.
* It usually has the navigation, menu, and style of the entire site.
* Multiple `.aspx` can asscotiate with the master page.
* Master page cannot run by itself, it is meant to used and associated by other pages.
* Right click on the project in the Solution explorer, the select master page to create.
* Right click on the project in the Solution explorer, then select Web form with master page to associate new `.aspx` page with the master page.
* Master can be used to set the title for the entire site dynamically using `<%: Page.Title %> - SiteName`.
* A web site my have multiple master page.
* Master pages can be nested.
* ContentPlaceHolders controls define regions for content in an ASP.NET master page.
* By default each master page will have one ContentPlaceHolder in the  section and one in the  section.

#### `.css` File

* For styling, Right-click the project, select Add / Add New Item... From the list, select Style Sheet, name it.
* Drag the css file into the `<head>` tag of the aspx file for association.
* Classes and Ids still need to be set in the `.aspx` for the css to work.
* One can add inline style in the asp tag in the style attribute, `style=""text-align:center;""`.
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

* all components has a `CssClass` attribute.

#### `.cs` custom class File

* Right-click the project, select Add / Add New Item... From the list, select the Code group, select Class, name it.
* Define a class in the file, then it can be used in the `.aspx.cs` file as a custom object.

```csharp
public class ClassName
{
    public string PropertyOne { get; set; }
    public DateTime PropertyTwo { get; set; }
    public int PropertyThree { get; set; }
}
```

### Database

#### Connection

* Using Server Explorer
  1. click server explorer in the bottom left corner.
  2. click on the `Connect to Database` icon.
  3. enter server name, Ex: `localhost\serverName`.
  4. select the database name to connect or select a database file that will be created in the server then connect.
* Add `.sql` file first.
  1. Open the database server.
  2. Add the `.sql` script into the project in the Solution Explorer.
  3. open the `.sql` file. click the `Execute` button.
  4. set Server Name, `localhost\serverName` or any other server address and name, click `Connect`.
  5. The `sql` script should be run in the target database.

#### Access Through Components

1. In `.aspx` file, click the task button of a component, select `Choose Data Source`.
2. Select `New Data Source`.
3. Choose the Database and set its ID.
4. Establish New Connection by following the steps to select the corresponding database table.
5. Connection String will be set in `Web.config` file in the project folder. Accessed by using the WebConfigurationManager. `var connectionString = WebConfigurationManager.ConnectionStrings["movie_trackerConnectionString"].ConnectionString;`
6. Select the corresponding columns of the table to display. Ex: index is used for value of a DropDownList.

#### Access in `.aspx.cs`

* Requires following directive
  * `using System.Data;`
  * `using System.Web.Configuration;`
  * `using System.Data.SqlClient;`
* Use the following code to add data to database

```csharp
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

```csharp
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

### Web Form Controls

* Denoted by asp, have the following property:
  * Richer functionality
  * Can be manipulated in code
  * run on server
  * Many Standard .NET Controls Work here.
* HTML Controls
  * Ordinary HTML
  * Still useful
  * Lightweight
  * Not processed by server, sent "as is".
* Buttons
  * has `CausesValidation="false"` property. will ignore validator and reset all validators when the button is clicked.
  * has Text attribute.
* Labels
  * its text is defined in the Text attribute.
* DropDownList
  * Click task button to edit items. Codes will be auto generated when the items are added.
  * Has value property to set its initial selection, set `Value="none"` if it need initial no selected value.
  * `.SelectedIndex` are still used in the `.aspx.cs` file.
  * has property `selectedValue`, `selectedIndex`.
  * Its listItem can have a `Value` attribute, it can be set to `none` for the first choice.
* TextBox - used to get user input
  * has attribute `TextMode="Date"` to control input type. Text boxes have multiple modes. of operation
    * SingleLine \(normal\)
    * MultiLine\(Can specify number of rows and/or columns\)
    * Password
    * Color
    * Date
    * Number
  * has MaxLength property
  * has placeholder attribute.
  * can `TextBox.Focus()`
* Rich
* Calendars, wizards, …
* Validation
  * Adding by dragging it from the left panel below the related component for validation.
  * Used to Validation a control's data, and present messages and adjust focus if validation fails.
  * all validators have attribute `Text="Must be from 1 to 10."` The message shown when validation failed. It can be a link to a image. `Text="<img src='images/error.png' alt='Date is required.' title='Required.' />"`\(The image needs to be dragged into solution explorer first.\)
  * all validators have attribute `SetFocusOnError="True"`.
  * all validators have attribute `ControlToValidate="controlID"`. This is used to associate it with certain input component.
  * Validator has the following types:
    * RangeValidator
      * has attribute `MaximumValue="10"`
      * has attribute `MinimumValue="1"`
      * has attribute `Type="Integer"`
    * RequiredValidator
      * `InitialValue` is used to inform the RequiredValidator knows and ignores its initial value.
    * ValidationSummary - a control that returns the ErrorMessages from all Validator in a point lists.
    * CompareValidator
    * RegularExpressionValidator
      * For email validation add attribute `ValidationExpression="^([\w-\.]+)@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.)|(([\w-]+\.)+))([a-zA-Z]{2,4}|[0-9]{1,3})(\]?)$"`.
    * CustomValidator - required server side code in OnServerValidate and client side code in ClientValidationFunction written in JavaScript.
  * Associate related controls for validation, type the target control's id in the ControlToValidate attribute.
  * Need to run `Install-Package AspNet.ScriptManager.jQuery` in the Tools/NuGet Package Manager / Package Manager Console.
  * `IsValid` variable can be used in `.aspx.cs` file. It returns true if validation is successful.
  * Dynamic property can make it auto adjust. If a control has more than one validation, add a display attribute as dynamic. `Display="Dynamic"`. This will prevent multiple validator of one control take extra blank space even when not Text message is shown.
* Client-side validation
* Data
* Literal control
  * It can be used to display text or HTML. When content is assigned to its Text property.
  * `outputLiteral.Text += $"<p style=\"color:red;\">{ex.Message}</p>";`.
* Page Object
  * It has the following Events:
    * PreInit
    * Init
    * InitComplete
    * PreLoad
    * Load - has a variable `IsPostBack`, `IsPostBack` returns false when first loaded, is true with page is reloaded.
    * LoadComplete
    * Control Events
    * PreRender - It is used to pass data before the page is shown, is called when button is clicked.
    * PreRenderComplete
    * SaveStateComplete
    * Unload
* GridView

  * A table, created by dragging GridView from toolbox the add data source, or drag a table from the server explorer.
  * Click the grid view's task button and click Edit Columns to change the table's content and format, and make certain column not editable\(read only\).
  * Click the grid view's task button to enable Auto Format, Enable Paging, Enable Sorting and Enable Editing.
  * in the `.aspx.cs` file the gridview object has `.Row.RowType`, `e.Row.DataItem`, `.Row.BackColor` properties.
  * can enable selection to make it an interactive control. like a dropdownlist, a selectable table can return a selected value.
  * Common DataFormatString values
    * `{0:c}` Currency
    * `{0:d}` Short date
    * `{0:n2}` Numeric with 2 decimal place
  * Use RowDataBound event hanler to highlight certain row.

  ```csharp
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
  * When write custom SQL statement surround everything with `[]`. Ex: `JOIN [orders] [o1] ON [o1].[id] = [sales].[id]`.
* DetailsView
  * it is used to show detail, has a default width attribute which is 125px.
  * It can `Enable Editing` in the task button options. for edit details.

## ASP.NET Core Application

* An ASP.NET Core web application is actually an ASP.NET Core console application
* The console application starts up an instance of an ASP.NET Core web server called Kestrel.

### Start a Web App Project as Console App

1. In VS, create a new project by selecting Console App \(.NET Core\) template that has C\#.
2. install `Microsoft.AspNetCore.Server.Kestrel` in the Manage NuGet Packages... panel.
3. start up an instance of the Kestrel Server by using the following sample code.

   ```csharp
   using Microsoft.AspNetCore.Builder;
   using Microsoft.AspNetCore.Hosting;
   using Microsoft.AspNetCore.Http;
   using System;
   namespace sample_server
   {
       class App
       {
           static void Main()
           {
               new WebHostBuilder()
                   .UseKestrel()
                   .Configure(a => a.Run(c => c.Response.WriteAsync("Web content goes here.")))
                   .Build()
                   .Run();
           }
       }
   }
   ```

4. From the console window that appears, copy one of the URLs and paste and run it in a browser.

### Start a Web App Project using MVC

* In VS, create a new project by selecting ASP.NET Core Web Application that has C\# with MVC template.

### `Program.cs` file

* It initiates a Kestrel Server.
* It will load the Pages from `Startup.cs`, by default.

```csharp
public class Program
{
  public static void Main(string[] args)
  {
      CreateWebHostBuilder(args).Build().Run();
  }

  public static IWebHostBuilder CreateWebHostBuilder(string[] args) =>
      WebHost.CreateDefaultBuilder(args)
          .UseStartup<Startup>();
}
```

### `Startup.cs` file

* The Configure method control the pages to be loaded in the Startup file.
* The ConfigureServices method add configuration for additional services for the middlewares in the Configure method.
* It can load text into the page by using one middleware.

  ```csharp
  app.Run(async (context) =>
    {
      await context.Response.WriteAsync("Hello World!");
    });
  ```

* Additional middleware can be added before `app.Run`. If not using `next()`, only one middleware can be seen at one time.

  ```csharp
  app.Use(async (context, next) =>
  {
      await context.Response.WriteAsync("New middleware. ");
      await next();
  });
  app.Run(async (context) =>
  {
      await context.Response.WriteAsync("Hello World!");
  });
  ```

* Middleware can be loaded when the webpage is loaded under certain path.

  ```csharp
  if (context.Request.Path.Value.StartsWith("/hi"))
  {
      await context.Response.WriteAsync("New middleware. ");
  }
  ```

* Middleware can be loaded when the webpage path has certain value.

  ```csharp
  if (context.Request.Path.Value.Contains("invalid"))
  {
    await context.Response.WriteAsync("New middleware contains invalid in its path.");
  }
  ```

* It can serve static pages from `wwwroot` folder in project folder using UseFileServer when page contents files are dragged into the `wwwroot` folder of the Solution Explorer.

  ```csharp
  app.UseFileServer();
  ```

* Add the following middleware in the first line of the Configure method to handle exception by redirecting all unhandled exception to the error page in Production mode.

  ```csharp
  app.UseExceptionHandler("/error.html");
  // throw new Exception("ERROR!"); can be used in another middleware to raise exception for testing.
  ```

* It can contains a MVC routing middleware.
  * In the Configure method add.

    ```csharp
    app.UseMvc(routes =>
      {   //It will open the page associate with the path ControllerName/PageName/
          // and by default the website will load home/index if no path is entered.
          routes.MapRoute("Default", "{controller=Home}/{action=Index}/{id?}");
      });
    ```

  * In the ConfigureServices method add

    ```csharp
    services.AddMvc();
    ```
* When use the repository data model, in the `ConfigureServices` method to inject the data in the controller's constructor.

  ```csharp
  // Add our own ExampleRepository as a service
  // Specify the type of the service contract (interface)
  // and the type of the implementation of the service (class)
  services.AddScoped<IExampleRepository, ExampleRepository>();
  ```

* Inject data into the controller's constructor form SQL Server, `services.AddDbContext<ExampleDataContext>(options => options.UseSqlServer(Configuration.GetConnectionString("ExampleDataContext")));`
* Inject data into the controller's constructor form for SQLite, `services.AddDbContext<ExampleDataContext>(options => options.UseSqlite(Configuration.GetConnectionString("ExampleDataContextLite")));`

### Controllers

* The main controller is `HomeController.cs` by default.
* It is located in the `Controllers` folder in the project Explorer.
* Each method in the controllers corespondes to a page, the method name is the same as the page name.
* It can return a string type or `IActionResult`, in these cases it does not need to inherite the Controller Class.

  ```csharp
  // The index page in Home Controller that returns a string content.
  public IActionResult Index()
  {
      return new ContentResult { Content = "Hello from HomeController / Index." };
  }
  ```

* A page can take one parameters entered in the path, if the MVC routing middleware has the corresponding variable.

  ```csharp
  public IActionResult PageName(int id)
  {
    return new ContentResult { Content = $"Hello from OtherController / Post, id={id.ToString()}." };
  }
  ```

* `/ControllerName/PageName?id=100` also works when passing parameters.
* If the value is not entered the default value for the related type will be used.
* `?` can be added after the type to make it nullable.
* a default value can be assigned to the parameter, `public IActionResult PageName(int id = 1)`
* Additional Control files can be added in the folder with the following naming convention, `NameController.cs`.
* One can also customize the route in the controller.

  ```csharp
  [Route("newpath/{year:int}/{month:int}/{key}")]
  public IActionResult PageName(int year, int month, string key)
  {
    return new ContentResult { Content = $"Hello from OtherController / Post, year={year}, month={month}, key={key}." };
  }
  ```

* The page will be accessed by the route path, not longer by the method name.
* One can add route constraints, for example, `[Route("stuff/{year:min(2018)}/{month:range(1,12)}/{key}")]`
* Change the return value to `view()` will display the page located in the `View/ControllerName/methodName.cshtml`.
  * If the page method returns `view()`, the controller class needs to inherite the Cotroller Class.
* In the controller method, data can be passed to `.cshtml` pages using `ViewBag`.

  ```csharp
  ViewBag.Title = "Heading From Controller";
  ViewBag.Name = "Bob Loblaw";
  ViewBag.Served = DateTime.Now;
  ```

* Controller methods can return class object defined in the `Models` folder. Then the related`.cshtml` page will have access to the object.

  ```csharp
  public IActionResult Index()
  {
    var stuff = new Stuff
    {
      Title = "Heading From Controller",
      Name = "Bob Loblaw",
      Served = DateTime.Now
    };
    return View(stuff);
  }
  ```

  * Right click controller page methods can create `.cshtml` page in the relative page folder.
    * Can choose a template. List template is a table. Create template is a form.
    * Can choose a data model.
  * The `MVC Controller with read/write actions template` is good at interacting with data model.
    * In `Index.cshtml` select the proper data model property for `Edit`, `Details`, `Delete` to link.
    * Add the data source in the return statement `view(dataName)` to display the data in the page.
    * It has Create, Edit, Delete Page GET method that load data to template pages.
      * The Detail page GET method return selected data object id. right click to add corresponding view.

        ```csharp
        public ActionResult Details(int id)
        {
        var movie = movies.Find(m => m.Id == id);
        return View(movie);
        }
        ```
    * It has Create, Edit, Delete POST methods to modify the data model then update the pages.
      * The delete POST method delete the selected data and return to the `Index` page after

        ```csharp
        public ActionResult Delete(int id, IFormCollection collection)
        {
          try
          {
              var index = data.FindIndex(m => m.Id == id);
              data.RemoveAt(index);
              return RedirectToAction(nameof(Index));
          }
          catch
          {
              return View();
          }
        }
        ```

* If using the repository data model. Declare it in the constructor, the repo is the argument of the constructor.

  ```csharp
  private IDataRepository db;
  public DataController(IDataRepository dataRepository):base()
  {
    db = dataRepository;
  }
  ```

* If using the Entity Framework data model. Declare it in the constructor, the DataContext is the argument of the constructor.

  ```csharp
  private MovieDataContext db;
    public MoviesController(MovieDataContext movieRepository):base()
    {
      db = movieRepository;
    }
  ```

* Sorting

  ```csharp
  public async Task<IActionResult> Index(string sortOrder)
  {
      ViewData["DescriptionSortParm"] = String.IsNullOrEmpty(sortOrder) ? "description_desc" : "";
      ViewData["CostSortParm"] = sortOrder == "cost" ? "cost_desc" : "cost";
      var medications = from m in _context.Medications
                          select m;
      switch (sortOrder)
      {
          case "description_desc":
              medications = medications.OrderByDescending(m => m.MedicationDescription);
              break;
          case "cost":
              medications = medications.OrderBy(m => m.MedicationCost);
              break;
          case "cost_desc":
              medications = medications.OrderByDescending(m => m.MedicationCost);
              break;
          default:
              medications = medications.OrderBy(m => m.MedicationDescription);
              break;
      }
      // return with change tracking disabled
      return View(await _context.Medicationsmedications.AsNoTracking().ToListAsync());
  }
  ```

* Search

  ```csharp
  ViewData["CurrentFilter"] = searchString;
  var medications = from m in _context.Medications
                      select m;
  if (!String.IsNullOrEmpty(searchString))
  {
      medications = medications.Where(m => m.MedicationDescription.Contains(searchString));
  }
  ```

  * the searchString is a parameter passed into the Index method. The variable name must match the `?VariableName=value` in the URL with the first letter in lowercase. The parameter also has to be of type `string`.

### Views

* Inside the `Views` folder.
* The page in represented as a Razor page file with `.cshtml` extension.
* Razor is a markup syntax for embedding server-based code into webpages
* The Razor syntax consists of Razor markup, C\#, and HTML.
* `@@` to escape the `@` symbol
* Comment Syntax: `@* comment *`.
* Implicit Razor expression is rendered as HTML, spaces not allowed, `<p>Today: @DateTime.Now</p>`
* Explicit Razor expression is renders as HTML, spaces allowed, `<p>Week ago: @(DateTime.Now - TimeSpan.FromDays(7))</p>`
* Razor code block, it doesn’t render as HTML, semicolons required

  ```csharp
  @{
    var name = "John Doe";
    var len = name.Length;
  }
  <p>The length of @name is @len bytes.</p>
  ```

* By default, The `Index.cshtml` page of each folder will be loaded.
* Each `.cshtml` is associated with the `view()` in the controllers methods.
* The Controller names are associated with the folder name inside the `views` folder.
* Access model object passed from the controller.

  ```csharp
  @model  projectName.Models.ModelClassName
  <p>@Model.PropertyName</p>
  ```

* `.cshtml` file supports Razor page code that access variable using `@` symbol.
* Passing variable in the page. `@DateTime.Now.Year`.
* Links are represented as `@Url.Action("PageRouteName", "ControllerName")`
* Access data passed in ViewBags. `<h2>@ViewBag.Title</h2><p>Name: @ViewBag.Name</p><p>Page served: @ViewBag.Served</p>`.
* Links are represented as `asp-controller="ControllerName" asp-action="PageName"`
  * `controllerName` is the first part of the controller file names. Ex, for `HomeController.cs`, `Home` is the value for the `asp-controller` attribute.
* `<input asp-for="Id" class="form-control" readonly />`, make the input readonly.
* `<input asp-for="Title" class="form-control" autofocus />`, make the input autofocused.
* HTML Helpers
  * `@Html.DisplayNameFor` – plain text to display the read-only field name
  * `@Html.DisplayFor` – figures out the best HTML5 for read-only display of the actual field value
  * `@Html.ActionLink` – action link with anchor tag
* A select List `<select asp-for="GenreId" class ="form-control" asp-items="ViewBag.ListItems"></select>`
  * SelectList is an object defined in the `.cs` file `ViewBag.ListItem = new SelectList(ListofItems, "ColA", "ColB");`
* Sorting

  ```markup
  <th>
      <a asp-action="Index" asp-route-sortOrder="@ViewData["DescriptionSortParm"]">
          @Html.DisplayNameFor(model => model.MedicationDescription)
      </a>
  </th>
  <th>
      <a asp-action="Index" asp-route-sortOrder="@ViewData["CostSortParm"]">
          @Html.DisplayNameFor(model => model.MedicationCost)
      </a>
  </th>
  ```

* Search

  ```markup
  <form asp-action="Index" method="get">
    <p>
      Filter by Description: <input type="text" name="SearchString"
      value="@ViewData["CurrentFilter"]" />
      <input type="submit" value="Search" class="btn btn-primary" /> |
      <a asp-action="Index">All Medications</a>
    </p>
  </form>
  ```

* Filter List

  ```csharp
  <form asp-action="Index" method="get">
    <p>
        Manager:
        <select asp-for="@Model.FirstOrDefault().NursingUnitId" asp-items="@ViewBag.NursingUnitId"></select>
        <input type="submit" value="Filter" class="btn btn-primary" /> |
        <a asp-action="Index">All Admitted Patients</a>
    </p>
  </form>
  ```

#### Layout file

* In the `Views/Shared` folder, a layout file can be created.
* It is usually called `_layout.cshtml`.
* layout can contains a replacable body and a replaceable section.
  * Render Body
  * In the layout file, use `@RenderBody()` to indicate the location for the individual page contents.
  * In the pages that use the layout, add `@{ Layout = "layoutFileName";}` at the top.
  * Render Section
    * A mandatory render section will raise exception when the content page have not define the render section content.
    * Add a mandatory render section in the layout file`<div class="container">@RenderSection("header")</div>`
    * Add an optional render section in the layout file`<div class="container">@RenderSection("header", false)</div>`
    * Add an optional render section with default content.

      ```csharp
      @if (IsSectionDefined("header"))
      {
        @RenderSection("header", false)
      }
      else
      {
        <br /><br />
        <h1>Header from _Layout</h1>
      }
      ```

    * Define a render section in the content page`@section header {<p>render section</p>}`

### Models

* They custom classes, `.cs` files, defined in the `Models` folders.
* `using projectName.Models;` directive is required for other files to access the class definition.
* Data annotation
  * Can be used to set constraints to the models' data.
  * Need `using System.ComponentModel.DataAnnotations;`
  * Used with `?` to define nullable type property.
  * Can also set the display name.
  * Example:

    ```csharp
    public class ClassName
    {
      [Key]
      public int Id { get; set; }
      [Required]
      public string Title { get; set; }
      [DataType(DataType.Date)]
      [Display(Name = "Date Seen")]
      public DateTime? DateTime { get; set; }
      public string Description { get; set; }
      [Range(1, 10)]
      [DisplayFormat(DataFormatString="{0:C}")]
      public int? Rating { get; set; }
      [EmailAddress]
      public string email { get; set; }
    }
    ```
* Use repository as data model
  * Can create public interface file in the model folder for other data model repository class to use.
  * Can create repository model that contains methods to manipulate data, the method can be used by controller class and make the controller class cleaner.
* Use database as data model
  * The Entity Framework is the ORM\(Object/Relational Mapping\) tool used by `.NET`.
  * Create a `MovieDataContext.cs` class that inherit `DbContext`.

    ```csharp
    public class DataNameDataContext : DbContext
    {
    // Add a DbSet property to represent the data table in the database.
    public DbSet<DataName> DataName { get; set; }
    // Add a constructor that ensures the database exists, if not creates the database.
    public DataNameDataContext(DbContextOptions<DataNameDataContext> options) : base(options)
    {
        Database.EnsureCreated();
    }
    }
    ```

  * implement the repository interface, complete its methods.
  * Implement the `OnModelCreating` method to populate data into the database on first creation.

    ```csharp
    protected override void OnModelCreating(ModelBuilder modelBuilder)
    {
      modelBuilder.Entity<DataName>().HasData(
        // Enter data here
      );
    }
    ```

  * Check the primary key in the data class, represented as the `[Key]` constraint.
  * Foreign Key will be denoted as `[ForeignKey("columnName")]`.
    * Use `using System.ComponentModel.DataAnnotations.Schema;` when database relationship is applied.
    * If two data model has a referencial relationship. Each data model class need to have a property of the other model class object\(Navigation property\). When access the other object use `ObjectsA.Include(m => m.ObjectBProperty)` in the controller and use `model.objectName.Property` in the `.cshtml` to access the objects from the other table.
  * Setup the inject in the `Startup.cs`.
  * Add connection string in the `appsettings.json`.

    ```javascript
    "ConnectionStrings": {
    "DataContext": "Data Source=localhost\\sqlexpress;Initial Catalog=project_name;Integrated Security=True"
    ```

  * Declear the Data Context object in the controller file.
  * To use `sqlite`:
    * Right-click the project and select `Manage NuGet Packages...`
    * Select the `Microsoft.EntityFrameworkCore.Sqlite package`. In the Version drop-down list, select `2.2.6`. Click Install.
  * Add `SQLite/SQL Server Compact Toolbox`
    1. From the Extensions menu, select Manage Extensions.
    2. On the left, select Online, Search for sqlite.
    3. Download the `SQLite/SQL Server Compact Toolbox`.
    4. Restart Visual Studio.
    5. From the `Tools` menu, select `SQLite/SQL Server Compact Toolbox`.
    6. Click the `Add SQLite and SQL Compact connections` from current Solution button.
    7. Expand database file. Right-click and select Edit Top 200 Rows to see the data.
* Database Migrations
  * In the Package Manager Console, run `Add-Migration init`.
    * make sure the default project is the current project.
    * A folder called `Migrations` will be created with two files inside.
      * `YYYYMMDDHHMMSS_init.cs` contains code to create the database schema.
      * `DataContextModelSnapshot.cs` contains code to insert the data.
  * run `Update-Database`
    * This will update the data into the associated database.
    * The database will have an expected table and a migration history table.
  * run `Add-Migration column_name` or `Add-Migration table_name` If a new column is created later.
    * one can always run `Update-Database` to synchronize the table.
* Scaffold-DbContext
  * It will automatically generate data and models for an existing database.
  * It needs to set the connection string first in the `appsetting.json`.

    ```javascript
    "ConnectionStrings": {
    "DBName": "Data Source=localhost\\sqlexpress;Initial Catalog=dbName;Integrated Security=True"
    },
    ```

  * In Package Manager Console, run `Scaffold-DbContext name=chdb Microsoft.EntityFrameworkCore.SqlServer -OutputDir Models -ContextDir Data -DataAnnotations`.
  * Then, controller can be generated using the `MVC Controller with views, using Entity Framework` option when creating the controller, select the table and data model for the controller.

### MVC Error Handling

* `ErrorViewModel.cs` is the error data model. It is the data that passed into the error page.
* `Error.cshtml` defines the error page, it is in the `Shared` folder.
* In the controller file, add condition and return the `Error.cshtml` page with error data to raise errors.

  ```csharp
  public ActionResult Details(int id)
  {
      var dataObject = data.Find(o => o.Id == id);
      if (dataObject == null)
      {
          return View("Error",
              new ErrorViewModel
              {
                  RequestId = id.ToString(),
                  Description = $"Unable to find movie with id={id}."
              });
      }
      return View(dataObject);
  }
  ```

* In the controller file, return an error page in the catch block.

  ```csharp
  catch (Exception ex)
    {
        return View("Error",
            new ErrorViewModel
            {
                RequestId = "0",
                Description = $"Exception message: {ex.Message}."
            });
    }
  ```

### MSTest

* Microsoft’s unit testing framework which is included with Visual Studio.
* It has the following annotation:
  * Test Classes are annotated with `[TestClass]`
  * Test actions \(methods\) are annotated with `[TestMethod]`
  * Initialization code that runs before each test is annotated with `[TestInitialize]`
  * Cleanup code that runs after each test is annotated with `[TestCleanup]`
* Start to test a project
  1. Open the project, Right-click the solution in the `Solution Explorer`, select `Add / New Project...`
  2. Select the `MSTest Test Project (.Net Core)` that has `C#`, create the test project.
     * By default, the test project is in the same folder as the existing project.
  3. Right-click the test project in the `Solution Explorer` and select `Add / Reference...` .
  4. Ensure `Projects` is selected on the left, select the project for testing, click `OK`.
  5. Select `NuGet Package Manager / Package Manager Console`. Run command `Install-Package Microsoft.AspNetCore.Mvc`.
  6. Write test code in the Test Method.
  7. From the Test menu, select `Windows / Test Explorer`.
  8. From the Build menu, select Build Solution. This will scan the solution for tests and place them in the Test Explorer.
  9. From the Test Explorer, click Run All to run all tests.
  10. When a test is failed, add a breakpoint. In the Text Explorer, right-click the `TestName` and select `Debug Selected Tests`.
  11. Testing project that has database connection, install `Microsoft.EntityFrameworkCore.InMemory` from `Manage NuGet Packages...` to provides an in memory simulation of the database context.
* Sample Test Method
  * Use the following structure to test and add the required directives.

    ```csharp
    [TestClass]
    public class UnitTest1
    {
        private IModelRepository db;
        public UnitTest1()
        {
            db = new ModelRepository();
        }
        [TestMethod]
        public void ModelsControllerIndexTest()
        {
          // Arrange
          ModelsController moviesController = new ModelsController();
          // Act
          ActionResult actionResult = modelsController.Index();
          // Assert
          Assert.IsInstanceOfType(actionResult, typeof(ViewResult));
          ViewResult viewResult = actionResult as ViewResult;
          Assert.IsInstanceOfType(viewResult.Model, typeof(List<Model>));
          List<Model> models = viewResult.Model as List<Model>;
          // Check the number of movies and a portion of every record and all fields
          Assert.AreEqual(3, models.Count);
          Assert.AreEqual(1, models[0].Id);
          Assert.AreEqual("Model Title", models[1].Property);
          Assert.AreEqual(new DateTime(2019, 9, 9), models[0].Property);
          Assert.AreEqual("ABC", models[2].Property);
          Assert.AreEqual(8, models[1].Property);
        }
    }
    ```
* Live Unit Testing
  1. Open the `.cs.` file for the controller.
  2. Test menu, select `Live Unit Testing / Start`.
  3. Make change to the controller file.
  4. See if the test pass or fail.
  5. From the Test menu, select `Live Unit Testing / Stop`.

```text

```

