Investigated by David Gale and Lloyd Shapley, 1962

Goal: Create an algorithm which works to match $n$ entities together from two groups

make sure there's not a chaotic system!

Common examples:
- matching between men and women (same number)
- matching between employers and applicants



It's not as simple as matching a single man to a woman and moving on! We need **criterion** for the match

#### ranking
each man has some ordering for women to match with
$$
m1: w_1 > w_2 > ... > w_n\\
w1: m_1 > m_2 > ... > m_n


$$

#### Instability
The below matching is not stable if man $m$ prefers woman $w`$ to woman $w$, and same for woman $w$ and man $m`$. If their preference is for the other, they will destroy the existing matching (denoted by parenthesis)
$$
(m,w)\ \&\ (m',w')
$$


$$
m(w') > m(w)\ \& \ w'(m) > w'(m')
$$


# Matching Algorithm
Start:

Assume all men and all women are free
![[Pasted image 20210623101335.png]]

While there is some man $m$ such that $m$ is free and $m$ did not propose to all $w$:
![[Pasted image 20210623101441.png]]
	Choose one such man
	Let $w$ be a woman such that $w$ is the most preferred by $m$ to all other women, and $m$ did not propose to $w$
	If $w$ is free, then add the pairing to the matching set $S$: $(m,w)\in S$
	Otherwise, there must be some set $(m',w) \in S$
	![[Pasted image 20210623144051.png]]
	
time complexity
$A(x)$ $T_A(x)$:

worst-case time complexity
$$|x|=n \\
T_A(n) = max(T_A(x);|x|=n)$$


average-case time complexity
$$
T_{Aa}(n) = 1k\sum_{|x|=n}{T_A(x)}
$$
