---
title: "How DNS Resolution Works"
seoTitle: "Understanding DNS Resolution Basics"
seoDescription: "Learn DNS resolution, components, and tools like `dig` for name servers and records. Understand DNS flow and practical applications"
datePublished: 2026-01-27T15:20:04.799Z
cuid: cmkwqt5mn000102jpgndm0i15
slug: how-dns-resolution-works
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1769522515376/b377cdfd-470b-4b89-a429-964719a43eff.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1769527158606/0fabcb46-d753-4771-bc54-bc81f3aa79f8.png
tags: dns, backend, computer-science, devops, networking, chaiaurcode, chaicode, chaicohort

---

In this blog I will share my knowledge about DNS what is DNS, how it works, why we need it, what is NS, records etc. With this we will use the `dig` command which will help to check DNS, name servers and records.

---

## What is DNS

Domain Name System (DNS) many of us heard about it somewhere, specially in the 2025 Cloudflare outage. DNS is the phonebook of the internet. Browsers interact through IP addresses, but we humans can’t remember IP addresses because IPs are long numbers with dots such as `192.168.0.1` (IPv4) and sometimes numbers with alphabet such as `8926:bc48:3802:1::b249:d83b` (IPv6).

That’s why we use domains. They are easy to remember and do the same job. But you might be thinking how, so here comes DNS. DNS translates domains to IP addresses. It is a hierarchical and decentralized system that follows some steps.

It is called name resolution. It exists to bridge the gap between us humans and computers. It helps us remember domains and helps computers get IP addresses. It also provides system agility. Name server resolution allows a website's server IP address to change without needing us to remember a new IP address. Server admin can easily update the DNS record and the existing domain continues to work. It takes some time to update the records on servers all over the world.

---

## dig command

Before diving more into DNS and name servers, we need to understand a tool called `dig`, which we will use to see DNS server details such as their IP, records and name servers.

Domain Information Groper (dig) is a command line tool used for querying DNS servers. It helps to verify DNS records, trace queries and do reverse lookups.

Basic command examples:

