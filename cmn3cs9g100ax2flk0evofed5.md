---
title: "Map and Set in JavaScript"
seoTitle: "Map and Set in JavaScript"
seoDescription: "Map and Set in JavaScript"
datePublished: 2026-03-23T15:41:16.372Z
cuid: cmn3cs9g100ax2flk0evofed5
slug: map-and-set-in-javascript
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/2709bb04-c028-43bd-9374-0a792fdcf97c.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/315b8210-a02e-484b-8679-98ad1e9e3d37.png
tags: programming-blogs, javascript, chaicode

---

In JavaScript, we usually use objects and arrays for most things.

Objects for key value data, Arrays for lists

But sometimes these are not enough.

Like:

*   you want keys that are not just strings
    
*   you want to store unique values only
    
*   you want better control over data
    

That’s where Map and Set come into the picture.

In this blog I will share how I understand Map and Set and when I actually use them.

* * *

## Problem with objects and arrays

Before jumping into Map and Set, let’s see the problem.

### Objects problem

```javascript
const obj = {}

obj[1] = "one"
obj["1"] = "string one"

console.log(obj)
```

Output:

```plaintext
{ '1': 'string one' }
```

Here:

number `1` and string `"1"` become same key

So object forces keys to be strings.

* * *

### Arrays problem

```javascript
const arr = [1, 2, 2, 3]
```

Here:

duplicates are allowed

Sometimes we don’t want that.

* * *

## What is Map

Map is like an object but better.

It stores data in key value pairs, but:

keys can be anything (number, string, object, function)

Example:

```javascript
const map = new Map()

map.set(1, "one")
map.set("1", "string one")

console.log(map)
```

```plaintext
Map(1) { 1 => 'one' }
Map(2) { 1 => 'one', '1' => 'string one' }
```

Here both keys are different.

So:

Map does not convert keys to string

* * *

## How Map feels

Think like:

Map = advanced key value storage

* * *

## Getting values from Map

```js
map.get(1)       // "one"
map.get("1")     // "string one"
```

* * *

## Map key value visual

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/a306a392-2c55-4ba9-9e91-3e424a1bff40.png align="center")

* * *

## What is Set

Set is used to store only unique values.

That’s its main job.

Example:

```javascript
const set = new Set([1, 2, 2, 3])

console.log(set)
```

Output:

```id="y7d2hb"
{1, 2, 3}
```

duplicates automatically removed

* * *

## How Set feels

Set = unique collection

No duplicates allowed

* * *

## Adding values in Set

```javascript
const set = new Set()

set.add(1)
set.add(2)
set.add(2)

console.log(set)
```

Still:

```id="p0v9xz"
{1, 2}
```

* * *

## Set visual

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/3e685d50-41fe-4e1d-9151-d60704414901.png align="center")

* * *

## Map vs Object

Both store key value, but:

Object:

*   keys become string
    
*   limited flexibility
    

Map:

*   keys can be anything
    
*   keeps original type
    
*   better for dynamic data
    

Simple line:

Object = basic

Map = flexible

* * *

## Set vs Array

Array:

*   allows duplicates
    
*   used for ordered list
    

Set:

*   only unique values
    
*   removes duplicates automatically
    

Simple line:

Array = list

Set = unique list

* * *

## When to use Map

Use Map when:

*   keys are not just strings
    
*   you need key value structure
    
*   keys can be objects or numbers
    
*   you want more control than object
    

Example use case:

```javascript
const user1 = { name: "A" }
const user2 = { name: "B" }

const map = new Map()

map.set(user1, "data1")
map.set(user2, "data2")
```

* * *

## When to use Set

Use Set when:

*   you want unique values
    
*   removing duplicates
    
*   checking if value already exists
    

Example:

```javascript
const nums = [1, 2, 2, 3]

const unique = new Set(nums)

console.log([...unique])
```

* * *

Map and Set are not used everywhere, but when needed, they make things much cleaner.

Map solves key limitations of objects

Set solves duplicate problems of arrays