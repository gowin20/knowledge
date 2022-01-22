# Java Arrays + 2D Arrays

Created: Aug 3, 2020 1:43 PM
Status: Complete
Type: [[Computer Science/Java]]

# What is an Array?

- An array is an ordered list of elements, which can be things like integers, double, booleans, or strings.
- when we create an array, we have to tell the computer up front how many elements the array will have room for
    - int[] arr = new int[10];
- Access specific elements of an array:
    - arr[0]
    - arr.length (no parentheses)
    - How to access the final element?
- loop through all the elements in an array?
- Explicitly defined size
- method which takes array as parameter
- method which returns an array
- Arrays are error-prone
- default value: 0 for int, 0.0 for double
    - "null" for objects

## Java vs Python

- Array vs List

## homework

- Palindrome checker method
- 3 methods from JS7 "Practice with Arrays"

## George's second homework:

- Method which converts strings to arrays
- method which converts arrays to strings
- how to loop through an array without knowing the size?
    - use a for-each loop
    - use "array.length"
    - explicitly have a variable set to the length of the array
    - NOT really any other good ways

# Two-Dimensional Arrays

- We can create arrays of any object, right?
- A 2D array is simply an array of arrays
- Represents a GRID of values
- What are some uses of 2D arrays?
    - anything which uses a grid
    - Create a MAP for a game
- more than 2 dimensions? how deep can you go?