# Mapping with Color

Created: Feb 19, 2021 1:12 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 180, Map Design
UID: 202102191312

# Color Systems

Each one of these uses different **perceptual dimensions**, sliders on certain properties of color

HSV

- Hue, Saturation, Value

CMYK

- Used for printing maps
- Cyan, Magenta, Yellow, Black

RGB

- Used on computers and displays
- Red, Green, Blue
- we would talk about HEX codes but arcgis is idiotic and does not allow you to input RGB as a hex

### Color on Reference Maps

- Hue used to differentiate features
- ex. blue for water, green for read

### Color on Thematic Maps

- often use colors not directly associated with visual properties

# What is color?

The way humans interpret color contains three perceptual dimensions

# HSV Color System

### Hue

What you probably think of, when you think of color

- color names: blue, purple, red, etc
- primary indexer of color

![[Mapping with Color/Untitled.png]]

Two methods of mixing hue, additive and subtractive

Additive: RGB (W)

- used for computer screens, because light is naturally white

Subtractive: CMY (K)

- used for printing, because ink is naturally black

### Lightness / Value

How light or dark a hue is

Good for visualizing ranked / ordered data:

- Darker hues = higher in value, lighter hues = lower in value
- Plays off the human subconscious, which naturally associates things this way

The amount of light reflecting or emitting from something

![[Mapping with Color/Untitled 1.png]]

One hue, only changing in terms of lightness

![[Mapping with Color/Untitled 2.png]]

Lightness on a map

### Saturation

How vivid a color is

- aka **Chroma, Colorfulness, Purity, Intensity**
- Desaturated == more gray
- Harder for humans to see changes in, compared to Hue and Lightness

![[Mapping with Color/Untitled 3.png]]

Oftentimes combined with changes in lightness to create color schemes:

![[Mapping with Color/Untitled 4.png]]

^ This color scheme varies both saturation and lightness

Small warning: more saturated colors look weird next to less saturated ones!

![[Mapping with Color/Untitled 5.png]]

## Visualizing the HSV System

![[Mapping with Color/Untitled 6.png]]

# RGB System

Specific values assigned to each value R, G, B represent the possible shades of red, green, and blue

Each 8-bit byte R,G,B encodes 256 possible shades respectively

- It's just hex codes. easy!
- 00FF00
- 16,777,216 possible colors

![[Mapping with Color/Untitled 7.png]]

# Color Contrast

The ability of humans to distinguish colors from one another depends on their color contrast

**Brightness Equation:**

$((Red * 299) + (Green * 587) + (Blue * 114)) / 1,000$

Yeilds a single brightness value for a color

- Compare two colors' brightness values. Their difference shows color contrast

> Kimerling et al. (2016): A brightness difference between two colors of **125 or higher** is the threshold for legibility

![[Mapping with Color/Untitled 8.png]]

Lighter backgrounds are easier to get a higher contrast with