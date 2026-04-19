# Week 10 — Adversarial Machine Learning in Networks

## Overview

This lecture examines what happens when AI systems used in networking and cybersecurity become **targets of attack**. Once machine learning is used for intrusion detection, traffic classification, anomaly detection, malware analysis, routing support, or LLM-assisted operations, the AI pipeline itself becomes part of the attack surface.

The lecture introduces the core ideas of **adversarial machine learning (AML)** and explains how attackers may manipulate inputs, training data, model behavior, or AI-assisted workflows in order to evade detection, degrade performance, trigger hidden behavior, or cause unsafe operational decisions.

This week builds directly on Week 9 and prepares the ground for Weeks 11–13, where LLM-based operations and trustworthy AI become central.

---

## Learning Objectives

By the end of this lecture, students should be able to:

- explain what adversarial machine learning is and why it matters in networking
- distinguish among inference-time and training-time attacks
- describe common attack classes such as evasion, poisoning, backdoors, model extraction, and availability attacks
- explain how adversarial threats appear in IDS, traffic classification, malware detection, graph learning, reinforcement learning, and LLM-based NetOps
- define attacker goals, capabilities, and knowledge assumptions in an AML threat model
- discuss realistic constraints in network-domain adversarial attacks
- describe defensive strategies such as robust training, input validation, bounded deployment, and runtime safeguards
- evaluate AML claims critically, especially with respect to realism, threat-model clarity, and benchmarking quality

---

## Lecture Structure

This lecture is organized into five main parts:

1. **Why adversarial ML matters in networking**
2. **Core attack types and threat models**
3. **Networking-specific adversarial ML**
4. **Defenses and secure deployment**
5. **Evaluation pitfalls and future directions**

---

## Slide Topics

1. Week 10 title and agenda  
2. Recap of Week 9  
3. From attacking networks to attacking models  
4. What is adversarial machine learning?  
5. Why network and security ML is especially vulnerable  
6. Threat-model vocabulary  
7. NIST AML taxonomy overview  
8. Security goals for ML systems  
9. Attack surface in network AI pipelines  
10. Training-time vs inference-time attacks  
11. White-box, gray-box, black-box attacks  
12. Evasion attacks  
13. Poisoning attacks  
14. Backdoor and trojan attacks  
15. Model extraction and inference attacks  
16. Availability attacks  
17. Attack pipeline example: NIDS evasion  
18. Attack pipeline example: traffic-classifier evasion  
19. Attack pipeline example: malware ML evasion  
20. Why adversarial examples work  
21. Transferability of attacks  
22. Constraints in networking AML  
23. Evasion in flow-based models  
24. Poisoning in security datasets  
25. Backdoors in cyber ML  
26. Attacking graph-based network models  
27. Adversarial issues in RL-based networking  
28. Adversarial issues in LLM-assisted NetOps  
29. OWASP LLM risks relevant to networking  
30. Prompt injection in network operations assistants  
31. Defender mindset: hardening the data pipeline  
32. Defender mindset: robust training  
33. Defender mindset: runtime defenses  
34. Defender mindset: secure deployment  
35. Evaluation methodology for AML  
36. Why many AML defenses fail  
37. Explainability and uncertainty in adversarial settings  
38. Benchmarking pitfalls  
39. Case study: AML against NIDS  
40. Case study: attacks on graph and network models  
41. Emerging direction: trustworthy AML evaluation  
42. Preview of Week 11  
43. Wrap-up and reading assignment  

---

## Key Themes

### 1. Once AI is deployed, the model becomes part of the attack surface
AI in networking is not only a tool for defenders. It is also something attackers can manipulate, evade, poison, or misuse.

### 2. Threat models matter
A result in adversarial ML is only meaningful if the attacker’s goals, knowledge, capabilities, and constraints are clearly defined.

### 3. Network-domain attacks must remain realistic
In networking, adversarial perturbations must still respect protocol behavior and operational plausibility. A “successful” attack that breaks the traffic or makes it unrealistic is not very convincing.

