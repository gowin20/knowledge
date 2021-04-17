# Fundamentals of Vector Data

Created: Feb 5, 2021 8:55 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 181A
UID: 202102052055

Variant of **object-based** models of geospatial data representation

Best suited for discrete objects, as opposed to raster data's continuous style

Represented as **points, lines (arcs), and polygons (areas)**

**Feature class:** thematic groups/collections of common features that share the same geometric representation

- fire hydrants (points)
- roads (lines)
- parcels of land (polygons)

Inside databases, feature classes are logically organized into layers or themes

- For example, a **drainage theme** with the following feature classes:
    - drain, drainage grate → point
    - drain pipe, network of popes → lines
    - drainage pond → area/polygon

![[Field Knowledge/GIS/GIS Data/Fundamentals of Vector Data/Untitled.png]]

Each layer contains **one and only one** type of geographic element

![[Field Knowledge/GIS/GIS Data/Fundamentals of Vector Data/Untitled 1.png]]

All three data types are intimately related:

- Any particular location can be defined by a set of points (x,y)
- A line is defined by a set of two or more points
- A polygon is defined by a set of three or more points!

Each point has an identifier (A), and possibly a number associated with it

Pay attention to the picture above! Shapes are delineated by an Identifier plus the number of verticies it possesses. The given number of verticies follows

![[Field Knowledge/GIS/GIS Data/Fundamentals of Vector Data/Untitled 2.png]]

### Building Topology

Topology: defining how one thing is related to another in space

The relationships between things!

Defining arcs(lines) is Arc-node topology

![[Field Knowledge/GIS/GIS Data/Fundamentals of Vector Data/Untitled 3.png]]

Polygons are defined as a series of lines!

![[Field Knowledge/GIS/GIS Data/Fundamentals of Vector Data/Untitled 4.png]]

Permits more advanced geographic analysis based on what things border each other!

Keep in mind the directions of the individual lines that makes up polygons

Directionality determined by start → end

the space **Surrounding** our area of interest is called the **universe polygon**

- denoted as "A" in the picture above

### Advantages of Vector Data

- effectively represent discrete features
- more compact and efficient when compared to rasters
- cartographic representation and quality
- sophisticated handling of attribute data

### Disadvantages of Vector Data

- more complex data model!
- difficult overlay analysis
- not good at presenting spatial variation
- compiling and collecting vector data is a little more expensive time/resource wise