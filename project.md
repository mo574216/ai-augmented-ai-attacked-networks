# Final Project

## AI-Augmented and AI-Attacked Computer Networks

The final project is a major component of this course.  
Its purpose is to help students apply AI methods to a meaningful problem in computer networking, cybersecurity, or network operations.

The project should combine:

- a clear networking or security problem
- an AI-based method or framework
- a realistic evaluation
- critical discussion of limitations, risks, and trustworthiness

---

## Project Goals

The final project is intended to help students:

- integrate networking knowledge with AI methods
- design an end-to-end technical solution
- evaluate a system beyond simple accuracy
- consider operational realism, security, and robustness
- communicate research and engineering results clearly

---

## Project Format

Projects may be completed:

- individually, or
- in small teams of 2 students

Team projects are expected to have a broader scope than individual projects.

---

## Suitable Project Areas

Projects should be related to one or more themes from the course, such as:

### ML for Networking
- traffic classification
- anomaly detection in network traffic
- QoS or congestion prediction
- routing or path selection support
- network telemetry analytics
- forecasting link utilization or service degradation

### AI for Cybersecurity
- intrusion detection systems
- DDoS detection and mitigation
- malware detection using static or dynamic features
- security alert prioritization
- anomaly detection in enterprise or IoT networks
- graph-based cyber threat detection

### LLMs for Network Operations
- log summarization assistant
- configuration explanation tool
- troubleshooting copilot
- incident report generation assistant
- retrieval-based assistant over runbooks and technical documentation
- safe LLM-based workflow support for NetOps or SecOps

### Trustworthy / Secure AI
- adversarial evaluation of a network ML model
- drift-aware traffic classifier
- confidence-aware anomaly detector
- human-in-the-loop AI workflow for network operations
- secure and bounded LLM pipeline for cyber or network tasks

---

## Project Requirements

Each project must include the following elements:

### 1. Problem Statement
Clearly define:
- the problem being solved
- why it matters in networking or cybersecurity
- the expected users or operational setting

### 2. Technical Method
Describe:
- the AI/ML/DL/LLM method used
- why this method is appropriate
- the system architecture or pipeline

### 3. Data or Experimental Setup
Explain:
- dataset used, or
- simulation/emulation/testbed environment
- source of data
- preprocessing steps
- train/test split or evaluation design

### 4. Evaluation
The project must include meaningful evaluation, such as:
- accuracy, precision, recall, F1
- PR curve, ROC curve
- latency, overhead, inference time
- robustness under drift
- false-positive burden
- groundedness or safety for LLM systems
- comparison with one or more baselines

### 5. Limitations and Critical Discussion
Every project must include discussion of:
- assumptions
- weaknesses
- possible failure modes
- security, adversarial, or operational risks
- trustworthiness considerations

### 6. Final Deliverables
Each team or student must submit:
- project proposal
- progress update
- final report
- final presentation
- code or implementation artifacts, if applicable

---

## Suggested Project Timeline

| Week | Milestone |
|---|---|
| Week 6–8 | Explore topics and form teams |
| Week 9 | Submit project proposal |
| Week 10–11 | Receive feedback and refine scope |
| Week 11 | Progress checkpoint |
| Week 12–13 | Final implementation and evaluation |
| Week 14 | Final presentation and final report submission |

---

## Project Proposal

The proposal should be short but clear.  
It should include:

- project title
- student name(s)
- problem statement
- motivation
- planned method
- dataset / environment
- expected outcome
- initial reference list

### Suggested proposal length
- 1–2 pages

---

## Progress Checkpoint

The progress checkpoint is intended to ensure that the project is moving in a realistic direction.

It should briefly report:

- work completed so far
- current technical design
- preliminary results, if any
- challenges encountered
- plan for the remaining weeks

---

## Final Report

The final report should be written in a technical and professional style.

### Suggested structure
1. Introduction  
2. Problem Definition  
3. Related Background  
4. Methodology  
5. Experimental Setup  
6. Results  
7. Discussion  
8. Limitations and Future Work  
9. Conclusion  
10. References  

### Suggested report length
- Individual project: 6–8 pages
- Team project: 8–12 pages

---

## Final Presentation

During the last week, each student or team will present their project.

### Presentation should include:
- problem and motivation
- dataset or environment
- method and architecture
- main results
- limitations and lessons learned
- future improvements

### Suggested presentation length
- 10–15 minutes presentation
- 3–5 minutes discussion or Q&A

---

## Evaluation Criteria

| Criterion | Weight |
|---|---:|
| Problem definition and motivation | 10% |
| Technical quality of method | 20% |
| Quality of implementation / experimental design | 20% |
| Evaluation and comparison with baselines | 20% |
| Discussion of limitations, risks, and trustworthiness | 10% |
| Report quality | 10% |
| Presentation quality | 10% |

---

## What Makes a Strong Project

A strong project:

- solves a meaningful and well-scoped problem
- uses an appropriate AI method, not just a fashionable one
- includes a realistic experimental design
- compares against a reasonable baseline
- discusses limitations honestly
- connects technical results to networking or security practice
- considers trust, safety, robustness, or operational usefulness

---

## What to Avoid

Projects should avoid:

- overly broad and unrealistic scope
- no baseline comparison
- weak or unclear evaluation
- copying an existing paper without meaningful adaptation
- using AI tools without understanding the underlying workflow
- presenting only accuracy without discussing false alarms, drift, cost, or safety

---

## Example Project Ideas

### Example 1: Flow-Based Traffic Classification
Build a supervised ML or DL pipeline to classify traffic flows into application categories and evaluate generalization across different splits.

### Example 2: DDoS Detection in SDN
Use traffic statistics from an SDN environment to detect DDoS behavior and propose mitigation logic.

### Example 3: RL-Based Routing Strategy
Train and evaluate an RL agent for adaptive path selection in a simulated network.

### Example 4: LLM-Based Troubleshooting Assistant
Create a bounded retrieval-based assistant that answers troubleshooting questions using runbooks, logs, and device documentation.

### Example 5: Graph-Based Network Anomaly Detection
Represent a network as a graph and use a graph-learning model to identify suspicious nodes or communication patterns.

### Example 6: Adversarial Evaluation of an IDS Model
Train an intrusion detection model and test its robustness against adversarial manipulation or dataset drift.

### Example 7: Trustworthy AI for NetOps
Design a network AI workflow with confidence thresholds, human approval, and rollback mechanisms.

---

## Academic Integrity

Students must properly cite:
- papers
- datasets
- software libraries
- models
- code sources
- AI tools used in the project

Any external assistance, including generative AI tools, must be disclosed according to course policy.

---

## Instructor Guidance

Students are encouraged to choose projects that are:

- technically meaningful
- feasible within one semester
- well aligned with the course themes
- interesting enough to support deeper discussion and critical evaluation

In this course, a project is not judged only by whether it “works,” but also by whether it is **well designed, well evaluated, and realistically positioned for network or security use**.
