# asyncio

Created: Dec 2, 2020 10:34 PM
Reviewed: No
Type: Python

Asyncio: a library used to handle asynchronous requests and coordinate multiple servers at once

More broadly, these notes are on

# Asynchronous Programming in Python

### Yield

```python
def generator():
	yield 1
	yield 2
	yield 3

for i in generator():
	print(i)

> 1
> 2
> 3
```

- Like a return statement, but able to resume execution afterwards
- able to "yield" things out of the function incrementally, rather than just returning everything in a list at the end
- useful when you don't want to store values in memory together

Check it out! This is a great way to implement a "range" statement. Consider the following two range functions

```python
def eager_range(end):
	sequence = []
	index = 0
	while index < end:
		sequence.append(index)
		index += 1
	return sequence

def lazy_range(end):
	index = 0
	while index < end:
		yield index
		index += 1
```

- eager_range collates all the numbers into a data structure. This can be useful, but if you're iterating over 1,000,000 numbers, you need space for 1,000,000 ints
- lazy_range yields numbers one at a time. This means that you can iterate over 1,000,000 ints and only ever need to store one at a time. Returning to execution is powerful!

# Concurrency, Parallelism, Asyncio

- **parallelism:** performing multiple operations at the same time
- **multiprocessing:** means to effect parallelism → spread tasks over multiple CPUs
    - better for CPU bound tasks: for loops, math operations
- **concurrency:** multiple tasks have the ability to overlap and run
    - more broad than parallelism
- **threading:** concurrent execution model → multiple threads take turns executing tasks
    - better for IO bound tasks, which have to wait for an input/output to complete
- **asyncio**
    - asynchronous IO, enabled through asyncio package
        - **asynchronous:** meaning routines that can "pause" while waiting on a result and let other routines run in the meantime
        - facilitates concurrent execution, gives the feel of concurrency
    - async and await language keywords
    - single threaded, single process, design
    - **cooperative multitasking**
        - feeling of concurrency despite using a single thread
    - style of concurrent programming that is not parallelism
- **coroutines:** functions whose execution you can pause (similar to generators)

![[asyncio/Untitled.png]]

# Async IO

