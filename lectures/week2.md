# Week 2 — Foundations of Machine Learning for Networking

## Overview

This lecture introduces the core machine learning concepts that students need before applying AI methods to networking problems. The goal is not to teach machine learning in the abstract, but to explain it from a **networking-first perspective**.

The lecture focuses on how machine learning problems appear in networking, what kinds of data are used, how tasks are defined, how models are evaluated, and why mistakes in evaluation are especially common in network and security settings.

This week builds the conceptual bridge from the broad course introduction in Week 1 to the more technical topics that follow, such as telemetry analytics, traffic classification, deep learning, reinforcement learning, and AI for cybersecurity.

---

## Learning Objectives

By the end of this lecture, students should be able to:

- explain why machine learning is useful in networking
- distinguish between supervised, unsupervised, semi-supervised, and reinforcement learning in networking settings
- identify different types of networking data used for ML tasks
- explain the role of features, labels, train/validation/test sets, and generalization
- distinguish among classification, regression, clustering, and anomaly detection problems in networking
- explain common evaluation metrics and their meaning in networking and security tasks
- identify common mistakes such as leakage, unrealistic splits, and overreliance on accuracy
- understand how model choice depends on task type, data type, and operational constraints

---

## Lecture Structure

This lecture is organized into five main parts:

1. **Why machine learning matters in networking**
2. **Core machine learning concepts**
3. **Networking-specific ML task types**
4. **Modeling and evaluation**
5. **Case studies and common mistakes**

---

## Slide Topics

1. Week 2 title and agenda  
2. Recap of Week 1  
3. Why ML in networking?  
4. What problem are we solving?  
5. ML workflow at a glance  
6. What is a learning task?  
7. Types of networking data  
8. Feature-based vs representation-based learning  
9. Supervised learning  
10. Unsupervised learning  
11. Semi-supervised and self-supervised learning  
12. Reinforcement learning  
13. Online vs offline learning  
14. Batch learning vs streaming learning  
15. Training, validation, and test sets  
16. Overfitting and underfitting  
17. Bias-variance intuition  
18. Core evaluation metrics  
19. Metrics for imbalanced network and security data  
20. Regression tasks in networking  
21. Classification tasks in networking  
22. Clustering tasks in networking  
23. Anomaly detection tasks  
24. Time-series learning for networking  
25. Graph-based learning intuition  
26. Labeling challenges in networking  
27. Dataset shift and concept drift  
28. Class imbalance  
29. Noise and uncertainty in labels  
30. Data preprocessing pipeline  
31. Feature engineering for flows  
32. Dimensionality reduction  
33. Classical ML models overview  
34. Deep learning models overview  
35. Model selection for networking tasks  
36. Interpretability vs performance  
37. Cost-aware ML in networking  
38. Robustness considerations  
39. ML pipeline example: traffic classification  
40. ML pipeline example: anomaly detection  
41. Common mistakes in ML-for-networking studies  
42. Preview of Week 3  
43. Wrap-up and reading assignment  

---

## Key Themes

### 1. Networking problems must be translated into learning tasks
Before choosing a model, we must define the task clearly. In networking, this may mean predicting delay, classifying applications, detecting anomalies, or learning control policies.

### 2. The data type strongly affects the method
Packets, flows, logs, telemetry streams, graphs, and time series all have different structure. Good model design starts with understanding the data, not with choosing a fashionable algorithm.

### 3. Evaluation is often the hardest part
Many ML-for-networking studies look strong only because of unrealistic train/test splits, leakage, poor baselines, or misleading metrics. Students must learn to evaluate models critically.

### 4. Operational constraints matter
In networking, model quality is not only about accuracy. Inference cost, latency, interpretability, stability, and robustness often matter just as much.

---

## Suggested Instructor Flow

A possible lecture flow is:

### Part 1: Why ML matters in networking
Slides 1–8  
Explain why networking increasingly needs ML and show the basic workflow from data to decisions.

### Part 2: Core ML concepts
Slides 9–19  
Introduce the main learning paradigms, train/validation/test logic, overfitting, and evaluation metrics.

### Part 3: Networking-specific task types
Slides 20–29  
Connect ML concepts to regression, classification, clustering, anomaly detection, time-series learning, and graph-based ideas in networking.

### Part 4: Models and pipelines
Slides 30–38  
Discuss preprocessing, feature engineering, dimensionality reduction, classical models, deep models, model selection, interpretability, and cost.

### Part 5: Case studies and pitfalls
Slides 39–43  
Walk through small end-to-end examples and emphasize common mistakes that appear in published work and student projects.

---

## Suggested Reading

### Core machine learning foundations
- Christopher M. Bishop, *Pattern Recognition and Machine Learning*

### Optional broader ML reference
- Aurélien Géron, *Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow*

### Contextual reading for networking
- Selected survey papers on machine learning for networking
- Selected survey papers on AI/ML in network management
- One survey or tutorial paper on traffic classification or network anomaly detection

---

## Suggested Discussion Questions

1. Why is high accuracy often a misleading metric in intrusion detection?
2. Which matters more in operational networking: interpretability or maximum predictive performance?
3. When should a network engineer prefer a simple model over a deep model?
4. What kinds of dataset shift are most likely in real network data?

---

## Suggested Lab / Activity

### Week 2 Lab
**First ML pipeline for networking**

Possible tasks:
- load a small network-related dataset
- inspect features and labels
- split into training, validation, and test sets
- train a logistic regression model and a random forest model
- compare precision, recall, F1, and confusion matrix
- discuss whether the model is operationally useful

### Week 2 Discussion
Students can discuss one question such as:

**What makes an ML result in networking convincing, and what makes it suspicious?**

---

## Practical Emphasis

This week should help students develop three important habits:

1. **Define the task carefully**  
   Do not start from the model. Start from the networking problem.

2. **Match the model to the data**  
   Not every problem needs deep learning. Some networking tasks are better solved by simpler models.

3. **Evaluate honestly**  
   A strong-looking result with leakage or unrealistic splits is not useful.

---

## References

### Core references
1. Christopher M. Bishop, *Pattern Recognition and Machine Learning*  
2. Aurélien Géron, *Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow*  

### Recommended topic areas for supporting readings
- machine learning for networking
- traffic classification
- anomaly detection in networks
- evaluation of ML models under class imbalance
- generalization and concept drift in cyber/network data

---

## Summary

Week 2 provides the machine learning foundation for the rest of the course. It teaches students how to think about networking problems as learning problems, how to choose among task formulations and data representations, and how to evaluate results correctly.

The main goal is to develop sound judgment. Students should leave this week understanding that good AI for networking starts with **correct problem formulation, appropriate data, realistic evaluation, and awareness of operational constraints**.

---

[← Previous Week](week1.html) | [Back to Schedule](../schedule.html) | [Next Week →](week3.html)
