---
title: "URL Parameters vs Query Strings in Express.js"
seoDescription: "URL Parameters vs Query Strings in Express.js"
datePublished: 2026-05-09T11:19:20.631Z
cuid: cmoy94gfo017y2em74y3b19lt
slug: url-parameters-vs-query-strings
tags: express, javascript, query, url, chaicode

---

When building APIs in Express.js, you’ll constantly see URLs like these:

```txt
/users/42
```

and:

```txt
/products?category=mobile&sort=price
```

Both send data through the URL.

But they solve completely different problems.

Understanding the difference between:

*   URL parameters
    
*   query strings
    

is important because it affects:

*   route design
    
*   API readability
    
*   filtering logic
    
*   resource identification
    

Let’s break them down properly.

* * *

# What Are URL Parameters?

URL parameters are dynamic values inside the route path itself.

Example:

```txt
/users/42
```

Here:

*   `42` is a URL parameter
    
*   it usually represents a specific resource identifier
    

* * *

# Why URL Parameters Exist

Applications often need routes that work dynamically.

Instead of creating:

```txt
/users/1
/users/2
/users/3
```

Express allows placeholders.

Example:

```js
app.get("/users/:id", (req, res) => {
  res.send(req.params.id);
});
```

Now:

*   `/users/1`
    
*   `/users/42`
    
*   `/users/999`
    

all match the same route.

* * *

# Accessing Params in Express

Express stores route parameters inside:

```js
req.params
```

Example:

```js
app.get("/users/:id", (req, res) => {
  console.log(req.params);
});
```

Request:

```txt
/users/42
```

Output:

```js
{
  id: "42"
}
```

* * *

# URL Params Represent Identity

This is the most important mental model.

URL params usually identify:

*   a specific user
    
*   a specific product
    
*   a specific post
    
*   a specific resource
    

Examples:

```txt
/users/42
/products/10
/posts/99
```

These routes point to exact resources.

* * *

# What Are Query Strings?

Query strings are extra key-value pairs added after `?` in a URL.

Example:

```txt
/products?category=mobile&sort=price
```

Here:

*   `category=mobile`
    
*   `sort=price`
    

are query parameters.

* * *

# Why Query Strings Exist

Sometimes we don’t want a specific resource.

Instead, we want to:

*   filter data
    
*   sort results
    
*   paginate
    
*   search
    
*   modify behavior
    

Query strings solve this.

* * *

# Accessing Query Strings in Express

Express stores query parameters inside:

```js
req.query
```

Example:

```js
app.get("/products", (req, res) => {
  console.log(req.query);
});
```

Request:

```txt
/products?category=mobile&sort=price
```

Output:

```js
{
  category: "mobile",
  sort: "price"
}
```

* * *

# Query Strings Represent Filters or Modifiers

This is the key difference.

Query strings usually describe:

*   how data should be filtered
    
*   how results should be sorted
    
*   optional behavior changes
    

Examples:

```txt
/products?category=laptop
/users?page=2
/search?q=react
```

These are not identifying a single resource.

They are modifying the request behavior.

* * *

# URL Structure Breakdown

Example:

```txt
/users/42/orders?status=completed&page=2
```

Breakdown:

| Part | Meaning |
| --- | --- |
| `/users` | resource |
| `42` | URL parameter |
| `/orders` | nested resource |
| `status=completed` | query string |
| `page=2` | query string |

* * *

# URL Params vs Query Strings

| Feature | URL Params | Query Strings |
| --- | --- | --- |
| Position | Inside route path | After `?` |
| Purpose | Identify resource | Filter/modify request |
| Required Usually? | Often yes | Usually optional |
| Accessed Using | `req.params` | `req.query` |
| Example | `/users/42` | `/users?page=2` |

* * *

# Real-World Examples

* * *

# Example 1: User Profile

```txt
/users/42
```

Why param?

Because:

*   user `42` is a specific identity
    
*   route points to one exact resource
    

* * *

# Example 2: Product Search

```txt
/products?category=shoes&sort=price
```

Why query?

Because:

*   category is a filter
    
*   sorting changes response behavior
    
*   results may vary
    

* * *

# Example 3: Pagination

```txt
/posts?page=3&limit=10
```

These values modify:

*   which results appear
    
*   how many results are returned
    

Not resource identity.

* * *

# Combining Params and Query Strings

Both can be used together.

Example:

```txt
/users/42/posts?published=true
```

Here:

*   `42` identifies the user
    
*   `published=true` filters posts
    

This is very common in REST APIs.

* * *

# Important API Design Insight

A good rule:

## Use Params For Identity

Examples:

*   user ID
    
*   post ID
    
*   product ID
    

* * *

## Use Query Strings For Optional Behavior

Examples:

*   search
    
*   sorting
    
*   filtering
    
*   pagination
    

* * *

# Common Mistake

Bad API design:

```txt
/getUser?id=42
```

Better:

```txt
/users/42
```

Because:

*   the resource identity belongs in the path
    
*   filters/modifiers belong in query strings
    

Cleaner URLs improve API readability.

* * *

# Simple Mental Model

## URL Params

> “Which exact resource do you want?”

* * *

## Query Strings

> “How should the result be modified?”

* * *

URL parameters and query strings may look similar, but they serve very different purposes.

*   URL params identify resources
    
*   Query strings modify requests
    

In Express:

*   `req.params` handles route identifiers
    
*   `req.query` handles filters and modifiers