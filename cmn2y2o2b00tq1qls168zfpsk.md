---
title: "Template Literals in JavaScript"
seoTitle: "Template Literals in JavaScript"
seoDescription: "Template Literals in JavaScript"
datePublished: 2026-03-23T08:49:27.637Z
cuid: cmn2y2o2b00tq1qls168zfpsk
slug: template-literals-in-javascript
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/180aaaf1-a814-4585-be38-8a3933d2865b.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/4d0a9592-7546-421e-903a-69969d298dff.png
tags: programming-blogs, javascript, coding, chaicode

---

When working with strings in JavaScript, many times we need to combine text with variables.

For example showing a user’s name, building messages or printing values.

Before template literals, we used **string concatenation**.

But that can get messy very quickly.

Let’s see why.

* * *

# Problem with Traditional String Concatenation

Suppose we want to print a message like this:

```javascript
const name = "Bruce"
const age = 35

const message = "My name is " + name + " and I am " + age + " years old"

console.log(message)
```

Output:

```plaintext
My name is Bruce and I am 35 years old
```

This works, but notice:

*   lots of `+`
    
*   harder to read
    
*   messy when string becomes longer
    

Now imagine doing this in bigger strings. It becomes difficult to manage.

* * *

# Template Literal Syntax

To solve this problem, JavaScript introduced **template literals**.

Instead of using quotes (`"` or `'`), we use **backticks** (`` ` ``).

Example:

```javascript
const name = "Bruce"
const age = 35

const message = `My name is ${name} and I am ${age} years old`

console.log(message)
```

Much cleaner and easier to read.

* * *

# Embedding Variables

Inside template literals, we can directly insert variables using:

```plaintext
${variable}
```

Example:

```javascript
const hero = "Batman"

console.log(`I am ${hero}`)
```

Output:

```plaintext
I am Batman
```

No need for `+` anymore.

* * *

# Multi line Strings

Another big advantage is **multi line strings**.

With normal strings:

```javascript
const text = "Hello\nWorld"
```

With template literals:

```javascript
const text = `Hello
World`

console.log(text)
```

Output:

```plaintext
Hello
World
```

No need for `\n`, it works naturally.

* * *

# Before vs After

Before (concatenation):

```javascript
const name = "Clark"

const msg = "Hello " + name + ", welcome to Metropolis"
```

After (template literal):

```javascript
const name = "Clark"

const msg = `Hello ${name}, welcome to Metropolis`
```

Cleaner and easier to understand.

* * *

## Visual Idea

Diagram idea: Before vs After

```plaintext
"Hello " + name + "!"   →   `Hello ${name}!`
```

* * *

# Use Cases in Modern JavaScript

Template literals are used everywhere in modern JavaScript.

For example:

**Dynamic messages**

```javascript
const score = 95

console.log(`Your score is ${score}`)
```

**Building HTML (frontend)**

```javascript
const name = "Diana"

const html = `<h1>Hello ${name}</h1>`
```

**Logging values**

```javascript
const item = "Laptop"
const price = 50000

console.log(`Item: ${item}, Price: ${price}`)
```

* * *

# Why Template Literals Are Better

*   More readable
    
*   Less messy
    
*   Easy to write multi line strings
    
*   No need for `+` everywhere
    

* * *

Template literals make working with strings much simpler.

Instead of joining strings manually, we can directly embed values inside them.