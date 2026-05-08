---
title: "Error Handling in JavaScript: Try, Catch, Finally"
seoTitle: "Error Handling in JavaScript: Try, Catch, Finally"
seoDescription: "Error Handling in JavaScript: Try, Catch, Finally"
datePublished: 2026-03-24T14:47:21.223Z
cuid: cmn4qarut005y20l84s904kz4
slug: error-handling-in-javascript-try-catch-finally
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/a27da5f2-4ff9-4a47-8b60-5aaff4b08324.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/ca372202-536d-4000-b945-e1b6a1324051.png
tags: programming-blogs, javascript, error-handling, chaicode

---

When we write JavaScript, we expect things to work.

But in real world apps, things break.

Maybe:

*   API fails
    
*   variable is undefined
    
*   wrong data comes
    

And when something breaks, JavaScript throws an error and stops execution.

That’s not good for users.

So we need a way to handle errors properly.

In this blog I will share how I understand error handling using try, catch and finally.

* * *

## What errors are in JavaScript

Errors are situations where something goes wrong during execution.

Example:

```javascript
console.log(x)
```

Output:

```id="k1l0m8"
ReferenceError: x is not defined
```

Here:

JavaScript stops execution

So if this happens in real app, user experience breaks.

* * *

## Why error handling matters

Instead of crashing the app, we can handle the error and continue.

show message, log error, fallback behavior

So error handling is about:

graceful failure

* * *

## Using try and catch

Basic idea:

try the code if error happens → catch it

Example:

```javascript
try {
  console.log(x)
} catch (error) {
  console.log("Something went wrong")
}
```

Now:

instead of crash → we handle it

* * *

## How it actually flows

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/7740f4ae-99c5-4a14-b41e-7c3228e59aa6.png align="center")

* * *

## Accessing the error

```javascript
try {
  console.log(x)
} catch (error) {
  console.log(error.message)
}
```

`error` contains details

Useful for debugging.

* * *

## The finally block

Finally always runs.

No matter what.

Example:

```javascript
try {
  console.log("Try running")
} catch (err) {
  console.log("Error")
} finally {
  console.log("Always runs")
}
```

Output:

```plaintext
Try running
Always runs
```

Even if error happens:

finally still runs

* * *

## Why finally is useful

Use it for:

*   cleanup
    
*   closing resources
    
*   final steps
    

* * *

## Try → Catch → Finally flow

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/550d3913-6200-466d-a8fd-e8e53b536e74.png align="center")

* * *

## Throwing custom errors

Sometimes we want to create our own error.

```javascript
function checkAge(age) {
  if (age < 18) {
    throw new Error("Age must be 18+")
  }

  console.log("Access granted")
}

try {
  checkAge(16)
} catch (err) {
  console.log(err.message)
}
```

Here:

we manually throw error

* * *

## Why throw is useful

*   validate data
    
*   enforce rules
    
*   control flow
    

* * *

## Real world feel

Instead of app crashing:

we control what happens when something goes wrong

* * *

## Common pattern

```javascript
try {
  // risky code
} catch (err) {
  // handle error
} finally {
  // always run
}
```

* * *

## Important thing to remember

*   try only catches runtime errors
    
*   syntax errors won’t be caught
    

* * *

Errors will happen.

That’s normal.

What matters is how you handle them.

Using try, catch, and finally helps you:

prevent crashes

debug better

build stable apps