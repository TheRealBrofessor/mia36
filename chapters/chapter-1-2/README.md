# Chapter 1 — Digital Confidence

> **Behind the Screen** by TheRealBrofessor
> Phase 1 of the beginner-friendly cybersecurity roadmap

---

## You're Allowed to Be Nervous

Let's get something out of the way first: it's completely normal to feel nervous about trying a new operating system.

You've been using Windows for years. You know where things are. It feels safe. And now someone's asking you to put a new system on your computer — and that voice in your head is whispering, *"What if I break something? What if I lose all my photos? What if I can't go back?"*

Here's the truth: **You are not breaking anything. You're just visiting.**

Think of it like test-driving a car before buying it. You sit in the driver's seat, feel the wheel under your hands, test the brakes — without committing to the purchase. You can walk back into the dealership, hand back the keys, and everything is exactly as it was. Same with an OS. You're allowed to try before you commit.

By the end of this chapter, you'll have tasted what a different operating system feels like — and nothing on your computer will have changed. When you restart and remove your USB, Windows will greet you like nothing happened. Because nothing did.

Let's prove that to ourselves.

---

## What Is Linux? (And Why Should I Care?)

You've probably heard of Windows (the thing that runs most home computers) or macOS (the thing that runs Apple computers). **Linux is another operating system** — a different way for a computer to work.

Think of it like this: if Windows is a Ford and macOS is a Toyota, Linux is a really reliable Honda that a whole community of mechanics has been improving for free, for decades. And just like car brands come in different models, Linux comes in different "flavors" called distributions — Ubuntu, Fedora, Debian, and many others.

Why does it matter for cybersecurity?

- **Most of the internet runs on Linux.** The websites you visit, the apps you use, the servers that store your data — a huge number of them are running Linux.
- **Security professionals use Linux every day.** If you want to understand how computers really work — and how to protect them — Linux is where you'll spend a lot of time.
- **It's free.** No license key, no subscription, no "upgrade to Pro for $149."

The best part? You can try Linux **without changing anything on your computer.** No deleting Windows. No complicated install. No risk.

We're going to do exactly that today.

---

## What We're Going to Do (The Big Picture)

By the end of this chapter, you will:

1. Understand what a USB drive is — the hardware in your hand
2. Download Ubuntu (a beginner-friendly version of Linux) from the official website
3. Download a free tool called balenaEtcher
4. Use balenaEtcher to put Ubuntu onto your USB drive
5. Boot your computer from that USB drive and see Linux running

That's it. Five steps. No jargon. No stress.

Let's go.

---

## Step 1: Pick the Right USB Drive

This is your first hardware interaction in this journey, so let's slow down and actually talk about what's in your hand.

A **USB flash drive** (sometimes called a thumb drive, jump drive, or pen drive) is a small storage device that plugs into your computer's **USB port** — that rectangular slot you've probably used hundreds of times without thinking about it.

![A standard USB flash drive next to a pencil for size comparison, showing it is small and portable](screenshots/usb-drive-example.png)
*Alt text: A standard USB flash drive next to a pencil for size comparison.*

### USB Types and Sizes: What You Need to Know

Not all USB drives are the same. Here's a quick breakdown of what you'll see:

**USB 2.0 vs USB 3.0 (and beyond)**

- **USB 2.0:** The older standard. Slower, but still works. These drives have been around since the early 2000s.
- **USB 3.0 (also called USB 3.1 or USB 3.2 Gen 1):** Much faster. You can usually tell by looking at the **inside of the plug** — USB 2.0 has a black or white plastic piece inside; USB 3.0 has a **blue** plastic piece inside.

Here's the good news: **they're all backward compatible.** A USB 3.0 drive works in a USB 2.0 port (just at the slower speed), and vice versa. You don't need to worry about getting the "wrong" kind.

**What happens when you plug in a USB drive?**

When you slide a USB drive into your port, your computer detects it almost instantly — you'll hear a sound, and a notification will appear. The operating system reads the drive's contents and makes it available to you. It's like handing someone a filing cabinet: they can look at what's inside, remove folders, add new ones — but only if you hand it to them first. **The drive doesn't do anything on its own.** It waits for the computer to ask it questions.

### What to look for in a USB drive:

| Requirement | Why it matters |
|---|---|
| **At least 8 GB** | Ubuntu needs room to breathe. 8 GB is the minimum. 16 GB is even better. |
| **USB 3.0 preferred (blue inside plug)** | Faster flashing and booting. Still works with USB 2.0 ports. |
| **Empty (or you don't mind erasing it)** | The process will wipe everything on the drive. Move any photos or files you want to keep somewhere safe first. |

**Don't have one?** They cost about $5–$10 at any office supply store, pharmacy, or big-box store. You don't need a fancy brand. Any basic USB drive works.

> **Important:** This process will erase everything on the USB drive. If you have family photos or important documents on it, copy them to your computer first. Yes, this warning is repeated — it's that important.

![A close-up of a USB 3.0 drive's blue internal connector next to a USB 2.0 drive's black internal connector](screenshots/usb-2-vs-3.png)
*Alt text: Side-by-side comparison of a USB 3.0 drive (blue inner connector) and a USB 2.0 drive (black or white inner connector).*

---

## Step 2: Download Ubuntu

Ubuntu is one of the most popular and beginner-friendly versions of Linux (a "distribution"). It's free, well-supported, and has a huge community of people who can help if you get stuck.

### Here's how to get it:

1. **Open your web browser** (Chrome, Edge, Firefox — whatever you normally use).

2. **Go to the official Ubuntu website:**
   👉 **https://ubuntu.com/download/desktop**

   ![The Ubuntu desktop download page showing the download button prominently](screenshots/ubuntu-download-page.png)
   *Alt text: The Ubuntu desktop download page with a large download button visible.*

3. **Click the "Download" button.** The latest version (called "Ubuntu Desktop") will start downloading.

4. **Wait for the download to finish.** The file is about 4–5 GB, so it might take a few minutes depending on your internet speed. Go grab a coffee.

5. **Find the downloaded file.** It will be in your Downloads folder. It'll be named something like `ubuntu-24.04-desktop-amd64.iso`.

   > **What's an ".iso" file?** It's basically a perfect snapshot of a CD or DVD, saved as a single file. Think of it as a box that contains the entire Ubuntu operating system, neatly packed up. You can't open it like a regular folder — your computer treats it as if it were a real disc inserted into a (virtual) disc drive.

### A note about versions

You might see version numbers like "24.04" or "22.04." Don't overthink it. **Just download the latest LTS version** (LTS means "Long Term Support" — it's the stable one that gets updates for years). The download page will recommend the right one.

