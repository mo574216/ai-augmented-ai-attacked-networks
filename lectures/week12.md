---
title: Week 12- LLMs as Attackers and Defenders
nav_order: 12
---

# Week 12: LLMs as Attackers and Defenders

## Overview

In the previous weeks, we gradually developed a broad view of AI-native networking, security, and operations.

- In Week 2, we studied the foundations of machine learning for networking.
- In Week 3, we examined telemetry, observability, and measurement as the basis of intelligent networking.
- In Week 4, we explored traffic classification and application identification as a problem of network perception.
- In Week 5, we studied deep learning for network analytics as a way to learn richer internal representations.
- In Week 6, we examined reinforcement learning for routing and congestion control.
- In Week 7, we studied AI for SDN and network resource management in the context of network softwarization.
- In Week 8, we studied graph learning for networked systems, emphasizing that many networking problems are fundamentally relational.
- In Week 9, we studied AI for cybersecurity, with focus on IDS, malware analysis, and DDoS defense.
- In Week 10, we studied adversarial machine learning and saw that once AI is deployed in networking and security, the AI system itself becomes part of the attack surface.
- In Week 11, we studied LLMs for network automation and operations, focusing on retrieval, bounded tool use, verification, and human oversight.

This week, we extend that discussion into a broader cyber context:

> **LLMs as Attackers and Defenders**

The key idea of this lecture is the **dual-use nature** of large language models in cybersecurity.

The same model family that can help defenders:

- summarize alerts,
- analyze incidents,
- retrieve technical knowledge,
- explain logs,
- draft detections,
- and support SOC workflows

can also help attackers:

- scale phishing,
- improve impersonation,
- accelerate reconnaissance,
- assist malicious scripting,
- coordinate offensive workflows,
- and lower the barrier to cyber misuse.

The purpose of this week is not to treat LLMs as magical offensive or defensive agents. That would be misleading.

Instead, the goal is to understand how LLMs change the:

- **speed**
- **scale**
- **accessibility**
- and **structure**

of cyber work on both sides.

In practice, LLMs are best understood as **force multipliers embedded in workflows**, not as complete replacements for human expertise.

This week builds directly on Week 11 by shifting from LLM-based operational assistance in NetOps toward the broader cyber dual-use landscape. It also prepares the ground for Week 13, where trustworthy and secure AI for networks becomes the central focus.

The deeper message of this week is this:

> The most important question is often not whether an LLM is powerful.  
> The more important question is how that power is embedded, constrained, verified, and governed inside real cyber workflows.

---

## Learning Objectives

By the end of this lecture, students should be able to:

- explain what it means for LLMs to be dual-use in cybersecurity
- identify common offensive and defensive uses of LLMs in cyber workflows
- describe why LLMs are useful to attackers and why they are also useful to defenders
- explain the limitations of LLM-based offense and defense
- discuss how LLMs can support incident analysis, alert triage, playbook generation, and knowledge retrieval
- identify risks such as hallucination, prompt injection, excessive agency, and unsafe integration
- explain why bounded workflows and human oversight remain essential
- evaluate LLM-based cyber systems using usefulness, groundedness, and safety rather than fluency alone

---

## Lecture Roadmap

This lecture is organized into five main parts:

1. **Dual-use framing**
2. **LLMs in offensive cyber workflows**
3. **LLMs in defensive cyber workflows**
4. **Risks and secure integration**
5. **Evaluation and future directions**

---

## Slide Topics

1. Week 12 title and agenda  
2. Recap of Week 11  
3. What “LLMs as attackers and defenders” means  
4. Why this matters for networking  
5. Offensive use categories  
6. Defensive use categories  
7. Why LLMs are useful to attackers  
8. Why LLMs are useful to defenders  
9. Current threat picture  
10. Official risk framing  
11. Reconnaissance with LLM support  
12. Phishing and impersonation support  
13. Social engineering amplification  
14. Malware and offensive scripting assistance  
15. Attack-path planning assistance  
16. Prompting as offensive workflow design  
17. AI-assisted fraud and cybercrime  
18. Limits of LLM offense  
19. Why LLMs do not replace attacker expertise  
20. Defensive use: security incident analysis  
21. Defensive use: SOC copilot workflows  
22. Defensive use: detection engineering  
23. Defensive use: playbook generation  
24. Defensive use: threat-intel digestion  
25. Defensive use: knowledge retrieval  
26. LLMs for security incident analysis benchmarking  
27. Human-in-the-loop defensive design  
28. Reliability problem on defense  
29. Hallucination in cyber workflows  
30. Prompt injection on defense  
31. Tool-use risks in defense pipelines  
32. OWASP LLM risks relevant here  
33. Excessive agency in cyber tools  
34. Data poisoning and hostile corpora  
35. Model denial of service and cost attacks  
36. Defensive design principles  
37. Verification before trust  
38. Case study: incident triage copilot  
39. Case study: attacker misuse attempts against public LLMs  
40. Evaluation methodology  
41. Emerging direction: agentic cyber offense and defense  
42. Preview of Week 13  
43. Wrap-up and reading assignment  

