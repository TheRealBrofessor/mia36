> **Behind the Screen** — [Chapter 1-2](chapter-1-2/) · [Chapter 3](chapter-3/) · [**Chapter 4**](chapter-4/) · [Chapter 5](chapter-5/) · [Chapter 6](chapter-6/) · [Chapter 7](chapter-7/) · [Project Memory](project-memory/vision.md)

---

# Chapter 4 — Internet Traffic: Where Does Your Data Actually Go?

> **Behind the Screen** by TheRealBrofessor
> Phase 4 of the beginner-friendly cybersecurity roadmap

---

## You Know the Machine. You Know the Network. Now Watch the Data Move.

Look at what you've accomplished. In Chapter 1, you booted Ubuntu from a USB drive. In Chapter 2, you used the terminal to talk directly to your computer. In Chapter 3, you identified your router, traced the cables, and logged into your network hardware.

That's not a small thing. Most people never do any of that. They just open a browser and hope everything works.

Now you're ready for the next step.

You know what a packet is (Chapter 3). You know what a router looks like (Chapter 3). You know how to open a terminal and run commands (Chapter 2). Now you're going to put all of that together and answer one question — a question most people never think to ask:

**Where does your data actually go when you press Enter?**

Not metaphorically. Not vaguely. You're going to watch it. In real time. See the addresses. See the path. See the moment your data leaves your machine and enters the wider internet.

And here's why this matters for cybersecurity: if you don't know what's leaving your computer, you can't control it. If you can't see your outgoing connections, you won't notice when something is phoning home that shouldn't be.

By the end of this chapter, you'll be able to see every active connection on your machine, explain how a packet reaches a server on the other side of the world, and understand why the person who initiates the connection is the one in control.

Let's watch your data move.

---

## The Big Analogy: Tracking a Package Through Checkpoints

**Ever tracked a package you ordered and watched it move through checkpoints?**

You order something online. At first, the status says "Order Placed." then it updates: "Picked Up." then "Arrived at Sorting Facility." then "Departed Memphis Hub." then "Out for Delivery." then "Delivered."

Each of those updates is a checkpoint. Someone scanned the package's label. They recorded where it was and when. You watched it move step by step across the country (or the world) until it showed up at your door.

**Packets work the same way.**

When you open a website, send a message, or refresh a page, your data doesn't travel as one big blob. It gets broken into small chunks — **packets** — and each one gets a label with your address, the destination address, and other information needed to get it where it needs to go.

And here's what makes this chapter different: today, for the first time, **you're going to watch your own packets move**. You'll see them leave your machine. You'll see where they go. You'll read the labels.

Not theory. Not a textbook. Your actual data, on your actual computer, right now.

---

## What Is a Packet, Really?

You met the postal system analogy in Chapter 3. Now let's get more precise, because understanding packets is the foundation for everything else in this chapter.

### The Problem Packets Solve

Imagine you want to send a 100-page document to someone across the country. You could put it all in one enormous envelope, tape it shut, and hope it survives the trip. But that's fragile. If the envelope gets lost or damaged, you lose everything.

A better approach: put each page in its own envelope. Number them. Send them all. The recipient reassembles them in order.

**That's what a packet is: one small, numbered piece of a larger message.**

Computers do this because:

- **Smaller pieces are more reliable.** If one packet gets lost, only that piece needs to be resent, not the whole file.
- **The network can handle different sizes efficiently.** Small chunks can fill gaps and use bandwidth better.
- **Multiple packets can take different paths.** If one route is congested, individual packets can be rerouted.

### What's Inside a Packet

A packet is two parts:

| Part | What It Is | Postal Equivalent |
|---|---|---|
| **Header** | Control information: source address, destination address, packet number, protocol type, size | The label on the envelope — to/from addresses, weight, tracking barcode |
| **Payload** | The actual data you want to send | The letter inside the envelope |

The header is usually much smaller than the payload. Think of a shipping label on a box. The label takes up almost no space, but it contains all the information needed to route the package.

### A Real Packet Header (Simplified)

Here's what a packet header looks like in plain English:

```
Source IP:      192.168.1.42       (your computer)
Destination IP: 93.184.216.34      (the server you're talking to)
Protocol:       TCP                (reliable delivery)
Packet Number:  3 of 15            (this is the 3rd piece of a 15-piece message)
Size:           1,460 bytes         (how big this specific packet is)
TTL:            64                 (how many routers can forward this before it dies)
```

