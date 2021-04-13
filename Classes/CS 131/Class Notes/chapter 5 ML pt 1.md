# chapter 5: ML pt 1

Created: Nov 3, 2020 2:55 PM
Reviewed: No
Type: ML, Textbook

# constants

- two numeric types: *int* and *real*
    - int: 1234
    - real: 123.4
- bool vals: true and false
    - case sensitive
- strings, characters

# operators

### integer

- +, -, *
- division
    - div
    - mod
- ~ for negation
    - -1 = ~1

### real

- +, -, *
- / for division

### string

- ^ for concatenation

### ordering

- >, <, ≤, ≥
- =, <> (equality and inequality)

# conditional expressions

```java
<conditional expression> ::= if <expression> then <expression> else <expression>
```

# type conversion

```java
1.0 * 3 
//error: operator and operand don't agree
```

- ML has predefined functions that you can use to convert values from one type to another

![[chapter 5 ML pt 1/Untitled.png]]

# variable definition

- "val" keyword

```java
val x = 1 + 2 + 3;

//can redefine an existing variable and change type
val fred = 23;
val fred = true;

(fred now = true)
```

- when you redefine an existing variable, it adds a definition on top of the previous one
    - does not alter or overwrite
    - any part of the program that was using the old definition before you defined it is still using that old definition

# tuples and lists

### tuples

- ordered collection of values of different types = **tuple**
- tuple is formed by putting two or more expressions, separated by commas, inside parentheses

```java
val barney = (1, 3.0, "brown)

type: int * real * string
* = type constructor

parens important!
string * (int * int) 

different from 
(string * int) * int
```

- to extract an element

```java
#i v
i is the index, v is the tuple

#2 barney 
gives: 3.0
```

### lists

- all elements must be the same type
- formed w square brackets instead of parens

```java
[1, 2, 3]
[(1,2) (3,4)] //list of tuples: (int * int) list
[[1,2][3,4]) //list of lists: int list list
```

- empty lists

```java
[] // empty list
type 'a list

function null can test whether list is empty 

null []
- outputs true
null [1,2,3]
- outputs false
```

- names beginning w ' = type variable
    - means that the type is unknown
- @ operator for concatenation of two lists of the same type, or cons operator (::)
    - cons operator used more frequently
        1. more naturally used in recursion
            - since it is right associative, it will create lists intuitively

            ```java
            1::2::3::[] will create [1, 2, 3] -> start from the right 
            if :: were left associative, 
            1::2::3::[] would be an error, since 1::2 would be the first operation
            and the second operand is not even a list
            ```

        2. more efficient

# functions

- uses the "fun" keyword
- to write a function with more than one input, use a tuple ??
- → symbol is another type constructor
- adding up elements of a list

![[chapter 5 ML pt 1/Untitled 1.png]]

- all of this seems to be for writing on the command line, not like in a ide or whatevs

# type annotations

- * = tuple types
- list = list types
- → = function types
- list has highest preference, → has lowest
- can write types in the program to give ML the type
    - just write a colon and then the type
    - can do this after any variable or expression

```ocaml
fun prod(a: real, b: real) : real = a * b;
(* otherwise, ML will think it's ints *)
```