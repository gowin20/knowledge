#cartography #gis180
# Cartographic Generalization

Created: Feb 21, 2021 6:29 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 180
UID: 202102211829



**See [[Cartographic Scale]]**



# Map Transformation Process

![[GIS/GIS Data/Cartographic Generalization/Untitled 3.png]]

The process of abstracting observations about the real world into a map. We've talked about several stylistic ways to do this, in the first few assignments of this course.

- Selection: choosing which classes of features to include on a map
- Classification: using classification tools to create things like choropleth maps
- Symbolization: applying appropriate symbols and labels

Now, we will learn about cartographic generalization.

**Cartographic Generalization:** the process of simplifying and reducing the unnecessary information and detail in our maps, by altering the geometry of the features

- Messy maps are chaotic! **Map chaos**
- Maintains basic geography and location of the spatial features and objects!!

# Vector Generalization Techniques

The process of generalizing the shapes in a vector file

### 1. Simplification

Reduces the density of points within vector features

![[GIS/GIS Data/Cartographic Generalization/Untitled 4.png]]

### 2. Smoothing

Reduces the angles between linear features

- Looks nice, but increases the number of points comprising a line

![[GIS/GIS Data/Cartographic Generalization/Untitled 5.png]]

### 3. Aggregation

Combines and groups points into areal features

- "Points within a certain distance should combine to form a polygon"

![[GIS/GIS Data/Cartographic Generalization/Untitled 6.png]]

### 3. Amalgamation

Merges areal features into a larger areal feature 

![[GIS/GIS Data/Cartographic Generalization/Untitled 7.png]]

### 4. Collapse

Change the details for an entity to a symbol

- At smaller scales, not appropriate to represent densely clustered vectors as polygons or lines. Turn them into point features so that they can be represented as symbols instead.

![[GIS/GIS Data/Cartographic Generalization/Untitled 8.png]]

### 5. Merging

Combine line features

- useful at smaller scales

![[GIS/GIS Data/Cartographic Generalization/Untitled 9.png]]

### 6. Refinement

only keep a selected part of an object

- good for removing extraneous features like highway on/off ramps at smaller scales

![[GIS/GIS Data/Cartographic Generalization/Untitled 10.png]]

### 7. Exaggeration

Enlarge part of an object in order to preserve the shape of objects at smaller scales

![[GIS/GIS Data/Cartographic Generalization/Untitled 11.png]]

### 8. Enhancement

Illuminating specific elements of an object - highlight them!

- for example, to highlight one street bridging over another

![[GIS/GIS Data/Cartographic Generalization/Untitled 12.png]]

### 9. Displacement

Separate objects more

![[GIS/GIS Data/Cartographic Generalization/Untitled 13.png]]

# Overall Goals of Generalization

We want to remove errors and unnecessary detail

This might include

- lines from physical maps
- classified data
- erros
- unnecessary detail

Below: speckled reference map resulting from high density of mapped points. Each point represents a biome at a selected region, but it's too general to interpret

![[Untitled 14.png]]

# The Proper Amount of Generalization

- generalize more at smaller scales
- show more detail at larger scales
- thin lines show more detail of the polygon; thick lines hide jagged edges and misaligned data (e.g. between country datasets)
- Check curvilinear lines
    - coastlines, rivers, boundaries
    - if these lines collapse into a polygon (2D area), it needs to be generalized more!
    - If there are sharp angles, it's too generalized

![[Untitled 15.png]]

**Left:** Low levels of generalization; **Right:** high levels of generalization