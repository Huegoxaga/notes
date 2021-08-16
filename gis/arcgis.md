# ArcGIS Platform

- The premier commercial desktop GIS software platform, developed by Esri(Redlands, California)
- It contains many components that communicate with each other via the ArcGIS REST API and common file formats.
- It provides the following products.
  - ArcGIS Pro - a new, integrated GIS application, planned to eventually supersede ArcMap and its companion programs. ArcGIS Pro works in 2D and 3D for cartography and visualization, and includes Artificial Intelligence (AI).
    - It works with many additional extensions.
  - ArcMap is the application used to view, edit and query geospatial data, and create maps.
  - ArcGIS Online - It is web app builder for GIS
  - ArcGIS SDKs - It is the GIS SDKs and APIs for developing web apps and mobile apps.
- Products can be sold is suites or seperately. e.g. ArcGIS Desktop contains ArcGIS Pro and ArcMap. [click here](https://www.esri.com/en-us/arcgis/products/index) for details.

## ArcGIS Pro

- It is the lastest Desktop GIS product from Esri
- It is created to replace ArcMap, and it is similar to ArcMap

### Import and Export

- It can import vector data format in a shape file with `.shp` extension and display it using different projected coordinate system.
  - shape file are consisted of basic shapes(lines, polygon etc.) and has attribute info associated with each shape.
  - the first shape file coordinate system decide the default coordinate system of the working layer
- It can import `csv` file and display the coordinates(`X`, `Y`) in each record as an event layer on the map.
  - make sure the point uses geographic coordinates system, instead of the default.
  - An event layer can be exported as a `.shp` file and added as a shape file layer for more functionality.

### Queries

- It can query shapes inside the shape file based on the relationship of the shapes using the `Select by Location` tool.
  - relationships of shapes from different layers can also be queried.
- It can query shape data content by using the `Select by Attributes` tool.
- queries that join data based on the coordinates of the shape is called spatial join. It can be done by right click layer and choose `Joins and Relates`.
  - geoprocessing tool can also do spatial join.

### Geoprocessing

- Geoprocessing is the execution of operations on spatial data to create new information, to enhance its spatial structure, or to analyze interrelationships between existing information.
  - It is located on the top menu bar
  - click `Search for Tools` for more tools.
  - The `Arc Toolbox` includes all the available tools for geoprocessing.
  - Tools from extensions can be found in the geoprocessing tool box.
    - If not found, click `customize` -> `Extension` and click the checkbox for a certain extension to activate.

#### Geoprocessing Tools

- Clip - create a new layer from an input layer using a mask.
- Intersect - create a new layer that is a geometric intersection of the input layers.
- Union - data from input layers combined to create output layers.
- Merge - combine two dataset into a larger output layer.
- Buffer - create new features(shapes) to represents the area within a given distance of an input feature
- Thiessen(Voronoi) - create new features(shapes) to represent the area nearest to each input point feature
- Spatial Join
- Spatial Analyst Tools
  - An extension, license is required
  - Heat Map is available in the density tool set of spatial analyst tools.

### Georeferencing

- It is the process of adding coordinates to each pixel of an image.
- This can be done by using the georeferencing toolbar.
  - Rotate, Shift and Scale tools are needed to locate the image to align with the map layer as much as possible
  - add referencial relationship between point on the map layer to point on the image layer
    - street intersections are good control(reference) points
  - click the reference point on the map layer then drag it to the point on the image layer
  - serval points in different parts of the image is preferred
  - Once reference is established, points on image map will move and return an error value on the point
  - The link tables has all control points
  - Use rectify to export the image with coordinates info

### Geodatabase

- It can be stored as the following format:
  - a file system folder
    - It has a extension as `.gdb`
  - a Microsoft Access database
  - a collection of datasets stored on a netword as ArcSDE(enterprise) geodatabase
- It stores vector data or raster datasets in tables and stores the relationship between tables.
- Feature class is the "table" in a geodatabase
- Each fearure class table has a shape field with type `Geometry` and many other custom fields like `Text`, `Date`.
- Each field can have a domain which are the list of choices for the field value
- Right click the database file in the right `Catalog` panel and click create to create a new feature layer
- Digitizing features are the processes of created new feature records into the feature class by adding shapes using the `Create Features` panel.
  - Click `Edit` button in the menu bar and select `Create Features`
  - To get started, Select a type of shape to create in the `Construction Tools` section of the `Create Features` panel
  - Shape are selected by the snapping tool
    - Snapping tool bar can be opened from the `Edit` dropdown menu and select `Snapping`
    - Snapping tolerance is the smallest number of pixel recognized by the snapping tool
- Raster data can be stored in `.gdb` and imported as a layer
  - qualitative rasters data have an attribute table that count the number of cell in each categories.
  - Click the `Identify Tool`(Info Icon) to see details each cell
  - The `Reclass` tool set proviced by the `Spatial Analyst Tools` extension can be used to reclassify cell's categorical data.
  - `Raster Calculator` in the `Map Algebra` from the `Spatial Analyst Tools` extension can be used to raster overlay
    - raster overlay is a cell-by-cell(matrix) combination of raster layers, boolean calculation between the value of cells in different layers are involved

### Publish Services

- Services can be published from ArcMap to ArcGIS servers or others ArcGIS products like ArcGIS Online. Services includes:
  - Feature classes
  - Maps
  - Geoprocessing tools
  - WMS and WFS
  - KML
  - Cached map services

## ArcGIS Online

- ArcGIS Online is a website for working with maps and other types of geographic information. ArcGIS Online includes maps, data, apps, and tools (including geoprocessing services) from Esri

### Web AppBuilder

- Web AppBuilder for ArcGIS is an intuitive what-you-see-is-what-you-get (WYSIWYG) application that allows you to easily build web applications without writing a single line of code.

## ArcGIS Enterprise

- The ArcGIS Enterprise product includes the following software components that are designed to work together:
  - ArcGIS Server—the core web services component for making maps and performing analysis.
    - Running a dedicated ArcGIS Online server
    - Moving the functionality of `ArcGIS Pro` online
  - Portal for ArcGIS—allows you to share maps, applications, and other geographic information with other people in your organization.
  - ArcGIS Data Store—lets you configure data storage for hosting and federated servers used with your deployment.
  - ArcGIS Web Adaptor—allows you to integrate your ArcGIS Server and Portal for ArcGIS with your existing web server and your organization's security mechanisms.

## ArcGIS for Developers

- It provides a series of ArcGIS APIs and SDKs
- When signing in to ArcGIS for Developers, it grants access to the dashboard and tools to manage applications, monitor credit usage and manage data. The dashboard also gives you access other ArcGIS applications tools across the platform.
- The following tools are also made available
  - ArcGIS Vector Tile Style Editor - create custom styles for basemaps
  - Create a new dataset - define a new point, line or polygon feature class for your application

### ArcGIS API for JavaScript

- [Click Here](https://developers.arcgis.com/javascript/latest/guide/) to view official API guide

### ArcGIS API for Python

- [Click Here](https://developers.arcgis.com/python/guide/) to view official API guide
- [Click Here](https://developers.arcgis.com/python/api-reference/index.html) to view python documentation
