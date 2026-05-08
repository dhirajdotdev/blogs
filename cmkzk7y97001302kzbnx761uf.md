---
title: "CSS Selectors 101: Targeting Elements with Precision"
seoTitle: "Mastering CSS Selectors for Precise Targeting"
seoDescription: "Learn the basics of CSS selectors to target HTML elements precisely and apply styles effectively. Perfect for beginners in web design"
datePublished: 2026-01-29T14:38:56.299Z
cuid: cmkzk7y97001302kzbnx761uf
slug: css-selectors-101
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1769697455765/7a1ff057-12d6-4d34-a970-79d4836cb6a5.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1769697513202/64fc75cd-5586-4b40-b563-271272268edb.png
tags: css3, css, chaiaurcode, chaicode, chaicohort

---

When you write CSS, you are not just writing styles. You are also telling the browser **which elements should get those styles**.

That’s where CSS selectors come into picture.

Selectors are how you choose elements on the page. Without selectors, CSS would not know what to style.

In this blog I will share my understanding of CSS selectors, why they are needed and how to use the most common ones to target elements in a clean and simple way.

---

## Why CSS selectors are needed

Imagine a webpage with many paragraphs, buttons, images and sections.

If you write CSS like this:

```xml
color: red;
```

Browser will not know where to apply it.

Selectors solve this problem. They tell the browser: Apply this style to *these* elements.

So selectors are basically **the address system of CSS**. They decide who gets what styles.

---

## Selectors as addressing people

Think of selectors like addressing people in a room.

If you say: “Everyone” → that’s like element selector.

If you say: “People wearing blue shirts” → that’s like class selector.

If you say: “Only Peter” → that’s like id selector.

So selectors help you be more and more specific about who you are targeting.

---

## Element selector

Element selector targets all elements of a specific type.

Example:

```css
p {
  color: blue;
}
```

This means: All `<p>` elements will become blue.

So element selector is the broadest way to target elements.

It is useful when you want to style all elements of one type.

---

## Class selector

Class selector targets elements with a specific class.

Class selector uses a dot.

Example:

```css
.card {
  border: 1px solid #ccc;
}
```

This means: All elements with class="card" will get this style.

Class selectors are used most of the time in real projects.

Classes are reusable. Many elements can have the same class.

So class selector is like: Target a group with the same label.

---

## ID selector

ID selector targets one specific element using its id.

ID selector uses a hash.

Example:

```css
#header {
  background: black;
}
```

This means: Only the element with id="header" will get this style.

IDs should be unique on a page.

So id selector is like: Target one specific person in the room.

---

## Class vs ID

This is common beginner confusion.

Use class when: You want to style multiple elements You want reusable styles

Use id when: You want to target one unique element You need something very specific

In most cases, you will use classes much more than ids.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769696973447/22f070e0-021e-4796-807f-fb27e4ded568.png align="center")

---

## Group selectors

Sometimes you want to apply same style to multiple different selectors.

Instead of writing CSS multiple times, you can group selectors.

Example:

```css
h1, h2, h3 {
  color: purple;
}
```

This means: All h1, h2 and h3 will be purple.

Group selectors help reduce duplicate CSS and keep things clean.

---

## Descendant selectors

Descendant selectors target elements that are inside other elements.

Example:

```css
div p {
  color: green;
}
```

This means: All `<p>` elements inside a `<div>` will be green.

This is very powerful because it lets you style based on structure.

So you are not just targeting element type. You are targeting element based on where it lives in the HTML.

---

## Selector targeting flow

CSS reads selectors from right to left and matches elements based on rules.

But for beginners, think simple: Selector describes what you want Browser finds matching elements Styles are applied

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769697079514/2e4571cb-ef60-44f2-8997-f88e97863bed.png align="center")

---

## Basic selector priority

Sometimes multiple selectors target the same element.

Then browser has to decide which style wins.

At very high level, priority works like this:

ID selector has higher priority than class selector. Class selector has higher priority than element selector.

So: #id &gt; .class &gt; element

This is called specificity, but you don’t need to go deep now.

Just remember: More specific selector usually wins.

---

## Before and after styling example (simple idea)

HTML:

```html
<p class="text">Hello</p>
```

CSS:

```css
p {
  color: blue;
}

.text {
  color: red;
}
```

Result: Text will be red because class selector is more specific than element selector.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769697275123/b4ecdddc-bef1-4f47-a7ee-0902b3fa7bdf.png align="center")

This helps you understand how browser chooses styles.

---

## Selectors are the foundation of CSS

CSS is not just about colors and margins. CSS is about targeting the right elements first.

If your selector is wrong, your styles won’t apply correctly.

Once you understand selectors well, CSS becomes much easier and less frustrating.

---

CSS selectors are how you tell the browser who should get which styles.

Start simple with: Element selectors Class selectors ID selectors

Then slowly use grouping and descendant selectors.

You don’t need to memorize everything. What matters is understanding how selectors target elements.

Selectors are the foundation of all CSS styling.