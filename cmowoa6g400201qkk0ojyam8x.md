---
title: "How React Virtual DOM Works Under the Hood"
seoTitle: " React Virtual DOM Works Under the Hood"
seoDescription: "How React Virtual DOM Works Under the Hood"
datePublished: 2026-05-08T08:48:09.512Z
cuid: cmowoa6g400201qkk0ojyam8x
slug: react-virtual-dom
cover: https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/ca84e6b0-50f7-486c-99f3-2ef194707240.jpg
tags: javascript, react-native, reactjs, typescript, chaicode

---

When people start learning React, one term appears everywhere:

> “React uses a Virtual DOM.”

But what does that actually mean?

Why did React introduce another DOM when browsers already have one?

To understand that, we first need to look at the problem React was trying to solve.

* * *

# The Problem With Direct DOM Manipulation

The browser’s DOM (Document Object Model) is expensive to update frequently.

Whenever JavaScript changes the Real DOM, the browser may need to:

*   recalculate layouts
    
*   repaint elements
    
*   reflow parts of the page
    
*   update rendering on screen
    

These operations are not cheap.

For small applications this is fine, but in large interactive apps with:

*   counters
    
*   forms
    
*   live search
    
*   notifications
    
*   dashboards
    

continuous DOM updates can become slow.

Imagine updating hundreds of elements every second manually.

That’s where React’s Virtual DOM comes in.

* * *

# Real DOM vs Virtual DOM

## Real DOM

The Real DOM is the actual browser structure rendered on screen.

Example:

```html
<div>
  <h1>Hello</h1>
</div>
```

This exists inside the browser memory and directly affects what users see.

Updating it repeatedly is costly because the browser must re-render parts of the UI.

* * *

## Virtual DOM

The Virtual DOM is a lightweight JavaScript representation of the Real DOM.

Instead of directly changing browser elements every time, React first updates this virtual copy.

Example mental model:

```javascript
{
  type: "div",
  children: [
    {
      type: "h1",
      children: ["Hello"]
    }
  ]
}
```

This object is much faster to create and compare than manipulating actual browser nodes.

* * *

# Initial Render in React

Let’s say we have this component:

```javascript
function App() {
  return <h1>Hello World</h1>;
}
```

When React renders this component for the first time:

* * *

## Step 1: React Creates a Virtual DOM Tree

React converts components into JavaScript objects internally.

Mental model:

```javascript
{
  type: "h1",
  children: ["Hello World"]
}
```

* * *

## Step 2: React Creates Real DOM Nodes

React then converts that Virtual DOM structure into actual browser DOM elements.

Now the browser finally displays:

```html
<h1>Hello World</h1>
```

* * *

## Flow

Component → Virtual DOM → Real DOM

* * *

# What Happens When State or Props Change?

Now imagine this component:

```javascript
function Counter() {
  const [count, setCount] = useState(0);

  return <h1>{count}</h1>;
}
```

When `setCount(1)` runs:

React does **not** directly modify the browser DOM immediately.

Instead, React starts a re-render process.

* * *

# Step-by-Step React Update Flow

* * *

## Step 1: State Changes

```javascript
setCount(1);
```

This tells React:

> “Something changed. Re-render this component.”

* * *

## Step 2: React Creates a New Virtual DOM Tree

Old Virtual DOM:

```javascript
<h1>0</h1>
```

New Virtual DOM:

```javascript
<h1>1</h1>
```

React now has:

*   previous tree
    
*   new tree
    

* * *

# What Is Diffing?

Diffing means comparing:

*   old Virtual DOM tree
    
*   new Virtual DOM tree
    

This comparison process is called:

# Reconciliation

React checks:

*   what changed
    
*   what stayed same
    
*   what actually needs updating
    

Instead of rebuilding the whole page, React calculates the minimum required changes.

* * *

# Example of Reconciliation

Old tree:

```javascript
<div>
  <h1>Hello</h1>
  <p>Count: 0</p>
</div>
```

New tree:

```javascript
<div>
  <h1>Hello</h1>
  <p>Count: 1</p>
</div>
```

React compares both trees.

It notices:

*   `<div>` unchanged
    
*   `<h1>` unchanged
    
*   only `<p>` text changed
    

So React updates only that specific text node.

This is the key optimization.

* * *

# Minimal Updates to the Real DOM

Instead of replacing the entire UI, React performs:

```javascript
paragraph.textContent = "Count: 1";
```

Only the changed part gets updated.

This reduces:

*   unnecessary DOM operations
    
*   browser repaint work
    
*   layout recalculations
    

And improves performance significantly.

* * *

# Why Virtual DOM Improves Performance

Important clarification:

The Virtual DOM itself is not “faster than the Real DOM.”

The optimization comes from:

*   reducing unnecessary DOM updates
    
*   batching changes efficiently
    
*   updating only what changed
    

The browser DOM is expensive.

JavaScript object comparison is comparatively cheap.

React uses this idea to minimize direct browser work.

* * *

# The Complete React Lifecycle Flow

Here’s the overall mental model:

* * *

## 1\. Initial Render

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/850f3a9e-be96-4486-a802-0af018945330.png align="center")

* * *

## 2\. State or Props Change

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/0d5e6441-9f3a-455f-bc1b-33036d01d8b3.png align="center")

* * *

## 3\. Diffing (Reconciliation)

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/e954c2e5-8797-40f2-b06f-ed849a47978a.png align="center")

* * *

## 4\. Commit Phase

![](https://cdn.hashnode.com/uploads/covers/69513de35d3cf3dcde6a6e95/3530610f-ec7a-40e4-9f07-7ea9f963561c.png align="center")

* * *

# Simple Mental Model

Think of the Virtual DOM like a “draft version” of the UI.

React:

1.  creates a new draft
    
2.  compares it with the old draft
    
3.  finds differences
    
4.  updates only necessary parts in the browser
    

Instead of rebuilding the entire page every time.

* * *

React’s Virtual DOM is essentially an optimization strategy.

The core idea is simple:

*   UI changes frequently
    
*   Direct DOM updates are expensive
    
*   So React compares lightweight JavaScript trees first
    
*   Then updates only necessary browser nodes
    

That’s why React applications can handle complex interactive interfaces efficiently without manually managing DOM updates everywhere.