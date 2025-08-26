---
title: " Module 1 - Network Architecture"
parent: Connect & Protect
nav_order: 1
layout: default
---

# Module 1
## Network Architecture

A network is a group of connected devices such as laptops, servers, phones, printers, and more that can share data and resources. 
Connections can be **wired** (Ethernet) or **wireless** (Wi-Fi).

Networks come in two main forms:  
- **Local Area Network (LAN):** Covers a small geographic area like a house, office, or school. Example: your home Wi-Fi.  
- **Wide Area Network (WAN):** Spans large geographic areas like cities, countries, or the entire globe. The internet itself is the largest WAN.

LANs can connect to WANs, allowing a device in your home to communicate with a server halfway across the world.

---

## Network Devices
Networks rely on specific hardware (or virtual equivalents in the cloud) to control traffic and maintain communication.

- **Hub:** Broadcasts all incoming data to every connected device. Simple, but insecure, anyone can intercept the traffic.  
- **Switch:** Forwards traffic only to the intended device by using a **MAC address table** (mapping each MAC address to a physical port). 
- **Router:** Connects multiple networks and routes packets based on **IP addresses**. 
- **Modem:** Converts your ISP’s transmission format (DSL, cable, fiber) to digital Ethernet connection for your network.  
- **Firewall:** Filters incoming and outgoing traffic based on security rules.  
- **Wireless Access Point:** Provides Wi-Fi connectivity using radio signals.

**Virtualization:** In modern networks, these functions can be implemented as **virtual network devices** in the cloud (e.g., virtual routers, firewalls, switches) for scalability and cost savings.

---

## Communication on a Network
Data is broken into **packets** before transmission. Each packet contains:
- **Header:** Source/destination addresses, protocol, control info.  
- **Payload:** Actual data (file part, HTML code, email content).  
- **Footer:** Marks the end and includes error-checking.

**Bandwidth:** Maximum data transfer capacity per second.  
**Speed:** Actual rate of delivery.

**Packet sniffing:** Capturing and analyzing packets to inspect traffic and detect anomalies.

---

## TCP/IP Model (4 Layers)

### 1. Network Access Layer
Handles physical delivery over Ethernet, Wi-Fi, etc. Frames are used here, containing:
- Source MAC address  
- Destination MAC address  
- Encapsulated packet

**ARP (Address Resolution Protocol)** operates here, it maps an IP address to its corresponding MAC address within the same network. 
Example: if your device knows the IP `192.168.0.10` but not the MAC, it sends an ARP request asking, “Who has this IP?” The device with that IP replies with its MAC.

---

### 2. Internet Layer
Adds IP addresses to create **IP packets**. Protocols here include:
- **IP (IPv4/IPv6):** Addressing and routing. It ensures each packet contains the correct source and destination IP addresses, determines how packets are forwarded.
  IPv4 uses 32-bit addresses, while IPv6 uses 128-bit addresses for a vastly larger address space.
- **ICMP (Internet Control Message Protocol):** Used by devices to send error messages, operational information, and diagnostics.

---

### 3. Transport Layer
Handles end-to-end communication between applications on different devices. Adds source/destination **ports** and creates:
- **Segments** when using TCP  
- **Datagrams** when using UDP

**TCP (Transmission Control Protocol)** is **connection-oriented**, before sending data, it uses the **3-way handshake**:
1. **SYN:** Client requests a connection.  
2. **SYN-ACK:** Server acknowledges and agrees.  
3. **ACK:** Client confirms, and data transfer begins.

This ensures reliable delivery, ordered packets, and retransmission if data is lost.

**UDP (User Datagram Protocol)** is **connectionless**, data is sent without establishing a connection first. Faster, but no guarantee of delivery or order.
Ideal for real-time applications like VoIP, gaming, and live streaming.

---

### 4. Application Layer
It directly involves the everyday user, containing all the networking protocols that software applications use to connect the user to the internet.
- **HTTP/HTTPS:** Web browsing  
- **DNS:** Resolving domain names to IP addresses  
- **FTP/SFTP:** File transfers  
- **SMTP/IMAP/POP3:** Email transfer and retrieval 

---

**Data naming at each stage:**
- Application layer → Data  
- Transport layer → Segment (TCP) or Datagram (UDP)  
- Internet layer → Packet  
- Network access layer → Frame

---

## OSI Model (7 Layers)
1. **Physical:** Cables, signals, wireless transmission.  
2. **Data Link:** MAC addresses, switches, Ethernet frames.  
3. **Network:** IP addressing, routing.  
4. **Transport:** TCP/UDP, segmentation, reassembly.  
5. **Session:** Session creation, management, and closure.  
6. **Presentation:** Data formatting, encryption, compression (e.g., SSL/TLS).  
7. **Application:** Services for end-users (web, email, file transfer).

---

## IP Addresses & MAC
- **MAC address:** Unique hardware identifier for local network delivery.  
- **IP address:** Logical identifier for routing across networks.

**IPv4:**  
- Format: `192.168.0.1`  
- 32-bit address space (~4.3 billion possible)  

**IPv6:**  
- Format: `2001:db8::ff21:23:45`  
- 128-bit address space (~3.4×10³⁸ possible)  

**Public vs Private:**  
- Public IP: visible on the internet, assigned by ISP.
  In most home and office networks, the router holds the public IP, and all devices behind it share that address externally through Network Address Translation (NAT).
- Private IP: internal-only, reserved for use within private networks, such as your home Wi-Fi or an office LAN, and is not routable on the public internet.
  
**NAT (Network Address Translation)**: Performed on routers, NAT maps private internal IP addresses to a single public IP by assigning unique source ports for each active connection.

The NAT table functions like a logbook, recording which internal device and port correspond to which public port:
192.168.0.5:51512 → 203.0.113.45:443
192.168.0.8:51513 → 203.0.113.45:443

When a response comes back from the internet, the router checks the NAT table entry and uses the port mapping to deliver the packet to the correct internal device.

---

## IPv4 Packet Structure
Fields include:
- Version, Header Length, Type of Service, Total Length  
- Identification, Flags, Fragment Offset  
- TTL, Protocol, Header Checksum  
- Source IP, Destination IP  
- Options (optional extra settings)

IPv6 removes some IPv4 fields, handles fragmentation differently, and adds **Flow Label**.

---

## Cloud Computing & SDN
**Cloud Service Models:**
- **SaaS:** Full applications (e.g., Gmail)  
- **PaaS:** Development environments (e.g., Microsoft Azure App Service)  
- **IaaS:** Virtualized infrastructure (e.g., Amazon EC2) 

**Deployment Models:**
- **Hybrid Cloud:** On-prem + cloud mix  
- **Multi-Cloud:** Multiple CSPs

**SDN (Software-Defined Networking):** Virtualized network control via software, enabling fast configuration and scaling.

---

## Why This Matters
- Pinpoint attack location (application exploit, transport flood, routing manipulation, MAC spoofing).  
- Trace malicious actors through NAT and MAC tables.  
- Apply the right defense at the right layer.  
- Understand how different protocols interact and where vulnerabilities may exist.

---

## Something Interesting  
The TCP/IP layers are often shown as neat, separate boxes in diagrams, but in real life they work more like a team in constant conversation.
A Transport Layer handshake can’t start until the Internet Layer provides an IP address, which in turn depends on the Network Access Layer finding a MAC address.
In reality, the layers coordinate closely, with processes in one layer often triggering actions in another.


[← Back: Course 2, Module 4](../Play-It-Safe/module-04.md)   &nbsp; | &nbsp;   [Next: Module 2 →](module-02.md)
