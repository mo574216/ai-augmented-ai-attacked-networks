---
title: Week 2 - Foundations of Machine Learning for Networking
nav_order: 2
---

# Week 2: Foundations of Machine Learning for Networking

## Overview

In Week 1, we established the motivation for **AI-augmented** and **AI-attacked** computer networks. We saw that modern networks are no longer static infrastructures. They are dynamic, data-rich, and increasingly programmable systems that generate massive streams of telemetry and require fast, intelligent decision-making.

This week, we build the conceptual foundation that allows us to use machine learning in networking in a principled way.

The goal of this week is **not** to turn network engineers into general-purpose machine learning researchers overnight. Rather, the goal is to develop the right way of thinking:

- What kind of networking problems are suitable for machine learning?
- What kind of data do networks produce?
- How do we convert networking behavior into features and labels?
- How do we evaluate whether an ML model is actually useful in an operational network?
- What are the limits, risks, and common mistakes of “applying ML” to networking problems?

By the end of this week, students should understand the major machine learning paradigms used in networking, the structure of ML workflows for networked systems, and the fundamental differences between building a model that looks good in a notebook and building one that is actually useful in a real network.

---

## Learning Objectives

By the end of this week, students should be able to:

1. Explain the difference between supervised, unsupervised, semi-supervised, and reinforcement learning.
2. Map common networking problems to appropriate machine learning formulations.
3. Distinguish between raw network data, features, labels, and targets.
4. Understand the end-to-end ML pipeline for networking applications.
5. Describe key evaluation metrics and explain when accuracy alone is misleading.
6. Identify common challenges such as class imbalance, concept drift, noisy labels, and overfitting.
7. Reason about the operational constraints of ML in networking, including latency, scalability, interpretability, and robustness.

---

## 1. Why Machine Learning in Networking?

Classical networking has historically relied on:

- protocol design,
- rule-based logic,
- mathematical optimization,
- queueing theory,
- control theory,
- and heuristics designed by experts.

These approaches remain extremely important. In fact, many networking problems should still be solved with them. Machine learning becomes attractive when the network environment is:

- highly dynamic,
- too complex for precise analytical modeling,
- data-rich,
- partially observable,
- or requires fast adaptation under uncertainty.

### Examples of networking tasks where ML may help

- **Traffic classification** when port numbers are unreliable or encrypted traffic hides application details.
- **Intrusion detection** where attack patterns evolve and cannot be captured by fixed rules alone.
- **Congestion prediction** in highly variable environments.
- **Routing or scheduling decisions** in complex wireless or edge systems.
- **Resource allocation** in cloud, edge, or software-defined networks.
- **Failure prediction** from logs and telemetry.
- **Anomaly detection** in enterprise or ISP networks.

### Important caution

Machine learning is **not** magic. It is not automatically better than traditional methods.

A good networking researcher must always ask:

> Is this really a learning problem, or is it better solved by rules, algorithms, or optimization?

For example:

- If the decision rule is already known and stable, ML may be unnecessary.
- If data is scarce or labels are unreliable, ML may perform poorly.
- If interpretability and predictability are critical, a simpler model may be preferable.

So the correct mindset is not “use AI everywhere,” but rather:

> Use ML when the structure of the problem, the availability of data, and the operational goals justify it.

---

## 2. What Makes Networking Data Special?

Networking data is very different from standard image or text datasets.

In image classification, we often assume:
- a relatively fixed dataset,
- stable labels,
- and independent examples.

In networking, we often face:
- streaming data,
- time dependence,
- multi-scale behavior,
- highly imbalanced events,
- changing traffic patterns,
- adversarial behaviors,
- and non-stationary environments.

### Common sources of networking data

- Packet headers
- Flow records (e.g., NetFlow, IPFIX)
- Routing updates
- Switch counters
- SNMP statistics
- Logs from firewalls, IDS, routers, controllers, and applications
- TCP metrics (RTT, retransmissions, window sizes)
- Wireless channel indicators (RSSI, SINR, CQI)
- Queue lengths and link utilizations
- Topology state
- User mobility information
- Security alerts and incident records

### Why this matters

A model trained on one network may fail in another because:

- hardware differs,
- protocols differ,
- user behavior differs,
- traffic mix differs,
- time of day matters,
- attacks evolve,
- or the network simply changes after deployment.

