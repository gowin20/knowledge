# The Function of Languages

Created: Oct 7, 2020 11:57 AM
Reviewed: No
Type: Comparing Languages

lecture 2: electric boogaloo

Every Computer Science language has some real problems, man!

Duplication results from people creating new but similar languages to deal with specific problems. ex, Java inspired by the failures of C

The new languages take the good features, but they're not compatible w the old 

COBOL sucks, used to be popular

no job security: dont learn COBOL 

learn english and you'll get a cs job easy

intel uses ML to design their chips! it's a secret though

IBM tried to take over the world using PL /  I (kinda what C# is now) 

Application Areas affected by programming languages

- backend *queries* in Google
    - started w C++ modules hooked together in a network, didn't work
    - spent too much time trying to hook modules together instead of finding better ways to do queries
    - took a BIG IDEA from functional programming - [MapReduce](https://en.wikipedia.org/wiki/MapReduce)
        1. Divide and Conquer! break problem into similar subproblems 
        2. each problem is fed to a individual computer, does not need to communicate w other computers 
        3. *MAP phase*: each node works on its individual problem, same concept, different data 
        4. Feed answers back to you 
        5. *REDUCE phase*: combine results
        - Avoid Side Effects: Each subproblem is handled discretely, so as to not cause changes of state in the computer
            - Side Effect: A change of state in the computer resulting from executing a piece of code. Ex, setting a variable allocates memory, changing state

    (*much of this lecture was on the different categories of programming languages. Find those notes here)*

    [[Categories of Programming Languages]]

    ## The Function of Languages

    - in math, a *function* is a *mapping* from a *domain* to a *range*
    - in math, a *functional form* is a higher order function, either its domain or range is a set of functions

    A **functional form** is a higher order function, where its domain or range is a set of functions (function as an argument)

    - definite integral is a *functional form*, because we're integrating across a function
        - Definite integral $\int_0^1{f(x)}dx$
        - in OCaml, this is represented as  `definite_integral 0 1 f`
    - functional composition is another *functional form*
        - (f o g) (x) == f ( g (x) )
        - `(o (f, g)) (x)` (*in Ocaml)*

    We do not use variables as in imperative coding languages

    - instead, variables in the mathematical sense (eg, the argument to a function)
    - once one of these variables has a value, it does not change in value
    - the reasoning behind this: we want f(x) in one place to equal f(x) elsewhere (assuming we're talking about the same function and same input)
        - This concept is called *referential transparency -* meaning it's easy for you to know what value a name refers to, since the values won't change
    - This lets us (and the compiler) do "common subexpression elimination"

        ```ocaml
        a = f(x+1)
        b = g(x+1)

        (* optimize to *)
        int n = x + 1
        a = f(n)
        b = g(n)
        ```

        - can't do this in C++, because `x` could be a global variable, maybe f(x+1) modifies this
        - but you CAN do this in functional programming - great source of optimization!

    an *idempotent* command C is one where C;C has the equivalent effect to C