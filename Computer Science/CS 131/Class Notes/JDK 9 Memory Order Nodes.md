# JDK 9 Memory Order Nodes

Created: Nov 3, 2020 1:42 PM
Reviewed: No
Type: [[Computer Science/Java]], Memory

VarHandle memory order nodes

- can be associated with any field, element, or static
- declared as static final fields, initialized in static blocks

VarHandle: a stongly-typed reference to a variable

Accessing variables like this uses various types of "access modes":

1. Plain read/write access
2. Volatile read/write access
3. Compare-and-Set access

```java
import java.lang.invoke.MethodHandles;
import java.lang.invoke.VarHandle;
class Point {
   volatile int x, y;
   private static final VarHandle X;
   static {
     try {
       X = MethodHandles.lookup().
           findVarHandle(Point.class, "x",
                         int.class);
     } catch (ReflectiveOperationException e) {
       throw new Error(e);
     }
   }
   // ...
}
```

Three main forms of parallelism:

1. Task Parallelism
    - two threads executing actions A and B
    - in one processor, either A then B or B then A
    - multiple processors, A and B are completely unordered
2. Memory Parallelism
    - memory like caches is managed by multiple parallel agents at once
    - we don't need to represent variables directly on any single device
    - instead, we need all the threads to talk to each other and agree on values associated with specific addresses
    - memory performs "bitwise parallelism" - operations of more than one bit at a time
3. Instruction Parallelism
    - CPUs process instructions in an overlapped fashion
    - Multiple instructions can be executed at the same time
    - Pipelining basically, from 33

Synchronization is tricky to get right!

- Oversynchronization makes things slow
- undersynchronization makes things wrong
- non-standard synchronization makes things unportable

Memory Order Modes, from weakest to strongest:

1. Plain
2. Opaque
3. Release / Acquire
4. Volatile

These nodes describe relations along memory accesses

Avents: read, write, update

focus on ordering because that's the main constraint of memory accesses

Terminology:

- Strict irreflexive orders
- Total Order
    - each event is ordered with respect to every other event
    - results in a linear chain of events
- Partial order
    - any two events need not be related at all (can be concurrent)
    - there are NO cycles
- Linear Extension (aka Topological Sort) of a partial order
    - a total ordering that obeys alll of its ordering constraints
    - While things can be unordered in a partial order, they become ordered when you take the linear extension

Ordering is based off of two strict relations:

1. Within Threads
    - local precedence
        - denotes that A access precedes B access within the same thread
    - 
2. Across Threads
    - Read-by relation
        - orders interthread access
        - if Read Rx reads from the write of Write Wx, then Wx must occur before Rx
    - Reads-from function
        - ensures that each read reads from its source Write properly, similar to "read-by" but easier to use because it's an actual function
- Used to define the antecedence relation
    - Antecedence links temporal orderings within threads with those across threads
    - antecedes: precedes in time

Access A antecedes access B if any of these three hold:

- A locally precedes B within a thread (Intrathread)
- A is read by B in another thread (Interthread)
- For some access I, (A antecedes I) and (I antecedes B) (Transitivity)

# Plain Mode

Plain read and write accesses:

- bitwise atomic ONLY for references and primitive values of at most 32 bits
- no ordering constraints other than on the executing threads

applies to accesses of non-volatile object fields, as well as statics + array elements

all accesses are to method-local arguments and variables

- maintains Local Precedence order for accesses
- not in general a sequential order
- oftentimes, optimizing compilers will eliminite unnecessary accesses and encourage out-of-oder execution
- This makes code faster and better

- thread-confined variables
    - created and only ever used by the current thread
    - no accesses in the "read-by" relation

Default mode of operation for only one thread

In a synchronized method:

- all synchronized blocks of an object can have only one thread executing inside of them at a time
    - all other threads are blocked until the thread inside the synchronized block exits
- All Plain accesses within the region are within-thread
- may act as if thread-confined

All of the constraints of the stronger modes below are unnecessary / absorbed by the uniprocessor semantics

