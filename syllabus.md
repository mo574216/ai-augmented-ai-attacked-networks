# AI-Augmented and AI-Attacked Computer Networks

## Course Description

This graduate-level course explores the intersection of artificial intelligence and computer networking from both the **defensive/operational** and **offensive/adversarial** perspectives. The course studies how AI and machine learning can improve network monitoring, traffic analysis, intrusion detection, routing, congestion control, software-defined networking, and network automation. It also examines how AI systems themselves become targets of attack and how generative AI and large language models can be used by both defenders and attackers.

The course is organized around three main themes:

1. **ML for networking**  
   Using machine learning and deep learning for traffic classification, anomaly detection, forecasting, routing, congestion control, and network resource management.

2. **AI for cybersecurity**  
   Applying AI to intrusion detection, DDoS defense, malware detection, and security analytics, while understanding adversarial machine learning and model robustness.

3. **LLMs for network automation and cyber operations**  
   Using large language models for troubleshooting, log analysis, configuration explanation, knowledge retrieval, incident reporting, and bounded operational assistance.

The course combines foundational concepts, current research directions, case studies, and hands-on labs. By the end of the semester, students should be able to critically evaluate AI-enabled network systems and design practical, trustworthy, and secure solutions for modern networking environments.

---

## Learning Outcomes

By the end of this course, students will be able to:

1. Explain the main opportunities and risks of applying AI in computer networks.
2. Identify suitable machine learning paradigms for networking tasks such as classification, anomaly detection, forecasting, and control.
3. Design and evaluate ML/DL pipelines for network traffic analysis and cybersecurity problems.
4. Analyze how reinforcement learning can be used for routing, congestion control, and resource management.
5. Explain the role of software-defined networking in enabling AI-driven network control.
6. Model networking problems using graph-based learning approaches when topology and relationships are central.
7. Compare AI techniques for intrusion detection, malware detection, and DDoS defense.
8. Analyze adversarial threats against network ML systems, including evasion, poisoning, and unsafe automation.
9. Design bounded LLM-assisted workflows for network operations and cybersecurity support.
10. Evaluate AI-enabled network systems not only by accuracy, but also by robustness, safety, explainability, trustworthiness, and operational usefulness.
11. Read and discuss recent research papers in AI for networking and AI for cybersecurity.
12. Build and present a final project that integrates networking knowledge with AI methods in a realistic and technically sound way.

---

## Prerequisites

Students are expected to have prior knowledge of:

- Computer Networks
- Basic Python programming
- Probability and statistics
- Introductory machine learning concepts

Recommended background:

- Network security fundamentals
- Linux command-line usage
- Experience with basic networking tools such as Wireshark, Mininet, or packet/flow analysis tools

---

## Grading Policy

| Component | Weight |
|---|---:|
| Reading summaries / paper discussions | 10% |
| Labs / hands-on assignments | 25% |
| Homework / technical exercises | 15% |
| Midterm exam or take-home assessment | 20% |
| Final project proposal and milestone | 10% |
| Final project report and presentation | 20% |

### Notes on grading
- **Reading summaries / paper discussions** are intended to build research literacy and critical reading skills.
- **Labs / hands-on assignments** will focus on practical skills such as traffic analysis, ML pipelines, anomaly detection, SDN experiments, and LLM-based operational workflows.
- **Homework / technical exercises** may include short design questions, evaluation critiques, and conceptual problem solving.
- **Midterm** will assess conceptual understanding of the first half of the course.
- **Final project** should address a concrete networking or cybersecurity problem using AI methods and must include a discussion of evaluation, limitations, and trust/safety considerations.

---

# Course Schedule

| Week | Topic | Lecture Page |
|---|---|---|
| 1 | Introduction to AI-Augmented and AI-Attacked Computer Networks | [Week 1](lectures/week1.html) |
| 2 | Foundations of Machine Learning for Networking | [Week 2](lectures/week2.html) |
| 3 | Network Telemetry, Data Collection, and Observability | [Week 3](lectures/week3.html) |
| 4 | Traffic Classification and Application Identification | [Week 4](lectures/week4.html) |
| 5 | Deep Learning for Network Analytics | [Week 5](lectures/week5.html) |
| 6 | Reinforcement Learning for Routing and Congestion Control | [Week 6](lectures/week6.html) |
| 7 | AI for SDN and Network Resource Management | [Week 7](lectures/week7.html) |
| 8 | Graph Learning for Networked Systems | [Week 8](lectures/week8.html) |
| 9 | AI for Cybersecurity: IDS, Malware, and DDoS Defense | [Week 9](lectures/week9.html) |
| 10 | Adversarial Machine Learning in Networks | [Week 10](lectures/week10.html) |
| 11 | LLMs for Network Automation and Operations | [Week 11](lectures/week11.html) |
| 12 | LLMs as Attackers and Defenders | [Week 12](lectures/week12.html) |
| 13 | Trustworthy and Secure AI for Networks | [Week 13](lectures/week13.html) |
| 14 | Integration, Case Studies, and Student Presentations | [Week 14](lectures/week14.html) |

---

## References

### Core Textbooks

1. **James F. Kurose, Keith W. Ross**  
   *Computer Networking: A Top-Down Approach*

2. **Christopher M. Bishop**  
   *Pattern Recognition and Machine Learning*

3. **Ian Goodfellow, Yoshua Bengio, Aaron Courville**  
   *Deep Learning*

4. **Richard S. Sutton, Andrew G. Barto**  
   *Reinforcement Learning: An Introduction*

---

### Recommended References

5. Selected survey papers on:
   - AI/ML for networking
   - Deep learning for intrusion detection
   - Encrypted traffic classification
   - AI in SDN and network management
   - Graph learning for communication networks
   - LLMs for network and service management
   - Adversarial machine learning
   - Trustworthy and secure AI

6. Recent research papers from venues such as:
   - IEEE/ACM Transactions on Networking
   - IEEE Internet of Things Journal
   - IEEE Transactions on Network and Service Management
   - Computer Networks
   - Computer Communications
   - Ad Hoc Networks
   - IEEE Communications Surveys & Tutorials
   - Journal of Network and Computer Applications

---

## Software and Tools

Students may use some of the following tools during the semester:

- Python
- Jupyter Notebook
- scikit-learn
- PyTorch or TensorFlow
- Wireshark
- tcpdump
- Mininet
- Ryu / POX
- Open vSwitch
- PyTorch Geometric or DGL
- Simple RAG / LLM toolchains for selected labs

---

## Final Project

Each student or team will complete a final project on a topic related to AI and networking. Possible directions include:

- traffic classification
- intrusion detection
- DDoS detection
- RL-based routing
- SDN optimization
- graph-based anomaly detection
- LLM-assisted troubleshooting
- trustworthy AI evaluation for networked systems

The final project must include:

- clear problem statement
- technical method
- dataset or experimental setup
- evaluation metrics
- limitations
- discussion of robustness, security, or trustworthiness

---

## Academic Integrity

Students must follow university policies regarding academic honesty and proper citation of code, datasets, models, and written materials. Any use of generative AI tools in assignments or projects must be clearly disclosed according to course policy.

---

## Instructor Note

This course emphasizes both **technical depth** and **critical judgment**. Students are expected not only to build AI-based networking solutions, but also to question whether those solutions are realistic, safe, explainable, and operationally trustworthy.
