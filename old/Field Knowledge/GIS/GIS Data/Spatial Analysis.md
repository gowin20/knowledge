# Spatial Analysis

Created: Sep 2, 2020 2:58 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 7
UID: 202009021458

### Topic: Spatial Analysis

### Recall

### Spatial Analysis

is used:

- Inductively — Examine evidence to look for patterns supporting new theories
- Deductively — Tests known theories against data
- Normatively — Develop new strategies for locational analysis

### Queries

- A question posed by a user, ex. searching a location on Google Maps
- Returns a subset of all the information avaiable to the database
    - Doesn't modify the information in any way!
- It's just SQL

Definition Queries

- State="CO"
- Population < 100,000
- Seems to be just attributes

Spatial Queries

- Cities in California, Census Tracts in LA County
- Based on Topology
- uses specific terms: "Within," "Neighbor," "next to," "identical to," "near," etc.

### Intersect

![[old/Field Knowledge/GIS/GIS Data/Spatial Analysis/Untitled.png]]

### Contain: One thing is completely within another

![[old/Field Knowledge/GIS/GIS Data/Spatial Analysis/Untitled 1.png]]

### Measurements

Numerical values decribing specific aspects of geographic data

Uses algorithms to determine length, area, shape, relationships, distance, direction

- Distance
    - Euclidian Distance
        - Pythagorean

            ![[old/Field Knowledge/GIS/GIS Data/Spatial Analysis/Untitled 2.png]]

    - Manhattan Distance
        - Block-based distance for when it's not possible to travel "as the crow flies"

            ![[old/Field Knowledge/GIS/GIS Data/Spatial Analysis/Untitled 3.png]]

    - When digitizing from a map, GIS tends to underestimate line length
    - When vectorizing from a raster, GIS tends to overestimate line length
- Polygon Area
    - Raster area calculation is e.z.
    - To find area of a polygon with n+1 vertices x,y:

        ![[old/Field Knowledge/GIS/GIS Data/Spatial Analysis/Untitled 4.png]]

- Polygon Shape
    - Compactness:
        - Ratio of the perimeter of the polygon to the circle with equivalent area

            ![[old/Field Knowledge/GIS/GIS Data/Spatial Analysis/Untitled 5.png]]

        - Applications in creating congressional districts, etc.
- Polygon Centroid
    - Center of gravity or mass

        ![[old/Field Knowledge/GIS/GIS Data/Spatial Analysis/Untitled 6.png]]

### Buffers

- Common Vector analysis tools that help us figure out proximity
- The areas within a specified distance of selected features
- used on any kind of vector
- Two primary types
    - Constant Width: We input a value by which features are buffered. Kinda like text
    - Variable width: use a buffer field in the attribute tabl

![[old/Field Knowledge/GIS/GIS Data/Spatial Analysis/Untitled 7.png]]