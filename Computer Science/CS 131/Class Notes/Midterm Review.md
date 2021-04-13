# Midterm Review

Created: Oct 28, 2020 12:02 PM
Reviewed: No

# OCaml

### Tail recursion

- how is memory being allocated?

- Stack: FILO, static allocation, fast, small
    - $RSP - "the top of the current stack", instruction pointer
    - $RBP - "the bottom of the current stack"

![[Screenshot_from_2020-10-30_12-18-54.png]]

- Heap: Fragment, dynamic allocation, slower, large
- Problem: stack overflow
- To reduce the chance of stack overflow, use tail-recursion
    - Tail recursion doesn't need to come back. Handle the results at our current recursive level
    - No need to store the caller's address any more, which saves lots of space

Normal recursion:

```ocaml
let rec f x =
	if x = 0 then 1
	else x * f (x-1);; (* need to come back to this call in order to multiply by x *)
```

Tail recursion:

```ocaml
let rec helper x prod =
	if x = 0 then prod
	else helper (x-1) (prod*x);;

let f x = helper x 1
```

No additional calculations are being performed inside of the recursive function. We do the calculation inside of a function argument, which means that there's no need to return back up to the higher levels.

This way we don't need to save the $RBP pointers of each recursive call. we directly return from the final one

### Grammar Types

- Hw1, Hw2 style grammar definitions
- Parse Tree
    - NOT the same as a syntax diagram
- BNF
- EBNF
- Syntax Diagram
    - aka syntax chart / syntax graph, etc.
    - specific regulations
- Abstract Syntax Tree
- Constructing any grammar: divide and conquer

# Java

- Concepts of OOP features (including OOP in C++)