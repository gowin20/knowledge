#web #backend #async
sources:
https://dev.to/cassiocappellari/basic-concepts-of-node-js-pch


---
# What is Node.js?

JS runtime environment for server-side programming -- back end.
- Executes JS code on a server, not on the local web browser
- Built to handle intense asynchronous input and output

Imagine a popular web application that sends hundreds of requests per seconds to a server, but the server can only process one request at a time. A huge backlog would quickly accumulate and cause performance problems on the website - all the users would be stuck waiting!

Node.js was specifically designed to prevent this by handling asynchronous input + output.
- [[Javascript - Overview|Javascript]] is the best language for this

- Uses the same JS compiler server-side as web browsers do, which makes it fast


- single thread characteristics w/ multithread platform running in the background

# Important to know

```diff
+ Handles high throughput of I/O very well through non-blocking methods
+ Fast: uses the same JS compiler server-side as web browsers do
+ Uses a "single thread" to program, delegates async operations to background threads
+ control flow driven by event listeners
```


**Node.js is Single Threaded, except when it's not.**

(See [[Node.js - Threads]])

Single Thread:
- Main code runs in a single thread that delegates asynchronous operations to a multi-thread platform, making it lightweight + easy to use
- Compare to python's async library


Node.js is Event Driven:
- when a node application starts, event listener called the **Event Loop** begins. When an event occurs, functions may execute.


To fully understand Node.js, we must understand its [[Node.js - Architecture|architecture]]