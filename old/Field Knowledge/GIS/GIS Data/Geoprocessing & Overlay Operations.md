# Geoprocessing & Overlay Operations

Created: Sep 2, 2020 2:59 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: [[old/Field Knowledge/GIS/7]]
UID: 202009021459

### Date: Sep 2, 2020

### Overlay Analysis

- Taking two or more maps, and overlaying them to create a single output data layer
- Multivariable analysis
- Vectors and rasters together
- Might need to change attribute data! Everything must also be properly registered and projected
1. Point-in-Polygon
    - ex. "All restaurants within a service area"

    ![[old/Field Knowledge/GIS/GIS Data/Geoprocessing & Overlay Operations/Untitled.png]]

2. Line-in-polygon

- ex. "which portions of road each county is responsible for"

![[old/Field Knowledge/GIS/GIS Data/Geoprocessing & Overlay Operations/Untitled 1.png]]

3. Intersection

- preserves features common to both layers

![[old/Field Knowledge/GIS/GIS Data/Geoprocessing & Overlay Operations/Untitled 2.png]]

4. Union

- preserves all information from both layers

![[old/Field Knowledge/GIS/GIS Data/Geoprocessing & Overlay Operations/Untitled 3.png]]

5. Symmetrical Difference

- kinda like an inverted intersection

    ![[old/Field Knowledge/GIS/GIS Data/Geoprocessing & Overlay Operations/Untitled 4.png]]

6. Identity

- prioritizes the first layer

    ![[old/Field Knowledge/GIS/GIS Data/Geoprocessing & Overlay Operations/Untitled 5.png]]

7. Clip

- Like cropping, crop the dataset according to some polygon

8. Erase

- Use a polygon to erase all information within a particular area

9. Split

- Overlays a "split layer" over some input layer, and splits it into different layers of analysis
- Opposite of Merge

    ![[old/Field Knowledge/GIS/GIS Data/Geoprocessing & Overlay Operations/Untitled 6.png]]

10. Merge

- Combines features withing a point/line/polygon layer into a single feature containing all the attribute information
- First attribute encountered is the value. The remaining attributes are lost
- Useful when polygons overlap / are duplicates

### Geoprocessing Operations

Tools which we use to manipulate vector datasets - automate repetitive preprocessing

All about manipulating the actual spatial data, instead of attributes associated with them

Union, Intersect, Symmetrical Difference, and Identify overlay methods

- Dissolve Operation
    - Combines adjacent polygon features in a layer based on a single attribute
    - Returns a layer with the same extent as original, but without random line segments
- Append
    - Combines the spatial extent of two or more layers
    - Returns a layer with the same feature type as the input layers (point, line, or polygon)
    - Input layers must be of the same type
- Select
    - Creates a layer based off of a user's query

![[old/Field Knowledge/GIS/GIS Data/Geoprocessing & Overlay Operations/Untitled 7.png]]

**SUMMARY:**

---