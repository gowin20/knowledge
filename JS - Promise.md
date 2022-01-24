#js #web
Source: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise


---
# Promise object

an object that represents the eventual terminus of an async operation AND its value

Used in [[JS - async and await|JS asynchronous programming]]

Value isn't known when the promise is created! Promises allow asynchronous methods to return values like synchronous stuff does: return a promise to supply a value at some point

Three states:
1. Pending, initial state
2. Fulfilled, operation completed check
3. Rejected, operation failed error
 
![](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/promises.png)