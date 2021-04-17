# Big Picture Syllabus of Stuff We've done in class

### Stuff on the syllabus / in notes that we've never touched before

- language design issues

- functions
    - amortized efficiency
    - functions as data (Odin, other languages)
- tokenization (have lecture notes on this)
- exceptions
    - design issues: when to not use exceptions
    - 
1. [[Field Knowledge/Computer Science/Java]]
    - the "Object" class
    - collections
    - exceptions **** seems important-ish
2. [[OCaml]]
3. Prolog
    - clausal form / horn clauses
    - memory management
4. Python
5. [[Scheme]]

### Stuff we've actually done in projects or homeworks or the midterm

- language design issues
    - efficiency, safety, convenience
    - programming categories:
        - procedural
        - functional
        - object-oriented
        - declarative
        - scripting
    - history, evolution of programming languages (imo not on final)
- variable names, scope, lifetime
- static vs dynamic scope
- control (prolog, OCaml, scheme, etc. - kind of big theme in the class)
    - backtracking
    - expression evaluation
    - pattern matching, unification
    - rewrite rules
- concurrency
    - multithreading
    - concurrency vs parallelism
    - synchronization
- exceptions
    - exceptions in java vs systems in other languages
    - zig, odin
- Grammars
    - BNF
    - EBNF
    - Syntax diagrams - probably will not be on the final
- Semantics
    - lambda calculus
    - program verification
1. Java
    - fundamentals of java:
        - primitive types
        - classes, instances
        - variables, methods, overloading, constructors
        - inheritance, abstract classes, final classes, interfaces
    - visibility
    - java class library basics
    - threads, multi-threading
    - java memory model
2. OCaml
    - a very difficult language
    - functional programming
    - OCaml / ML syntax
    - type inference
    - pattern matching
    - list comprehension
    - recursion
    - higher-order functions, currying
    - type constructors (types like Symbol, Tree, Leaf, etc.)
    - syntax and grammar stuff
    - BNF, EBNF
    - parse trees
    - really lots of stuff
3. Prolog
    - propositional logic (thank u philo 31)
    - predicate calculus (also philo 31)
    - the resolution principle
    - depth-first backward chaining with backtracking (trying the rules in order lol)
    - debugging
    - closed world assumption (nothing outside of the program exists, the program just uses explicitly what we give it)
4. Python
    - fundamentals of python
    - generators? + the yield keyword
    - [[asyncio]] library, asynchronous programming
    - API requests
    - server herd management
    - flooding algorithms
5. Scheme
    - a shitty booty ass language
    - basics of programming in Scheme (and by extension drRacket and Lisp)
    - list comprehension
    - syntax (defining functions, let, cond, other stuff like that)
    - let keyword
        - (let ([x 5] [y 10]) ((+ x y)))
    - lambda keyword, functions
        - ((lambda (a b) ((+ a b)) 5 10)
    - tail recursion
        - 
    - comparisons: eq? vs equal? (equal? is recursive for all types while eq? is for primitives, at least i think so)