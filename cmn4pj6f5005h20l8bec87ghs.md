---
title: "The `new` Keyword in JavaScript"
seoTitle: "The `new` Keyword"
seoDescription: "The `new` Keyword"
datePublished: 2026-03-24T14:25:53.731Z
cuid: cmn4pj6f5005h20l8bec87ghs
slug: the-new-keyword-in-javascript
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/b0a74cf3-df52-46a0-8d40-47a435d24b29.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/7e2bf0e8-adf2-4cb8-a2d4-43a735d96578.png
tags: programming-blogs, javascript, chaicode

---

In JavaScript, you might have seen `new` in code like:

```javascript
const user = new User()
```

We use it, but many times we don’t really know what it’s doing internally.

It feels like it just creates an object.

But actually, a lot of things are happening behind the scenes.

In this blog I will share how I understand the `new` keyword and what really happens when we use it.

* * *

## What the `new` keyword does

When you use `new`, JavaScript creates a new object for you.

But not just that.

It also connects things, sets values and returns that object.

So `new` is doing multiple steps, not just one.

* * *

## Constructor functions

To use `new`, we usually have something called a constructor function.

Example:

```javascript
function User(name, age) {
  this.name = name
  this.age = age
}
```

Now we use:

```javascript
const user1 = new User("Dhiraj", 20)
```

Here:

`User` is a constructor --> `user1` is an instance

* * *

## How it actually feels

constructor = blueprint

instance = real object

* * *

## Object creation step by step

When we do:

```javascript
const user1 = new User("Dhiraj", 20)
```

JavaScript does this internally:

### Step 1: create empty object

```js
{}
```

* * *

### Step 2: set `this` to that object

Inside function:

```plaintext
this → {}
```

* * *

### Step 3: add properties

```javascript
this.name = "Dhiraj"
this.age = 20
```

Now object becomes:

```plaintext
{ name: "Dhiraj", age: 20 }
```

* * *

### Step 4: link prototype

```javascript
user1.__proto__ = User.prototype
```

so it can access shared methods

* * *

### Step 5: return object

Final result:

```js
user1
```

* * *

## Constructor → instance flow

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/1a7d4c6f-2dd7-4f75-a098-b5d595e5f108.png align="center")

* * *

## How prototype is linked

```javascript
function User(name) {
  this.name = name
}

User.prototype.sayHi = function () {
  console.log("Hi " + this.name)
}

const user1 = new User("Dhiraj")
user1.sayHi()
```

Why this works?

because `user1` is linked to `User.prototype`

So it can access `sayHi`

* * *

## Prototype visual idea

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/3e83b107-905a-4a8b-8d30-5d444ae37b5f.png align="center")

* * *

## Instances created from constructors

```javascript
const u1 = new User("A")
const u2 = new User("B")
```

both are different objects

But:

share same prototype

So methods are not duplicated.

* * *

## Why `new` is useful

Without `new`, you would have to manually:

*   create object
    
*   assign values
    
*   link prototype
    

`new` does all that automatically.

* * *

## What happens if we don’t use `new`

```javascript
const user = User("Dhiraj", 20)
```

Now:

`this` = global object

So it can break things.

That’s why `new` is important here.

* * *

## Simple way to remember

`new` does:

create object --> bind `this` --> link prototype --> return object