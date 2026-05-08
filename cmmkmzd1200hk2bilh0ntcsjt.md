---
title: "The Magic of this, call(), apply() and bind() in JavaScript"
seoTitle: "The Magic of this call apply and bind in JavaScript"
seoDescription: "this in JavaScript depends on the caller. Learn how it works in functions and objects, and how call(), apply(), and bind() control its value."
datePublished: 2026-03-10T13:19:06.424Z
cuid: cmmkmzd1200hk2bilh0ntcsjt
slug: javascript-this-call-bind-apply
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/320cb3d2-f952-4e78-85a0-72965e504fd4.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/418d36b8-3fe8-4762-9281-1fa8b0afaceb.png
tags: software-development, javascript, coding, this-keyword, chaiaurcode, chaicode, chaicohort

---

## What `this` Means in JavaScript

In JavaScript, `this` is a reference to an object, but it depends on **how and where we use it**.

In a Node environment without strict mode, `this` refers to the global object.

In browsers, `this` refers to the `window` object.

When strict mode is enabled, `this` inside a normal function becomes `undefined`.

So the value of `this` is not fixed. It depends on **who is calling the function**.

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/35cde34e-8985-4e09-8052-9ee51b7eedf6.png align="center")

* * *

## `this` Inside Normal Functions

Inside a normal function, `this` usually refers to the global object (or the `window` object in browsers).

Example:

```javascript
function thisFn() {
  console.log(this)
}

thisFn() // global object...
```

Here the function is called directly, so `this` refers to the global object.

* * *

## `this` Inside Objects

Inside an object, `this` refers to that object.

Example:

```javascript
const f1Team = {
  team: "Ferrari",
  playerMSG: "I have the seat full of water",

  teamRadio() {
    console.log(`${this.team}: must be the water`);
  }
};

f1Team.teamRadio(); 
```

Output:

```plaintext
Ferrari: must be the water
```

Here `this.team` refers to the `team` property of the `f1Team` object.

Because the object `f1Team` is calling the method.

* * *

# Function Borrowing

Sometimes we want to use a method from another object.

JavaScript allows this using:

*   `call()`
    
*   `apply()`
    
*   `bind()`
    

This concept is often called **function borrowing**.

It lets one object use a function that belongs to another object.

* * *

# What call() Does

`call()` gives us the power to control what `this` refers to.

We can call a function and explicitly tell JavaScript which object should be `this`.

Example:

```javascript
const f1Team = { team: "Ferrari" };

function strategy(planA, planB) {
  console.log(`${this.team}: ${planA} ${planA}... actually ${planB}... actually ${planA}`);
}

strategy.call(f1Team, "Box", "Stay out");
```

Output:

```plaintext
Ferrari: Box Box... actually Stay out... actually Box
```

Here we used `call()` to run the function with `this` referring to `f1Team`.

* * *

# What apply() Does

`apply()` works almost the same as `call()`.

The only difference is **how arguments are passed**.

With `apply()`, arguments are passed as an array.

Example:

```javascript
const f1Team = { team: "Ferrari" };

function strategy(step1, step2) {
  console.log(`${this.team}: ${step1}... let us check ${step2}`);
}

strategy.apply(f1Team, ["Plan A", "the spreadsheet"]);
```

Output:

```plaintext
Ferrari: Plan A... let us check the spreadsheet
```

So the difference is simple:

*   `call()` → arguments passed normally
    
*   `apply()` → arguments passed as an array
    

* * *

# What bind() Does

`call()` and `apply()` execute the function immediately.

But `bind()` works differently.

`bind()` does **not execute the function immediately**. Instead, it returns a new function with `this` permanently set.

Example:

```javascript
const f1Team = { team: "Ferrari" };

function teamRadio(driverMsg, engineerReply) {
  console.log(`${this.team}: Driver: ${driverMsg}... Engineer: ${engineerReply}`);
}

const ferrariRadio = teamRadio.bind(
  f1Team,
  "Tyres are gone",
  "Telemetry says they are fine"
);

ferrariRadio();
```

Output:

```plaintext
Ferrari: Driver: Tyres are gone... Engineer: Telemetry says they are fine
```

Here `bind()` created a new function where `this` is always `f1Team`.

* * *

# Difference Between call, apply and bind

| Method | Executes Immediately | Arguments | Returns |
| --- | --- | --- | --- |
| call() | Yes | Passed normally | Result |
| apply() | Yes | Passed as array | Result |
| bind() | No | Passed normally | New function |

* * *

`this` in JavaScript depends on **who is calling the function**.

Inside objects, `this` refers to the object.

Inside normal functions, it usually refers to the global object.

And when we want to control the value of `this`, we can use:

*   `call()`
    
*   `apply()`
    
*   `bind()`
    

These three methods allow functions to be reused across different objects.