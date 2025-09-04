---
title: " Module 3 - Network Intrusions"
parent: Connect & Protect
nav_order: 3
layout: default
---

# Module 3
## Network Intrusions

When you think of a network, you imagine just packets darting back and forth in wires or air. Every request, every packet, every handshake is a potential doorway for someone curious, malicious, or just bored enough to break in.  

**Every network has inherent vulnerabilities.** The game isn’t about perfection, it’s about staying alert, patching cracks before someone else crawls through.  

---

## Packet Sniffing: Reading Other People’s Mail  

Packets are like little envelopes, carrying headers (addresses) and bodies (messages). Packet sniffing is like the postman secretly reading every letter on the route.  

- **Passive sniffing**: the attacker quietly reads traffic, like eavesdropping without leaving fingerprints.  
- **Active sniffing**: the attacker alters packets in flight, like intercepting your bank transfer and rewriting the account number.  

The scary part? Tools like **Wireshark** or **tcpdump** can be used by both defenders and attackers. The same magnifying glass that helps analysts troubleshoot also lets hackers steal login credentials floating through an unencrypted network.  

Defense here is straightforward in theory: **encrypt everything (TLS, HTTPS, VPN).** 

---

## IP Spoofing: The Art of Pretending  

Imagine a stranger putting your friend’s return address on a letter. The letter arrives, seems trusted, but inside is something entirely different. That’s IP spoofing: changing the source IP of packets to impersonate someone authorized.  

Spoofing unlocks several attacks:  

### On-path attacks (a.k.a. Man-in-the-Middle / MITM)  

Think of two people having a private conversation. A third person sneaks in between them, listening carefully, maybe even whispering in responses on behalf of one of them. That’s what an on-path attack is: the attacker positions themselves in the middle of a trusted connection.  

**How it works:** The attacker uses **IP spoofing** to convince each side that they’re talking to the other, when in fact everything is passing through the attacker.  
**Impact:** The attacker can simply eavesdrop (stealing usernames, passwords, session cookies) or actively alter traffic (e.g., changing a bank transfer’s destination account).  
**Defense:** **Encryption (TLS/HTTPS)** is the strongest defense. Even if an attacker gets in the middle, the data is unreadable without the keys.  

On-path attacks are dangerous because they don’t require breaking into a system, just controlling the flow of traffic.  

---

### 🔹 Replay attacks  

Imagine a thief watching someone use their subway card, recording the swipe, and later playing back that same signal to get a free ride. That’s a replay attack.  

**How it works:** An attacker captures legitimate packets from a network session (e.g., an authentication request) and resends them later. To make the replay convincing, the attacker often **spoofs the original sender’s IP address**, so the packet looks like it came from the real user instead of the attacker’s machine.  
**Example:** Suppose you log into a service and your device sends an encrypted “login token.” An attacker who records that token can replay it later, spoofing your IP in the process, and impersonating you without ever knowing your password.  
**Impact:** Replay attacks exploit trust. The system thinks the attacker is the legitimate user, because the packet was real, just reused at the wrong time.  
**Defense:** Use of **nonces** (numbers used once), **timestamps**, and **session expiration** ensures that even if a packet is captured, replaying it won’t work.  

Replay attacks are sneaky because nothing looks “fake” in the packet itself, the header looks right (thanks to spoofing), the data is valid, but the *timing* is malicious.  

---

### Smurf attacks  

This one is about amplification. Picture shouting into a canyon, and your single voice comes back as a hundred echoes that overwhelm someone on the other side.  

**How it works:** The attacker sends **ICMP echo request (ping)** packets with a spoofed source IP (the victim’s IP). Instead of sending them directly, they send them to the **network’s broadcast address**, which forwards the ping to all devices on that network.  
**Impact:** Every device replies to the ping but because the source IP was spoofed, all replies flood the victim. One ping suddenly multiplies into hundreds or thousands.  
**Defense:** Configure **routers/switches to block directed broadcasts**, and use **next-generation firewalls** that can detect abnormal ICMP floods.  

Smurf attacks are essentially a **combo attack**, they combine **IP spoofing** with a **denial-of-service technique**, using innocent devices as amplifiers to overwhelm the victim with traffic.  
 The attacker barely spends any resources but causes the victim to drown in responses.  

The counter? Smarter firewalls and anomaly detection. Spot traffic that pretends to be local when it clearly isn’t. **Defense-in-depth at work.**  

---

## Backdoors: The Hidden Escape Hatch  

Sometimes vulnerabilities aren’t accidents, they’re intentional shortcuts. A programmer might leave a “backdoor” to simplify testing or admin access. Harmless in theory, disastrous in practice.  

