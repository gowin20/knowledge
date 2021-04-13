# Scheme Syntax

Created: Nov 13, 2020 1:09 PM
Reviewed: No
Type: Scheme

Another functional programming language!

Similar to LISP (LISt Processor)

Scheme: Very minimal dialect of LISP

Racket: Standard Scheme + some additional features

very popular!

# Setup

![[Scheme Syntax/Untitled.png]]

Enter command line by  typing "racket"

exit by (exit)

# Hello World in Racket

**From the command line:**

```scheme
(display "Hello, world!\n")
```

**From a file** (hello.ss)

```scheme
(display "Hello, world!\n")
```

then call with

```scheme
racket hello.ss
```

# Procedure

the Scheme system knows when it has an expression by matching double quotes and parentheses

# Basic Syntax

### Comments

```scheme
; - comments a line
#| comments a block |#
```

- 

### Numbers

```scheme
1
1/2
0.5
5e-1
```

- 

### Strings

```scheme
"Hello World\n"
```

### Symbols

```scheme
'Nice
'No-whitespace
'a->b?
```

- Similar to strings, but without whitespace

### Booleans

```scheme
#t
#f
```

- EVERYTHING that is not #f is #t
- the only false thing is #f itself!
- Similar short-circuiting to python, except loss things are #f

### Pair

```scheme
(cons 1 2)
(cons 1 "Hello")
```

- restricted to 2 elements
- prepend with "cons"

### List

```scheme
(list 1 2 3)
(list 1 "hi")
'(1 2 3) ;treated as a constant
```

- adding a single quote ' will tell Racket to treat the value as a constant
- single quote

```scheme
(car (list 1 2 3)) -> 1
(cdr (list 1 2 3)) -> (list 2 3)

(caar '((1 2) 3 4)) -> 1
(cadr '((1 2) 3 4)) -> 3
(car (cdr '((1 2) 3 4))) -> 3

first
rest
second
third
map
filter
foldl

```

- car → Content of Address Register
- cdr → Content of Decrement Register

ALL lists are pairs of head | tail

Pairs are not necessarily lists 

### Evaluation

- every procedure is within parenthesis
- possible to FORCE any expression to be treated as a list of symbols, rather than a function call

```scheme
(define symbol_list '(+ 1 2))
(eval symbol_list)
-> 3
```

- in files, we must define a namespace to be used with eval:

```scheme
(define my-program '(display "Hello World!"))

(define ns (make-base-namespace))
(eval my-program ns)
```

### Checking Types

```scheme
(number? 5) ; #t
(string? "hi") ;#t
(boolean? #t)
(pair? (cons 1 2))
(cons? (cons 1 2))
```

### Function Calls

the function name **always** comes first in function calls!

- even arithmetic operations!!!

```scheme
> (+ 1 2)
3
> (* 3 15)
45
```

# Conditionals

### If

```scheme
(if (equal? "apple" "orange")
	'yes
	'no)
-> 'no
```

- put the "then" and "else" branches on their own lines - this doesn't matter to plait, though
- if (test-expr) expr expr

### Cond

```scheme
(cond
	[(< 2 1) 'ha]
	[(> 2 1) 'fool]
)
-> 'fool
```

- Multi-way "if" statement
- tries clauses in order - essentially an "if / elif" block
- the final clause can be (else), equivalent to writing (#t) - "if all else fails"

### And / Or

```scheme
(and #t #f)
-> #f

(or #t #f)
-> #t

(and (< 2 1) (zero? (/ 1 0))) ; second expression is not evaluated
-> #f

(or (< 1 2) (zero? (/ 1 0))) ; second expression is not evaluated
-> #t

(and #t #t #t #t)
-> #t

(or #f #f #f)
-> #f
```

- not binary - works with any number of expressions!
- short-cicuiting, stops once we can determine result

# Definitions

Defining variables is similar function to defining syntax

similar to "let ... = ... ;;"

### define keyword

```scheme
> (define pi 3.1415926)
> pi
3.1415926

> (define (print_name name_to_be_printed) (display (string-append "Hello, " name_to_be_printed)))
> (print_name "Shreya")
"Hello, Shreya"
```

- 

### let statement

```scheme
> (let ([x 5]) (* x 2))
10
> (let ([x 5] [y 6]) (+ x y))
11
```

- "lambda" useage of defining X and Y inside of square brackets
- 

### Comparing Values

```scheme
=
<
>
<=
>=

> (< 1 2 3)
> (=
```

- Can be a pplied to **multiple values**
- not binary!

### Equality

```scheme
(= 1 2) ; numbers

(equal? (list 1 2 3) (list 1 2 4)) ;for other types, checked recursively

(define a (list 1 2 3))
(eq? a a) ;for object references
```