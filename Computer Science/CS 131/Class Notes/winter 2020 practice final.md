# winter 2020 practice final

Created: Dec 17, 2020 7:29 PM
Reviewed: No

![[Computer Science/CS 131/Class Notes/winter 2020 practice final/Untitled.png]]

- interpreter: converts high level program code into machine code
    - converts the source code line by line
    - allows less evaluation and modification of program when it is running

A.  Interpreter for Ocaml written in Prolog - very hard

- OCaml is functional programming, Prolog is more rule-based /  logical style → writing different kinds of programs
- Prolog is very special purposed languages, not meant for types of problems other than logic problems
- so even if this is possible, it's going to take a ton of effort and probably not be very efficient
- OCaml is more statically typed → checks at compile time, Prolog is runtime checking
    - So you would need to check the types in Prolog manually

B.  Interpreter for Prolog written in OCaml - easier than A, still have to implement some harder stuff

- again, very different kinds of programs
- recursion might work slightly different, in Prolog there's backtracking after recursion, so OCaml needs to implement this, but they both use recursion so that won't be too hard to implement
- OCaml is a general purpose language, Prolog is a specially purposed language
- Functional languages usually work well for writing interpreters
- you call predicates in Prolog with variables that you want to solve for, vs in OCaml you're calling functions with parameters that are known values
    - different ways of calling functions

C. Interpreter for Python written in Java 

- very similar languages
- static vs dynamic typing, need to check the types in Java manually
- Python has GIL which prevents true multithreading, Java has multithreading
    - need to stop multiple threads from executing at the same time

D. Interpreter for Java written in Python 

- multithreading issues → would have to implement multiple threads since Java has it
    - harder than part c
- dynamic typing being used to implement static typing is probably easier

![[Computer Science/CS 131/Class Notes/winter 2020 practice final/Untitled 1.png]]

![[Computer Science/CS 131/Class Notes/winter 2020 practice final/Untitled 2.png]]

- difficulties
    - cyclic grammars
    - time efficiency issues
    - we're probably going to need to iterate through the grammar multiple times
    - example:
        - S → A
        - A → B
        - B → c (terminal symbols)
        - need to keep iterating because if you just replace B, you've turned A into a newly terminal
        - but then S → c
            - again, there's a problem because this is still  nearly terminal
            - so this is not possible to turn into a not nearly terminal grammar
            - same for if the grammar just started something like this with just a rule
    - hard to iterate through rules w production functions
        - lots of function calls

![[Computer Science/CS 131/Class Notes/winter 2020 practice final/Untitled 3.png]]

- I/O means not necessarily CPU intensive
- Java
    - through JVM, can run bytecode on many different architectures → makes distribution easier
    - multi-threading
        - same as below, latency for each task may be higher
    - GC, don't need to free memory manually
        - could make it slightly slower
- C++
    - multi-threading
        - latency of each individual task may be lower since there are multiple threads to handle the tasks
    - no garbage collection → more effort but runs faster
        - memory consumption lower due to no garbage collection
    - static typing
        - programs themselves a bit faster but writing programs maybe slower
    - more difficult to write bug free code
- Python
    - no multithreading → one thread
    - development may be faster, higher level language than C++
        - dynamic type checking, easier syntax
    - Garbage collection makes this easier to develop, don't need to free memory manually
        - could make it slightly slower
        - some delay in memory not being used and memory being released
        - lots of connections = maybe using more memory than we need because of this delay

![[Computer Science/CS 131/Class Notes/winter 2020 practice final/Untitled 4.png]]

- what did we actually learn from each of these languages:
    - OCaml
        - functional programming
        - recursion and tail recursion
        - type inference / type system
    - Java
        - OO
        - multithreading - different synchronization techniques
        - GC / memory management
        - JVM
    - Python
        - OO
        - GC / memory management
        - [[Computer Science/CS 131/Class Notes/Python - Asyncio]]
    - Prolog
        - logical programming
        - rule based
        - different parameter passing scheme
        - recursion
    - Scheme
        - tail recursion
        - continiuation
        - code as data
        - functional programming

    - Zig
        - has async await, could replace Python?
    - D
        - has garbage collection
            - could replace Java?

![[Computer Science/CS 131/Class Notes/winter 2020 practice final/Untitled 5.png]]

```scheme
(+ 1 (+ 2 3)) 
continuation tells us what to do next 
after we execute + 2 3, continuation is + 1 plus whatever the result is
continuation stores instruction pointer and environment poiner

in scheme, you can do this explicitly using call/cc

(+ 1 (call/cc (lambda (cont)(cont (+ 2 3))))
-> explicitly looking at this continuation

if you store this continuation somewhere, you can jump back and forth to and from this location 
```

```scheme
protinuation: instead of jumping to a specific spot in the future, want to jump backwards in history 
```

- need to save all past stack states
- going to consume tons of memory
- so you could have a call protinuation function that takes the parameter of the number of steps you want to jump backwards
    - for ex: call/protinuation 10 would jump backwards 10 steps

![[Computer Science/CS 131/Class Notes/winter 2020 practice final/Untitled 6.png]]

- Python "await" awaits a Future object
- continuations are kind of like coroutines
    - harder than Python to implement and understand
    - more powerful than coroutines
    - continuations help you implement control flow abstractions, like exiting a program
    - can also use continuations and the dynamic-wind procedure to handle exceptions
        - dynamic-wind takes 3 args (3 functions: inFn bodyFn outFn)
            - calls bodyFn
            - when bodyFn is entered, called inFn, when bodyFn is exited, calls outFn
- similar in that a Future is an eventual result of something
- continuation is the next expression that receives the result of the current
- they're both like the next step in the program
- Future objects are awaitable → so you can have asynchronous code
- Future objects can probably be implemented in terms of continuations

- OCaml
    - functional programming
    - recursion and tail recursion
    - type inference / type system
- OCaml
    - functional programming
    - recursion and tail recursion
    - type inference / type system
- OCaml
    - functional programming
    - recursion and tail recursion
    - type inference / type system