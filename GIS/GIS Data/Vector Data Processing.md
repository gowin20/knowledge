# Vector Data Processing

Created: Jan 28, 2021 2:55 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 181A
UID: 202101281455

Kinda like raster data processing

1. Input Functions
    - map digitizing
    - image scanning
    - inporting / converting data
2. Analysis Functions
    - Non-topological (attributes) functions
    - Topological (spatial relations of objects) functions
3. Output Functions
    - Presenting results obtained from analysis functions in the form of maps, tables, and graphs

# Map Digitizing

Steps to digitize a map:

1. Acquisition through digitizing, compilation
2. Verification and editing
3. Formatting and Translation
4. Linking graphical data to associated attribute data

![[Vector Data Processing/Untitled.png]]

## Maintaining the Integrity of Datasets

![[Vector Data Processing/Untitled 1.png]]

1. Lines intersect where they are expected to intersect (no overshoots or undershoots)
2. Nodes are created at ALL points where lines intersect
3. ALL polygons are closed
4. Each polygon contains a LABEL POINT
5. Topology can be built ('CLEAN' & 'BUILD' in ArcGIS)

Digitizing environments permit tolerance settings where nodes automatically snap to lines, and polygons are automatically closed