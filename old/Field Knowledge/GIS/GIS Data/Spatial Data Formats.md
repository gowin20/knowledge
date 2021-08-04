# Spatial Data Formats

Created: Jan 16, 2021 10:45 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 181A
UID: 202101162245

# [[Vector Data]] File Formats

All vector formats store ONE OR MORE of these types of geometry: points, lines, and polygons

Store GEOMETRIES as well as ATTRIBUTES

### Binary Encoding

- Shapefile (ESRI)
    - most popular by far, created by ESRI
- MapInfo .TAB
    - only used by MapInfo, another commercial GIS
- Spatialite (SQLite)
    - portable format
    - easily perform queries, etc. without additional software

### Text Encoding

In this format, geometries are encoded as arrays/lists of coordinates. These define the boundaries of the shape

- GeoJSON
    - spatial extension for JSON files (JavaScript Object Notation)
    - Used frequently in Web Mapping, Web GIS
    - Basically just JSON, but it can encode coordinates in its dictionaries
- Geography Markup Language (GML)
    - OGC-based XML spatial data standard
    - Markup language like XML/HTML, so it uses tags
    - Each feature has attributes as well as locations, etc.
- KML (Google)
    - Google Earth, other Google mapping products use this natively
    - Most similar to GML

![[old/Field Knowledge/GIS/GIS Data/Spatial Data Formats/Untitled.png]]

The highlighted files are those which make up a single shapefile. Additionally, there is a KML file, GML file, and GeoJSON file

# [[Raster Data]] File Formats

Gridded arrays of data values, with each band of the raster file corresponding to a different attribute! Basically just a giant rectangular grid, potentially with multiple layers

Used for data which has continuous values across space, like elevation

- GeoTIFF (.tif)
    - lossless image storage format with spatial awareness
    - similar to normal TIF files, but GeoTIFF provides additional spatial context
    - most common interchange format
- MrSID (.sid)
    - highly compressible format
    - used for aerial imagery, remotely sensed imagery
    - good for communicating large quantities of information
    - lossy!
- Esri Grid
    - proprietary format developed for ArcGIS
- Digital Raster Graphic (DRG)
    - used for digitized USGS products

### Raster Compression

Uncompressed rasters store each pixel individually

Lossless compression (like run length encoding, RLE) allows you to reassemble the image in full resolution

Run Length Encoding:

![[old/Field Knowledge/GIS/GIS Data/Spatial Data Formats/Untitled 1.png]]

For large files, not practical to do everything lossless

Lossy compression discards image detail, usually those not perceptible to the human eye

PNG vs JPG, i mean come on