Worse, attackers who compromise a system often **create their own backdoors** to guarantee return access. Once inside, they can drop malware, disable defenses, or prepare the stage for a larger attack.  

Backdoors are the hacker’s bookmark: *“I’ll come back later.”*  

---

## Denial of Service: Drowning the System  

If packet sniffing is stealth, DoS is brute force. Overload the system until it collapses.  

### SYN Floods  
In a **SYN flood**, the attacker spams the server with SYN requests but never completes the final ACK step.  

- The server, trying to be polite, keeps ports “half-open” waiting for that final ACK.  
- When the number of half-open connections skyrockets, the server’s connection table fills up.  
- **Result:** the server has no room left to accept real users, and legitimate clients are denied service.  

**Why it’s nasty:** It doesn’t require much bandwidth. Just a steady stream of half-handshakes can exhaust server resources.  
**Defense:** Techniques like **SYN cookies** or connection timeouts help the server drop bogus requests more quickly.  

---

### ICMP Floods  

In an **ICMP flood** (sometimes called a “ping flood”):  

- The attacker bombards the target with a massive number of ICMP Echo Requests.  
- The target tries to reply to each one, chewing up CPU cycles and bandwidth.  
- With enough requests, the target becomes so busy answering “are you alive?” pings that it can’t handle legitimate traffic.  

**Why it’s effective:** ICMP is a very basic protocol — no authentication, no handshake, just “ask and answer.” This makes it easy to abuse.  
**Defense:** Firewalls and intrusion detection systems can **rate-limit ICMP traffic** or block suspicious floods while allowing normal diagnostic use.  

---

### Ping of Death  

Most ICMP packets are small — the max size is supposed to be **64 KB**. But some systems in the past couldn’t properly handle oversized packets.  

The **Ping of Death** exploit works like this:  

- The attacker crafts an ICMP packet larger than the maximum allowed size.  
- When the target system receives it, the oversized packet causes a **buffer overflow** or memory corruption.  
- The system crashes, freezes, or reboots — a denial of service with just **one malformed ping**.  

**Why it’s infamous:** Unlike SYN or ICMP floods (which require lots of packets), a Ping of Death could knock out a system with just a single oversized packet.  
**Defense:** Modern operating systems have patched this vulnerability, but it remains a classic reminder: even the most basic protocols can harbor critical flaws.   

---

## Distributed Denial of Service (DDoS)  

And when attackers multiply these tactics across thousands or even millions of compromised machines, a **botnet**, 
the attack evolves into a **Distributed Denial of Service (DDoS)**, a digital tidal wave that’s far harder to contain.  

One of the most infamous examples is the **2016 DNS DDoS attack**. It was powered by the **Mirai malware**, which had infected countless everyday devices like webcams, DVRs, 
and even routers that were poorly secured with default passwords. Overnight, these simple household gadgets became unwilling soldiers in a massive botnet.  
At around 7:00 AM on October 21st, the botnet unleashed tens of millions of DNS requests targeting a major DNS service provider. 
Since DNS servers are like the “phone book” of the internet, their disruption meant users couldn’t reach popular sites by name. 
The result: Twitter, Netflix, Reddit, GitHub, and many other platforms across North America and Europe went dark.  

The attack didn’t exploit some cutting-edge vulnerability, it weaponized insecure consumer devices and one of the internet’s most fundamental services. 


---

## tcpdump: The Analyst’s Magnifying Glass  

In the chaos, analysts need tools. **tcpdump** is one of the simplest but sharpest. A text-based packet sniffer, it shows timestamps, source and destination IPs, and ports of the network traffic.

On a normal day, traffic flows smoothly. But when traffic looks odd, a flood of SYN packets, or ICMP requests too frequent to be natural, tcpdump exposes the anomaly.  

Attackers use sniffers to steal. Analysts use them to see.  

---

## Defense-in-Depth: Layered Armor  

There is no silver bullet. Instead, the mantra is **defense-in-depth**. Encrypt traffic. Configure firewalls smartly. Monitor constantly. Assume every layer can fail, so stack them.  

---

## Final Reflection  

Studying these attacks makes you appreciate networks differently. Every packet is both a function and a risk. Every convenience, from DNS to free Wi-Fi, is also an opening.  

As analysts, our job is less about chasing perfection and more about curiosity: looking for anomalies, understanding how attackers think, and always asking *“what if?”*.  

The battlefield is invisible, but it’s real. And it never sleeps.  

---

[← Back: Module 2](module-02.md)   &nbsp; | &nbsp;   [Next: Module 4 →](module-04.md)
