# Week 12 — LLMs as Attackers and Defenders

## Overview

This lecture examines the **dual-use nature** of large language models in cybersecurity. The same model family that can help defenders summarize alerts, analyze incidents, retrieve knowledge, and draft detection logic can also help attackers scale phishing, reconnaissance, social engineering, malicious scripting, and offensive workflow automation.

The purpose of this week is not to treat LLMs as magical offensive or defensive agents. Instead, it is to help students understand how LLMs change the **speed, scale, accessibility, and structure** of cyber work on both sides. In practice, LLMs are best understood as force multipliers embedded in larger workflows rather than complete replacements for human expertise.

This week builds on Week 11 by shifting from operational assistance in NetOps to the broader cyber dual-use landscape, and it prepares the ground for Week 13 on trustworthy and secure AI for networks.

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

## Lecture Structure

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

## Suggested Instructor Flow

A possible lecture flow is:

### Part 1: Dual-use framing
Slides 1–10  
Introduce the idea that LLMs are useful to both attackers and defenders and explain why this matters for cyber operations and network security.

### Part 2: Offensive uses
Slides 11–19  
Discuss reconnaissance, phishing, impersonation, social engineering, malicious scripting assistance, attack planning, and the practical limits of LLM-supported offense.

### Part 3: Defensive uses
Slides 20–27  
Explain how LLMs can support security incident analysis, alert triage, detection engineering, playbook generation, knowledge retrieval, and analyst workflows.

### Part 4: Risks and secure design
Slides 28–37  
Cover hallucination, prompt injection, tool-use risks, excessive agency, poisoning, denial of service, defensive design principles, and verification requirements.

### Part 5: Evaluation and future directions
Slides 38–43  
Use case studies to discuss real misuse and real defensive workflows, then introduce evaluation methodology and the future of agentic cyber systems.

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

## References

### Core references
1. Readings on LLMs in cybersecurity  
2. Readings on incident-analysis assistance and SOC copilots  

### Recommended topic areas for supporting readings
- dual-use AI in cyber offense and defense
- prompt injection and LLM application security
- excessive agency in tool-connected LLM systems
- incident-analysis benchmarking
- agentic AI in cybersecurity
- governance of LLM-enabled cyber workflows

---

## Summary

Week 12 explores the dual-use reality of LLMs in cybersecurity. It shows how the same capabilities that help defenders summarize incidents, retrieve knowledge, and support triage can also help attackers scale phishing, reconnaissance, and offensive automation.

The main goal is to help students understand that LLMs change cyber work by increasing **speed, scale, and accessibility**, but that safe use depends on **grounding, bounded agency, verification, and human oversight**.

---

[← Previous Week](week11.html) | [Back to Schedule](../schedule.html) | [Next Week →](week13.html)
