# Map Projections

Created: Sep 2, 2020 3:04 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: [[7]]
UID: 202009021504

### Date: Aug 9, 2020

### Topic: Map Projections

### Recall

### Notes

- [https://thetruesize.com/](https://thetruesize.com/)
- [https://www.jasondavies.com/maps/transition/](https://www.jasondavies.com/maps/transition/)
- RF: Representative Fraction
    - describes scale as a ratio
    - numerator is always one, denotes distance ON THE MAP
    - denominator is high, denotes distance IN REAL LIFE
    - 1:1,000 is a LARGER scale than 1:100,000
    - Large-scale maps show **more detail** and **less area**
    - Small-scale maps show more area, and less detail (small-scale == large area)
- Developable Surfaces
    - Geometric shape which can be laid into a flat surface without stretching, tearing, or distorting position
    - 3 Types: Cylinder, Cone, and Plane
    - SPHERE is not a developable surface because we can't flatten it while preserving distance
    - The envelop of a single parameter family of planes is called a developable surface
- GISes are **multiscalar:**
    - Can zoom in an out across a wide variety of geographic scales
- No single two-dimensional projection of the three-dimensional surface of the Earth can contain a representation of the Earth's surface or its features that does not contain distortion in some form.
    - Types of distortion:
        - Shape
        - Direction
        - Area
        - Distance
    - 

    ![[GIS/GIS Data/Map Projections/Untitled.png]]

**SUMMARY:** Can't flatten a 3d sphere while preserving distance, so map projections exist. Different map projections distort different things, giving us disparate maps