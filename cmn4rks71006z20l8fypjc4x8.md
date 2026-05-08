---
title: "Synchronous vs Asynchronous JavaScript"
seoTitle: "Synchronous vs Asynchronous JavaScript"
seoDescription: "Synchronous vs Asynchronous JavaScript"
datePublished: 2026-03-24T15:23:07.839Z
cuid: cmn4rks71006z20l8fypjc4x8
slug: synchronous-vs-asynchronous-javascript
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/9bb4037c-6c0d-4270-83b2-daa113e74379.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/bb3f68a2-0628-4756-bbe6-84fe4c2ed86c.png
tags: programming-blogs, javascript, chaicode

---

When we write JavaScript most of the time code runs line by line.

One step after another.

Simple.

But in real apps things do not always happen instantly.

Sometimes you have to wait:

*   fetching data from API
    
*   loading files
    
*   timers
    

So what happens then?

Does JavaScript just stop and wait?

No.

That is where synchronous and asynchronous behavior comes in.

In this blog I will share how I understand sync vs async in JavaScript.

* * *

## What synchronous code means

Synchronous means:

one thing at a time

Code runs step by step.

Example:

```javascript
console.log("Start")
console.log("Middle")
console.log("End")
```

Output:

```plaintext
Start
Middle
End
```

each line waits for previous one

* * *

## How it feels

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/815a1612-5a4a-4503-9b90-2f1c7d46ac50.png align="center")

Straight line execution

* * *

## What asynchronous code means

Asynchronous means:

do not wait move ahead

Example:

```javascript
console.log("Start")

setTimeout(() => {
  console.log("Inside timeout")
}, 2000)

console.log("End")
```

Output:

```plaintext
Start
End
Inside timeout
```

Even though timeout is in middle it runs later

* * *

## Why JavaScript needs async

Imagine this:

You call an API that takes 5 seconds.

If JavaScript waits:

everything freezes

*   UI stuck
    
*   buttons not working
    
*   bad experience
    

So instead JavaScript says:

I will start this task and continue other work

* * *

## Real life example

Think like ordering food:

Synchronous:

order → wait → get food → then do next thing

Asynchronous:

order → do other work → get food later

* * *

## Blocking vs non blocking

Synchronous:

blocking

It waits.

Asynchronous:

non blocking

It continues.

* * *

## Problem with blocking code

Let us look at this:

```javascript
console.log("Start")

setTimeout(() => {
  console.log("Waited 3 seconds")
}, 3000)

console.log("End")
```

Output:

```plaintext
Start
End
Waited 3 seconds
```

Now imagine if JavaScript waited for this like synchronous code:

```plaintext
Start
(wait 3 seconds)
Waited 3 seconds
End
```

everything would pause

nothing else would run

app would feel stuck

* * *

## Async flow

When async task happens:

JavaScript sends it to background

continues execution

later runs the function

* * *

## Async mental model

Diagram idea:

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/6b7bedc1-062e-4a8e-848a-a5aa1efc6f96.png align="center")

* * *

## Simple async example

```javascript
setTimeout(() => {
  console.log("Done")
}, 1000)
```

runs after delay

* * *

## Where you see async

*   API calls
    
*   database queries
    
*   timers
    
*   file operations
    

* * *

## Why this matters

Without async:

apps would freeze

With async:

smooth experience

* * *

## Quick comparison

Synchronous:

*   step by step
    
*   blocking
    

Asynchronous:

*   runs in background
    
*   non blocking
    

* * *

JavaScript is single threaded.

So it cannot do everything at once.

Async is how it handles waiting tasks without stopping everything.