This means that **generalization** is much harder in networking than in many textbook ML settings.

---

## 3. The Main Machine Learning Paradigms

## 3.1 Supervised Learning

In supervised learning, we have input-output pairs:

- **input**: a representation of network behavior
- **output**: the correct target or label

The model learns a mapping from inputs to outputs.

### Networking examples

- Predict whether a flow is benign or malicious.
- Classify traffic into application categories.
- Predict future link utilization.
- Estimate QoS degradation.
- Predict whether a node will fail.

### Typical tasks

- **Classification**: output is a category  
  Example: attack vs. normal, video vs. web vs. VoIP
- **Regression**: output is a number  
  Example: predict latency, throughput, or packet loss

### Example

Suppose each flow is represented by features such as:

- average packet size,
- flow duration,
- number of packets,
- inter-arrival time statistics,
- upstream/downstream byte ratio.

If the label is:
- `0 = benign`
- `1 = malicious`

then the problem is supervised classification.

### Strengths

- Often produces strong performance when good labeled data is available.
- Easy to evaluate quantitatively.
- Many mature algorithms exist.

### Weaknesses

- Requires labeled data, which is expensive and often noisy.
- Labels may become obsolete as traffic patterns evolve.
- Models may overfit to specific environments or datasets.

---

## 3.2 Unsupervised Learning

In unsupervised learning, we have inputs but no labels. The goal is to discover structure in the data.

### Networking examples

- Detect unknown anomalies in traffic patterns.
- Group similar flows into clusters.
- Learn latent structure in user behavior.
- Reduce high-dimensional telemetry into a lower-dimensional representation.

### Common tasks

- **Clustering**: group similar items together
- **Dimensionality reduction**: compress feature space while preserving useful structure
- **Density estimation / anomaly detection**: identify unusual behavior

### Example

A network operator may not know in advance what an attack looks like. Instead of training on labeled attacks, the operator may model “normal” traffic and then flag deviations.

### Strengths

- Useful when labels do not exist.
- Can reveal hidden patterns.
- Helps exploratory analysis.

### Weaknesses

- Output can be hard to interpret.
- “Clusters” are not guaranteed to correspond to meaningful operational categories.
- Evaluation is harder than in supervised learning.

---

## 3.3 Semi-Supervised Learning

Semi-supervised learning lies between supervised and unsupervised learning.

We have:
- a small amount of labeled data,
- a large amount of unlabeled data.

This is very realistic in networking.

### Why it matters in networking

Obtaining labels for all flows, incidents, or performance events is expensive. Experts may only label a small subset. Semi-supervised methods try to exploit the larger pool of unlabeled data.

### Example

A SOC team labels a few thousand flows as malicious or benign, while millions of other flows remain unlabeled. A semi-supervised approach may learn from both.

---

## 3.4 Reinforcement Learning

In reinforcement learning (RL), an agent interacts with an environment and learns by trial and error.

The agent:
- observes a **state**,
- takes an **action**,
- receives a **reward**,
- and tries to maximize long-term cumulative reward.

### Networking examples

- Congestion control
- Routing in dynamic networks
- Channel allocation in wireless networks
- Task offloading in edge computing
- Adaptive caching
- Scheduling and resource allocation

### Example

An RL agent may observe:
- queue lengths,
- delay,
- link utilization,
- and packet loss,

and then choose:
- a routing path,
- a transmission rate,
- or a scheduling priority.

The reward may encourage:
- high throughput,
- low delay,
- fairness,
- and low packet loss.

### Why RL is interesting in networking

Networking is naturally sequential and dynamic. A decision now affects future states. That makes RL a natural framework for many control problems.

### Why RL is difficult

- Real networks are noisy and partially observable.
- Exploration may be unsafe.
- Rewards are difficult to design well.
- Training can be unstable.
- Performance in simulation may not transfer to real networks.

---

## 4. Mapping Networking Problems to ML Formulations

A key skill is translating a networking problem into the language of machine learning.

Let us look at several examples.

### Example 1: DDoS Detection

**Networking question:** Is this traffic pattern part of a DDoS attack?

**ML formulation:** Supervised classification

- **Input:** traffic statistics over a time window
- **Output:** attack / non-attack

### Example 2: Traffic Matrix Forecasting

**Networking question:** What will the next time-step demand be between source-destination pairs?

**ML formulation:** Supervised regression or time-series prediction

