> **Behind the Screen** — [Chapter 1-2](chapter-1-2/) · [Chapter 3](chapter-3/) · [Chapter 4](chapter-4/) · [Chapter 5](chapter-5/) · [**Chapter 6**](chapter-6/) · [Chapter 7](chapter-7/) · [Project Memory](project-memory/vision.md)

---

# Chapter 6: Installing Software — apt, Repos, and Packages

> "You've learned to look. Now it's time to do."

---

## The Big Idea

You've made it through five chapters. You understand what a computer is, how it talks, how networks work, and how to browse the web without getting burned. Now we're crossing a threshold.

Up until now, you've mostly been *observing*. Looking at files. Reading about networks. Staying safe online. That was intentional — you can't protect what you don't understand.

But now? Now you're going to start *changing things*.

This chapter is about installing software on Linux. It's one of the most fundamental things you'll do as someone who works with computers. And it's also one of the most dangerous if you do it carelessly.

Don't worry. We're going to go slow.

---

## The Shopping List and the Store

Here's the analogy that makes this all click:

**Think of apt as a shopping list and repos as the store shelves.**

When you want software, you don't hunt for it on random websites — you check the store's catalog, pick what you need, and the store delivers it to your door. That's what apt does for Linux.

Let's break that down:

- **apt** (Advanced Package Tool) is the delivery system. It's the thing that goes and gets software for you, brings it back, and puts it in the right place.
- A **repository** (or "repo") is the store. It's a trusted collection of software packages that someone maintains and keeps safe.
- A **package** is the actual software — the thing you want to install.

When you say "I want to install Firefox," apt doesn't go hunting around the internet. It checks the trusted repositories your system already knows about, finds Firefox there, downloads it, and installs it.

This is *much* safer than the way people install software on other operating systems, where you Google something, click a random download button, and hope for the best.

---

## What Is apt, Really?

apt stands for **Advanced Package Tool**. It's the package manager for Ubuntu (and other Debian-based Linux distributions).

A package manager does a lot of things:

1. It knows where to find software (the repositories).
2. It downloads that software.
3. It installs it in the right place.
4. It keeps track of what's installed.
5. It can update software when new versions come out.
6. It can remove software cleanly.

Think of it like a really good personal assistant who handles all the logistics of getting and managing software. You just tell it what you want, and it figures out the details.

---

## What Is a Repository?

A repository is a **trusted store of software packages**.

When you install Ubuntu, it comes pre-configured with several official repositories. These are maintained by Ubuntu (and by Debian, the distribution Ubuntu is based on). They contain thousands of software packages that have been tested, reviewed, and signed.

There are different types of repositories:

- **Main** — Officially supported, free and open-source software.
- **Universe** — Community-maintained, free and open-source software.
- **Restricted** — Proprietary drivers (like for some graphics cards).
- **Multiverse** — Software with restricted licensing.

You can also add third-party repositories (called PPAs — Personal Package Archives), but we'll talk about why you should be careful with those later.

The key point: **repositories are curated**. Someone is maintaining them. Someone is checking that the software in them is what it claims to be. This is what makes them safe.

---

## Checking the Catalog: `sudo apt update`

Before you install anything, you should update your local catalog of what's available. This is like checking the store's inventory to see what's in stock.

```bash
sudo apt update
```

Let's break this down:

- `sudo` — This means "run this command with administrator privileges." We'll talk more about this soon. For now, just know that installing software requires special permission.
- `apt` — The package manager.
- `update` — The command. This tells apt to go check all the repositories and download the latest list of available packages.

When you run this, you'll see a bunch of output. apt is connecting to the repositories and downloading package lists. It might take a few seconds.

You'll see lines like:

```
Hit:1 http://archive.ubuntu.com/ubuntu jammy InRelease
Get:2 http://archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]
...
Reading package lists... Done
```

This is normal. It's just apt doing its job.

**Important:** `apt update` doesn't install anything. It doesn't upgrade anything. It just refreshes the catalog. It's safe to run anytime.

---

## Ordering from the Store: `sudo apt install <package>`

Now let's actually install something. Let's install a text editor called `nano`:

```bash
sudo apt install nano
```

Here's what happens:

1. apt looks in its catalog for the `nano` package.
2. It finds it in the repository.
3. It downloads the package (and any other packages it depends on — more on that in a moment).
4. It installs everything in the right place.
5. It updates its records to note that `nano` is now installed.

You'll see output like:

```
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  nano
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 280 kB of archives.
After this operation, 891 kB of additional disk space will be used.
Do you want to continue? [Y/n]
```

Type `Y` and press Enter. The installation will complete in a few seconds.

**What are dependencies?** Software often relies on other software to work. If you install a program that needs a certain library, apt will automatically find and install that library too. This is one of the great things about apt — it handles the chain of dependencies for you. You don't have to hunt down each piece manually.

---

## Returning Something You Don't Want: `sudo apt remove <package>`

What if you install something and decide you don't want it? Easy:

```bash
sudo apt remove nano
```

This removes the package. It's like returning something to the store.

Note: `remove` deletes the program but keeps its configuration files. If you want to remove everything, including configuration files, use:

