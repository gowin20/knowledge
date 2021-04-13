# Prolog Syntax

Created: Nov 9, 2020 12:19 PM
Reviewed: No
Type: Prolog

![[Computer Science/CS 131/Class Notes/Prolog Syntax/Untitled.png]]

- every Prolog "clause" (like a statement) ends in "."
- scope of a local variable is its containing clause
- a predicate is "true" if there is no :- after it

# prolog syntax

- prolog term is one of the following
- atom: equal only to itself, spelled like an identifier that starts with a lower case letter, or a single quoted string
    - ex: a, aXyz, 'X y'
    - these are all only equal to each other and not equal to any other atom
    - a = 3 is false, a only = a
- number: integer or floats
- variable: logical variables
    - identifier starting with a capital letter, or with '_'
    - variable can become **bound** to a value, which is any Prolog character, on successful computation
        - called instantiation
    - you can look at a variable's value after a successful computation to see what the "answer" is
    - a variable can become **"unbound"** on failure
        - on success, X = a, but then if computation fails, then X becomes unbound again
        - unbound variable means the variable has no value
        - Prolog does not know the value
    - these are the only two ways you can change variables
    - you can discover the value after successful computation, or unbound it by failing a computation and then succeed it in a different way to change the value
    - but you can not change a variable's value like in other languages
        - x = x + 1 is not possible
    - think about variables like:
        - you're discovering the value of a variable, and sometimes you'll mess up
        - don't think about "adding one to the variable", that's not thinking like Prolog that's thinking like C++
- structure: of the form "functor(arg1, arg2,...)"
    - must have at least one argument
    - functor is an atom
    - f(A, g(X)) is a f/2 structure with functor f, and 2 arguments
        - g(X) is also a structure, so structures are nestable
    - looks like a function call, but its NOT, only data structures
    - every functor call is like a constructor call in C++ or Java or Python, except not as fancy at all
        - you are just building a data structure w this call

# syntactic sugar in Prolog

- lots of infix, prefix, postfix operators

```prolog
3 + 4 * 5      ==    '+'(3, '*'(4, 5))
A = 2 + 3      ==    '='(A, '+'(2, 3))
sort (A, B) :- same_elements(A,B), sorted(B) ==  ':-'(sort(A,B), ',' (same_elements(A,B), sorted(B))
```

- since we're using single quotes around the functors, they're all atoms

# lists

- list syntax

```prolog
[ ] == '[]'
[a, b, c] == '.'(a, '.'(b, '.'(c, '[]')))
[X, Y | Z] == '.'(X, '.'(Y,Z))
```

# Timing Programs

```prolog
statistics(runtime,[Start|_]),

do_something,

statistics(runtime,[Stop|_]),
```

Runtime variable is equal to Stop-Start

# Cut in Prolog

# Negation

Prolog doesn't do true negation. There is no 'not'.

```prolog
member(X, [X|_]).
member(X, [_|L]) :- member(X, L).

?- member(3, [X,4,7]).
X = 3

?- ~ (member(3, [5,9,2])). % this doesn't exist!

\+ exists, but \+ is not 'not'
not is an alias for '\+'
\+(Call) :- Call, !, fail.
\+(_).

?- N = 3, \+(N = 4).
N = 3
?- \+(N = 4), N = 3.

```