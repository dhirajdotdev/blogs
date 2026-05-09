---
title: "What is Middleware in Express and How It Works"
seoTitle: "What is Middleware in Express and How It Works"
seoDescription: "What is Middleware in Express and How It Works"
datePublished: 2026-05-09T13:08:15.822Z
cuid: cmoyd0j0s01d22em7dl9ca3f1
slug: what-is-middleware-in-express
tags: express, javascript, nodejs, chaicode

---

When building applications with Express, requests usually do not go directly from:

```txt
Client → Route Handler → Response
```

Instead, requests often pass through multiple intermediate functions first.

Examples:

*   logging requests
    
*   checking authentication
    
*   validating request data
    
*   parsing JSON
    
*   handling errors
    

These intermediate functions are called:

# Middleware

Middleware is one of the most important concepts in Express because almost everything in Express works through middleware internally.

Let’s understand how it actually works.

* * *

# What Is Middleware in Express?

Middleware is a function that runs:

*   between receiving a request
    
*   and sending a response
    

It acts like a checkpoint in the request lifecycle.

Example mental model:

```txt
Request
↓
Middleware
↓
Route Handler
↓
Response
```

Middleware can:

*   modify requests
    
*   modify responses
    
*   stop requests
    
*   continue requests
    
*   execute additional logic
    

* * *

# Middleware as a Request Pipeline

Think of middleware like security checkpoints at an airport.

A request enters the system and passes through multiple checkpoints:

*   logging checkpoint
    
*   authentication checkpoint
    
*   validation checkpoint
    

Each middleware decides:

*   continue request
    
*   reject request
    
*   modify request
    

Only after passing all required checkpoints does the request reach the final route handler.

* * *

# Basic Middleware Example

Example:

```js
const middleware = (req, res, next) => {
  console.log("Middleware Running");

  next();
};
```

* * *

# Understanding Middleware Parameters

Middleware functions usually receive:

```js
(req, res, next)
```

| Parameter | Meaning |
| --- | --- |
| `req` | Incoming request |
| `res` | Outgoing response |
| `next` | Pass control to next middleware |

* * *

# Where Middleware Sits in the Request Lifecycle

Example flow:

```txt
Client sends request
↓
Middleware executes
↓
Another middleware executes
↓
Route handler executes
↓
Response sent back
```

Requests move through a middleware chain.

* * *

# Role of `next()` Function

`next()` is extremely important.

It tells Express:

> “Move to the next middleware or route handler.”

Example:

```js
const logger = (req, res, next) => {
  console.log("Request Received");

  next();
};
```

Without `next()`:

*   request gets stuck
    
*   route handler never runs
    

* * *

# What Happens Without `next()`?

Example:

```js
app.use((req, res) => {
  console.log("Middleware");
});
```

Here:

*   no response sent
    
*   no `next()` called
    

The request hangs forever.

Because Express is waiting for the middleware chain to continue.

* * *

# Using Middleware in Express

Example:

```js
app.use((req, res, next) => {
  console.log("Middleware Executed");

  next();
});
```

`app.use()` registers middleware globally.

This means:

*   every request passes through it
    

* * *

# Middleware Execution Order

Middleware executes in the exact order it is defined.

Example:

```js
app.use((req, res, next) => {
  console.log("First");
  next();
});

app.use((req, res, next) => {
  console.log("Second");
  next();
});
```

Request flow:

```txt
First
Second
```

Order matters a lot in Express applications.

* * *

# Request Pipeline Example

```txt
Request
↓
Logger Middleware
↓
Authentication Middleware
↓
Validation Middleware
↓
Route Handler
↓
Response
```

Each middleware performs one responsibility.

* * *

# Types of Middleware in Express

Express supports multiple middleware types.

* * *

# 1\. Application-Level Middleware

Middleware attached directly to the Express app.

Example:

```js
app.use((req, res, next) => {
  console.log("App Middleware");

  next();
});
```

Runs for matching requests across the application.

* * *

# 2\. Router-Level Middleware

Middleware attached to specific routers.

Example:

```js
router.use((req, res, next) => {
  console.log("Router Middleware");

  next();
});
```

Useful for grouping related routes.

Example:

*   admin routes
    
*   auth routes
    
*   API routes
    

* * *

# 3\. Built-In Middleware

Express already provides built-in middleware.

Example:

```js
app.use(express.json());
```

This middleware:

*   parses JSON request bodies
    
*   makes data available inside `req.body`
    

Without it:

*   JSON request data would not be parsed automatically
    

* * *

# Real-World Middleware Examples

Middleware becomes powerful because it allows reusable request processing.

* * *

# Example 1: Logging Middleware

```js
app.use((req, res, next) => {
  console.log(req.method, req.url);

  next();
});
```

Purpose:

*   track incoming requests
    
*   debugging
    
*   monitoring traffic
    

* * *

# Example 2: Authentication Middleware

```js
const auth = (req, res, next) => {
  const token = req.headers.authorization;

  if (!token) {
    return res.status(401).send("Unauthorized");
  }

  next();
};
```

Purpose:

*   protect private routes
    
*   verify user identity
    

* * *

# Example 3: Request Validation Middleware

```js
const validate = (req, res, next) => {
  if (!req.body.email) {
    return res.status(400).send("Email Required");
  }

  next();
};
```

Purpose:

*   validate incoming request data
    
*   prevent invalid requests
    

* * *

# Middleware Can Modify Requests

Middleware can add data to requests.

Example:

```js
req.user = {
  id: 1
};
```

Now later middleware or routes can access:

```js
req.user
```

This is commonly used in authentication systems.

* * *

# Middleware Can End Requests Early

Middleware does not always continue execution.

Example:

```js
if (!token) {
  return res.status(401).send("Unauthorized");
}
```

Sometimes middleware blocks requests completely.

* * *

# Express Middleware Flow Example

```js
app.use(logger);

app.get("/dashboard", auth, (req, res) => {
  res.send("Dashboard");
});
```

Flow:

```txt
Request
↓
Logger middleware
↓
Auth middleware
↓
Dashboard route
↓
Response
```

* * *

# Why Middleware Is Powerful

Middleware helps:

*   separate concerns
    
*   reuse logic
    
*   keep routes cleaner
    
*   organize backend architecture
    

Instead of repeating logic everywhere, middleware centralizes functionality.

* * *

# Simple Mental Model

Think of middleware like checkpoints on a highway.

Each checkpoint:

*   inspects request
    
*   modifies request
    
*   allows request forward
    
*   or blocks request completely
    

* * *

Middleware is the core mechanism behind Express request processing.

It sits between:

*   incoming request
    
*   final response
    

and allows applications to:

*   process requests step-by-step
    
*   organize reusable logic
    
*   control request flow cleanly
    

The key ideas are:

*   middleware runs in sequence
    
*   execution order matters
    
*   `next()` moves the pipeline forward