Every packet is like this. Hundreds are flying through the air and cables around you right this second. Most of them have nothing to do with of them? Those are yours. And starting today, you can see them.

---

## Source and Destination: Your Address and Theirs

### IP Addresses Are Street Addresses for Computers

You already learned about IP addresses in Chapter 3. Now let's deepen that understanding, because you're about to see IP addresses in action on your own machine.

An IP address does for computers what a street address does for houses. When you send a packet, you need to know:

1. **The destination address** — where it's going (the return address on the envelope)
2. **Your source address** — where it came from (so the other side can reply)

Without both, communication doesn't work. A letter with no return address? The recipient can't write back. A letter with no delivery address? It never arrives.

### Two Kinds of IP Addresses You'll See

When you start looking at your actual packets, you'll notice two types of IP addresses:

**Private IP (your local address):**
- Looks like `192.166.x.x` or `10.0.x.x` or `172.16.x.x`
- Assigned by your router
- Only meaningful inside your own network
- This is your address within your "house" — useful locally, invisible to the outside world

**Public IP (your internet address):**
- Assigned by your ISP
- How the internet sees your whole network
- When data leaves your router, it uses this address
- This is like your home's street address — anything going outside needs it

Think of it like an apartment building. Your private IP is "Apt 4B" — useful inside the building, meaningless outside. Your public IP is "123 Main Street" — that's what the postal system actually sees.

### Finding YOUR Addresses Right Now

Let's see yours. Boot into Ubuntu, open a terminal, and run:

```bash
hostname -I
```

That gives you your private IP — your local address. You saw this in Chapter 3.

Now let's see your public IP — the address the internet sees:

```bash
curl ifconfig.me
```

That's your public address. Everything leaving your network to the internet uses that address (until it gets translated by something called NAT, but that's for another chapter).

Write both numbers down. You're going to see them again.

---

## The Full Path: Your Data's Journey Step by Step

When you click a link or open a website, your packet travels through a specific path. Let's trace it. Remember the hardware from Chapter 3 — the cables, the router, the modem? Here's how data moves through all of it.

### Step by Step

```
YOUR COMPUTER
    │
    │  (packet is created with source & destination addresses)
    │  (your OS checks: is the destination on my local network?)
    │  If no → send to the router
    ▼
ROUTER
    │
    │  (router receives the packet on its LAN port)
    │  (router checks the destination address)
    │  (router replaces your private IP with your public IP — NAT)
    │  (router forwards the packet to the modem)
    │
    │  HARDWARE: The packet travels through the physical ports
    │  on the back of your router. You can see the Ethernet port
    │  lights blinking when data moves. That's not decoration —
    │  that's your data, physically leaving your house.
    ▼
MODEM
    │
    │  (modem converts the digital signal to one that can travel
    │   over cable, fiber, DSL, or phone lines)
    │  (modem sends the signal to your ISP)
    ▼
ISP (Internet Service Provider)
    │
    │  (ISP receives your packet at their local infrastructure)
    │  (ISP routes it into their backbone network)
    │  (packet may pass through several ISP routers)
    │  (each router reads the destination address and forwards
    │   the packet one step closer)
    │
    │  HARDWARE: Your packet is now traveling through fiber optic
    │  cables, possibly underground or under the ocean. It's moving
    │  at nearly the speed of light. It's been less than 100
    │  milliseconds since you clicked.
    ▼
THE INTERNET BACKBONE
    │
    │  (large-scale routers and fiber connections between cities,
    │   countries, and continents)
    │  (your packet hops from router to router, each one reading
    │   the destination and forwarding it)
    │
    │  HARDWARE: Massive data centers, undersea cables, and
    │  high-speed routers. Your tiny packet is one of billions
    │  moving through this infrastructure right now.
    ▼
DESTINATION SERVER
    │
    │  (the server receives your packet)
    │  (the server reads the source address — that's YOUR address)
    │  (the server prepares a response)
    │  (the server sends packets back, using your address as the
    │   destination)
    ▼
... and the whole path happens in reverse, back to your screen.
```

### How Many Hops?

Each router your packet passes through is called a **hop**. A typical web request might pass through 10-20 hops between your computer and a server.

You can see this yourself. In your terminal:

```bash
traceroute example.com
```

