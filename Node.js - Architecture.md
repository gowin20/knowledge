#nodejs #backend #web
Source: https://dev.to/cassiocappellari/basic-concepts-of-node-js-pch

---
# Node.js Architecture: 3 parts

### 1. Event Queue
When a client's request (seen as an event) reaches the server, it slots into the Event Queue
- Waiting room for events that need to be processed

### 2. [[Node.js - Event Loop|Event Loop]]
**This is the single thread platform**, the primary component of Node. When an event is ready to be processed, it will enter the event loop. The event loop sees events as blocking operations and delegates them out of necessecity to keep the server running. It delegates requests (blocking operations) to the Thread Pool and then reads in another event.
- Runs the V8 Engine, which is Javascript
1. Take request from queue
2. Delegate request to thread pool for processing

### 3. Thread Pool
This is the multi-thread platform that processes events asynchronously. When an event is completed its callback function it put in the event queue. When Node's execution stack is empty the Thread Pool takes 
- runs the **libuv** library
- Has C++ at its core

![[Pasted image 20220123142148.png]]


#### [[Node.js - my summary]]