| Task | Command |
| --- | --- |
| Simple Lookup | `dig` [`google.com`](http://google.com) |
| Short Answer (IP only) | `dig` [`google.com`](http://google.com) `+short` |
| Query Specific Record | `dig` [`google.com`](http://google.com) `MX` |
| Query Specific Server | `dig @8.8.8.8` [`google.com`](http://google.com) |
| Reverse Lookup | `dig -x 142.250.182.206` |
| Full Trace | `dig` `+trace` [`google.com`](http://google.com) |

---

## Recursive DNS Resolver

Before root, TLD and authoritative servers come into picture, there is something very important called **recursive DNS resolver**. This is usually provided by your ISP or public DNS like:

* 8.8.8.8 (Google)
    
* 1.1.1.1 (Cloudflare)
    
* 9.9.9.9 (Quad9)
    

Your browser does not directly talk to root or TLD servers. It talks to recursive resolver.

Recursive resolver’s job is:

* Ask other DNS servers on your behalf
    
* Cache results
    
* Finally give IP back to your browser
    

So recursive resolver is like your personal assistant who runs around and collects answers for you.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769589111616/759bfb07-9826-40dd-a758-adc9e6018481.png align="center")

---

## Root Servers

As we know Domain Name System hierarchy, so at the top of pyramid this root server stands. They are just like the Elder from John Wick. Root servers don’t store the website IP. They don’t even know full domain details.

If user's recursive DNS server gets an uncached DNS query, then the query goes to Root Server. They get queries, check which Top Level Domain (TLD) it is (like .com, .org) and then refer to that TLD server. That’s the job of root server.

There are 13 main root servers around the globe.

### dig . NS

When you run:

```plaintext
dig . NS
```

This shows you the **name servers for the root zone**. These are the root servers.

What this means in real flow:

* These servers are responsible for directing queries to TLD servers
    
* They don’t give you google.com IP
    
* They just say: “Go ask .com servers”
    

So root servers are like traffic controllers for the top of DNS hierarchy.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769526011373/dfd540c7-edb9-4541-86c4-2c03d1f00d86.png align="center")

---

## TLD Servers

In the domain hierarchical pyramid, these are the second from top, just like High Table from John Wick. TLDs categorize websites by purpose, type or geography etc. Some TLDs: .com, .org, .net, .in, .uk etc.

TLD server stores list of domains under that TLD and their authoritative name servers.

So when a user sends a request for a domain, the TLD server receives the request from a root server and responds by providing the address of the specific authoritative name server for that domain. Then authoritative does the rest job.

### dig com NS

When you run:

```plaintext
dig com NS
```

This shows you the **name servers responsible for .com TLD**.

What this means in real flow:

* Root server sends query to these .com servers
    
* These servers don’t give IP for google.com
    
* They only tell which authoritative servers handle google.com
    

So TLD servers are like a directory that tells you where to find the real owner of the domain.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769526260828/83539abd-8aad-49cf-8c04-5a86b58eda8d.png align="center")

---

## Authoritative Name Servers

This is the DNS server that stores all records:

* IP address (A / AAAA)
    
* Mail server info (MX)
    
* TXT records
    
* CNAME etc.
    

This is the 3rd position from top of the pyramid. They are just like The Continental from John Wick. They provide the final result to a DNS query for that domain.

These servers manage zone files and are responsible for a specific domain.

### dig google.com NS

When you run:

```plaintext
dig google.com NS
```

This shows you the authoritative name servers for google.com

What this means in real flow:

* TLD server points to these servers
    
* These servers actually know about google.com
    
* These servers hold real DNS records for google.com
    

So authoritative servers are the only ones that can give final correct answer for that domain.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769526496965/dc6d3102-3ce5-4121-9c1e-730d7b916baa.png align="center")

---

## dig google.com

When you run:

```plaintext
dig google.com
```

You are asking your recursive resolver to resolve google.com

Behind the scenes, this is what happens (if not cached):

1. Recursive resolver asks Root Servers
    
2. Root points to .com TLD Servers
    
3. TLD points to google.com Authoritative Servers
    
4. Authoritative returns IP address
    
5. Recursive resolver caches it
    
6. Recursive resolver sends IP to your computer
    

So even though you typed one command, a lot of DNS servers were involved.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769526631730/92ee22bb-485f-4097-986f-87de475c8f39.png align="center")

---

## Full DNS Resolution Flow

Let’s understand the full DNS resolution flow in simple way.

Think like this: you want to watch YouTube. You don’t know the IP of youtube.com but you know the domain. So you type youtube.com in browser.

Flow looks like this:

1. Browser asks Recursive DNS Resolver
    
2. If cached → resolver returns IP immediately
    
3. If not cached → resolver asks Root Servers
    
4. Root sends resolver to .com TLD Servers
    
5. TLD sends resolver to youtube.com Authoritative Servers
    
6. Authoritative returns IP address
    
7. Resolver caches it
    
8. Resolver sends IP to browser
    
9. Browser connects to that IP and loads website
    

So browser never talks to root or TLD directly. Recursive resolver does all the heavy work for you.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769589124625/70414d71-d258-4296-86cf-73c0d2df4c07.png align="center")

---

## Why NS records matter

NS records tell you **which servers are authoritative for a domain**.

This is important because:

* They define who controls DNS for a domain
    
* They decide where queries should be sent
    
* If NS records are wrong, domain will break
    
* They are key part of DNS delegation
    

That’s why dig NS commands are very useful in debugging DNS issues.

---

## How this connects to real world systems

When you open a website, your browser depends fully on DNS to find the server IP. If DNS is slow or broken, website feels slow or broken even if server is healthy.

In backend and system design, DNS is critical because:

* Load balancers use DNS
    
* Multi-region setups use DNS
    
* Failover is often handled using DNS
    
* Traffic routing can be done at DNS level
    

---

## Mapping dig to DNS layers

* `dig . NS` → Root Servers
    
* `dig com NS` → TLD Servers
    
* `dig` [`google.com`](http://google.com) `NS` → Authoritative Servers
    
* `dig` [`google.com`](http://google.com) → Full resolution via recursive resolver