# Mapping with Texture

Created: Feb 21, 2021 7:30 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 180, Map Design
UID: 202102211930

# Adding Texture to Maps

Terrain Shading!

- AKA Hillshading, relief shading, analytical shading, and shaded relief

Artificially light a surface using azimuth and altitude

- Azimuth: Direction of the light source (e.g. 315 degrees northwest)
- Altitude: encoded by pixels in raster datasets. Each pixel encodes a single elevation value

![[old/Field Knowledge/GIS/GIS Data/Mapping with Texture/Untitled.png]]

Relief inversion: depending on the direction of light, relief can look inverted

- Humans like the northwest
- Default go-to for human azimuths is **315** degrees, experience inversion at **135**
- Not an accurate visual representation!

### Multi-directional Shaded Relief

Relief parallel to the light source does not get shaded enough. Different angles highlight different features!

- Create several hillshades from multiple angles, and use map algebra to combine them!
- possible to weight some hillshades more heavily than others (e.g. from the northwest!)

Terrain shading is typically used **as a background** to enhance the map. We overlay more information on top

- need a low contrast, light colors to do this well!

![[old/Field Knowledge/GIS/GIS Data/Mapping with Texture/Untitled 1.png]]

### Hyposmetric Tints

Colors overlaid to indicate the relative elevation

- More gradual than something like choropleth mapping

![[old/Field Knowledge/GIS/GIS Data/Mapping with Texture/Untitled 2.png]]

### Bump Mapping

Adding more surface texture to maps

- Adding randomly placed "bumps" to create more texture on the surface
- Useful to simulate the look of trees, shrubs, rocks, or buildings
- rAy CaSTeD TrEeS