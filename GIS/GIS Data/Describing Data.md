# Describing Data

Created: Jan 16, 2021 10:57 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 180
UID: 202101162257

**Measures of central tendency**: numeric indicator used to describe the 'center of gravity' of a variable

- Mode: (nominal, ordinal, interval, ratio) most common value
- Median: (interval, ratio) middle-most value
- Mean: (interval, ratio) average value

**Measures of Dispersion:** indicators which describe the spread of a variable around the mean

- Interquartile Range (IQR) - range of the middle half of a variable
- Variance: the sum of the squared differences between data values and the mean, divided by total number of records minus one
    - $\frac{\sum (mean - data value)^2)}{(count-1}$
- standard deviation: the square root of the variance with the following properties in NORMALY DISTRIBUTED DATA:
    - 68% of valued are within +- 1 s.d.
    - 95% within +- 2 s.d.
    - 99% values within +- 3 s.d.

[https://www.calculatorsoup.com/calculators/statistics/descriptivestatistics.php](https://www.calculatorsoup.com/calculators/statistics/descriptivestatistics.php)

# Data terminology

**qualitative vs quantitative:** categorical vs numeric

**variable:** describes something that can change

**univariate vs multiveriate, bivariate:** single variable vs more than one, and analysis of relationships between variables

**dependent variable:** variable whose value is determined by values of other variables

**independent variable:** a variable that influences the value of dependent variables

**population:** the universe of all possible values of interest

**sample:** a subset of population, used to obtain informative insights about the population itself

discrete: students in a class, orders in a shipment, finite and atomic

continuous: unlimited intermediate values

## Four types / measurements of data

1. Nominal / Categorical
    - qualities, of the thing
    - types of thing
    - descriptive
    - color, species, day of week
2. Ordinal
    - ranking or order in regards to other data
    - low-high, s-m-l-xl
    - all still relative!
3. Interval
    - measurement with equidistant units with an arbitrary zero point
    - temperature!
4. Ratio
    - measurement scale with equidistant units. absolute reference point
    - height, percentages

## Missing Data

how to handle data that's missing!

- **missing value:** create arbitrary missing value indicator, address missing data on case by case basis
- **listwise deletion:** remove the record and all values associated with it
- **substitution:** systematically replace missing data with another value, such as the average of existing value