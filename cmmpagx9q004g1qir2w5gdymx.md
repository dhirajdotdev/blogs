---
title: "Function Declaration vs Function Expression: What’s the Difference?"
seoTitle: "Function Declaration vs Function Expression"
seoDescription: "Function Declaration vs Function Expression"
datePublished: 2026-03-13T19:27:41.680Z
cuid: cmmpagx9q004g1qir2w5gdymx
slug: function-declaration-vs-function-expression
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/48c921be-d882-46be-a271-d57e4a8a020e.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/14e3c216-8326-41fd-ae94-d9721d8eba6e.png
tags: javascript, chaiaurcode, chaicode

---

When we write programs, we often repeat the same logic again and again.

For example imagine we need to add two numbers in different parts of a program.

Instead of writing the same code multiple times, we can create a function and reuse it whenever we need it.

Functions are reusable blocks of code that perform a specific task.

Example:

```javascript
function add(a, b) {
  return a + b
}

console.log(add(2, 3))
```

Output:

```plaintext
5
```

Here the function performs the addition and we can call it anytime we need.

We can create functions in many ways in JavaScript, but in this blog we will focus on these two ways:

*   Function Declaration
    
*   Function Expression
    

Let’s understand both.

* * *

# Function Declaration

A function declaration defines a function using the `function` keyword followed by the function name.

Example:

```javascript
function multiply(a, b) {
  return a * b
}

console.log(multiply(4, 5))
```

Output:

```plaintext
20
```

Here we created a function named **multiply**.

The function is declared using the `function` keyword and can be called normally in the program.

* * *

# Function Expression

A function expression is slightly different.

Here the function is stored inside a variable.

Example:

```javascript
const multiply = function(a, b) {
  return a * b
}

console.log(multiply(4, 5))
```

Output:

```plaintext
20
```

The function still performs the same task.

The difference is that instead of declaring it directly, we assign the function to a variable.

So the variable now holds the function.

* * *

# Side by Side Comparison

Function Declaration:

```javascript
function add(a, b) {
  return a + b
}
```

Function Expression:

```javascript
const add = function(a, b) {
  return a + b
}
```

Both create functions and both work in almost the same way when we call them.

But there is one important difference between them.

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/4ddd5d29-6f09-4a3d-ad1f-83f0117518e1.png align="center")

* * *

# Hoisting

In JavaScript, before the code runs, the engine prepares some things in memory. This behavior is commonly referred to as **hoisting**.

At a very high level, this means some declarations become available earlier than where they appear in the code.

Function declarations follow this behavior.

Example:

```javascript
console.log(add(2,3))

function add(a, b) {
  return a + b
}
```

Even though the function appears later in the code, the program still runs.

Now look at a function expression:

```javascript
console.log(add(2,3))

const add = function(a, b) {
  return a + b
}
```

This will cause an error.

That happens because the variable that holds the function is not ready yet at that point.

So the simple idea is:

Function Declaration → can be called earlier in the code  
Function Expression → cannot be called before it is defined

No need to go deep into how JavaScript internally handles this. Just remembering this behavior is enough for now.

* * *

# When to Use Each Type

Both styles are used a lot in JavaScript.

Function declarations are commonly used when the function represents a main piece of logic in the program.

Function expressions are useful when functions need to be stored in variables, passed around or used inside other functions.

You will see function expressions very often when working with callbacks and modern JavaScript patterns.

* * *

# Example

Function declaration that multiplies two numbers:

```javascript
function multiply(a, b) {
  return a * b
}

console.log(multiply(3, 4))
```

The same logic using a function expression:

```javascript
const multiplyExp = function(a, b) {
  return a * b
}

console.log(multiplyExp(3, 4))
```

If you try calling these before their definitions, you will notice something interesting.

Function declarations still work, but function expressions will throw an error.

That small behavior difference is what usually separates these two ways of creating functions.