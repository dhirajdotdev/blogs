---
title: "JavaScript Operators: The Basics You Need to Know"
seoTitle: "JavaScript Operators The Basics You Need to Know"
seoDescription: "JavaScript Operators The Basics You Need to Know"
datePublished: 2026-03-03T15:27:22.491Z
cuid: cmmarhcop004t2fjufktcdpii
slug: javascript-operators
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/4d329a4d-fbed-4bd6-8e18-70a174b094cb.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/d58101bf-a915-42a1-970c-34afb7622cf7.png
tags: javascript, chaiaurcode, chaicode

---

Just like we need operators to do mathematics in real life, we also need them in any programming language. In JavaScript too.

In JS we have arithmetic operators. We also have more operators for validation and logic like comparison operators, logical operators and assignment operators.

Let’s deep dive into this pool of operators.

* * *

## What Operators Are

To perform arithmetic operations we use certain symbols. For addition we use `+`, for subtraction we use `-` and so on. These symbols are called operators.

In simple words, operators are special symbols that perform operations on values.

They tell JavaScript what action to perform.

* * *

## Arithmetic Operators

As now we know what operators are, let’s start with math operators.

In JavaScript we use:

`+` for addition  
`-` for subtraction  
`*` for multiplication  
`/` for division  
`%` for remainder

Let’s understand each with examples.

```javascript
let num1 = 10;
let num2 = 3;

console.log(num1 + num2); // 13
console.log(num1 - num2); // 7
console.log(num1 * num2); // 30
console.log(num1 / num2); // 3.333...
console.log(num1 % num2); // 1
```

The `%` operator gives remainder.

10 divided by 3 leaves remainder 1, so that’s what it returns.

These are the operators you will use almost daily.

* * *

## Comparison Operators

To validate data through comparison, JavaScript provides comparison operators:

`==`, `===`, `!=`, `!==`, `<`, `>`

These operators compare two values and return a Boolean value, which means either true or false.

There’s a catch between `==` and `===`.

`==` checks only the value.  
`===` checks both value and type. It is a strict check.

Let’s see it clearly.

```javascript
console.log(5 == "5");  // true
console.log(5 === "5"); // false
```

Why?

Because in the first case `==` only checks the value. 5 and "5" are treated as equal.

But in the second case `===` checks type also. One is number and the other is string. So it returns false.

That’s why in real projects we prefer `===` because it is more strict and safer.

Now look at not equal operators.

```javascript
console.log(5 != 10);   // true
console.log(5 !== "5"); // true
```

`!=` checks value only.  
`!==` checks value and type.

Now greater than and less than.

```javascript
console.log(10 > 5); // true
console.log(3 < 1);  // false
```

Comparison operators always return true or false.

* * *

## Logical Operators

There are three main logical gates.

AND  
OR  
NOT

To perform these logical operations JavaScript gives us:

`&&` for AND  
`||` for OR  
`!` for NOT

Let’s understand each.

### AND ( && )

AND means both conditions must be true.

```javascript
let age = 20;
let hasId = true;

console.log(age > 18 && hasId); // true
```

If both sides are true, result is true.  
If one is false, result becomes false.

* * *

### OR ( || )

OR means at least one condition must be true.

```javascript
let isAdmin = false;
let isEditor = true;

console.log(isAdmin || isEditor); // true
```

If one condition is true, result becomes true.

* * *

### NOT ( ! )

NOT reverses the value.

```javascript
let isLoggedIn = false;

console.log(!isLoggedIn); // true
```

If value is true, it becomes false.  
If value is false, it becomes true.

Logical operators are mostly used in conditions.

* * *

## Assignment Operators

To assign value to a variable we use `=`

```javascript
let score = 10;
```

But JavaScript also gives shortcut assignment operators like `+=` and `-=`

Example:

```javascript
let points = 5;

points += 3; // points = points + 3
console.log(points); // 8

points -= 2; // points = points - 2
console.log(points); // 6
```

These operators help us update values easily.

* * *

## Let’s Try Everything Together

Now let’s perform some operations practically.

```js
let a = 15;
let b = 5;

console.log("Addition:", a + b);
console.log("Subtraction:", a - b);
console.log("Multiplication:", a * b);
console.log("Division:", a / b);
console.log("Remainder:", a % b);
```

Now compare values using both `==` and `===`

```js
let value1 = 10;
let value2 = "10";

console.log(value1 == value2);  // true
console.log(value1 === value2); // false
```

Now write a small condition using logical operators.

```js
let age = 19;
let hasPermission = true;

if (age > 18 && hasPermission) {
  console.log("Access granted");
}
```

Here both conditions must be true for access.

* * *

## Operator Categories Overview

You can think of operators in simple groups:

Arithmetic → Do math  
Comparison → Compare values  
Logical → Combine conditions  
Assignment → Assign or update values

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/98fa3f2d-ae00-4e34-8d57-190cbf918eaa.png align="center")

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/fc824ae3-63f4-4d29-8c29-7045278d7f04.png align="center")

* * *

Operators are the backbone of logic in JavaScript.

Without operators we cannot:

Do calculations  
Compare values  
Write conditions  
Update variables