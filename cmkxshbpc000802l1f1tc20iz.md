---
title: "DNS Record Types Explained"
seoTitle: "Understanding DNS Record Types"
seoDescription: "Discover the essential DNS record types that power the internet and learn how they work together to make websites function seamlessly"
datePublished: 2026-01-28T08:54:38.208Z
cuid: cmkxshbpc000802l1f1tc20iz
slug: dns-record-types-explained
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1769590344080/32be5458-eb79-4523-8214-bd1f15f1bdee.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1769590449890/63c49c6f-1bd9-495c-91ba-7cf91a669aaa.png
tags: dns, internet, networking, chaiaurcode, chaicode, chaicohort

---

Whenever we type a website in browser, somehow it knows where to go. We just write a domain name and boom, website loads. But behind the scenes, there are multiple DNS records working together to make this happen.

In this blog, I will share my understanding of DNS record types what they are, why we need them and how they all work together for a real website.

---

## What is DNS

DNS is the phonebook of the internet.

Humans remember names like google.com, youtube.com. But computers don’t understand names. They understand IP addresses like 172.217.23.206

So DNS is the system that converts domain names into IP addresses.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769588831380/39d7cf9e-7f3c-4a7f-b35c-1b00119626f2.png align="center")

---

## Why DNS records are needed

DNS records are the actual instructions stored in DNS that tell the internet what to do with your domain.

Without DNS records your domain is just a name with no meaning. DNS records tell things like:

* Where your website server is
    
* Which server handles your email
    
* Who controls DNS for your domain
    
* Extra verification info for services
    

So DNS records are like different types of notes in the phonebook that explain how your domain should work.

---

## What an NS Record is

NS record means **Name Server record**.

NS record tells which DNS servers are responsible for your domain. In simple words, it tells who is in charge of DNS for your domain.

When you buy a domain, your domain provider gives you default name servers. But you can change them to use another DNS provider like Cloudflare.

So NS records are like: This company handles DNS for this domain.

If NS records are wrong nothing else will work website, email everything breaks.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769586849975/70b6ea07-6be4-4ff4-b0c0-b05b0324c8b5.png align="center")

---

## What an A Record is

A record is the most common DNS record.

A record maps a domain name to an IPv4 address.

So it tells: domain name → server IP address

So when browser asks for a domain, DNS looks at A record and gives back the IPv4 address of the server where website is hosted.

You can think A record like: Name → House address

---

## What an AAAA Record is

AAAA record is similar to A record, but for IPv6.

It maps a domain name to an IPv6 address instead of IPv4.

So: domain name → IPv6 address

Most of the time we only see A records, but AAAA is for newer IP format.

So: A = IPv4, AAAA = IPv6

Same job, different IP version.

---

## What a CNAME Record is

CNAME means **Canonical Name**.

CNAME record does not point to an IP address. It points to another domain name.

So instead of: name → IP

It is: name → another name

Example from my setup:

I use Hashnode for blogs. Hashnode gave me this hostname:

```plaintext
hashnode.network
```

So I created a CNAME record:

```plaintext
blog.dhiraj.dev → hashnode.network
```

So when someone opens blog.dhiraj.dev, DNS says: “Go to hashnode.network and use whatever IP it has.”

So CNAME is useful when you don’t control the IP and the service manages it for you.

You can think CNAME like: Nickname → Real name

---

## What an MX Record is

MX record means **Mail Exchange record**.

MX records tell where emails for your domain should be delivered.

When someone sends email to: contact@dhiraj.dev

Mail servers use MX records to find which mail server should receive that email.

So MX record is not for website. It is for email.

So: Website traffic → A / CNAME, Email traffic → MX

---

## What a TXT Record is

TXT record is used to store extra text information for a domain.

TXT records are commonly used for:

* Domain ownership verification
    
* Email security (SPF, DKIM, DMARC)
    
* Connecting third party services
    

Most of the time, services tell you: “Add this TXT record to verify your domain.”

So TXT record is like a note that proves you own the domain or enables some feature.

---

## Common confusion

### A vs CNAME

* **A record** points to an IP address
    
* **CNAME** points to another domain name
    

If you have server IP → use A, If service gives you hostname → use CNAME

---

### NS vs MX

* **NS record** decides who manages DNS
    
* **MX record** decides where email goes
    

NS is for DNS control. MX is only for email delivery.

---

## How all DNS records work together for one website

Here is how all DNS records work together using my real setup, so it’s easier to understand.

I purchased **dhiraj.dev** from Hostinger (domain provider).

At first Hostinger was managing the DNS because they were the domain provider. But I wanted to use Cloudflare for DNS management, security and better control.

So I updated the **NS records to Cloudflare**.

This means now Cloudflare became the authoritative DNS for my domain. From this point, Cloudflare is responsible for all DNS records of dhiraj.dev.

So now flow looks like this: dhiraj.dev → NS records → Cloudflare

Now for my main website.

My website is hosted on **Vercel**. Vercel gave me a DNS record (A record), which points to their server IP.

So in Cloudflare DNS dashboard, I added that A record.

So now: dhiraj.dev → A record → Vercel server IP

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769588007462/624ee3e6-9489-49b3-b7d2-59e8354d0207.png align="center")

This is how my main website loads. Browser uses DNS, gets the IP from A record, and connects to Vercel server.

Now for **blog.dhiraj.dev**

I’m using **Hashnode** for blogs. Hashnode gave me this hostname:

```plaintext
hashnode.network
```

Hashnode does not give a fixed IP. They manage their own servers and IPs. So instead of A record, they tell to use a CNAME.

So I added a CNAME record in Cloudflare DNS:

```plaintext
blog.dhiraj.dev → hashnode.network
```

This means: blog.dhiraj.dev is just another name for hashnode.network

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769588270940/b066dc74-43ec-40de-9fe3-1d013a5dfdb6.png align="center")

So when someone opens blog.dhiraj.dev, DNS says: “Go to hashnode.network and use whatever IP it currently has.”

So now for my domain, multiple DNS records are working together:

* **NS records** → Point domain to Cloudflare (who manages DNS)
    
* **A record** → Point main website to Vercel
    
* **CNAME record** → Point blog subdomain to Hashnode
    
* **MX records** → tell where emails should go
    
* **TXT records** → Used for verification and email security
    

So one single domain is not just one record. It is a combination of multiple DNS records that make website, blog and email all work together.

This is how DNS records connect different services under one domain and make everything work smoothly.