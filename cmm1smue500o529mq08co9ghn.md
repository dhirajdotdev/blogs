---
title: "Understanding Variables and Data Types in JavaScript"
seoTitle: "JavaScript Variables and Data Types: A Beginner's Guide with"
seoDescription: "Learn JavaScript variables and basic data types (var, let, const) with simple explanations and examples to help beginners write cleaner, dynamic code."
datePublished: 2026-02-25T08:49:42.752Z
cuid: cmm1smue500o529mq08co9ghn
slug: understanding-variables-and-data-types
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/a5201915-8b24-491c-aa6e-ce2b4d148dd5.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/53408029-312c-4ecb-ab15-1d3bcb4d3a12.png
tags: javascript, chaiaurcode, chaicode, dhirajdotdev

---

When we start learning JavaScript, one of the first things we hear about is variables.

But what exactly is a variable and why do we need it?

If programming is about working with data, then variables are how we store that data. Without variables, we cannot build logic, cannot store user input and cannot create dynamic behavior.

In this blog, I will share my understanding of variables and basic data types in JavaScript in a simple way

* * *

## What is a Variable

Think of a variable like a box.

You take a box, write a name on it and put something inside it. Later, whenever you need that thing, you just use the box name.

In JavaScript, a variable is a named container that stores a value.

Example :

```javascript
let name = "Dhiraj";
```

Here :  
`name` is the box  
"Dhiraj" is the value inside

Now whenever we use `name`, JavaScript remembers the value stored inside it.

* * *

## Why Variables are Needed

Without variables, code becomes repetitive and hard to manage.

For example :

```javascript
console.log("Dhiraj");
console.log("Dhiraj");
console.log("Dhiraj");
```

If the name changes, you must change it everywhere.

But with variables :

```javascript
let name = "Dhiraj";

console.log(name);
console.log(name);
console.log(name);
```

Now you change it once and everything updates.

Variables help us :  
Store data  
Reuse values  
Update values  
Keep code clean

* * *

## Declaring Variables in JavaScript

In JavaScript, we can declare variables using :

*   var
    
*   let
    
*   const
    

Example :

```javascript
var city = "Kolkata";
let age = 20;
const country = "India";
```

All three create variables, but they behave differently.

* * *

## Difference Between var, let and const

### var

This is the older way of declaring variables.  
It still works, but in modern JavaScript we mostly avoid using `var`.

* * *

### let

`let` allows you to change the value later.

```javascript
let score = 10;
score = 20;

console.log(score); // 20
```

The value was successfully updated.

* * *

### const

`const` means constant.

You cannot reassign the value after declaring it.

```javascript
const pi = 3.14;
pi = 3.14159; // Error
```

JavaScript will throw an error because we tried to change a constant value.

* * *

### Simple Rule

Use `const` by default.  
Use `let` when value needs to change.  
Avoid `var` in modern code.

* * *

## Primitive Data Types

Variables store values and those values have types.

Let’s look at the most basic primitive data types.

* * *

### String

Used to store text.

```javascript
let name = "Dhiraj";
```

Examples :  
Name  
City  
Email

Text must be written inside quotes.

* * *

### Number

Used to store numbers.

```javascript
let age = 20;
```

Examples :  
Age  
Price  
Score

* * *

### Boolean

Used to store true or false.

```javascript
let isStudent = true;
```

Examples :  
isLoggedIn  
hasAccess  
isAdmin

Boolean values are often used in conditions.

* * *

### undefined

If a variable is declared but not assigned a value, it becomes undefined.

```js
let result;
console.log(result); // undefined
```

This means the variable exists, but no value is assigned yet.

* * *

### null

Null means intentionally empty.

```js
let selectedUser = null;
```

Difference :  
undefined → not assigned  
null → intentionally empty

* * *

## Let’s Store Real Data

Now let’s declare some real variables.

```javascript
let name = "Dhiraj";
let age = 20;
let isStudent = true;
const country = "India";
```

Now print them :

```javascript
console.log("Name:", name);
console.log("Age:", age);
console.log("Is Student:", isStudent);
console.log("Country:", country);
```

Output will be :

```plaintext
Name: Dhiraj
Age: 20
Is Student: true
Country: India
```

* * *

## Changing Values

Now let’s update some values.

```javascript
age = 21;
isStudent = false;

console.log("Updated Age:", age); // 21
console.log("Updated Is Student:", isStudent); // false
```

This works because we used `let`.

Now try changing the constant:

```javascript
country = "USA";
```

You will get an error :

```plaintext
TypeError: Assignment to constant variable.
```

That’s the difference in action.

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/ef8d7459-4931-40b5-a47a-20e04745bb7a.png align="center")

* * *

## What is Scope

Scope means where a variable can be accessed.

Think of scope like a room.

If you create a variable inside a room, you can use it inside that room. Outside that room, it does not exist.

Example :

```javascript
{
  let message = "Hello";
  console.log(message); // Works
}

console.log(message); // Error
```

`message` was declared inside the block. Outside, it is not accessible.

So scope controls visibility of variables.

just remember :  
`let` and `const` are block-scoped.

* * *

## Quick Comparison

At a very high level :

*   var → old way
    
*   let → value can change
    
*   const → value cannot be reassigned
    

Most of the time you will use `let` and `const`.

* * *

Variables and data types are the foundation of JavaScript.