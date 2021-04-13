# Higher Order Functions, Recursive Functions

Created: Oct 12, 2020 11:43 AM
Reviewed: No
Type: OCaml

# type inference:

- ocaml infers the type of an expression by looking at:
    - its components
    - its context

```ocaml
let succ x = x + 1;;
```

- '+' is a function, infers int → int → = <fun>
- knows it's not floating point addition because there is another operator for that: '+.'

# objected oriented ocaml

# higher order functions

```ocaml
let dons a b = a::b;;
val dons : 'a -> (('a list) -> ('a list)) <fun>

(dons (47)) (* will return a function, then call dons again, with that function as the second argument *)
(dons (47)) ([5;9;2;]);; 
```

- higher order functions can have inputs that are functions, return value is a function
- **currying** - the original motivation was using higher order functions to simulate multiple argument functions
    - Haskell Curry was writing papers about functions and how to compute things, he had to use a lot of subscripts, which made the paper and code hard to read
    - so he decided to write the theory of functions with just one argument, and said that one argument functions can do anything that multi argument functions can do, so long as you allow higher order functions

    ```ocaml
    f a b c = ((f a) b) c

    type: A->B->C (where A is a's type, etc) 
    call the function with argument a, then call it again with the function it returns as argument B, etc
    ```

# pattern matching  (ocaml warnings??)

- *pattern matching is not exhaustive* - means that you've specified that the code should match a value against a series of patterns, but its possible that no pattern will match, so the compiler won't know what to do
- *syntactic sugar* - short, easy to read syntax that has exactly the same meaning as a simpler but more verbose syntax

    ```ocaml
    (++i) is syntactic sugar (i = i + 1) in C
    ```

# more functions

in Ocaml: 

![[Higher Order Functions, Recursive Functions/Untitled.png]]

in C: 

![[Higher Order Functions, Recursive Functions/Untitled 1.png]]

## recursive functions!

- use 'rec' for recursion
- ordinary 'let' requires you to define f in terms of functions that are already defined identifiers
- 'rec' tells the ocaml system: let me define my function within itself
- why do we have to SPECIFY 'rec'? he will tell us later, it is important
- recursion is powerful and dangerous, don't use it lightly

```ocaml
(* calculates minimum value of a list *)
let rec minval l = 
	match l with 
	| [] -> 99999999999999999999999 (* this is too specific and bad, only works with lists of ints *)
	| h::t -> let tmin = minval t
							if h < tmin then h else tmin 
```

instead: 

```ocaml
let rec minval lt id l = match l with 
	| [] -> id
	| h::t -> let tmin = minval lt id t in 
							if lt h tmin then h else tmin
```

- 'lt' is the less than function
- 'id' is the number greatest number
    - so 'minval (<) 9999999999 list' is equivalent to the first function