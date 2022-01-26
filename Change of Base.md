#binary #programming


Converting from any base to any base is as simple as repeatedly dividing by a number and recording its remainder.

### base 10 to base 2
```python
base10 = int(input("enter a base 10 number please"))
base2 = ""
while (base10 > 0):
	remainder = base10 % 2
	base2 += str(remainder)
	base10 /= 2
return int(base2)
```