# The Data Collection Workflow

Created: Sep 2, 2020 3:00 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 7
Topic: [[Data Structures in GIS]]
UID: 202009021500

### Date: Aug 27, 2020

### Topic: Proper Data Collection Workflow

### Recall

Planning

Preparation

Digitizing

Editing

Evaluation

Orthophotos

Data Conversion

SDTS

Edgematching

### Notes

Data Sources

- Tons of different places online. Wherever you can find data honestly
- Free Data from the Government
    - USGS Topo Maps
    - Census Data
    - NOAA
    - NASA
    - Local Governments, like LA County
- Paid Data from the Government
- Internet map servers
- Commercial Data
    - ESRI
    - EastView Cartographic
- Data from other GIS users

ALWAYS look for existing data, before trying to create your own!

### Spatial Data Capture

- Takes 85% of our time, money, and energy! Very time consuming and expensive

Primary Spatial Data Sources

- Gather data ourselves
- Raster data capture
    - Remote Sensing
        - Aerial Photos
        - Sattelite Imagery
        - LiDAR data
    - Indirect measurement
- Orthophotos
    - A photo map with details corrected using map geometry
    - Corrects for angular imperfections, adjusts for irregularities in terrain
    - Makes things "flat" for use in maps
- Vector data capture
    - Ground Surveying (Street lights, gas lines, etc.)
    - GPS
    - Mobile Devices, Tablets, phones (creates vector data as points, lines, or polygons by walking around)

Secondary Spatial Data Sources

- Data that has been collected by someone else
- Heads-up Digitizing
    - A combination of scanning and manual digitizing
    1. Scan the map
    2. Register the map
        - Control points, transformed into real world coordinates
    3. Digitize on-screen (trace points, lines, and polygons onto a map)
- Automated Digitizing
    1. Automatically converts a RASTER scan to vector lines
    2. Requires image to be very clean, have well-defined boundaries
    3. Semi-automated is the best of both worlds

Issues to watch out for

- Data conversion among formats
- Data conversion between map projections
- Organizing data storage
- Correction of errors : Spatial, Attribute, meta data
- Topological Errors
    - Undershoot / Overshoot
    - Dangling nodes
    - Pseudo nodes
    - Direction Errors, Label Errors

Data Conversion

- Direct Conversion
    - From one proprietary format to another
    - MapInfo MIF → ArcGIS Shapefile (MIF-to-Shapefile Command)
- Neutral Conversion
    - From a proprietary format to a neutral one
    - Spatial Data Transfer System (SDTS)
    - Can be read by any number of GIS

Registration: Transforming paper coordinates to real world coordinates

- Rotation, Translation, and Scaling operations

Edgematching

- Joining adjacent spatial layers
- Make sure that lines along the edges of layers match up, so that the lines are continuous across the border

**SUMMARY:**

---