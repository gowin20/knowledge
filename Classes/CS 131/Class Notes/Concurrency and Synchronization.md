# Concurrency and Synchronization

Created: Nov 4, 2020 12:22 AM
Reviewed: No
Type: Java

# Concurrency in Java

Concurrency: Multiple programs running simultaneously without stepping on each other's toes

Two main types of concurrency architecture:

SIMD (Single Instruction Multiple Data)

- A single instruction, "+" applied to two vectors of numbers, pairwise to get a vector of sums
- linear algebra. Apply the instruction to multiple numbers pairwise

MIMD (Multiple Instruction Multiple Data)

- Many different instruction pointers operating in parallel
- Each executing a part (typically different, possibly the same part) of the program
- + more flexible
- - more complex (harder to program, etc.

Modern computers, even cell phones, use both of these concurrency architectures

The most commonly used concept for programming these architectures is called a **thread**.

- A thread of execution corresponds to a SINGLE INSTRUCTION POINTER in an MIMD machine
- How Java implements concurrency

### The World's Current Fastest Computer:

- Fugaku
    - 158,976 CPUs
        - 48-core ARM each
        - all have 512-bit vector processing instructions
        - MIMD (158,976 * 48 instruction pointers)
        - SIMD (vector-processing instructions)
    - It runs Linux and its own kernel

    Probably shouldn't try to run java on this machine.

    - Java programming gmodel assumes that each thread can access each
    - called SMP: Symmetric Multiprocessing
        - All CPUs are the same
        - All access memory in the same manner
    - Doesn't scale well to large numbers of processors

### Thread's life cycle

- creation via 'new' in one of two ways
1. create an object of type subclass of Thread 

```java
class PurpleThread extends Thread
{
	void run()
}
Thread t = new PurpleThread();
```

2. Create a thread but give thread constructor a runnable object

```java
interface Runnable {
	void run();
}
class MyApp implements Runnable {
	void run();
	Thread t = new Thread(new MyApp());
}
```

![[Concurrency and Synchronization/Untitled.png]]

# synchronization

- for currency to work, we need synchronization
- several ways of doing this
- synchronized methods

```java
class C {
	int v;
	int next() {
		return v++;
	}
}

C o = new C();
Thread 1: int i = o.next(); //at about the same time 
Thread 2: int i = o.next();

class C {
	int v;
	synchronized int next() {
		return v++;
	}
}
```

- synchronized = Java compiler inserts code at the start of the method that "locks" the object the method is called on
- if some other thread has locked the object, the thread waits until the other thread unlocks the object
- other ways to synchronizie

![[Concurrency and Synchronization/Untitled 1.png]]

# Atomic Operations

synchronized: spend more time context switching gand using locks, which can be less efficient since the program itself is so small

atomic add / subtract:

low-level machine instructions in order to ensure data integrity

Compare and Swap:

- memory location (in this case, an index of an array)
- existing value of the variable A
- the new value, which needs to be set B

Update the memory location to be the new value B, but only if the existing value in memory matches A.

For increment:

add one to the value, but only if the existing value is B-1. that’s the gist of it

If this doesn’t hold, then no action is taken.

if it doesn’t succeed, we can either:

- move on and do other stuff
- keep trying again and again until it succeeds

```java
public class SafeCounterWithoutLock {
	    private final AtomicInteger counter = new AtomicInteger(0);
	    
	    public int getValue() {
	        return counter.get();
	    }
	    public void increment() {
	        while(true) {
	            int existingValue = getValue();
	            int newValue = existingValue + 1;
	            if(counter.compareAndSet(existingValue, newValue)) {
	                return;
	            }
	        }
	    }
	}
```