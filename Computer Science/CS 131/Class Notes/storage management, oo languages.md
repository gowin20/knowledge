# storage management, oo languages

Created: Dec 7, 2020 1:00 PM
Reviewed: No
Type: [[C]], [[Python]]

# python-like storage management

- reference counting
- each object has a count of number of pointers that point to that obj
- when you do pointer assignment (p = q)
    - it decrements the reference count of the object that p points as
    - it increments the reference count of the object that q points at
- counts start at 1 at object allocation
- free the object's storage when the count drops to 0

# pros and cons to python storage management

- pros
    - simple and fast
    - discover garbage right away
- cons
    - pointer assignment gets more expensive
    - cycles of pointers can prevent garbage from being discovered and freed

# portability problem with Python

- C Python uses reference counts
- J Python uses the JVM, so it uses [[Computer Science/Java]]'s mark and sweep
- in order to make sure storage gets freed,
    - never create cycles of pointers
    - or break the cycles when the objects are no longer needed
        - create objects
        - compute with them
        - o.next = none will break the link (substitute for free(o))

# object oriented languages

- OO language is not the same as OO style
    - you can write OO code in a not OO language
        - each struct contains a descriptor word that points to an area containing address of functions / methods to call
        - you can write OO in assembly language even
    - OO languages make OO code easier to write
    - you can also write non OO code in C++ or Ocaml
        - which we did in hw 1 and 2
- many variations in OO langauges and style
    - no one set of rules
- important differences:

    ### static vs dynamic type checking

    - OCaml, Java → static
    - Python → dynamic

    ### static vs multiple inheritance

    - can you inherit from only one or multiple classes?
    - java → single
    - Python → multiple
    - can a class omit (instead of override) methods of its parent?
    - what do you inherit?
        - API - types of arguments, results, etc
        - implementation
        - in some languages eg Eiffel, you can inherit invariants

    ### do you have classes at all?

    - we've focused on class based languages
    - Ocaml, Java, Python
    - JavaScript, etc, are not class based
        - JS uses a technique called prototype based languages

        ### prototype based languages

        - basic idea: classes are too complicated, insead, we'll use:
            - o represents one class

            ```jsx
            p = o.clone() - makes a copy of an object
            p.add = {my implementation of add} 
            ```

            - p is like a subclass → it has all other methods, but it has its own add method
            - o and p are prototypes for objects
            - instead of using "new", you use "clone"
            - this approach gives you more flexibility, you can decide on your own if you want multiple inheritance, etc
            - downside: assumes dynamic typing
                - because you can create new prototype whenever you want, so that means you have to have dynamic checking

    ### parameter passing

    - syntactic issues
        - correspondence issues: which actual parameter (caller) corresponds to which formal parameter (callee)
        - positional: left to right
        - keyword: caller specifies parameter name
    - semantic issues
        - call by value
            - caller evaluates the parameter, gets a value, passes a copy of the value to the callee
            - when the callee modifies the parameter, it's only modifying a copy
            - C, C++, Java, Python, etc
            - pros: easy to understand, simple
            - downside: if the values are large, this can get really expensive
                - Fortran had a problem w this, where it dealt w arrays and call by value was rly expensive if you have a larger array
        - call by reference
            - caller evaluates actual parameter, gets its address
            - passes that address to callee
            - callee accesses formal parameter by dereferencing it
            - C++, etc
            - pros: not expensive w arrays, because you can just pass the first pointer, and the callee can figure it out from there
        - call by need
            - call by name and cache the result
            - callee invokes the thunk at most once
            - function programming languages like haskell do this