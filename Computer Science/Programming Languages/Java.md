# Java

Created: Dec 30, 2020 1:05 PM
ID: 202012301305
Subject: Java
Type of Note: Category







# Basic Summary (from 131)

Memory Management: mark and sweep GC
- can account for cycles
- shorter time, less memory usage
- heap: contains all runtime memory for classes and arrays
- non heap memory stores runtime constants, method data
- stack memory has all the pointers to heap memory and all the regular stack stuff
Other Notable Features: - both python and java are interpreted to bytecode before execution, then code is translate to machine code 
- used in Android programming
- used for the server side of medium to large web applications
- interface vs abstract classes
- single inheritance
Threading: true multithreading
- large # of threads encouraged when IO related, like using a server
- "synchronized": thread must have the lock of an object to modify it
- "final": immutable and read only
- "volatile": change to an object visible across all threads
Type Checking: Static
- type checked at compile time, vars declared with type
Type of Language: OO