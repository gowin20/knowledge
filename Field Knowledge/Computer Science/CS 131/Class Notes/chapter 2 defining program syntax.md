# chapter 2: defining program syntax

Created: Nov 3, 2020 2:55 PM
Reviewed: No
Type: Grammar, Textbook

- **syntax:** part of the language definition that says how programs look
    - form and structure
- **semantics:** part of the language definition that says what programs do
    - behavior and meaning

# grammars (simple english ex)

- set of rules that say how to build a tree for a particular language
    - tree is called a **parse tree**
    - children of each only have what is allowed by the grammar
    - by reading the tree left to right, you get a sentence

a simple grammar: 

![[Field Knowledge/Computer Science/CS 131/Class Notes/chapter 2 defining program syntax/Untitled.png]]

a simple tree: 

![[Field Knowledge/Computer Science/CS 131/Class Notes/chapter 2 defining program syntax/Untitled 1.png]]

# grammars (for programming languages)

- four important parts
    1. tokens - basically the terminals
    2. non terminal symbols - non terminal nodes
    3. productions - consists of a left hand side, the separator ::=, and a right hand side
        - left hand side is a non terminal, right hand side is a sequence of things, either terminal or non terminal
        - the right hand side rules may be separated by '|', for convenience
    4. start symbol - non terminal symbol that is root of tree

    simple grammar:

    ![[Field Knowledge/Computer Science/CS 131/Class Notes/chapter 2 defining program syntax/Untitled 2.png]]

    simple tree: 

    ![[Field Knowledge/Computer Science/CS 131/Class Notes/chapter 2 defining program syntax/Untitled 3.png]]

    - form for writing grammars was developed by John Backus & Peter Naur
    - notation of grammars is called Backus-Naur-Form (BNF)

# writing grammars

example: Java

- write a grammar for declaring a local variable

```java
examples: 
float a;
boolean a, b, c;
int a=1, b, c=1 + 2;

strategy: divide and conquer

what we know: 
let's say <var-dec> is the start symbol
major components are type name, list of variables, semicolon, so: 
<var-dec> :: = <type-name> <declarator-list> ;

<type-name> will be a java primitive type, so 
<type-name> :: = boolean | short | int | long | etc

<declarator-list> :: = <declarator> | <declarator>, <declarator-list> 
can either be just a declarator, or a declarator followed by a smaller list 
(like head::body)

<declarator> ::= <variable-name> | <variable-name> = <expr>

would then need to define <expr> and <variable-name> but you get the premise

```

# phrase structure vs. lexical structure

- usually specified with two different grammars
- phrase structure: token level grammar, defining a program as a sequence of tokens
- lexical structure: character level grammar, defining a text file as a sequence of program elements like tokens and white space

    ex: 

    ![[Field Knowledge/Computer Science/CS 131/Class Notes/chapter 2 defining program syntax/Untitled 4.png]]

# other grammar forms

- **BNF**
    - some minor variations
    - = or → instead of ::=
    - taking out angle brackets
    - BNF special characters: <, >, |, ::=
        - called metasymbols
- **EBNF (extended BNF)**
    - adding a few more metasymbols to BNF
    - [ ] mean optional
    - {} means whatever is inside the brackets can be repeated a number of times
    - parentheses used to group things so |, [], {} can be used in the same production
    - common patterns can be defined more easily
    - ex:

    ![[Field Knowledge/Computer Science/CS 131/Class Notes/chapter 2 defining program syntax/Untitled 5.png]]

# syntax diagram

- basically you just use arrows to link everything
- wtf is this shit i thought i was going to get some beautiful TPs and VPs and all of that
- this is ugly

![[Field Knowledge/Computer Science/CS 131/Class Notes/chapter 2 defining program syntax/Untitled 6.png]]

![[Field Knowledge/Computer Science/CS 131/Class Notes/chapter 2 defining program syntax/Untitled 7.png]]

# context free grammars

- type of grammars we've been looking at
- children of a node in the parse tree depend only on that node's non terminal symbol
- don't depend on other neighboring nodes