---

## 1. Dual-Use Framing

The term **dual-use** means that the same technology can support both beneficial and harmful purposes.

This is especially true for LLMs in cybersecurity.

### On the defensive side, LLMs can help with:
- incident summarization
- alert triage
- log explanation
- knowledge retrieval
- detection drafting
- workflow support
- playbook assistance

### On the offensive side, LLMs can help with:
- phishing content generation
- impersonation support
- reconnaissance assistance
- scripting help
- fraud scaling
- attack-planning assistance
- manipulation of human targets

The key point is not that LLMs create cyber offense from nothing. Skilled attackers existed long before LLMs.  
The more important point is that LLMs can change:

- how quickly tasks are performed
- how easily content is drafted
- how accessible certain tactics become
- and how much workflow friction is reduced

So the main effect is often **acceleration and amplification**, not complete replacement of expertise.

---

## 2. Why This Matters for Networking

This topic matters in a networking course because modern networking is deeply connected to cyber operations.

Networks are not only:
- performance systems,
- connectivity systems,
- or control systems.

They are also:
- surveillance surfaces,
- attack paths,
- enforcement points,
- and operational ecosystems where AI assistance is increasingly present.

If LLMs become part of:
- incident response,
- SOC operations,
- detection engineering,
- NetOps copilots,
- or cross-tool security workflows,

then both defenders and attackers are affected.

For example:

- A defender may use an LLM to interpret alerts faster.
- An attacker may use an LLM to draft more persuasive phishing messages.
- A SOC may use an assistant to summarize logs.
- A hostile user may try to manipulate that assistant with poisoned context.
- A team may use an LLM to help generate detections.
- An attacker may use an LLM to rewrite malware scripts or adapt evasion ideas.

So this week is about understanding how LLMs change the operational landscape around networks, not only the models themselves.

---

## 3. Offensive Use Categories

To understand dual use clearly, it helps to separate offensive applications into categories.

### Common offensive-support categories include:

- reconnaissance assistance
- phishing and impersonation support
- social engineering amplification
- malicious scripting assistance
- attack-path planning support
- workflow coordination and drafting
- cybercrime enablement at larger scale

The important point is that LLMs are often useful not because they autonomously “hack systems,” but because they reduce effort in the surrounding workflow.

For example, they can help attackers:
- write faster,
- translate better,
- script more quickly,
- organize steps,
- generate variants,
- and communicate more persuasively.

---

## 4. Defensive Use Categories

Similarly, defensive uses can also be grouped into categories.

### Common defensive-support categories include:

- incident analysis
- alert triage
- detection engineering
- playbook drafting
- threat-intelligence digestion
- knowledge retrieval
- analyst workflow support
- incident reporting and summarization

Again, the value is not that the LLM becomes a complete defender.  
The value is that it can reduce friction in knowledge-heavy and language-heavy cyber workflows.

This symmetry is important:

> Offensive and defensive value often come from similar model capabilities.  
> The difference lies in how those capabilities are embedded, governed, and verified.

---

## 5. Why LLMs Are Useful to Attackers

LLMs are useful to attackers for several reasons.

### 5.1 Speed
Tasks that previously required more time can be completed faster.

### 5.2 Language quality
Attackers can produce more polished text for:
- phishing
- impersonation
- persuasion
- localization
- fraud

### 5.3 Accessibility
Less experienced attackers may gain support for tasks they previously found difficult.

### 5.4 Iteration
Attackers can quickly generate variants, alternatives, and refinements.

### 5.5 Workflow support
LLMs can help structure a sequence of steps or explain tools and concepts.

This does not mean the LLM independently performs all offensive tasks well.  
It means the surrounding workflow may become easier, faster, or more scalable.

---

## 6. Why LLMs Are Useful to Defenders

