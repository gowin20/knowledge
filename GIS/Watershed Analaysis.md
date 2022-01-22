Author: Solomon Vimal
URL: 
Tags: #literature-note 
#GEOG181B #GIS 

---
Watershed Analysis and layer creation


**watershed**: a region of arbitrary size, within which all water in that region exits the region at a single point
- also known as a catchment or basin
- defined by where you place the point - arbitrary size
- nested concept: huge watersheds cover massive parts of earth, containing smaller and smaller watersheds within
- Outlet: 

### Channel Initiation:
the closer channels begin to drainage divides, the greater the number of channels that occupy a unit area, and therefore the more dissected the landscape will be.

It's important to predict where channels begin! Channel being a water path. This forms a key component of landscape evolution theories

### Overland Flow
Perennial Stream: water all year
Ephemeral Streams: water only part of the year
Overland flow rate is governed by soil infiltration capacity and topographic slope
Channel flow is governed by channel hydraulic geometry

100km^2 of area is needed before a river appears on the surface

![[Pasted image 20210829165424.png]]

these "grid cell thresholds" are defined by us, the people creating these files. "100 grid cell threshhold" means 100 cells must surround a pixel in order for that pixel to be designated as a river. "1000 grid cell threshold" means there will be 1 river pixel for every 1000 surrounding.

to compare files (such as calculated reach vs actual reach), we can create a difference raster

# Deriving a watershed using a DEM file
5-6 steps in total




![[Pasted image 20210829165856.png]]