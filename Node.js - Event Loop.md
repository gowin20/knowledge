#nodejs #backend #web 
Sources: 
Overview: https://nodejs.dev/learn/the-nodejs-event-loop
Node YT: https://www.youtube.com/watch?v=zphcsoSJMvM
this Ahmad guy: https://www.youtube.com/watch?v=y3V0ChRs-9Y

---
# Node Event Loop
This is the core of why Node.js is asynchronous with non-blocking I/O, which is why it is so successful.


- Runs code in JS on a single thread, simplifying how you program


All javascript executed by Node.js is run in a single thread, but the event loop itself (which is written in C++) is multi-threaded!



---


# Ahmad's Take
Understanding the Node Event Loop
"Process" of events
100ft overview of everything

enter REPL loop: type "node"
typeof window -- on server, undefined. this is major diff between V8 engine on server vs in browser
on local: typeof global -- object

"node" is **a c++ library that includes the JS V8 Engine**


event loop allows non-blocking IO operations even though JS is inherently single-threaded
- does so by offloading operations to the system kernel whenever it can :) bascially gets help from the OS whenever possible

JS is single-threaded but the event loop is not!

"non-blocking" because it doesn't block the single JS thread


When an operation is complete, the kernel tells Node and it adds the callback to the poll queue.


TODO Event Loop visual: find one

bert belder talk on event loop

event loop is really a single loop that keeps going while refs > 0

use EventEmitter to define your own eventemitter class

# nodejs.dev's take

most browsers have an event loop for every browser tab

write code that's built for single event loop + avoid blocking it. the rest of it is taken care of via Node and browsers and kernels

Blocking event loop:
- almost all primitives in JS are non-blocking and so are network requests, filesystem ops, etc
- JS is based on callbacks, [[JS - Promise|promises]], [[JS - async and await|async]]/await for this reason



**call stack: another component of node's architecture**

event loop continuously checks to see what functions are on the call stack, and executes everything on the stack in order
This is similar to the [[call stack]] in other programming as well.


in node: `setTimeout(() => {}, 0)` calls a function, but delays execution of it until after every other function in the current code has been executed.

```js
const bar = () => console.log("bar")

const foo = () => {

 console.log('foo')
 setTimeout(bar, 0)
 console.log("whee")

}
```
output:
```bash
foo
whee
bar
```
this happens due to **the Message Queue** in Node.js. When setTimeout() is called, it adds the provided callback function to the message queue after a set amount of time (in the example above, 0 seconds.)

