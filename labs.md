# Labs

## AI-Augmented and AI-Attacked Computer Networks

This page describes the hands-on lab component of the course.

The labs are designed to help students move from theory to practice.  
They focus on building, testing, and evaluating AI-enabled networking and cybersecurity workflows.

The labs are not intended to be only coding exercises.  
They are also intended to help students develop good judgment about:

- data quality
- model selection
- evaluation design
- operational realism
- security and robustness
- trustworthiness of AI-enabled systems

---

## Lab Goals

By completing the labs, students should be able to:

- work with networking and security datasets
- build simple ML and DL pipelines for network tasks
- use simulation or emulation tools where appropriate
- evaluate AI-based networking methods critically
- understand the gap between benchmark performance and real deployment
- design safer and more trustworthy AI workflows for operations and security

---

## Lab Format

Depending on the week and topic, labs may include:

- guided coding exercises
- small experiments
- short technical reports
- paper-based critique tasks with implementation
- mini design tasks
- tool-based exploration in simulation or emulation environments

Some labs may be completed individually, while some may be done in pairs or small teams.

---

## Suggested Software and Tools

Students may use some of the following tools during the semester:

### Networking / Data Collection
- Wireshark
- tcpdump
- Mininet
- Open vSwitch
- Ryu or POX
- iperf

### AI / Data Science
- Python
- Jupyter Notebook
- NumPy
- pandas
- matplotlib
- scikit-learn
- PyTorch or TensorFlow

### Graph Learning
- PyTorch Geometric
- DGL
- NetworkX

### LLM / Retrieval Workflows
- Python-based RAG pipelines
- vector database or lightweight retrieval tools
- API wrappers for LLM experimentation
- structured-output and prompt templates

---

## Weekly Lab Plan

| Week | Lab Topic | Main Goal |
|---|---|---|
| 1 | Environment setup and course toolchain | Prepare the technical environment for later labs |
| 2 | First ML pipeline for networking | Build a simple supervised learning pipeline on network data |
| 3 | Telemetry and observability pipeline | Collect, inspect, and analyze basic telemetry signals |
| 4 | Flow-based traffic classification | Train and evaluate traffic classification models |
| 5 | Deep learning for traffic or anomaly detection | Compare deep models with classical baselines |
| 6 | RL for routing or congestion control | Explore sequential decision-making in a network setting |
| 7 | AI-assisted SDN experiment | Use telemetry and controller logic to influence network behavior |
| 8 | Graph-based network learning | Model a networking problem using graph structure |
| 9 | AI for cybersecurity analytics | Build a detection workflow for IDS, DDoS, or malware-related data |
| 10 | Adversarial evaluation of a network AI model | Test robustness under manipulation or hostile input |
| 11 | Bounded LLM-based NetOps copilot | Build a safe retrieval-assisted operational assistant |
| 12 | LLM dual-use evaluation | Compare useful and unsafe behaviors in cyber workflows |
| 13 | Trustworthiness review of an AI workflow | Evaluate safety, drift, confidence, and deployment readiness |
| 14 | Final project integration / presentation support | Final refinement, demonstration, or project review |

---

## Detailed Lab Descriptions

---

### Week 1 — Environment Setup and Course Toolchain

**Goal:**  
Prepare the working environment for the semester.

**Tasks may include:**
- installing Python and required packages
- preparing Jupyter Notebook environment
- testing packet capture tools
- testing Mininet or a lightweight network emulation setup
- verifying access to ML libraries

**Expected outcome:**  
Students should leave with a working technical environment for later labs.

---

### Week 2 — First ML Pipeline for Networking

**Goal:**  
Build a simple supervised ML workflow using network-related data.

**Tasks may include:**
- loading a small dataset
- exploring features
- splitting data into training, validation, and test sets
- training one or two simple models
- evaluating using confusion matrix, precision, recall, and F1

**Expected outcome:**  
Students understand the basic structure of an ML workflow for networking.

---

### Week 3 — Telemetry and Observability Pipeline

**Goal:**  
Understand the role of data collection and signal quality in network intelligence.

**Tasks may include:**
- collecting packets or logs
- converting pcap to flow summaries
- visualizing simple metrics
- comparing packet-level and flow-level views
- identifying one anomaly or incident pattern

**Expected outcome:**  
Students understand that AI quality depends on telemetry quality.

---

### Week 4 — Flow-Based Traffic Classification

**Goal:**  
Train and evaluate a practical traffic classifier.

**Tasks may include:**
- using flow-based features
- training classical ML models
- comparing different feature subsets
- testing a more realistic split such as time-based or host-based split
- discussing encrypted-traffic limitations

**Expected outcome:**  
Students learn how traffic classification is built and why evaluation design matters.

---

### Week 5 — Deep Learning for Traffic or Anomaly Detection

**Goal:**  
Compare deep learning with simpler baselines.

**Tasks may include:**
- training a simple MLP, CNN, LSTM, or autoencoder
- comparing with a classical baseline
- examining training curves
- discussing overfitting and deployment overhead
- analyzing whether the deep model is really justified

**Expected outcome:**  
Students understand when deep learning helps and when it may not be worth the cost.

---

### Week 6 — RL for Routing or Congestion Control

**Goal:**  
Explore reinforcement learning in a networking setting.

**Tasks may include:**
- defining state, action, and reward
- running a simple routing or control environment
- comparing an RL policy with a heuristic baseline
- evaluating throughput, delay, fairness, or packet loss
- discussing safety and generalization issues

