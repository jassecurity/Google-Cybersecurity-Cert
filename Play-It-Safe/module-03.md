---
title: "Module 3 - SIEM & SOAR "
parent: Play It Safe
nav_order: 3
layout: default
---

# Module 3
## SIEM & SOAR

Last time we talked about tools, it was all about seeing the network — sniffers, IDS, SIEMs — and how those tools help you *notice* something’s wrong.  
If you missed that, go check out my earlier blog from [Course 1, Module 4](../../Foundations-of-Cybersecurity/Play-It-Safe/module-04.md), where I broke down that layered approach using road traffic as an analogy.

This module talks about how those tools are evolving, how cloud-based dashboards are reshaping analyst workflows, how log sources are expanding, and how automation is becoming a critical part of the response process.

---

## 🧠 SIEM Dashboards: From Raw Logs to Real Insight

As we mentioned earlier, SIEM tools like **Splunk** and **Chronicle** collect logs, correlate events, and help analysts detect threats.  
But this time, we got to know about the **SIEM dashboards** where all that data becomes readable and actionable.

It’s kind of like comparing raw weather data to a weather app.
You could look at temperature, pressure, and wind speed number or you could see the storm front coming on a map.

With SIEM dashboards, you’re doing the same thing turning **firewall logs**, **network traffic**, and **server activity** into visual, filterable panels that let you catch the weird stuff fast.

Example?  
500 login attempts for the same account from 3 countries in 5 minutes.  
You don’t need to scroll logs to know something’s up, the dashboard lights up like a warning sign.

---

## Logs: The Foundation We Keep Building On

As we mentioned earlier, everything depends on logs.  
But now we’re categorizing them more precisely:

- **Firewall logs** – Track connection attempts and traffic crossing the network boundary.
- **Network logs** – Capture what’s moving between devices *inside* the network.
- **Server logs** – Record service level stuff: logins, emails, app activity.

Each one gives a different layer of the story. And the SIEM combines them all.

---

## The Cloud Shift: What It Means for SIEM

This module emphasized how SIEMs aren’t just sitting on-prem. 

- **Cloud-hosted** SIEMs (like Splunk Cloud) let vendors manage the infra. You just log in and start analyzing.
- **Cloud-native** SIEMs (like Google Chronicle) go even further, built for scale, flexibility, and speed.

The advantage? More data, faster insights, and no need to maintain servers yourself.

The challenge? Customization, access control, and staying ahead of new types of **threat actor behavior** that’s designed to move silently across massive, distributed environments.

This also made me think about **third party risk**. When you're relying on external tools to handle sensitive logs, trust becomes part of the equation.

---

## SOAR: The Analyst’s New Teammate

SIEM tools are starting to lean on **automation**. This isn’t about replacing analysts, it’s about **speeding up repetitive detection and response tasks**.

But here’s the thing: most of that response automation comes from **SOAR integrations** or **built-in SOAR like features**.

Enter **SOAR** (Security Orchestration, Automation, and Response), it adds playbooks and decision trees to the SIEM's alerts.

With SOAR in the mix, the system can:

- Trigger an alert,  
- Launch a playbook,  
- Block an IP or user,  
- Log the action for review.

So while traditional SIEMs **detect**, SOAR helps them **respond**.

---

## Mixing Open Source with Enterprise Tools

This module didn’t frame open source and proprietary tools as rivals, it showed how they often **work together** in real world setups.

Tools like **Suricata** (open-source) might handle deep packet inspection, while something like **Chronicle** (proprietary) pulls all that data into a high-speed SIEM dashboard.

It’s not about picking sides, it’s about knowing what each tool brings to the table.

---

## 🧠 Final Thoughts

Logs and alerts are just noise without context. Dashboards, SOAR workflows, and real-time analytics give that noise shape, and help you act on it, fast.

[← Back to Module 2 ](module-02.md)   &nbsp; | &nbsp;   [Next: Module 4 →](module-04.md)