- **Input:** historical traffic matrices
- **Output:** future traffic matrix values

### Example 3: Unknown Anomaly Discovery

**Networking question:** Is this behavior unusual, even if we do not know the exact attack type?

**ML formulation:** Unsupervised anomaly detection

- **Input:** unlabeled traffic/telemetry
- **Output:** anomaly score or cluster structure

### Example 4: Dynamic Routing in Wireless Mesh

**Networking question:** Which next hop should be selected under changing conditions?

**ML formulation:** Reinforcement learning

- **State:** channel quality, queue status, interference, mobility indicators
- **Action:** routing or forwarding decision
- **Reward:** throughput, delay, delivery ratio, energy efficiency

### Example 5: Flow Type Discovery in Encrypted Traffic

**Networking question:** Can we infer application classes without seeing payload?

**ML formulation:** Supervised or semi-supervised classification

- **Input:** flow metadata, timing, directionality, burst patterns
- **Output:** application class

---

## 5. The ML Pipeline for Networking

A networking ML system is not just a model. It is a pipeline.

## 5.1 Problem Definition

Everything starts here.

A vague problem statement like “use AI to improve the network” is not useful.

A good problem definition specifies:

- what decision is being made,
- what data is available at decision time,
- what the output should be,
- what the operational objective is,
- and what constraints matter.

### Poor statement
“Use ML for routing.”

### Better statement
“Predict short-term congestion on backbone links every 30 seconds using telemetry data, in order to support proactive traffic engineering.”

---

## 5.2 Data Collection

The next step is to obtain relevant data.

In networking, data collection is often expensive and error-prone. Sampling, packet loss in telemetry pipelines, clock mismatch, encryption, and device heterogeneity all matter.

Questions to ask:

- What is the observation unit? Packet, flow, host, session, time window, path?
- How frequently is data collected?
- Is the data complete or sampled?
- Are timestamps synchronized?
- Is privacy an issue?
- Are labels trustworthy?

---

## 5.3 Feature Engineering

Raw networking data often cannot be fed directly into classical ML models. We usually derive features.

### Packet-level features
- packet size
- TTL
- protocol type
- TCP flags

### Flow-level features
- flow duration
- total bytes
- total packets
- average packet size
- burstiness
- inter-arrival statistics
- forward/backward ratio

### Time-window features
- packets per second
- bytes per second
- entropy of destination IPs
- number of distinct ports contacted
- queue occupancy changes
- retransmission rate

### Topology-aware features
- node degree
- path length
- centrality
- neighborhood load
- edge capacities

### Important point

Good feature engineering requires networking knowledge.

Two researchers can train the same model on the same algorithm class, but the one with better networking-aware feature design often wins.

---

## 5.4 Labeling

In supervised learning, labels are crucial.

But in networking, labels are often:
- incomplete,
- expensive,
- noisy,
- outdated,
- or biased.

### Examples of labeling difficulty

- Security logs may contain false positives.
- Traffic may be labeled by application port even though ports are misleading.
- Human analysts may disagree on incident categories.
- Performance degradation may have multiple root causes.

This means that “ground truth” in networking is often imperfect.

Students must understand this deeply:  
**bad labels can easily produce misleadingly good-looking results.**

---

## 5.5 Model Selection

Different models have different strengths.

### Classical ML models
- Logistic Regression
- Decision Trees
- Random Forests
- SVM
- k-NN
- Gradient Boosting

### Deep learning models
- MLPs
- CNNs
- RNNs / LSTMs / GRUs
- Transformers
- Graph Neural Networks

### RL methods
- Q-learning
- Deep Q Networks
- Policy Gradient
- Actor-Critic methods

### Important principle

Do not start with the most complex model.

In many networking tasks, a simple baseline:
- is easier to interpret,
- is easier to deploy,
- trains faster,
- and may perform surprisingly well.

A mature research workflow often starts with:
1. heuristic baseline,
2. simple ML baseline,
3. more advanced model only if justified.

---

## 5.6 Training and Validation

Data must usually be divided into:
- training set,
- validation set,
- test set.

But in networking, random splitting can be dangerous.

### Why?

If samples from the same flow, host, or time period appear in both training and test sets, the test result may be overly optimistic.

### Better evaluation strategies

- time-based split,
- topology-based split,
- device-based split,
- scenario-based split,
- cross-environment testing.

