# OCaml Basics + Resources

Created: Oct 12, 2020 11:43 AM
Reviewed: No
Type: [[OCaml]]

## OCaml Basic Properties

1. static type checking (checking types at compile time) 
    1. like Java, C++, C
    2. unlike Python, JavaScript
2. don't have to write down types all the time 
    1. like Python, Scheme
    2. not like C, C++
3. don't need to worry about storage management
    1. storage is automatically created and freed
    2. built in garbage collector 
    3. does this mean the heap and stack are the same? 
        1. there is a stack, but you don't need to worry about it 
        2. no pointers into the stack 
    4. no null pointers → yayyyyyy!!!!!! watch us still somehow get some ptr exceptions
4. good support for higher order functions
    1. it's a functional language
    2. but it's not purely functional ( you can create side effects, do bad stuff, etc, but you don't have to)
5. "we're adults, you know what you're doing, you can compare floating point numbers." 
    1. eggert thinks we know what we're doing lmao lol!

    Surface differences between OCaml and ML

    ![[Field Knowledge/Computer Science/CS 131/Class Notes/OCaml Basics + Resources/Untitled.png]]

[https://ocaml.org/learn/tutorials/basics.html](https://ocaml.org/learn/tutorials/basics.html)

[https://ocaml.org/learn/tutorials/99problems.html](https://ocaml.org/learn/tutorials/99problems.html)

[https://www.cs.umd.edu/class/fall2016/cmsc330/lectures/howtodebug_ocaml.pdf](https://www.cs.umd.edu/class/fall2016/cmsc330/lectures/howtodebug_ocaml.pdf)

[https://www.cs.cornell.edu/courses/cs3110/2019fa/a1/](https://www.cs.cornell.edu/courses/cs3110/2019fa/a1/)