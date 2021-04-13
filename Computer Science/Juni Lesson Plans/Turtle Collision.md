# Turtle Collision

Created: Aug 15, 2020 2:59 PM
Type: Python 1

# Do the rest of the project first

# Collision

Sample project I made to explain things better

[https://repl.it/@gowin/collision#main.py](https://repl.it/@gowin/collision#main.py)

```python
if abs(t.xcor() - t2.xcor()) < 10 and abs(t.ycor() - t2.ycor()) < 10:
```

Break this snippet down into two separate parts, one for the X and one for the Y

```python
abs(t.xcvor() - t2.xcor()) < 10
```

## Distance

We want to find out how apart the turtles are. If they're close together, then it's a collision

t.xcor() - t2.xcor()

shows us how far apart the turtles are in the X direction

## Absolute Value - abs()

Gives us a positive number