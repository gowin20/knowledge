# More Scheme Syntax

Created: Dec 17, 2020 1:54 PM
Reviewed: No
Type: [[Scheme]], Textbook

- lists are written as sequences of objects surrounded by parentheses
    - (1 2 3 4)
- quote forces a list or anything to be treated as data, rather than a procedure call

    ```pascal
    (quote (+ 3 4) -> (+ 3 4))
    can also write this with a single '
    ' is considered an abbreviation for quote
    ('( 1 2 3 4) -> (1 2 3 4))

    also works w things that are not lists: 
    (quote hello) -> hello
    so scheme knows to treat hello as a symbol and NOT a variable

    ```

    - quote is not a procedure call
    - why do applications and variables share notations with lists and symbols?
        - shared notation allows scheme programs to be represented as scheme data, which simplifies the writing of interpreters, compilers, editors, etc
        - important feature of scheme

    ### manipulating lists

    ```pascal
    (car '(a b c)) -> a
    (cdr '(a b c)) -> (b c)
    (cons 'a '(b c )) -> (a b c)
    ```

    - cons actually builds pairs
        - takes two arguments: second is a list, first becomes the first element in the resulting list
    - a list is a sequence of pairs: each pair's cdr is the next pair in the sequence

    ![[Computer Science/CS 131/Class Notes/More Scheme Syntax/Untitled.png]]

    - proper list: the cdr of the last pair is the empty list
    - improper list: printed ini dotted pair notation

    ```pascal
    (cons 'a 'b) -> (a . b)
    ```

### variables and let expressions

```pascal
(let ((var expr) ...) body1 body2 ...) 
```

- variables are bound to the values by the let
- brackets are often used
- can nest let expressions
    - when nested let's bind the same variable, only the binding created by the inner let is visible within the body

        ```pascal
        (let ([x 1])  // x = 1
        	(let ([x (+ x 1)]) // x = 2
        		(+ x x)) // only last x is visible, so this = 4
        ```

        - inner binding for x shadows the outer binding

### lambda expressions

```pascal
(lambda (var ...) body1 body2 ...) 
((lambda (x) (+ x x)) (* 3 4)) -> 24
```

- procedure is value of (lambda (x) (+ x x)), values are (* 3 4)
- so x is bound to 12, and the result of this procedure is 24
- can use procedure more than once → on a list

![[Computer Science/CS 131/Class Notes/More Scheme Syntax/Untitled 1.png]]

- using lambda statements with let statements

![[Computer Science/CS 131/Class Notes/More Scheme Syntax/Untitled 2.png]]

- procedure f, bound to the lambda expression
    - call f with b (as the variable y), and then x is from the let statement
- let and lambda statements are pretty similar: this is identical

```scheme
(let ([x 'a]) (cons (x x)) = ((lambda (x) (cons x x)) 'a) 
```

- more examples for general syntax

![[Computer Science/CS 131/Class Notes/More Scheme Syntax/Untitled 3.png]]

- first two require any number of arguments
- g evaluates to a list whose first element is the first argument, and the second element is a list containing the remaining arguments
- similar thing with h but you are separating the first 2 elements of the list

### top level calls

- so basically top level procedure calls are lambda expressions
- but you can suppress the lambda stuff for easier reading and writing

```scheme
(define (var0 var1 var2...) (e1 e1) 
						is ACTUALLY
(define var0 (lambda (var1 var2 ...) (e1 e2))

; var0 being procedure name i believe
```

### control flow

- if statements
- predicates: <, >, =, etc, return #f or #t
    - type predicates end w a question mark
        - pair? list? etc

    ```scheme
    (cond (text expr)....(else expr))

    (cond 
    	[(< n 0) 
    		(expr)]
    	[(> n 0)
    		(expr)]
    	[else 
    		(expr)]
    		
    ```