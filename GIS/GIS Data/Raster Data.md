# Fundamentals of Raster Data

Created: Jan 27, 2021 11:47 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 181A
UID: 202101272347


# What is a Raster Image?
A field based model of geospatial data representation

characterized by tessellations of shapes that completely cover a 2D surface
AKA: PIXELS

**Pixel: short for PICTURE ELEMENT**  Pic - El
Grid of pixels = image, duh



**basic spatial unit:** a predefined area of space for which attribute data are recorded.

- regular tessellations: shapes that occur regularly across space and have a consistent shape. includes pixels

![[GIS/GIS Data/Fundamentals of Raster Data/Untitled.png]]

- irregular tessellations:
    - TIN raster model :triangulated irregular network
    - made of shapes of different shapes and sizes

        each red point has a radius around that. wherever those circles intersect, a vertex of a triangle is placed

        ![[GIS/GIS Data/Fundamentals of Raster Data/Untitled 1.png]]

# Anatomy of Raster Data

![[GIS/GIS Data/Fundamentals of Raster Data/Untitled 2.png]]

Each spatial attribute has its own layer!

## Data Formats for Raster:

- BMP
- TIFF
- GeoTIFF
- GIF
- JPEG
- PNG
- MrSID
- GRID

# Advantages:

- effectively represent continuous surfaces
- FAST processing for computers!
    - raster is faster, vector is corrector
    - more common nowadays to integrate both types
- quickly display, visualize surface data
- lots of data available
- handle VERY large datasets
- model over surfaces