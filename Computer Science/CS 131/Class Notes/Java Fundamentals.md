# Java Fundamentals

Created: Oct 28, 2020 12:01 PM
Reviewed: No
Type: [[Java]]

# Java differences from C++

- Java tries to be portable → same app on multiple devices
- C, C++, size of data types (int, long, etc) depend on machine
    - x86: 32 bits, etc
- Java: long is always 64 bits
    - twos complement only
    - no endianness because no pointers

    ```ocaml
    a = b * c + f(x) // order of eval is left to right
    int x;           // x initially = 0 or compiler complains
    ```

### Java arrays

- Java arrays are objects (vs concatenation of elements in C++)
    - allocated on the heap (all objects are allocated on heap)
    - exist separately from where they were declared
    - create an array via 'new' keyword
    - no explicit delete, if you stop calling / using it, it will be deleted (automatic garbage collection!)
    - size of an array is fixed once allocated, but size isn't part of the type!

### Java references

- no pointers in Java
- instead, there are references ("tamed pointer")
- properties of references:
    - can't point into an array
    - can't take the address of a variable
    - reference is like a hidden pointer to the representation of the object
    - object assignment in java is always pointer assignment

### Java classes and inheritance

Instead of multiple inheritance, java only has single inheritance

- Class can only have one parent class that it "extends"
- 

### Interfaces

Java uses interfaces instead:

```java
public interface Drawable {
	public void draw (DrawWindow w);
	public void erace (DrawWindow w, int timeout);
	...
}
```

An interface consists of a "class" containing only empty method declarations. Any class can "implement" an interface, which means that it must provide method definitions for each method defined in the interface

- Implementation of an interface requires the child class to write code for the method - it's like inheriting a debt
- Advantage: This makes your class's objects compatible with other classes who also implement the same interface. You can use stuff in more places than before

### Abstract Classes

An ordinary class combined with an interface

```java
abstract class Ticket {
	abstract int priority(); //abstract method: API only
	int price() { return cost + profit; } // "concrete" method: API + code
}

//extending the abstract class is just like extending a normal class.
// for any "abstract methods," we MUST provide implementations of them here
// ^ just like interfaces
class Foo extends Ticket { ... }

//ACCOMPLISHING THE SAME THING WITHOUT THE ABSTRACT KEYWORD:
//all 'concrete' methods are in a concrete class
class Tick { int price() { return cost + profit; } }
//all 'abstract' methods are in an interface
interface TickInterface { int priority(); }

//the foo class extends the concrete methods, and implements the interface
class Foo extends Tick implements TickInterface { ... }
```