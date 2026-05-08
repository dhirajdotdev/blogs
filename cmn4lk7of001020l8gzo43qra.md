---
title: "Destructuring in JavaScript"
seoTitle: "Destructuring in JavaScript"
seoDescription: "Destructuring in JavaScript"
datePublished: 2026-03-24T12:34:43.554Z
cuid: cmn4lk7of001020l8gzo43qra
slug: destructuring-in-javascript
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/f55bc015-3d63-419c-8338-6e650392fc15.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/0ba79af2-b35e-4004-be6a-6baa2b92dc54.png
tags: programming-blogs, javascript, chaicode

---

When we work with arrays and objects in JavaScript, we often need to take values out of them.

Normally we do something like:

```javascript
const user = {
  name: "Dhiraj",
  age: 20
}

const name = user.name
const age = user.age
```

Works fine.

But it feels repetitive.

So JavaScript gives us a cleaner way to do this.

That is destructuring.

In this blog I will share how I understand destructuring and how it makes code simpler.

* * *

## What destructuring means

Destructuring means:

taking values out of an array or object and assigning them to variables

In short:

extract → assign

* * *

## Destructuring objects

Instead of this:

```javascript
const user = {
  name: "Dhiraj",
  age: 20
}

const name = user.name
const age = user.age
```

We can do:

```javascript
const { name, age } = user
```

That’s it.

less code, same result

* * *

## How it actually feels

Object → variables

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/e1486a5b-5ace-4a4c-a8c9-6acdfdbbbc98.png align="center")

* * *

## Important thing

Variable name must match key:

```javascript
const { name } = user
```

takes `user.name`

* * *

## Destructuring arrays

Arrays work a bit differently.

```javascript
const arr = [10, 20, 30]

const [a, b, c] = arr
```

So:

*   `a = 10`
    
*   `b = 20`
    
*   `c = 30`
    

Here it depends on position.

* * *

## Array mapping idea

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/c53971a4-9d4b-4442-818b-2f1a70e3d7e8.png align="center")

* * *

## Skipping values

```javascript
const arr = [10, 20, 30]

const [a, , c] = arr
```

skips middle value

* * *

## Default values

Sometimes value may not exist.

```javascript
const user = {
  name: "Dhiraj"
}

const { name, age = 18 } = user
```

if `age` not present → use default

* * *

## Before vs After

Before:

```javascript
const title = post.title
const author = post.author
const date = post.date
```

After:

```javascript
const { title, author, date } = post
```

cleaner, less repetition

* * *

## Benefits of destructuring

*   reduces repetitive code
    
*   makes code cleaner
    
*   easier to read
    
*   faster to write
    

* * *

## Small real example

```javascript
function greet(user) {
  const { name } = user
  console.log("Hi " + name)
}
```

Even shorter:

```javascript
function greet({ name }) {
  console.log("Hi " + name)
}
```

* * *

## Where you will see it a lot

*   React props
    
*   API responses
    
*   function parameters
    
*   arrays from functions
    

* * *

Destructuring is just a cleaner way to take values out of arrays and objects.

Once you start using it, going back feels weird.

It doesn’t add new power, just makes things simpler.