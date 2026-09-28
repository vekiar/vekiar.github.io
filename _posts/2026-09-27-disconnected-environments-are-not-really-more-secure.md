---
layout: post
date: 2026-09-27
title: "Disconnected environments are (not really!) more secure"
categories: security madlibs
---

A few years ago, a former colleague (let's call them "Mike") was put in charge of evaluating a move to AWS/GCP/Azure. Mike concluded that none of the options was "good enough". Their rationale, in three acts: 1/ The company's internal cloud had no direct access to or from the internet; 2/ 80% of issues on AWS are caused by misconfigurations (i.e. AWS makes it easy to "shoot yourself on the foot"); and 3/ there was no benefit for the engineering population of learning and / or upskilling to AWS.  

TL;DR: Mike was **wrong**. At the core was a big, hairy, conceptual mistake. And most customers in regulated industries make the same mistake.  

Mike's flawed premise rests on the fact that "not connected to the internet" dos not mean something is secure. This belief assumes that the internet is the primary threat (it is not); that isolation implies control (it does not); and that fewer network paths means a proportionately smaller attack surface (it does not).  

In reality, most serious breaches in corporate environments do not come from exploiting obscure zero-day vulnerabilities over the internet. They come from identity compromises, supply chain attacks, insider access (especially contractors), lateral movement from trusted systems, backup infrastructure, and management planes. None of these threats dissapear just due to the lack of direct internet connectivity.  

But, is the threat model for a private cloud not "better" than that of its public equivalent? To answer this, we need to first look at what the "cloud" being "private" gains us. (Note: air quotes for emphasis of terms that may have different definitions to different people). The bottom line is that severing all internet connectivity from a set of computers (a "datacenter") give us narrower opportunities for attackers to scan, a smaller range of "commodity" attacks, and fewer opportunities for drive-by's. Then we need to consider what is lost. Namely, the scale of security research and development a hyperscaler brings with them, the lack of continuous red-team/adversary-emulation capabilities (even if they never speak about them), and the lack of hardware root-of-trust, provable control plane isolation, and default cryptographic identity fabric (this last one may deserve its own write up!). As most regulated / security conscious (slash paranoid!) companies will be able to attest to, defending against known insiders (and silent failure modes) is not inherently easier than defending against "the internet". Interestingly, removing one does not make the job easier. And, in some cases, it may contribute to making the job harder, if engineers and leaders buy into Mike's "disconnected means safer" fallacy.  

Bottom line up front: AWS/GCP/Azure are not secure by default. They take planning, architecting, and implementing controls carefully. But they enable security properties that no "private" cloud, however disconnected or airgapped from the internet, can deliver. By default, AWS offers customers the type of primitive that is hard-to-impossible to replicate. Hardware-backed identity (Nitro, TPM, instance attestation), machine-to-machine auth, no interactive access ("zero" operator access), policy-as-code, and auditable trails across all of their services and systems. The last time a non-hyperscaler company evidenced having (any of) these controls was ... well, never.  

In fact, non-hyperscaler companies tend to have the reverse incentive. Absent economies of (large) scale, local optimisation kicks in. If you asked Mike how their company manages their PKI infrastructure, his (hypothetical) answer would most likely be "with a Windows 10 laptop and a Yubikey". Let that sink in ...  

The uncomforable truth is that Mike feels his private cloud is "more secure" because it is opaque. Mike cannot see nor measure every single corner. And often, companies (managers) deliberately break down ownership of and work on the platform such that each team only sees and understands a small piece of the estate, and not the whole picture. Unfortunately, the only thing this creates is a false sense of confidence. And, with zero external pressure to improve, the narrative that "private is safer" and "disconnected is secure" quickly takes over. Mike believed it. Mike's CTO believed it. Mike's CEO got on stage at a company town hall and branded the company's estate "the most secure platform in our industry".  

Less than 24 hours later, their trade secrets had made their way across the English channel.  

So, are we saying this would not have happened if they had migrated to AWS/GCP/Azure? Not exactly. In principle, public cloud creates a brutal amount of visibility. Teams are forced into better hygiene, and incompetence _may_ (note the italics, nothing is guaranteed!) find it hard to hide. But any company that has made the jump to public cloud will know that "just" moving into cloud ("lift-and-shift") will only perpetuate the same issues companies have on ground. Public cloud only wins if companies take the time and effort to redesign and re-architect their systems.  

And there is one place where private cloud will hands-down, hulk-hogan-inside-the-steel-cage-judge-jury-and-executioner win: jurisdictional exposure. Digital Sovereignty is a loaded term. But to put it simply, using a public cloud carries legal and regulatory implications the limits of which may not end where the borders of your country (or the one where your company is registered / operates) end. These are not stictly speaking security arguments, and you should always check with a solicitor to get an educated assessment of where you and / or your company stands relative to any such risks and / or exposure.  

So what is the takeaway?
- "Not connected to the internet is more secure" is a 2005 argument that has not worked since you first found out what Counterstrike was;
- Security boils down to how you manage identities (more on that in a future article!), control planes, and failure modes / blast radius;
- Most people will confuse comfort with safety;
- What Mike so passionately defended is not a measurable, falsifiable security model, but rather an emotional attachment;