# Opaque Mode

- bitwise atomic
- coherently ordered w.r.t. accesses to THE SAME VARIABLE

Adds constraints over plain mode that make programs aware of the variables accessed by multiple threads

1. Per-variable antecedence acyclicity
    - For each variable accessed only in Opaque mode, the antecedence relation for that variable is a partial order
    - fixes several anomalies of Plain mode, especially those where future accesses appear to impact the past because of reordering
    - Only applies on the scale of single variables, no assurances about orderings of other variable accesses
        - Big limitation!!!! Makes it inapplicable in most interthread communication constructions
2. Coherence
    - Visible overwrites to each variable are ordered
    - if opaque mode is used for all accesses to a variable, updates do not appear out of order
    - does not hold if only the reads, not writes, are performed in opaque mode
    - Plain mode may skip / reorder writes, while Opaque mode doesn't
3. Progress
    - Writes are eventually visible
    - defining property of cache-coherent multiprocessors, as well as distributed data stores
    - to formalize progress guarentees, we can use these things:
        - Quiescent Consistency, Eventual Consistency, and Obstruction Freedom
    - Does NOT hold in plain mode - spin loops aren't required to notice writes if it was not seen on the first encounter
4. Bitwise Atomicity
    - If opaque or stronger modes are used for ALL accesses, then all reads are guarenteed to not mix the bits of multiple writes

Because Opaque mode doesn't directly impost ordering constraints w.r.t other variables, it has some limitations

- You can't always tell when Opaque mode will access a variable w.r.t other plain accesses
- reading a value in Opaque mode doesn't tell you anything about values of other variables
- coherence doesn't guarentee specific ordering, in particular for read-write pairings (where something must write then read in that order)

It's still useful, someitmes

- When collecting progress indicators that ONLY need to be accurate at the end
- When the surrounding constraints are strong enough that further ordering isn't necessary (just use plain mode here though)

# Release / Acquire (RA) Mode

- complies with opaque mode constraints
- reads and subsequent accesses are ordered, after matching "release" mode writes with their previous accesses

Builds on top of Opaque mode: Adds a "cumulative" casuality constraint

Extends the partial order antecedence guarentees to cover weaker accesses within the same thread

- If access A precedes interthread Release mode write W in the source program, then A precedes W in local order for thread T
    - If access A comes before write W in the program, then it also comes before in the local thread
- If interthread Acquire mode read R precedes access A in source program order, then R precedes A in local order for thread T
    - If read R comes before access A in the program, then it also comes before in the local thread

Main idea behind "casually consistent" systems

Basically, this just preserves ordering between multiple variables / accesses 

Nearly ALL java.util.concurrent components include this kind of "happens-before" consistency in their API documentation

When two or more threads can write the same variable at the same time, then RA mode falters

# Volatile Mode

- obeys all of the release/acquire properties
- all volatile operations are totally ordered w.r.t. each other

default access mode for the **volatile** keyword

- "stored in main memory", instead of the CPU cache
- guarentees that changes to this variable will be visible across threads

adds this requirement to Release / Acquire Mode:

- Volatile mode accesses are totally ordered (Interthread)

when all accesses use volatile mode, program execution is sequentially consistent

- two volatile accesses A and B, either A precedes B or vice versa
- In normal RA mode, they might be unordered and concurrent

- opaque mode relies on acyclicity
    - for each variable, antecedence is a partial order
    - guarantees about access atomicity, etc
- Volatile mode relies on concensus
    - total ordering of accesses
    - threads all reach agreement about program states
- release / acquire mode relies on casuality
    - partial ordering of antecedence
    - communication across threads

Use all three of these modes in order to create custom protocols

cache invalidation is the hardest thing in computer science

Commutativity, Coherence, Casuality, Concensus

java.util.concurrent solves a lot of the stuff for us

# Locks

Used in "synchronized" blocks

mutex locks maintain a total ordering of locked regions

Read - Acquire mode used for these