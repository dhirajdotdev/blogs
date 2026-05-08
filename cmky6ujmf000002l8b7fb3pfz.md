---
title: "TCP Working: 3-Way Handshake and Reliable Communication"
seoTitle: "Understanding TCP: 3-Way Handshake Explained"
seoDescription: "Learn about TCP's 3-way handshake, how it ensures reliable communication, manages sequence and acknowledgements, and handles packet loss effectively"
datePublished: 2026-01-28T15:36:49.623Z
cuid: cmky6ujmf000002l8b7fb3pfz
slug: what-is-tcp-and-why-it-is-needed
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1769614434163/c96add80-9627-4708-9f15-92c75bbc15d3.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1769614585102/c633bd44-1858-465a-b4f8-d1ade308dbfd.png
tags: networking, tcp, chaicode, chaicohort

---

When two computers share data with each other on the internet, they need some protocols to follow to maintain proper data transfer. In the transport layer, which is responsible for sending and receiving data between computers, there are two primary protocols: TCP and UDP.

In this blog I’m gonna share my knowledge about TCP.

---

## What is TCP and why it is needed

Transmission Control Protocol (TCP) is a communication standard of the internet. It delivers data accurately and in order between devices.

TCP has its use cases when we need to send important data in sequence where we can’t afford data loss or these kind of issues where reliability matters more than delay. There we need TCP.

TCP maintains some rules that we will discuss in this blog further. Without these rules, if data is sent, data can get lost and connection can be dropped while sending data.

So TCP exists to make sure communication is reliable and controlled.

---

## Problems TCP is designed to solve

When we want to send data and make sure every single packet should go to the destination, TCP helps with reliability.

If at the time of sending data it goes out of its sequence, then the data gets corrupted and we can’t afford such things. TCP helps with ordering. It checks the packet order and maintains that.

Another factor is loss detection. It solves the problem of loss detection. When packets go very long distance, some packets can get lost. There TCP checks which packet got lost and performs retransmission and sends that packet again.

It also works on flow and congestion control so network doesn’t stop in the process. It adjusts the transmission speed to prevent overwhelming the receiver or the network.

So TCP mainly solves: Data loss, Wrong order, Missing packets, Network overload

---

## TCP 3-Way Handshake

Whenever data needs to be sent between one computer to another in a TCP connection, it needs to confirm in an order that both are ready to send data to each other.

It performs 3 steps for confirmation. That’s why it’s called 3-way handshake.

Think like this using my story:

You call your friend and you are sending money to your friend. First you ask their account number (IP for TCP). Then your friend confirms that given account number is correct. Now you send money (data packets). If you miss some amount, you send again those missed amounts. Then you ask your friend that did they get all of it. Your friend confirms. Then you cut your call.

So before real money transfer, both sides confirm details and after transfer both sides confirm everything is correct.

Same thing happens in TCP before real data transfer starts.

---

## Step-by-step working of SYN, SYN-ACK and ACK

TCP uses three main messages to start a connection: SYN, SYN-ACK and ACK.

### Step 1: SYN

Client sends a packet with SYN flag.

This means: Client is saying: I want to start a connection with you.

This is like asking for account number or knocking on the door.

Client → Server : SYN

---

### Step 2: SYN-ACK

Server receives SYN. Server replies with SYN-ACK.

This means: Server is saying: I got your request and I am also ready to talk.

Server is both acknowledging client and also sending its own request.

Server → Client : SYN-ACK

---

### Step 3: ACK

Client receives SYN-ACK. Client sends ACK.

This means: Client is saying: I got your response and I am ready too.

Now both sides are confirmed and connection is established.

Client → Server : ACK

Now real data transfer can start.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769613820584/d59f3398-b8df-4157-be5d-7ca3ed0fbaef.png align="center")

---

## Sequence numbers and acknowledgements

After handshake, TCP starts sending real data.

TCP does not send data as one big block. It breaks data into smaller packets. Each packet has a sequence number.

Sequence number helps TCP know: Which packet came first Which packet came next If any packet is missing

Receiver sends acknowledgements (ACK) to sender to say: I received this data.

So sender and receiver keep talking like this: Sender sends data Receiver sends ACK Sender sends next data Receiver sends ACK

This is how TCP keeps track of everything.

---

## How data transfer works in TCP

After handshake, data transfer starts.

Sender sends packets with sequence numbers. Receiver checks sequence numbers. Receiver sends ACK for received data.

If packets come in wrong order, TCP reorders them before giving to application.

So even if network messes up order, TCP fixes it for you.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769613846176/29ceca80-4af7-437c-b941-6e45049fec3c.png align="center")

---

## How TCP ensures reliability, order and correctness

TCP ensures reliability by: Using sequence numbers Using acknowledgements Tracking missing packets Retransmitting lost packets

TCP ensures order by reordering packets based on sequence numbers.

TCP ensures correctness by making sure all data is received before giving it to application.

So application always sees clean and complete data.

---

## How TCP handles packet loss

Sometimes packets get lost on the network.

TCP detects packet loss using acknowledgements and timeouts.

If sender does not receive ACK for some packet in time, TCP assumes that packet is lost.

Then sender retransmits that packet again.

So TCP makes sure missing data is sent again until it is received properly.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769613856068/429ecdea-6328-46c5-aed9-de6c681a5aae.png align="center")

---

## Flow and congestion control (simple idea)

TCP also makes sure sender does not send data too fast.

If receiver is slow, TCP slows down sender. If network is congested, TCP reduces speed.

This prevents: Receiver overload Network overload Connection drops

So TCP tries to keep communication stable.

---

## How a TCP connection is closed

Just like connection setup, closing connection also has rules.

TCP uses FIN and ACK to close connection properly.

### Step 1: FIN

One side sends FIN. This means: I am done sending data.

### Step 2: ACK

Other side sends ACK. This means: I got your FIN.

### Step 3: FIN

Other side sends FIN when it is also done.

### Step 4: ACK

First side sends ACK.

Now connection is fully closed.

So both sides agree before closing. This makes sure no data is lost during close.

---

## TCP connection lifecycle

So full TCP flow looks like this:

Connection establish using 3-way handshake Data transfer with sequence numbers and ACKs Packet loss handling using retransmission Connection close using FIN and ACK

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769613896558/d4c83f32-7421-47a6-9363-57750a21dfb8.png align="center")

---

TCP may look complex, but it solves very simple real-world problems. It makes sure two computers can talk reliably.

Without TCP, things like websites, logins, file downloads and emails would break very easily.

TCP is like the protocol that makes sure serious conversation happens properly.