```bash
sudo apt purge nano
```

For most purposes, `remove` is fine.

---

## What Is a .deb File?

A `.deb` file is a Debian software package. It's the actual file that contains the software.

**Think of a .deb file like a package delivered to your door.** You inspect it before opening it. You check who sent it. You make sure it's what you ordered.

When you use `apt install`, apt downloads `.deb` files behind the scenes and installs them. You usually don't see the `.deb` files themselves.

But sometimes you'll download a `.deb` file directly from a website. Maybe a software vendor offers their program as a `.deb` download. In that case, you can install it with:

```bash
sudo dpkg -i package-file.deb
```

(We'll talk about `dpkg` in a moment.)

**But here's the critical warning:**

---

## NEVER Install Random .deb Files from the Internet

This is one of the most important security lessons in this entire book.

When you install from a repository using apt, you're getting software from a **trusted, curated source**. The repository maintainers have checked it. It's been signed with cryptographic keys. It's been tested.

When you download a `.deb` file from a random website, you have **no such guarantees**. That file could contain anything. It could be the legitimate software. It could be malware disguised as legitimate software. It could be a modified version that steals your data.

**The rule is simple: only install `.deb` files from sources you absolutely trust.** And even then, verify them first.

---

## Verifying Downloads: Checksums, GPG Keys, and Official Sources

How do you know a file is legitimate? There are a few ways:

### Checksums (The Seal of Authenticity)

A checksum is a string of letters and numbers that uniquely identifies a file. It's like a seal on a package — if the seal is broken, you know someone tampered with it.

When you download software from a reputable source, they'll often provide a checksum (usually SHA256). You can compute the checksum of the file you downloaded and compare it to the one they published. If they match, the file hasn't been tampered with.

```bash
sha256sum downloaded-file.deb
```

This will output a long string. Compare it to the checksum the publisher provided. If they're identical, the file is intact.

### GPG Keys (The Signature)

GPG (GNU Privacy Guard) keys are a more advanced form of verification. A developer signs their software with a private key, and you can verify that signature with their public key. This proves the software came from them and hasn't been modified.

Repositories use GPG keys automatically. When you add a repository, you also add its GPG key, and apt uses that key to verify every package you download from it. This is one of the main reasons repositories are safe.

### Official Sources

Always download software from the official source. If you want Firefox, get it from Mozilla's website or from the Ubuntu repository. Don't get it from "firefox-free-download-2024.xyz."

---

## Permissions and sudo: Why Linux Asks for Your Password

When you run `sudo apt install`, Linux asks for your password. Why?

Because installing software is a **privileged operation**. It changes the system. It writes files to protected directories. It affects all users on the computer.

Linux is designed so that normal users can't do these things. Only the **administrator** (also called "root") can. When you use `sudo`, you're saying "I want to run this one command as the administrator."

This is a **security feature**, not an annoyance. It means that even if you accidentally run something malicious, it can't install itself without your password. It means that software you install intentionally has to ask permission first.

**A few rules about sudo:**

1. **Only use sudo when you need it.** Don't run random commands with sudo just because someone on the internet told you to.
2. **Understand what a command does before you run it with sudo.** If you don't know what a command does, look it up first.
3. **Never run `sudo` on a script you haven't read.** This should go without saying, but people do it all the time.

---

## What Is dpkg?

`dpkg` is the **underlying tool** that apt uses to actually install `.deb` files.

Think of it this way:
- **apt** is the smart assistant. It finds software, resolves dependencies, and manages everything.
- **dpkg** is the worker. It takes a `.deb` file and unpacks it, putting all the files where they go.

When you run `sudo apt install nano`, apt does all the thinking (finding the package, checking dependencies, downloading), and then it calls `dpkg` to do the actual installation.

You can use `dpkg` directly, but it's less convenient. It doesn't resolve dependencies automatically. If you try to install a `.deb` file with `dpkg` and it's missing a dependency, `dpkg` will complain and stop. apt would have just installed the dependency for you.

You'll mostly use `dpkg` for:
- Installing a `.deb` file you downloaded: `sudo dpkg -i file.deb`
- Listing installed packages: `dpkg -l`
- Checking what files a package installed: `dpkg -L packagename`

---

## Snap and Flatpak: Alternative Delivery Methods

apt isn't the only way to install software on Linux. There are two other popular methods:

### Snap

Snap is a package format created by Canonical (the company behind Ubuntu). Snap packages are self-contained — they include all their dependencies inside the package itself. This makes them larger but more portable.

```bash
sudo snap install firefox
```

Snaps are automatically updated in the background. They're sandboxed, which means they're isolated from the rest of your system (a security benefit).

### Flatpak

Flatpak is similar to Snap but is community-driven rather than controlled by a single company. It also uses sandboxing and self-contained packages.

```bash
flatpak install flathub org.libreoffice.LibreOffice
```

### Which Should You Use?

For now, stick with apt. It's the default, it's the most common, and it's what most tutorials and documentation assume you're using. As you get more comfortable, you can explore Snap and Flatpak.

---

## How to Check What's Installed

Want to see everything installed on your system?

```bash
apt list --installed
```

This will show a long list of every package on your system. There are usually thousands.

To see just the first 20:

```bash
apt list --installed | head -20
```

To search for a specific package:

```bash
apt list --installed | grep nano
```

To check if a specific program is installed and where it is:

```bash
which nano
```

This will show you the path to the `nano` executable, like `/usr/bin/nano`. If it's not installed, `which` will return nothing.

---

## Hardware Context: What Happens When You Install

Remember what you learned in Chapters 3 and 4? Installing software uses all of that:

- **Storage (hard drive/SSD):** The package files are downloaded and stored on your drive. Software takes up space. A small program might be a few megabytes. A large one could be hundreds of megabytes or more.
- **RAM:** The installer runs in memory. When you use the software, it loads into RAM.
- **Network:** The package is downloaded from a repository over the internet. This uses your network connection.

This is why installing software on a slow connection takes time. This is why you need enough disk space. And this is why understanding the hardware-software connection matters.

---

## Security: The Rules of Safe Installation

Let's put it all together. Here are the rules for installing software safely on Linux:

### 1. Use apt and the official repositories whenever possible.

This is the safest way to install software. The repositories are curated, signed, and maintained.

### 2. Avoid `curl | bash`.

You'll see this pattern online:

```bash
curl https://some-website.com/install.sh | bash
```

**Never do this.** This downloads a script from the internet and immediately runs it as administrator. You have no idea what that script does. It could do anything. It could install malware. It could delete your files.

If you need to install something this way, download the script first, read it, understand it, and *then* run it.

### 3. Only add repositories you trust.

Adding a third-party repository means you're trusting that repository's maintainers. Only add repositories from well-known, reputable sources.

### 4. Verify downloads.

If you download a `.deb` file or any software directly, verify the checksum. Make sure it matches what the publisher published.

### 5. Keep your system updated.

```bash
sudo apt update && sudo apt upgrade
```

This updates your catalog and then upgrades all installed packages to their latest versions. This patches security vulnerabilities. Do this regularly.

### 6. Don't install things you don't need.

Every piece of software on your system is a potential vulnerability. If you don't need it, don't install it. If you installed it and don't use it anymore, remove it.

---

## Cumulative Exercise: Install, Verify, Remove

This is where everything comes together. You're going to install software, verify it's there, and then remove it. This is system management.

**Step by step:**

1. **Boot into Ubuntu.** You know how to do this by now.

2. **Open the terminal.** Ctrl+Alt+T, or find it in the applications menu.

3. **Update your package catalog:**
   ```bash
   sudo apt update
   ```
   Enter your password when prompted. Remember: `sudo` means "run as administrator." Linux is asking for your password to make sure it's really you.

4. **Install a text editor:**
   ```bash
   sudo apt install nano
   ```
   Type `Y` when it asks if you want to continue.

5. **Verify it's installed:**
   ```bash
   which nano
   ```
   You should see `/usr/bin/nano`. That means it's installed and ready to use.

6. **Remove it:**
   ```bash
   sudo apt remove nano
   ```
   Type `Y` to confirm.

7. **Check what's installed:**
   ```bash
   apt list --installed | head -20
   ```
   This shows the first 20 packages installed on your system. There are thousands more.

**What you just did:** You updated your software catalog, installed a program, verified it was there, removed it, and checked your system's inventory. That's system management. That's what system administrators do every day.

You're not just a user anymore. You're someone who can manage a system.

---

## Cheat Sheet

| Term/Command | What It Means |
|---|---|
| `apt update` | Check the catalog — refresh the list of available software |
| `apt install <package>` | Order a package — download and install software |
| `apt remove <package>` | Return a package — uninstall software |
| `.deb` | A physical package file — like a box delivered to your door |
| `sudo` | Manager permission — run a command as administrator |
| `repo` | Trusted store — a curated collection of software packages |
| `checksum` | Seal of authenticity — verifies a file hasn't been tampered with |
| `dpkg` | The unpacking tool — installs .deb files at a low level |
| `apt list --installed` | Check inventory — see what's installed on your system |
| `which <program>` | Find a program — shows the path to an installed program |
| `GPG key` | Digital signature — verifies who published the software |
| `Snap/Flatpak` | Alternative delivery methods — self-contained packages |

---

## Day 6 Win

You installed software today. You removed it. You checked what's on your system. You used `sudo` and understood why it asked for your password.

That's not nothing. That's real system administration.

A lot of people use computers for years without ever understanding how software gets onto their machine. You now understand the whole pipeline: repositories, packages, apt, permissions, verification. You know why it's dangerous to install random files from the internet. You know how to check what's on your system.

You're building a foundation. Every chapter adds another layer. And the layers are starting to stack up into something real.

Take a breath. You're doing great.

---

## Coming Up: Chapter 7 — Home Lab & VM

Now that you can do everything — navigate files, manage users, configure networks, browse safely, and install software — it's time to put it all together.

In Chapter 7, you're going to build your own sandbox. A home lab. A virtual machine where you can experiment freely, break things, fix them, and learn without any risk.

You've learned to look. You've learned to do. Now it's time to *play*.

See you in Chapter 7.
