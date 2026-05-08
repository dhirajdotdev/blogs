---
title: "Understanding JavaScript Promises with Shaktimaan vs Dr. Jackal"
seoTitle: "Understanding JavaScript Promises with Shaktimaan"
seoDescription: "Understanding JavaScript Promises with Shaktimaan vs Dr. Jackal"
datePublished: 2026-03-01T12:24:15.640Z
cuid: cmm7q25ue00rj2eoigj396i0q
slug: understanding-javascript-promises-with-shaktimaan-vs-dr-jackal
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/6dd08c34-f89c-4f59-b6f7-7a1a890c17ab.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/fb7c1ebc-bcc9-4aa0-8623-394aaea3e044.png
tags: chaiaurcode, chaicode, chaicohort

---

Okay let's understand Promise with Shaktimaan.

In one episode Dr Jackal created a clone of Shaktimaan. The clone looked exactly like the real Shaktimaan but he was working for evil.

People in the city got confused because sometimes Shaktimaan was saving people and sometimes Shaktimaan was destroying things.

Nobody knew which Shaktimaan was real.

People had to wait until the real Shaktimaan defeated the clone.

That waiting for a final result is exactly what a Promise is in JavaScript.

A Promise represents something that will finish in the future but we don't know the result yet.

* * *

## What is a Promise

Think about this situation.

Real Shaktimaan goes to fight Jackal's clone.

Nobody knows what will happen.

People just wait for the result.

Two things can happen:

*   Real Shaktimaan defeats the clone → success
    
*   Clone escapes → failure
    

Until the fight finishes, the result is unknown.

That is exactly what a Promise represents.

A Promise has three states:

*   Pending → fight is still happening
    
*   Fulfilled → Shaktimaan defeated the clone
    
*   Rejected → clone escaped
    

* * *

## Creating a Promise

Let's say Shaktimaan goes to stop Jackal's clone.

Right now we don't know what will happen. The result will come later.

```javascript
const shaktimaanVsClone = new Promise((resolve, reject) => {

  let cloneDefeated = true;

  if (cloneDefeated) {
    resolve("Real Shaktimaan defeated Jackal's clone");
  } else {
    reject("Clone escaped and city is still in danger");
  }

});
```

Here the Promise represents the fight between Shaktimaan and the clone.

When the fight finishes, the Promise gets resolved or rejected.

* * *

## Getting the Result

Once the fight is over, we can handle the result.

```javascript
shaktimaanVsClone
.then(result => {
  console.log(result);
})
.catch(error => {
  console.log(error);
});
```

If Shaktimaan wins:

```plaintext
Real Shaktimaan defeated Jackal's clone
```

If the clone escapes:

```plaintext
Clone escaped and city is still in danger
```

This is how Promise works in real programs. We start something and then wait for the result.

* * *

## Promise.all When Everything Must Succeed

Now imagine Jackal created multiple problems in the city.

*   Clone must be defeated
    
*   Jackal's lab must be destroyed
    
*   Jackal must be captured
    

The city becomes safe only if all problems are solved.

If even one problem remains, danger still exists.

This situation is like Promise.all.

* * *

### Example

```javascript
const cloneDefeated = Promise.resolve("Clone defeated");

const labDestroyed = Promise.resolve("Jackal lab destroyed");

const jackalCaptured = Promise.resolve("Jackal captured");
```

Now we wait for all problems to be solved.

```javascript
Promise.all([
  cloneDefeated,
  labDestroyed,
  jackalCaptured
])
.then(results => {

  console.log("City is safe");
  console.log(results);

})
.catch(() => {

  console.log("City still in danger");

});
```

If all succeed:

```plaintext
City is safe
```

If even one Promise fails, Promise.all fails.

So Promise.all means everything must succeed.

* * *

## Promise.any First Success Is Enough

Now imagine people just want proof that the real Shaktimaan is back.

They don't need everything solved immediately.

As soon as Shaktimaan saves people somewhere, everyone understands the real Shaktimaan is there.

That situation is like Promise.any.

First success is enough.

* * *

### Example

```javascript
const cloneSpotted = Promise.reject("Clone seen destroying buildings");

const realShaktimaanAction =
Promise.resolve("Real Shaktimaan saved people");

const jackalSignalLost =
Promise.reject("Jackal signal lost");
```

Now we wait for the first success.

```javascript
Promise.any([
  cloneSpotted,
  realShaktimaanAction,
  jackalSignalLost
])
.then(result => {

  console.log(result);

});
```

Output:

```plaintext
Real Shaktimaan saved people
```

Promise.any succeeds as soon as one Promise succeeds.

* * *

## Promise.allSettled Full Report of What Happened

After everything ends, Geeta Ji reports what happened in the city.

*   Clone defeated
    
*   Lab destroyed
    
*   Jackal escaped
    

Now people just want to know the results.

They don't care if some failed.

They want the full picture.

That situation is like Promise.allSettled.

* * *

### Example

```javascript
const cloneBattle =
Promise.resolve("Clone defeated");

const jackalEscape =
Promise.reject("Jackal escaped");

const labExplosion =
Promise.resolve("Lab destroyed");
```

Now we check all results.

```javascript
Promise.allSettled([
  cloneBattle,
  jackalEscape,
  labExplosion
])
.then(results => {

  console.log(results);

});
```

Output looks like this:

```plaintext
[
 { status: "fulfilled", value: "Clone defeated" },

 { status: "rejected", reason: "Jackal escaped" },

 { status: "fulfilled", value: "Lab destroyed" }
]
```

Promise.allSettled shows the result of everything.

Success and failure both.

* * *

## Simple Way to Remember

At a very basic level:

Promise → One future result

Promise.all → Wait for everything

Promise.any → First success wins

Promise.allSettled → See all results

* * *

Promise is basically waiting for a future result.

Just like people had to wait to see whether the real Shaktimaan would defeat Jackal's clone.

Sometimes the result is success.

Sometimes the result is failure.

That uncertainty and waiting is what Promise represents in JavaScript.