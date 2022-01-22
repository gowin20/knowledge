# Zig

Notable Features: 
- no hidden control flow or memory allocations
- performance and safety 
- security → crash on undefined behavior 
- debug using stack traces


# stuff it says in the intro

- robust:
    - behavior is correct even for edge cases
- optimal:
    - write programs the best way they can behave and perform
- reusable:
    - same code works in many different environments with different constraints
- maintainable:
    - low overhead to reading code
    - precisely communicate intent to compiler and other programmers
    - resilient to changing environments

# Standout Things

- No hidden control flow or memory allocations
- compared to D:
    - D has @property functions
    - D has operator overloading
    - D has throw + catch *exceptions*
- All of this means that functions could be secretly called when it doesn't look like it
- lazily analyzed global variables, order independent
- pointers cannot be null
- manual memory management, programmers must manage their own memory
- and deal w allocation errors
- defer, errdefer: good way to handle errors, but also makes all code easily verifiable
- standard lib can take stack traces and then dump that to standard error for debugging
- Zig has try and catch keywords, but errors are handled as *values*
- conpetes with C
- least similar to C
- cImport imports C libraries
    - types, variablec, functions, macros
- also functions as a C compiler!
- async functions!
    - no dependence on host operating system
    - infers which functions are async
    - allows await/async on non async functions, which means that zig libraries are agnostic of blocking vs async io
- comes with a make system, don't need to use make or cmake or anything
- wide range of support with targets

    ![[Computer Science/CS 131/Class Notes/Zig/Untitled.png]]

    much more of this table

    - standard lib supports all tier 1 and tier 2 targets
    - machine code for tier 1 targets
    - debug capabilities and stack trace on failed assertions for tier 1 targets and tier 2 targets

## Performance and Safety

four build modes, mixable all the way down to scope granularity

-optimizations: speed at the cost of debugging + compile time

-runtime safety: crash instead of undefined behavior. Great safety component, but sacrifices speed!

[https://github.com/ziglang/zig/wiki/Why-Zig-When-There-is-Already-CPP,-D,-and-Rust%3F](https://github.com/ziglang/zig/wiki/Why-Zig-When-There-is-Already-CPP,-D,-and-Rust%3F)

- competes with C
- Zig standard lib can integrate with lib C though, but does not depend on it
- different syntax and feel than C