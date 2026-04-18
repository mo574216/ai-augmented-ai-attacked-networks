# Week 1 — Introduction to AI-Augmented and AI-Attacked Computer Networks

## Overview

This lecture introduces the course and explains why the intersection of artificial intelligence and computer networking has become an important research and engineering area. The lecture builds a common foundation by reviewing essential networking ideas, essential AI ideas, and the growing role of AI in network management, cybersecurity, and automation.

The lecture also introduces the dual perspective of the course:

- **AI-augmented networks**, where AI helps monitor, optimize, defend, and automate networks
- **AI-attacked networks**, where AI is used by attackers or where AI components themselves become attack surfaces

This first week is intended to give students a clear conceptual map of the whole course before moving into technical methods in later weeks.

---

## Learning Objectives

By the end of this lecture, students should be able to:

- explain the difference between AI-augmented and AI-attacked computer networks
- describe why AI is becoming important in networking and cybersecurity
- review the basic architecture and performance concepts of computer networks
- review the basic categories of AI and machine learning relevant to networking
- identify major application areas of AI in networking, security, and operations
- explain why future directions such as LLM-based NetOps, agentic operations, and digital twins matter

---

## Lecture Structure

This lecture is organized into five main parts:

1. **Course framing**
2. **Networking foundations**
3. **AI foundations**
4. **AI applied to networking and security**
5. **Future directions**

---

## Slide Topics

1. Course title and framing  
2. Why AI + networking now?  
3. What is an AI-augmented network?  
4. What is an AI-attacked network?  
5. Course map  
6. Learning outcomes  
7. Assessment overview  
8. Prerequisites refresh  
9. What is a computer network?  
10. Internet architecture at a glance  
11. Layered architecture  
12. TCP/IP stack review  
13. Network performance basics  
14. Routing and forwarding  
15. Traffic, flows, and sessions  
16. Observability in networks  
17. Traditional network management  
18. Limits of manual and rule-based operations  
19. What is AI?  
20. What is machine learning?  
21. Main ML paradigms  
22. Deep learning in one slide  
23. LLMs in one slide  
24. AI workflow for networking  
25. Types of network data for AI  
26. Example task 1: traffic classification  
27. Example task 2: anomaly detection  
28. Example task 3: intrusion and DDoS detection  
29. Example task 4: routing and traffic engineering  
30. Example task 5: log summarization and troubleshooting  
31. Why ML works well in networking  
32. Why ML is hard in networking  
33. Threat model: AI attacking networks  
34. Threat model: attacking AI in networks  
35. Human-in-the-loop principle  
36. Safety and governance in AI-driven NetOps  
37. From SDN to intent-based and AI-driven operations  
38. LLMs for network and service management  
39. AI-based network management agents  
40. Agentic autonomous networks  
41. Network digital twins plus AI  
42. Open research questions  
43. Week 1 wrap-up and reading assignment  

---

## Key Themes

### 1. Networking is becoming too complex for purely manual control
Modern networks generate large volumes of telemetry and involve complex interactions across devices, services, applications, and users. This makes AI increasingly attractive for monitoring, prediction, optimization, and automation.

### 2. AI in networking is both an opportunity and a risk
AI can improve network operations, traffic engineering, anomaly detection, and incident response. At the same time, AI systems can be attacked, misled, or used by adversaries.

### 3. The course is not only about models
This course is not limited to machine learning algorithms. It is also about telemetry, control loops, cybersecurity, LLM-assisted operations, adversarial robustness, and trustworthy deployment.

### 4. Future networking is moving toward constrained autonomy
Emerging directions suggest that the future of networking may involve AI assistants, bounded agents, digital twins, and more autonomous workflows. However, this autonomy must be carefully constrained and verified.

---

## Suggested Instructor Flow

A possible lecture flow is:

### Part 1: Course framing
Slides 1–8  
Introduce the course, explain motivation, define expectations, and describe the overall roadmap.

### Part 2: Networking foundations
Slides 9–18  
Refresh core networking concepts such as the TCP/IP stack, performance metrics, routing, observability, and network management.

### Part 3: AI foundations
Slides 19–24  
Introduce AI, machine learning, deep learning, and LLMs at a high level.

### Part 4: AI in networking and cybersecurity
Slides 25–36  
Show concrete examples of traffic classification, anomaly detection, intrusion detection, routing, troubleshooting, and human-in-the-loop operation.

### Part 5: Future directions
Slides 37–43  
Introduce SDN, LLM-based NetOps, network management agents, agentic operations, digital twins, and open research questions.

---

## Suggested Reading

### Networking foundations
- James F. Kurose and Keith W. Ross, *Computer Networking: A Top-Down Approach*

### AI and deep learning foundations
- Ian Goodfellow, Yoshua Bengio, and Aaron Courville, *Deep Learning*

### LLMs and future network management
- Recent survey papers on LLMs for communication, network, and service management
- Selected architecture-oriented readings on AI-based network management agents
- Selected readings on agentic and digital-twin-based network operations

---

## Suggested Discussion Questions

1. Which networking tasks are most suitable for AI, and which should remain deterministic?
2. What is more dangerous in practice: AI attacking networks, or unsafe AI controlling networks?
3. Should LLMs in network operations remain advisory only?
4. What kinds of telemetry should an AI-enabled network observe?

---

## Suggested Lab / Activity

### Week 1 Lab
**Environment setup and course toolchain**

Possible tasks:
- install Python and required packages
- prepare Jupyter Notebook environment
- verify packet capture tools such as Wireshark or tcpdump
- test Mininet or other lightweight network emulation tools
- verify basic ML libraries

### Week 1 Discussion
Students can discuss one question such as:

**Where should AI be trusted in networking, and where should it not be trusted yet?**

---

## References

### Core references
1. James F. Kurose and Keith W. Ross, *Computer Networking: A Top-Down Approach*  
2. Ian Goodfellow, Yoshua Bengio, and Aaron Courville, *Deep Learning*  

### Recommended topic areas for supporting readings
- AI and ML for networking
- LLMs for network automation
- AI in network and service management
- AI-based network management agents
- digital twins for network operations
- trustworthy AI in operational systems

---

## Summary

Week 1 establishes the conceptual foundation of the course. It explains why AI and networking now need to be studied together, introduces the dual-use nature of AI in networking and cybersecurity, and prepares students for later weeks on ML, deep learning, RL, SDN, graph learning, cybersecurity, LLMs, adversarial ML, and trustworthy AI.

The main goal is not to teach details yet, but to build a strong and shared mental model for everything that follows.

---

[Back to Schedule](../schedule.html) | [Next Week →](week2.html)
