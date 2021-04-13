# Odin

Created: Dec 9, 2020 10:19 PM
Reviewed: No
Type: Comparing Languages

this is software to coordinate cameras

+

a standalone program running inside of a camera

Odin is a general-purpose language designed for systems programming. It is a strongly typed language with manual memory management. Programs are constructed from packages.

explicit, simple

Uses EBNF

# What Odin has that others don't

- Unicode support ( doesn't matter )
- context system (below)
- procedure overloading
- control over memory layout (endian-ness, data sizes, offsets, etc)
- multiple return values
- compile time "when" statements
- fast performance
- all programs defined through "procedures"
- have to manage your own memory / allocations. good for low-level
- built-in logging system
- foreign system for interfacing with other code, such as C libraries

> foreign import kernel32 "system:kernel32.lib"

# Less good stuff

- no exception statements!
    - Odin uses plain error handling through the use of multiple return values.
- explicit conversion ONLY - no implicit
- 

### Context System

In all environments, an implicit "context" variable

local to each scope, passed by pointer to any procedure call in that scope

Main purpose: intercept third-party code libraries and modify functionality

able to easily modify how libraries allocate or log things

intercept third-party code to see what it does

.odin file extension

Odin: alternative to C

Simplicity

High Performance, built for modern systems