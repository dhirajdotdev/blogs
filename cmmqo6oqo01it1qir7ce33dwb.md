---
title: "Arrow Functions in JavaScript: A Simpler Way to Write Functions"
seoTitle: "Arrow Functions in JavaScript"
seoDescription: "Arrow Functions in JavaScript: A Simpler Way to Write Functions"
datePublished: 2026-03-14T18:39:24.867Z
cuid: cmmqo6oqo01it1qir7ce33dwb
slug: arrow-functions-in-javascript
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/c9da5258-9e3c-45be-8efe-d9dfbb19428c.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/10be9732-c2c8-4652-af0c-8b366f8146af.png
tags: javascript, arrowfunction, arrow-functions-in-javascript, chaicode

---

When writing JavaScript functions, sometimes the syntax can feel a little long. Especially when the function is small and only does a simple task.

For example calculating a number, returning a value or transforming data.

To make function writing simpler and cleaner, JavaScript introduced **arrow functions** in ES6.

Arrow functions provide a shorter syntax for writing functions and are widely used in modern JavaScript.

Let’s understand how they work.

* * *

# Normal Function Example

First let’s start with a normal function.

Suppose we want a function that calculates the square of a number.

```javascript
function square(num) {
  return num * num
}

console.log(square(4))
```

Output

```plaintext
16
```

This works perfectly fine.

But for very small functions, this syntax can feel a bit verbose.

Arrow functions provide a simpler way.

* * *

# Arrow Function Syntax

The same function written using an arrow function looks like this.

```javascript
const square = (num) => {
  return num * num
}

console.log(square(4))
```

The arrow `=>` replaces the `function` keyword.

So instead of writing `function`, we write an **arrow**.

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/4193bfcb-d23a-4155-9039-8fc0aebb80f9.png align="center")

* * *

# Arrow Function with One Parameter

If the function has **only one parameter**, we can even remove the parentheses.

```javascript
const square = num => {
  return num * num
}

console.log(square(5))
```

This is very common in modern JavaScript.

* * *

# Arrow Function with Multiple Parameters

If the function has multiple parameters, we keep the parentheses.

Example:

```javascript
const add = (a, b) => {
  return a + b
}

console.log(add(3, 7))
```

Here both parameters go inside the parentheses.

* * *

# Implicit Return vs Explicit Return

Arrow functions have a useful feature called **implicit return**.

If the function body contains only one expression, JavaScript automatically returns the result.

Normal arrow function:

```javascript
const square = (num) => {
  return num * num
}
```

Implicit return version:

```javascript
const square = num => num * num
```

Here we removed:

*   curly braces
    
*   `return` keyword
    

JavaScript automatically returns the result.

This makes arrow functions very concise.

* * *

# Even or Odd Example

Here is a small example that checks if a number is even.

```javascript
const isEven = num => num % 2 === 0

console.log(isEven(6))
```

Output

```plaintext
true
```

* * *

# Arrow Functions with Arrays

Arrow functions are often used with array methods like `map()`, `filter()`, and `reduce()`.

Example using `map()`.

```javascript
const numbers = [1, 2, 3, 4]

const squares = numbers.map(num => num * num)

console.log(squares)
```

Output

```plaintext
[1, 4, 9, 16]
```

Here the arrow function makes the code much shorter and easier to read.

* * *

# Basic Difference from Normal Functions

Arrow functions and normal functions both create functions, but they are used slightly differently.

Normal functions are commonly used for defining main logic.

Arrow functions are often used for:

*   short utility functions
    
*   callbacks
    
*   array transformations
    

One important difference is how they handle `this`, but that is a deeper topic and we don’t need to go into it right now.

* * *

# Syntax Breakdown

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/569476b2-69c9-4911-ad5e-108ea237b09a.png align="center")

* * *

Arrow functions provide a shorter and cleaner way to write functions in JavaScript.

They reduce boilerplate code and make small functions easier to read.

Because of this, arrow functions are widely used in modern JavaScript, especially when working with arrays, callbacks and functional patterns.

Normal functions are still important, but arrow functions make many everyday tasks much simpler.