# Scope

Created: Dec 17, 2020 7:56 PM
Reviewed: No
Type: Memory

# Static Scoping

A programming convention that sets the scope of a variable such that it can only be referenced within the scope it's defined in

- AKA Lexical Scoping
- [[C]], C++, Java are always statically scoped

Variables always refer to their top-level environment

From looking at the code, you know what each variable refers to. Easier to write modular code

Bound variable is independent of the runtime function call stack

```c
int x = 20;

int f() { return x; }

int g() {
	x = 20;
	return f();
}

printf(f());
printf(g());

/* output:
10
10
*/
```

# Dynamic Scoping

A global identifier refers to the identifier used in the most recent environment

Each identifier has a global stack of binding. The definition used is the most recent binding on the stack

```c
int x = 20;

int f() { return x; }

int g() {
	int x = 20;
	return f();
}

printf(f());
printf(g());

/* output:
10
20

^ 20 because the most recent binding of X when g is called is within G
*/
```

Implementing using just a stack:

dynamic scoping is easier with just a stack, because you're just looking at the local 

iterate through the stack frames (activation record) and see if the variable is defined there

static scoping:

keep a mapping of each variable and function to the environment in which it is defined

the environment of a function is the scope of where it is defined in the code, so keep track of that

call stack: a master stack of activation records (aka stack frames) which are added to the stack as new methods are called, and removed as those methods return

activation records are implementation specific