LLMs are useful to defenders for many of the same structural reasons.

### 6.1 Speed
Defenders also face time pressure and large information loads.

### 6.2 Summarization
Security operations produce huge volumes of:
- alerts
- logs
- tickets
- reports
- threat intel

### 6.3 Retrieval
Important knowledge is often scattered across:
- playbooks
- wikis
- prior incidents
- documentation
- case notes

### 6.4 Explanation
Defenders need help understanding:
- what happened
- what evidence matters
- what a log sequence implies
- what a recommended next step means

### 6.5 Workflow support
Defensive work often requires structured reasoning and handoff across humans and tools.

So the defender value of LLMs comes from the same general capabilities:
- language understanding
- summarization
- retrieval
- drafting
- translation
- orchestration support

This is why the dual-use framing is so important.

---

## 7. Current Threat Picture

The current risk picture around LLMs in cyber should be framed carefully.

On one hand:
- LLMs can lower barriers for certain cyber abuse tasks
- they can scale social engineering
- they can improve fraud quality
- they can accelerate scripting and workflow drafting

On the other hand:
- they do not automatically replace attacker expertise
- they may produce flawed technical output
- they are often unreliable without verification
- strong offensive operations still require real skill, tooling, and domain understanding

So the most accurate view is often:

> LLMs are not universal cyber attackers.  
> They are accelerants and multipliers inside broader offensive workflows.

The same balanced framing is true on defense.

---

## 8. Official Risk Framing

A useful way to think about official or policy-oriented risk framing is that LLM risks in cybersecurity are often described along dimensions such as:

- misuse potential
- amplification of malicious workflows
- lowered barriers to harmful behavior
- unsafe autonomy
- prompt injection and tool abuse
- data leakage
- overtrust by defenders
- lack of verification in operational use

This framing matters because it shifts the focus away from science-fiction narratives and toward realistic workflow risk.

---

## 9. Reconnaissance with LLM Support

One offensive use of LLMs is reconnaissance support.

The model may help with:
- summarizing public information
- organizing findings
- drafting search strategies
- structuring target profiles
- comparing technologies or exposed services
- generating hypotheses for further investigation

Again, the point is not magical automation.  
The point is workflow acceleration.

An LLM may help an attacker process more information faster, especially when much of the input is textual or semi-structured.

---

## 10. Phishing and Impersonation Support

This is one of the clearest areas where LLMs can be useful offensively.

They can help produce:
- more fluent phishing messages
- more targeted impersonation text
- multilingual variants
- stylistically adapted messages
- plausible business-context wording

This matters because phishing and impersonation are language-centered attacks, and LLMs are strong at language production.

For defenders, this means content quality can no longer be assumed to correlate strongly with legitimacy.

---

## 11. Social Engineering Amplification

LLMs can also amplify broader social engineering workflows by helping attackers:

- tailor messaging
- adapt tone to context
- draft role-specific persuasion
- generate conversation branches
- create plausible explanations or urgencies
- sustain interaction quality over multiple turns

This highlights a broader lesson:

> LLMs are especially powerful where the attack is partly a language-and-context problem rather than purely a technical exploit problem.

---

## 12. Malware and Offensive Scripting Assistance

LLMs may assist with:
- explaining code
- drafting scripts
- rewriting logic
- translating one scripting style into another
- generating scaffolding for automation

But this area must be described carefully.

LLMs often make technical mistakes.  
They may produce incomplete, unsafe, or nonfunctional output.  
So they are not reliable autonomous malware authors.

Still, they may reduce friction in parts of offensive scripting workflows, especially for adaptation, explanation, and iteration.

---

## 13. Attack-Path Planning Assistance

Another possible use is helping attackers think through:
- possible next steps
- sequences of actions
- dependencies among steps
- likely requirements
- or decision branches in a campaign

Again, the model may be wrong or shallow, but even imperfect workflow support can be useful if it accelerates planning.

This resembles how LLMs can support troubleshooting on defense: the benefit is often in structuring thinking, not guaranteeing correctness.

---

## 14. Prompting as Offensive Workflow Design

A useful conceptual point for students is that prompting itself can become part of workflow design.

An attacker may iteratively refine prompts to obtain:
- more targeted outputs
- more polished impersonation text
- better structured scripting ideas
- more organized planning assistance

This means the interface between attacker and LLM is not static. It is adaptive and iterative.

This is also why alignment and usage controls matter.

---

