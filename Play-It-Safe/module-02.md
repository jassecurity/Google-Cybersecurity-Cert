---
title: "Module 2 – Security in Practice"
parent: Play It Safe
nav_order: 2
layout: default
---

# Module 2
## Security in Practice: Frameworks, Controls, OWASP, and Audits

Once you’ve mapped your risks, spotted your weak points, and wrapped your head around the whole CIA triad, the real work begins.

Because let’s be honest, **threats are inevitable**, mistakes will happen, and people *will* click things they shouldn’t. 
So the question isn’t *how to avoid all attacks*. It’s **how to stay standing when they come**.

---

## The Control Trio: Encryption, Authentication, Authorization

If you're protecting a system, there’s no getting around them. Let me explain them not as definitions, but as **decisions** you have to make when you're designing security.

* **Encryption** is about locking the content. Data, files, traffic — everything. It's the difference between a letter and a sealed envelope. 
Even if someone snatches it mid-transit, they can’t read it. 
But it’s more than just protecting files; it’s about **preserving confidentiality and sometimes integrity** too.

* **Authentication** asks: *Are you who you say you are?* But it’s not just login screens. It’s biometrics, OTPs, a whole ecosystem of proof.
Because verifying identity is foundational. Get this wrong, and all other controls crumble.

* **Authorization** goes one step further: *Okay, you’re in, but what are you allowed to do?* 
You wouldn’t give a student access to financial records, just like you wouldn’t give a guest account admin privileges. Authorization guards **scope and access**.

These three controls live at the core of most systems, **and they directly defend the CIA triad**:

---

## Frameworks Help You Think; Controls Help You Act

I’ve already talked about this in the last blog, **frameworks give you direction**, but they don’t tell you which firewall vendor to choose or how long your passwords should be.

There are three main types of controls:

- **Preventive Controls**: Stop something from happening (e.g., password requirements).
- **Detective Controls**: Spot when something’s wrong (e.g., intrusion detection systems).
- **Corrective Controls**: Fix the damage (e.g., restoring from a backup after ransomware).

These controls are how we apply frameworks in real life.

---

### The 6 NIST CSF Functions (Not 5 Anymore)

Turns out, it’s not just 5 functions. 
This is the one new function added to the CSF- its **Govern.**

 -Who is accountable for security decisions?
 -Is cybersecurity tied to business objectives?
 -Is there a defined risk tolerance?

Without governance, security becomes a patchwork, random controls, scattered priorities, and no long term vision. 
This function forces organizations to treat cybersecurity as part of the business, not just IT.

The remaining five functions- Identify, Protect, Detect, Respond, and Recover were already explored in Course 1, Module 3.

---

## CTF: Understanding the Threat in Layers

The **Cyber Threat Framework (CTF)** was introduced as a way to *categorize what attackers do*, from basic reconnaissance to actual impact.

And it’s kind of like watching a thief case a house before breaking in. There’s a pattern.

The CTF breaks attacks into phases:

1. **Preparation** - Scanning, planning  
2. **Engagement** - Gaining access  
3. **Presence** - Staying hidden, moving laterally  
4. **Effect** - Doing damage: stealing data, destroying systems  

What’s useful here is that it doesn’t just help blue teams (defenders) recognize what to look for, it also informs **which controls go where**.

* Detecting *preparation*? That’s firewall logs and threat intel.  
* Blocking *engagement*? That’s MFA and password managers.  
* Stopping *presence*? That’s anomaly detection and segmented networks.  
* Preventing *effect*? That’s encryption, backups.

CTF makes threat modeling more **structured and predictable**, which helps controls become **more intentional**.

---

## ISO/IEC 27001: Security at a Management Level

If NIST CSF is a practical framework for operations, **ISO/IEC 27001** is more about **building a culture of security** across the organization.

It’s international. It’s audit-focused. And it’s not just about firewalls, it’s about policies, responsibilities, risk treatment plans, and documentation.

You don’t pass ISO 27001 by having good antivirus. You pass it by **demonstrating that security is embedded into your organization’s decisions**, from HR to IT to procurement.

---

## OWASP Security Principles

**OWASP** principles are like the commandments of secure software development. Most people know the Top 10 (injections, broken auth, etc.), but the **core principles** go deeper:

* **Minimize Attack Surface Area** - Reduce points of entry.  
* **Establish Secure Defaults** - Default configurations should be the safest.  
* **Principle of Least Privilege** - Only give permissions needed.  
* **Defense in Depth** - Layered defenses to handle failure.  
* **Fail Securely** - Systems should remain secure on failure.  
* **Don’t Trust Services** - External services can’t be assumed safe.  
* **Separation of Duties** - Avoid giving one entity total control.  
* **Avoid Security by Obscurity** - Don’t rely on secrecy for security.  
* **Keep Security Simple** - Complexity = more mistakes.  
* **Fix Security Issues Correctly** - Don’t patch blindly, understand the root cause.  


---

## Audits: When You Turn the Lights On

All of this- frameworks, controls, principles means nothing if you never check whether they’re actually working.

That’s where **audits** come in. Not the “someone’s in trouble” kind but the “let’s validate our setup” kind.

There’s a difference between:

* *Assuming you’re secure*, and  
* *Proving you are*

Audits force organizations to check their controls:

Here’s how it typically flows:

1. **Set the scope**  
   Decide what systems, assets, and policies you’re evaluating, and why. Is it for compliance? Risk reduction? Regular hygiene?

2. **Review policies**  
   Check if documented procedures actually reflect what’s happening. Are people following them? Are they still relevant?

3. **Assess risk**  
   Look at where the biggest threats or gaps exist, from outdated controls to budget issues or compliance gaps.

4. **Test controls**  
   Verify if the safeguards in place (like firewalls, MFA, locked doors) are working as intended.

5. **Build a mitigation plan**  
   For anything broken or risky, outline how you’ll fix it, what, who, when.

6. **Report findings**  
   Summarize the results for stakeholders: what’s working, what’s not, what needs urgent attention.  

**This module also includes an audit project** You can view the audit report **[here](audit-report.md).**

---

## What I Took Away from This

Security is not just about blocking threats. It’s about **building something resilient enough to take hits** and still stand.

This module stitched together a lot of scattered ideas:

* How threat intelligence feeds decisions on controls (CTF)  
* How frameworks give us structure (NIST, ISO)  
* How controls are tactical defenses (encryption, auth)  
* How software has to be built smart from the ground up (OWASP)  
* How you close the loop with verification (audits)

It’s like designing a house in a flood zone:

* You plan with blueprints (frameworks)  
* You build with the right materials (controls)  
* You anticipate how water will try to enter (CTF)  
* You make sure the plumbing and electric are safe (OWASP)  
* And then, you inspect it regularly (audits)

---

## What I Want to Explore

I plan to explore the OWASP Top 10 using Juice Shop and secure it using core security principles.

---

## Final Thought: Secure Systems Expect Failure

That’s the mindset shift I’m noticing.

It’s not just “stop hackers.” It’s *design systems that expect people to mess up, expect attacks to slip through, and still protect what matters*.

Security isn’t about perfection. It’s about **resilience**.

And the more I learn, the more I respect how much thought goes into getting it right, not just reacting to damage, but **planning for it before it happens**.

---
[← Back to Module 2](module-01.md)   &nbsp; | &nbsp;   [Next: Module 3 →](module-03.md)
