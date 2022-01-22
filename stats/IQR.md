#stats
# IQR: Interquartile Range
Tells us how much space **the middle 50% of the data** occupies (a range)

#### Quartiles
1. Q1: First Quartile, 25% of data are below this point
2. Q2: [[Median]], 50% of data are below this point
3. Q3: Third Quartile, 75% of data are below this point


 ## Finding IQR and Quartiles

There are other ways to do this, but this is the only method used in UCLA's STATS 10 course.

**Sample dataset:**  $63, 64, 64, 70, 72, 76, 77, 81, 81$

1. Find median
	$$
	63, 64, 64, 70, \color{red}72, \color{white}76, 77, 81, 81 
	$$
2. Recursively find median of upper and lower halves to calculate quartiles
	$$
	63, \color{red}64,|\ 64, \color{white}70, \color{gray}72, \color{white}76, \color{red}77,|\ 81, \color{white}81 
	$$
$Q1=(64+64)/2=64$
$Q3=(77+81)/2=79$

3. Find IQR by subtracting  $Q3-Q1$

**First Quartile: the median of the lower half
Third Quartile: the median of the upper half**


![[Pasted image 20220119142703.png]]