## 15. AI-Assisted Fraud and Cybercrime

Beyond traditional “cybersecurity” in a narrow technical sense, LLMs may also assist cybercrime-related workflows such as:

- scam drafting
- impersonation
- fraudulent customer interaction
- fake support or fake escalation messages
- large-scale multilingual abuse content

This is important because networking and cyber defense increasingly intersect with fraud, abuse, and trust operations.

---

## 16. Limits of LLM Offense

Students should be careful not to overstate offensive capability.

LLMs often struggle with:
- precise exploitation detail
- persistent long-horizon planning
- accurate system-specific reasoning
- reliable code correctness
- hidden contextual constraints
- execution realism

So the key lesson is:

> LLM-supported offense is often helpful, but not automatically competent.

The main risk is often not perfect autonomous attack generation.  
The main risk is lowered friction, faster iteration, better persuasion, and increased scalability.

---

## 17. Why LLMs Do Not Replace Attacker Expertise

This is worth stating explicitly.

Real offensive operations still require:
- technical skill
- environment understanding
- tool use
- adaptation to feedback
- operational security
- persistence
- and judgment

LLMs may support parts of that work, but they do not eliminate the need for expertise.

This is important because it helps students keep a realistic view rather than an exaggerated one.

---

## 18. Defensive Use: Security Incident Analysis

On defense, one of the strongest LLM use cases is incident analysis.

A defender may provide:
- alerts
- logs
- asset context
- timeline notes
- prior incident data
- playbook fragments

The LLM can help produce:
- a concise timeline
- likely hypotheses
- evidence summaries
- missing-information requests
- candidate next steps

This is highly valuable because incident analysis is:
- knowledge-heavy
- text-heavy
- and time-sensitive

---

## 19. Defensive Use: SOC Copilot Workflows

A SOC copilot is one of the most natural operational roles for an LLM.

It can help with:
- alert triage
- case summarization
- note drafting
- evidence organization
- retrieval of relevant procedures
- explanation of technical artifacts
- analyst workflow guidance

The important idea is that the LLM supports the analyst rather than replacing the analyst.

This helps preserve accountability and reduce unsafe overtrust.

---

## 20. Defensive Use: Detection Engineering

LLMs can also help analysts and detection engineers by assisting with:

- rule drafting
- query explanation
- translating detection logic across systems
- summarizing telemetry patterns
- converting investigative observations into candidate detections

This is promising because detection engineering often involves language, logic, and translation across tools.

But generated logic must still be:
- reviewed
- tested
- validated
- and grounded in real evidence

---

## 21. Defensive Use: Playbook Generation

LLMs can help draft:
- response steps
- triage playbooks
- structured procedures
- escalation templates
- communication drafts

This is especially useful when:
- human teams are overloaded
- documentation is incomplete
- or procedural consistency is needed

But again, helpful drafting is not the same as trusted authority.

---

## 22. Defensive Use: Threat-Intel Digestion

Threat intelligence is often long, inconsistent, and difficult to absorb quickly.

An LLM can help:
- summarize reports
- extract key indicators
- identify likely implications
- compare threat notes
- map intel to local environment questions

This is a strong example of the model acting as a knowledge compression tool.

---

## 23. Defensive Use: Knowledge Retrieval

This connects directly to Week 11.

A defender may need to retrieve:
- old incidents
- relevant runbooks
- platform documentation
- asset history
- prior escalations
- vendor notes
- policy constraints

An LLM with retrieval can help unify these into a more usable view.

This is often one of the most practically valuable defensive roles.

---

## 24. LLMs for Security Incident Analysis Benchmarking

An important academic and practical question is how to evaluate LLM performance on security incident analysis.

Possible criteria include:
- correctness
- completeness
- groundedness
- evidence linkage
- unsafe suggestion rate
- usefulness to analysts
- abstention quality when evidence is insufficient

This reminds students that evaluation must go beyond fluency.

---

## 25. Human-in-the-Loop Defensive Design

One of the strongest lessons of this week is that defensive LLM systems should usually be designed with humans in the loop.

A safe pattern often looks like:

1. retrieve evidence
2. summarize and structure it
3. propose hypotheses or next steps
4. cite evidence
5. require analyst review
6. only then proceed to action or escalation

This preserves usefulness while limiting unsafe autonomy.

---

## 26. Reliability Problem on Defense

Even when used defensively, LLMs have a reliability problem.

