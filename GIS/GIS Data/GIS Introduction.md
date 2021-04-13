# GIS Introduction

Created: Aug 6, 2020 2:58 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 7
UID: 202008061458

# Geography Studies

## Physical Geography

The study of nature, natural systems, and processes. Our real world

## Human Geography

Geographic Characteristics of people and their behaviors

## Geographic Techniques

Computational research methods, using things like GIS to analyze geographic data about our world

# Remote Sensing: acquiring information about something without making physical contact with it

Jean Piaget: Stages of Spacial Cognition

![[GIS Introduction/Untitled.png]]

MENTAL MAPS are universal, but everyone's are unique

They're all heirarchically organized, and contain discrete features

## Geographic Questions

Location

- Where?

Distribution

- Local or widespread?

Association

- What else is near it?
- What coincides with the subject matter? ex. what vegetation is associated with forest fires?

Interaction

- Is it linked to something?

Change

- Has it always been there? How recent / what's the timeframe

# GIS

A GIS is special type of computer program capable of storing, editing, processing, and presenting information & geographic data as maps

GIS Software providers: ERSI, ArcGIS, PitneyBowes

[http://www.esri.com/](http://www.esri.com/)

[http://www.pbinsight.com/](http://www.pbinsight.com/)

[http://grass.itc.it/](http://grass.itc.it/) (open source)

Hardware of a GIS:

- Computer
- Memory
- Storade Devices
- Scanners
- Printers
- GPS Unit
- Other physical components

Uses of a GIS:

- Maintain, Analyze, and Share data / information. Super useful

# Methods to Analyze Data with

Histograms represent data by mapping information points to one of several CATEGORIES or CLASSES

## Histogram Guidelines

- Use between 5 and 15 different classes. The exact number depends on the characteristics of your observations
- Each observation goes into one and only one class
- When possible, have each class cover an equal range of values

## Measures of Central Tendency

- Mean
    - AKA the "average"
    - Most commonly used one
- Median
- Mode

## Measures of Dispersion

### Range

- Simplest

### Interquartile Range

- The difference between the upper and lower quartile

Divide the dataset into Four Quartiles

- Use the median to divide the sorted array into two halves
- Divide each half again by using their own medians
- Quartile 1 (Q1) is the median of the lower half of the sorted array (lower quartile)
- Q2 is the median
- Q3 is the median of the upper half of the array (upper quartile)

### Variance

- Subtract the raw value of each point from the mean of all the points'
- Some differences are positive, some are not
- Sum of all the differences equals zero
- Overcoming the zeroing property:
    - Square Each Deviation, removing negative values

    ![[GIS Introduction/Untitled 1.png]]

    Divide the sum of the squares by (n-1 for a sample) or (n for a population)

    ![[GIS Introduction/Untitled 2.png]]

### Standard Deviation

The most common method of dispersion analysis

Take the square root of the variance

![[GIS Introduction/Untitled 3.png]]

Shows us many things:

- Small deviation means that the values are similar to each other
- Large deviation means the values are scattered wildly
- If the dataset conforms to a normal distribution (bell shape in a frequency distribution), that tells us more stuff
    - When it's not notmal, it is either positively or neggatively skewed
    - Normally distributed data has these properties:
        - 68% of the data falls within 1 standard deviation of the mean
        - 95% of the data falls within 2 standard deviations of the mean