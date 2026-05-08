---
title: "Understanding Network Devices"
seoTitle: "Network Devices: A Beginner's Guide"
seoDescription: "Learn about network devices: modems, hubs, switches, routers, firewalls, and load balancers, and how they interconnect to form efficient networks"
datePublished: 2026-01-23T17:50:07.045Z
cuid: cmkr6ep50000002jifpcec3vk
slug: understanding-network-devices
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1769937050781/ff3aa546-ca1b-413f-89c2-0bc6416a7ba1.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1769937073538/d20f14fd-cb7f-4dfa-be07-98b41497034d.png
tags: software-development, web-development, security, router, internet, networking, load-balancer, firewall, computer-networks, networking-for-beginners, chaicode

---

  
  
We use the internet every single day for watching videos, chatting with friends, playing games, shopping online and doing work. But most of the time we don’t really think about what actually happens when we open a website or send a message. In the background, our data is traveling from our device through many network devices and across different networks to reach another computer somewhere in the world. The internet is a huge network of networks that connects millions of computers together so we can communicate and share information.

  
In this blog I will share my knowledge about network devices, how they work and connect with each other and how they create a network with examples. I will follow a sequence so these things will make sense.

---

## MODEM

If you are from that era when for a decent internet connection we needed a telephone line, I hope you saw a modem. As we know about digital signals and analog signals, these telephones worked on analog signals, but to use the internet we need digital signals. So we need something which can convert analog signal to digital signal and vice versa, otherwise we can’t send or receive data through telephone line.

Here comes MODEM. In the name you can understand what it does Modulator Demodulator. It does the heavy work and converts signals.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769182293606/72c69161-b390-4742-96b2-69c61f914458.png align="center")

You can connect a single computer with ethernet in it and use internet, but if you want to use multiple computers at the same time, you will need a router which I’m gonna talk about after hub and switch. Also now modern routers come with inbuilt modem.

---

## HUB

Just like the name, it’s a hub. It joins multiple computers with each other and creates a local network, but there is a catch. It sends or receives data to every computer on that network. It just broadcasts data to everyone. Here a major security issue you can say, but it has its use cases.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769184599631/9d585581-34a1-4bd8-b2dd-314e4d5d0921.png align="center")

---

## Switch (To solve hub security problem)

To solve this security problem, we have switches. Let’s talk about switches.

Switches are like hub but with brain. It connects with every computer and notes down a special ID of those computers called [MAC](https://en.wikipedia.org/wiki/MAC_address) address. No, it’s not related to MacBook or Mac desktop. Each computer's [NIC (Network Interface Card)](https://en.wikipedia.org/wiki/Network_interface_controller) has a unique ID. It’s called MAC address. So if any computer wants to send or receive data from a particular computer within that network, switch only sends or receives from that computer by identifying that computer’s MAC address.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769185975935/6236eca7-6ce4-4403-8671-c883ec88f6d5.png align="center")

---

## Router

So this far we got to know about hub and switch. These things work on local network, but what if you want to use the internet. You can’t watch YouTube on local network, that’s why we need router.

I’m assuming we all saw router in our home or office. It’s a small machine but does a lot of work just to connect us with the internet, so yeah size doesn’t matter.

Think about this: you want to buy something online. Using Google, you searched to see fans. Now you get the results only fans, no ac, cooler or other things. You got the thing you wanted. So for internet it’s called routing finding the right path to that destination.

When you visit a website from your computer, the router finds best path possible and connects your computer to the internet. You can connect direct with a router or you can connect your local network's switch to it to make them access the internet. Router uses [IP address](https://en.wikipedia.org/wiki/IP_address) to find addresses of other computers online.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769186720425/a6336e9d-cbd2-400b-a4cb-73f8ae59512d.png align="center")

---

## Hub vs Switch (Local Network)

Both hub and switch are used to connect computers in a local network, but they work very differently.

* **Hub** sends data to *every* computer even if data is for only one computer
    
* **Switch** sends data only to the *specific* computer using MAC address
    

So: Hub broadcast to all (no security, no brain) & Switch private delivery (more secure, smarter)

---

## Modem vs Router (Internet Connection)

Both modem and router are related to internet, so people confuse them, but their jobs are different.

* **Modem** connects to ISP and converts signals so internet can come to your network
    
* **Router** takes that internet and decides where to send data on the internet
    

So: Modem brings internet inside Router sends your data to right place on internet

---

## FIREWALL

At this point we know how things work at a basic level, but internet is a huge ocean and there are sharks too. So to save users from those sharks I mean hackers we need something, right? That’s when firewall comes into the picture. Let’s see what it is.

To secure the internet and prevent users from getting malware or things like these, we need some type of shield or wall that will block unnecessary, untrusted things. So firewall does this job. It works like a wall that protects users.

There are 2 types of firewall:

### Host Based Firewall

Mostly software that works on the computer. It filters data coming from router. It blocks those which are off the list. So firewall needs some rules who to pass or who to block, then it does its job.

### Network Based Firewall

It stands before the router. Mostly hardware are used here. It does same job as host based firewall but on a large scale. If anything gets passed by network based firewall which is not allowed and somehow got passed, there is host based firewall to stop it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769187637881/07a16c95-92e1-4159-847d-c5eeb3577274.png align="center")

---

## Load Balancer

So much info, damn, but we need all these to use internet. Another thing we need is to use websites or services smoothly without any lag or buffering. It’s called load balancer. Let’s know about it, then we will see how all these work together. I hope you can picture it now, but I will make it easier for you.

Let’s put it like this: you are waiting for your favorite web series on Netflix. Like you, there are millions of fans of that particular show. When all these fans try to watch it at same time, there might be lag because too many users are logged in and playing same thing at same time. It can use all the resources of the server if it’s a single server.

But as we know, it doesn’t happen every time when they are going to drop a season or movie because they use Load Balancing. They use multiple servers to serve content to all users.

This is how all load gets distributed to many servers and the users can Netflix and chill.

For load balancing we can use reverse proxy server like nginx. It does the job. When server gets too much requests, it can distribute all those to multiple servers.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769188200120/3fd2b557-ceb5-4e23-80f4-85f7e511482d.png align="center")

---

## How all these devices work together in a real world setup

So now as we read about these things, we can connect the dots together.

So let’s say I’m at a cyber cafe and with 4 people we hop on an online multiplayer game. All these 5 computers are connected with a hub that creates a network. But as I said, it’s an online multiplayer game, so if we are on a local network we can’t play. We need a switch because in the game it will not get to know who is playing what. As we are connected on hub, everyone gets everyone’s data, so it mixes up each other’s info.

So if we connect on a switch, here switch knows who is who through MAC ID. It can send or receive individual’s data now.

But on the local network now, if we connect that switch to router, we can access internet. So the router establishes our connection to game server and now we can play the game together.

But it isn’t safe yet. There are hackers out there who can steal data while we are playing game by mimicking like game data and can enter in those computers. So here in the computer, host based firewall makes sure that it doesn’t happen. And in the game server, there are network based firewalls to make sure we are on a safe network.

Then when we are playing, there are too many active players also playing at the same time. To make sure all can play smoothly without ping issue or packet loss, there are multiple servers available in every country. Load balancer makes sure that our data goes on a server which one isn’t full and can handle our data easily.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769189870524/a1c824ee-a442-45c0-8b2d-f5a8427fe40d.png align="center")

So this is how real world things work.