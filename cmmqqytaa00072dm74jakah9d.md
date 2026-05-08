---
title: "Understanding Objects in JavaScript"
seoTitle: "Understanding Objects in JavaScript"
seoDescription: "Understanding Objects in JavaScript"
datePublished: 2026-03-14T19:57:16.357Z
cuid: cmmqqytaa00072dm74jakah9d
slug: understanding-objects-in-javascript
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/61f43c83-601f-46ab-b17f-4168e3d99bf3.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/2c7e1033-6e52-4371-a4f4-fbab16554646.png
tags: software-development, javascript, coding, objects, chaicode

---

When we write programs, we often need to store related pieces of information together.

For example imagine we want to store details about a person like their name, age and city.

We could store them in separate variables, but that quickly becomes messy.

```javascript
const name = "Bruce Wayne"
const age = 35
const city = "Gotham"
```

These values belong together, but they are scattered.

To organize related data in a better way, JavaScript provides **objects**.

An object lets us store multiple values inside a single structure.

You can think of an object as a collection of **key value pairs**.

* * *

# What an Object Looks Like

Here is a simple example.

```javascript
const hero = {
  name: "Bruce Wayne",
  heroName: "Batman",
  city: "Gotham"
}
```

Here:

*   `name`, `heroName`, and `city` are **keys**
    
*   `"Bruce Wayne"`, `"Batman"`, `"Gotham"` are **values**
    

So the object stores information like this:

```plaintext
name → Bruce Wayne
heroName → Batman
city → Gotham
```

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/11c243f0-1c99-4988-88e5-32636aef2a72.png align="center")

* * *

# Creating Objects

Objects are created using **curly braces** `{}`.

Example:

```javascript
const hero = {
  name: "Clark Kent",
  heroName: "Superman",
  city: "Metropolis"
}
```

Each property is written as:

```plaintext
key: value
```

* * *

# Accessing Object Properties

There are two ways to access values inside an object.

## Dot Notation

This is the most common way.

```javascript
console.log(hero.name)
console.log(hero.heroName)
```

Output

```plaintext
Clark Kent
Superman
```

* * *

## Bracket Notation

Another way is using square brackets.

```javascript
console.log(hero["city"])
```

Output

```plaintext
Metropolis
```

Both ways work the same, but bracket notation can be useful when property names are dynamic.

* * *

# Updating Object Properties

We can update values inside an object easily.

```javascript
hero.city = "Smallville"

console.log(hero.city)
```

Output

```plaintext
Smallville
```

The value simply changes.

* * *

# Adding New Properties

Objects are flexible, so we can add new properties anytime.

```javascript
hero.power = "Flight"

console.log(hero)
```

Now the object contains a new property.

* * *

# Deleting Properties

If we want to remove a property, we can use the `delete` keyword.

```javascript
delete hero.city

console.log(hero)
```

The `city` property will be removed from the object.

* * *

# Looping Through Object Keys

Sometimes we want to go through all properties inside an object.

JavaScript provides a simple loop for this.

```javascript
for (const key in hero) {
  console.log(key, hero[key])
}
```

Example output

```plaintext
name Clark Kent
heroName Superman
power Flight
```

The loop goes through every key and prints the value.

* * *

# Array vs Object

Sometimes beginners confuse arrays and objects.

Arrays store values using **index numbers**.

Example:

```javascript
const heroes = ["Batman", "Superman", "Wonder Woman"]
```

Accessing array values:

```javascript
heroes[0]
heroes[1]
```

Objects store values using **keys instead of indexes**.

Example:

```javascript
const hero = {
  name: "Diana Prince",
  heroName: "Wonder Woman"
}
```

Accessing object values:

```javascript
hero.name
hero.heroName
```

**Array vs Object**

```plaintext
Array
["Batman", "Superman", "Wonder Woman"]
   0          1           2

Object
name → Diana Prince
heroName → Wonder Woman
```

* * *

# Example: Student Object

Let’s create an object representing a student.

```javascript
const student = {
  name: "Barry Allen",
  age: 24,
  course: "Forensic Science"
}
```

Update a property.

```javascript
student.age = 25
```

Now print all keys and values.

```javascript
for (const key in student) {
  console.log(key, student[key])
}
```

Output

```plaintext
name Barry Allen
age 25
course Forensic Science
```

* * *

Objects are one of the most important data structures in JavaScript.

They allow us to group related information together using key value pairs.

With objects we can store data, update values, add new properties, delete properties and loop through them easily.