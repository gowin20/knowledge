#web #nodejs #backend #async 
source: https://www.youtube.com/watch?v=zphcsoSJMvM
### **Node.js is single [[Threads|threaded]] - except when it's not**

---

# Node's "Single Thread"
All Javascript, V8, and the Node.js [[Node.js - Event Loop|Event Loop]] run in a single thread called **the main thread.** [[Javascript - Overview|JS]] doesn't have access to threads

However Node.js also contains a lot of [[C++]] code (~33% of it), which can use threads

- JS methods called in node that are backed by a C++ method will run in the main thread *if they are synchonous*
- C++-backed **asynchronous methods sometimes don't run in the main thread.**



# Example 1: [[Node.js - Crypto|Crypto]] module
This contains lots of different CPU-intensive methods, both synchronous and asynchronous

Synchronous:
- **[[Node.js - pbkdf2|pbkdf2sync]]** -- hashing method that takes a long time


Runtime for this:
![[Pasted image 20220124163948.png]]

Same code, but using the asynchronous **[[Node.js - pbkdf2|pbkdf2]]** method (exactly the same method, but the asynchronous version):
![[Pasted image 20220124164038.png]]

All we have to do is just write normal code, and Node.js will automatically use C++ methods to compute operations in parallel

**always use asynchronous methods whenever possible!** - this is why.

Now let's run the same code with 4 requests, still run on a dual core processor:
![[Pasted image 20220124164250.png]]
This took longer! That's because the computer this ran on contained a dual core processor, so there is a [[bottleneck]] of only two threads.

This is all generic to all languages :)


Increasing to 6 requests in total, let's look at the trend:
![[Pasted image 20220124164426.png]]

Node doesn't create a new thread for each request!

**Node uses a set amount of threads called the [[Node.js - Thread Pool|Thread Pool]], set to 4 by default**
- Default of 4 is why the first 4 ran first, then last 2 ran later.



# Example 2: [[HTTP|HTTP(S)]] Module

`https.request` allows api requests to be made to retrieve files from websites.

```node
const https = require('https');
const NUM_REQUESTS = X;

for (let i = 0; i < NUM_REQUESTS; ++i) {
	https.request('https://nebri.us/static/me.jpg', (res) => {
		res.on('data', () => {});
		res.on('end', () => {});
	}).end();
}
```

Time for 2 requests:
![[Pasted image 20220124165007.png]]
Time for 4 requests:
![[Pasted image 20220124165019.png]]

Unlike with crypto the total time didn't increase! That's because **for file downloads, the [[bottleneck]] is the network**, rather than the computation :)


This code isn't subject to thread pool limitations, because Node.js uses [[async|asynchronous]] C++ primitives whenever possible in C++-backed methods.

