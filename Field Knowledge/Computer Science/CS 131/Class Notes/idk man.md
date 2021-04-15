# idk man

Created: Dec 2, 2020 12:35 PM
Reviewed: No

# multi-dimensional arrays

```prolog
T A[L1 .... U1][L2 ... U2] //multi dim array, address is A
```

# storage management of all the stuff you need to execute a function

- execute one call to a function
- **activation record** is technical time
    - contains:
        - local variables for functions
        - parameters
        - return address (is a register)
        - saved registers from caller (eg, stack pointer) or any other registers that you need
        - temporaries used by the function
            - **temporary:** intermediate values you need while evaluating the rest of an expression
    - compilers often cache this stuff into registers → for ex, return address is usually just put into a register, in x86-64, first few args put in registers
    - but let's assume that this does not happen, and everything gets put into memory
    - parts of activation record can be reused

        ```prolog
        int f (int x) 
        {
        	if (x == 0)
        	{
        		do stuff with variable y
        	}
        	else {
        		do stuff w variable z
        	}
        }

        needed for activation record: 
        return address
        x 
        y and z (both share the same space - since only one will ever be used,
        					because of the if statement)
        ```

    ### where are the activation records stored?

    - *static allocation*
        - compiler / linker decides where activation record is
        - advantages
            - very simple
            - optimize access since locations are known statically
        - disadvantages
            - you may use more storage than you need to
            - can't do recursion
    - *stack allocation*
        - function call allocates an activation record
        - function return deallocates activation record
        -