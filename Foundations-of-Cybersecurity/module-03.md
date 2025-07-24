---
title: "Module 3 – Designing Security From the Start "
parent: "Foundations of Cybersecurity"
nav_order: 3
layout: post
---

# Module 3

## What Happens After You Know the Threats

After learning how cyber attacks work and how humans often end up being the weakest link, this week’s module shifted the focus to something more proactive: **how organizations build security into their systems from the start**.


Because once you know how attackers think, you realize the real goal isn’t to patch things up *after* the damage. It’s to **design systems that are harder to break in the first place**. That’s where frameworks, controls, and smart thinking come in.

---

## What Are We Even Trying to Protect?

Before anything else, a security team needs to understand what they’re up against.

- **Asset**: Anything valuable like data, money, systems, services, or even your brand reputation.  
- **Vulnerability**: A weakness in a system that a threat actor can take advantage of, like an unpatched app or weak password.  
- **Risk**: The **likelihood** that an attack will happen, and how bad the impact would be if it does.

Let's understand with an example:

**Your gold ring is the asset.**  
Leave it on the road (big **vulnerability**) and thieves (**threat actors**) are likely to steal it. Since both the **likelihood** and the **impact** (losing something valuable) are high, the **risk is high**.

Lock it in a safe, the **threat still exists**, but the **likelihood drops**, so **risk is low**.

Now replace the gold with a **plastic ring**. On the road, the **likelihood of theft** is still high, but the **impact is low**, so the **risk stays low**.

> **Risk = Likelihood × Impact**

- **High risk** = easy to steal **+** high value (gold on road)  
- **Low risk** = easy to steal **+** low value (plastic on road)  
- **Low risk** = hard to steal **+** high value (gold in safe)


---

## The CIA Triad Still Guides It All

Back in Blog 1, I talked about the **Confidentiality, Integrity, Availability (CIA) triad**- the 3 goals of cybersecurity. What I now realize is that **every threat, vulnerability, and risk comes down to one of these being at stake**.

> **The CIA triad isn’t just a concept — it helps teams decide what kind of controls to put in place.**

- If you’re worried about data leaks -> you put controls in place to protect **Confidentiality**  
- If you’re worried about data being changed or corrupted -> focus on **Integrity**  
- If you’re worried about systems being unavailable during emergencies -> protect **Availability**  

That one principle guides almost every security decision. Whether you’re writing a policy, setting up backups, or training your team, you're usually protecting one (or more) parts of CIA.

---

## You Can’t Just Hope for the Best, You Design for the Worst

Good security is proactive, not reactive. And that means thinking about risks *before* someone gets hacked.

That’s where something called **secure design** comes in, planning systems in a way that reduces risk from the very beginning.

---

## Frameworks: The Game Plan

A **security framework** helps organizations figure out what areas to cover, without telling them exactly how to do it. Think of it as a checklist for building mature, thoughtful security.

The one focused on was the **NIST Cybersecurity Framework**, which breaks security into 5 functions:

1. **Identify** what’s at risk  
2. **Protect** it using safeguards  
3. **Detect** when something bad happens  
4. **Respond** to incidents  
5. **Recover** and learn from the damage  

This isn’t just for tech teams, it helps the whole organization align on priorities and plan for the real world.

---

## Controls: The Actual Defense Moves

Frameworks are the strategy. But **controls** are the actual things companies do to reduce risk.

They come in all forms:

- **Technical controls** - like encryption, firewalls, or login restrictions  
- **Administrative controls** - like training, policies, or regular audits  
- **Physical controls** - like locked doors or badge access  

Every control is chosen based on:
- What threats the organization faces  
- What vulnerabilities exist  
- Which risks are most critical to address 
- And which part of the **CIA triad** is most at risk

For example:
- Phishing emails? → Training and spam filters (**Confidentiality + Integrity**)  
- Servers crashing? → Redundant systems and backups (**Availability**)  
- Weak passwords? → Strong password policy + multi-factor authentication (**All three**)  

So the triad isn’t just theory. It helps teams figure out which **controls** are worth their time and money.

In the gold ring example, the **locked safe is the control** that reduces risk by limiting access to the asset.  
So, **risk goes up or down based on how exposed the asset is — and controls are what shrink that exposure**.


---

## Compliance: When Security Isn’t Optional

On top of doing what’s smart, many companies also have to do what’s **required**, that’s **compliance**.

Depending on the industry, there are strict rules about how data should be protected:

- **HIPAA** for healthcare  
- **GDPR** for data privacy in Europe  
- **PCI DSS** for payment systems  

If a company doesn’t meet compliance standards, the risks aren’t just technical, they’re legal, financial, and reputational.

That’s why security isn’t just an IT problem. It’s an **entire organization’s responsibility**.

---

## The Human Part: Ethics in Cybersecurity

The last part of this module took it a step further: even if your controls and tools are perfect, **you still need people to act with integrity**.

Ethics matters because:

- Security professionals often have access to sensitive data  
- The power to protect is also the power to misuse  
- Trust is everything in this field  

Whether it’s reporting misconduct, protecting user privacy, or refusing to bend the rules under pressure, being ethical is just as important as being technically skilled.

---

### What I Want to Explore More

**What kind of controls can we design to protect even the most naive or unaware user?** 

I want to reach a point where **clicking a malicious link doesn’t even matter**, because the system is built so well that it blocks or isolates the threat before it causes harm. 
Designing security that doesn’t depend on people always doing the right thing.

Because let’s be honest: people will keep clicking. The system should be smart enough to expect that and still hold strong.

---

## Final Thoughts: Good Security Is Built, Not Bolted On

This module made me realize that cybersecurity isn’t just about responding to attacks, it’s about **designing systems that are ready for them**.

You:

- Understand your risks  
- Follow a clear framework  
- Pick the right controls  
- Stay compliant  
- And lead with ethics  

And all of that is guided by the one principle that’s been there since Blog 1: **the CIA triad**.

[← Module 2](module-02.html) &nbsp; | &nbsp; [Module 4 →](module-04.html)
