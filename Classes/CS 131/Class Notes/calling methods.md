# calling methods

Created: Dec 18, 2020 1:31 PM
Reviewed: No
Type: Memory

```c
func f(a) {
	print(a)
	print(a)
}
func g() {
	print("g called")
	return 1
}

f(g())

//Call by Value:
inner g() called first and evaluated. then, value passed to F
/*output:
g called
1
1
*/

//call by name:
g() call not evaluated until necessary in the code. 
passed to F and evaled in the print statement
/*output:
g called
1
g called
1
*/

//call by need:
g() call not evaluated until necessary. 
Passed to f and evaled in the FIRST print statement. 
afterwards, the return value is cached
this means we don't evaluate g() again in the second print - just use cached val

/*output: (same as call by value)
g called
1
1
*/
```

# Call by Name

arguments are not evaluated before the function is called - rather, they are evaluated whenever they appear in the function

# Call by Need

Commonly implemented through lazy evaluation

if an argument is evaluated, it's stored for future use (cache the result)

don't look at any values of variables until you absolutely need to

# Call by Value

- C++, C, OCaml, Java, Scheme, Python

caller evaluates the argument and passes a copy of the value to the callee

pretty standard, make a copy and modifications only affect the copy

- + simple, easy to understand
- - expensive for large values

# Call by Reference

- C++, C, etc.

Caller evaluates the argument but only stores its address. Passes the address to the callee as a pointer

Callee accesses data by dereferencing pointer on each access

- + inexpensive and efficient
- - aliasing means things get confusing and weird

aliasing: two names for the same variable

C calls by value only

![[calling methods/Untitled.png]]

# Call by Result

- used in Ada

The caller does NOT evaluate the argument at all

the callee determines the argument by assigning to it

then, the callee returns the value by copying it back to the caller

- underlying pointers aren't accessible to the programmer in this method

# Call by Value-Result

call by value + call by result

less efficient without any aliasing problems, safer form of call by reference

1. caller copies values to callee
2. callee computes, returns
3. copies values back from the callee to the caller

# Call by Unification

Perform a pattern match between the caller and callee

this makes the two arguments the "Same", as long as it's possible to do so

Means that you can pass an unknown and hope that it binds to an actual result

if not possible, you get a failure

![[calling methods/Untitled 1.png]]

# answer

![[calling methods/Untitled 2.png]]

```scheme
so what we have here: if count becomes greater than 1 -> infinite loop 

for both call by value and call by need, bar is only going to evaluate once
for call by need, bar is going to be evaluated twice, since the foo is being passed the entire function as the arg
-> so this causes count to equal 2, which equals infinite loop 
```