These are often more realistic than random shuffling.

---

## 5.7 Deployment and Monitoring

A model is only useful if it operates well after deployment.

Deployment questions include:

- Can inference run in real time?
- Is the model light enough for edge devices?
- What happens when traffic changes?
- How often must the model be retrained?
- Can operators understand its predictions?
- Can attackers manipulate its behavior?

This is why operational ML in networking is much harder than producing good offline test accuracy.

---

## 6. Core Evaluation Metrics

A central lesson of this week is that **accuracy is not enough**.

## 6.1 Classification Metrics

### Accuracy
The fraction of correct predictions.

This can be misleading in imbalanced settings.

Example:  
If 99.5% of traffic is benign, a model that predicts “benign” for everything gets 99.5% accuracy while being useless for attack detection.

### Precision
Among items predicted as positive, how many are truly positive?

Useful when false alarms are costly.

### Recall
Among true positives, how many did we detect?

Useful when missing attacks is costly.

### F1-score
Harmonic mean of precision and recall.

Useful when balancing missed detections and false alarms.

### ROC-AUC / PR-AUC
Useful for threshold-based evaluation, especially under class imbalance.

---

## 6.2 Regression Metrics

For numeric prediction tasks:

- Mean Absolute Error (MAE)
- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)
- Mean Absolute Percentage Error (MAPE), when appropriate

In networking, prediction errors should also be interpreted operationally.

For example, an average error of 5 ms may be acceptable for one application and disastrous for another.

---

## 6.3 System-Level Metrics

In networking, model metrics alone are insufficient. We also care about system impact.

Examples:

- throughput improvement,
- delay reduction,
- packet loss reduction,
- fairness,
- energy savings,
- controller overhead,
- memory usage,
- inference latency,
- retraining cost.

A networking ML paper that reports only ML metrics but ignores system impact is incomplete.

---

## 7. Common Pitfalls in ML for Networking

## 7.1 Class Imbalance

Many important networking events are rare:

- intrusions,
- failures,
- congestion collapses,
- routing anomalies.

This means models may learn to ignore rare but important events.

Possible responses:
- resampling,
- cost-sensitive learning,
- anomaly detection,
- threshold tuning,
- better metrics.

---

## 7.2 Overfitting

A model may memorize the dataset rather than learn general principles.

This is especially dangerous when:
- datasets are small,
- features leak label information,
- or train/test separation is unrealistic.

---

## 7.3 Concept Drift

Networking environments change over time.

Examples:
- user behavior changes,
- new applications appear,
- routing policies evolve,
- attackers adapt,
- encryption patterns change.

A model that worked six months ago may fail now.

This is called **concept drift**.

---

## 7.4 Dataset Bias

A public dataset may not represent modern real-world traffic.

For example:
- old intrusion datasets may contain artifacts,
- synthetic traffic may be too clean,
- lab environments may not reflect real deployments.

This is why dataset choice and data provenance matter greatly.

---

## 7.5 Data Leakage

A very common mistake.

A model appears excellent because information that should be unavailable at prediction time accidentally leaks into the features.

Examples:
- using post-event counters to predict the event,
- mixing future time windows into current prediction,
- using labels derived from the same heuristic used in feature design.

---

## 7.6 Ignoring Operational Constraints

A model may be accurate but unusable.

For example:
- it may require too much CPU,
- too much memory,
- too much telemetry,
- or too much delay for real-time deployment.

A routing decision that takes 2 seconds may be useless in a fast-changing wireless environment.

---

## 7.7 Ignoring Adversaries

In networking, especially security settings, the environment may be adversarial.

Attackers may:
- evade classifiers,
- poison training data,
- mimic benign patterns,
- exploit blind spots.

So a model should not be judged only by average-case performance.

---

## 8. Representative ML Algorithms and Their Intuition

This section gives a conceptual view rather than full mathematical derivations.

## 8.1 Logistic Regression

Despite the name, it is mainly a classification model.

It estimates the probability that an input belongs to a class.

### Why it matters
- Simple
- Fast
- Interpretable
- Strong baseline

### Networking use
- Binary intrusion detection
- Link failure prediction
- QoS violation prediction

---

## 8.2 Decision Trees and Random Forests

A decision tree learns a sequence of if-then splits.  
A random forest combines many trees.

