> **Behind the Screen** — [Chapter 1-2](chapter-1-2/) · [**Chapter 3**](chapter-3/) · [Chapter 4](chapter-4/) · [Chapter 5](chapter-5/) · [Chapter 6](chapter-6/) · [Chapter 7](chapter-7/) · [Project Memory](project-memory/vision.md)

---

# Chapter 3 — Networking: Router, Switch, Ethernet, OSI, TCP/IP

> **Behind the Screen** by TheRealBrofessor
> Phase 3 of the beginner-friendly cybersecurity roadmap

---

## You Already Have the Hard Skills — Now Let's Connect Them

Look at what you've done so far. In Chapter 1, you booted into Ubuntu from a USB drive. In Chapter 2, you opened a terminal and ran commands like `pwd`, `ls`, and `whoami`. Those weren't small things. You proved you can interact with a computer on its own terms — not just clicking icons, but actually talking to the machine.

Now it's time to connect that machine to something bigger.

Because here's the truth: a computer by itself is useful. A computer *connected to a network* is powerful. And a computer connected to the internet — well, that's the world you live in every day. But do you actually know what happens between your screen and the rest of the world?

That's what this chapter is about. Not abstract theory. Not certification-exam memorization. We're going to answer one question, over and over, from different angles:

**What goes from what to make everything work?**

By the end, you'll understand the path your data takes — from your keyboard, through your machine, out your router, and into the wider world. You'll know what a router actually looks like, what a switch does, why your ethernet cable matters, and how the whole system fits together.

And you'll do it all using skills you already have: booting Ubuntu and opening a terminal.

Let's go.

---

## The Big Analogy: The Internet Is the World's Postal System

Before we touch any hardware or commands, let's build a mental model that will carry you through this entire chapter.

**The internet is the world's postal system.**

Think about how mail works in real life:

