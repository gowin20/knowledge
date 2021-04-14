# Origins of Java

Created: Nov 3, 2020 11:56 PM
Reviewed: No
Type: [[Java]]

# Smalltalk

- smalltalk interpreter which executed "bytecodes" - instructions for an abstract Smalltalk machine
    - intermediate representation of the traditional approach, you could put them into files
- Smalltalk is an IDE, takes over your screen, can type Smalltalk code into a window, and it'll execute it
- modify the code that's displaying on your screen
    - like color of text you're writing
    - you edit the code that you run
- internally: code that you type is translated to portable bytecode
    - not machine specific (works on x86, x86-64, etc)
- a low level Smalltalk interpreter, written in ASM, executes the bytecode
    - machine specific
- all one big program, one big state
- type save to get the IDE to the way you like it
    - someone else can restore and they're running a copy of your IDE, and it should look just like a word processor
- **TURING AWARD given for this work to Alan Kay**

# The Origins of Java

- Created in the early 1990s by Sun Microsystems
- Sun Microsystems (now part of Oracle) were making good $$ selling workstations and servers using their proprietary software:
    - Solaris operating system (flavor of UNIX) in C/C++
    - SPARC processor and CPU (competitor to x86)

    Java originated when Sun Microsystems wanted to create intelligent toasters

    - Running the traditional Solaris OS on toasters was not feasible
        - SPARC CPUs are too expensive for toasters. x86 is too expensive as well
        - C and C++ have some shortcomings:
            - notoriously unreliable. People hate it when their toaster software bricks and burns their toast
                - are you sure? i like my toast burned personally. just like really charred
                - dw, our new toaster OS has a "shreya" setting which burns your toast for you
            - apps are bloated! in early 1990s, networks were 20 kb/s and unable to transmit giant apps quickly
                - why are apps so bloated?
                    - the executable uses dynamic linking, a.out files use dynamic linking
                    - dynamic linker needs tables in the executable to link code together
            - not well-suited for applications and front-end things like toasters

    Solution for toasters: Let's steal some ideas from Smalltalk

    - so needed some way to port Solaris to cheaper chips
        - app maker needed to recompile their apps for each toaster model
        - Positive of Smalltalk:
            - using bytecode:
                - executables are tiny instead of bloated
                - executables run on MIPS, SPARC, etc
                - bytecode interpreter can catch smaller errors and throw and exception to the exception handler, which can then decide what to do
        - Negatives of Smalltalk:
            - syntax was unusual → Sun decided to use C++ like syntax
            - developed like an IDE → Sun decided to take a bit of the software tools approach
            - Sun liked multiprocessor servers, wanted their solution here to scale to multiple CPU approaches → so they added multithreading
            - Sun wanted to include the internet, wanted to easily connect apps to internet, download apps from internet, apps update themselves
    - Solution:
        - Java Virtual Machine
            - formalization of Smalltalk interpretere
            - operates on instructions specified by JVM bytecodes
            - could be hardware, but its done via software almost everywhere
        - Java language
            - came up with a language to correspond to the JVM
            - syntax like that of C++
            - semantics were like Smalltalk
                - runtime errors are caught, storage management is automatic (eg no garbage collector needed!!!!!! so freaking helpful)
                - ONE MAJOR DIFFERENCE where Java differs from Smalltalk:
                    - Java (like C++), uses static type checking
                        - compiler checks type, not a runtime check
                        - this is more reliable than runtime checking, wanted their app to be reliable as a priority
        - after all of this, the project was about to be cancelled, but the engineers convinced their bosses to do some demos
            - this is a story that apparently cannot be fact checked so we'll have to take eggert's word for it???
            - included one demo: a competitor to the first successful web browser
                - the first successful web browser
                    - called Mosaic (early 1990s, UIUC)
                        - written in C++
                        - negatives: it was hard to update because you need to rerun the entire executable (inflexible), crashed a lot
            - Sun people wrote HotJava (mid 1990s)
                - written in Java
                - reliable
                - easy to update using "applets" - web page + JVM bytecode - allowed people to do animations of web pages
                - Eggert heard that HotJava was written in a weekend
                - not as efficient as Mosaic, but it addressed the downsides of Mosaic
            - convinced the bosses to not kill the Java project
            - Java turned out to be better for the server side
                - multi threading
                - static checking was better than Smalltalk's, or Python, etc
                -