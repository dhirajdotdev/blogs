---
title: "Array Methods You Must Know"
seoTitle: "Array Methods You Must Know"
seoDescription: "Each array method with a simple practical example"
datePublished: 2026-03-11T19:31:50.210Z
cuid: cmmmfqjpb00gq2cp0hp9r9us7
slug: javascript-array-methods
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/7ba24649-f4e8-44d6-ad58-1543950a7f0e.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/838a7faf-cebb-4cb8-9564-a47aac81491c.png
tags: software-development, javascript, array, array-methods, chaiaurcode, chaicode

---

Arrays help us store multiple values in a single variable. But storing data is only part of the story. Most of the time we also need to **process that data**.

For example:

*   change values
    
*   remove unwanted values
    
*   calculate totals
    

JavaScript gives us built in methods to do these tasks easily.

Some of the most useful array methods are:

*   `map()`
    
*   `filter()`
    
*   `reduce()`
    

Let’s understand them one by one.

* * *

# map()

`map()` is used when we want to **transform every value in an array**.

It goes through each element and returns a **new array** with the updated values.

Example array:

```javascript
const numbers = [2, 4, 6, 8]
```

Suppose we want to **double each number**.

### Using a traditional loop

```javascript
const numbers = [2, 4, 6, 8]

const doubled = []

for (let i = 0; i < numbers.length; i++) {
  doubled.push(numbers[i] * 2)
}

console.log(doubled)
```

Output:

```plaintext
[4, 8, 12, 16]
```

Now let’s do the same thing using `map()`.

### Using map()

```javascript
const numbers = [2, 4, 6, 8]

const doubled = numbers.map(function(num) {
  return num * 2
})

console.log(doubled)
```

Output:

```plaintext
[4, 8, 12, 16]
```

Original array stays the same:

```js
console.log(numbers)
```

```plaintext
[2, 4, 6, 8]
```

`map()` creates a **new array** instead of modifying the original one.

* * *

# filter()

Sometimes we only want **some values from an array**.

That is where `filter()` helps.

It returns a **new array containing only the values that match a condition**.

Example array:

```javascript
const numbers = [5, 12, 8, 20, 3]
```

Suppose we want **numbers greater than 10**.

### Using a loop

```javascript
const numbers = [5, 12, 8, 20, 3]

const result = []

for (let i = 0; i < numbers.length; i++) {
  if (numbers[i] > 10) {
    result.push(numbers[i])
  }
}

console.log(result)
```

Output:

```plaintext
[12, 20]
```

Now using `filter()`.

### Using filter()

```javascript
const numbers = [5, 12, 8, 20, 3]

const result = numbers.filter(function(num) {
  return num > 10
})

console.log(result)
```

Output:

```plaintext
[12, 20]
```

Again, the original array remains unchanged.

* * *

# reduce()

`reduce()` is used when we want to **combine all values into a single result**.

Common examples:

*   calculating totals
    
*   counting items
    
*   combining values
    

Example array:

```javascript
const numbers = [10, 20, 30, 40]
```

Suppose we want the **total sum**.

### Using a loop

```javascript
const numbers = [10, 20, 30, 40]

let total = 0

for (let i = 0; i < numbers.length; i++) {
  total += numbers[i]
}

console.log(total)
```

Output:

```plaintext
100
```

Now using `reduce()`.

### Using reduce()

```javascript
const numbers = [10, 20, 30, 40]

const total = numbers.reduce(function(sum, num) {
  return sum + num
}, 0)

console.log(total)
```

Output:

```plaintext
100
```

How it works:

1.  Start with `sum = 0`
    
2.  Add each number
    
3.  Return the final value
    

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/47803709-7f8d-4573-9214-af04e4a443a9.png align="center")

* * *

# Try These Examples Yourself

Create an array of numbers.

```javascript
const numbers = [5, 10, 15, 20]
```

Double every number using `map()`.

```javascript
const doubled = numbers.map(function(num) {
  return num * 2
})

console.log(doubled)
```

Get numbers greater than 10 using `filter()`.

```javascript
const greater = numbers.filter(function(num) {
  return num > 10
})

console.log(greater)
```

Calculate the total sum using `reduce()`.

```javascript
const total = numbers.reduce(function(sum, num) {
  return sum + num
}, 0)

console.log(total)
```

Try running these examples in your browser console.

* * *

Array methods make working with data much easier.

Instead of writing long loops, we can use built in methods like:

*   `map()` to transform values
    
*   `filter()` to select values
    
*   `reduce()` to combine values