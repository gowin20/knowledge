# Spatial Autocorrelation and Spatial Weights

Created: Mar 6, 2021 5:05 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 181A
UID: 202103061705

# Spatial Autocorrelation

- geographic changes in a phenomenon over time

Tobler's First Law of Geography: **Everything is related to everything else, but near things are more related than distant things**

Using this law as a starting point, let's talk about spatial autocorrelation

**Spatial Autocorrelation:** used to measure the degree of spatial clustering / dispersion of a data variable

**Auto** - means that we're measuring the variable's correlation with itself spatially

## Forms of Global Spatial Autocorrelation

Use spatial statistics to teast whether Tobler's first law applies to a given variable

- If a variable's values are **significantly clustered** in space, that's **positive** spatial autocorrelation
- If a variable's values are **evenly dispersed** in space, that's **negative** spatial autocorrelation
- If values are randomly distributed, then no spatial autocorrelation exists at all!

![[GIS/GIS Data/Spatial Autocorrelation and Spatial Weights/Untitled.png]]

If spatial autocorrelation is present for a variable, we can assume that some degree of **spatial dependence** exists for it - geography matters!

### The Null Hypothesis: Spatial Randomness

With spatial randomness, we assume that geography isn't really a factor in a variable's distribution. This baseline assumption is something that we can then reject once we find evidence to the contrary.

**Moran's I**: a common test used to measure the form and strength of spatial autocorrelation

- Values from -1 → 1
    - -1: perfect spatial dispersion (negative!)
    - 0: random distribution
    - 1: perfect spatial clustering (positive!)

If the pseudo p-value is smaller than the significance level, we can reject the null hypothesis

# Spatial Lag

The spatial lag for a variable in a given location is defined as the average value of all neighboring values!

Example: for the variable location with a value of 3, the spatially lagged variable value is the value of all neighboring cells":

$(2+3+2+3)/4 = 2.5$

![[GIS/GIS Data/Spatial Autocorrelation and Spatial Weights/Untitled 1.png]]

When variables fall into different quadrants on this Moran's plot, that is indicative of specific types of relationships in the dataset

High-High and Low-Low both are positive indicators of spatial autocorrelation. 

Low-High and High-Low indicate that values are surrounded by values which are not similar. This is a negative indicator of spatial autocorrelation

![[GIS/GIS Data/Spatial Autocorrelation and Spatial Weights/Untitled 2.png]]

### Neighboring Values are defined using Spatial Weights

# Spatial Weights

allow us to define which spatial relationships are used to determine which features are neighbors

Chess analogies incoming!

- **Rook Contiguity**: polygons with shared borders are considered neighbors (neighboring 4 on grid)
- **Queen Contiguity:** polygons with shared borders or verticies are considered neighbors (neighboring 8 on grid)
- **k-Nearest Neighbors**: formally treat a defined number of a feature's nearest neighbors as neighbors
- **Distance threshold:** treat all features within a given distance of a feature as neighbors (kinda like buffer analysis)

# Local Spatial Autocorrelatoin

Global spatial autocorrelation indicates the level of clustering for any phenomena

- don't allow us to see specific locations!

Local spatial autocorrelation indicates the locations of specific clusters geographically!

**Local Indicators of Spatial Autocorrelation (LISA)** tests

- used to identify significant spatial clusters of variable values
- describe the nature of the values (high, low, etc)
- **Positive LISA** indicates that neighbors are **more similar to each other than they are globally**
- **Negative LISA** - **more different from each other than they are globally**

### LISA Cluster Types

LISA Cluster maps only show the areas which are statistically signifigant - aka where we can reject the null hypothesis!

Correlate to where the values would fall on a Moran Scatterplot. The added map is great for spatial analysis though

- **High-High:** high values surrounded by other high values
- **High-Low:** high values surrounded by low values
- **Low-High:** Low values surrounded by high values
- **Low-Low:** Low values surrounded by low values
- **Not Significant:** areas not contained within statistically significant local clusters (can't reject null hypothesis)

![[GIS/GIS Data/Spatial Autocorrelation and Spatial Weights/Untitled 3.png]]

# Change and Time

both Global and Local spatial autocorrelation are great for assessing clustering, identifying clusters for one or two variables at a time. Do not cover timespans well!

- Use a single variable to encapsulate change (i.e. difference from one time period to another in votes cast for a political candidate, etc)
- **Spatial Dynamics** methods - such as **directional LISA** - for comparing multiple temporal cross-sections of a variable's incidence

For handling change and time, the underlying geography must stay exactly the same!

![[GIS/GIS Data/Spatial Autocorrelation and Spatial Weights/Untitled 4.png]]