# Tableau

## Introduction

- It is a business intelligence tool that can be used to analyze data and generate interactive data visualization, founded in 2003 by Christian Chabot, Pat Hanrahan and Chris Stolte, in Mountain View, California
- It is availble for Windows and MacOS platform, [Click](https://www.tableau.com/products/trial) to download the software or run `brew cask install tableau` on MacOS
  - Free trial is available for 14 days
  - Students or Teachers can obtain one-year Tableau licenses at accredited academic institutions through our Tableau for Students program
    - Registered Students can have access to eLearing and discount for taking Tableau Desktop Specialist Exam
  - One product key can be used to activate two machines. To activate more machines, deactivate one of those two activations first
- [Free Training Videos](https://www.tableau.com/learn/training/20203) are available at its official website
- [Tableau eLearning](https://www.tableau.com/learn/training/elearning) is a web-based interactive training program
  - eLearning for Creator is for Tableau Desktop and Tableau Prep
  - eLearning for Explorer is for Tableau Online or Tableau Server
- [Tableau Desktop Specialist Exam Readiness](https://www.tableau.com/learn/training/specialist-certification-prep) is a training and certification bundle that includes Tableau Desktop Specialist exam voucher, access to eLearning for Creator and Tableau Desktop software extended trial
- [Tableau Certification](https://www.tableau.com/learn/certification) for individuals includes:
  - Tableau Desktop Specialist
  - Tableau Desktop Certified Associate
  - Tableau Desktop Certified Professional
  - Tableau Server Certified Associate
  - Tableau Server Certified Professional
- It can import to various data files and connect to 50+ types of database
- It can create 24 diffferent types of charts
- Tableau products:
  - Tableau Desktop - creating reports
  - Tableau Online - creating reports
  - Tableau Server - publishing reports
  - Tableau Reader - publishing reports
  - Tableau Public - publishing reports publicly
  - Tableau Prep - Preparing data
    - Tableau Prep Builder - building data flows
    - Tableau Prep Conductor - scheduling, monitoring and managing flows across the organization
  - Tableau Vizable - Consumer data visualization app for iPad
  - Tableau Mobile - Mobile App view reports published on Tableau Server or Tableau Online
  - Tableau CRM - CRM (customer relationship management) analytics

## Tableau Desktop

- It is used to generate graphs on worksheets from data source
- Multiple worksheets can be used to create a dashboard
- Multiple dashboard and worksheets can be used to create a story

### Connect to a Data Source

- Click the `Add Database` button or `Connect to Data` button to connect
- Data is added by either importing files or connecting to a database
- Connection to Google Analytics 4 is currently not supported, universal analytics from GA is supported

### Create Worksheet

- Once data source is connected, Click view icon beside each sheet name to view in a separate window
- Once data source is connected, each table can be opened as a sheet(Worksheet) by dragging it to the right, then click `Sheet` button on the button navi bar to open the sheet
- First row from the data source is usually the field names
  - Select multiple column titles and right click to pivot
  - Assign the proper data type to each column title
- Drag two table to the right to inner join two tables
- Double click column name to rename
- Click the drop-down for each field on the right to hide/unhide column, reset column name, copy，or split data in each row to two columns
- Click the icon beside field name to sort its data
- The table name for each field is described in the grey text above field names on the right data panel
- Use custom split to specify the seperator
- Change rows number in the input box to view the first `n` rows
- Data Types can be show on the right as icon for each column
- Number(Hash tag icon)
  - decimal
  - whole
- Date(Calendar icon)
- Date & Time(Calendar with clock icon)
- Boolean(`T|F` icon)
- String(`Abc` icon)
- Geographic Roles(Globe icon)
- Sort the column names from left to right by using the `Sort fields` drop-down

### Work with Worksheet

- All numerical values are considered as `Measures`, All others data are considered as `Dimensions`
- Graphs will be drawn based on field types selected for the `Columns` and `Rows` input
  - Drag a `Dimensions` data to `Columns` and a `Measures` data to `Rows` can generate a vertical bar chart
  - Drag a `Measures` data to `Columns` and a `Dimensions` data to `Rows` can generate a horizontal bar chart
  - Drag a `Dimensions` data to `Rows` and a `Measures` data to `Marks` can generate a table
  - Drag a `Date` data to `Columns` and a `Measures` data to `Rows` can generate a line chart
- Addition Data can be dragged to the Marks section and add additional info to the graph
  - Drag `Measures` to `Color`, higher values will have a darker color
  - Drag `Measures` to `Label`, the values will be printed on the graph
- Data selected for `Columns` and `Rows` can be swapped by click the `swap` icon in the tool bar
  - or press `Ctrl + W`
- Multiple fields can be dragged to `Rows` or `Columns`
- Fields from the left column can be dragged and combined into a hirearchy, name the hirearchy the the field in the input on the right will have a plus icon
- Date data type is a hirearchy by default
  - It can have `Year`, `Quater`, `Month`, `Date` by default
  - Graph is discrete by default, click the drop-down to select the continuous graph
- Data can be reformatted by opening the drop-down from the field name after dragging, and selecting the desired format
  - Changing font size and color by select `format..` in the drop-down
- When connected to a database, `Live` option will update data in sheet dynamically and `Extract` option will take a snapshot of the data table
  - Right click the data source icon in the left panel and select `Refresh` to reload data when using `Live` option
  - Right click the data source icon in the left panel and select `Extract -> Refresh` to reload data when using `Extract` option
- Click the sort icon beside the text for each axis on the graph to sort
  - Sort icons can be clicked three times, they will sort in ascending order, descending order, and cancel sort
- Select selected data field in the `Columns` or `Rows`, then click the sort button to sort
- Use the data field drop-down in the `Columns` or `Rows`, the click sort to do advanced sort
