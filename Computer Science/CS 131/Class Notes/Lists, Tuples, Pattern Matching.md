# Lists, Tuples, Pattern Matching

Created: Oct 9, 2020 12:07 PM
Reviewed: No
Type: [[OCaml]]

# Why OCaml?

- Strong
- Functional, and also supports imperative & OOP Styles
- type inference
- no side effects
- easy parallelism, upscaling

# Lists in OCaml

- Homogeneous, immutable

### empty list

```ocaml
[];;
```

### Defining Lists

```ocaml
let l1 = [1;2;3;];;
let l2 = 1::2::3::[];;
```

- these create the same list using 2 different methods

### append operator

```ocaml
a@b
append a b
concat [a;b]
```

- all three of these are equivalent, where a and b are both lists

### Separating the list

```ocaml
List.hd [1;2;3];;              (* 1 *)
List.tl [1;2;3];;              (* [2;3] *)
```

- hd - the head of the list, first element
- tl - the tail of the list, every element after the first (body)

# Tuples

- heterogenous, immutable

### ex tuple

```ocaml
("3", 4, .5, "turtles");;
```

- 

### first and last elements

```ocaml
fst ("1", 2);;                        (* "1" *) 
snd ("1", 2);;                        (* 2 *)
```

- only works on tuples with size 2

# Functions from the "List" module

![[Screenshot_from_2020-10-09_12-24-02.png]]

noteworthy:

list.filter

### Pattern Matching

```ocaml
let rec inList a lst = 
	match lst with
		[] -> false
		| head::body -> if a = head then true
				else inList a body
```

- 

string_of_int (int) → converts int to string

### Data Structures

```ocaml
type my_type int * (int list) (* (3, [1;2]):my_type *)

type my_type2 = int * char * (int * float) (* (3, 'a', (5, 3.0)):my_type2 *)

type shape = Rect of float * float  (* width * length *)
		| Circle of float                (* radius *)
	

type quiz_grade = float / float * 100.
(*  gives a quiz grade out of 100
correct answers / all questions * 100 *)

(17,20):quiz_grade (* => 17/20 * 100 = 85 *)

type rock = "rock"
type paper = "paper"
type scissors = "scissors"
type shoot = rock | paper | scissors

(rock):shoot
```

- Type can be used to create new names for types, as well as variant types
- kinda like a poor man's class from java - we define our own types to create instances of them
- "|" pipe - the "or" symbol. Types can have multiple definitions - instances of the type need only fulfill one

```ocaml
type ('nonterminal, 'terminal) symbol =
  | N of 'nonterminal
  | T of 'terminal

let rec cleaned lst_of_symbols = 
	match lst_of_symbols with
	| [] -> []
	| first::rest_symbols ->
		let cleaned_rest_symbols = cleaned rest_symbols in (*actual recursive call takes place here, returned as a list called cleaned_rest_symbols *)
		match first_symbol with (*figure out if a symbol in our grammar is okay *)
		| N sym -> sym::cleaned_rest_symcols (*nonterminal with a value of "sym" type => add it to the rest *)
		| T _ -> cleaned_rest_symbols;; (* terminal symbol with no value => don't add it to the rest *)
```

- underscore: wildcard pattern matching. used when we don't care about the value of a variable

# "lambda expressions"

```ocaml
fun x -> x*2
```

/everyone be gay

/lesbian growl instead of saying hello

- [ ]