### 4. Secure deployment matters as much as robust models
Data validation, retrieval control, least privilege, approval gates, and bounded automation are all part of defending AI systems in practice.

---

## Suggested Instructor Flow

A possible lecture flow is:

### Part 1: Motivation and threat models
Slides 1–11  
Explain why deployed AI systems become attack targets, introduce threat-model vocabulary, and distinguish between training-time and inference-time attacks.

### Part 2: Main adversarial attack types
Slides 12–21  
Cover evasion, poisoning, backdoors, extraction, availability attacks, and why transferability makes adversarial attacks especially dangerous.

### Part 3: Networking-specific adversarial ML
Slides 22–30  
Show how AML appears in flow-based models, IDS, malware ML, graph models, RL systems, and LLM-assisted network operations.

### Part 4: Defenses and secure deployment
Slides 31–34  
Discuss pipeline hardening, robust training, runtime defenses, structured outputs, bounded tools, and secure operational integration.

### Part 5: Evaluation and future directions
Slides 35–43  
Focus on evaluation rigor, weak defenses, uncertainty, benchmarking pitfalls, case studies, and the transition to Week 11 on LLMs for network operations.

---

## Suggested Reading

### Core AML foundations
- introductory readings on adversarial machine learning
- NIST-oriented readings on AML taxonomy and terminology

### Recommended topic readings
- survey papers on adversarial machine learning for network intrusion detection
- readings on adversarial attacks on graph learning systems
- readings on prompt injection and LLM application security
- papers on robust evaluation for cyber and network ML systems

---

## Suggested Discussion Questions

1. Why is adversarial evaluation in networking harder than in image classification?
2. Which is more dangerous in practice: evasion, poisoning, or prompt injection?
3. Should network operators trust any model that has not been evaluated under adaptive attacks?
4. Can an LLM-based NetOps assistant ever be safe without strong tool restrictions and approval gates?

---

## Suggested Lab / Activity

### Week 10 Lab
**Adversarial evaluation of a network AI model**

#### Option A: IDS or traffic classification
Possible tasks:
- train a simple classifier on flow features
- define a realistic threat model
- perturb a limited set of features to test evasion
- check whether the perturbed traffic would still be operationally plausible
- compare the baseline model with one hardened or constrained variant

#### Option B: LLM-assisted NetOps
Possible tasks:
- build a small troubleshooting assistant over logs or configuration snippets
- inject misleading or malicious text into retrieved context
- observe prompt-injection or unsafe-action behavior
- redesign the workflow using safer prompting, structured outputs, and approval steps

### Week 10 Discussion
Students can discuss one question such as:

**What should count as convincing robustness evidence for an AI system used in networking or cyber defense?**

---

## Practical Emphasis

This week should help students build four important habits:

1. **Always ask for the threat model**  
   A robustness claim without a clear attacker model is weak.

2. **Respect domain constraints**  
   In network AML, attacks must remain functional and realistic.

3. **Think beyond the model**  
   Secure AI systems require secure pipelines, secure tool integration, and bounded operational design.

4. **Be skeptical of weak defenses**  
   Many defenses appear strong only because the evaluation is unrealistic or incomplete.

---

## References

### Core references
1. Introductory readings on adversarial machine learning  
2. NIST-oriented readings on AML taxonomy and terminology  

### Recommended topic areas for supporting readings
- adversarial ML for network intrusion detection
- evasion and poisoning in cyber ML
- attacks on graph-based learning systems
- prompt injection and LLM application security
- trustworthy and realistic AML evaluation

---

## Summary

Week 10 introduces adversarial machine learning as a central issue for AI-enabled networking and cybersecurity. It shows that once AI systems are integrated into detection, classification, routing, or operations, they themselves become potential targets of attack.

The main goal is to help students understand that secure AI is not just about model accuracy. It is about **clear threat models, realistic constraints, robust evaluation, pipeline security, and bounded deployment in adversarial environments**.

---

[← Previous Week](week9.html) | [Back to Schedule](../schedule.html) | [Next Week →](week11.html)
