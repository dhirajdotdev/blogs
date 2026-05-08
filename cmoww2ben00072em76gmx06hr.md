---
title: "Async Code in Node.js: Callbacks and Promises"
seoTitle: "Async Code in Node.js Callbacks and Promises"
seoDescription: "Async Code in Node.js: Callbacks and Promises"
datePublished: 2026-05-08T12:25:59.619Z
cuid: cmoww2ben00072em76gmx06hr
slug: async-code-in-node-js-callbacks-and-promises
tags: javascript, asynchronous, nodejs, asynchronous-javascript, chaicode

---

JavaScript runs on a single thread.

That means it executes one task at a time.

So a big question appears:

> How does Node.js handle file reading, APIs, databases, or timers without freezing the entire application?

The answer is:

# Asynchronous Code

Instead of blocking execution and waiting for tasks to finish, Node.js delegates long running operations and continues executing other code.

This is one of the biggest reasons Node.js can handle thousands of concurrent operations efficiently.

Let’s understand how this works using file reading.

* * *

# Why Async Code Exists in Node.js

Imagine reading a huge file from disk.

If Node.js waited for the file completely before moving forward, the entire server would stop during that time.

Example problem:

```js
const data = readFileSync("large.txt");
console.log(data);
```

`readFileSync()` blocks execution.

Nothing else can run until the file is fully read.

In a server environment, this is bad because:

*   requests may get delayed
    
*   users may wait unnecessarily
    
*   the application becomes less scalable
    

Node.js solves this using asynchronous operations.

* * *

# Callback-Based Async Execution

Node.js originally handled async tasks using callbacks.

Example:

```js
const fs = require("fs");

fs.readFile("data.txt", "utf-8", (err, data) => {
  if (err) {
    console.log(err);
    return;
  }

  console.log(data);
});

console.log("Reading file...");
```

* * *

# What Happens Internally?

Step-by-step flow:

1.  `fs.readFile()` starts file reading
    
2.  Node.js delegates the task
    
3.  JavaScript continues executing next lines
    
4.  `"Reading file..."` prints immediately
    
5.  File reading finishes later
    
6.  Callback function executes with result
    

Output:

```txt
Reading file...
File content here...
```

This is asynchronous execution.

The program does not stop while waiting for the file.

* * *

# Understanding the Callback

This function:

```plaintext
(err, data) => {}
```

is called a callback.

It is simply a function passed into another function to run later.

Node.js says:

> “When the task finishes, call this function.”

* * *

# The Problem With Nested Callbacks

Callbacks work well initially.

But things become messy when multiple async operations depend on each other.

Example:

```js
loginUser(user, (userData) => {
  getPosts(userData.id, (posts) => {
    getComments(posts[0].id, (comments) => {
      console.log(comments);
    });
  });
});
```

This structure keeps growing inward.

This is commonly called:

# Callback Hell

Problems:

*   deeply nested code
    
*   difficult debugging
    
*   poor readability
    
*   hard error handling
    
*   difficult maintenance
    

As applications scale, callback chains become harder to manage.

* * *

# Promise-Based Async Handling

Promises were introduced to make async code cleaner and more manageable.

A Promise represents a value that may complete:

*   now
    
*   later
    
*   or fail
    

* * *

# Promise States

A promise has 3 states:

*   Pending → operation still running
    
*   Fulfilled → operation completed successfully
    
*   Rejected → operation failed
    

* * *

# File Reading Using Promises

Example:

```js
const fs = require("fs/promises");

fs.readFile("data.txt", "utf-8")
  .then((data) => {
    console.log(data);
  })
  .catch((err) => {
    console.log(err);
  });

console.log("Reading file...");
```

* * *

# What Changed?

Instead of passing a callback directly:

*   `readFile()` returns a Promise
    
*   `.then()` handles success
    
*   `.catch()` handles errors
    

This creates a cleaner async flow.

* * *

# Comparing Callback vs Promise Readability

## Callback Version

```js
getUser(id, (user) => {
  getPosts(user.id, (posts) => {
    getComments(posts[0].id, (comments) => {
      console.log(comments);
    });
  });
});
```

* * *

## Promise Version

```js
getUser(id)
  .then((user) => getPosts(user.id))
  .then((posts) => getComments(posts[0].id))
  .then((comments) => console.log(comments))
  .catch((err) => console.log(err));
```

The Promise version:

*   flows top to bottom
    
*   reduces nesting
    
*   centralizes error handling
    
*   improves readability
    

* * *

# Why Promises Are Better

Promises solve many callback problems.

Benefits:

*   cleaner chaining
    
*   better readability
    
*   easier error handling
    
*   less nesting
    
*   more maintainable code
    

They also became the foundation for:

```js
async/await
```

which is modern JavaScript’s preferred async syntax.

* * *

# Async Flow Mental Model

## Callback Flow

Start task

↓

Continue execution

↓

Task finishes later

↓

Callback runs

* * *

## Promise Flow

Start async operation

↓

Promise returned immediately

↓

Operation completes later

↓

`.then()` or `.catch()` executes

* * *

# Important Insight About Node.js

Node.js is not “doing multiple JavaScript things at once.”

JavaScript still runs on a single thread.

What actually happens is:

*   Node.js delegates expensive operations
    
*   JavaScript continues running
    
*   completed tasks return later
    

This is why async programming is essential in Node.js.

Without it, servers would block constantly.

* * *

Async programming is one of the core ideas behind Node.js.

Callbacks introduced the ability to run non-blocking operations, but managing large callback chains became difficult.

Promises improved this by making async flows:

*   cleaner
    
*   flatter
    
*   easier to reason about
    

The key idea is simple:

Node.js avoids waiting.

Instead of stopping execution for slow operations like:

*   file reading
    
*   database queries
    
*   API requests
    

it schedules them and continues running other code.

That’s what makes Node.js efficient for scalable backend applications.