# Data Classification with Choropleth Maps

Created: Jan 28, 2021 12:10 AM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 180
UID: 202101280010

Thematic maps: show spatial distributions

**Spatial Distributions:**

![[Data Classification with Choropleth Maps/Untitled.png]]

![[Data Classification with Choropleth Maps/Untitled 1.png]]

Continuous data with abrupt change: choropleth map

continuous data with smooth change: elevation, etc. rasters usually

# Choropleth Maps

Areas are shaded based on measurement of an attribute

Name origin is Greek: Choro = area, Plethos = magnitude

### Enumeration Unit

Area that the data is aggregated to

- states, counties, tracts, etc

### Normalization

- original measurements are RAW DATA
- derived measures are COMPUTED
    - density, rates, percentages
- choropleth maps are usually better for derived data, because then data is directly comparable

![[Data Classification with Choropleth Maps/Untitled 2.png]]

## Modifiable Areal Unit Problem (MAUP) - 1984

Different enum boundaries result in different spatial patterns!

Basically, depending how we classify things we see lots of different patterns. this is basically gerrymandering

![[Data Classification with Choropleth Maps/Untitled 3.png]]

# Data Classification

Group the data into different classes

- Different classification methods - have to choose one!
- the less classes there are, the more important the method choice is
- method affects the appearance of the map. purpose, audience, and distribution all matter a lot

![[Data Classification with Choropleth Maps/Untitled 4.png]]

## Data **Classification Methods:**

1. Quantile Intervals
    - same number of observations in each class
    - number of classes variable
        - 4 classed = 25% of data in each class
        - 5 classes = 20% of data points in each class
    - best used for:
        - relative rankings
        - hiding outliers
    - easy to understand
2. Equal Intervals
    - total range divided by the number of class
    - each class has the same range
    - best used for equally distributed data (rectangular distribution)
        - bad for uneven, lopsided
    - easy to understand as well!
3. Natural Break Intervals
    - class breaks determined by the natural breaks in data between clusters (Jenks)
    - Minimize variation within classes, maximize variation between classes
    - "optimized" is very similar to this
4. Mean-Standard Deviation Intervals
    - Mean = break point
    - standard deviations add to or subtract from the mean to calculate other breaks
    - ONLY use with normally distributed data
    - possibly unintuitive to those who don't understand statistics
5. Critical-Value Intervals
    - cartographers decide critical values for breaks
    - ex: poverty line, previous year/time average, median, mean, etc.
    - use when critical value is meaningful to the theme of your map

## Create Map Classes for Easier Map Reading

- Too many classes is hard to differentiate!
- Manually round values for class breaks
- Use commas
- Include descriptive titles (e.g. Incidents per 1,000 people)

![[Data Classification with Choropleth Maps/Untitled 5.png]]

# Color Schemes

Choose colors that lend for easier map reading

## Sequential

Colors can vary in lightness. Darker == higher / more of something

![[Data Classification with Choropleth Maps/Untitled 6.png]]

we can choose between single-hue or multi-hue

## Diverging

A pair of sequential color schemes with a critical midpoint

common color is the midpoint

![[Data Classification with Choropleth Maps/Untitled 7.png]]

## Qualitative

Use completely different hues to represent different categories. No category is "more" than another

![[Data Classification with Choropleth Maps/Untitled 8.png]]

Binary qualitative: two hues, like on election maps