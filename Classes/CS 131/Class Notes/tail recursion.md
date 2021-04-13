# tail recursion

Created: Dec 17, 2020 4:10 PM
Reviewed: No
Type: Scheme

### recursion

- let bound procedure can't really be recursive

![[tail recursion/Untitled.png]]

- sum is only visible within the let body, not the lambda expression that is bound to sum
- but letrec can

![[tail recursion/Untitled 1.png]]

- in letrec, the variables are visible in the expr, as well as the body

### tail calls / tail recursion

- when a procedure call is in tail position wrt a lambda expression, it is considered a tail call
- when a procedure tail calls itself, the result is tail recursion
- call is in tail position if its value is returned directly from the lambda expression → there is nothing to do after the call , just return the value
    - in tail position if it is the last expression in the body, the "else" of an if statement, the last expression in the body of a let, etc

    ![[tail recursion/Untitled 2.png]]

    - all calls to F are tail recursive, calls to G are not

    ![[tail recursion/Untitled 3.png]]

    - this is tail recursive fibonacci

    ![[tail recursion/Untitled 4.png]]

    - this one above is doubly recursive, as you have to compute to recursive calls at each step

    ![[tail recursion/Untitled 5.png]]

    - stack trace for NOT TAIL RECURSIVE fib
    - multiple calls to fib0, fib2, fib1

    ![[tail recursion/Untitled 6.png]]

    - stack trace for TAIL RECURSIVE fib