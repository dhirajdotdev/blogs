---
title: "Getting Started with cURL"
seoTitle: "Beginner's Guide to cURL"
seoDescription: "Learn how to use cURL for sending requests to servers, testing APIs, and understanding client-server communication without relying on browser UI"
datePublished: 2026-01-24T13:19:08.379Z
cuid: cmksc62jf000d02ju1ugy91nt
slug: getting-started-with-curl
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1769257479072/89b5e0b9-1cb4-4f32-acad-0f52431fb016.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1769260722921/fbb78c49-e933-48a6-9794-c80209e9b907.png
tags: curl, api, apis, learning, chaiaurcode, chaicode, chaicohort

---

Whenever we use a website or app our computer is talking to some server in the background. We don’t really see it because browser hides everything and just shows us UI. But under that it’s always request and response going on between our computer and server somewhere on the internet.

As developers sometimes we don’t want to depend on browser. We want to directly talk to server and see what is happening. That’s where cURL comes in.

In this blog I will share how I understand cURL, why I use it and how it helps when working with servers and APIs.

---

## What is a Server

A server is just another computer whose job is to respond to requests. When you open a website, your computer is basically asking another computer for some data. That computer sends something back and your browser shows it to you nicely.

So everything is just computers talking to computers.

---

## What is cURL

cURL is just a tool to send requests to a server from terminal. Instead of opening a website in browser, you type a command and cURL sends request for you and prints whatever server sends back.

So browser and cURL both talk to server. The difference is browser shows UI and cURL shows raw response.

---

## Why programmers use cURL

When you are working with backend or APIs, many times there is no UI. You only have URLs and endpoints. cURL makes it easy to hit those endpoints and see what server is returning.

It’s also useful when something is not working and you want to quickly check if server is alive or if your API is actually responding.

---

## cURL command

The most basic thing you can do is:

```plaintext
curl https://randomuser.me/
```

This just tells cURL to go to that server and get whatever is there. The server sends back a response and you see it in terminal.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769258289581/7c2b8357-35bc-4259-9872-55e8c2c56773.png align="center")

It’s the same like opening website just without browser UI.

---

## Request and Response

Whenever you use cURL, two things are always happening:

You send a request. Server sends a response.

So the flow is always:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769258768922/5f8d509d-4b06-41e8-bb13-019ee6932701.png align="center")

This is exactly what browser also does, just hidden from you.

---

## Using cURL with APIs

Most APIs don’t return webpages. They return data. When you use cURL on an API URL, you usually see JSON in terminal.

This is very common in backend and frontend work. Frontend talks to backend using APIs and backend talks to other services using APIs.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769258933709/26a19799-ff7c-422a-b648-1d0af7278cdf.png align="center")

cURL makes it easy to see what data is actually coming back from server.

---

## GET and POST

Most beginner use cases are just GET and POST.

When you run a normal cURL command, you are usually doing a GET request. That means you are just asking server to give you some data.

POST is when you send some data to server like login info or form data.

GET = get data

POST = send data

---

## Browser vs cURL

Browser does a lot of things for you. It sends request, gets response, renders HTML, runs JavaScript and shows UI.

cURL just sends request and prints response.

So browser is like full experience. cURL is like raw communication.

Both are talking to same server.

## Browser

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769259530969/76eda6f4-75d9-478b-ae54-07646ea88a03.png align="center")

## cURL

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769259593833/b907f818-1d27-4edd-bd80-0c42b7dd7697.png align="center")

---

## Common beginner confusion

At start, many people get confused when they see raw JSON or HTML in terminal. It feels messy. But that’s actually the real response from server. Browser usually hides all that and makes it look clean.

So when you see messy output in cURL, it doesn’t mean it’s wrong. It just means you are seeing what server actually sends.

---

## Where cURL fits for backend

When you work with backend or APIs, everything is just request and response. Services talk to each other using HTTP.

cURL helps you test those endpoints, debug issues and understand how systems are actually communicating.

So learning cURL is like learning how to directly talk to servers without UI in between.

---

cURL is a simple tool, but it helps you understand something very important how your computer talks to servers on the internet.