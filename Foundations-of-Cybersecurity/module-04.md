---
title: "Module 4 – Tools That Actually Do the Work"
parent: "Foundations of Cybersecurity"
nav_order: 1
layout: default
comments: true
---
# Module 4

## Tools That Actually Do the Work

In this module, I started to understand how a security analyst actually works, with the tools, the data, and the daily grind of defending systems.

We didn’t get hands-on yet, but this module made me start *thinking like a defender*. Here's how I understood it.
Not everything I’ve written here was covered directly in the module but I explored beyond it to better understand how these tools work together and what role each one plays.

---

## It All Starts With Network Traffic

Everything on a network like emails, files, links, logins moves around as packets of data. These packets are tiny chunks of information, flying across the network 24/7.  
Most are harmless. Some are not.

A **threat** can hide in one of those packets. It could be malware inside an email attachment. A suspicious connection from an unknown IP. Or a compromised device sending out stolen data.

As defenders, we don’t have a sixth sense, we have tools. And the first thing we do is **listen**.

---

## Packet Sniffers: Listening to the Noise (CCTV Cameras)

This is where tools like **Wireshark** come in.  
They’re called **network protocol analyzers**, or more casually, *packet sniffers*.

They watch everything on the wire. Every single packet.

- Someone sends a PDF? You’ll see the request.
- A user visits a sketchy site? You’ll catch the DNS lookup.

But sniffers don’t tell you what’s wrong, they just give you visibility. You have to know what to look for. It’s like standing on a highway trying to spot a stolen car. Powerful, but overwhelming.

---

## IDS: Watching for Trouble = The Trained Traffic Cop

Enter the **Intrusion Detection System (IDS)**.  
It builds on what sniffers see but adds logic.

An IDS monitors traffic and compares it against known patterns of malicious behavior.

- Someone tries to log in 500 times in 30 seconds? Alert.
- A device suddenly starts sending huge amounts of data out? Alert.

Unlike packet sniffers, an IDS isn’t just watching, it’s judging. It flags things that look suspicious or outright dangerous.

But it’s still passive. It tells you *something happened*. It doesn’t stop it or give full context.

---

## SIEM: The Brain Behind It All = The City’s Traffic Control Center

A SIEM is like the command center. It collects logs from *everything*, the network, endpoints, servers, cloud services, firewalls, even the IDS itself.

All those individual events that seem unrelated?  
The SIEM stitches them together and looks for patterns over time.

 It asks:
- Are multiple alerts connected?
- Is this isolated, or part of a coordinated attack?
- Who logged in, from where, and what did they do next?

If the IDS says a car is driving weird, and the logs say that car came from a known dangerous neighborhood, SIEM puts the pieces together and raises a bigger flag.

Alone, these are red flags. Together, it’s a **story of compromise**.  

Tools like **Splunk**, **Chronicle**, or **Elastic SIEM** do this job. 

---

## Logs: The Truth Lives Here

All of this- sniffers, IDS, SIEM depends on **logs**. 

A log is a simple record:  
- “User X logged in at 2:04 AM from IP Y.”  
- “Service Z crashed.”  

Without logs, there’s no story to tell.  

Learning to read logs is like learning to read a digital crime scene. Analysts don’t just read logs, they **interpret** them. It’s a skill I want to build.

---

## Playbooks : Handling Incidents Right

Even with all this tech, the response needs to be clear. That’s where **playbooks** come in. They’re like your emergency manual when a traffic jam, hit-and-run, or accident happens on the network highway.

These documents outline what to do, when to do it, and how to do it without making things worse.

Key concepts I learned:

- **Chain of Custody:** Keep track of who accessed what, when, and why. Just like tagging evidence in a real investigation. You don’t want evidence contaminated or questioned.

- **Preservation of Evidence:** Don’t touch the original data. Make forensic copies. If you’re pulling a hard drive or analyzing RAM, the way you do it matters.

- **Order of Volatility:** It's about **what data disappears the fastest**.
  Here's the general order, from most to least volatile:
  1. **CPU cache, memory (RAM), running processes**  
  2. **Network connections and live data**  
  3. **Temporary files and disk data**  
  4. **Logs**

  So during incident response, you **capture memory and live traffic first** and not the disk. That’s counterintuitive but makes sense when you realize how quickly RAM and connections can vanish.

Playbooks aren't about guessing, they're about being ready, even under pressure. And in cybersecurity, process can make or break your response.


---

## How These Tools Work Together

Let me try to piece it all together, the way I understand it now:

1. **Traffic flows** across the network.
2. **Packet sniffers** record everything.
3. **IDS** watches for suspicious patterns in real time.
4. **Logs** get generated by every system involved.
5. **SIEM** collects those logs, correlates events, and raises alerts.
6. **Playbooks** guide the analyst in responding.

They all play a part like different parts of the immune system.

---

## My Takeaways

This module reminded me that **threats don’t always come charging through the front door**.  
They sneak in through packets, email links, misconfigured apps, or human error.

A threat actor might look like a normal user in the logs.  
Or hide malicious code inside a file.  
Or spread across systems slowly, over weeks.

**Detection is subtle.** And it’s only possible if you're collecting the right data and know what to do with it.

---

## What I Want to Explore More

- **Hands-on tools** – We learned about them, but I want to use them. Install Wireshark. Trigger alerts. See real SIEM dashboards.
- **Automation with Python** – To filter logs, detect patterns, and maybe even simulate attacks in test environments.

---

## Final Thoughts

This module didn’t hand me tools but it *did* show me what the tools are for.  
And that shifted my thinking. I’m not just learning terms anymore. I’m learning **how things connect**.

I still don’t know everything, far from it. But now I can see the workflow.

And honestly? That’s exciting.

---
Course 1 - Foundations - done. I’m walking away with knowledge, yes. But more importantly: curiosity, confidence, and a sense of direction.

*Next: deeper dives, more technical skills, and eventually, hands-on labs.*

[**Module 3**](./module-03.md)  &nbsp; | &nbsp;  [**Course 2 - Module 1**](/Play-It-Safe/module-01.md))
