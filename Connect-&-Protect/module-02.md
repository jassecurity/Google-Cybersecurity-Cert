---
title: " Module 2 - Network Operations"
parent: Connect & Protect
nav_order: 2
layout: default
---

# Module 2
## Network Operations

We talked about **TCP, UDP, IP, ARP, NAT** in the previous blog, here's some additional protocols-

- **DHCP:** On a home or office network, every device needs a private IP address, while the router alone exposes the public IP to the internet.
   In theory, you could assign those addresses manually (static assignment), but that quickly becomes unmanageable as the number of devices grows.
   This is where the Dynamic Host Configuration Protocol (DHCP) comes in.
   DHCP automates giving out private addresses by leasing them from a pool and also providing the correct default gateway and DNS settings.
   As a result, devices like laptops, phones, and printers can join the network instantly without the hassle of manual configuration.
     
- **IMAP vs. POP3** are protocols that control how email is retrieved from a mail server.
   With **POP3 (Post Office Protocol v3)**, messages are usually downloaded to the local device and then removed from the server.
   This made sense in the early days of email, when users typically checked mail from a single desktop. But it creates problems in today’s world: once the mail is pulled down,
   it may no longer exist on the server, making it hard to access the same messages from multiple devices.
  **IMAP (Internet Message Access Protocol)** solved that issue by keeping messages on the server. Devices only download copies or headers, meaning your inbox stays consistent whether you check it from your laptop, phone, or webmail. Modern services like Gmail, Outlook, and iCloud all rely on IMAP to support multi-device syncing.

  From a security angle, both protocols can be abused if misconfigured. Older, unencrypted POP3 or IMAP traffic sends credentials in plaintext, which attackers can intercept. 
  That’s why secure versions wrapped in SSL/TLS (IMAPS on port 993, POP3S on port 995) are the default today.
  
- **Telnet vs SSH:** represent two very different eras of remote access. **Telnet** was one of the earliest protocols for managing systems over a network.
   It allowed administrators to log into remote machines, but everything like usernames, passwords, and commands were transmitted in plain text.
   On an untrusted network, that meant anyone intercepting traffic could read credentials directly, making Telnet a huge security liability.
  **SSH (Secure Shell)** was introduced as a secure replacement. It encrypts all communication, uses stronger authentication (including key-based methods), and prevents eavesdroppers
   from seeing what’s being typed or executed. SSH runs on *port 22* and has become the standard way to securely manage servers, network devices, and even automated scripts.
   SSH, on the other hand, is not just for remote login, it’s also the foundation for secure file transfer and tunneling
  .
- **HTTP vs HTTPS:** HTTP is functional but insecure; all communication between your browser and the web server travels in plaintext that includes login forms, cookies, and session tokens.
   On an open Wi-Fi network, anyone running a simple packet sniffer could capture and read that traffic. **HTTPS** solves this by adding a layer of **SSL/TLS encryption**.
   Instead of sending everything in the clear, our browser and the server perform a handshake, exchange keys, and establish an encrypted tunnel.
   From that point on, even if an attacker intercepts the packets, all they see is scrambled ciphertext.
  
- **SSL/TLS:** SSL (Secure Sockets Layer) and its successor TLS (Transport Layer Security) aren’t just about securing websites.
   They’re the underlying protocols that provide encryption, authentication, and integrity for many types of network communication.
   When you connect to a secure website over HTTPS, send email through IMAPS or SMTPS, or establish a VPN tunnel, it’s SSL/TLS doing the heavy lifting in the background.
   The protocol works by performing a handshake between two systems (like your browser and a server). During this handshake, the server proves its identity with a digital certificate,
   the two sides agree on encryption keys, and then they switch to an encrypted session.
   From that point forward, anything sent, whether it’s a password, an email, or a file, it is encrypted so that only the intended parties can read it.

---

## Wireless Protocols: Where Security is Tested  

Wired networks are inherently contained; wireless networks bleed into the physical world. 
That’s why the evolution of Wi-Fi security protocols tells a story of defense catching up to exploitation:  

- **WEP (1999):** Tried to give “wired equivalent privacy.” Its RC4 implementation was weak, keys could be cracked in minutes, and it’s now considered useless.  
- **WPA (2003):** A stopgap using TKIP to patch WEP flaws. Better, but still exploitable (e.g., KRACK attacks).  
- **WPA2 (2004):** Adopted AES and CCMP, making it the default for years. Still vulnerable to handshake manipulation.  
- **WPA3 (2018):** Introduced SAE (Simultaneous Authentication of Equals) to fix KRACK-type issues and pushed stronger encryption (128-bit minimum, 192-bit optional in enterprise).  

