# Categories of Programming Languages

Created: Oct 7, 2020 12:21 PM
Reviewed: No
Type: Comparing Languages

Three major categories of programming Languages

- in some sense, none of these categories dominate the others
- all Turing equivalent, can do whatever any deterministic program can do
- Pretty much every programming language is Turing complete! Except for old languages (apparently not C)

# Imperative Programming Languages

A program is like a recipe for performing a computation

A program is a series of commands to be executed

String commands together such as C1; C2; C3; → also uses loops and conditionals

first-mover effect → they came first 

- C
- C++
- C#
- Java
- Python
- 

# Functional Programming Languages

A program is like a mathematical expression that yields a value 

A program is an expression, typically a function call, which gets evaluated like an equation

hook together → f ( x, g (y) , h (z , w) )

can also have conditionals and recursion 

recursion in a functional language is a generalization of loops in imperative languages

didn't get popular until 1970s, when ppl discovered that imperative languages were bad for multiple-CPU apps 

- ML
- OCaml 🐫
- Haskell
- F#

John Backus (originator of FORTRAN 1950s, trying to atone for the design deficiencies)

motivations: 

1. Functional programming was created to align with traditional mathematical notation. Imperative languages were a big departure from math, especially when considering things like variables (a = a+1 doesn't make any sense)

    in math:                             in c++:

    a = 0                                  a = 0 (change the value of a to 0, we don't care what it was before)   

    a = a + 1 (false)                a = a + 1 (allowed)

    f(a) = f(a) (true)               f(a) = f(a) (could be false, if the function changes the value) 

2. parallelizability (efficiency in time)

    CPU ←—> RAM

    C1, C2, C3 can be optimized into 

    (C1 || C2), C3

    make sure that C1 doesn't change things that C2 needs, vice versa 

    often the compiler doesn't know if this is safe, so it won't do it 

Functional programming uses unambiguous notation, and is deterministic. Computer programmers like to reinvent shitty version of the wheel

Additional information about Functional Programming Languages:

[[The Function of Languages]]

# Logic Programming Languages

A program is a statement in logic

A query of a complex database of facts and logical rules 

hook together → p(X, Y) & q(Y, Z) | w(X, Z)

- Prolog
- Logic 2010