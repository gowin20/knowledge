# Standard Deviation: a measure of variation
Once again works best on data with a [[Symmetric Distribution]]

The Standard Deviation (SD) is a unit of measurement that measures of the average distance of a value from the [[Mean]].
Wait that actually makes sense. How far away is the average value from the mean?

If a dataset is symmetric and unimodal, more than 50% of data values will lie **less than one standard deviation away from the mean.**

## Calculating Standard Deviation

$$s = \sqrt{\frac{\sum{(X-\overline{X})^2}}{n-1}}$$
where $\overline{X}$ represents the [[Mean]].

Even if datasets have the same shape (symmetric) and the same mean (zero), they may have different standard deviations


**Process of calculation:**
1. Find mean
2. Subtract the mean from every indivirual data point, then square those differences
3. Add all squared values from previous step
4. Divide resulting value by the number of data points minus one.

At this point you have calculated **variance.**

5. Now, take the square root of the variance to get a standard distribution.

#### Example
For example, given the test scores $79, 82, 94, 83, 92$:

1. The mean, $\overline{X}=86$
2. Subtract mean from each value, square the difference
	- $(79-86)^2=49$
	- $(82-86)^2=16$
	- $(94-86)^2=64$
	- $(83-86)^2=9$
	- $(92-86)^2=36$
3. Sum all squared values
	- $49 + 16 + 64 + 9 + 36 = 174$
4. Divide by the number of data points minus one
	- $\frac{174}{5-1}=43.5$

**43.5 is the variance**

5. Take the square root of the variance
	- $s=\sqrt{43.5}=\color{lime}6.6$

So the Standard Deviation of this data is 6.6!


## Empirical Rule for SD
Here is our rule of thumb for data, assuming it is both **unimodal** and **symmetric**.

- 