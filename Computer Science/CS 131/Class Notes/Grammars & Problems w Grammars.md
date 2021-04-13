# Grammars & Problems w Grammars

Created: Oct 21, 2020 12:05 PM
Reviewed: No
Type: Grammar

# simple english grammar

```ocaml
S → NP VP
NP → N
NP → Adj NP
VP → V
VP → VP Adv
```

N = dog, cat

V = bark, meows

Adj = green, blue

Adv = loudly, backwards

honestly we know all of this i don't even need to take notes but i want to document the one time im actually understanding something in his class

- problem is, this grammar allows sentences that aren't grammatically correct:
    - green dog bark loudly. → because the grammar doesn't keep track of singular vs plural
- ok so we want to make our grammar pickier so this doesn't happen
    - to solve this, we are going to have 2 types of sentences: one with singular nouns / verbs, and the other with plural nouns / verbs

    ```ocaml
    S -> SNP SVP
    S -> PNP PVP

    SNP -> SN
    SNP -> Adj SNP
    SVP -> SV
    SVP -> SVP Adv

    PNP -> PN
    PNP -> Adj PNP
    PVP -> PV
    PVP -> PVP Adv
    ```

    SN = dog, cat

    PN = dogs, cats

    SV = barks, meow

    PV = bark, meow

    etc

- since we went from one type of sentence to two, we doubled the amount of lines by about 2
    - not quite 2 because we didn't have to change adj and adv
    - 9 rule

# problem with grammars

1. the number of rules in a grammar will grow exponentially based on how many attributes you have 
2. ambiguous grammars: will allow too many parsings of the same sentence

    ```ocaml
    ex: 
    E -> E + E
    E -> E * E
    E -> ID
    E -> NUM
    E -> (E)

    3 + 4 * 5 
    can be parsed in two different ways: 

    3, 4, 5 are all expressions 
    E * E is valid, so is E + E

    so you can either go: 
    (3 + 4) * 5
    or 
    3 + (4 * 5) 
    ```

- we fix this by adding a "term" to the grammar, but this still doesn't help all the way because we still can have addition done either way
    - eg: (3 + 4) + 7 vs 3 + (4 + 7)
    - matters when we're dealing w floats + ints, etc

    ```ocaml
    E: expression
    T: term
    F: factor 

    E -> E + T
    E -> T
    T -> T * F
    T -> F
    F -> ID
    F -> NUM
    F -> (E)
    ```

    ```ocaml

    **** i don't think this is right i'm quite confused on what he did 
    		 his handwriting is so fucking shit that i can't understand what he's even writing ****

    how this works: 
    4 + 9 + 12

    all the nums are factors 
    turn each into a term 
    since there is no rule that says that you can add 2 expressions, you must add the first two numbers first
    because you make the 4 into a term, then an expression
    add to 9, which is a term
    add to 12, which is a term 

    if you did it the other way:
    9 + 12 becomes an expression
    for some reason 4 is an expression here too? why can't it just be a term
    	i guess maybe u can't do T + E?? idk 
    but since 4 is an expression too you can't add two expressions so this wouldn't work

    ```

3. automating parsing of expressions

- parsing: given the token sequence for a purported sentence:
    - produce a parse tree, a proof that it's a valid sentence OR failure indication
    - three problems with parsing:
        1. recursion → parsers must create trees of arbitrary depths
            - this is always going to happen with parsing
        2. concatenation 
            - A → B C D
            - how do you concat a parser for D, for C, for B, etc, to get the big parser for A
        3. disjunction 
            - A → B | C | D
            - this is the hard part
            - One way to handle this is using an *acceptor*

    acceptor: 

    - a function which tells you whether your caller likes your parse
    - a callback to be invoked when your matcher succeeds
    - lets you fall back on an alternative when your **caller** doesn't like one of the rules
    - The matcher doesn't fully exit when it satisfies a disjunct
    - con: acceptors make concatenation harder to do
        - you might need to backtrack into an earlier part of a concatenation

# how to look for ambiguity

- look for associativity problems (binary operators)
- look for precedence problems (unary / binary operators)
- look for another class of problems: the "dangling else class"
- example grammar for C

![[Computer Science/CS 131/Class Notes/Grammars & Problems w Grammars/Untitled.png]]

```ocaml
if (Expr) Stmt else Stmt             <----- too generous, allows ambiguity 
so the problem here is that if Stmt = another if, this is ambiguity 

1. if (a == 3) if (b == 2) z == 1; else z == 3
2. if (a == 3) {
	if (b == 1) 
		z == 1;
	else 
		z == 3;
}
3. if (a == 3) {
	if (b == 1)
		z == 2;
}
else {
	z == 3
}

so we break this up: 
Stmt: 
Stmt1
if (Expr) Stmt 

Stmt1: 
; 
Expr;
...
if (Expr) Stmt1 else Stmt
...

so basically, we now cannot have a double if, Stmt1 can never be an if 
```

# precedence

- binary ops are left associative, except ** right associative
- unary ops have higher precedence
- this usual way of doing things makes the parse trees simpler