(If `traceroute` isn't installed, run `sudo apt install traceroute` first.)

Each line is a hop. Each one is a router that touched your packet. You're watching your data's journey in real time.

---

## DNS: The Internet's Phonebook

Before your packet can leave your machine, it needs to know where to go. And here's the thing: **you don't type IP addresses. You type names.**

You type `google.com`, not `142.250.80.46`. You type `wikipedia.org`, not `208.80.154.224`.

So how does your computer know where to send the packet?

### The Phonebook Analogy

Think about how you call someone. You don't memorize phone numbers for everyone you know. You look up their name in your contacts, and your phone translates that name into a number.

**DNS (Domain Name System) is the internet's contacts app.**

When you type a website name:

1. Your computer asks a DNS server: "What IP address belongs to this name?"
2. The DNS server looks it up and replies: "That name is at this IP address."
3. Your computer now has the destination IP and can send the packet.

Without DNS, the internet would still work — but you'd have to memorize IP addresses for every website. DNS is what makes the internet human-friendly.

### Watching DNS in Action

Let's see DNS working on your machine. In your terminal:

```bash
nslookup example.com
```

You'll see something like:

```
Server:     192.168.1.1
Address:    192.168.1.1#53

Non-authoritative answer:
Name:       example.com
Address:    93.184.216.34
```

That's DNS in action. You asked for a name. You got an IP address back. Your computer can now send packets to that address.

### Why DNS Matters for Security

Here's something to think about: **someone can see what DNS requests you make.** Your ISP, your network administrator, or anyone monitoring your network can see that you looked up `example.com`, even if they can't see the full content of what you did there.

DNS is usually not encrypted (though that's changing with newer protocols). That means your DNS requests are like sending postcards — anyone handling them can read what's written on them.

This is why DNS matters for cybersecurity. It's one of the first places to look when you want to understand what a computer is doing.

---

## Watching Your Outgoing Connections: The Terminal Commands

This is the part you've been building toward. You know what packets are. You know the path they take. Now let's see them on YOUR machine.

### `curl -v`: Watch a Connection Happen in Real Time

`curl` is a command that fetches data from the internet. The `-v` flag means "verbose" — show me everything that happens.

Run this:

```bash
curl -v https://example.com
```

You'll see output like this (simplified):

```
*   Trying 93.184.216.34:443...
* Connected to example.com (93.184.216.34) port 443
> GET / HTTP/1.1
> Host: example.com
> User-Agent: curl/7.81.0
> Accept: */*
>
< HTTP/1.1 200 OK
< Content-Type: text/html
< Content-Length: 1256
...
```

Let's break down what you're seeing:

- `* Trying 93.184.216.34:443...` — Your computer resolved `example.com` to an IP address (DNS!) and is trying to connect to port 443 (HTTPS).
- `* Connected to example.com (93.184.216.34) port 443` — The connection was established. Your data has a path to the server.
- Lines starting with `>` — These are the headers your computer SENT to the server. Your request.
- Lines starting with `<` — These are the headers the server SENT BACK. The response.

**You just watched your data leave your machine, travel to a server, and come back.** That's not a simulation. That's real.

### `ss`: See ALL Active Connections on Your Machine

`ss` (socket statistics) shows you every network connection your computer currently has open. Think of it as a live view of everything your machine is talking to.

Run this:

```bash
ss -tuln
```

The flags mean:
- `-t` — show TCP connections
- `-u` — show UDP connections
- `-l` — show only listening connections (services waiting for incoming data)
- `-n` — show IP addresses instead of names (faster, and you see the real addresses)

You'll see output like:

```
State      Recv-Q     Send-Q       Local Address:Port         Peer Address:Port
LISTEN     0          4096         0.0.0.0:22                 0.0.0.0:*
LISTEN     0          511          127.0.0.1:631              0.0.0.0:*
ESTAB      0          0            192.168.1.42:54231        93.184.216.34:443
```

Let's read this:

- **State**: `LISTEN` means your computer is waiting for incoming connections on that port. `ESTAB` (established) means there's an active connection right now.
- **Local Address:Port**: Your computer's address and the port it's using.
- **Peer Address:Port**: The remote address and port you're connected to.

That third line? That's an active connection from your machine (`192.168.1.42`) to a server (`93.184.216.34`) on port 443 (HTTPS). That's your `curl` command from earlier, still showing up.

### `netstat`: The Older Alternative

`netstat` does the same thing as `ss` but is older. Some systems still have it:

```bash
netstat -tuln
```

If it's not installed, use `ss` — it's faster and more modern. But if you see tutorials using `netstat`, know that it's showing the same information.

### What to Look For

When you run `ss -tuln`, ask yourself:

- **Do I recognize every connection?** If you see an established connection to an IP you don't recognize, that's worth investigating.
- **Are there services listening that shouldn't be?** If you see something listening on a port you didn't set up, find out what it is.
- **How many connections are active?** A typical idle machine might have a few. A busy one might have dozens. Know your baseline.

This is one of the most practical cybersecurity skills you can develop: **knowing what your own machine is doing.** If something unexpected shows up, you'll notice.

---

## Why Outgoing Traffic Matters Most

Here's a concept that changes how you think about security:

**If YOU initiate a connection, YOU control what leaves your machine.**

This is huge. Let me explain.

### Outgoing vs. Incoming

**Outgoing traffic** — connections your computer initiates. You open a browser. You check email. You run an update. Your computer reaches out to a server.

**Incoming traffic** — connections initiated by something else. Someone tries to connect to your computer. A server pushes data to you. A scan probes your machine.

### Why Outgoing Is What You Control

When you initiate an outgoing connection:

- **You chose the destination.** You decided to visit that website, use that app, run that command.
- **You control what you send.** Your data, your credentials, your files — they only go where you tell them to.
- **You can see it happening.** As you just learned, `ss` and `curl -v` show you exactly what's leaving.

When someone else initiates an incoming connection:

- **You didn't choose it.** It just shows up.
- **Your firewall decides what to do with it.** (More on that in a moment.)
- **You might not even notice it happened.**

### The Security Implication

Here's the key insight: **most of the data that leaves your machine does so because YOU told it to.**

- You installed an app that phones home? That's outgoing traffic. You chose to install it.
- You visited a website that tracks you? That's outgoing traffic. You chose to visit.
- You entered your password into a form? That's outgoing traffic. You chose to type it.

This doesn't mean you're to blame for privacy violations. It means **you have more control than you think.** Every outgoing connection is a choice. And once you can see those choices (using `ss`, `curl -v`, and the other tools from this chapter), you can make better ones.

### The Other Side: Malware and Unexpected Outgoing Traffic

Here's where this gets serious. If malware gets onto your machine, it often needs to communicate outward — to receive instructions, to send stolen data, to report back to its controller.

That communication is **outgoing traffic that YOU didn't initiate.**

And that's why watching your outgoing connections matters. If you run `ss` and see your machine connected to an IP address you don't recognize, on a port you didn't open, to a server you've never heard of — that's a red flag.

You might not know what it is. But you'll know it's there. And that awareness is the first step to catching something wrong.

---

## Firewalls: The Checkpoint That Decides What Gets Through

You've seen the path your data takes. Now let's talk about the checkpoint along the way.

### What a Firewall Does

A **firewall** is a filter. It sits between your computer and the network (or between your network and the internet) and inspects every packet that tries to pass through.

For each packet, the firewall asks:

- **Where is this packet coming from?**
- **Where is it going?**
- **Is this allowed?**

Based on the answers, the firewall does one of two things:
- **Allow** — the packet passes through
- **Block** — the packet is dropped, silently or with a rejection notice

### The Checkpoint Analogy

Think of a firewall like a security checkpoint at a building entrance:

- People with badges get through (allowed traffic).
- People without badges get stopped (blocked traffic).
- The security guard has a list of rules: who's allowed, who isn't, what hours the building is open, which doors are accessible.

A firewall works the same way, but for data instead of people.

### Two Types of Firewalls

**Software firewall** — runs on your computer. It controls what that specific machine can send and receive. Ubuntu comes with one built in: `ufw` (Uncomplicated Firewall).

**Hardware firewall** — built into your router. It controls what enters and leaves your entire network. Every packet going to or from the internet passes through it.

You have both. Your router's firewall protects your whole network. Your computer's firewall protects just your machine.

### Checking Your Firewall on Ubuntu

Let's see if your firewall is active:

```bash
sudo ufw status
```

You'll see either `Status: active` or `Status: inactive`.

If it's inactive, you can enable it:

```bash
sudo ufw enable
```

And you can see the rules:

```bash
sudo ufw status verbose
```

By default, Ubuntu's firewall denies incoming connections and allows outgoing ones. That's a sensible default: you can reach out to the internet, but the internet can't reach into your machine without permission.

### Why Firewalls Matter for This Chapter

Remember: you just learned to see your outgoing connections with `ss`. A firewall is the tool that controls which of those connections are allowed to happen in the first place.

- Want to block a specific website? Firewall rule.
- Want to stop a program from phoning home? Firewall rule.
- Want to prevent incoming connections from a suspicious IP? Firewall rule.

The firewall is your enforcement mechanism. `ss` and `curl -v` are your visibility tools. Together, they give you both the eyes and the authority to control your network traffic.

---

## The Physical Side: Your Data Is Real, and It Travels Through Real Things

It's easy to think of internet traffic as abstract — invisible, weightless, happening "in the cloud." But your data is physical. It moves through real hardware, real cables, and real infrastructure.

Let's ground what you've learned in physical reality.

### Your Computer

Your data starts here. It's electrical signals in your processor, then electrical signals on your network interface card (NIC). If you're on Wi-Fi, those signals become radio waves broadcast from your antenna. If you're on Ethernet, they become electrical signals on a copper wire.

### The Ethernet Cable

That cable plugged into the back of your computer? It's carrying your data right now. Electrical pulses representing 1s and 0s, moving at a significant fraction of the speed of light. The cable is shielded to prevent interference, and the connector (RJ-45) has eight tiny wires inside, each carrying part of the signal.

If you're on Wi-Fi, the same data is being broadcast as radio waves from your computer's antenna. Those waves travel through the air, through walls, to your router's antenna. Anyone within range could theoretically intercept those signals. (That's why Wi-Fi encryption matters — but that's a later chapter.)

### The Router's Ports

Your packet arrives at your router through one of its LAN ports (or via Wi-Fi). Inside the router, a processor reads the packet's destination address and decides where to send it next. The router's operating system (yes, routers have operating systems) runs the logic that forwards your packet toward the internet.

The lights on the back of your router? They correspond to physical ports. When they blink, data is physically moving through that port. You can watch your data leave your house by watching those lights.

### The Modem

Your router hands the packet to the modem. The modem's job is to convert the digital signal from your network into a format that can travel over your ISP's infrastructure — whether that's coaxial cable, fiber optic, DSL phone line, or cellular signal.

If you have fiber, your data becomes pulses of light traveling through a glass thinner than a human hair. If you have cable, it's electrical signals on coaxial wire. If you have DSL, it's electrical signals on a phone line.

### The ISP's Infrastructure

Once your packet leaves your modem, it enters your ISP's network. This is a vast infrastructure of cables, routers, switches, and data centers. Your packet might travel through underground conduits, along telephone poles, or through fiber optic cables buried alongside highways.

At each step, routers read your packet's destination address and forward it one hop closer. Each router makes a decision in milliseconds. Your packet might pass through 10-20 of these before reaching its destination.

### The Destination Server

Your packet arrives at a server — a computer in a data center, sitting in a rack, connected to the internet via high-speed fiber. The server's network interface card receives the electrical or optical signals and converts them back into digital data. The server's operating system processes your request and sends a response back along the same path.

The whole trip — from your click to the server's response — typically takes between 50 and 200 milliseconds. In that time, your data traveled through dozens of physical devices, possibly across a continent or an ocean, and back.

**That's not magic. That's infrastructure. And now you can see it happening.**

---

## Putting It All Together: The Cumulative Exercise

You've been building skills across four chapters. Now let's use all of them at once.

### The Exercise

Do these steps in order. Don't skip any. Each one builds on the last.

**Step 1: Boot into Ubuntu**

You know how to do this from Chapter 1. Boot from your USB drive or your installed system. Get to the desktop.

**Step 2: Open a Terminal**

You know how to do this from Chapter 2. Open the terminal. You're going to use it for everything else.

**Step 3: Watch a Connection Happen**

Run this command:

```bash
curl -v https://example.com
```

Watch the output. See the IP address your computer connects to. See the request headers going out. See the response headers coming back. That's your data, leaving your machine, reaching a server, and returning.

Note the IP address you connected to. Write it down.

**Step 4: See All Active Connections**

Now run:

```bash
ss -tuln
```

Look at the output. See the established connections. See the listening ports. That's everything your machine is doing on the network, right now, in this moment.

If you still have the terminal open from your `curl` command, you might see the connection to `example.com` in the list.

**Step 5: Run a Traceroute**

Run:

```bash
traceroute example.com
```

Watch the hops. Each line is a router that touched your packet. You're seeing the physical path your data takes.

### What You Just Did

Let that sink in. You:

1. Booted a computer into a real operating system (Chapter 1)
2. Used the terminal to run commands (Chapter 2)
3. Identified your network hardware and understood its role (Chapter 3)
4. Watched your data leave your machine, travel to a server, and come back (Chapter 4)
5. Saw every active connection on your computer (Chapter 4)
6. Traced the physical path your packets took (Chapter 4)

**You just watched your data leave and arrive.** That's not a beginner exercise. That's real network awareness. That's the foundation of cybersecurity.

---

## Common Mistakes and Gotchas

### "I ran `ss` and saw a connection I don't recognize. Am I hacked?"

Probably not. Many programs make background connections — update checks, time synchronization, cloud sync services, telemetry. Before panicking, look up the IP address. You can use:

```bash
nslookup <IP address>
```

Or just search the IP in a browser. Most will turn out to be legitimate services.

### "My `curl -v` output is overwhelming."

That's normal. The verbose output includes a lot of information. Focus on the lines that start with `*` (connection info) and the first `>` line (your request). The rest is details you'll learn to read over time.

### "Traceroute shows `* * *` on some hops."

That means that router isn't responding to traceroute probes. This is common — many routers are configured not to respond to the specific messages traceroute uses. It doesn't mean your packet didn't go through. It just means that particular router is quiet.

### "I don't have `traceroute` installed."

Run `sudo apt install traceroute`. Same goes for `nslookup` ( doesn't install every tool by default.

### "My firewall was already active."

Good. That's the default on many Ubuntu installations. Check the rules with `sudo ufw status verbose` to see what's allowed and what's blocked.

---

## Cheat Sheet

Print this. Stick it on your wall. Reference it when you forget.

| Term | What It Means | One-Line Definition |
|---|---|---|
| **Packet** | A small chunk of data with a header | A labeled envelope carrying a piece of your data |
| **Header** | The control information on a packet | The shipping label — source, destination, size, number |
| **Payload** | The actual data inside the packet | The letter inside the envelope |
| **IP Address** | A unique address for a device on a network | A street address for computers |
| **Source IP** | Where the packet came from | The return address |
| **Destination IP** | Where the packet is going | The delivery address |
| **Private IP** | Your address on the local network | Your apartment number |
| **Public IP** | Your address on the internet | Your street address |
| **DNS** | The system that translates names to IPs | The internet's phonebook |
| **Router** | Forwards packets between networks | The post office |
| **Modem** | Converts signals for the ISP's infrastructure | The translator between your network and the street |
| **ISP** | Your internet service provider | The company that connects you to the internet |
| **Hop** | One router a packet passes through | One checkpoint on the journey |
| **Port** | A numbered endpoint for a specific service | A specific door on a building |
| **Firewall** | A filter that allows or blocks traffic | The security checkpoint |
| **Outgoing** | Traffic your computer initiates | Mail you send |
| **Incoming** | Traffic initiated by others | Mail you receive |
| **`curl -v`** | Fetch a URL and show all connection details | Your package tracking tool |
| **`ss`** | Show all active network connections | Your connection viewer |
| **`traceroute`** | Show every hop between you and a destination | Your route map |
| **`nslookup`** | Look up the IP address for a domain name | Your phonebook query |
| **`ufw`** | Ubuntu's built-in firewall | Your checkpoint guard |

---

## Remember This

> It's never too late to learn cybersecurity. You don't need to understand every protocol or memorize every port number. You just need to be willing to look at what your own machine is doing and stop treating the internet like a mystery.

Today, you watched your data leave your computer. You saw the IP addresses. You traced the path. You used the terminal to see every active connection on your machine. You looked at the physical infrastructure that carries your packets.

That's not nothing. That's visibility. And visibility is the foundation of security.

You can't protect what you can't see. Now you can see.

---

## Day 4 Win

Here's what you did today:

- You understand what a packet is — a small chunk of data with a header, like a labeled envelope
- You know the difference between source and destination IP addresses
- You can trace the full path your data takes from your computer to a server and back
- You used `curl -v` to watch a connection happen in real time
- You used `ss` to see every active connection on your machine
- You used `traceroute` to see every hop between you and a destination
- You understand DNS as the phonebook that translates names to IP addresses
- You know why outgoing traffic matters — because you control what leaves your machine
- You understand firewalls as the checkpoints that decide what gets through
- You connected the physical hardware (cables, routers, modems) to the data flowing through them
- You combined all four chapters into one cumulative exercise

That's a lot. And you did it by building on what you already knew.

---

*Next up: Chapter 5 — Web Safety. Now that you can see where your data goes, let's learn if those destinations are safe. How do you know if a website is legitimate? What does that little padlock icon actually mean? And what happens to your data after you hand it over? Keep going.*
