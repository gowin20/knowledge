# Compilation Parsing and Linking

Created: Oct 26, 2020 12:01 PM
Reviewed: No
Type: [[C]], Grammar

![[Computer Science/CS 131/Class Notes/Compilation Parsing and Linking/Untitled.png]]

## Transition Steps

```c
#unclude <stdio.h>
int main(void) {
return getchar();
}
	    getchar                        main                             getchar
[EXT] [INT]  [ID] [(] [VOID] [)] [;] [INT] [ID] [(] [VOID] [)] [{] [RET] [!] [ID] [(] [)] [;] [}]
19     12     2   13   27    14   6   12    2   13   27    14     ...

// The compiler turns our code into a list of tokens like the above
// the parser then parses this code within the paradigm of the C langguage
```

code 

semantic analysis, filling in the tree

- create a tree
- look up types of tokens in the symbol table, in order to make sure it's well formed
- type inference for operations as well:
    - for instance, when you add an INT and a FLOAT, it outputs a FLOAT. check the data types of the operands and fill in what type the result will be

intermediate code generation (some kind of abstract assembly language)

- turn it into "c assembly" kinda
- Transitioning from a parse tree to instructions is difficult
    - Simple approach: write a translator from parse trees to machine code, that does this:
        - for each node in the tree
            1. Translate each child into machine codes C1, C2, ...
            2. Glue together C1, C2, ..., into something that implements the entire code
- that intermediate assembly can be shared between all parts of the compiler
- then, different parts of the compiler will turn it into different types of actual assembly (x86-64, ARM, RISC U)
- 

    ![[Computer Science/CS 131/Class Notes/Compilation Parsing and Linking/Untitled 1.png]]

    example "intermediate assembly"

# execution steps

- preprocessor
- tokens
- semantic analysis and creation of parse tree
- .....conversion into intermediate assembly and distribution to parts of the compiler
- assembly
- object code
- executable
- load the executable into memory
- program then sits in RAM

# linking

- combine .o files of your program with the .o files of the C, C++, other libraries
- each library's .o files are combined into .a files
- *static linking*: gcc combines your .o files with a library .a file, say, libc.a into an executable with a copy of all of this stuff
    - each executable is separate, can be separately optimized, only contains the code it needs
- 2 major downsides of *static linking:*
    - if there is a bug in a library, for ex, you find that your getChar() function doesn't work write w ur code, all the files must be relinked using the library. you might not have the object code though
    - if you're running several executables at once, you have a separate copy of each library in each executable
        - this consumes extra memory and extra cache
- *dynamic linking*
    - executable only contains stubs, not library code
        - when you call the stub, it finds the code in RAM and instantiates it during runtime
        - you only need one copy of everything, don't need to relink everything every time
    - *load time dynamic linking:* link together all the libraries before main() starts running
        - executable is running, but main() is not run until everything is linked
    - *runtime dynamic linking:* program itself decides what to link using standard functions like 'dlsym'
        - self modifying code: executable modifies itself as it runs, using dynamic linker
- **self modifying code** suggests a different way of building executables
    - *software tools approach (talked abt before break):* executable is built via a bunch of separate tools
        - each reads some files and outputs others, tools are replaceable, communicate via byte streams
        - UNIX, Bell Labs, ancestor of LINUX
    - *integrated development environment approach (using self modifying code):*
        - one big happy application, called IDE
        - IDE is text editor, your compiler, your debugger, all in one interface, hooked together via object oriented tech (classes, methods, where your program text, object code, are all objects)
        - Smalltalk, Xerox, ancestor of OO languages