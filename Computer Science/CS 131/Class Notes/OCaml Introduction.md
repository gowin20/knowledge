# OCaml Introduction

Created: Oct 2, 2020 12:05 PM
Reviewed: No
Type: [[OCaml]]

A purely functional programming language

- Finctions are "first-class objects"
- you can treat functions as if they were any other variables
- can also pass them into other functions

Statically typed from the start, with type inference for variables

- don't need to specify the type of variables - like Python, but less flexible
- functions must have defined types. Like C, not Python
- functions cannot have overloaded definitions

# Basic Syntax

File extension: ***.ml***

### C: End of Line

```ocaml
;;

print_string("Hello World");;
```

### C: Comments

```ocaml
(* comment is like this! *)
```

- no such thing as a single-line comment

### C: Variables

```ocaml
let a=10;;
```

- 

### C: If statement

```ocaml
if i < 5 then a + 1 else a * 2;;
```

- also a functional return
- similar to the ternary expression in C/C++ (a < 3 ? a+5 : a-1)

### C: Basic Algebraic Operators

```ocaml
+ - * /   (*operations on integers*)
+. -. *. /.   (*operations on floats*)
```

- only apply to variables of the same data type

### C: Function syntax

```ocaml
(* (a,b) ===> <float>,<float> *)
let average a b =
	(a+. b) /. 2.0;;

average 1. 5.;;

val average : float -> float -> float -> float = <fun>
```

- 

### C: Recursive functions

```ocaml
let rec range a b =
	if a > b then []
	else a :: range (a+1) b;;
range 1 10;;
```

- 

### C: Polymorphic Functions

```ocaml
let identical x = x;;
```

- similar to templates, no specific type

    ### C: Defining an Anonymous Function

```ocaml
(* two times x *)
fun x -> x * 2;;
(* sum of x and y *)
fun x y -> x + y;;

(* passing 3 into this anonymous function *)
(fun x -> x * 2) 3;;
```

- doesn't have to be an explicit function
- exactly like a lambda operation

### C: Local variables inside a function

```ocaml
let plus_3_plus_5_times_8 x =
	let a = 3
	and b = 5 in
	let c = a + b in
	(x + a + b) * c;;

plus_3_plus_5_times_8 0;;
```

- let / in just like in haskell, allows for local declaration of variables such as a b and c

### C: quitting

```ocaml
exit(0);;
```

- exits the OCaml shell