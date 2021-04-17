# Map Abstraction & Fundamentals

Created: Sep 2, 2020 3:04 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: [[Field Knowledge/GIS/7]]
UID: 202009021504

Date: Aug 13, 2020 

### Topic: Types of Maps

### Recall

### Notes

- Mental Maps
    - Everyone has them
    - continuously evolving
- Reference Maps
    - Emphasis on geographic data. aims to preserve things as accurately as possible
    - Used for... reference
    - Represents scale in 3 ways:
        - Descriptive, "1 centimeter == 1 kilometer"
        - Graphic, "scale bar"

            ![[Field Knowledge/GIS/GIS Data/Map Abstraction & Fundamentals/Untitled.png]]

        - Representative Fraction, "1 : 24,000"
- Thematic Maps
    - About a particular theme
    - conveys information, doesn't care about geographic accuracy
    - Cartograms, etc.
    - Choropleth Map
        - Map containing polygon features, where polygons are shaded on the basis of any given attribute

All maps share a **scale**

**SUMMARY:**

---

### Date: Aug 13, 2020

### Topic: Map Abstraction

### Recall

### Notes

Map Abstraction: The process by which we turn real world objects into features on a map

Let's figure out **what to include** and **how to include**

- Scale : The factor by which things are reduced in order to be shown
    - Relationship between detail and area
    - Large-scale maps are ZOOMED IN (1:2 scale)
    - Small-scale maps are ZOOMED OUT (1:5,000 scale)
        - does not correspond to area, the "large" and "small" describes the amount of detail
- Map projection : the math formula we use to transform the 3d world into 2d
    - distortions are inevitable

### Feature: a prominent part, characteristic, or quality of earth and its surface

Features on the earth:

- Discrete Features
    - Have clearly defined boundaries
    - Readily seen
    - Buildings, roads, parks, etc.
- Continuous features
    - no clearly defined boundaries
    - Generally over a large area (small scale), hard to see
    - elevation, temperature, rainfall

### Vector Data: Representing Discrete Features

- Points
    - X, Y points
    - A SINGLE vertex
    - Trees / hydrants
- Lines
    - Two or more vertices
    - Roads, rivers
- Polygons
    - Three or more vertices
    - Lakes, parks, any areas

### Raster Data: Representing Continuous Features

an EVENLY SPACED rectangular grid

- each grid based on geographic coordinates
- Contains a **z-value** which represents the feature of interest (elevation, temperature, etc.)

**Spatial Resolution**: the smallest distance between two adjacent features that can be detected in an image. We base our value ranges off of this resolution

![[Field Knowledge/GIS/GIS Data/Map Abstraction & Fundamentals/Untitled 1.png]]

^ raster data

![[Field Knowledge/GIS/GIS Data/Map Abstraction & Fundamentals/Untitled 2.png]]

While vector data is more of "how we see the world", raster data is more "complete" as every cell has a value

**SUMMARY: We take our physical world and abstract it such that it can be represented on a map**