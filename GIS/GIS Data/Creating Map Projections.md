# Creating Map Projections

Created: Sep 2, 2020 2:54 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: [[7]]
UID: 202009021454

### Date: Aug 29, 2020

### Topic: Map Projections

### Recall

### Notes

### Flattening the earth (well, it's already flat!)

Real Earth → The Geoid → 3D Reference Ellipsoid → 2D Projection

![[GIS/GIS Data/Creating Map Projections/Untitled.png]]

Geoid

- a three dimensional model of the earth
- Very accurate, detailed
- No land masses! just water - earth without topography
- Used to determine the Mean Sea Level (MSL) surface underneath all the world's landmasses

Datum

- a 3d reference ellipsoid, which is a geometric object
- Used to determine surface locations
- World Geodetic System (WGS) 1984 Standard Datum

![[GIS/GIS Data/Creating Map Projections/Untitled 1.png]]

Geogrpahic Coordinate Systems (GCS)

- Determined by a 3D Sphere / Spheroid
- Consists of:
    - A datum
    - An angular measure
    - a prime meridian

Angular Measures

- Latitude: measured relative to the equator, from +90 at North Pole to -90 at the south pole
- Longitude: measured relative to the prime meridian, from -180 (west) to +180 (east)
- Decimal Degrees (DD) : -18.5o
- Degrees, Minutes, Seconds (DMS) : 18o30'00"
- + : north and east
- - : south and west

DMS to DD

- 1 Degree = 60 minutes
- 1 Minute = 60 seconds
- 40o 26' 2" =
- 40 + 26/60 + 2/3600 =
- 40.434o

Parallels : run EAST AND WEST

- Equator is the benchmark, zero latitude

Meridians : run NORTH AND SOUTH

- Prime meridian is the benchmark, zero longitude

Graticule : the grid of latitude and longitude

World Circumference through the POLES: ~24,859.82 miles

World Circumference through the EQUATOR: ~24,901.55 miles

State Plane Coordinates

- Zones
    - 125 Zones, each following state / county boundaries with its own projection
    - Lambert Conformal Projection for zones that go east-west
    - Transverse Mercator projection for zones that go north-south
- 1+ for each state
- Can't join zones together ☹️

![[GIS/GIS Data/Creating Map Projections/Untitled 2.png]]

Distinguish between GCS (Decimal Degrees) and Local Coordinate Systems (Feet / Meters)

### Developable Surfaces

- 3d Surfaces that you can flatten to form a map
- Plane
- Cone
- Cylinder
- Infinite number of ways to project onto these surfaces

### Map Projections

Projection Families

- Conformal : preserve angular relations
- Equidistant : preserve distances
- Equal Area : preserve areas

Universal Transverse Mercator (UTM)

- Used by the US military, many other NGOs
- Global
- Metric Coordinate
- Longitude: 6 degrees wide
- Latitude: 8 degrees high

![[GIS/GIS Data/Creating Map Projections/Untitled 3.png]]

Projections get distorted

Tissot's Indicatrix - indicates the distortions of any map

Draw perfect circles, see what happens to them

![[GIS/GIS Data/Creating Map Projections/Untitled 4.png]]

[https://www.jasondavies.com/maps/transition/](https://www.jasondavies.com/maps/transition/)

**SUMMARY:**

---