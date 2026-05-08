---
title: "Async Await in JavaScript Writing Cleaner Asynchronous Code"
seoTitle: "Async Await in JavaScript Writing Cleaner Asynchronous Code"
seoDescription: "Async Await in JavaScript Writing Cleaner Asynchronous Code"
datePublished: 2026-03-24T16:26:20.044Z
cuid: cmn4tu2a2008z20l84l05fazi
slug: async-await-in-javascript
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/3ce29b53-6fe8-4599-b252-5daa14dc50ac.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/f5fe4ac1-77f5-49b2-abcf-5cf24eac9d2e.png
tags: programming-blogs, javascript, chaicode

---

When we learned about asynchronous JavaScript we saw how callbacks work.

Then promises came to solve callback nesting.

But even promises can feel messy sometimes with `.then()` chains.

So JavaScript introduced async and await to make things cleaner.

In this blog I will share how I understand async await and why it makes async code easier to read and write.

* * *

## Why async await was introduced

With promises we usually write code like:

```javascript
fetchData()
  .then((res) => {
    return processData(res)
  })
  .then((data) => {
    console.log(data)
  })
  .catch((err) => {
    console.log(err)
  })
```

This works fine.

But as things grow it starts looking like a chain.

Harder to read.

So async await was introduced to make this look like normal code.

* * *

## How async functions work

When you add `async` before a function:

```javascript
async function getData() {
  return "hello"
}
```

This function always returns a promise.

Even if you return a normal value.

```js
getData().then(console.log) // hello
```

So:

async function → always returns promise

* * *

## What await does

`await` is used inside async function.

It pauses the execution until promise resolves.

Example:

```javascript
async function getData() {
  const res = await fetch("https://api.freeapi.app/api/v1/public/randomusers?page=1&limit=10")
  console.log(res)
}
```

Here:

JavaScript waits for fetch to finish then moves to next line

So it feels like synchronous code.

* * *

## How it actually feels

Instead of:

Promise → then → then

You write:

Step 1 wait Step 2

* * *

## Promise vs async await

Promise style:

```javascript
fetchData()
  .then((res) => processData(res))
  .then((data) => console.log(data))
```

Async await style:

```javascript
async function run() {
  const res = await fetchData()
  const data = await processData(res)
  console.log(data)
}
```

Same thing.

But second one looks cleaner.

* * *

## Async function flow

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/8d389d47-3fdd-4591-bdf0-f2660530d5bf.png align="center")

* * *

## Error handling with async await

With promises:

```javascript
fetchData()
  .then((res) => console.log(res))
  .catch((err) => console.log(err))
```

With async await:

```javascript
async function run() {
  try {
    const res = await fetchData()
    console.log(res)
  } catch (err) {
    console.log(err)
  }
}
```

Same concept.

Just cleaner.

* * *

## Why this matters

Async await makes code:

*   easier to read
    
*   easier to debug
    
*   easier to write
    

It looks like normal step by step code even though it is async.

* * *

## Important thing to remember

*   await only works inside async function
    
*   async function always returns promise
    

* * *

## Simple real example

```javascript
async function getUser() {
  try {
    const res = await fetch("https://api.freeapi.app/api/v1/public/randomusers?page=1&limit=10")
    const data = await res.json()
    console.log(data)
  } catch (err) {
    console.log("Error fetching user")
  }
}
```

* * *

## Mental model

async await is just:

promise + cleaner syntax

Nothing new under the hood.

* * *

Async await does not replace promises.

It is built on top of promises.

It just makes async code look simple and readable.