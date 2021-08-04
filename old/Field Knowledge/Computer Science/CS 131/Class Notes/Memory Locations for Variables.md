# Memory Locations for Variables

Created: Dec 16, 2020 1:38 AM
Reviewed: No
Type: Memory, Textbook

### Intro

- imperative language: obvious connection between variables and memory locations → value is assigned to a variable, it is stored somewhere
    - C makes this explicit, for ex. &c gives you the memory location of c
- purely functional language: variables are more hidden since there isn't assignment

### Activation Specific Variables

- in most languages, you can declare a variable that is bound to a memory location but only for a particular execution of a function
    - for each function call, the values of variables declared in the function will be different
    - in ML programs, the variables may or may not be bound to the same memory locations on later calls, there's no way to tell
- function lifetimes
    - a function is called, performs computation, returns to caller
    - lifetime of this one execution of the function from call to return is called **activation** of the function
    - variables iin each function are **activation specific**
    - in most languages, local variables are activation specific
    - also, if you have "ifs" or "while" etc, you could have a variable that only matters if that specific function block is called
        - a language system may then only bind the variable if the block is entered
        - the variable is still activation specific, but its specific to activation of a block, not the function

        ![[old/Field Knowledge/Computer Science/CS 131/Class Notes/Memory Locations for Variables/Untitled.png]]

        - here, the block w "b" is not always executed
        - variable b is activation specific to an activation of the let block

### Other Variables

- most imperative languages have a way to declare a variable that is bound to one memory location for the entire runtime
- for ex: in C, any variable declared outside a function has this kind of lifetime
- static allocation iis the only way to handle these long lifetime variables, so they are called **static variables**
- **IMPORTANT:** local variables does not automatically equal activation specific lifetime!!!!!
    - C allows the definition of static variables with lots of different scopes

    ```c
    int nextcount() {
    	static int count = 0;
    	count = count + 1;
    	return count;
    }
    ```

    - even though count is a local var, it is still static and has a static lifetime
- other than activation specific variables and static variables, there are other kinds
    - for OO languages like Java, you can have variables whose lifetimes go w an object's lifetime
    - another kind are **persistent variables:** variables with super long lifetimes that extend across multiple executions of the program
    - most variables are activation specific

### Activation Records

Another name for a Stack Frame

3 parts:

- locals to the callee
- return address of the caller
- parameters of the callee

functions have many different activations during execution 

- multiple activations can be alive at the same time, when one function calls another
    - they're not executing at the same time, but one is nested in the other so activation specific variables are preserved across the return
- additional activation specific data must be stored in memory
    - **return address:** location within the calling function's code where execution should resume when the function returns
    - we learned about this in 33! praise tony
    - **activation record:** language implementations usually gather all the activation specific variables and other activation specific data together into this one block of memory
- when a block within a function is stepped into
    - most language systems do not create a complete new activation record for this
    - space for the variables on each block can often be preallocated within the activation record
        - this assumes that the amount of memory required for each variable is known when the function is entered
        - if this is not true, like for example the language allows a local variable in a block to be an array whose size was computed just before the block was entered, this has to be handled in some other way. one option is to extend the activation record when the block is entered and then shrink

### Static Allocation of Activation Records

- way to handle activation records: allocate one for every function, *statically*
- meaning allocate one for each function before the program begins running
- has efficiency advantages
- older dialects of Fortran and Cobol used this system

```fortran
Function AVG (ARR, N)
DIMENSION ARR(N)
SUM = 0.0
DO 100 I = 1, N
	SUM = SUM + ARR(I)
100 CONTINUE
AVG = SUM / FLOAT(N)
RETURN 
END
```

- for this function, the activation record would look something like this:

    ![[old/Field Knowledge/Computer Science/CS 131/Class Notes/Memory Locations for Variables/Untitled 1.png]]

    - order of the components of the activation record depends on the implementation
    - can now allocate this block statically
    - how are memory locations determined?
        - in static allocation, every activation of a given function uses the same block of memory for its activation specific data
        - so the system will fail if there is ever more than one activation of a function alive at the same time → eg, recursion
            - the two or more activations will overwrite each others variables if they share a single record
            - before, Fortran and Cobol just made recursion illegal
            - but now you can't just go around making things illegal
            - plus recursion is so cool
            - even if its confusing
            - but its so useful
            - so back to the drawing board on allocation i guess
            - well.. not for long → read on!

### Dynamic Stacks of Activation Records

- languages that support recursion need to be able to allocate a new activation record for each activation
- activation records are pushed on call and popped on return
- activation record forms a stack at runtime
- such a popular system that activation records are just known as **stack frames**
    - wow literally who knew! it's like we learned literally all of this in 33