### Why they matter
- Handle nonlinear structure
- Often work well on tabular network features
- Can provide feature importance

### Networking use
- Traffic classification
- Intrusion detection
- Fault diagnosis

---

## 8.3 Support Vector Machines

SVMs try to separate classes using a decision boundary with large margin.

### Why they matter
- Effective in some medium-sized feature spaces
- Can model nonlinear boundaries with kernels

### Networking use
- attack detection,
- traffic classification,
- anomaly detection.

---

## 8.4 Neural Networks

Neural networks learn hierarchical representations.

### Why they matter
They are powerful when:
- data is large,
- patterns are complex,
- feature engineering is limited,
- or sequential/spatial structure matters.

### Examples in networking
- sequence models for traffic time series,
- CNN-based payload or flow pattern analysis,
- GNNs for topology-aware tasks,
- deep RL for control.

---

## 8.5 Clustering Algorithms

Examples:
- k-means
- hierarchical clustering
- DBSCAN

### Networking use
- grouping hosts by behavior,
- traffic pattern discovery,
- anomaly exploration,
- device fingerprinting.

---

## 8.6 Reinforcement Learning Algorithms

These are useful when networking decisions are sequential.

### Networking use
- congestion control,
- adaptive routing,
- edge offloading,
- caching,
- wireless scheduling.

### Conceptual challenge
Unlike classification, RL must balance:
- **exploration**: trying new actions
- **exploitation**: choosing what seems best now

In real networks, poor exploration may be costly.

---

## 9. A Concrete End-to-End Example

Let us walk through a full example.

## Problem: Detecting DDoS traffic at flow level

### Step 1: Define the task
Binary classification:
- benign
- DDoS

### Step 2: Choose observation unit
Each sample is one network flow.

### Step 3: Collect data
Possible fields:
- source/destination IP
- source/destination port
- protocol
- duration
- packets
- bytes
- packet size statistics
- inter-arrival times
- TCP flags

### Step 4: Create features
Examples:
- average packet size
- packets per second
- bytes per second
- SYN packet ratio
- inbound/outbound ratio
- variance of packet inter-arrival times

### Step 5: Label data
Flows are labeled from:
- controlled attack experiments,
- IDS correlation,
- expert annotation,
- or trusted datasets.

### Step 6: Train baseline models
- Logistic Regression
- Random Forest
- Gradient Boosting

### Step 7: Evaluate properly
Not just overall accuracy. Also:
- precision,
- recall,
- F1,
- false positive rate,
- inference latency.

### Step 8: Think operationally
Ask:
- Can this run at line speed?
- What is the cost of false positives?
- Will the model still work on encrypted traffic?
- Does it fail when attacks evolve?

This example shows that building the model is only one part of the problem. The full networking context matters.

---

## 10. ML in Networking vs ML for Generic Data Science

Students should clearly understand this distinction.

### Generic data science often assumes:
- a fixed dataset,
- stable labels,
- offline evaluation,
- no adversary,
- and little concern about deployment latency.

### Networking ML often involves:
- continuous data streams,
- changing environments,
- rare critical events,
- real-time constraints,
- system feedback loops,
- partial observability,
- and adversarial conditions.

That is why strong networking ML requires both:
- machine learning knowledge,
- and deep networking intuition.

---

## 11. Practical Design Questions Students Should Always Ask

Before applying ML to a networking problem, ask:

1. What is the decision we are trying to make?
2. What data is available at the exact decision time?
3. What is the prediction target?
4. Is this supervised, unsupervised, or RL?
5. What is the cost of errors?
6. What is the right baseline?
7. Is the dataset realistic?
8. Does the evaluation reflect deployment conditions?
9. Can the solution run under real system constraints?
10. How will the model behave when the environment changes?

These questions are often more important than choosing the newest algorithm.

---

## 12. Practical Examples of Problem Formulation

### Example A: QoS Violation Prediction
- **Input:** recent link loads, queue lengths, RTT, packet drops
- **Output:** whether SLA violation will occur in next interval
- **Type:** supervised classification

### Example B: Throughput Forecasting
- **Input:** historical throughput and congestion indicators
- **Output:** next-step throughput value
- **Type:** supervised regression

### Example C: Device Behavior Clustering
- **Input:** communication patterns of IoT devices
- **Output:** clusters of similar device behavior
- **Type:** unsupervised learning

