---
layout: default
title: Asyncrhonous Programming in JS
parent: 2020
nav_order: 10
---

# Asynchronous Programming

> _Asynchrony, in computer programming, refers to the occurrence of events independent of the main program flow and ways to deal with such events. These may be "outside" events such as the arrival of signals, or actions instigated by a program that take place concurrently with program execution, without the program blocking to wait for results. Asynchronous input/output is an example of the latter case of asynchrony, and lets programs issue commands to storage or network devices that service these requests while the processor continues executing the program. Doing so provides a degree of parallelism._ - **Wikipedia**

# JavaScript is single-threaded

JavaScript runtime is commonly referred to be 'single-threaded', which brings about a lot of confusion around how it handles concurrency and asncyhrony. What it really means is that there's only one call stack where the function is excecuted, but long running processes such as API calls, I/O events and timers are 'offloaded' to the Web API, which handles thse tasks in the background and push the callback functions into the message queue of the JavaScript runtime.

# Styles of Asynchronous Programming in JavaScript

There are 3 styles of Asynchronous programming for JavaScript:

1. Callback
2. Promise
3. async / await

## Callback

A pattern where a function accepts other 'callback' functions as arguments, which is run after some asynchronous operation has completed or failed.

```js
const fs = require("fs");

fs.readFile("/Users/joe/test.txt", "utf8", (err, data) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(data);
});
```

The callback pattern is commonly seen in the older APIs and developers won't typically be writing this pattern in their own code, as it is considered to be somewhat outdated and the Promise pattern is preferred.

Chaining multiple asynchronous operations via callback styled API can often lead to what is known as a 'callback hell'.

```js
fs.readdir(source, function (err, files) {
  if (err) {
    console.log("Error finding files: " + err);
  } else {
    files.forEach(function (filename, fileIndex) {
      console.log(filename);
      gm(source + filename).size(function (err, values) {
        if (err) {
          console.log("Error identifying file size: " + err);
        } else {
          console.log(filename + " : " + values);
          aspect = values.width / values.height;
          widths.forEach(
            function (width, widthIndex) {
              height = Math.round(width / aspect);
              console.log(
                "resizing " + filename + "to " + height + "x" + height
              );
              this.resize(width, height).write(
                dest + "w" + width + "_" + filename,
                function (err) {
                  if (err) console.log("Error writing file: " + err);
                }
              );
            }.bind(this)
          );
        }
      });
    });
  }
});
```

## Promise

Promise is an object representing the eventual completion or failure of an asynchronous operation.
Essentially, you 'attach' callbacks to Promise instead of passing callbacks into a function, which allows more easily readable code especially when trying to chain multiple asynchronous operations.

### 3 States of Promise

A `Promise` is in one of these states:

- 🤚🏻 Pending: initial state, neither fulfilled nor rejected.
- 🙆‍♂️ Fulfilled: meaning that the operation was completed successfully.
- 💔 Rejected: meaning that the operation failed.

A Promise is said to be 'settled' if it's either fulfilled or rejected.

### Error propagation

Unlike callback pattern where you'd have to pass in `onError` callback to each function when chaining multipe operations, errors are propagated down the Promise chain for `.catch` or `onRejected` handler.

```js
doSomething()
  .then((result) => doSomethingElse(result))
  .then((newResult) => doThirdThing(newResult))
  .then((finalResult) => console.log(`Got the final result: ${finalResult}`))
  .catch(failureCallback); // any error in the Promise chain preceding the catch, will be handled by the failureCallback
```

### Running multiple operations concurrently

`Promise.all()` takes an interable of Promises as an input, and returns a single Promise that resolves to an array of the results.

```js
const p1 = Promise.resolve(3);
const p2 = 1337;
const p3 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("foo");
  }, 100);
});

Promise.all([p1, p2, p3]).then((values) => {
  console.log(values); // [3, 1337, "foo"]
});
```

Keep in mind that a rejection in `any` of the input Promises will result in the Promise from `Promise.all()` itself to be rejected. Therefore, you'll need to handle the rejection by chaining the input Promises with `.catch()` or use `Promise.allSettled()` instead, if this fail-fast behaviour is not favourable.

## async / await

`async` and `await` are syntactic sugar for working with promises, and allow writing asynchronous, promise-based code to be read like synchronous code.

- The `await` keyword is only permitted in a function declared with the `async` keyword.
  - However, `await` can be used on its own with [JavaScrpt modules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)
- An async function always returns a Promise. If the return value of an async function is not explicitly a Promise, it will be implicitly wrapped in a Promise.

```js
function getProcessedData(url) {
  return downloadData(url) // returns a promise
    .catch((e) => {
      return downloadFallbackData(url); // returns a promise
    })
    .then((v) => {
      return processDataInWorker(v); // returns a promise
    });
}
```

is equivalent to

```js
async function getProcessedData(url) {
  let v;
  try {
    v = await downloadData(url);
  } catch (e) {
    v = await downloadFallbackData(url);
  }
  return processDataInWorker(v);
}
```
