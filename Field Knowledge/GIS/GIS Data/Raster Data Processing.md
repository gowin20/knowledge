# Raster Data Processing

Created: Jan 27, 2021 11:54 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 181A
Topic: [[structure test]]
UID: 202101272354

Three classes of procedures for [[Raster Data]]:

1. Input Functions
    - Prepare and structure raster datasets for use in GIS
    - georeferencing, editing, etc
2. Analysis Functions
    - figure out spatial relationships contained within the data
    - logical operations, raster algebra, overlay, modeling
    - used for hydrology, watershed, all sorts of uses
3. Output Functions
    - present our results in the form of various maps, tables, and graphs

# Georeferencing an Image

Converting a raster dataset from the native raster coordinate system (x,y) into a GCS (long, lat)

![[Field Knowledge/GIS/GIS Data/Raster Data Processing/Untitled.png]]

- Easting == X
    - Northing == Y
- (row,column) in Raster. that's y,x
    - (Easting, Northing) in Maps
- Raster: origin on top left, start counting from there
    - MCS / GCS: origin at 0,0, but it's in the lower left

By applying GCS to raster data, we produce an image that's free of geometric distortions and errors

Two ways to georeference images:

### Image to map rectification

apply geographical coordinates to image/raster coordinates

- Spatial interpolation by coordinate transformation
    - Identify ground coordinates in terms of eastings and northings for **control points**
    - solve a set of polynomial equations using image coordinates of control points, with their corresponding ground coordinates. These equations relate the image with the real world
- Attribute interpolation by resampling
    - determine new attribute values for cells aligned to the geographic coordinate system
    - apply geographic space to the image

### Image to Image rectification

apply geographical coordinates from a previously georeferenced image, to a non-georeferenced image