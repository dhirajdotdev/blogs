---
title: "JavaScript Modules: Import and Export Explained"
seoTitle: "JavaScript Import and Export Explained"
seoDescription: "JavaScript Import and Export Explained"
datePublished: 2026-03-23T08:42:19.875Z
cuid: cmn2xti0200ta1qlsgic8dt5r
slug: javascript-modules-import-and-export-explained
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/41f30204-b6a7-4a2d-bd3b-9f5119ad8531.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/338e3e19-bebe-430a-be34-7801aa120c04.png
tags: programming-blogs, javascript, coding, chaicode

---

When we start writing small programs, everything usually goes inside a single file.

That works fine in the beginning.

But as the project grows, we start adding more functions, more logic and more features.

Slowly, one file becomes very big and difficult to manage.

```javascript
function add(a, b) { return a + b }
function multiply(a, b) { return a * b }
function divide(a, b) { return a / b }
// many more functions...
```

Now everything is mixed in one place.

It becomes harder to:

*   find code
    
*   reuse code
    
*   maintain code
    

This is where **modules** come in.

* * *

# Why Modules Are Needed

Modules help us **split code into multiple files**.

Each file can handle a specific responsibility.

For example:

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/f67ceb51-fb5f-4322-be19-1975779db511.png align="center")

Instead of writing everything in one file, we organize code into smaller pieces.

This makes the code easier to read and manage.

* * *

# Exporting Code

To use code from one file in another, we need to **export** it.

Example: `math.js`

```javascript
export function add(a, b) {
  return a + b
}

export function multiply(a, b) {
  return a * b
}
```

Here we are exporting two functions.

Now these functions can be used in other files.

* * *

# Importing Code

To use exported functions, we **import** them.

Example: `app.js`

```javascript
import { add, multiply } from "./math.js"

console.log(add(2, 3))
console.log(multiply(4, 5))
```

Now `app.js` can use functions defined in `math.js`.

* * *

# Default vs Named Exports

There are two ways to export things.

## Named Export

This is what we saw earlier.

```javascript
export function add(a, b) {
  return a + b
}
```

Importing:

```javascript
import { add } from "./math.js"
```

We must use the **same name** while importing.

* * *

## Default Export

A file can also have one **default export**.

```javascript
export default function subtract(a, b) {
  return a - b
}
```

Importing:

```javascript
import subtract from "./math.js"
```

Here we can use **any name** while importing.

* * *

# Module Flow

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/8b3336fc-95e3-4fb8-83cd-a462491d71c4.png align="center")

Data flows from one file to another using import/export.

* * *

# Benefits of Modular Code

Using modules improves code in many ways.

**Better organization** Code is split into smaller files.

**Reusability** Functions can be reused in different files.

**Maintainability** Changes in one module don’t affect everything.

**Readability** Each file has a clear purpose.

* * *

# Small Example

`math.js`

```javascript
export function square(num) {
  return num * num
}
```

`app.js`

```javascript
import { square } from "./math.js"

console.log(square(5))
```

Output

```id="6phu3y"
25
```

* * *

As applications grow, keeping everything in one file becomes difficult.

Modules help us break code into smaller, manageable pieces.

Using **export and import**, we can share code between files and build better structured applications.