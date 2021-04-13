# D

Created: Dec 9, 2020 8:39 PM
Reviewed: No
Type: Comparing Languages

# General Notes

### D:

- general purpose systems and applications programming language
- high level language, but retains ability to write high performance code and interface directly with operating systems API and hardware
- well suited to writing medium to large scale million line programs
- not an interpreted language
- no VM or overriding philosophy
- object oriented
    - single inheritance enhanced with interfaces
    - classes instantiated b reference, code to clean up after exceptions not required
- functional programming
    - pure functions
    - immutable types and data structures
    - lambda functions and closures
- best of both static and dynamic world
    - allows writing large code fragments without reduntantly specifying types, like dynamic languages
    - but static inference deduces types and other code properties
- @ safe, @ trusted, @ system attributes allow programmer to decide safety efficiency tradeoffs of a application
- who is D for?
    - projects that need built in testing and verification
    - programmers who use code analysis tools to eliminate bugs before code is compiled
    - people who compile with max warning levels
    - teams who write million lines of code
    - programmers who think the language should provide enough features to obviate the necessity to manipulate pointers
    - programmers who spend half their application in scripting languages and the other half in native languages
    - D's lexical analyzer and parser are independent, meaning that it is easy to write simple tools to manipulate D source without having to build a compiler, and source code can be transmitted in tokenized form for specialized applications

# 1: The software running inside the cameras must be cleanly written and easy to audit.

### D:

- C like syntax, good for people who know C / C++ like this project spec says
- Some design goals of D:
    - write fast effective code in a straightforward manner
    - short learning curve for programmers familiar w C or C++ or Java
    - provide syntactic and semantic restraints that reduce the need for third party static code checking
    - incorporate unit testing methodology

# 2: The software should be a [freestanding program](https://en.wikipedia.org/wiki/Standalone_program), with no separate operating system (as the OS itself would be a source of security holes).

- A stand-alone program, also known as a freestanding program, is a computer program that does not load any external module, library function or program and that is designed to boot with the bootstrap procedure of the target processor – it runs on bare metal. (wikiepedia)

### D:

- one of the major design goals for D: write lightweight and standalone programs [https://dlang.org/overview.html](https://dlang.org/overview.html)
- 

# 3. The software running should be as simple and stripped-down as possible. This rules out using higher-level languages like Python or Java, which assume components like interpreters or garbage collectors that your potential customers might not trust.

### D:

- "D is a systems programming language with support for garbage collection. Usually it is not necessary to free memory explicitly. Just allocate as needed, and the garbage collector will periodically return all unused memory to the pool of available memory." [https://dlang.org/spec/garbage.html](https://dlang.org/spec/garbage.html)
    - only runs during allocation, only if there is memory available to allocate
    - GC does not sit in the background and periodically scan the heap
    - Phobos, D's standard library, has undergone a massive effort to be more conservative in its GC usage
    - some functions were made to work with lazy ranges, some rewritten to take buffers supplied by caller, and some reimplemented to avoid unnecessary allocations internally
    - result: standard lib that is amenable to GC free code
- not an interpreted language
- no VM or overriding philosophy

# 4. The software must be capable of interfacing to low-level hardware devices, such as camera or network interfaces.