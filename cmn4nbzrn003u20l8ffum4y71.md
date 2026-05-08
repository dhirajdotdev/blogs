---
title: "Spread vs Rest Operators in JavaScript"
seoTitle: "Spread vs Rest Operators in JavaScript"
seoDescription: "Spread vs Rest Operators in JavaScript"
datePublished: 2026-03-24T13:24:19.285Z
cuid: cmn4nbzrn003u20l8ffum4y71
slug: spread-vs-rest-operators-in-javascript
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/70b7ca41-0a6b-4748-a38e-40abdccadf1f.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/0c63d96f-8124-4eac-b75f-29958b069430.png
tags: programming-blogs, javascript, chaicode

---

In JavaScript, you might have seen these three dots `...`

Sometimes they behave like magic.

Same syntax, but different use.

Sometimes it spreads values Sometimes it collects values

So what’s actually happening?

In this blog I will share how I understand spread and rest operators and how to use them properly.

* * *

## What is spread operator

Spread means:

take something and expand it

Example:

```javascript
const arr = [1, 2, 3]

console.log(...arr)
```

Output:

```id="d4e5f6"
1 2 3
```

array got expanded

* * *

## Spread with arrays

```javascript
const arr1 = [1, 2]
const arr2 = [3, 4]

const newArr = [...arr1, ...arr2]
```

Result:

```id="j1k2l3"
[1, 2, 3, 4]
```

combining arrays becomes easy

* * *

## Spread with objects

```javascript
const user = { name: "Dhiraj" }
const updatedUser = { ...user, age: 20 }
```

copies old object + adds new data

* * *

## Spread idea

**Diagram idea:**

\[1, 2, 3\] → 1, 2, 3

(expanding values)

* * *

## What is rest operator

Rest means:

collect multiple values into one

Example:

```javascript
function sum(...nums) {
  console.log(nums)
}

sum(1, 2, 3)
```

Output:

```id="s1t2u3"
[1, 2, 3]
```

values collected into array

* * *

## Rest in arrays

```javascript
const arr = [1, 2, 3, 4]

const [first, ...rest] = arr
```

So:

*   `first = 1`
    
*   `rest = [2, 3, 4]`
    

* * *

## Rest idea

**Diagram idea:**

1, 2, 3, 4 → \[1, ...rest\]

(rest collects remaining)

* * *

## Spread vs Rest (main difference)

Both use `...` but:

Spread:

expands values

Rest:

collects values

Simple way:

Spread = open

Rest = gather

* * *

## When to use spread

Use spread when:

*   combining arrays
    
*   copying objects
    
*   adding values
    

Example:

```javascript
const arr = [1, 2]
const newArr = [...arr, 3]
```

* * *

## When to use rest

Use rest when:

*   function arguments
    
*   extracting remaining values
    
*   handling unknown number of inputs
    

Example:

```javascript
function log(first, ...others) {
  console.log(first)
  console.log(others)
}
```

* * *

## Real world feeling

Spread:

breaking things apart

Rest:

grouping things together

* * *

## Small practical example

```javascript
const user = {
  name: "Dhiraj",
  age: 20,
  city: "Kolkata"
}

const { name, ...rest } = user
```

`name` separate, rest contains remaining data

* * *

Spread and rest look same but do opposite things.

Spread expands

Rest collects