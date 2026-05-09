---
title: "Setting Up Your First Node.js Application Step-by-Step"
seoTitle: "Setting Up Your First Node.js Application Step-by-Step"
seoDescription: "Setting Up Your First Node.js Application Step-by-Step"
datePublished: 2026-05-09T12:26:08.870Z
cuid: cmoybid7o01am2em72zxi83be
slug: setting-up-your-first-node-js-application
tags: javascript, server, nodejs, chaicode

---

When people first hear about Node.js, they usually think:

> “It lets JavaScript run outside the browser.”

And that’s exactly what it does.

Node.js is a JavaScript runtime that allows you to:

*   build servers
    
*   create APIs
    
*   work with files
    
*   build backend applications
    

Before building large applications, it’s important to understand how a basic Node.js setup works from the ground up.

This article walks through:

*   installing Node.js
    
*   verifying installation
    
*   understanding the Node REPL
    
*   running JavaScript files
    
*   creating your first server
    

without using any frameworks.

* * *

# What Is Node.js?

Normally, JavaScript runs inside browsers.

Example:

*   Chrome
    
*   Firefox
    
*   Edge
    

Node.js allows JavaScript to run directly on your computer using the V8 JavaScript engine.

This means JavaScript can now:

*   access files
    
*   create servers
    
*   interact with operating system resources
    

That’s what makes backend development possible with JavaScript.

* * *

# Installing Node.js

The easiest way to install Node.js is from the official website.

[Node.js Official Website](https://nodejs.org)

You’ll usually see:

*   LTS (Long Term Support)
    
*   Current version
    

For beginners, LTS is generally preferred because it is more stable.

* * *

# What Gets Installed?

Installing Node.js usually installs:

*   Node.js runtime
    
*   npm (Node Package Manager)
    

`npm` is used later for installing libraries and packages.

* * *

# Checking the Installation

After installation, open your terminal and run:

```bash
node -v
```

Example output:

```txt
v24.15.0
```

This confirms Node.js is installed successfully.

* * *

# Checking npm

You can also verify npm:

```bash
npm -v
```

Example:

```txt
11.11.0
```

* * *

# Understanding the Node REPL

Before creating files, Node.js provides something called:

# REPL

REPL stands for:

*   Read
    
*   Evaluate
    
*   Print
    
*   Loop
    

It is an interactive environment where you can run JavaScript directly from the terminal.

* * *

# Starting the REPL

Run:

```bash
node
```

You’ll see something like:

```txt
>
```

Now you can execute JavaScript instantly.

Example:

```js
2 + 2
```

Output:

```txt
4
```

* * *

# Why the REPL Exists

The REPL is useful for:

*   quick testing
    
*   experimenting
    
*   debugging small snippets
    
*   learning JavaScript behavior
    

Instead of creating files every time, you can test code immediately.

* * *

# Exiting the REPL

You can exit using:

```bash
.exit
```

or:

```txt
Ctrl + C
```

twice.

* * *

# Creating Your First JavaScript File

Now let’s create an actual Node.js application.

Create a file named:

```txt
app.js
```

Inside it:

```js
console.log("Hello Node.js");
```

* * *

# Running the Script

Inside the terminal, run:

```bash
node app.js
```

Output:

```txt
Hello Node.js
```

* * *

# What Actually Happened?

Flow:

```txt
app.js
↓
Node.js runtime reads file
↓
JavaScript executes
↓
Output printed in terminal
```

Node.js acts as the environment executing your JavaScript code.

* * *

# Understanding the `node` Command

This command:

```bash
node app.js
```

basically tells Node.js:

> “Execute this JavaScript file.”

Unlike browsers, Node.js runs code directly on your machine.

* * *

# Writing Your First Node.js Server

Now let’s create a basic HTTP server.

Replace your code with:

```js
const http = require("http");

const server = http.createServer((req, res) => {
  res.end("Hello from Node.js server");
});

server.listen(3000, () => {
  console.log("Server running on port 3000");
});
```

* * *

# Running the Server

Run:

```bash
node app.js
```

Output:

```txt
Server running on port 3000
```

Now open:

```txt
http://localhost:3000
```

You’ll see:

```txt
Hello from Node.js server
```

* * *

# Understanding What Happened

Let’s break it down.

* * *

# Step 1: Import HTTP Module

```js
const http = require("http");
```

Node.js includes built-in modules for backend functionality.

The `http` module helps create web servers.

* * *

# Step 2: Create Server

```js
http.createServer()
```

This creates a server capable of handling browser requests.

* * *

# Step 3: Handle Requests

```js
(req, res) => {}
```

*   `req` → incoming request
    
*   `res` → outgoing response
    

Whenever someone visits the server, this function runs.

* * *

# Step 4: Send Response

```js
res.end("Hello from Node.js server");
```

This sends data back to the browser.

* * *

# Step 5: Start Listening

```js
server.listen(3000)
```

This starts the server on port `3000`.

Now Node.js continuously waits for incoming requests.

* * *

# What Is `localhost`?

`localhost` refers to:

*   your own computer
    
*   local development machine
    

Example:

```txt
http://localhost:3000
```

means:

> “Access port 3000 on this machine.”

* * *

# Simple Mental Model

Think of Node.js like this:

## JavaScript File

> “Instructions.”

* * *

## Node Runtime

> “Engine executing those instructions.”

* * *

## HTTP Server

> “Program waiting for browser requests.”

* * *

# Full Flow

```txt
Browser request
↓
Node.js server receives request
↓
Request handler executes
↓
Response sent back
↓
Browser displays output
```

* * *

Your first Node.js application is actually very small:

*   install Node.js
    
*   write a JavaScript file
    
*   execute it using Node
    
*   optionally create an HTTP server
    

But this tiny setup is the foundation for:

*   APIs
    
*   backend systems
    
*   real-time apps
    
*   full-stack applications
    

The most important realization is:

Node.js is simply JavaScript running outside the browser with access to backend capabilities.

Once you understand:

*   the runtime
    
*   the REPL
    
*   script execution
    
*   server creation
    

the entire Node.js ecosystem becomes much easier to learn.