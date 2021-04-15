# Mapping with Symbols

Created: Jan 28, 2021 12:10 AM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 180, Map Design
UID: 202101280010

![[Field Knowledge/GIS/GIS Data/Mapping with Symbols/Untitled.png]]

# Point Symbols:

![[Field Knowledge/GIS/GIS Data/Mapping with Symbols/Untitled 1.png]]

Smaller size: smaller data values

Larger size: larger data values

### Proportional vs Graduated Circles

![[Field Knowledge/GIS/GIS Data/Mapping with Symbols/Untitled 2.png]]

Proportional == unclassed, graduated == classed

### Proportional Symbols: Flannery Compensation

Slightly adjust symbol sizes due to common underestimation issues! areas scale on a square so we underestimate it lol

![[Field Knowledge/GIS/GIS Data/Mapping with Symbols/Untitled 3.png]]

![[Field Knowledge/GIS/GIS Data/Mapping with Symbols/Untitled 4.png]]

Make sure to set the **scaling factor!** Scale to easily distinguish classes, but with the least amount of overlap

Point symbology can show qualatative differences between things

## Selecting Good Map Symbols

![[Field Knowledge/GIS/GIS Data/Mapping with Symbols/Untitled 5.png]]

Use oriented symbols to show orientation in things like wind direction, etc

![[Field Knowledge/GIS/GIS Data/Mapping with Symbols/Untitled 6.png]]

## Lines

Size: width, size of lines based on importance

Pattern: change spacing, shape and length of pattern to differentiate

## Area

Pattern

- use easy to comprehend patterns
- Coarse → Fine to show heirarchy
- Higher value == larger shapes, closer spacing
- Different shape == different qualitative feature

![[Field Knowledge/GIS/GIS Data/Mapping with Symbols/Untitled 7.png]]

![[Field Knowledge/GIS/GIS Data/Mapping with Symbols/Untitled 8.png]]

# Dot Density

Each dot is a spepcific value

Fill enumeration units with randomly placed dots