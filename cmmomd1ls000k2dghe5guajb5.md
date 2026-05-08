---
title: "Control Flow in JavaScript: If, Else and Switch Explained"
seoTitle: "Control Flow in JavaScript: If, Else, and Switch Explained"
seoDescription: "Control Flow in JavaScript: If, Else, and Switch Explained"
datePublished: 2026-03-13T08:12:49.892Z
cuid: cmmomd1ls000k2dghe5guajb5
slug: control-flow-in-javascript-if-else-and-switch-explained
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/950b71b6-14c2-461b-89f9-316cd7fdfd04.png
ogImage: https://cdn.hashnode.com/uploads/og-images/69513de35d3cf3dcde6a6e95/97fb3b6c-f56e-4460-91e2-3eb077101959.png
tags: javascript, javascript-framework, chaicode

---

When we write programs, not every line of code should run every time.

Sometimes the program needs to **make decisions**.

Think about a game.

*   If a player has enough health, they continue playing.
    
*   If the health reaches zero, the game is over.
    
*   If the player collects a special item, they unlock a new ability.
    

The game constantly checks conditions and decides what should happen next.

This decision making is called **control flow**.

Control flow controls **which part of the program runs based on conditions**.

In JavaScript we mainly use:

*   `if`
    
*   `if-else`
    
*   `else if`
    
*   `switch`
    

Let’s understand them using simple game examples.

* * *

# The `if` Statement

The `if` statement runs code **only if a condition is true**.

Imagine a player trying to enter a special level that requires at least **100 coins**.

```javascript
let coins = 120

if (coins >= 100) {
  console.log("Level unlocked")
}
```

Output:

```plaintext
Level unlocked
```

If the player has enough coins, the level unlocks.

If not, nothing happens.

* * *

# The `if-else` Statement

Sometimes we want **two possible outcomes**.

Example: checking player health.

```javascript
let health = 0

if (health > 0) {
  console.log("Player is still alive")
} else {
  console.log("Game Over")
}
```

Output:

```plaintext
Game Over
```

Here the game checks the condition.

If true → player continues  
If false → game ends

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/edc148d7-3a9e-4157-88c3-12eda525c259.png align="center")

* * *

# The `else if` Ladder

Games often have **multiple conditions**.

Example: assigning player rank based on score.

```javascript
let score = 850

if (score >= 1000) {
  console.log("Legend Rank")
}
else if (score >= 800) {
  console.log("Diamond Rank")
}
else if (score >= 500) {
  console.log("Gold Rank")
}
else {
  console.log("Bronze Rank")
}
```

Output:

```plaintext
Diamond Rank
```

The program checks conditions **from top to bottom**.

As soon as one condition is true, the rest are skipped.

* * *

# The `switch` Statement

Sometimes we check **specific values instead of ranges**.

Example: choosing a character class in a game.

```javascript
let character = "mage"

switch (character) {
  case "warrior":
    console.log("Strong attack and high defense")
    break

  case "mage":
    console.log("Powerful magic abilities")
    break

  case "archer":
    console.log("Long range attacks")
    break

  default:
    console.log("Unknown character")
}
```

Output:

```plaintext
Powerful magic abilities
```

The `break` statement stops execution once a match is found.

Without `break`, the next cases would also run.

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/a35dd186-80bc-4016-8102-93f8bc89a9af.png align="center")

* * *

# When to Use `switch` vs `if-else`

Both structures help us make decisions.

Use **if-else** when checking conditions or ranges.

Example:

```plaintext
score >= 800
health > 0
coins >= 100
```

Use **switch** when checking **specific values**.

Example:

```plaintext
character type
weapon type
game difficulty
```

* * *

# Examples

Check if a player's score is positive, negative or zero.

```javascript
let score = -10

if (score > 0) {
  console.log("Positive score")
}
else if (score < 0) {
  console.log("Negative score")
}
else {
  console.log("Score is zero")
}
```

Now choose a game difficulty using `switch`.

```javascript
let difficulty = "hard"

switch (difficulty) {
  case "easy":
    console.log("Enemies are weaker")
    break

  case "medium":
    console.log("Balanced difficulty")
    break

  case "hard":
    console.log("Enemies are stronger")
    break

  default:
    console.log("Unknown difficulty")
}
```

In the first example we used **if-else** because we are checking conditions.

In the second example we used **switch** because we are checking specific values.

* * *

Control flow is one of the most important concepts in programming.

It allows programs to **react to different situations**.