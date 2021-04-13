# GIS Data Models

Created: Sep 2, 2020 3:01 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 7
UID: 202009021501

### Date: Aug 13, 2020

### Topic: Data Models

### Recall

### Overview

- A set of rules used to describe and represent the real world digitally
- Formalized version of Map Abstraction
- To model the real world, we have to make explicit decisions about how to represent features. They must be consistent and precise
- Entities / Features
    - Anything in the real world that we would like to model!
    - Can be either discrete (borders) or continuous (light pollution)
- Geometric Form
    - All entities have a geometric form. Discrete features are representable via points, lines, and polygons
    - Can be nested within each other (x/y → latitude/longitude)
- Attributes
    - All entities have attributes. This is the information which we actually work with
- Data Model Abstraction Levels
    - Real World (no abstraction)
    1. Conceptual Model
        - Definitions and parameters for the attributes we're interested in
        - Attributes
        - ex:
            - What is a lake?
            - What about lakes are we interested in? (pH, depth, size, species richness, location, etc.)
            - Thresholds for including things in the definition (no puddles or ponds!)
    2. Logical Model
        - Formalize the definitions and measurements of attributes
        - Establish consistent rules for describing, including, and excluding objects. They should also have a location / spatial aspect
    3. Digital Model
        - Describe and represent the features which were defined earlier

### Raster Data Models

- Widely used in all technology
    - JPEG, BMP, and TIFF formats
    - All LCD Displays

The raster data model consists of rows and columns of equally sized pixels connected to form a planar surface

- The pixels form the building blocks for creating points, lines, and surfaces
- Relies on a **uniform series** of square pixels, grid-based
- Each cell holds attribute values
- Raster model displays the **average** of all attribute values on a pixel
- Size of the grid determines the spatial resolution of the raster model - all about **granularity**
    - "1 kilometer image" == each pixel is 1km x 1km
    - Using an overly coarse resolution will cause information to be lost
    - Using an overly fine resolution will cause the file size to be huge and everything to be slow
- Types of raster data:
    - Scanned maps
    - Aerial Photographs
    - Land Use / Land Cover maps
    - Other maps which represent continuous features

Advantages of Raster:

- Easy to create this kind of graphics, widely supported
- Underlying data structure is pretty simple

Disadvantages of Raster

- Files are very large
- Less pretty than their vector counterparts - looks like Minecraft
- Geometric transformations from map projections can be an issue
- Only good for some types of analysis

### Raster Encoding

1. Cell-by-cell raster encoding
    - Encodes a raster image by creating a unique record for EACH CELL by row and column

    ![[GIS Data Models/Untitled.png]]

2. Run-length raster encoding
    - Employs "runs" of similarly valued pixels to make a more efficient dataset

    ![[GIS Data Models/Untitled 1.png]]

3. Quad-tree raster encoding
    - Divides the raster into a hierarchy of quadrants
    - Each quadrant is subdivided based on similarly valued pixels
    - Division stops when a quadrant is made of cells of the same value
    - A quadrant that can't be subdivided forms a leaf node
    - Indexed spatially

    ![[GIS Data Models/Untitled 2.png]]

### Vector Data Models

Vector Data uses X+Y coordinates to represent spatial features

- Points, Lines, Polygons

**Topological Information:** info about how features interact with each other in space

- Does the data model contain topological information?

Without topological Information

- QUICK retrieval
- Spaghetti model: each feature has its own shape (all state borders represented multiple times)
- High redundancy, inefficient
- Limited Spatial Analysis

    Popularly used in Computer Aided Design (CAD)

    - CAD uses Local Drawing Coordinates
    - Objects aren't uniquely identified, and have no topological data

Topological Vector Model

- All about relationships and connectivity
- **Nodes:**
    - the place where two lines / arcs intersect
    - endpoints
    - a point along a line
- **Arcs:**
    - A segment between two nodes - 1 start node and 1 end node
- All polygons must be closed
- No overshooting or undershooting lines
- All arcs must be connected by nodes

    ![[GIS Data Models/Untitled 3.png]]

### Key Topological Concepts

1. Connectivity (arc-node topology)
    - Nodes define the shape of an arc
    - Arcs all connect to each other at nodes
2. Area Definition
    - Arcs that surround an area form a polygon
    - Polygons are defined by a set of X/Y coordinates that enclose an area
    - Each arc is stored only ONCE

    ![[GIS Data Models/Untitled 4.png]]

3. Contiguity
    - All arcs have a direction (from start node to end node) and adjacency (left or right)
    - Polygons that share an arc are adjacent
    - Universe Polygon: giant polygon containing EVERYTHING in GIS

    ![[GIS Data Models/Untitled 5.png]]

So what?

- Automatically detect errors: snap undershoots, clean up overshoots
- Spatial Analysis
- Surface Analysis
- Network Analysis
- Contiguity Analysis

Cadastral Mapping 

Advantages

- Good representations of discrete phenomena
- Accurate graphics
- Scalable
- Topology allows us to use error detection

Disadvantages

- Complex Data Structures
- Implementing Spatial Analysis is pretty tough stuff

**SUMMARY:**