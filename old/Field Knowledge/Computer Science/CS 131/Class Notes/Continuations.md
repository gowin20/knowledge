# Continuations

Created: Dec 17, 2020 4:10 PM
Reviewed: No
Type: [[Scheme]]

[https://courses.cs.washington.edu/courses/cse341/04wi/lectures/15-scheme-continuations.html](https://courses.cs.washington.edu/courses/cse341/04wi/lectures/15-scheme-continuations.html)

every expression, in every programming language, uses continuations. They are an abstract idea which represents the control flow of the program

continuations describe what to do next!

In C:

```prolog
x = (1 + (2 * 3));
printf("Done");
```

- the continuation of the "x=..." assignment is the "printf" statement
- the continuation of (2 * 3) is (1 + ans)
- the continuation of the entire computation (1 + (2 * 3)) is the assignment of that value to x

**current continuation:** from the perspective of the code that's running, the current continuation is derived from the current point in a program's execution

In C, the information needed to access a continuation conceptually is split across the main memory heap, the stack, registers, and the program counter.

Scheme lets us explicitly access continuations, which are usually hidden. 

**first-class continuations:** constructs which enable a language to save its current state of execution and return to that point later on in the program, possibly multiple times

^^^ this is what scheme uses

a data structure which represents the computational process at a given point in execution. by explicitly defining them, they can be accessed by programs instead of being hidden in the runtime environment

- during evaluation of a scheme expr, implementation must keep track of
    - what to evaluate
    - what to do with the value
- the "what to do with the value" part is called the *continuation* of the computation
- so at any point during evaluation, there is a continuation that continues the computation
    - like a relay race

```scheme
for the expr: 
(if (null? x) (quote ()) (cdr x)) 

there are 6 continuations during the evaluation,
the continuations that will happen with: 
1. the value of the whole statement
2. the value of null?x 
3. value of null? 
4. value of x
5. value of cdr
6. value of x

the continuation for (cdr x) is not listed because it is the same as the one waiting for the entire expressiono
```

scheme allows the continuation of any expression to be captured w procedure **call/cc.** 

- call/cc takes 1 argument that is a procedure. that procedure itself takes one argument (usually called k) which represents the current continuation
    - current continuation is what comes next in a program's execution at that point
- call with current continuation
- call/cc is passed a procedure p
- call/cc creates a representation of the current continuation and passes it to p
- the continuation itself is represented by a procedure k
- each time k is applied to a value, it returns the value to the continuation of the call
    - then this value is the value of the application of call/cc
- if p does not invoke k, the value returned by the procedure becomes the value of call/cc

```scheme
(call/cc 
	(lambda (k)
		(* 5 4))) -> 20 
k is never invoked, value becomes 20 

(call/cc
	(lambda (k)
		(* 5 (k 4))) -> 4
k is invoked, so the value is returned 

(+ 2 
	(call/cc
		(lambda (k)
			(* 5 (k 4))))) -> 6
k is invoked here, so 4 is returned to the call/cc, and then 2 is added 
```

- call/cc providing exit from recursion

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/Continuations/Untitled.png]]

- "break" is "k" in this case, when a zero value is detected, the whole thing will return immediately with value 0

Uses of continuations: