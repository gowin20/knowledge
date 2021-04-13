# Memory Management

Created: Dec 16, 2020 1:39 AM
Reviewed: No
Type: Memory, Textbook

### introduction

- lots of different data must be stored in memory
- most modern languages require a complex and hidden library of runtime support code to perform the chores of dynamic memory allocation

### memory model using java arrays

- assumed that the operating system grants each running program one or more fixed sized regions of memory to use for its dynamic allocation
- these regions will be treated as int [] arrays
- memory management techniques implemented in the following notes will be Java classes of this form:

```java
public class MemoryManager {
	private int [] memory;
	/**
	* MemoryManager constructor.
	* @param initialMemory the int[] of memory tto manage
	*/
	public MemoryManager (int [] initialMemory) {
		memory = initialMemory;
	}
}
```

- initial memory array is an argument to the constructor
- memory manager provides methods that can be called by running the program to allocate and deallocate blocks of addresses in the memory array
- you would probably not implement memory management for a real language system this way, its just presented like this is to show some of the algorithms

### stacks

- activation records form a stack at runtime
- they are pushed on call and popped oon return
- memory manager can take advantage of the stack order
    - the first activation record allocated will be the last one deallocated
- empty memory array, of eight words

![[Memory Management/Untitled.png]]

- suppose the program now needs an activation record of three words
- program will call m.push(3), telling stack manager how many words are needed
    - method will return the address 5, the first address in the block of 3 words allocated to the program

![[Memory Management/Untitled 1.png]]

- activation record takes spaces 5, 6, 7
- space 4 is needed to store the previous value of the "top" of the stack
- suppose now we need two more words:

![[Memory Management/Untitled 2.png]]

- same thing as before
- when the function using the second activation record is finished, it'll call m.pop() to deallocate
- m.pop() will get the value at memory[top], which is the previous top value
    - for ex, it'll get memory[1], see that that's 4, and know that the next stuff starts there
- this general "bump the pointer" technique is very common
    - just making simple adjustments to top address
    - very efficient
    - but this depends on the fact that allocation and deallocation are restricted to stack order

### heaps

- many languages have constructs that require unordered runtime memory allocations
    - C has malloc and free
    - C++ use new and delete
- a **heap** is a pool of blocks of memory, with an interface for unordered runtime memory allocation and deallocation

### first fit mechanism

- heap manager maintains a linked list of free blocks, initially containing one big block
- to allocate a block, the heap manager searches for the free list for the first sufficiently large free block. if there is extra space, the block is split and the unused portion is returned to the free list
- to free a block, the heap manager returns it to the front of the free list
- example:

```java
p1 = m.allocate(4)
p2 = m.allocate(2)
m.deallocate(p1)
p3 = m.allocate(1)
```

- initial state, completely empty heap: one big free block

![[Memory Management/Untitled 3.png]]

- after the first allocation
    - heap manager finds that the first and only block is more than large enough
    - allocates 5 words → the requested 4 plus 1 more and returns the remainder to the free list
    - returns address 1, the first of the 4 requested words

![[Memory Management/Untitled 4.png]]

- second allocation:
    - heap manager finds that the first and only free block is more than large enough
    - allocates 3 words (2 + 1 more) and returns the remainder
    - address returned is 6, the first of the 2 requested words

![[Memory Management/Untitled 5.png]]

- next allocation, is a deallocation of p1
    - deallocates p1, returns it to the front of the free list

![[Memory Management/Untitled 6.png]]

- so now the free list has two blocks, one of five words and one of two words
- program makes its final allocation m.allocate(1)
- heap manager finds the 5 word block at head of free list, allocates 2 words of this and returns the three to the free list

### coalescing free blocks

- say you have two free blocks, one with 3 words of memory, one with 4, right next to each other
- if you need a 6 word. memory allocation, you can't, because you don't have a block that big
- but you have that much free memory, it's just not joined
- so it's time to coalesce the freek blocks
- modify the deallocate method to make it coalesce adjacent free blocks
- the method will maintain the free list sorted in increasing order of address
- if it finds the right insertion point in the list, then it inserts it and merges it with the previous free and following free block if they are adjacent

### quick lists

- common way to improve performance of a heap manager is to maintain separate free lists for the popular block sizes
- on each of these lists, all the blocks are the same size
- allocate method can just quickly check the list of the size it needs, if there is a list for the requested size and a free block on the list, just return it
- if these block sizes are frequently allocated and deallocated, there will be significant performance improvement
- no coalescing though, so that brings up the same problem as before

### fragmentation

- heap manager cannot combine non adjacent free blocks
- this leads to a lo of fragmentation, where you can have enough space but still can't allocate the memory

### other heap mechanisms

- heap manager must decide on **placement** for every block allocated
    - allocator has many places it can put the word, first fit algorithm is just one choice
- heap manager usually implements block **splitting**
    - one possibility is allocate exactly what is requested and free the rest
    - but if the total block size is very similiar to the requested size, might be more efficient to just not free anything
- heap manager also does some **coalescing**
    - we saw this already

### current heap links (i don't understand this section)

- **current heap link:** memory location where a value is stored that the running program will use as a heap address
- general procedure heap managers follow to trace current heap links:
    - start with the root set, the set of all memory locations of all the running program's variables. omit all those whose values obviously cannot be used as heap addresses
    - for each memory location in the set, look at the allocated block it points to and add all memory locations within that block

### heap compaction

- using heap links, heap manager can move allocated blocks around without disturbing the running program
    - copies the block to a new location, updates all the current heap links to the old block, and makes them point to the new location
- heap managers use this capability to perform **heap compaction**
    - move all the allocated blocks together at one end of the heap, leaving all free space in a single free block at the other end
    - stops fragmentation
    - but is expensive
    - moving allocated blocks is safe only if the current heap links have no errors

### garbage collection

- some languages require garbage collection
    - for ex, Java, since there is a "new" word but no deallocation
    - some, like C, don't since you can malloc and free
- programmers who like garbage collection feel that the time it saves not having to worry about deallocation is worth the extra processor time

```pascal
Procedure Leak;
	type
		p: ^Integer;
	begin
		new(p)
	end;
```

- this has a **memory** **leak**
- allocates a heap block and then does not deallocate it
- problem obviously, because if this were a large program it would use more and more unnecessary memory and run out of space
- some language systems eliminate this problem by having a automatic **garbage collector**
    - heap manager finds the allocated blocks that the running program is no longer using reclaims them automatically
- three basic techniques for garbage collector: mark and sweep, copying, and reference-counting
- *mark-and-sweep*
    - mark: garbage collector traces current heap links and marks the allocated blocks that are the target of those links
    - sweep: garbage collector makes a pass over the heap and finds all blocks that did not get marked and adds them to the free list
    - mark and sweep collectors do not move allocated blocks
    - heap remains fragmented
    - not sensitive to inclusion errors
- *copying*
    - heap manager uses one of half of its available memory at a time
    - when that half is full, it copies all the non garbage blocks into the other half
    - in the new half, all the allocated blocks are together and all the free space is a single free block
    - then resumes normal allocation in the new half
    - switches back to the first half once new half is full, etc
    - move allocated blocks, so sensitive to inclusion errors
- *reference counting*
    - does not need to trace current heap links
    - every allocated heap block has a counter that keeps track of how many copies of its address there are
    - when the counter becomes zero, that block is known to be garbage and can be freed
    - poor performance, since maintaining this counters adds lots of overhead
    - also, cannot collect cycles of garbate

    ![[Memory Management/Untitled 7.png]]

    - if we have something like above, the variable circle is a reference to one of three objects linked to each other
    - if the running program assigns circle to be none, then we have this situation:

    ![[Memory Management/Untitled 8.png]]

    - none of the heap blocks have a reference count of 0, so they are all allocated, but cannot be reached anymore
    - reference counting garbage collectors are rare bc of high overhead and difficulties with cycles
- *other kinds of collectors*
    - generational collectors: divides collection of allocated blocks according to age and garbage collects mostly within the younger blocks
    - incremental collectors: recover a little garbage at a time, while the program is running, instead of doing it all at once