---
title: "String Polyfills and Common Interview Methods in JavaScript"
seoTitle: "String Polyfills and Common Interview Methods in JavaScript"
seoDescription: "String Polyfills and Common Interview Methods in JavaScript"
datePublished: 2026-03-24T12:17:05.029Z
cuid: cmn4kxiwz01mh2flk79nyan76
slug: string-polyfills-and-common-interview-methods-in-javascript
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/8ca4b1dd-4f0a-4866-8893-f836e2ba9e20.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/b5e7dad2-e212-4ddb-bada-c9e254646069.png
tags: programming-blogs, javascript, polyfills, chaicode

---

In JavaScript we use string methods all the time.

`includes()`, `slice()`, `toUpperCase()` we just use them and move on.

But in interviews or real problem solving, you might get asked:

how does this work internally ?

can you implement it yourself ?

That’s where polyfills come in.

In this blog I’ll share how I understand string methods, how they actually work behind the scenes and how to approach them in interviews.

* * *

## What string methods are

String methods are just functions attached to strings.

```javascript
"hello".toUpperCase()
```

Looks simple.

But internally it’s just:

loop over characters --> change something --> return new string

Nothing magical.

* * *

## How to think about it

Every string method is basically:

input string --> process --> output string

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/8b1eb99f-4c17-41c8-9ac2-3c740690fe34.png align="center")

* * *

## Why developers write polyfills

Polyfill = writing your own version of built in method.

Why?

*   to understand how it works
    
*   interview questions
    
*   improve logic building
    

So it’s less about code, more about thinking.

* * *

## Important: where methods actually live

All string methods come from:

```javascript
String.prototype
```

So when you do:

```javascript
"hello".includes("he")
```

it’s actually using `String.prototype.includes`

So real polyfills are written like:

adding your own method to prototype

* * *

## Polyfill example (includes)

```javascript
String.prototype.myIncludes = function (word) {
  const str = this

  for (let i = 0; i <= str.length - word.length; i++) {
    let match = true

    for (let j = 0; j < word.length; j++) {
      if (str[i + j] !== word[j]) {
        match = false
        break
      }
    }

    if (match) return true
  }

  return false
}
```

Usage:

```javascript
"hello".myIncludes("he") // true
```

What’s happening:

we slide over string match character by character

* * *

## Polyfill example (startsWith)

```javascript
String.prototype.myStartsWith = function (word) {
  const str = this

  for (let i = 0; i < word.length; i++) {
    if (str[i] !== word[i]) {
      return false
    }
  }

  return true
}
```

* * *

## Why `this` is important here

Inside prototype:

`this` = the string calling the method

```javascript
"hello".myIncludes("he")
```

`this` = `"hello"`

* * *

## Implementing simple string utilities

Most string utilities are just loops.

### Reverse string

```javascript
function reverse(str) {
  let res = ""

  for (let i = str.length - 1; i >= 0; i--) {
    res += str[i]
  }

  return res
}
```

* * *

### Check palindrome

```javascript
function isPalindrome(str) {
  return str === reverse(str)
}
```

* * *

### Count characters

```javascript
function countChars(str) {
  const map = {}

  for (let char of str) {
    map[char] = (map[char] || 0) + 1
  }

  return map
}
```

* * *

## Common interview mindset

When interviewer asks:

“implement includes / slice / reverse”

They are checking:

*   can you break problem
    
*   can you use loops
    
*   can you think step by step
    

Not memorization.

* * *

## Polyfill behavior

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/650b8e92-240b-4583-a2fe-b49c4b421d92.png align="center")

* * *

## Importance of understanding built in behavior

If you only use methods:

you know usage

If you understand internals:

you know control

That helps in:

*   interviews
    
*   debugging
    
*   writing custom logic
    

* * *

## One important note

In real projects:

don’t modify `String.prototype`

But for:

learning, interviews

this is exactly what you should do.

* * *

String methods are simple once you break them.

They are just loops + conditions.

Polyfills help you see that clearly.