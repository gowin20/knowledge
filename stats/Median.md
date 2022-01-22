#stats

# Median: a measure of center
The median is the midpoint of ranked values in a set.

**Example:** here are final scores of previous students - $79, 82, 83, 92, 94$

#### Finding the median:
1. Sort values in increasing order
2. Pick the value in the middle of the data set - if even number of items, pick the value halfway between center values
$$
79, 82, \color{red}83, \color{white}92, 94
$$
## Why is Median useful?
[[Mean]] is still better in many cases, but Median definitely has specific uses that make it quite powerful. Let's look at **skewed datasets** containing outliers.
Adding an outlier to the above data:
$$
\color{lime}3, \color{white}79, 82, 83, 92, 94
$$
New median:
$$
3, 79, \color{red}82,| \ 83, \color{white}92, 94 = (82+83)/2 = 82.5
$$
Notice that it doesn't change much even with the addition of an outlier.


### Median vs Mean
Compare to new mean: $(3+79+82+83+92+94)/6 = 433/6 = 72.2$

Here are the values before and after the addition of a 3:

|method|before 3|after 3|
|---|---|---|
|mean|86|72.2|
|median|83|82.5|

The median is more resistant to outliers than the mean!

In the specific situation of **a skewed distribution,** the median works better than mean. In general, mean works better and is also what is used for calculating standard deviation.


![[Pasted image 20220119141623.png]]
