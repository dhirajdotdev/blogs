---
title: "JavaScript Arrays 101"
seoTitle: "Understanding JavaScript Array"
seoDescription: "Understanding JavaScript Array"
datePublished: 2026-03-07T21:02:03.057Z
cuid: cmmgt75m700oh2eq9e4l41v0w
slug: javascript-arrays
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/96c84ff1-4a83-476c-b948-8f8ea0c35f62.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/e79f2646-1afd-467a-82e2-32c7031f0019.png
tags: software-development, javascript, coding, chaiaurcode, chaicode

---

When we write programs we often need to store multiple values.

For example imagine storing movie names.

```javascript
let movieOne = "Inception"
let movieTwo = "Interstellar"
let movieThree = "Dune: Part Two"
```

This works for small data, but what if we need to store **50 movies or 100 student marks**? Creating variables for each value would become messy.

This is where arrays help us.

Arrays allow us to store multiple values in a single memory reference and access them easily.

* * *

## What Arrays Are

Arrays are non primitive values and are a special type of object in JavaScript.

Arrays allow us to store multiple values inside a single variable.

These values can be numbers, strings, objects or even other arrays.

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/f98c57e9-8ebd-4110-be5f-ec3d2ef9afe6.png align="center")

* * *

## How to Create an Array

There are many ways to create arrays in JavaScript.

### Simple way

The most common way is using square brackets.

```javascript
[1, 2, 3, 4, 5]
```

Just write values between `[]` and your array is ready.

Example:

```javascript
const numbers = [1, 2, 3, 4, 5]
```

* * *

### Array constructor

```javascript
Array(6)
```

This creates:

```plaintext
[ <6 empty items> ]
```

This creates an array with 6 empty slots.

* * *

### Array.of()

```javascript
Array.of(9)
```

This creates:

```plaintext
[9]
```

It creates an array containing the provided values. You can also add multiple values separated by commas.

Example:

```javascript
Array.of(1, 2, 3)
```

* * *

### Array.from()

```javascript
Array.from("six")
```

This creates:

```plaintext
["s","i","x"]
```

It converts iterable data into an array.

Here every character of the string becomes an element in the array.

* * *

## Accessing Elements Using Index

Arrays are **0 based**. That means indexing starts from 0.

Example array:

```javascript
const movies = ["Inception", "Interstellar", "Shawshank Redemption", "Dune: Part Two", "Se7en"]
```

Indexes look like this:

```plaintext
0  1  2  3  4
```

To access individual values we use:

```plaintext
variableName[index]
```

Example:

```javascript
console.log(movies[0]) // Inception
console.log(movies[1]) // Interstellar
console.log(movies[2]) // Shawshank Redemption
console.log(movies[3]) // Dune: Part Two
console.log(movies[4]) // Se7en
```

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/143480cc-b7f7-4630-80e2-1475a848b8c9.png align="center")

* * *

## Updating Elements

We can easily update values inside an array by targeting the index.

Example:

```javascript
movies[0] = "Forrest Gump"
```

Now print the array.

```javascript
console.log(movies)
```

Output:

```plaintext
["Forrest Gump", "Interstellar", "Shawshank Redemption", "Dune: Part Two", "Se7en"]
```

So we accessed index `0` and updated its value.

* * *

## Array Length Property

Counting small arrays is easy.

You can just count 1 to 5.

But imagine counting elements of a **very large array**. That would be difficult.

JavaScript gives us a built in property called `length`.

Let's use the same movie array because these are some of the best movies.

```javascript
const movies = ["Inception", "Interstellar", "Shawshank Redemption", "Dune: Part Two", "Se7en"]

console.log(movies.length) // 5
```

Important thing:

Length and index are not the same.

*   Length tells **how many values exist**
    
*   Index tells **position of each value**
    

* * *

## Basic Looping Over Arrays

Instead of accessing elements one by one, we can loop through the array.

Here I'm using a simple `for` loop to print every movie.

```javascript
const movies = ["Inception", "Interstellar", "Shawshank Redemption", "Dune: Part Two", "Se7en"]

for(let i = 0; i < movies.length; i++){
    console.log(movies[i])
}
```

Output:

```plaintext
Inception
Interstellar
Shawshank Redemption
Dune: Part Two
Se7en
```

This loop runs from index `0` to the last index and prints each value.

* * *

Arrays are one of the most commonly used data structures in JavaScript.

They help us store and manage multiple values easily.