### Example D: SDN Route Selection
- **Input/state:** topology state, link usage, queue levels
- **Action:** choose forwarding path
- **Reward:** delay reduction + throughput improvement
- **Type:** reinforcement learning

### Example E: Unknown Attack Discovery
- **Input:** unlabeled traffic behavior vectors
- **Output:** anomaly score
- **Type:** unsupervised anomaly detection

---

## 13. Discussion: When Not to Use ML

This is an important intellectual discipline.

Do **not** use ML when:

- a deterministic rule solves the problem cleanly,
- labels are unreliable and unsupervised output is not actionable,
- interpretability is mandatory and black-box behavior is unacceptable,
- the training data does not reflect reality,
- the system cannot tolerate unpredictable behavior,
- or the computational budget is too tight.

Sometimes the best solution is:
- a protocol redesign,
- a control-theoretic controller,
- a queueing-based policy,
- an optimization method,
- or a simple threshold.

A strong engineer chooses the right tool, not the most fashionable tool.

---

## 14. Summary

This week introduced the conceptual foundation of machine learning for networking.

We studied:

- why ML is useful in some networking problems,
- why networking data is challenging,
- the major learning paradigms,
- how to formulate networking tasks as ML problems,
- the ML pipeline from data collection to deployment,
- and the evaluation pitfalls that commonly mislead researchers.

The most important takeaway is this:

> In networking, success with machine learning depends at least as much on problem formulation, data quality, feature design, and evaluation realism as on the choice of algorithm.

In the following weeks, we will build on this foundation and move closer to specific networking applications, data collection pipelines, observability, traffic analysis, and AI-driven network control.

---

## Key Terms

- Supervised Learning
- Unsupervised Learning
- Semi-Supervised Learning
- Reinforcement Learning
- Classification
- Regression
- Clustering
- Anomaly Detection
- Feature Engineering
- Labeling
- Concept Drift
- Overfitting
- Class Imbalance
- Data Leakage
- Generalization
- Inference Latency
- Operational Constraints

---

## Suggested In-Class Discussion Questions

1. Why is high accuracy often a misleading metric in network intrusion detection?
2. What makes networking datasets more difficult than standard benchmark datasets?
3. In what situations is reinforcement learning more natural than supervised learning for networking?
4. Why can a model that performs well in simulation fail in a real network?
5. What kinds of networking problems are better solved without machine learning?

---

## Suggested Short Exercises

### Exercise 1: Problem Formulation
Choose one networking problem from the list below and formulate it as an ML task:
- DDoS detection
- traffic forecasting
- route optimization
- anomaly detection in IoT
- congestion prediction

For your chosen problem, specify:
- input,
- output,
- ML paradigm,
- evaluation metrics,
- and one practical deployment challenge.

### Exercise 2: Metric Critique
Suppose a classifier achieves 99.2% accuracy in attack detection.  
List at least three reasons why this result may still be operationally useless.

### Exercise 3: Feature Brainstorming
For encrypted traffic classification, propose at least eight features that do not rely on packet payload contents.

---

## Mini Practical Activity

### Title
First ML Thinking Exercise for Networking

### Objective
Learn how to transform a networking problem into a structured ML pipeline.

### Task
Students work in small groups and choose one of the following:
- malicious traffic detection,
- link load prediction,
- user behavior clustering,
- or adaptive routing.

Each group must produce a one-page design including:
1. problem statement,
2. available data,
3. sample features,
4. ML paradigm,
5. candidate baseline model,
6. evaluation metrics,
7. operational risks.

### Deliverable
A short markdown or PDF summary.

---

## Recommended Reading

### Networking + ML Perspective
- Survey papers on ML for networking
- Papers on traffic classification, anomaly detection, and congestion prediction
- Introductory materials on supervised, unsupervised, and reinforcement learning

### Conceptual Topics to Review
- Bias-variance tradeoff
- Precision and recall
- Class imbalance
- Time-series prediction
- Exploration vs exploitation
- Generalization under distribution shift

---

## Preview of Next Week

Next week, we move from conceptual ML foundations to the **data foundation of AI-driven networking**.

We will study:

- network telemetry,
- logs, metrics, and traces,
- flow-level monitoring,
- observability pipelines,
- and why data engineering is often the hidden backbone of successful ML systems in networking.

The central theme will be:

> Before intelligent decisions come intelligent measurements.

---