They may:
- hallucinate
- overstate evidence
- miss contradictions
- produce unsafe recommendations
- misread logs
- or sound more confident than the evidence deserves

This is why usefulness and trustworthiness must be separated.

A system may be useful as a drafting or triage assistant while still being unsafe to trust directly.

---

## 27. Hallucination in Cyber Workflows

Hallucination is particularly dangerous in cyber workflows because it may lead to:

- wrong incident conclusions
- wasted investigation effort
- missed threats
- incorrect escalation
- unsafe response steps
- or false confidence

This is why good cyber LLM systems should:
- cite evidence
- distinguish fact from inference
- flag uncertainty
- and avoid fabricating unsupported claims

---

## 28. Prompt Injection on Defense

This connects directly to Weeks 10 and 11.

If a defensive LLM consumes:
- tickets
- logs
- reports
- wiki content
- user-submitted text
- or retrieved documents

then hostile instructions may be embedded there.

A malicious context item may try to:
- suppress relevant evidence
- redirect workflow
- produce unsafe guidance
- or trigger tool misuse

So prompt injection is a very practical defense-side risk.

---

## 29. Tool-Use Risks in Defense Pipelines

If the LLM has access to tools, the risk increases.

Possible dangers include:
- over-permissioned tools
- unsafe action chaining
- execution without adequate review
- accidental sensitive-data exposure
- misuse of ticketing, search, or response systems

So tool-connected defensive assistants must be designed with:
- least privilege
- bounded scope
- approval gates
- and clear auditability

---

## 30. OWASP LLM Risks Relevant Here

Especially relevant categories in this week include:
- prompt injection
- insecure output handling
- data leakage
- excessive agency
- insecure retrieval
- unsafe tool use
- overreliance on generated outputs

These are not abstract model concerns. They are workflow and system-design concerns.

---

## 31. Excessive Agency in Cyber Tools

A central warning of this lecture is against **excessive agency**.

An LLM system becomes far more dangerous when it can:
- act broadly
- call many tools
- trigger changes
- access sensitive data
- or make unreviewed response decisions

This is true whether the system is used by defenders or manipulated by attackers.

So bounded agency matters more than stylistic prompt engineering.

---

## 32. Data Poisoning and Hostile Corpora

If an LLM-based cyber system relies on retrieval or internal corpora, those sources may themselves be manipulated.

Examples:
- poisoned runbooks
- malicious wiki content
- misleading incident notes
- attacker-planted instructions in retrieved documents
- corrupted threat-intel content

This means that safe cyber use of LLMs depends partly on content governance and provenance.

---

## 33. Model Denial of Service and Cost Attacks

Another practical concern is that LLM systems may be targeted through:
- excessive-query abuse
- expensive-context prompts
- repeated low-value usage
- context flooding
- or manipulations that increase cost and latency

This matters especially in operational environments where:
- response time matters
- inference cost matters
- and degraded assistant availability may harm workflows

---

## 34. Defensive Design Principles

The safe use of LLMs in cyber defense depends on a few core design principles.

### Important principles include:
- evidence-linked outputs
- least-privilege tool access
- retrieval filtering
- structured outputs
- approval before action
- explicit uncertainty handling
- provenance awareness
- separation between suggestion and execution

These principles are often more important than raw model quality.

---

## 35. Verification Before Trust

This is one of the strongest practical lessons of the week.

LLM outputs should be treated as:
- candidate reasoning
- draft analysis
- proposed next steps

They should not be treated as inherently trustworthy conclusions.

Verification may include:
- checking evidence
- checking syntax
- checking consistency
- checking policy compliance
- checking operational relevance
- confirming with human analysts

---

## 36. Case Study: Incident Triage Copilot

A useful case study is a copilot for security incident triage.

Possible workflow:
1. ingest alerts, logs, asset context, and a short runbook
2. retrieve relevant prior incident patterns
3. generate a structured output:
   - timeline
   - likely cause
   - supporting evidence
   - confidence
   - recommended next actions
4. require analyst review before escalation or response

This is a good example because it shows both:
- real utility
- and the need for bounded trust

---

## 37. Case Study: Attacker Misuse Attempts Against Public LLMs

Another useful case study is attacker misuse of public LLM systems.

Important themes include:
- attempts to obtain offensive assistance
- iterative prompt refinement
- attempts to bypass safeguards
- the difference between high-level assistance and reliable technical execution
- the practical limits of model misuse under guardrails

This helps students avoid both exaggeration and complacency.