- You write a letter (that's your data — an email, a web request, a video stream).
- You put it in an envelope with an address on it (that's a **packet**).
- You drop it in a mailbox or take it to the post office (that's your **router**).
- Inside the post office, workers sort the mail by zip code and route it toward the right destination (that's a **switch**).
- The letter travels through sorting facilities, trucks, and planes (that's the internet's backbone).
- It arrives at the destination post office, gets sorted again, and ends up in the right mailbox.
- If you're sending something important, you might use a tracking number so you know it arrived (that's **TCP**).

Here's the full mapping:

| Postal World | Networking World | What It Does |
|---|---|---|
| The postal system | The internet | The global infrastructure that moves data from place to place |
| A letter | A packet | A small chunk of data with an address on it |
| The post office | Your router | The place where your local mail enters and leaves the system |
| The mail sorter | A switch | Directs mail to the right local destination |
| A tracking number | TCP | Makes sure your letter arrived and in the right order |
| A postcard | UDP | Sends a message without confirmation — faster, but no guarantee |

Keep this analogy in your back pocket. We'll come back to it. It's going to make everything easier.

---

## Meet Your Router — The Post Office of Your Home

Go look at the box with the blinking lights in your house. It might be on a shelf, in a closet, or behind your desk. That box is your **router** — the single most important piece of networking hardware you own.

### What a Router Actually Looks Like

**The outside:**
- A rectangular box, usually black or white, from paperback-book to pizza-box size.
- **Lights on the front** (LED indicators):
  - **Power** — solid means on. Blinking during startup is normal.
  - **Internet/WAN** — solid means connected to your provider. Blinking means data flowing. Off means no internet.
  - **Wi-Fi lights** — often two (2.4 GHz and 5 GHz). Blinking means wireless activity.
  - **Ethernet port lights** — one per port on the back. Solid/blinking means something's connected.
- **Antennas** — some have external sticks. More antennas generally means better coverage. Some modern routers hide them inside.

**The back panel:**
- **Power port** — where the power cable plugs in.
- **WAN/Internet port** — usually a different color (blue or yellow). This connects to your modem or wall jack. Your front door to the internet.
- **LAN ports** (usually 4) — for wired connections (computer, game console, smart TV).
- **USB port** (some models) — for sharing a printer or drive.
- **Reset button** — tiny pinhole. Hold 10 seconds with a paperclip to factory reset.
- **WPS button** — for easy device pairing (you may want to disable this later).

**The sticker on the bottom/back:**
- Default network name (SSID)
- Default Wi-Fi password
- Default admin username and password
- Router's IP address

> **Security note:** That sticker is the first thing someone near your router would look at. If you're still using the default admin password, anyone within range can log in and change your settings.

### What Your Router Does

| Job | What It Means |
|---|---|
| **Assigns addresses** | Every device gets a unique IP address so data goes to the right place |
| **Directs traffic** | When your phone asks for a website, the router sends the answer to your phone — not your laptop |
| **Connects two worlds** | It's the bridge between your private home network and the public internet |

### The Router's Admin Page

Every router has a built-in webpage for configuration — the **admin page**. You access it by typing the router's IP address into a browser. It's where you:
- See connected devices
- Change Wi-Fi name and password
- Update firmware
- Change the admin password (you should do this)
- Control your entire home network

---

## Modem vs. Router — Why Some Homes Have Two Boxes

### The Modem

The modem talks to your internet provider. It translates the signal from outside (cable, phone line, or fiber) into something your home can use.

**What it looks like:** A simpler box than a router. Often has just two ports — one to the wall, one Ethernet port to the router. Fewer lights. No antennas.

**Key point:** A modem alone gives you internet for only ONE device. It doesn't create a network, assign IPs, or broadcast Wi-Fi. It's just a translator.

### The Combo Box (What Most People Have)

Most providers give you a single box combining **modem + router + Wi-Fi** into one device (called a "gateway"). That's why most people only have one box — it's doing three jobs at once.

**How to tell what you have:**
- One box with antennas and multiple Ethernet ports → combo
- Two boxes connected by a cable → the one connected to the wall is the modem, the other is the router
- Not sure? Look up the model number online.

---

## The Switch — The Mail Sorter Inside Your Building

A **switch** connects multiple wired devices on the same local network. It's like a power strip for network cables — it gives you more Ethernet ports.

But a switch is smarter than a power strip. It learns which devices are connected to which ports and sends data only to the intended recipient — not to every device. This makes the network faster and more efficient.

### Switch vs. Router

| | Router | Switch |
|---|---|---|
| **Job** | Connects different networks (home ↔ internet) | Connects devices within the same network |
| **Analogy** | The post office | The mail sorter in the building |
| **Assigns IPs?** | Yes (via DHCP) | No |
| **Wi-Fi?** | Usually | No (wired only) |
| **Ports** | 1 WAN + 4 LAN | 5, 8, 16, 24, or 48 LAN ports |
| **Where** | Homes and small businesses | Offices, server rooms, larger homes |

**In plain language:** The router is the boss — it connects you to the internet. The switch is the assistant — it handles local traffic between wired devices.

Most homes don't need a separate switch because the router has 4 LAN ports. But if you need more wired connections (desktop PC, game console, smart TV, printer, security cameras), you add a switch.

### What a Switch Looks Like

- No WAN port (all ports are LAN)
- No antennas (wired-only)
- More ports than a router (8, 16, 24, or 48)
- Simpler lights — just link/activity indicators
- Often rack-mounted in offices, or small desktop units for home

---

## Ethernet Cables — The Physical Roads Your Data Travels On

None of the hardware we've discussed works without physical cables connecting everything. Let's talk about what's actually in your hands when you plug in a network cable.

### What Is Ethernet?

Ethernet is the standard way computers connect to a network using a cable. When you plug a cable from your computer into your router, you're using Ethernet.

### What an Ethernet Cable Looks Like

An Ethernet cable looks like a thick phone cable. The connector (called an **RJ45 connector**) is a clear plastic clip that clicks into place when you push it into a port. To unplug it, press the little tab down and pull.

Key features:
- **The connector** — clear plastic clip, slightly wider than a phone connector
- **The click** — you should hear and feel it click into place
- **The tab** — the little plastic lever on top that holds it in place (be gentle — it can break off)
- **The cable** — usually round, various colors (blue is most common)

### CAT5, CAT5e, CAT6 — What's the Difference?

| Cable Type | Max Speed | What It Means for You |
|---|---|---|
| **CAT5** | 100 Mbps | Obsolete. Don't use for new setups. |
| **CAT5e** | 1 Gbps | The minimum you should use today. |
| **CAT6** | 1 Gbps (10 Gbps short distances) | Better for modern homes. More future-proof. |
| **CAT6a** | 10 Gbps | For power users. Thicker, less flexible. |

**The simple version:** Buy **CAT5e at minimum, CAT6 if you can.** They cost about the same (a few dollars). CAT5 is outdated — if you have old CAT5 cables, consider replacing them.

### Why Ethernet Matters (Even in a Wi-Fi World)

1. **Speed** — Wired is almost always faster than Wi-Fi, especially for large transfers.
2. **Reliability** — Wi-Fi can be affected by interference (microwaves, walls, neighbors). Ethernet is a direct, dedicated connection.
3. **Latency** — For gaming or video calls, wired has lower delay.
4. **Security** — Someone has to physically plug in to intercept wired traffic. Wi-Fi goes through walls.
5. **The backbone** — Even if your laptop uses Wi-Fi, the router-to-modem and router-to-switch connections run on Ethernet.

> **Practical tip:** If your desktop PC or game console is near the router, plug it in with Ethernet. Better performance, and you free up Wi-Fi for your phone and tablet.

---

## Wi-Fi Access Points — Broadcasting Your Network Through the Air

A **Wi-Fi access point** broadcasts your network wirelessly. In most homes, the router IS the access point — it's built right in. But in larger spaces, a separate access point extends coverage to areas the main router can't reach.

### How Wi-Fi Works (Simple Version)

Your router broadcasts on specific frequencies:
- **2.4 GHz** — Slower, travels farther, penetrates walls better. Good for devices far from the router.
- **5 GHz** — Faster, shorter range. Best for devices close to the router.
- **6 GHz (Wi-Fi 6E)** — Newest, fastest, shortest range. Only on newest devices.

### Wi-Fi vs. Internet — Not the Same Thing

**Wi-Fi is a local connection.** It connects your devices to your router. When your laptop prints to your wireless printer, that never leaves your house.

**The internet is a global connection.** It connects your home to the rest of the world.

**The router connects the two.** Wi-Fi is the hallways inside your building. The internet is the street outside. The router is the front door.

---

## IP Addresses — Every Device Needs a Home Address

Every device on your network has an **IP address** — a unique number that identifies it. Think of it like a home address for your devices.

**Private IP addresses (inside your home):** Every device gets an internal address like `192.168.1.5`. These only matter inside your home — like apartment numbers within a building.

**Public IP address (outside your home):** Your entire home shares one public IP when talking to the internet. Assigned by your provider. Like the street address of your building.

**How data finds its way:**
1. Your laptop (private IP) sends a request to your router
2. Your router forwards it to the internet using your public IP
3. The website responds to your public IP
4. Your router remembers which device asked and delivers it to the right private IP

This is **NAT (Network Address Translation)** — the router mapping between private and public addresses.

---

## The OSI Model — The 7 Layers of Networking

Now let's zoom out and look at the big picture. How does data actually travel from your computer to a server on the other side of the world?

Computer scientists created a model called the **OSI model** (Open Systems Interconnection) that breaks networking into 7 layers. Each layer handles a specific job, and they all work together to move data from one place to another.

Don't let the name intimidate you. Each layer is simple on its own. Let's go through them from top to bottom — from what you see to what's actually happening.

### The 7 Layers (Plain English)

| Layer | Name | Plain English | What It Does |
|---|---|---|---|
| **7** | Application | The app you're using | This is your web browser, email app, or game. It says "I want to visit this website." |
| **6** | Presentation | The translator | Formats data so the other side can understand it. Encryption happens here. |
| **5** | Session | The conversation manager | Opens, maintains, and closes the connection between two devices. |
| **4** | Transport | The delivery service | Makes sure data arrives completely and in order. This is where TCP and UDP live. |
| **3** | Network | The address system | Figures out the best path for data to travel. IP addresses live here. |
| **2** | Data Link | The local delivery | Moves data between devices on the same local network. MAC addresses live here. |
| **1** | Physical | The actual wire | The cables, radio waves, and electrical signals. The hardware. |

### The Postal Analogy for OSI Layers

Let's map the postal system to the OSI layers:

| OSI Layer | Postal Analogy |
|---|---|
| **7 - Application** | You writing a letter |
| **6 - Presentation** | Translating the letter into a language the recipient understands |
| **5 - Session** | Deciding to start a pen pal relationship |
| **4 - Transport** | Choosing certified mail (TCP) or a postcard (UDP) |
| **3 - Network** | Writing the destination address on the envelope |
| **2 - Data Link** | The mail carrier who picks up the letter from your mailbox |
| **1 - Physical** | The roads, trucks, and planes that move the mail |

### Why Should You Care?

When something goes wrong, the layers help you find *where* the problem is:

- Can't connect to Wi-Fi? → Layer 1 (Physical) or Layer 2 (Data Link)
- Connected but no internet? → Layer 3 (Network) — IP or routing issue
- Website looks broken? → Layer 6 (Presentation) — formatting/encryption
- Website is slow? → Layer 4 (Transport) — TCP issue

You don't need to memorize the layers now. Just understand: networking is a stack of jobs, each layer handles one piece.

---

## TCP/IP — The Language of the Internet

The OSI model is a *conceptual* model — it helps us understand how networking works. But the internet actually runs on a different set of rules called **TCP/IP** (Transmission Control Protocol / Internet Protocol).

TCP/IP is simpler than OSI — it combines some of the layers into a 4-layer model:

| TCP/IP Layer | OSI Layers It Combines | What It Does |
|---|---|---|
| **Application** | 5, 6, 7 | Your apps and the data they produce |
| **Transport** | 4 | TCP or UDP — how data is delivered |
| **Internet** | 3 | IP addresses and routing |
| **Network Access** | 1, 2 | The physical connection and local delivery |

### TCP vs. UDP — The Two Ways to Send Data

**TCP (Transmission Control Protocol):** Connection-oriented. Establishes a connection first, guarantees delivery, guarantees order. Slower but reliable. Used for web pages, email, file transfers — anything where you need every piece.

**UDP (User Datagram Protocol):** Connectionless. Just sends data — no guarantees of delivery or order. Faster but less reliable. Used for video streaming, gaming, live broadcasts — where speed matters more than perfection.

**One-sentence summary:**
- **TCP** is certified mail with a tracking number — reliable but takes longer.
- **UDP** is shouting across a crowded room — fast, but no guarantee they heard you.

### The Three-Way Handshake

TCP establishes a connection with a three-step process:

1. **SYN** — Your computer: "Hey, I'd like to connect." (Knock knock.)
2. **ACK-SYN** — The server: "I hear you, and I'd like to connect too." (Who's there? I'm here.)
3. **ACK** — Your computer: "Great, let's go." (Let's talk.)

Only after this handshake does data flow. Both sides agree they're ready first — that's what makes TCP reliable.

---

## Putting It All Together: The Path Your Data Takes

Let's trace a real request from start to finish. You type "example.com" into your browser and press Enter. Here's what happens:

1. **Your browser** creates an HTTP request (Layer 7).
2. **TCP** breaks it into segments and initiates the three-way handshake with the server (Layer 4).
3. **IP** wraps each segment in a packet with your address and the destination address (Layer 3).
4. **Your network card** wraps it in a frame with MAC addresses and converts it to electrical signals or radio waves (Layers 1-2).
5. **Your router** receives it, replaces your private IP with your public IP (NAT), and forwards it to the internet.
6. **Routers across the internet** hop the packet closer to the destination, each reading the IP address and forwarding it.
7. **The server** receives the packet, processes it up through the layers, and sends a response back.
8. **Your router** receives the response, translates the public IP back to your private IP, and forwards it to your device.
9. **TCP** reassembles the segments in order, the browser renders the page, and you see the website.

All of this happens in milliseconds.

**The postal version:** You write a letter → put it in an envelope with an address → hand it to your post office (router) → it travels through sorting facilities (internet routers) → arrives at the destination → the recipient reads it and writes back → the response travels back through the postal system → your post office delivers it to your mailbox.

---

## Cheat Sheet

Here's a quick reference for the most important facts from this chapter. Keep this handy.

### Router Admin Page Address Format

Your router's admin page is accessed by typing an IP address into your browser's address bar:

```
http://192.168.1.1
```

It always starts with `http://` (not `https://` — router admin pages usually don't use encryption for the local connection) and uses a private IP address.

### Common Manufacturer Router IPs

| Manufacturer | Default IP Address |
|---|---|
| **Netgear** | `192.168.0.1` or `192.168.1.1` |
| **Linksys** | `192.168.1.1` |
| **TP-Link** | `192.168.0.1` or `192.168.1.1` |
| **ASUS** | `192.168.1.1` or `192.168.50.1` |
| **Xfinity/Comcast** | `10.0.0.1` |
| **AT&T** | `192.168.1.254` |
| **Google Nest** | `192.168.86.1` |
| **Eero** | `192.168.4.1` |

> **Note:** If none of these work, use the terminal command `ip route show` (see the exercise below) to find your actual router address.

### OSI Layers in Plain English

| Layer | Name | One-Line Description |
|---|---|---|
| **7** | Application | The app you're using (browser, email, game) |
| **6** | Presentation | Formats and encrypts data so both sides understand it |
| **5** | Session | Manages the connection between two devices |
| **4** | Transport | Makes sure data arrives completely (TCP) or quickly (UDP) |
| **3** | Network | Addresses and routes data using IP addresses |
| **2** | Data Link | Moves data between devices on the same local network |
| **1** | Physical | The actual cables, radio waves, and electrical signals |

**Memory trick:** "Please Do Not Throw Sausage Pizza Away" (bottom to top) or "All People Seem To Need Data Processing" (top to bottom).

### TCP vs. UDP (One Sentence Each)

- **TCP:** A connection-oriented protocol that guarantees your data arrives completely and in the right order — like certified mail with a tracking number.
- **UDP:** A connectionless protocol that sends data as fast as possible without guaranteeing delivery — like a postcard dropped in a mailbox.

---

## Common Networking Myths (Busted)

- **"Wi-Fi and the internet are the same thing."** — Wi-Fi connects devices to your router. The internet connects your router to the world. You can have one without the other.
- **"My network is too small for anyone to care about."** — Attackers use automated tools that scan millions of addresses. You're not targeted — you're just in a wide net.
- **"If my internet is working, my network is fine."** — Working internet just means the connection is active. It says nothing about who else is connected.
- **"Ethernet cables are all the same."** — CAT5 is outdated. CAT5e is the minimum. CAT6 is better. Old cables can limit your speed.
- **"The router my provider gave me is good enough."** — It's fine for basic use, but often has weaker security and range than a good standalone router.

---

## Why This Matters for Cybersecurity

1. **Your router is the front door.** If someone gains access, they can see your traffic, redirect connections, or lock you out. Understanding it is the first step to securing it.
2. **Every device is a potential entry point.** Smart TVs, printers, cameras — anything on your network can be a target. Know what you have.
3. **Network knowledge is security knowledge.** Firewalls, intrusion detection, VPNs, packet analysis — all work at the network level. You can't defend what you don't understand.
4. **The path data takes is the path an attack can take.** Understanding packet flow means you can understand interception — and how to stop it.

---

## The Vocabulary of Networking (Quick Reference)

| Term | Plain Meaning |
|---|---|
| **Router** | Directs traffic between your home network and the internet |
| **Switch** | Connects multiple wired devices on the same local network |
| **Modem** | Connects your home to your internet provider |
| **Access Point** | Broadcasts Wi-Fi to extend wireless coverage |
| **Gateway** | Combo device: modem + router + Wi-Fi in one box |
| **Ethernet** | Physical cable connection for networking |
| **IP Address** | Unique number identifying a device on a network |
| **Private IP** | Address used inside your home (like `192.168.x.x`) |
| **Public IP** | Address your whole network uses on the internet |
| **MAC Address** | Hardware-specific identifier burned into every network device |
| **NAT** | Router translating between private and public IP addresses |
| **TCP** | Reliable protocol that guarantees data delivery |
| **UDP** | Fast protocol that sends data without guarantees |
| **Packet** | Small chunk of data with addressing information |
| **Frame** | Packet wrapped with local network addressing (Layer 2) |
| **Admin Page** | Webpage built into your router for configuration |
| **DHCP** | Service that automatically assigns IP addresses |
| **DNS** | System that translates domain names to IP addresses |
| **CAT5/CAT6** | Cable categories with different speed capabilities |
| **WAN** | Wide Area Network — the port connecting to the internet |
| **LAN** | Local Area Network — the ports connecting to your devices |

---

## Cumulative Exercise: Chapters 1, 2, and 3 Combined

This is the big one. You're going to use everything you've learned so far — booting Ubuntu, using the terminal, and understanding your network — in one smooth sequence.

**Here's what to do:**

### Step 1: Boot into Ubuntu
- Plug in your USB drive (from Chapter 1)
- Restart your computer
- Press the boot menu key (F12, F9, Esc — whatever your computer uses)
- Select your USB drive
- Choose "Try Ubuntu"

*You just used Chapter 1 skills.*

### Step 2: Open the Terminal
- Press **Ctrl + Alt + T**
- A terminal window appears

*You just used Chapter 2 skills.*

### Step 3: Find Your Router's IP Address
- In the terminal, type this command and press Enter:

```
ip route show
```

- You'll see output that looks something like:

```
default via 192.168.1.1 dev wlan0 proto dhcp metric 600
```

- The number after "default via" is your router's IP address. In this example, it's `192.168.1.1`.

*You just used Chapter 2 terminal skills for a Chapter 3 networking purpose.*

### Step 4: Access Your Router's Admin Page
- Open a web browser in Ubuntu
- Click the address bar
- Type your router's IP address (like `http://192.168.1.1`)
- Press Enter
- You'll see a login page

### Step 5: Log In and Count Devices
- Use the credentials from the sticker on your router (or try admin/admin)
- Look for "Connected Devices," "Device List," "DHCP Clients," or similar
- Count how many devices are connected
- Do you recognize every device on the list?

**You just combined Chapters 1, 2, and 3.** You booted a computer, used the terminal to find network information, and accessed your router's admin page. That's not beginner stuff. That's real, practical cybersecurity awareness.

---

## Day 3 Win

Here's what you did today:

- You understand the difference between a router, a switch, a modem, and an access point
- You know what ethernet cables look like and why CAT5e/CAT6 matters
- You can explain the OSI model's 7 layers in plain English
- You understand the difference between TCP and UDP
- You know how to find your router's IP address using the terminal
- You accessed your router's admin page and saw what devices are connected
- You can trace the path data takes from your computer to the internet

That's a lot. And you did it by building on what you already knew.

---

## Remember This

> It's never too late to learn cybersecurity. You don't need to memorize every protocol or understand every technical detail. You just need to be willing to look at the systems you already use every day and stop treating them like magic.

Today, you looked at the box with the blinking lights and understood what it does. You traced the path your data takes. You used the terminal to find your router's address. You logged into a piece of networking hardware and saw your own network from the inside.

That's not nothing. That's actual power. Use it.

---

*Next up: Chapter 4 — Internet Traffic. Now that you know how your network works, we'll follow your data as it leaves your router and travels across the internet. What happens along the way? Who can see it? And what does that mean for your privacy? Keep going.*