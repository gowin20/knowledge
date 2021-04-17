# Map Labels

Created: Feb 10, 2021 9:55 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 180, Map Design
UID: 202102102155

# 3 Kinds of Map Text in GIS

## Graphic Text

Text not associated with specific map elements / data frames

- titles
- sources
- notes

When you move the map or zoom, this kind of text stays in the same position. Can be a problem because you have to keep fucking with it!

## Dynamic Labeling

Automatically label datasets based on an attribute from the attribute table

If the dataset is missing names, you can look for another dataset or manually enter in missing names (depending on how much is missing)

- can control elements across the entire dataset, like halos/font size/color

labels automatically shift when you move the map

## Annotation

- Fixed relative to data
- you can reposition labels and edit characters
- can't move outside the dataframe
    - e.g. not titles, notes, anything in the margin

Start with dynamic labeling, then convert into annotation in order to reposition and refine individual labels!

# Labels as Symbols

Labels can show **feature categories** and **feature hierarchies**

## **Showing feature categories:**

![[Field Knowledge/GIS/GIS Data/Map Labels/Untitled.png]]

Common font choices for categories:

1. Serif: cultural features (roads, towns, points of interest)
2. Sans Serif: physical features (mountains, valleys, hydrography)

In order to avoid creating a visual heirarchy (Sometimes we don't want some features to appear more important than others), change:

- Font (create larger categories by only using a couple)
- Regular vs *Italic*
- Hue
- Arrangement, bending

## Showing Feature Hierarchies:

Use specific type characteristics to create a heirarchy:

- point size
- weight

    ![[Field Knowledge/GIS/GIS Data/Map Labels/Untitled 1.png]]

- Scaling

    ![[Field Knowledge/GIS/GIS Data/Map Labels/Untitled 2.png]]

- color lightness (for lighter colors, make them bold for better printing)
- case

# Placing Labels

## Placing Labels for Points

- Use horizontal alignment
- Offset from point

![[Field Knowledge/GIS/GIS Data/Map Labels/Untitled 3.png]]

- Justify based on the text location relative to point!

![[Field Knowledge/GIS/GIS Data/Map Labels/Untitled 4.png]]

- Use uppercase Judiciously!

![[Field Knowledge/GIS/GIS Data/Map Labels/Untitled 5.png]]

- variation in lowercase letters encodes more information. easier to read
- position text so it doesn't cross over lines or other features
- position text on the same side of features as points

## Placing Labels for Lines

- Label along line
- If long line, repeat the label instead of stretching text!
- Small gap between line and label
- be sure to only follow one feature per label
- use simple curves
- keep text on one side - e.g. all vertical lines on right side, etc. - something like that

## Placing Labels for Areas

- Position label to showcase the full extent
- Show extent through spacing between characters and leading - the space between lines
- UPPERCASE letters when increasing space between them
- Don't adjust text point size for smaller / larger areas, as that will create false heirarchy
- Offset alignment between labels next to one another