<img src="profile.jpg" width="128" alt="Shesh Budhabhatti" align="right">

# Shesh Budhabhatti

**Live site: [sheshbud.github.io/portfolio](https://sheshbud.github.io/portfolio/)**

Cybersecurity & Software Engineering | Northeastern University, Khoury College of Computer Sciences

B.S. in Cybersecurity and Business Administration (Finance concentration), expected April 2028. Dean's List (Fall 2025, Spring 2026).

- **LinkedIn:** [linkedin.com/in/sheshbudhabhatti](https://linkedin.com/in/sheshbudhabhatti)
- **Email:** sheshbudhabhatti@gmail.com
- **Location:** Boston, MA / Connecticut

---

## Experience

**Product Security Intern — Medtronic** (June 2026 to Present), Boston, MA
Designed, built, and evaluated an autonomous Wi-Fi resilience system for hospital-grade medical device networks (full write-up below); analyzed wireless attack surfaces and developed developer security training.

**AI Student Ambassador and WICxDevSecOps Program Participant — Microsoft** (October 2025 to February 2026), Boston, MA
Selected for security training on Azure DevSecOps pipelines, threat modeling, and AI model security protocols; demoed Copilot/Omi AI to 100+ users, collecting structured feedback for product teams.

**R&D Software Engineering Intern — Medtronic** (Summers 2024 and 2025), North Haven, CT
Reduced test fixture calibration time by 37% through Python automation; authored a fixture manual for cross-functional teams across the US and India; implemented AES-256 and Blowfish encryption for the Signia™ Stapling System to meet HIPAA compliance and pass an FDA cybersecurity audit.

**Cybersecurity and Safety Researcher — Secure and Assured Intelligent Learning Lab** (June 2023 to February 2024), New Haven, CT
Identified 8 security vulnerabilities in LLM systems through 50+ prompt injection attacks.

**Summer Intern, Audit/Tax/Advisory Accounting — KPMG** (July to August 2023), Hartford, CT
Collaborated across 5-person teams on 3 client engagements, identifying 2 key control weaknesses in inventory tracking; analyzed financial data with Tableau to visualize audit-risk insight for senior stakeholders.

**Founder, Executive Director, and TEDx Speaker — Gurls Chess Club Non-Profit** (December 2021 to Present), USA
Founded a chess non-profit coaching 200+ students (70% female); delivered 70+ lessons; redesigned curriculum using retention data analysis, improving participant retention from 40% to 78%.

---

## Featured: Adaptive Wi-Fi Resilience for Hospital Networks
*Medtronic Product Security · Summer 2026 · Hardware + embedded systems research*

Connected medical devices are validated against interference in clean, controlled labs, but real hospitals are noisier and nothing keeps a device adapting once it's out in the field. This project asks: what happens when other RF shows up, can it disrupt the link, and can a system catch that and re-route on its own? The result auto-senses trouble and re-routes itself, live, with zero manual input.

**What I built:** Specced, wired, and assembled the entire testbed from scratch: a Raspberry Pi 5 access point, an ESP32 client reporting live metrics, additional ESP32s as interference generators, and an ALFA adapter independently monitoring nearby Wi-Fi to separate real traffic from noise. Wrote a decision engine from scratch that fuses latency, jitter, packet loss, and signal strength into a single health score, with a trend check that catches degradation early and a guard that only switches channel/band if the alternative is genuinely better.

**Testing:** One variable at a time (baseline, distance, load, independent interference), every sample logged the same way. Load-tested to 28 real clients / 600 packets/sec; ran 20 hours on the busiest channel to isolate congestion effects.

**Findings:**
- Congestion isn't the threat: weak signal and 28 clients / 600 pps barely moved latency (devices take turns automatically).
- Independent, uncoordinated interference is the real threat: 0 to 4 disruptors took latency from 3ms to 33ms while packet loss stayed at zero.
- Degradation compounds non-linearly: +112% latency at 1 to 2 disruptors, +209% at 2 to 4.
- Validated overnight, unattended: with 4 disruptors running, the engine detected 3 consecutive bad samples, switched itself from 2.4GHz to 5GHz with zero manual input, and held cleanly for ~10 hours.
- **Headline finding:** a link can look completely healthy while latency and jitter are already climbing toward failure. Silent degradation, not disconnection, is the real risk to watch for.

**Also explored:** a decentralized ESP-NOW-based variant for direct device-to-device communication with no access point. It worked, though the lack of a retry layer meant ~9% packet loss, pointing at the next research direction.

---

## Systems & Networking Projects

- **[Memory Allocator](https://github.com/sheshbud/memory-allocator)**: C allocator using `mmap`/`munmap`, a sorted coalescing free list, and first-fit allocation to minimize fragmentation. (CS3650 Computer Systems)
- **[Basic Memory Allocator](https://github.com/sheshbud/basic-memory-allocator)**: Earlier `sbrk`-based version of the above, for comparison. (CS3650 Computer Systems)
- **[FTP Client](https://github.com/sheshbud/ftp-client)**: FTP client built from raw Python sockets: PASV mode parsing, control/data channel handling, six operations (ls/mkdir/rmdir/rm/cp/mv). (CS4700 Network Fundamentals)
- **[Fakebook Web Crawler](https://github.com/sheshbud/fakebook-web-crawler)**: Web crawler over raw TLS sockets with manual HTTP/1.1 handling: CSRF token extraction, cookie-based sessions, chunked transfer encoding, BFS-based crawling. (CY2550 Foundations of Cybersecurity)
- **[BGP Router](https://github.com/sheshbud/bgp-router)**: BGP router in Python: route aggregation, longest-prefix-match forwarding with a full tie-breaking chain, handshake/update/withdrawal handling, all IP address bit-math written from scratch. (CS4700 Network Fundamentals)
- **[Transport Protocol](https://github.com/sheshbud/transport-protocol)**: Reliable transport protocol over raw UDP: sliding window, retransmission, RTT estimation. (CS4700 Network Fundamentals)
- **[Threaded Merge Sort](https://github.com/sheshbud/threaded-merge-sort)**: Multithreaded merge sort benchmarked across a 2-core cloud VM and a 10-core Apple M4, empirically validating that speedup tracks physical core count. (CS3650 Computer Systems)

## Software Engineering Projects

- **[CookYourBooks](https://github.com/sheshbud/cookyourbooks)**: Recipe management app in Java: unit conversion (metric/imperial + ingredient-specific density conversions), recipe scaling, and an interactive CLI. (CS3100 Program Design & Implementation)

## Side Projects

- **SnapCal**: Mobile-first PWA: snap a photo of any schedule or syllabus, AI vision extracts every dated event, confirm/edit, then export as `.ics` or add straight to a calendar. Per-event reminders embed VALARM into the export, calendars auto-name from the document title, no account required. Built with Vite + React (PWA, installable, no app store), a Vercel serverless function keeping the AI API key private, and the Claude API for vision extraction.

## Cybersecurity Projects

### [Discretionary Access Control & CTF Challenges](ctf-challenges/README.md)
Multi-level CTF challenges: HTML/JS inspection, steganography, cron job privilege escalation, broken access control, authentication bypass, and vulnerability chaining.

### [Password Cracking with John the Ripper & Hashcat](password-cracking/README.md)
Cracked 50+ passwords from simulated Linux shadow files using rule-based attacks, mask attacks, and hash analysis.

### [Cryptography Implementation](cryptography/README.md)
Applied AES/Blowfish encryption, hash function security, digital signatures, and secure key exchange, including the real-world implementation used in the Medtronic Signia™ Stapling System work above.

### Bandit CTF Wargame
Completed OverTheWire Bandit levels: Linux command-line navigation, file permissions, SSH, and basic binary analysis.

---

## Technical Skills

**Languages:** Python, Java, C, C++, JavaScript, SQL, Assembly
**Systems & Tools:** Git/GitHub, Linux/Unix, Docker, GDB, Valgrind, Azure DevSecOps
**Security:** Wireshark, Metasploit, Hashcat, threat modeling, penetration testing, cryptographic protocols

---

## Recognition

- TEDx Speaker: "Empowering Equality, Inspiring Action" (2023)
- SMARTA Podcast guest: "If You're Young, You Still Can Make a Difference" (2025)
- Lean Six Sigma Yellow Belt (2024)
- CT Women's Chess Champion (2018)
- TRAIN's Intro to Artificial Intelligence, Certified (2024)
