# Language Design Issues

Created: Oct 5, 2020 12:04 PM
Reviewed: No
Type: Comparing Languages

# Languages we'll be Learning

Three "stem" languages from which most modern technology has descended

1. Java / Scala, etc.
2. ML / [[OCaml]]
3. Prolog

Additional Important Languages

- Scheme / Lisp (AI, metaprogramming - programs with programs as input / output)
- Python
- One additional language (Dart / Go / something else)

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/Language Design Issues/Untitled.png]]

Literate Programming 

- write a paper at the same time that you write the corresponding program
    - both in the same src code file

    pseudocode and literal code translation next to each other

pascal code: 

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/Language Design Issues/Untitled 1.png]]

Hash trie - like a hash tree, but combined with an array mapped trie

- Easy to add words and traverse in decreasing count order

### bash script to count words

```bash
tr -cs 'A-Za-z' '[\n*]' |
sort |
uniq -c |
sort -nr
```

tr

- -c : complement the set
- -s : squeeze duplicate outputs

uniq

- -c : gives us a count of each unique word

sort 

- -nr : sort in reverse order

always pick the right language

# Core of Programming Languages

Each language follows a separate programming model. Each model is based on certain principles and has certain limitations

- Design of notation
- use
- support for

# Language design issues

### Orthogonality

- different features of your language should be independent types vs. object lifetimes
- Non-orthogonality in C:
    - a function can return a value of any type EXCEPT FOR arrays
    - arrays "decay" to pointers by default. That means when attempting to return an array, it just returns a pointer to an array instead.
    - This is weird because functions should be robust and able to return values of any type

### Efficiency (runtime)

- CPU time
- clock time
- RAM (local storage)
- I/O (to flash or disk)
- Network access (often biggest bottleneck)

### Simplicity

- things should be as simple as they can be
- ex: python. No extra syntax to learn in order to increment variables (no i++ or ++i), prefer that people use i = i+1 (they would add i += 1 later)

### Convenience

- take few steps, little time to read and write the program

### Safety

- ex: static vs dynamic check of programming language rules
- char * p = NULL; * p = x;
    - dereferencing a null ptr → this is an error in C, C++, the implementation is not required to detect the error; in CS 31, the implementation catches this error at run-time
    - in OCaml, compiler will give not allow you to run this → dereferencing null CANNOT occur
        - means that OCaml is much SAFER in this case than C or Java
- Static error checking does not allow for ambiguity. While it's less flexible, it will never allow undefined behavior such as dereferencing null pointers during runtime.

### Exception Handling

- related to safety, another way to do dynamic checking
- oftentimes violates abstraction

### Abstraction

- How well can you build abstraction layers in your program?
    - should be easy to see your program at a high level, like a birds eyes view

### Concurrency

- parallelism

### Mutability

- How easy is it to change and improve the language and syntax and notation itself?
- Should be an evolving language