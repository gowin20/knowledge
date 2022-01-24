#js #web #async
Sources: 
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function

---
# Asynchronous Functions in JS

Declared with the "async" keyword, Asynchronous functions are the only area that the "await" keyword is permitted within.

See [[async]] for a primer on asynchronous programming.

```js
async function name([param[, param[, ...param]]]) {
   statements
}
```
"await" may be used within the body of the function, represented as statements.


### Return Values

All async functions **return a [[JS - Promise|promise]]** that is eventually resolved by the value the function returns.

This means that return values always behave similarly to a function with return value wrapped in a promise.

e.g.
```js
async function foo() {
   return 1
}
```
is pretty much equivalent to
```js
function foo() {
   return Promise.resolve(1)
}
```
(see mozilla source for why they're not *actually* equivalent)

### Await

Await expressions make functions that return promises (async functions) behave as if they're synchronous, by halting execution of the code until the awaited promise is either fulfilled or rejected.

Resolved value of the promise becomes the return value of the await expression!


