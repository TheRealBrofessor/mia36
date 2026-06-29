# Behind the Screen — Project Memory & Vision

## Project Goal
A beginner-friendly cybersecurity learning repo by TheRealBrofessor. Target audience: people who feel left behind by technology and think cybersecurity is "not for them." Tone is encouraging, analogy-rich, and anxiety-aware.

## Core Design Principles
1. **Every chapter has an analogy** that maps unfamiliar tech to everyday life
2. **Cumulative skill building** — each chapter reuses ALL prior skills + adds one new thing
3. **Muscle memory** — by Chapter 6, reader has a complete workflow
4. **Hardware context woven in** — no standalone hardware chapter; hardware is introduced where relevant
5. **Anxiety-aware** — every chapter starts by validating the reader's nervousness

## Chapter Structure (6 chapters)

| # | Title | New Skill | Hardware Context | Cumulative Workflow |
|---|-------|-----------|------------------|---------------------|
| 1 | Digital Confidence | Boot Ubuntu from USB, test run | USB drives, ports | Boot + explore |
| 2 | Linux Terminal | Navigate OS, terminal, commands, folders | Keyboard, monitor, screen | + terminal fluency |
| 3 | Networking | Router, switch, ethernet, OSI, TCP/IP | Router, switch, cables, Wi-Fi | + network basics |
| 4 | Internet Traffic | Packets: origin, path, delivery (outgoing focus) | Modem, NIC, data path | + packet awareness |
| 5 | Web Navigation | Visiting sites, safety, HTTPS, phishing, browsers, VPN | Browser as vehicle | + safe navigation |
| 6 | Installing Software | apt, repos, packages, downloads, permissions | Storage, RAM, sudo | + system management |
| 7 | Home Lab & VM | Build a VM, apply all 6 skills in sandbox | Virtual hardware | Complete workflow |

## Analogies Per Chapter
- Ch 1: Test-driving a car before buying
- Ch 2: GPS (mouse) vs paper map (terminal)
- Ch 3: Postal system (letters, addresses, sorting)
- Ch 4: Tracking a package through checkpoints
- Ch 5: Checking the lock on a hotel door
- Ch 6: Grocery shopping (repos = store shelves, apt = shopping list)

## Progress (Updated June 28, 2026 — 12:30)
- [x] Chapter 1: Digital Confidence — REWRITTEN (test-drive analogy, USB hardware, repeat exercise)
- [x] Chapter 2: Linux Terminal — REWRITTEN (GPS vs map analogy, keyboard/monitor hardware, cheat sheet, cumulative exercise)
- [x] Chapter 3: Networking — REWRITTEN (postal system analogy, router/switch/ethernet hardware, OSI/TCP, cumulative exercise)
- [x] Chapter 4: Internet Traffic — DRAFTED (package tracking analogy, outgoing focus, curl/ss demos, cumulative exercise)
- [x] Chapter 5: Web Navigation & Safety — DRAFTED (door lock analogy, HTTPS, phishing, VPN, browsers, cumulative exercise)
- [x] Chapter 6: Installing Software — DRAFTED (shopping list analogy, apt, repos, permissions, cumulative exercise)
- [x] Chapter 7: Home Lab & VM — DRAFTED (car analogy, VirtualBox, snapshots, cumulative 10-step exercise)
## Restructure Complete For Ch 1-3
- Hardware concepts woven into relevant chapters (USB in Ch 1, keyboard/monitor in Ch 2, router/switch/ethernet in Ch 3)
- Each chapter has: analogy, hardware context, cheat sheet, cumulative exercise referencing all prior chapters
- File locations:
  - Ch 1-2: /tmp/behind_the_screen/topics/linux-basics/README.md
  - Ch 3: /tmp/behind_the_screen/topics/networking-basics/README.md
  - Ch 4: /tmp/behind_the_screen/topics/internet-traffic/README.md
  - Ch 5:   /tmp/behind_the_screen/topics/web-navigation/README.md
  - Ch 6:   /tmp/behind_the_screen/topics/installing-software/README.md
  - Ch 7:   /tmp/behind_the_screen/topics/home-lab/README.md

## Next Chapters to Draft
- Ch 6: Installing Software (grocery shopping analogy, apt, repos, permissions)
- Ch 7: Home Lab & VM (capstone — all skills applied in a sandbox)

## Notes
- Each chapter ends with a repeat exercise that incorporates ALL prior skills
- Screenshot placeholders in existing drafts — add real screenshots later
- Target: 15-20KB per chapter (Ch 4 ran ~31KB — acceptable for depth)
- Project memory file: /tmp/behind_the_screen/project-memory/vision.md
