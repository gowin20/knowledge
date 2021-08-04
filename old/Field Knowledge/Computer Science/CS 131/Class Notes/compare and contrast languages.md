# compare and contrast languages

Created: Dec 17, 2020 7:55 PM
Reviewed: No
Type: Comparing Languages

Functional & Logical programming paradigms are both types of Declarative Programming

### [[Python]]
OO
- "reference count [[Garbage Collectors|GC]]"
-can't account for cycles
-longer time, but less memory usage
-private heap containing Python objects and data structures
-management of Python heap is controlled by interpreter, user has no say
"|"Dynamic
- type checked at runtime, vars can be anything
- type errors are harder to detect
- can change type of variable (int earlier in the program, string later, since the value is not determined till runtime) "|"GIL, only single threading
- parallel execution is a context switch, where control is passed to another thread
- any thread must hold GIL to access shared memory"|"- both python and java are interpreted to bytecode before execution, then code is translate to machine code 
- easy syntax
-[[asyncio]] library!
- async / await are efficient bc other things get done in the meantime
- built in support for server stuff: open_connection, etc
- chronological order may not be sustained"



### [[old/Field Knowledge/Computer Science/Java]]
- OO
- mark and sweep GC
- can account for cycles
- shorter time, less memory usage
- heap: contains all runtime memory for classes and arrays
- non heap memory stores runtime constants, method data
- stack memory has all the pointers to heap memory and all the regular stack stuff"|"Static
- type checked at compile time, vars declared with type"|"true multithreading
- large # of threads encouraged when IO related, like using a server
- ""synchronized"": thread must have the lock of an object to modify it
- ""final"": immutable and read only
- ""volatile"": change to an object visible across all threads"|"- both python and java are interpreted to bytecode before execution, then code is translate to machine code 
- used in Android programming
- used for the server side of medium to large web applications
- interface vs abstract classes
- single inheritance"



### [[OCaml]] 

"ML w OO features"

functional programming as a whole: 
- recursion used for iteration, while in OO, iteration are loops
- attempts to avoid mutable data, eliminating side effects
- w the same parameters, the output of a function should be the same every time
- thrives where state is not a factor
- data is only transformed through functions, not put in objects"|- built in GC|"compile time checking with type inference (types determined at compile time like in java, but it infers types like in python)"|,"- grammars, parse trees
- type inference like in python
- multiple inheritance → classes can inherit from multiple classes
- pattern matching
- [head::tail]
- currying functions
- tail recursion
- functional languages good for writing interpreters"


### [[Prolog]]
Logical and Declarative
- logical languages are built on predicates w no return value
- rule based (horn clauses)
- functional languages are built on function w return value
- encode a logical situation → enter all the things that must be true and the program will give you the ""input"" that matches"|,,not really in the scope of the class - based on standard C multithreading support|"structure of prolog programs: 
- facts declaring objects and relationships 
- rules governing objects and relationships
- questions are asked about the objects and their relationships
- Prolog is called with variables that you don't know and you are trying to find, Ocaml and other languages call functions w parameters w values you probably know"


### [[Scheme]]
"functional and procedural programming"
- procedural is a step towards declarative programming 
- kinda middle of ocaml and prolog
- two different programming styles, scheme supports both "|,,|"- Scheme is better than prolog at IO stuff (Lisp is much better at IO than prolog)
- continuations → ways to create and manipulate continuations
- the worst syntax imaginable
- quote, lambda expressions
- mostly used as a research tool or in academia
- pattern matching (like ocaml)
- car, cdr, similar to ocaml
- tail recursion"


### [[D]]
aims to improve upon C/C++
garbage collection, but conservative
syntactic and semantic restraints for code analysis before compile
built in unit tests"


### [[Odin]]
"no exceptions, everything handled as data structures (even functions)"


### [[Zig]]
no hidden control flow or memory allocations
performance and safety 
security → crash on undefined behavior 
debug using stack traces"
,|,,|