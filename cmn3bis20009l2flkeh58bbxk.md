---
title: "Understanding the `this` Keyword in JavaScript"
seoTitle: "Understanding the "this" Keyword"
seoDescription: "Understanding the "this" Keyword"
datePublished: 2026-03-23T15:05:54.314Z
cuid: cmn3bis20009l2flkeh58bbxk
slug: understanding-the-this-keyword-in-javascript
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/7da2d15f-c8ec-4f2c-bbf6-b35c40bd8110.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/c02c093d-3cbc-41cb-a7a5-925386c41900.png
tags: programming-blogs, javascript, this-keyword, chaicode

---

When we start writing JavaScript, everything feels simple. Variables, functions, objects all good.

Then suddenly we see `this`.

And things start getting confusing.

Sometimes it works, sometimes it doesn’t. Same code, different output.

So what actually is `this`?

In this blog I will share how I understand `this` and why it behaves differently in different places.

* * *

## What `this` actually represents

The easiest way to think about `this` is:

`this` means **who is calling this function**

Not where the function is written Not where it is defined

But **who is calling it**

That’s the whole game.

* * *

## `this` in global context

If you use `this` outside any function:

```javascript
console.log(this)
```

In browser, this points to:

`window`

So here:

```javascript
this === window // true
```

So global level → `this` = global object

* * *

## `this` inside an object

Now the interesting part.

```javascript
const user = {
  name: "Dhiraj",
  greet() {
    console.log(this.name)
  }
}

user.greet()
```

Output:

```id="m3yazk"
Dhiraj
```

Why?

Because:

`user` is calling `greet()`

So:

`this` = `user`

Simple.

* * *

## `this` inside a normal function

Now this is where confusion starts.

```javascript
function show() {
  console.log(this)
}

show()
```

Here:

No object is calling this function

So in browser:

`this` = `window`

Because it falls back to global object.

* * *

## Same function, different caller

Now see this carefully:

```javascript
const obj1 = {
  name: "A",
  show() {
    console.log(this.name)
  }
}

const obj2 = {
  name: "B",
  show: obj1.show
}

obj1.show() // ?
obj2.show() // ?
```

Output:

```plaintext
A
B
```

Same function.

Different output.

Why?

Because caller changed

So:

*   `obj1.show()` → `this` = obj1
    
*   `obj2.show()` → `this` = obj2
    

This proves:

`this` depends on caller, not function

* * *

## Calling context changes everything

Let’s break it more.

```javascript
const user = {
  name: "Dhiraj",
  greet() {
    console.log(this.name)
  }
}

const fn = user.greet
fn()
```

Output:

```plaintext
undefined
```

Why?

Because now:

function is called directly no object is calling it

So:

`this` = window window.name is undefined

That’s why output is undefined

* * *

## Simple way to remember

Just ask:

Who is calling this function?

That’s your `this`.

* * *

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/9c334dc5-ee8c-4eed-9c99-5ecad52e2834.png align="center")

* * *

## One more simple example

```javascript
const car = {
  brand: "BMW",
  show() {
    console.log(this.brand)
  }
}

car.show()
```

car is calling → `this` = car

* * *

## Where people get confused

Main confusion happens when:

*   function is detached from object
    
*   function is passed somewhere
    
*   function is called without object
    

Because then:

`this` changes

* * *

`this` is not complicated.

We just overthink it.

Just remember one line:

`this` = who is calling the function