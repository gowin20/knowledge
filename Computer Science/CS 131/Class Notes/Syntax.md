# Syntax

Created: Oct 14, 2020 1:11 PM
Reviewed: No
Type: Grammar

[[Syntax]]: the form of a language, independent of meaning

Hello linguistics!

"colorless green ideas sleep furiously"

- how many times have we heard this example!

english is ambiguous, not good for computer programs 

- i feel like all of this is obvious lol

![[Computer Science/CS 131/Class Notes/Syntax/Untitled.png]]

# Grammars

- part of the birth of CS in the 1960s, made CS respectable
- used over and over again, in not only languages, but also in data and network protocol
- come in many flavors, each with different capabilities
    - regular exps are notations for simple grammars
        - not powerful enough → can't do nesting, so they aren't good enough to do C, Java because those include nestin g
    - BNF: "Backus Normal Form"  or "Backus-Naur Form"
        - notation for *context free* grammars
        - the most common tech used for grammars in programming
        - *context free grammar* allows nesting
    - EBNF → extended BNF, uses auxiliary notation to make grammars easier to understand

context-free grammar: the basic version most grammar systems that we've used in Linguistics thus far

consists of:

- A finite set of *tokens* (aka terminal symbols, output), typically a few dozen
    - sample lexicon: [{,(,),+,-,ID,NUM, if, else, while, ...}]
    - (ID stands for any identifier [a-zA-Z_][a-zA-Z_0-9]*)
    - NUM is any number [0-9]+
- A nonempty finite set of *nonterminal symbols*
    - These describe the interior nodes of your parse tree
    - eg {expression, statement, type expression, ...}
    - higher level of abstraction than tokens
    - describe entire phrases of your tree
- A finite set of rules
    - specify how you can generate phrases from other phrases
    - each rule is a replacement rule, lets you replace a single nonterminal (the left hand side) with a finite sequence of symbols (either tokens or nonterminals)
- A start symbol, one of the nonterminals, specifying the top node in the parse tree

A *sentence* is a finite sequence of terminals that be derived from the grammar, by starting with the start symbol and by repeatedly applying rules, one at a time, until no nonterminals remain

A *grammar* describes a language, which is the set of sentences you can derive from the grammar

# things about grammars

- use recursion heavily. practical BNF grammars are invariable recursive
- recursion is hard. but egger thinks that everything else is boring
    - commonly used auxiliary notation to make the grammars easier to understand
    - EBNF → extended BNF, uses auxiliary notation to make grammars easier to understand
- there are lots of notations from grammars, both for BNF and for EBNF
    - do as the romans do

# example notations for grammars

- Internet RFC 5322 (for email)
    - in email headers, you have a line like this:
    - "Message ID: <eggert.$423423."xyz"@cs.ucla.edu>" (not valid according to grammar)
    - uniquely identifies the email, to be able to catch duplicates
    - Internet RFC grammar for this:
    - msg-id       =   "<" id-left "@" id-right ">"
        - ms-id, id-left, id-right, are nonterminals
        - the terminals are <, @, >

Another example grammer: dot-atom-text

EBNF Form: 1*atext *("."* 1*atext)

- atext = printable US-ASCII characters not including special symbols
- 1*x means one or more occurences of x
- *x means zero or more occurences of x
- EBNF: one of more occurences of atext, then zero or more dots followed by one or more occurences of atext

grep -E equivalent: '[a-z]+(\.[a-z]+)*'

BNF Equivalent rules:

- dot-atom-text = word dotwords
- word = atext
- word = word atext
- dotwords =                                                (empty, also denoted with epsilon)
- dotwords = dotwords "." word

this grammar is the result of negotiation among email suppliers

assuming "msg-id" is the start symbol

this grammar is so limited in recursion, it could be done using a regex 

# ISO standard for EBNF

- ISO standardizes everything → from electrical sockets to javascript
- standards that have grammars in them, needed a standardized grammatical notation
- created a international committee to standardize, but they didn't always agree
    - eg, you can use double or single quotes to wrap tokens
    - **notation**

        [[Notation]]

### ISO EBNF Standard is defined within the ISO EBNF Standard

ISO EBNF defined within ISO EBNF:

- syntax = start symbol, meta id = any nonterminal
- syntax = syntax rule, {syntax rule}
- syntax rule = meta id, '=', definitions list, ';'
- definitions list = definition, {'|', definition};
- definition = term, {',' term}
- term = factor, {'-', exception]
- ....etc
- questionable to define notation in terms of itself, they solve the problem by defining it elsewhere and putting all of this in an appendix

# one more notation - featuring DIAGRAMS!

- george is excited abt diagrams
- "syntax graphs" "syntax charts" "syntax diagrams" etc
- 

![[Computer Science/CS 131/Class Notes/Syntax/Untitled 1.png]]