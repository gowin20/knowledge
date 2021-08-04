# Uncertainty in GIS

Created: Sep 2, 2020 3:01 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 7
UID: 202009021501

### Date: Aug 27, 2020

### Topic: Uncertainty in GIS

### Recall

[https://www.census.gov/cgi-bin/geo/shapefiles/index.php](https://www.census.gov/cgi-bin/geo/shapefiles/index.php)

### Notes

Error

- Refers to the difference between a true value and the observed/predicted value

Population

- The universe of all possible values
- The group of items that we want to describe

Sample

- A subset of population
- Supposed to accurately represent the larger population as a whole
- More realistic than representing the entire population, due to time constraints / logistics

Margin of error

- How confident we are that our estimate is accurate
- The larger the sample, the smaller margin of error

    ![[old/Field Knowledge/GIS/GIS Data/Uncertainty in GIS/Untitled.png]]

- Tradeoff between sample size and margin of error
- Represents how confident we are in ONE particular variable
- Doesn't represent how confident we are in the difference between discrete variables

3 sources of uncertainty, when we transition betweeen parts:

- Real world → conception
- Conception → measurement
- measurement → analysis

Spatial Uncertainty

- There are very few *natural* units of geographic analysis - most are arbitrary, like countries' borders
    - What is a region?
        - World regional geography: continents as regions. Other region definitions use smaller and more informative regions
- Vagueness in phenomena - what is a wetland?
- Where does the wetland begin and end?
- Linguistic ambiguity: spatial terminology is not universal or objective
    - Terms in different languages have cultural meanings which are not translatable
    - ex: "Homeland"
- Indicator Ambiguity
    - Direct indicators correspond with a phenomenon
    - Indirect indicators are a proxy measure for the phenomenon we're interested in
    - We cannot directly measure wealth, or global warming. An "indirect indicator" of global warming would be average yearly temperature.

Uncertainty in Representation and Measurement

- Different data models conceptualize uncertainty in different ways
- Human error when digitizing
- Instrument error in GPS systems
- Conflating information from different data sources

Uncertainty in Analysis

- Units of analysis
- Scale and Aggregation Effects
- Modifiable Areal Unit Problem (MAUP)

**SUMMARY:**

---