- takes long waiting periods in which functions would be blocked, and allows other functions to run during that time
- more efficient, cuts down on time
- [https://asyncio.readthedocs.io/en/latest/performance.html](https://asyncio.readthedocs.io/en/latest/performance.html)

![[asyncio/Untitled 1.png]]

### async and await

- **coroutine:** specialized version of Python generator function
    - function that can suspend its execution before reaching return
- *asynchronous version*

![[asyncio/Untitled 2.png]]

- *outputs*
    - one, one, one, two, two, two
    - the other calls to count execute WHILE the first one does
- *synchronous version*

    ![[asyncio/Untitled 3.png]]

    - *outputs*
        - one, two, one, two, one, two
        - each function executes before the next is called

```python
async def say(what,when):
	await asyncio.sleep(when)
	print(what)

loop = asyncio.get_event_loop()
loop.create_task(say('hello!',2))
loop.create_task(say('goodbye!',1))

loop.run_until_complete() #also possible to use loop.run_forever() here
loop.close()
```

Output:

```python
> goodbye!
> hello!
```

- notice that "goodbye" prints first, because there was a shorter wait time specified

# rules of async io

- keyword "await" passes function control back to the event loop, suspending execution of the surrounding coroutine
- "async def" introduces either a native coroutine or an asynchronous generator
    - may use await, return, yield, all are optional
    - function: all or nothing, when it's called, its runnin, can't stop it
    - generator:
- to call a coroutine function (like one declared w "async def") you must await to get the results
- "async def" cannot use "yield from" → error
- if you use "async def" and "yield", you create a async generator
- awaitable if the object is a coroutine or an object defining an "._await_()" method that returns an iterator
- native coroutines are preferred over generators for the purpose of being explicit

# when is async io the right choice?

- async vs multi processing
    - can be used together
    - if you have multiple uniform CPU bound tasks, you should use multiprocessing
- async vs threading
    - more direct comparison
    - threading can seem easy to implement but lead to bugs that are impossible to trace due to memory usage and race conditions
    - threads are a system resource with finite availability, so creating thousands of threads is not feasible
    - but creating thousands of async IO tasks will work
- async io's time to shine
    - tasks where otherwise, you would have a lot of blocking time
    - network IO, server or client side
    - serverless designs, like a group chatroom
    - read/write operations where you have a "fire and forget" style
        - not really worrying about holding a lock on reading or writing
    - cons:
        - await has to have very specific objects and functions
    - there are also other libraries that do what asyncio does, bu with different APIs and different approaches
        - curio
        - trio

### open_connection

```python

```

### start_server

Opens a socket on the assigned port.

```python
coroutine asyncio.start_server(client_connected_cb, host=None, port=None, *, 
	loop=None, limit=None, family=socket.AF_UNSPEC, flags=socket.AI_PASSIVE, 
	sock=None, backlog=100, ssl=None, reuse_address=None, reuse_port=None, 
	ssl_handshake_timeout=None, start_serving=True)¶
```

host is the IP

port is the Port

client_connected_cb is a function which is automatically called whenever a client connects to the given port.

# Usage with aiohttp

```python
import asyncio
import aiohttp

async def fetch_page(session, url):
    with aiohttp.Timeout(10):
        async with session.get(url) as response:
            assert response.status == 200
            return await response.read()

loop = asyncio.get_event_loop()
with aiohttp.ClientSession(loop=loop) as session:
    content = loop.run_until_complete(
        fetch_page(session, 'http://python.org'))
    print(content)
loop.close()
```

# python vs java

### memory management

- Java
    - garbage collected
    - essential for security
    - runs mark-and-sweep algorithm
        - traverse all objects, mark everything found as alive
        - all the heap memory not occupied by marked objects is marked as free
    - not as time consuming as python, don't have to constantly mark things w their reference counts
- Python
    - CPYthon manages memory using reference counting and mark-and-sweep garbage collection
        - reference counting ensures prompt deletion of objects when reference count = 0
        - each time an object is referenced and dereferenced, the interpreter / VM must check if the count = 0
        - time consuming
        - unreliable because can't access cyclical reference issues (cyclic data structure is when its references form a loop → an object can be reached by following references from itself)

[https://www.memorymanagement.org/mmref/lang.html](https://www.memorymanagement.org/mmref/lang.html)

[https://rushter.com/blog/python-garbage-collector/](https://rushter.com/blog/python-garbage-collector/)

[https://www.dynatrace.com/resources/ebooks/javabook/how-garbage-collection-works/#:~:text=As long as an object,and reclaims the unused memory](https://www.dynatrace.com/resources/ebooks/javabook/how-garbage-collection-works/#:~:text=As%20long%20as%20an%20object,and%20reclaims%20the%20unused%20memory)

[https://www.quora.com/What-are-the-differences-between-Python-and-Java-memory-management](https://www.quora.com/What-are-the-differences-between-Python-and-Java-memory-management)

### type checking

- java: statically typed
    - type checking at compile time
    - java var name and type declared before using it
    - object does not equal the type it is assigned = error
    - java container objects (lists, etc) can only have generic type objects
    - vulnerable to small coding errors, eg semicolons
- python: dynamically typed
    - type checking deferred until runtime
    - don't need to declare type when declaring the variable
    - variable can be reassigned to object of different type
    - lists and dictionaries can contain objects of any time
    - makes the syntax easier to use
    - type errors are harder to detect in code

[https://www.snaplogic.com/glossary/python-vs-java#:~:text=The most significant difference between,checking is deferred until runtime.&text=Also%2C a Python variable name,object of a different type](https://www.snaplogic.com/glossary/python-vs-java#:~:text=The%20most%20significant%20difference%20between,checking%20is%20deferred%20until%20runtime.&text=Also%2C%20a%20Python%20variable%20name,object%20of%20a%20different%20type)

### multi-threading

- java:
    - JVM supports multithreading on multiple cores
    - true parallel execution
    - max performance: c * n threads, where c is a number under 5 and n is the number of cores
    - if there are too many threads relative to # cores, context switch kicks in, which decreases performance
    - large number of threads makes sense when the job type is IO related, like a server
    - JVM supports fine grained locks for each resource
    - so we can use "synchronized" "final" "volatile" to control shared object
        - "synchronized": obtain the lock of the object to access the object
        - "final": immutable, read only, so any thread can access
        - "volatile": value change will be visible to other threads
- python:
    - CPython is C implementation of python
    - JPython is Java implementation
    - lol isn't that funny cpython and jpython
    - Cpython is not thread safe, does not support fine grained locking like JVM
    - instead, has GIL: global interpreter lock
        - any thread must hold the GIL to access memory
    - parallel execution is context switch
    - multi-threading only suggested for IO related joobs
    - python provides multiprocessing libraries for true parallel execution

    [https://liyanxu.blog/2019/04/19/summary-of-multithreading-and-multiprocessing-in-java-python/](https://liyanxu.blog/2019/04/19/summary-of-multithreading-and-multiprocessing-in-java-python/)

# asyncio vs node js

- Node js is a runtime environment for JavaScript
- both python and javascript can't execute code in parallel
    - single threaded
- but you can still do STUFF in parallel
    - async / await stuff
- so as we know python has async await
- in JS, you use promises
    - but you still have async / await just built on promises and callbacks instead of coroutines
    - code looks pretty similar in both cases
- python's equivalent of promises are awaitables, which can coroutines, async Tasks, of Futures
- node js is faster than python
- node.js is a event driven environment, enables async input
- python needs asyncio to do this
- so overall pretty similar

[https://medium.com/@interfacer/intro-to-async-concurrency-in-python-and-node-js-69315b1e3e36](https://medium.com/@interfacer/intro-to-async-concurrency-in-python-and-node-js-69315b1e3e36)

[https://medium.com/@interfacer/intro-to-async-concurrency-in-python-and-node-js-69315b1e3e36](https://medium.com/@interfacer/intro-to-async-concurrency-in-python-and-node-js-69315b1e3e36)