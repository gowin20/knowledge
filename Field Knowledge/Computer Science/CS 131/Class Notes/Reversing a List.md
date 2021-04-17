# Reversing a List

Created: Oct 14, 2020 12:01 PM
Reviewed: No
Type: [[OCaml]]

### Using Recursion to reverse a list

[a;bc;d] → [d;bc;a]

```ocaml
let rec buggy_reverse = function 
	| [] -> []
	| h::t -> buggy_reverse t @ h

ocaml outputs: 
val buggy_reverse: 'a list list -> 'a list = <fun>
we can see this is wrong, since types are wrong !!
	
```

```ocaml
let rec reverse = function 
	| [] -> []
	| h::t -> (reverse t) @ [h]
```

- Wrapping the list head in brackets [] allows the concatenate operator to function properly, as it requires two lists as input'

'@' → concatenate operator 

- Concatenates two lists together. Similar to append in the List module, or concat
- takes in two lists and gives you one list
- if you input only one list, it instead returns a function. This function will take a list as input, and return that list concatenated with the original list you gave it

```ocaml
[1;5]@[3;7]
= 
[1;5;3;7]
```

- this works well, but isn't efficient
    - example: if we try to reverse a list of length 1,000,000
        - we reverse a list of length 999,999, and then call concatenate to add that to [h] → O(N) each time through the loop
        - so this = N + N - 1 + N - 2, etc, as you go through each iteration
        - this means the efficiency = N(N + 1) / 2 = O(N^2)

### Avoiding O(n**2) behavior

1. step outside the box, solve a more general problem
2. use a accumulator
    1. an extra argument given to a recursive function 
    2. not really needed by callers of the func
    3. lets the rec function do the work by accumulating work done so far

```ocaml
(* compute the reverse of l, concatenated with a. *)
let rec reverse_append l a = match l with 
|[] -> a
| h::t -> reverse_append t (h::a)

(* compute the reverse of the second arg, concatenated with A *)
let rec append_reverse a = function 
| [] -> []
| h::t -> append_reverse (h::a) t
```