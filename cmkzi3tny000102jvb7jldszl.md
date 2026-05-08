---
title: "Understanding HTML Tags and Elements"
seoTitle: "HTML Tags Explained: A Beginner's Guide"
seoDescription: "Learn the basics of HTML tags and elements, their functions, and how they create web page structures in simple terms"
datePublished: 2026-01-29T13:39:44.494Z
cuid: cmkzi3tny000102jvb7jldszl
slug: understanding-html-tags-and-elements
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1769693868778/af866eb4-f550-4408-a1c3-7c81b6050779.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1769693936006/e196a087-cf54-425b-962b-06cdbdcd01cd.png
tags: html, html5, chaiaurcode, chaicode, chaicohort

---

Whenever we open a website, what we see on screen is built using HTML. Text, headings, buttons, images and sections all of these start from HTML.

HTML is the first thing a browser reads when it loads a page. So if you want to understand how websites are built, HTML is where everything starts.

In this blog I will share my understanding of HTML tags and elements what they are, how they work and how they build the structure of a webpage in simple terms.

---

## What HTML is and why we use it

HTML stands for Hypertext Markup Language.

HTML is used to define the structure of a webpage.

You can think of HTML as the skeleton of a website.

HTML does not make things pretty. HTML does not add animations. HTML just says: This is a heading This is a paragraph This is a section This is an image

CSS makes it look good. JavaScript makes it interactive. HTML gives the basic structure.

So HTML is the foundation of every webpage.

---

## What an HTML tag is

An HTML tag is a keyword wrapped inside angle brackets.

Example:

```xml
<p>
<h1>
<div>
<span>
```

Tags tell the browser what type of content it is dealing with.

So when browser sees `<p>`, it knows this is a paragraph. When browser sees `<h1>`, it knows this is a main heading.

You can think of tags like labels on boxes that tell what is inside.

---

## Opening tag, closing tag and content

Most HTML tags have: Opening tag Content Closing tag

Example:

```xml
<p>Hello World</p>
```

Here: `<p>` is opening tag `Hello World` is content `</p>` is closing tag

So structure looks like this:

```xml
<tag> content </tag>
```

This tells browser exactly where content starts and where it ends.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769692574557/d042f9f6-8bb5-426d-8761-a20a411d26c5.png align="center")

---

## What an HTML element means

HTML tag and HTML element are not the same thing.

HTML tag is just the label. HTML element is the full thing.

So this is an HTML tag:

```xml
<p>
```

But this is an HTML element:

```xml
<p>Hello World</p>
```

Element = Opening tag + Content + Closing tag

So when people say “HTML element”, they usually mean the complete structure, not just the tag.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769692694336/22424797-185a-41ab-9233-9c84776d91dc.png align="center")

---

## Self-closing (void) elements

Some HTML elements do not have closing tags. These are called self-closing or void elements.

Examples:

```xml
<img>
<br>
<hr>
<input>
<meta>
<link>
```

These elements don’t wrap content. They just exist by themselves.

For example:

```xml
<img src="photo.jpg">
```

There is no `</img>` tag.

So rule of thumb: If element does not contain content, it is usually self-closing.

---

## Block-level vs inline elements

HTML elements behave differently in layout. Two important categories are: Block-level elements Inline elements

### Block-level elements

Block-level elements take full width and start on a new line.

Examples:

`<div>`

`<p>`

`<h1>` to `<h6>`

`<section>`

`<article>`

So block elements stack on top of each other.

---

### Inline elements

Inline elements do not start on new line. They only take as much width as needed.

Examples:

`<span>`

`<a>`

`<strong>`

`<em>`

Inline elements flow inside text.

So inline elements are used inside block elements.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769693115784/11964e8b-fd13-4e34-85ee-f8156ac24aa5.png align="center")

---

## Commonly used HTML tags

Here are some very common HTML tags you will see everywhere:

`<h1>` to `<h6>` → Headings

`<p>` → Paragraph

`<div>` → Generic container

`<span>` → Inline container

`<a>` → Link

`<img>` → Image

`<ul>` and `<ol>` → Lists

`<li>` → List item

`<input>` → Input field

`<button>` → Button

These tags are enough to build most basic webpage structures.

---

## Tag vs Element

This is very important for beginners.

Tag = Just the name inside angle brackets

Example:

```xml
<p>
```

Element = Full structure

Example:

```xml
<p>This is a paragraph</p>
```

So: Tag is part of element. Element is the complete thing.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769693443046/13263b16-6f20-4a9b-b9bb-dae9e445230d.png align="center")

Once you understand this, HTML becomes much less confusing.

---

## Simple box analogy

Think of HTML element like a box.

Opening tag = opening the box Content = what you put inside the box Closing tag = closing the box

So element is the full box with stuff inside.

---

## Inspecting HTML in browser

One of the best ways to learn HTML is to inspect real websites.

Right click on any webpage and click Inspect.

You will see: HTML structure, Elements and tags, How browser sees the page

This helps you connect what you write in HTML to what browser actually understands.

---

HTML tags and elements are the building blocks of every website.

HTML is simple by design. It just describes content. Everything else builds on top of it.