# Basic Java Properties (week 3 discussion)

Created: Oct 21, 2020 12:05 PM
Reviewed: No
Type: Java

# Java

- everything is in a class
- say you have a [helloworld.java](http://helloworld.java) with a class 'HelloWorld'→ compile using 'javac helloworld.java' which creates the class HelloWorld
    - run using 'java HelloWorld'
- constructor
    - same name as class name, initializes values
    - no destructor bc java is nice and does garbage collection for u
- java code is compiled to bytecode
    - runs on a JVM → java virtual machine
- OOP
    - each module correlates to a certain functionality
    - reuse code
    - easy to debug
    - intuitive
    - popular
    - basically java is great
    - fuck da camels
        - do u like my use of 'da'
        - im imitating u
    - objects, have methods (functions) and fields (variables)
    - objects of the same class have the same fields and methods
    - to use an object make an instance of a class
        - im just wasting my finger energy at this point like do i rly need to take notes on this not rly

# key features of OOP in java

- abstraction
- encapsulation
    - private variables
    - no external interference
- inheritance
    - 'extends' keyword

    ```ocaml
    TA extends Student

    TA a = new TA();
    Student b = a;

    Student a = new Student();
    TA b = a;

    Student a = new TA();
    TA b = a; //does not work because Student is the parent class 

    Student a = new TA();
    TA b = (TA)a; //so cast it instead
    ```

- interface
    - class can implement multiple interfaces
    - '*implement*' keyword
    - ALL functions are abstract: has method declarations with no bodies
        - must implement all the methods, then create instance
- abstract classes
    - methods do not need to have function bodies, but CAN
    - '*extend'* keyword
    - cannot create an instance of this class
    - you must create a child class, implement the function bodies of the abstract class, then create an instance
- use 'extends' when the subclass wants to use functionality already declared in the super class
- use 'implements

# polymorphism in java

- **method-overloading** → static
    - static: method is decided after compilation, since we're just looking at the argument lists
- **method-overriding** → dynamic
    - dynamic: method to be called is decided at runtime, since you need to know the type of the variable that is calling the function
- overloading: within a class, more than one method having the same name w diff arguments
- overriding: a subclass is implementing a method of its superclass

# generics in java

```ocaml
class Box<T> //called by var box = new Box<String>;
```

- specifically handles given type T
- easy to debug, elegant
- compile time check

# hw 3

- step 1: remove the 'synchronized' keyword from the function and change the class name
    - figure out the performance now and how to make it better
- step 2:

*synchronized*

- each object has one lock
- only one thread can enter the sync method at any time
    - so after removing you're going to have risk conditions because there's going to be a billion function calls that are executed NOT one by one

*concurrency*

# java memory model (JMM)

- multiple CPUs
- multiple threads of the same process distributed onto different CPUs
- every CPU has its own cache
- without additional action there is no guarantee when the cache will sync w main memory

![[Computer Science/CS 131/Class Notes/Basic Java Properties (week 3 discussion)/Untitled.png]]%20acae65454d2d4f04ac050536e4738fa7/Untitled.png)

- *volatile* keyword: the other threads will see the changes immediately, will sync with the other caches
    - can be added to both private and public variables
    - once updated by write, updates all the way to main memory
    - read from main memory
    - prevent reordering
- this isn't enough though because if 2 threads are reading / writing at the same time, that will still cause problems

# slides at the end have some options to make ur code atomic