From a security analyst’s perspective, knowing which protocol your organization uses isn’t trivia, it directly defines your attack surface. 
An enterprise running WPA2-Enterprise with RADIUS-backed authentication is in a very different posture than a café router still on WPA2-Personal with a shared password.  

---

## Firewalls: Packets Don’t Walk In Unchallenged  

Firewalls are the gatekeepers, but they aren’t all the same:  

- **Stateless firewalls** operate only on predefined rules (like IP addresses and ports). They don’t remember past sessions or analyze traffic patterns,
  every packet is treated in isolation. That makes them faster, but also less secure, since they can’t detect suspicious trends.  

- **Stateful firewalls** go further by keeping track of the state of active connections. They don’t just check if a packet matches a rule;
  they analyze network traffic for **characteristics and behavior that appear suspicious** and block it before it enters the network. Because they maintain a session table,
  they can also easily tell the difference between legitimate return traffic and unsolicited packets from an attacker.  

- **Next-Generation Firewalls (NGFWs)** build on stateful inspection with even deeper security features. They can inspect packets at the application layer, apply IDS/IPS rules,
  perform deep packet inspection, and integrate threat intelligence feeds to recognize new attack patterns in real time.  

## Application Layer Firewalls: Why NGFWs Are Different  

You may have noticed that Next-Generation Firewalls (NGFWs) are described as **application-layer firewalls**. 
A **network-layer firewall** only sees the outside of the packet: source IP, destination IP, port, and protocol. If it sees HTTPS traffic on port 443, it assumes it’s fine and lets it through.  
An **application-layer firewall** goes deeper. It looks inside the request itself. For example, if an attacker tries to upload an unusually large file through an HTTPS request something far beyond what normal users would do, the application-layer firewall can spot this abnormal behavior and block it.  
That ability to understand **what the traffic is actually doing**, not just where it’s going, is why NGFWs are placed in the application-layer firewall category.  

### How IDS/IPS Work Inside NGFWs  

Suppose an attacker is running a **brute-force login attack** against a web application:  

- The **firewall** might still allow the traffic, since the requests look like normal HTTPS connections.  
- The **IDS** would notice the pattern of repeated failed logins and alert the security team.  
- The **IPS**, sitting inline, could block the attack in real time by dropping the malicious requests or cutting off the attacker’s session.  

It’s important to note that a **standalone IPS cannot create dynamic firewall rules**. It can only block packets or sessions as they pass through.  
When IPS features are integrated into an **NGFW**, however, detections can feed back into the firewall engine, allowing it to automatically generate **temporary blocklists or dynamic rules** against the attacker’s IP.  

---

## VPNs and VPN Protocols: Tunnels Through Hostile Territory  

A **VPN (Virtual Private Network)** hides and secures traffic as it moves across the uncontrolled internet. Instead of sending data in the clear, the VPN software on your device **encrypts the payload and encapsulates it inside another packet**.  

From the ISP’s point of view, all it can see is:  
- The **source IP** of your home router.  
- The **destination IP** of the VPN server you’re connecting to.  

The ISP cannot see the actual websites or services you’re reaching inside the tunnel.  

Once your encrypted traffic reaches the VPN server:  
1. The VPN server **decrypts** it.  
2. It **decapsulates** the original packet.  
3. It then replaces the **source IP** with its own and forwards the traffic to the final destination.  

To the destination site, it looks like the request came directly from the VPN server — not from your home IP. This provides both **privacy** (your ISP and local observers can’t read your data) and **anonymity** (the destination doesn’t see your real IP).  

---

### Two key deployment models  
- **Remote Access VPNs:** User devices connect securely into the corporate network. Think work-from-home employees who need access to internal apps.
    User Device → Home Router ⇄ Encrypted Tunnel ⇄ VPN Server/Gateway → Corporate Network
   
- **Site-to-Site VPNs:** Entire branch offices link securely over the internet as if they were one LAN.  
    LAN A → VPN Gateway A ⇄ Encrypted Tunnel ⇄ VPN Gateway B → LAN B
---

### Protocols That Power VPNs  
- **IPSec:** Supported by nearly every OS and widely used in site-to-site connections. Strong, but can be complex to configure.  
- **WireGuard:** The newcomer. Lightweight codebase, easy setup, often faster throughput. Increasingly favored for remote access.  

Protocol choice affects usability, performance, and risk tolerance, but the underlying idea remains the same: **build a secure tunnel through hostile territory.**  

---

## Proxy Servers: Middlemen With Purpose  

A **proxy server** is more than just “another hop.” It sits between a client and the wider internet (or between the internet and a server), and changes the way traffic is handled.  