**Expected outcome:**  
Students understand RL formulation in network control tasks.

---

### Week 7 — AI-Assisted SDN Experiment

**Goal:**  
Connect telemetry, AI-based analysis, and programmable control.

**Tasks may include:**
- building a small Mininet topology
- collecting switch statistics
- training a model for congestion prediction, flow classification, or anomaly detection
- using controller logic to apply a policy action
- comparing against a static control policy

**Expected outcome:**  
Students see how AI can become an operational decision-support layer in SDN.

---

### Week 8 — Graph-Based Network Learning

**Goal:**  
Use graph structure to model a networking problem.

**Tasks may include:**
- constructing a graph from topology or communication data
- defining node and edge features
- applying a simple graph model
- comparing graph-based and non-graph baselines
- discussing generalization across graph structures

**Expected outcome:**  
Students understand when graph-based learning is appropriate.

---

### Week 9 — AI for Cybersecurity Analytics

**Goal:**  
Apply AI methods to a cybersecurity problem.

**Possible directions:**
- intrusion detection
- DDoS detection
- malware-related feature classification
- anomaly detection in traffic or logs

**Tasks may include:**
- training at least one baseline model
- evaluating precision, recall, F1, or PR curve
- analyzing false positives
- discussing operational usefulness and limitations

**Expected outcome:**  
Students understand the practical difficulty of AI-based cyber defense.

---

### Week 10 — Adversarial Evaluation of a Network AI Model

**Goal:**  
Test robustness of a previously built model.

**Tasks may include:**
- defining a threat model
- perturbing selected features
- testing evasion or robustness limits
- evaluating model degradation
- discussing realistic vs unrealistic attacks

**Expected outcome:**  
Students learn that network AI models must be evaluated under hostile conditions.

---

### Week 11 — Bounded LLM-Based NetOps Copilot

**Goal:**  
Build a retrieval-assisted assistant for a NetOps-style task.

**Tasks may include:**
- creating a small knowledge base from runbooks, configs, or notes
- implementing a simple retrieval pipeline
- asking the model to summarize logs or explain configuration
- requiring structured output
- evaluating correctness, evidence use, and safety

**Expected outcome:**  
Students understand how LLMs can help operations when properly bounded.

---

### Week 12 — LLM Dual-Use Evaluation

**Goal:**  
Examine both useful and risky behavior in LLM-based cyber workflows.

**Tasks may include:**
- comparing a benign defensive task with a misuse-oriented prompt set
- testing the effect of hostile context
- applying safer prompt and workflow constraints
- discussing governance and safe deployment boundaries

**Expected outcome:**  
Students understand the dual-use character of LLMs in cyber contexts.

---

### Week 13 — Trustworthiness Review of an AI Workflow

**Goal:**  
Evaluate whether an AI system is ready for real operational use.

**Tasks may include:**
- analyzing confidence and calibration
- identifying drift risks
- assessing false-action or unsafe-suggestion risk
- designing fallback or human-approval mechanisms
- writing a short trustworthiness assessment

**Expected outcome:**  
Students move beyond accuracy and think in terms of deployment readiness.

---

### Week 14 — Final Project Integration / Presentation Support

**Goal:**  
Use the lab time to finalize, test, debug, or present project work.

**Tasks may include:**
- system demonstration
- experimental validation
- final result comparison
- project troubleshooting
- presentation rehearsal

**Expected outcome:**  
Students prepare a technically coherent final project deliverable.

---

## Lab Deliverables

Depending on the lab, deliverables may include:

- source code
- notebook
- experiment summary
- short reflection
- report with plots/tables
- discussion of errors and limitations

A lab submission should usually include:

1. **what was done**
2. **how it was implemented**
3. **what results were obtained**
4. **what limitations or risks were observed**

---

## Suggested Evaluation Criteria for Labs

| Criterion | Weight |
|---|---:|
| Technical completion | 30% |
| Correctness and clarity | 20% |
| Quality of evaluation | 20% |
| Discussion of limitations | 15% |
| Code / notebook organization | 15% |

---

## Expectations for Lab Reports

A short lab report or notebook summary should typically include:

- objective
- dataset or environment
- method
- results
- interpretation
- limitations

Students are encouraged to include figures, tables, and short comparisons whenever useful.

---

## Good Practices in Labs

Students are encouraged to:

- use clear train/test separation
- compare against at least one baseline
- report more than one metric
- avoid overstating weak results
- discuss operational realism
- note any trust, safety, or adversarial concerns

---

## What to Avoid

Labs should avoid:

- reporting only accuracy
- ignoring class imbalance
- using unclear evaluation splits
- presenting code without analysis
- treating LLM output as correct without verification
- claiming robustness without testing it

---

## Relationship Between Labs and Final Project

The labs are designed to help students prepare for the final project.

Students may:
- extend a lab idea into a final project
- reuse technical components from earlier labs
- build on a lab but improve the evaluation and scope

However, the final project should go beyond simple lab repetition and include deeper design and analysis.

---

## Academic Integrity

Students must properly cite:
- datasets
- code libraries
- external code sources
- papers
- generative AI tools used during development

Any external assistance must be disclosed according to course policy.

---

## Final Note

The purpose of the labs is not only to “make something run.”  
The real goal is to help students build technically sound, critically evaluated, and operationally meaningful AI-enabled networking systems.
