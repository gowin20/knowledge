# Python

Memory Management: reference count GC
- can't account for cycles
- longer time, but less memory usage
- private heap containing Python objects and data structures
- management of Python heap is controlled by interpreter, user has no say

Other Notable Features: - both python and java are interpreted to bytecode before execution, then code is translate to machine code 
- easy syntax
- [[Computer Science/CS 131/Class Notes/Python - Asyncio]] library!
- async / await are efficient bc other things get done in the meantime
- built in support for server stuff: open_connection, etc
- chronological order may not be sustained
Threading: GIL, only single threading
- parallel execution is a context switch, where control is passed to another thread
- any thread must hold GIL to access shared memory
Type Checking: Dynamic
- type checked at runtime, vars can be anything
- type errors are harder to detect
- can change type of variable (int earlier in the program, string later, since the value is not determined till runtime) 
Type of Language: OO