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

## ArcMap

### Import and Export

- It can import shape file with `.shp` extension and display it using different projected coordinate system.
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

#### Geoprocessing Tools

- Clip - create a new layer from an input layer using a mask.
- Intersect - create a new layer that is a geometric intersection of the input layers.
- Union - data from input layers combined to create output layers.
- Merge - combine two dataset into a larger output layer.
- Buffer - create new features(shapes) to represents the area within a given distance of an input feature
- Thiessen(Voronoi) - create new features(shapes) to represent the area nearest to each input point feature
- Spatial Join
