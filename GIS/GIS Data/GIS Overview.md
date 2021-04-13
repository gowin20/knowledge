# GIS Overview

Created: Sep 2, 2020 3:03 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 7
UID: 202009021503

### Date: Aug 13, 2020

### Topic: GIS

### Recall

### Types of GIS

- Open-Source
    - QGIS
- Proprietary
    - ESRI ArcGIS

In GIS, we often express LONGITUDE first

Longitude : X coordinate

Latitude : Y coordinate

### How to Use QGIS

- Create a new project: the core organizing document of qGIS
- Core data model types: vector and raster (see Map Abstraction Topic)

Vector Data:

- Noncontinuous (discrete)
- Two Primary components
    - Geometry
    - Attribute Values

Raster Data:

- Continuous

Establishing Visual Heirarchy

Establishing Figure Ground

- The cartographic design and visual principle
- How users of a map distinguish its foreground from its background
- Visually differentiate the feature we want, from the features we don't care about

### Shapefiles

The most popular format for encoding GIS data

- Originally developed by ESRI (industry standard)
- Consists of **several independent files that MUST STAY TOGETHER**
- Really a series of files which constitutes a dataset. You must not separate them!

Components of a shape file:

- .shp : shapefile itself
    - Contains the boundaries and **feature geometry**
    - The file which we actually load. Even though this is a "shapefile," it is NOT THE ENTIRE SHAPEFILE
    - Required
- .dbf : the entire attribute file
    - Attribute data file
    - Contains the attribute table which we
    - Do not separate from .shp! Even if there's no attribute data, we include this file to provide the necessary attribute id fields
    - Required
- .shx : index
    - Tells the software how to interpret a shapefile's content
    - Required
- .prg & .qpg : projection specifications
    - tells the software what kind of map projection and coordinate system a map uses
    - Optional
- .xml : metadata
    - Lots of rich information about the contents of the shapefile and other files here
    - Optional

**SUMMARY:**