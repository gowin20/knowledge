# Exceptions

Created: Dec 30, 2020 1:49 PM
ID: 202012301349
Subject: [[Java]]

Exceptions in Java are treated as OBJECTS

Exceptions are powerful:

- Separate from the normal flow of execution
- Propagate up the stack. We don't have to worry about returning them
- Standardized way of handling errors

Two types of exceptions:

## Runtime Exceptions

Caused by bugs in our code

We should fix these!

Name a few examples

## Checked Exceptions

Less common, exceptions outside of our control

Can't always be avoided

- IO Exception
    - FileNotFound Exception
- ClassNotFound Exception
- SQLException
- InvocationTargetException