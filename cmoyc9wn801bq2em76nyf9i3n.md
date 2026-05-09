---
title: "Creating Routes and Handling Requests with Express"
seoTitle: "Creating Routes and Handling Requests with Express"
seoDescription: "Creating Routes and Handling Requests with Express"
datePublished: 2026-05-09T12:47:33.767Z
cuid: cmoyc9wn801bq2em76nyf9i3n
slug: creating-routes-and-handling-requests-with-express
tags: express, server, nodejs, chaicode

---

When people first build servers using Node.js, they usually start with the built-in `http` module.

It works, but very quickly the code becomes difficult to manage.

Example raw Node.js server:

```js
const http = require("http");

const server = http.createServer((req, res) => {
  if (req.url === "/" && req.method === "GET") {
    res.end("Home Page");
  } else if (req.url === "/about" && req.method === "GET") {
    res.end("About Page");
  } else {
    res.end("404 Not Found");
  }
});

server.listen(3000);
```

Even with just two routes, the logic already starts becoming repetitive.

That’s why Express.js became popular.

* * *

# What Is Express.js?

Express.js is a lightweight web framework built on top of Node.js.

It simplifies:

*   routing
    
*   request handling
    
*   responses
    
*   middleware
    
*   server structure
    

Instead of manually handling low-level HTTP logic, Express provides cleaner APIs.

* * *

# Why Express Simplifies Node.js Development

Without Express:

*   manual route checking
    
*   manual request parsing
    
*   repetitive boilerplate
    
*   harder scalability
    

With Express:

*   cleaner route definitions
    
*   organized structure
    
*   simpler request handling
    
*   faster backend development
    

It reduces complexity while still using Node.js underneath.

* * *

# Installing Express

Inside your project:

```bash
npm install express
```

This installs the Express framework into your application.

* * *

# Creating Your First Express Server

Create a file:

```txt
server.js
```

Add:

```js
const express = require("express");

const app = express();

app.listen(3000, () => {
  console.log("Server running on port 3000");
});
```

* * *

# Understanding the Code

* * *

# Step 1: Import Express

```js
const express = require("express");
```

This imports the Express library.

* * *

# Step 2: Create App Instance

```js
const app = express();
```

`app` becomes your Express application.

This object manages:

*   routes
    
*   requests
    
*   responses
    
*   middleware
    

* * *

# Step 3: Start Server

```js
app.listen(3000)
```

This starts the server on port `3000`.

* * *

# Running the Server

Run:

```bash
node server.js
```

Output:

```txt
Server running on port 3000
```

* * *

# What Are Routes?

Routes define:

*   which URL was requested
    
*   which HTTP method was used
    
*   what response should be sent
    

Example:

```txt
GET /users
POST /login
```

Each route handles specific application behavior.

* * *

# Handling GET Requests

GET requests are commonly used for:

*   fetching data
    
*   loading pages
    
*   retrieving resources
    

Example:

```js
app.get("/", (req, res) => {
  res.send("Welcome Home");
});
```

Now visiting:

```txt
http://localhost:3000/
```

returns:

```txt
Welcome Home
```

* * *

# Understanding Route Handler Parameters

Example:

```js
(req, res) => {}
```

These represent:

| Parameter | Meaning |
| --- | --- |
| `req` | Incoming request |
| `res` | Outgoing response |

* * *

# What Is Inside `req`?

The request object contains:

*   headers
    
*   query params
    
*   URL params
    
*   request body
    
*   HTTP method
    

Basically everything sent by the client.

* * *

# What Is Inside `res`?

The response object helps send data back.

Examples:

*   text
    
*   JSON
    
*   HTML
    
*   status codes
    

* * *

# Sending Responses

Simple text response:

```js
res.send("Hello");
```

JSON response:

```js
res.json({
  success: true
});
```

Express automatically handles many response details internally.

* * *

# Handling Multiple Routes

Example:

```js
app.get("/", (req, res) => {
  res.send("Home");
});

app.get("/about", (req, res) => {
  res.send("About");
});
```

Each route responds differently depending on the requested URL.

* * *

# Handling POST Requests

POST requests are commonly used for:

*   form submission
    
*   login
    
*   registration
    
*   sending data to server
    

Example:

```js
app.post("/login", (req, res) => {
  res.send("Login Request Received");
});
```

Now Express listens specifically for:

```txt
POST /login
```

* * *

# GET vs POST

| Method | Purpose |
| --- | --- |
| GET | Retrieve data |
| POST | Send data to server |

* * *

# Request → Route → Response Flow

Here’s the mental model:

```txt
Client sends request
↓
Express checks matching route
↓
Route handler executes
↓
Response returned
```

* * *

# How Express Finds Routes

Example request:

```txt
GET /about
```

Express:

1.  checks route list
    
2.  finds matching method + path
    
3.  executes corresponding handler
    

If no route matches:

*   request remains unhandled
    
*   often returns 404
    

* * *

# Why Express Routing Feels Simpler

Compare raw Node.js:

```js
if (req.url === "/about")
```

vs Express:

```js
app.get("/about")
```

Express removes repetitive low-level checks and creates cleaner application structure.

* * *

# Example Small Express App

```js
const express = require("express");

const app = express();

app.get("/", (req, res) => {
  res.send("Home Page");
});

app.get("/about", (req, res) => {
  res.send("About Page");
});

app.post("/login", (req, res) => {
  res.send("Login Successful");
});

app.listen(3000, () => {
  console.log("Server Started");
});
```

This tiny application already demonstrates:

*   routing
    
*   request handling
    
*   responses
    
*   multiple HTTP methods
    

* * *

# Simple Mental Model

Think of Express routes like reception desks.

Each route says:

> “If someone comes to this URL using this method, handle them here.”

* * *

# Express Request Lifecycle

```txt
Browser/API sends request
↓
Express receives request
↓
Matching route found
↓
Handler function runs
↓
Response sent back
```

* * *

Express simplifies backend development by abstracting away repetitive HTTP handling logic.

Instead of manually checking:

*   URLs
    
*   request methods
    
*   responses
    

Express provides a clean routing system where:

*   routes define behavior
    
*   handlers process requests
    
*   responses return data
    

Once you understand:

*   routes
    
*   request objects
    
*   response objects
    
*   HTTP methods
    

building APIs with Express becomes much more intuitive.