- **Forward proxies**:  
  These act on behalf of internal users. When your device makes a request, the proxy forwards it to the destination site, but replaces your IP address with its own. To the website, it looks like the request came from the proxy, not you. This can:  
  - Hide internal IPs from the outside world.  
  - Enforce filtering rules (block categories of websites).  
  - Cache responses so multiple users don’t keep hitting the same external site.  

- **Reverse proxies**:  
  These sit in front of internal servers. External users think they’re talking to the server, but in reality, they’re talking to the proxy. This hides the server’s real IP and adds layers of control:  
  - Load balancing traffic across multiple backend servers.  
  - Applying TLS/SSL offloading (the proxy handles encryption/decryption, easing server load).  
  - Blocking malicious requests before they ever reach the server.  

- **Specialized proxies**:  
  - **Email proxies** filter spam and phishing before mail hits internal servers.  
  - **Web application proxies** can add WAF-like functionality, blocking things like SQL injection attempts.  

Unlike firewalls, which focus on **allow/deny decisions** based on rules, proxies **rewrite and mediate traffic**. They can cache, anonymize, filter content, or even terminate connections on behalf of clients or servers.  

### Why Not Use Proxies for Everything?  

It’s tempting to think proxies could replace firewalls or VPNs, since they can filter traffic and hide IPs. But their roles are different:  

- **Firewalls vs Proxies**  
  - Firewalls sit at the network boundary, enforcing broad rules on what traffic is allowed at all (e.g., block all inbound except HTTPS).  
  - Proxies only act on the traffic they’re explicitly handling (e.g., web proxy handles HTTP/HTTPS). They don’t cover all protocols or provide baseline perimeter defense.  
  - Without a firewall, attackers could bypass proxies entirely by using protocols the proxy doesn’t touch.  

- **VPNs vs Proxies**  
  - VPNs encrypt all traffic between your device and the VPN server, protecting data confidentiality across hostile networks.  
  - Proxies don’t inherently encrypt, unless combined with TLS, so your traffic might still be visible to eavesdroppers.  
  - VPNs also tunnel *all applications* (system-wide), while proxies usually work on specific apps (like browsers or email). 

---

## Security Zones, Subnets, and CIDR: Network Architecture as Defense  

A flat network is a security nightmare. If every device can freely talk to every other device, one compromised machine can put the entire environment at risk.
That’s why organizations use **segmentation**, dividing the network into zones and subnets that act like internal borders.  

- **Uncontrolled Zone:**  
  The outside world, the public internet. Nothing here is trusted, and all traffic from this zone must be inspected and filtered before entering the organization.  

- **Controlled Zone:**  
  Everything inside the organization’s boundary, but still segmented based on sensitivity:  
  - *DMZ (Demilitarized Zone)* → public-facing services like web server, DNS, or email server. Exposed to the internet, but isolated from the internal network.  
  - *Internal Network* → private servers and data that the organization needs to protect.
  - *Restricted Zone* → highly confidential information that is only accessible to employees with certain privileges. 

- **Subnetting and CIDR:**  
  These zones are built using **subnets** defined by **CIDR (Classless Inter-Domain Routing)** notation. For example:  
  - `192.168.1.0/24` means the first **24 bits** are the **network portion**, leaving **8 bits** for host addresses.  
  - That provides **2^8 = 256 addresses total**.  
  - Only **254 are usable**: the first (`192.168.1.0`) is the **network ID**, and the last (`192.168.1.255`) is the **broadcast address**(for ARP requests).  

## IP Address Classes vs CIDR  

Old IP classes had fixed sizes:  
- **A (/8):** ~16 million hosts  
- **B (/16):** ~65k hosts  
- **C (/24):** 254 hosts  
(D = multicast, E = experimental)  

This wasted space, so **CIDR** replaced it with flexible prefixes (`/24`, `/26`, `/30`) sized to actual need.  


- **Why it matters:**  
  Subnetting enforces isolation. If a worm spreads on the DMZ subnet, routers and firewalls prevent it from directly reaching the restricted zone. Each subnet acts like a containment chamber, reducing the blast radius of an attack.  

In short: **zones define trust boundaries**, while **CIDR and subnetting enforce them technically at the IP layer**. Together, they form the blueprint of defensive network architecture.  

---

## Closing Reflection  

The takeaway is simple: protocols and tools are not standalone. A secure Wi-Fi standard doesn’t matter if mail still comes in through plaintext POP3. Subnets are meaningless if all rules are open.  

Real security is about **integration**. Protocols, wireless standards, segmentation, firewalls, proxies, and VPNs all working together. That’s the reality of defending a network: one misstep in any layer can break the chain.  

---

[← Back: Module 1](module-01.md)   &nbsp; | &nbsp;   [Next: Module 3 →](module-03.md)