---

## Step 3: Download balenaEtcher

Now we need a tool to put that Ubuntu file onto your USB drive. The easiest, most beginner-friendly tool is called **balenaEtcher**.

### Here's how to get it:

1. **Go to the official balenaEtcher website:**
   👉 **https://etcher.balena.io**

   ![The balenaEtcher homepage showing download options for Windows, macOS, and Linux](screenshots/balenaetcher-homepage.png)
   *Alt text: The balenaEtcher homepage with download buttons for different operating systems.*

2. **Click the green download button** for your operating system (if you're on Windows, click the Windows version).

3. **Run the installer** once it downloads. It's a normal install — just click "Next" a few times and "Finish." Nothing tricky.

4. **Open balenaEtcher.** You'll see a clean, simple screen with three steps laid out for you.

   ![balenaEtcher's main screen showing the three-step interface: Flash from file, Select target, Flash!](screenshots/balenaetcher-main-screen.png)
   *Alt text: balenaEtcher's main screen showing the three-step interface: Flash from file, Select target, and Flash.*

> **Why balenaEtcher?** Because it does one thing and does it well. You pick a file, you pick a USB drive, and you click Flash. It handles all the complicated stuff behind the scenes. It's like a toaster — you put bread in, toast comes out.

---

## Step 4: Put Ubuntu on the USB Drive

This is the moment. Take a breath. You've got this. Let's walk through it.

### What's about to happen

balenaEtcher will take that Ubuntu "box" (the .iso file) and carefully unpack it onto your USB drive — setting it up so your computer can read it and start from it. This is called "flashing."

**This will erase your USB drive.** Everything currently on it will be gone. That's why we warned you in Step 1.

### Let's do it

1. **Plug your USB drive into your computer.**
   - If it's a USB 3.0 drive (blue inside), try to find a USB 3.0 port on your computer (also blue inside). If you can't tell, any port works — it'll just be a bit slower.
   - Your computer might make a sound or show a notification. You can close/ignore that for now.

2. **Open balenaEtcher** (if it's not already open).

3. **Click "Flash from file."**
   - A file picker will open.
   - Navigate to your Downloads folder.
   - Select the Ubuntu `.iso` file you downloaded earlier.

   ![balenaEtcher's file picker showing the Ubuntu ISO file selected](screenshots/flash-from-file.png)
   *Alt text: balenaEtcher's file picker with the Ubuntu ISO file highlighted and selected.*

4. **Click "Select target."**
   - You should see your USB drive listed. If you have other drives connected, look for the one that matches your USB drive's name or size.
   - Click the checkbox next to it.
   - Click "Select."

   > **Double-check you picked the right drive!** This will erase everything on it. Make sure it's your USB drive and not your computer's main hard drive. If you're unsure, unplug other USB devices and try again.

   ![balenaEtcher showing the USB drive selected as the target](screenshots/select-target.png)
   *Alt text: balenaEtcher's target selection screen with the USB drive checked and selected.*

5. **Click "Flash!"**
   - balenaEtcher will now write Ubuntu to your USB drive.
   - This takes about 5–15 minutes depending on your drive speed and whether you used a USB 3.0 port.
   - You'll see a progress bar. Go grab another coffee.

   ![balenaEtcher showing the flashing progress bar at about 60%](screenshots/flashing-progress.png)
   *Alt text: balenaEtcher's flashing screen with a progress bar showing the write in progress.*

6. **Wait for it to say "Flash Complete."**
   - balenaEtcher will also verify the write to make sure everything went correctly. This is its way of double-checking its own work.
   - When it's done, you can close balenaEtcher.
   - You may see a message saying the drive can't be read — that's normal. The drive now contains a bootable Linux system, not a regular Windows-formatted drive.

   ![balenaEtcher showing the Flash Complete success message](screenshots/flash-complete.png)
   *Alt text: balenaEtcher's success screen showing "Flash Complete" with a green checkmark.*

**Congratulations.** You just created a bootable Linux USB drive. That's a real tech skill, and you did it.

---

## Step 5: Boot from the USB Drive

Now for the exciting part — actually running Linux on your computer.

### What "booting from USB" means

"Booting" is just the word for what happens when your computer starts up and loads an operating system. Normally when you turn on your computer, it loads Windows from your hard drive. "Booting from USB" just means telling your computer, "Hey, this one time, start from the USB stick instead."

**This does NOT install anything.** It does NOT change Windows. It's like putting a different DVD in your car's stereo — the car is still the same car when you take the DVD out.

### Here's how to do it — step by step

1. **Leave the USB drive plugged in.** (Don't remove it — we need the computer to read from it.)

2. **Restart your computer.** (Click Start → Power → Restart.)

3. **As your computer starts up, press the boot menu key.**

   This is the part that feels tricky, but it's just because every computer brand decided to use a different key. You need to press this key **repeatedly** — as in, tap-tap-tap like you're impatiently ringing a doorbell — starting the instant you press the power button.

   **But why?** Here's what's happening behind the scenes: when your computer turns on, it goes through a quick startup routine called POST (Power-On Self-Test). During those first few seconds, it checks which devices are connected and asks, "Which one should I start from?" It only listens for that key press during this brief window — a few seconds at most. If you wait too long, it'll default to your hard drive and load Windows.

   | Computer brand | Key to press (repeatedly, as it starts up) |
   |---|---|
   | **Dell** | F12 |
   | **HP** | F9 or Esc |
   | **Lenovo** | F12 or Fn + F12 |
   | **Acer** | F12 |
   | **ASUS** | Esc or F8 |
   | **Microsoft Surface** | Hold Volume Up while pressing Power |

4. **A menu will appear** showing your storage devices. Use the arrow keys to select your USB drive (it might be called "USB," "UEFI: [brand name]," or "Removable Device").

   ![The boot menu showing a list of bootable devices with the USB drive highlighted](screenshots/boot-menu.png)
   *Alt text: A computer's boot menu showing a list of devices with the USB drive option highlighted.*

5. **Press Enter.**

6. **Ubuntu will load a screen** asking what you want to do. Select **"Try Ubuntu"** — NOT "Install Ubuntu."

   > **Why "Try"?** Because we're test-driving. We're not buying the car yet. "Try Ubuntu" loads the entire operating system into your computer's temporary memory (RAM). Nothing touches your hard drive. Your files, your photos, your Windows — all untouched.

   ![The Ubuntu startup screen showing "Try Ubuntu" and "Install Ubuntu" options](screenshots/try-ubuntu.png)
   *Alt text: The Ubuntu welcome screen with "Try Ubuntu" and "Install Ubuntu" buttons, with "Try Ubuntu" highlighted.*

7. **Wait a minute or two.** Ubuntu is loading into your computer's memory. You'll see a loading screen.

8. **Welcome to Linux!** You'll see a desktop with a web browser, file manager, and other apps. Click around. Open the browser. Look at the settings. You're running a completely different operating system, and your Windows is still right there, untouched, waiting for you when you restart and remove the USB.

   ![The Ubuntu desktop showing the default wallpaper, dock, and a web browser open](screenshots/ubuntu-desktop.png)
   *Alt text: The Ubuntu desktop with its purple wallpaper, application dock on the left, and a web browser window open.*

### When you're done exploring:

- Click the power icon in the top-right corner → "Power Off"
- Remove the USB drive
- Turn your computer back on
- Windows will load exactly as it always did

Nothing changed. Nothing was deleted. You just proved something to yourself.

---

## Troubleshooting (Don't Panic Section)

If something went wrong, you're not alone. This is a finicky process, and most people need a second try. Here are the most common issues:

**"My computer didn't show the boot menu."**
This is the most common hiccup. Try restarting and pressing the key **earlier** — as soon as you press the power button, start tapping. Some computers are picky about timing. If that doesn't work, search "[your computer model] boot menu key" — someone online has definitely figured it out.

**"It went straight to Windows."**
You probably missed the timing window. That's totally normal. The boot menu might only be listening for 2–3 seconds. Restart and try again, tapping faster. It often takes 2–3 attempts — even for experienced users.

**"balenaEtcher says 'Access Denied' or won't flash."**
Try running balenaEtcher as an administrator (right-click the icon → "Run as administrator"). Also make sure no other program (like your file explorer) is open and looking at the USB drive.

**"Ubuntu loads but looks weird or the screen is the wrong size."**
That's completely normal when running from a USB. Ubuntu isn't loading your computer's full graphics drivers — it's using basic "safe mode" graphics. Everything will look better if you ever decide to install it for real (but that's a future chapter — not today).

**"I can't find my USB drive in balenaEtcher."**
Unplug it and plug it back in. Sometimes a quick reconnect is all it takes. Also double-check you haven't accidentally picked your computer's hard drive instead.

---

## Day 2 Win: You Just Did the Thing

Here's what you accomplished today:

- You handled a USB drive and understood what USB 2.0 vs 3.0 means
- You learned what happens when you plug a USB into your computer
- You downloaded Ubuntu from the official Ubuntu website
- You used balenaEtcher to create a bootable Linux USB drive
- You changed your computer's boot order — something most people never do
- You ran a completely different operating system without touching your existing setup

**That's not "baby steps." That's a real, tangible tech skill.**

You didn't need to be an expert. You didn't need to know command lines or code. You didn't need to memorize anything. You just needed to follow the steps and be willing to try.

And you did it.

---

## Your Repeat Exercise: From Memory

Here's your challenge. Before reading the next chapter:

**Boot into Ubuntu again — this time without looking at the steps.** See if you can do it from memory. If you get stuck, glance back, but try to do as much as you can on your own.

Once you're at the Ubuntu desktop, **write down 3 things you noticed this time that you didn't notice the first time.**

Maybe it's something visual — the dock on the left, the color of the wallpaper, the way the browser looks. Maybe it's something physical — the sound your computer made during boot, the feel of tapping F12 over and over. Maybe it's something conceptual — you realized what "booting" actually means, or you noticed your files weren't there.

It doesn't matter what those 3 things are. What matters is that **you saw more the second time.** That's what learning looks like. Not getting it perfect on the first try — seeing more on the second pass.

---

## Quick Reference

| Resource | Location |
|---|---|
| Ubuntu download | https://ubuntu.com/download/desktop |
| balenaEtcher download | https://etcher.balena.io |
| Minimum USB size | 8 GB (16 GB recommended) |
| USB standard | USB 3.0 preferred (blue inside plug); USB 2.0 works fine |
| Key choice in Ubuntu | "Try Ubuntu" — never "Install" for testing |
| When done | Power off, remove USB, restart → back to Windows |

---

## Remember This

> It's never too late to learn cybersecurity. The world needs people who care about protecting themselves and others online — and that includes you. Linux, AI, networking, modern technology — none of it is off-limits. You don't have to be young. You don't have to be a genius. You just have to be willing to take the first step.

Today, you took that first step. You held a USB drive, understood what it was, understood what you were asking your computer to do, and you did it. You test-drove an operating system and walked away without a scratch.

That wasn't luck. That was you being braver than you thought you were.

Tomorrow, we keep going.

---

## Chapter 2: Linux Terminal — Navigate, Commands, Folders

> **Behind the Screen** by TheRealBrofessor
> Phase 1 of the beginner-friendly cybersecurity roadmap

---

### Welcome Back — You've Already Done the Hard Part

Remember what you did in Chapter 1? You downloaded Ubuntu, put it on a USB drive, and booted into a whole new operating system — without breaking anything. That was the scary part. You handled it.

Now it's time to actually *use* Linux. Not just look at the desktop — but talk to it. And the way you talk to Linux is through something called the **terminal**.

I know. The word "terminal" sounds intimidating. It sounds like something from a hacker movie where someone in a hoodie types furiously while green text scrolls across the screen.

Here's the truth: the terminal is just a text-based way of telling your computer what to do. Instead of clicking icons, you type simple words. That's it. You're going to learn five of those words today, and by the end of this chapter, you'll feel something you might not have felt in a long time while using a computer: **in control.**

Let's go.

---

### Your Hardware Is Your Ally Now

In Chapter 1, you learned about USB drives, keyboards, and monitors as separate pieces of a puzzle. Now you're going to start using them *together* — intentionally.

Here's what's happening when you use the terminal:

- **Your keyboard** is your primary tool. This is how you talk to the terminal. Every command, every letter, every space — it all comes from your fingers on the keyboard. You're not just typing emails anymore. You're typing *instructions* that your computer follows.

- **Your monitor** is where you see the conversation. When you type a command and press Enter, the monitor shows you the result. It's a two-way dialogue: you type, the computer responds, and you read that response on the screen.

- **Screen navigation** is different now. In a web browser, you scroll with a mouse. In the terminal, you scroll with the scrollbar on the right side of the window, or with the **Page Up** and **Page Down** keys on your keyboard. You can also press **Shift + Page Up/Down** to scroll through the terminal's history.

Think of it this way: before, you were a passenger in a car, looking out the window. Now you're in the driver's seat. The keyboard is your steering wheel. The monitor is your windshield. And the terminal is the dashboard telling you everything you need to know.

You're not just *using* the computer anymore. You're *driving* it.

---

### The Mouse vs. The Terminal: GPS vs. Map

Here's an analogy that will stick with you:

**The mouse is like GPS — it tells you where to go. The terminal is like reading a map — YOU decide the route. Knowing both makes you unstoppable.**

When you use the mouse, you click on icons, double-click folders, and drag things around. The graphical interface guides you. It's like GPS navigation: you follow the arrows, and you get where you need to go. It's easy, it's visual, and it works.

But what happens when GPS fails? What happens when the road is closed, or you need to take a shortcut the GPS doesn't know about?

That's where the map comes in. When you can read a map, you understand the *layout* of the land. You know that Main Street connects to Oak Avenue, even if the GPS doesn't suggest that route. You're not dependent on the turn-by-turn directions anymore.

The terminal is your map. When you type `cd Documents`, you're not clicking through a series of folders — you're *telling* the computer exactly where to go, directly. When you type `ls`, you're not opening a file manager window — you're asking the computer to show you what's there, instantly.

Both tools are valuable. You'll still use the mouse for many things — browsing the web, editing photos, reading documents. But when you need precision, speed, or control, the terminal is your map. And once you can read the map, you'll never feel lost in a computer again.

---

### Opening the Terminal (It's Just an App)

The terminal is just another application — like a web browser or a word processor. You open it the same way you'd open anything else.

There are two ways to open it:

**Method 1: The Keyboard Shortcut (the cool way)**
Press these three keys at the same time: **Ctrl + Alt + T**

That's it. A window will pop up with some text. That's your terminal.

**Method 2: The Mouse Way (totally fine)**
1. Click "Activities" in the top-left corner
2. Type "terminal" in the search box
3. Click the Terminal icon

![The Ubuntu Activities search showing "terminal" typed in the search bar with the Terminal app icon appearing in results](screenshots/opening-terminal.png)
*Alt text: The Ubuntu Activities overview with "terminal" typed in the search bar and the Terminal application icon visible in the results.*

Either way works. Use whatever feels comfortable. There's no "wrong" way to open an application.

> **Try this right now:** Open the terminal using the keyboard shortcut (Ctrl + Alt + T). Then close it. Then open it again using the mouse method. You now have two ways to get to the same place. That's the whole chapter in a nutshell.

---

### First Look at the Terminal: Don't Panic

When the terminal opens, you'll see something that looks like this:

```
yourname@yourcomputer:~$ 
```

![A freshly opened terminal window showing the default prompt with username and hostname](screenshots/terminal-first-look.png)
*Alt text: A new terminal window showing the default Ubuntu prompt with a username, hostname, and a blinking cursor.*

Let's break that down in plain English:

- **yourname** — This is your username. In the live USB session, it's probably "ubuntu."
- **@yourcomputer** — This is the name of the computer. In the live session, it might also say "ubuntu."
- **~** (tilde symbol) — This means you're in your "home folder." Think of it as your personal space on the computer, like "My Documents" in Windows.
- **$** — This is the prompt. It means the terminal is ready and waiting for you to type something.

That blinking cursor? That's the computer saying, "I'm listening. What do you want me to do?"

Look at your monitor right now. That text you see? It's the computer's way of talking back to you. This is a conversation. You type something, it responds. You type something else, it responds again. The terminal is not a test — it's a dialogue.

You're about to tell it what to do.

---

### The 5 Commands You Need to Know

Everything in the terminal comes down to **commands** — short words you type that tell the computer to do something specific. Today, you're going to learn five of them. These five are your foundation. Master these, and everything else in Linux becomes easier.

Here they are, in order:

1. `pwd` — Where am I?
2. `ls` — What's around me?
3. `cd` — Take me somewhere
4. `whoami` — Who am I right now?
5. `clear` — Clean up my screen

Let's learn them one at a time. Type each one yourself. Don't just read — *do it*. Your keyboard is your tool, and you need to build the muscle memory.

---

### Command #1: `pwd` — "Where Am I?"

The first command is `pwd`, which stands for **"print working directory."** In human terms: "Tell me what folder I'm in right now."

Type this and press Enter:

```
pwd
```

You should see something like:

```
/home/ubuntu
```

![The terminal showing the pwd command and its output displaying the current directory path](screenshots/command-pwd.png)
*Alt text: The terminal showing the user typed "pwd" and the output "/home/ubuntu" was displayed.*

**What just happened?** You asked the terminal where you are, and it told you. You're in the `/home/ubuntu` folder. That's your home base — your personal area on this system.

This is like opening your file manager and looking at the address bar to see which folder you're in. Except you did it with one word.

**You just ran your first Linux command.** How does that feel?

> **Practice it:** Type `pwd` three more times. Yes, really. The goal is to make your fingers remember: p-w-d, Enter. You're building muscle memory. Every repetition makes the next time easier.

---

### Command #2: `ls` — "What's Around Me?"

The second command is `ls`, which stands for **"list."** It shows you what files and folders are in your current location.

Type this and press Enter:

```
ls
```

You might see something like:

```
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos
```

![The terminal showing the ls command and its output listing folder names in the home directory](screenshots/command-ls.png)
*Alt text: The terminal showing the user typed "ls" and a list of folder names appeared: Desktop, Documents, Downloads, Music, Pictures, Public, Templates, and Videos.*

**What just happened?** The terminal listed all the folders in your home directory. These are the same folders you'd see if you opened the file manager and looked inside your home folder.

Think of `ls` as glancing around a room to see what's there. It's that simple.

> **Try this:** Type `ls Desktop` and press Enter. That tells the terminal to list what's *inside* the Desktop folder. You can do this with any folder name.

> **Practice it:** Run `ls` a few times. Try `ls Documents`, `ls Downloads`, `ls Pictures`. You're exploring your own computer using nothing but text. That's powerful.

---

### Command #3: `cd` — "Take Me Somewhere"

The third command is `cd`, which stands for **"change directory."** It moves you from one folder to another.

Let's try it. Type this and press Enter:

```
cd Documents
```

Now type `pwd` again:

```
pwd
```

You should see:

```
/home/ubuntu/Documents
```

![The terminal showing the cd Documents command followed by pwd, confirming the directory changed](screenshots/command-cd.png)
*Alt text: The terminal showing the user typed "cd Documents" then "pwd" and the output now shows "/home/ubuntu/Documents".*

**What just happened?** You told the terminal to go into the Documents folder, and it did. Then you checked with `pwd` to confirm you were in the right place.

This is exactly like double-clicking on a folder in Windows to open it — except you did it by typing.

**Want to go back?** Type:

```
cd ..
```

The `..` (two dots) means "go back one folder." It's like clicking the "Back" button in your file manager. Now type `pwd` again — you should be back in `/home/ubuntu`.

> **Quick tip:** Press the **Up Arrow** key on your keyboard. It brings back your last command. This is super useful when you want to run something again without retyping it. Press Up Arrow multiple times to scroll through your command history. Your keyboard is full of these shortcuts — they save you time.

> **Practice it:** Navigate to Documents, then to Downloads, then back home. Use `cd` and `pwd` together. Go forward, go back. Get comfortable with the rhythm: move, check, move, check.

---

### Command #4: `whoami` — "Who Am I Right Now?"

The fourth command is `whoami`, and it does exactly what it sounds like.

Type this and press Enter:

```
whoami
```

You'll see:

```
ubuntu
```

![The terminal showing the whoami command and its output displaying the current username](screenshots/command-whoami.png)
*Alt text: The terminal showing the user typed "whoami" and the output "ubuntu" was displayed.*

**What just happened?** The terminal told you which user account you're currently using. In the live USB session, this is "ubuntu" — the default account.

This might seem pointless right now, but it becomes really important in cybersecurity. When you're working on a system, you always need to know: *who am I logged in as? What level of access do I have?* Different users have different permissions, and that matters a lot when it comes to security.

Think of it like checking your ID badge when you walk into a building. `whoami` is your digital ID badge. It tells you who the computer thinks you are.

> **Practice it:** Type `whoami` a few times. It will always say "ubuntu" in the live session. But when you install Linux on your own machine, it will say *your* name. And in cybersecurity, knowing your identity on a system is the first step to understanding what you can and cannot do.

---

### Command #5: `clear` — "Clean Up My Screen"

This one isn't really about navigating — it's about comfort. Your terminal might be getting full of text from all the commands you've been running.

Type this and press Enter:

```
clear
```

The screen wipes clean. Fresh start. All your previous commands are still in the history (remember the Up Arrow key), but now you have a clean workspace.

![The terminal before and after running the clear command, showing a cluttered screen becoming empty](screenshots/command-clear.png)
*Alt text: A side-by-side comparison of the terminal screen before (filled with previous commands) and after (clean and empty) running the clear command.*

> **Bonus tip:** You can also press **Ctrl + L** to clear the screen without typing anything. Keyboard shortcuts are your friend. Your keyboard isn't just for typing letters — it's a control panel.

> **Practice it:** Run a bunch of commands, then clear. Run more commands, then clear again. Get used to the idea that you can always start fresh. The terminal is forgiving — it lets you clean up and try again.

---

### Understanding the File System: A Tree, Not a Maze

Now that you've run some commands, let's talk about how Linux organizes files. This is one of those concepts that seems confusing at first but is actually pretty logical once someone explains it.

In Windows, you're used to drive letters: `C:\`, `D:\`, maybe `E:\` for a USB drive. Each drive has its own separate tree of folders.

Linux does it differently. There's **one big tree**, and everything branches off from a single starting point called the **root** (written as just `/`).

Here's a simplified picture:

```
/                    ← This is "root" — the very top of everything
├── home/            ← Where users' personal folders live
│   └── ubuntu/      ← Your home folder
│       ├── Desktop/
│       ├── Documents/
│       ├── Downloads/
│       └── ...
├── etc/             ← System configuration files
├── bin/             ← Essential programs (like your commands)
├── usr/             ← Installed software
└── var/             ← Variable data (logs, etc.)
```

![A simple diagram showing the Linux file system as a tree structure branching from root](screenshots/linux-filesystem-tree.png)
*Alt text: A tree diagram showing the Linux file system starting from "/" at the top, branching into home, etc, bin, usr, and var directories.*

**Why does this matter?**

- Everything in Linux is a file. Your documents are files. Your programs are files. Even your keyboard and screen are represented as files. This "everything is a file" philosophy is one of the things that makes Linux so powerful for security work.
- There are no drive letters. When you plug in a USB drive, it gets "mounted" (attached) somewhere in the tree — usually under `/media/`. It all becomes part of the same system.
- The structure is logical and consistent. Once you understand the tree, you can navigate anywhere.

> **You don't need to memorize all the folders.** Just understand the concept: one tree, starting at `/`, and everything branches from there. The details will stick over time.

---

### What Is "Root" and What Is "sudo"? (Plain English)

You've probably seen the word "root" floating around. Let's clear this up, because it's important and it's simpler than people make it sound.

**Root is the super-user.** It's an account that can do *anything* on the system — delete any file, change any setting, install or remove any program. Think of root as the building manager who has a master key to every room.

**Your regular account is like a tenant.** You have keys to your own apartment (your home folder), and you can use the common areas, but you can't walk into other people's apartments or rewire the building's electrical system.

This is actually a **security feature**. If you accidentally run a harmful command, or if a malicious program tries to mess with your system, it can't do much damage because you're not root. You're just a regular user.

But sometimes you *need* to do something that requires higher privileges — like installing software or changing system settings. That's where `sudo` comes in.

**`sudo` stands for "superuser do."** It's like saying, "Hey, I know I'm not the building manager, but I need to do this one thing that requires manager access. Please let me do it — and I'll prove I'm allowed."

When you use `sudo`, the system asks for your password. If you enter it correctly, the command runs with elevated privileges — but only for that one command. It's not like logging in as root permanently. It's a controlled, temporary elevation.

Here's a simple example (don't run this yet — just read it):

```
sudo apt update
```

This tells Ubuntu: "I'm a regular user, but I need to check for software updates, which requires system-level access. Let me do it."

![The terminal showing a sudo command being entered and prompting for a password](screenshots/sudo-example.png)
*Alt text: The terminal showing "sudo apt update" being typed, followed by a password prompt that says "[sudo] password for ubuntu:".*

**Why this matters for cybersecurity:**

- The separation between regular users and root is one of Linux's core security principles. It limits the damage from mistakes and attacks.
- Understanding `sudo` is essential because you'll use it constantly when installing security tools.
- Many attacks try to gain root access — so understanding how privilege escalation works is fundamental to both defending and (ethically) testing systems.

> **Important safety note:** Never run `sudo` commands from random websites or tutorials unless you understand what they do. With great power comes great responsibility. You now have the master key — use it wisely.

---

### Opening Folders: Two Ways to Get Anywhere

Let's put the GPS vs. Map analogy into practice. You're going to open a folder using the mouse, then navigate to the same folder using the terminal. Same destination, two different routes.

**The Mouse Way (GPS):**
1. Click on the file manager icon in the dock (it looks like a folder)
2. Double-click on "Documents"
3. You're in Documents. The address bar shows your location.

**The Terminal Way (Map):**
1. Open the terminal (Ctrl + Alt + T)
2. Type `cd Documents` and press Enter
3. Type `pwd` — it says `/home/ubuntu/Documents`
4. You're in the exact same place.

Both methods got you to the same folder. The mouse was visual and guided. The terminal was direct and precise. Neither is "better" — they're different tools for the same job.

Now here's where it gets interesting. Try this in the terminal:

```
cd /home/ubuntu/Documents
```

That's the **full path** — you specified the entire route from the root of the file system. You didn't have to go through each folder one at a time. You jumped directly to your destination.

That's the power of the terminal. The mouse makes you walk through every room to get to the kitchen. The terminal lets you teleport.

> **Try this exercise:** Open your file manager with the mouse. Navigate to a folder. Look at the address bar to see the full path. Now open the terminal and type `cd` followed by that full path. Press Enter. Type `pwd` to confirm. You just used the map to get exactly where you wanted to go.

---

### Navigating the Screen: Your Monitor Is a Window

When you're working in the terminal, your monitor is showing you a window into the computer. But that window has limits — it can only show so many lines of text at once. What happens when the output is longer than your screen?

**Scrolling:**
- Use the **scrollbar** on the right side of the terminal window (mouse method)
- Use **Shift + Page Up** and **Shift + Page Down** (keyboard method)
- Use the **mouse scroll wheel** if you have one

**Seeing more at once:**
- You can **resize the terminal window** by dragging its edges. Make it bigger to see more output.
- You can **maximize** the terminal window to fill the entire monitor. This gives you the most screen real estate.
- Press **Ctrl + Shift + +** (plus) to make the text bigger. Press **Ctrl + -** (minus) to make it smaller. This is helpful if the text is hard to read on your monitor.

**Multiple terminals:**
- Open a second terminal with Ctrl + Alt + T. Now you have two terminal windows. You can arrange them side by side on your monitor.
- This is useful when you want to see two things at once — like reading a file in one terminal while running a command in another.

Your monitor is your workspace. Arrange it however makes you comfortable. There's no single "right" way to set up your screen.

---

### Why Do Security Professionals Love Linux?

You might be wondering: "Okay, I ran some commands. But why does everyone in cybersecurity use Linux? Why not just stick with Windows?"

Great question. Here are the main reasons:

**1. Transparency (Open Source)**
Linux is open source, which means anyone can look at the code that makes it work. For security professionals, this is huge. You can see exactly what the system is doing — there are no hidden backdoors or secret features. If there's a vulnerability, the global community can find it and fix it quickly.

**2. Control**
Linux gives you granular control over everything — what's running, what's connected, what's allowed. When you're investigating a security incident, you need that level of control. Windows often hides things from you; Linux puts it all on the table.

**3. The Tools**
Most cybersecurity tools are built for Linux first (and sometimes Linux only). Tools for network analysis, penetration testing, forensics, and vulnerability scanning — they all live in the Linux ecosystem. Want to use Wireshark, Nmap, Metasploit, Burp Suite, or Aircrack-ng? Linux is their natural home.

**4. The Terminal**
Remember those five commands you just learned? That's the foundation. In cybersecurity, you'll often work on remote servers that don't have a desktop at all — just a terminal. The skills you're building right now are the same skills used by security analysts, penetration testers, and incident responders every single day.

**5. Security by Design**
Linux was built with multi-user security in mind from the start. The user permission system, the file permissions, the way processes are isolated — it's all designed to keep things secure. Windows has caught up a lot, but Linux has been doing this for decades.

**6. It Runs Everything**
Most web servers, cloud infrastructure, mobile phones (Android is Linux!), and IoT devices run Linux. If you want to understand how the modern world works — and how to protect it — you need to understand Linux.

![An infographic showing logos of popular cybersecurity tools that run on Linux: Wireshark, Nmap, Metasploit, Burp Suite, Aircrack-ng](screenshots/security-tools-linux.png)
*Alt text: An infographic displaying logos of popular cybersecurity tools — Wireshark, Nmap, Metasploit, Burp Suite, and Aircrack-ng — with a Linux penguin logo in the center.*

> **The bottom line:** Learning Linux isn't just a nice-to-have for cybersecurity. It's essential. And you've already started.

---

### Putting It All Together: A Mini Practice Session

Let's do a quick run-through of everything you've learned. Open a fresh terminal (or clear your current one) and try this sequence:

```
pwd          → See where you are
ls           → See what's around you
cd Documents → Go into Documents
pwd          → Confirm you moved
ls           → See what's in Documents
whoami       → Check who you are
cd ..        → Go back home
clear        → Clean up
```

![The terminal showing the full practice sequence of commands being executed one by one](screenshots/practice-session.png)
*Alt text: The terminal showing a sequence of commands being typed and their outputs: pwd, ls, cd Documents, pwd, ls, whoami, cd .., and clear.*

That's it. You just navigated a file system, checked your identity, and managed your workspace — all from a text prompt. That's real. That's a real skill. And it's the foundation of everything that comes next.

---

### Common Fears (And Why They're Okay)

**"What if I break something?"**
In the live USB session, you literally can't break anything permanent. Everything is running in your computer's memory. If something goes wrong, you restart and it's like nothing happened. This is the safest possible way to learn.

**"What if I type the wrong thing?"**
Then you'll get an error message. Error messages aren't failures — they're the computer trying to help you understand what went wrong. You'll learn to read them over time. For now, just know that an error message is not a disaster.

**"This doesn't feel natural yet."**
Of course it doesn't. You've been using a mouse for decades. You've been typing in terminals for about 10 minutes. Give it time. In a few weeks, these commands will feel as natural as double-clicking a folder.

**"I'm too old to learn this."**
You're not. Your brain is still capable of learning new things — that doesn't expire. The only difference between you and a 20-year-old learning this is that you have something they don't: life experience, patience, and a real reason to learn. That's an advantage, not a weakness.

---

### Note-Taking: Write It Down

Here's something that separates people who *learn* from people who *forget*: **take notes.**

Get a notebook, a text file, a sticky note — whatever works for you. After each practice session, write down what you did and what you learned.

**Write down in your own words what each command does. Teaching someone else is the best way to learn.**

If you can explain `pwd` to a friend in plain English, you truly understand it. If you can't, that's a sign to practice more. Teaching forces you to organize your thoughts and find the gaps in your understanding.

Here's a note-taking prompt for each command:

- What does this command do? (One sentence, your own words)
- When would I use it? (A real scenario)
- What did I see on my monitor when I ran it? (The actual output)

Keep your notes somewhere you can find them. You'll be surprised how often you look back at them — and how much clearer things seem when you write them down.

---

### Cheat Sheet: Your 5 Commands

Here they are — all five commands in one place. Screenshot this. Print it out. Tape it to your monitor. Whatever works.

| # | Command | What It Does | When to Use It | Example |
|---|---------|-------------|----------------|---------|
| 1 | `pwd` | Shows your current folder location | "Where am I right now?" | `pwd` → `/home/ubuntu` |
| 2 | `ls` | Lists files and folders in current location | "What's in this folder?" | `ls` → `Desktop Documents Downloads` |
| 3 | `cd` | Changes to a different folder | "Take me to this folder" | `cd Documents` (go in), `cd ..` (go back) |
| 4 | `whoami` | Shows your current username | "Who am I logged in as?" | `whoami` → `ubuntu` |
| 5 | `clear` | Clears the terminal screen | "Clean up my workspace" | `clear` (or press Ctrl + L) |

**Bonus keyboard shortcuts:**

| Shortcut | What It Does |
|----------|-------------|
| Ctrl + Alt + T | Open a new terminal |
| Ctrl + L | Clear the screen (same as `clear`) |
| Up Arrow | Bring back your previous command |
| Ctrl + Shift + + | Make text bigger |
| Ctrl + - | Make text smaller |
| Ctrl + C | Stop a running command |
| Shift + Page Up/Down | Scroll through terminal output |

> **Print this page or take a screenshot.** Having a physical reference while you practice makes a huge difference. You don't have to memorize everything — you just have to know where to look.

---

### Cumulative Exercise: Prove It to Yourself

This is where it all comes together. Do this entire sequence without looking at your notes. If you get stuck, that's okay — look, then try again from the top.

**1) Boot into Ubuntu.**
You already know how to do this from Chapter 1. USB drive, boot menu, Ubuntu desktop. You've done it before. Do it again.

**2) Open the terminal without looking at notes.**
Ctrl + Alt + T. Three keys. You know this. If you forget, think: "Ctrl, Alt, T — all three at once." Your fingers remember even when your brain doesn't.

**3) Run all 5 commands from memory.**
- `pwd` — Where am I?
- `ls` — What's around me?
- `cd Documents` — Take me somewhere.
- `whoami` — Who am I?
- `clear` — Clean up.

If you can do all five without looking at a cheat sheet, you've internalized them. That's real learning.

**4) Open a folder using the mouse, then navigate to it using the terminal.**
- Open the file manager. Click on Documents. You're there — GPS style.
- Open the terminal. Type `cd Documents`. Press Enter. Type `pwd`. You're there — map style.
- Same destination. Two different routes.

**You now have TWO ways to get anywhere.**

That's not just a skill — that's freedom. You're no longer limited to one way of interacting with your computer. You have options. And options mean control.

---

### What's Next

You've opened a terminal, run basic commands, understood the file system concept, and learned why Linux matters for security. That's a *lot* for one session.

In the next chapter, we'll shift gears. You'll learn about the network inside your home — what your router does, how Wi-Fi and the internet are different things, and why knowing what devices are connected to your network is the first step to protecting them.

But for now, sit with what you've learned. Practice those five commands. Open the terminal a few times just to prove to yourself that you can do it.

You're building a foundation. And foundations take time.

---

### Day 2 Win

Here's what you did today:

- You opened the Ubuntu terminal without fear
- You ran five basic commands: `pwd`, `ls`, `cd`, `whoami`, and `clear`
- You navigated into a folder and back using the terminal
- You opened a folder with the mouse AND with the terminal — two ways to the same place
- You understand what the Linux file system is (one big tree, starting at `/`)
- You understand what "root" means (the super-user with full access)
- You understand what `sudo` does (temporary, controlled elevation of privileges)
- You can explain why Linux is the operating system of choice for cybersecurity professionals
- You have a cheat sheet you can print or screenshot
- You wrote notes in your own words

**That's not beginner stuff. That's the real thing.**

You're not "playing around" anymore. You're building actual skills that security professionals use every day. The terminal isn't scary — it's just a conversation with your computer. And you're learning the language.

---

> It's never too late to learn cybersecurity. Every expert was once a beginner who was afraid to open the terminal. You opened it. You ran commands. You navigated with both the mouse and the keyboard. You're already ahead of where you were yesterday. Keep going.

---

*Next up: Chapter 3 — Networking Basics. You'll learn about the network inside your home, what your router does, and why knowing what's connected is the first step to protecting it. See you there.*