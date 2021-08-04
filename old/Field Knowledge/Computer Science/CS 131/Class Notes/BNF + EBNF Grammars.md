# BNF + EBNF Grammars

Created: Oct 16, 2020 12:24 PM
Reviewed: No
Type: [[Grammar]]

hello there!

well hello! -shreya 

This week is for more [[OCaml]] grammar and syntax

left recursion

left-corner parsing!

right recursion

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/BNF + EBNF Grammars/Untitled.png]]

acceptor:

accepts a fragment and checks against a grammar

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/BNF + EBNF Grammars/Untitled 1.png]]

# BNF Grammars (Backus-Naur Form)

Consists of four parts:

- Set of tokens (terminal symbols)
    - Atomic, smallest unit of syntax
    - Strings in most cases
- Set of non-terminal symbols
    - Larger units of syntax
- Starting Symbol (nonterminal)
- Set of productions
    - AKA Rules
    - take the form left-hand side ::= right-hand side
    - LHS is a non-terminal Symbol
    - RHS is a sequence of 1+ tokens or nonterminals
    - BNF also allows these to be expressed as **LHS ::= list of possible RHS**
        - In the list of right-hand sides, each is separated by the special symbol **|**
        - 

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/BNF + EBNF Grammars/Untitled 2.png]]

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/BNF + EBNF Grammars/Untitled 3.png]]

# Partial Application

- Providing only part of the argument, thereby fixing the values of the function
- Creating a function with fewer argument

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/BNF + EBNF Grammars/Untitled 4.png]]

# Types

- Ocaml is a **strongly typed language**
    - every value should have a certain consistent type
- but Ocaml does type inference
    - so in most circumstances, you actually don't need to specify types
    - does this based on certain rules

# hw 2

- take a grammar, build a parser

### problem 1: convert the rule list of the grammar to a function

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/BNF + EBNF Grammars/Untitled 5.png]]

### problem 2: return a list of leaves from the left to the right

- counter process to parser
- here you're taking a result, and returning the original symbols
- so you need to walk through this tree, and walk through the leaf nodes from the left to the right

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/BNF + EBNF Grammars/Untitled 6.png]]

### prob 3: returns matcher for grammar gram

- matcher tells us if prefix of input can be generated using grammar
- not looking for longest match → return first match found

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/BNF + EBNF Grammars/Untitled 7.png]]

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/BNF + EBNF Grammars/Untitled 8.png]]