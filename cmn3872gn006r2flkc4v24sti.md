---
title: "Callbacks in JavaScript: Why They Exist"
seoTitle: "Callbacks in JavaScript"
seoDescription: "Callbacks in JavaScript"
datePublished: 2026-03-23T13:32:49.084Z
cuid: cmn3872gn006r2flkc4v24sti
slug: callbacks-in-javascript
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/c5035f38-b12c-4f67-8427-e7b59dc4dd6d.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/644cacf4-1f7b-490a-a14b-8dbca0fd7b69.png
tags: programming-blogs, javascript, coding, chaicode

---

When we write JavaScript, we usually call functions and get results immediately. Everything feels simple you call something, it runs and gives back output.

But in real world apps, things are not always instant.

Sometimes you are fetching data from an API, reading a file or waiting for some operation to finish. These things take time. JavaScript doesn’t want to stop everything and wait for that.

So how does it handle this?

That’s where callbacks come into the picture.

In this blog I will share how I understand callbacks, why they exist and where they are actually used.

* * *

## Functions as values

Before callbacks, we need to understand one simple thing.

In JavaScript, functions are just values.

That means you can:

*   store them in variables
    
*   pass them to other functions
    
*   return them from functions
    

Example:

```javascript
function sayHello() {
  console.log("Hello")
}

function greet(fn) {
  fn()
}

greet(sayHello)
```

Here we are passing a function inside another function.

So this is the base of callbacks.

* * *

## What is a callback function

A callback is just a function that you pass into another function so it can be called later.

That’s it.

Example:

```javascript
function greet(name, callback) {
  console.log("Hi " + name)
  callback()
}

function sayBye() {
  console.log("Bye")
}

greet("Dhiraj", sayBye)
```

Here:

*   `sayBye` is passed as a callback
    
*   `greet` decides when to call it
    

So callback means:

“I’ll give you this function, you call it when needed”

* * *

## Why callbacks exist

Now the important part.

Why do we even need callbacks?

Because some tasks take time.

Example:

*   fetching data from server
    
*   reading files
    
*   timers
    
*   database queries
    

JavaScript is single threaded, so it cannot block everything and wait.

Instead, it says:

“Start this task and when it finishes, call this function”

That function is the callback.

* * *

## Simple async example

```javascript
setTimeout(() => {
  console.log("This runs later")
}, 2000)

console.log("This runs first")
```

Output:

```plaintext
This runs first
This runs later
```

Here:

*   `setTimeout` takes a function
    
*   runs it after 2 seconds
    

That function is a callback.

So flow becomes:

You give a function → JS runs it later

* * *

## Callback in real use

Let’s say you are fetching data:

```javascript
function getData(callback) {
  setTimeout(() => {
    console.log("Data received")
    callback()
  }, 2000)
}

getData(() => {
  console.log("Process data")
})
```

Here:

*   first data comes
    
*   then callback runs
    

So instead of waiting, we say:

“When data is ready, then do this”

* * *

## How it actually flows

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/39b4fea7-fdf1-4918-b59c-de40f674e2cc.png align="center")

* * *

## Passing functions as arguments

This is the main thing behind callbacks.

```javascript
function doSomething(fn) {
  console.log("Doing something")
  fn()
}

doSomething(() => {
  console.log("Callback called")
})
```

So:

*   function goes inside another function
    
*   gets executed when needed
    

* * *

## Where you actually see callbacks

You already use callbacks without noticing:

*   `setTimeout`
    
*   event listeners
    
*   API calls (older style)
    
*   array methods like `map`, `filter`
    

Example:

```javascript
[1, 2, 3].map((num) => num * 2)
```

That function inside `map` is also a callback.

* * *

## The problem with callbacks

Callbacks solve async problem, but they create another problem.

When things get complex, callbacks start going inside callbacks.

Example:

```javascript
setTimeout(() => {
  console.log("Step 1")

  setTimeout(() => {
    console.log("Step 2")

    setTimeout(() => {
      console.log("Step 3")
    }, 1000)

  }, 1000)

}, 1000)
```

Now it starts going right → right → right

This is called:

callback nesting or callback hell

Hard to read Hard to debug Hard to maintain

* * *

## Why this becomes a problem

Because:

*   code becomes deeply nested
    
*   flow is hard to understand
    
*   error handling becomes messy
    

So while callbacks solve async, they introduce complexity.

That’s why later:

Promises came, async/await came

(but that’s for another blog [here](https://blog.dhiraj.dev/understanding-javascript-promises-with-shaktimaan-vs-dr-jackal) you can read)

* * *

## Nested callback flow

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/310f82df-0ccf-4df9-a94b-953c3a22e609.png align="center")

* * *

Callbacks are simple.

Just functions passed into other functions.

But they exist for a very important reason to handle things that don’t happen instantly