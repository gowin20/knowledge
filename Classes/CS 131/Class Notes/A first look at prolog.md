# A first look at prolog

Created: Dec 16, 2020 1:39 AM
Reviewed: No
Type: Prolog, Textbook

Prolog: logic-based programming language

Prolog is a **declarative programming language**. Each statement is a declaration which corresponds to a simple mathematical abstraction in first-order logic. Viewed this way, prolog programs are simply a series of logical formulas which make assertions

you don't "run" programs. Instead, programs are a series of logical expressions. The user then poses questions to the program that are defined within its system

syntactically very simple, but looks very different than other languages

### Terms

The unit which everything in prolog is built from

Three main types of terms:

1. Constants
2. Variables
3. Compound Terms

**Constants**: integers, numbers, anything atomic

- Anything that starts with a lowercase letter is an atom!
- atoms are kinda like string constants in java, ml
- all of the following are constants:

```prolog
shreya
1
4
george
[]
=
@#$
```

**Variables:** anything beginning with an uppercase letter or underscore, followed by zero or more additional characters

```prolog
X
Child
Adult
_nice
_ONE
```

**Compound Terms**: A combination of many different atomic terms. Takes the form of a constant, followed by a set of parenthesis to specify arity

```prolog
x(y,z)
parent(adam,seth)
```

Simplified rule system:

![[A first look at prolog/Screenshot_from_2020-12-16_01-49-31.png]]

Know how the prolog grammar system works!!!!!

Tries rules from the top down

## Unification

Two terms in prolog **unify** if there is some way of binding their variables that makes them identical

```prolog
parent(bonnie,Child).
parent(bonnie,shreya).
```

These two terms unify by binding the "Child" variable to the "shreya" atom

Horn Clause: a logical formula that takes the form of a rule, useful in programming

all statements of the form

```prolog
a :- b.
```

are horn clauses

This is how the bulk of prolog programs are implemented!