---

## 38. Evaluation Methodology

LLM-based cyber systems should be evaluated on criteria such as:

- usefulness
- groundedness
- correctness
- safety
- evidence linkage
- resistance to hostile context
- tool-use discipline
- abstention quality
- operator usefulness
- cost and latency

This reinforces a recurring course theme:

> Good cyber AI is not defined by eloquence. It is defined by reliability, evidence, safety, and bounded integration.

---

## 39. Emerging Direction: Agentic Cyber Offense and Defense

A future direction is more agentic cyber systems.

That may include:
- multi-step assistants
- bounded planning agents
- tool-using detection copilots
- semi-automated investigative chains
- offensive misuse attempts that rely on multi-step orchestration

But the more agentic the system becomes, the more important:
- governance
- verification
- logging
- bounded authority
- and human oversight become.

So agentic systems are promising, but also much riskier.

---

## Key Themes

### 1. LLMs change the speed and scale of cyber work
LLMs do not eliminate the need for expertise, but they can greatly accelerate drafting, summarization, scripting, translation, and workflow coordination. This matters for both attackers and defenders.

### 2. Offensive and defensive value come from similar capabilities
Language understanding, generation, retrieval, summarization, and tool orchestration are useful in both offensive and defensive settings. The difference lies in how they are embedded into workflows and governed.

### 3. The main danger is often unsafe integration, not only model error
A persuasive but wrong model is already risky. A persuasive model connected to tools, sensitive data, or autonomous actions is far more risky.

### 4. Bounded, evidence-linked workflows are essential
In cybersecurity, LLM outputs should be grounded in artifacts, linked to evidence, and constrained by privilege boundaries and approval steps.

---

## Suggested Reading

### Core topic readings
- selected readings on LLMs in cybersecurity
- readings on LLM-assisted incident analysis
- readings on dual-use AI in cyber offense and defense

### Recommended topic readings
- readings on OWASP LLM security risks
- papers on incident-analysis benchmarking for LLMs
- readings on agentic AI in cybersecurity
- reports on AI-enabled cybercrime and misuse attempts

---

## Suggested Discussion Questions

1. Are LLMs mainly increasing attacker capability, or mainly lowering the barrier to entry?
2. Which defensive cyber tasks are mature enough for LLM support today?
3. Is prompt injection the biggest practical risk in LLM-based cyber defense, or is excessive agency even more dangerous?
4. Should defenders ever trust an LLM-generated response action without explicit verification?

---

## Suggested Lab / Activity

### Week 12 Lab
**Compare LLM use in defensive and misuse-aware cyber workflows**

#### Defensive track
Possible tasks:
- provide the model with an incident bundle such as alerts, logs, asset context, and a short runbook
- ask it to produce a timeline, likely cause, evidence list, and recommended next actions
- require structured output with explicit evidence references
- evaluate groundedness, completeness, and unsafe suggestions

#### Misuse-awareness track
Possible tasks:
- provide benign but messy inputs that include misleading or manipulative instructions
- test whether the model can be diverted by hostile context
- redesign the workflow using retrieval filtering, stronger instructions, structured outputs, and approval steps
- compare behavior before and after hardening

### Week 12 Discussion
Students can discuss one question such as:

**What makes an LLM useful in cyber defense without making it dangerously overtrusted?**

---

## Practical Emphasis

This week should help students build four important habits:

1. **See LLMs as workflow components**  
   They should be treated as parts of larger cyber workflows, not as stand-alone authorities.

2. **Separate usefulness from trustworthiness**  
   A system can be helpful while still being unsafe to trust directly.

3. **Constrain agency carefully**  
   Tool access, action privileges, and execution paths should remain bounded.

4. **Evaluate with evidence and safety in mind**  
   Good outputs should be grounded, verifiable, and aligned with operational constraints.

---

## Summary

Week 12 explores the dual-use reality of LLMs in cybersecurity. It shows how the same capabilities that help defenders summarize incidents, retrieve knowledge, and support triage can also help attackers scale phishing, reconnaissance, and offensive automation.

The main goal is to understand that LLMs change cyber work by increasing:

- **speed**
- **scale**
- **and accessibility**

but that safe use depends on:

- **grounding**
- **bounded agency**
- **verification**
- **and human oversight**

That is the central lesson of this week.

---

[← Previous Week](week11.html) | [Back to Schedule](../schedule.html) | [Next Week →](week13.html)
