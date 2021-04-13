# Fundamentals of Scheme

Created: Dec 17, 2020 1:54 PM
Reviewed: No
Type: [[Scheme]]

# intro

- high level language
- portable across versions of the same Scheme implementations on different machines
- scheme supports many types of data including characters, strings, symbols, lists, etc
- storage required to hold contents is dynamically allocated as necessary and deallocated automatically with a garbage collector
- all objects are first class data values: are retained indefinitely, may be passed freely as arguments to procedures, returned as values, and combined to form new objects
- call by value: values are pointers to actual storage
- scheme variables are lexically scoped and scheme programs are block structured
    - local binding is visible only lexically, within the program text that makes up the block of code
    - scope of a binding is the block in which the bound identifier is visible
- procedures are first class data objects, variables are bound to procedures like they are bound to other objects
    - procedures may be recursive
    - **tail call ****is when one procedure directly returns the result of invoking another procedure
    - **tail recursion** is when a procedure recursively tail calls itself
- considered to be a dialect of lisp

### scheme syntax

- keywords, variables, symbols are all called identifiers
- structured forms and list constants are enclosed within parentheses
- programs should be indented to show flow

### scheme naming conventions

- predicates end with a question mark
    - eq? zero? etc
    - procedures that return a true or false
- type predicates are created from the name of the type
    - pair?
- names of most character, string, and vector procedures start with char- string- , etc
    - string-append
- names of procedures to convert an object from one type to another are type1→type2
    - vector→list

# Lambda Calculus

the core of scheme functionality derives from lambda calculus! Lambda calculus is a form of logic used to express statements using bound variables and substitution.

powerful concept, used to simulate any turing machine