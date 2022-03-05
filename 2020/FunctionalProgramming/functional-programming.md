---
layout: default
title: Functional Programming and Testable Code
parent: 2020
nav_order: 8
---

# Functional Programming and Testable Code
{: .no_toc }
Presented on 26th July 2020 by [Heath](https://github.com/heathryu)

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## What is Functional Programming?
Functional Programming is a paradigm that treats computation as evaluation of mathematical functions and avoids state and mutable data

Put another way, Functional Programming favours use of pure functions and tighly controls side-effects.

### Side-effect
A function is said to have side-effect if it modifies some state variable outside its local environment. There is also a concept of 'side-causes', when the function depends on something that is not observable by the function's parameter such as global variable, the time when the function is executed, etc. The 'side-causes' terminology is not as widely used as side-effect, and people will often refer to both as 'side-effect'.

### Pure Function
A Pure Function is a function that has both of the following characteristics:
1. Returns the same result for the same set of input *every time*
2. Does not have **side-effects** (and **side-causes**).

#### Examples of Pure Functions

```js
function add(a, b) {
  return a + b;
}
```

```js
function formatInput(input) {
    return `The input is ${input}`;
}
```

```js
function addEngineer(engineers, engineer) {
    return [
        // Note: If the function added to the original 'engineers' list without the spread operator, the function will no longer be 'pure', because it is modifying the argument passed by reference
        ...engineers,
        {
            name: engineer.name,
            recentEvent: engineer.recentEvent
        }
    ];
}
```

#### Examples of Impure Functions
```js
function printSum(x, y) {
    console.log(x + y);
}
```

```js
// Note: Even if 'a' is a constant, the 'add' function is still considered to have a side-effect (side-cause).
const a = 1;

function add(b) {
    return a + b;
}
```

```js
function getReceipt(item) {
    return {
        item,
        purchaseDate: new Date()
    }
}
```

### The benefits of Pure Function
Pure Functions are easy to test and maintain. You can predict its behaviour easily and essentially treat it as a 'black box' when testing, as you can simply assert the value the function returns based on the input that is passed in.


### Why use impure functions at all, then?
One might wonder by now, why use 'impure' functions at all, if pure functions are so great? The answer is, programs typically *need* to have side-effects to be useful. Applications will need to read or write to database, make network calls to external APIs,print and display things on the screen and so forth. The goal of **Functional Programming**, therefore, is to **eliminate side-effects wherever possible and tightly  control them wherever it's not.**


## The benefits of **Functional Programming**
- Code becomes more concise and powerful
- Functions tend to be good at doing one thing
- Code becomes easier to reuse, test and maintain
- State of application is more predictable
- Concurrent programming becomes safer
- First-class functions introduces useful advanced concepts
  - Higher order functions
  - Currying
  - Partial functions


You don't need to go all in on Functional Programming with a black & white mindset. The key things, no matter what programming language one is using, should be to be cognisant of side-effects all the time and consider the following when writing a function:
- Does it make sense for this function to have this side-effect?
- How honest is the interface of your function about its complexity?
- How will this affect the testability of the code?