- when a function returns here, there are two important addresses:
    - the address of the machine code to return to in the calling function
    - the address of the activation record that the function was using
    - activation records are dynamically allocated and their addresses are not know at compile time anymore, so now we have too keep track of this info

```c
// example recursive factorial function 
int fact (int n) {
	int result;
	if (n < 2) result = 1;
	else result = n * fact(n - 1);
	return result;
}
```

- when fact(3) is called

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/Memory Locations for Variables/Untitled 2.png]]

- so you have the parameter n, an its value
- the return address, where to resume in caller's code
- the previous activation record which has the address of the caller's activation record
- and the result, which is unknown rn
- next, function is recursively called with fact(2)

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/Memory Locations for Variables/Untitled 3.png]]

- so now we have everything from before, w n = 3
- and then we have everything again, for n = 2
    - this time, the "previous activation record" for n = 2 is the activation record of n = 3
    - n = 3 activation record is active, but suspended until n = 2 returns
- recursive call with n = 1

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/Memory Locations for Variables/Untitled 4.png]]

- same thing as before
- result now has a value, since in the code it says that if n < 2, result = 1
- when the third activation returns to the second, the second activation gets value 1 for fact(1), multiplies by 2, gets 2 for result
    - then pop the third record off the stack
- then again, fact(3) gets the return value of 2 from fact(2), multiples that by 3, gets 6
    - pop the second record off the stack
- in many languages, when something gets popped of the stack, the memory is deallocated and its memory space can be used

### Another Dynamic Example, this one in ML (GROSS)

```ocaml
fun halve nil = (nil, nil)
| halve [a] = ([a], nil)
| halve (a::b::cs) = 
	let 
		val (x,y) = halve cs
	in 
		{a::x, b::y}
	end;
```

- takes a list parameter and returns a pair of lists, each containing half the elements of the original
- trace this with the list [1, 2, 3, 4]
- first activation record, when the function is called:

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/Memory Locations for Variables/Untitled 5.png]]

- the recursive call is then made to cs, with is [3, 4]
- this is the activation record for that:

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/Memory Locations for Variables/Untitled 6.png]]

- next, recursive call with cs, which is empty
- since a is the empty list, the first alternative for halve is chosen, since the parameter is the empty list
- so just returns the empty list

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/Memory Locations for Variables/Untitled 7.png]]

- when the third activation returns to the second, the second activation matches (x, y) with ([], []), and constructs return value
- second activation returns to the first, same thing happens
- matches (x, y) with (3, 4)
- constructs return value → ([1, 3], [2, 4])

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/Memory Locations for Variables/Untitled 8.png]]

### Nested Function Definitions

- the system we just learned about for allocation si not enough for languages that allow nested function definitions with non local references
- lots of languages have an intermediate kind of reference: a reference to a variable that is not local but also not static
    - means, a reference to a variable that is in another function's activation record

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/Memory Locations for Variables/Untitled 9.png]]

- example: this is the ML version of quicksort
- nested function split
- the problem is that the variable pivot is used in split, but is local to quicksort, not to split
- when the split function is executing, it's not going to have the pivot variable anywhere
- we need to keep track of the activation record for the outer function, ie, the function that this function is nested in
    - called **nesting link**

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/Memory Locations for Variables/Untitled 10.png]]

- all the nesting links point to the same quicksort function
- if you have multiple nested functions, use nesting links that number of times

![[old/Field Knowledge/Computer Science/CS 131/Class Notes/Memory Locations for Variables/Untitled 11.png]]

- ordinary local references: f1 to v1, f2 to v2
    - handled in regular activation record
- one nesting level away: f2 to v1, etc
    - handled using a nesting link
- two nesting levels away: f3 to v1
    - the nesting link for f3 is the address of activation record for f2, the nesting link from f2 is address of activation record for f1, containing v1
- nesting links is not the only solution
    - can also keep all the nesting links in a single static array called a **display**
    - can also pass each function all the variables it needs as hidden parameters, called **lambda lifting**

### functions as parameters

```ocaml
fun addXToAll (x, theList) = 
	let 
		fun addX y = 
			y + x;
		in 
			map addX theList
		end;
```

- addX function has a non local reference to x
- the calls function map with the function addX as a parameter
- what is in memory for addXToAll before map is called:

    ![[old/Field Knowledge/Computer Science/CS 131/Class Notes/Memory Locations for Variables/Untitled 12.png]]

    - function values in ML include the implementation and the nesting link to use with it
    - here, the function is represented as an oval, with those two parts

### long lived functions

- some languages allow function values to persist after the function that has created them has returned
- to handle this situation, languages cannot just deallocate an activation record cuz you might need the variable again
- memory space can only be reused when the program no longer has any active links to it
- this requires **garbage collection** DUN DUN DUN .... foreshadowing