# Week 10: Adversarial Machine Learning in Networks

## Overview

In the previous weeks, we gradually built a broader understanding of AI-native networking and security.

- In Week 2, we studied the foundations of machine learning for networking.
- In Week 3, we examined telemetry, observability, and measurement as the basis of intelligent networking.
- In Week 4, we explored traffic classification and application identification as a problem of network perception.
- In Week 5, we studied deep learning for network analytics as a way to learn richer internal representations.
- In Week 6, we examined reinforcement learning for routing and congestion control.
- In Week 7, we studied AI for SDN and network resource management in the context of network softwarization.
- In Week 8, we studied graph learning for networked systems, emphasizing that many networking problems are fundamentally relational.
- In Week 9, we studied AI for cybersecurity, with focus on IDS, malware analysis, and DDoS defense.

This week, we take a critical next step:

> **What happens when the AI systems used in networking and cybersecurity themselves become targets of attack?**

Once machine learning is used for:

- intrusion detection,
- traffic classification,
- anomaly detection,
- malware analysis,
- graph-based security analytics,
- routing support,
- reinforcement-learning-based control,
- or LLM-assisted network operations,

the AI pipeline itself becomes part of the attack surface.

This is the central topic of **adversarial machine learning (AML)**.

The lecture introduces the core ideas of adversarial machine learning and explains how attackers may manipulate:

- inputs,
- training data,
- model behavior,
- graph structure,
- reward signals,
- retrieved context,
- or AI-assisted workflows

in order to:

- evade detection,
- degrade performance,
- trigger hidden behavior,
- mislead analysts,
- or cause unsafe operational decisions.

This week builds directly on Week 9, because the systems we use to defend networks can themselves be attacked. It also prepares the ground for Weeks 11–13, where LLM-based operations and trustworthy AI become even more central.

The deeper message of this week is this:

> In AI-native networking, it is no longer enough to ask whether a model is accurate.  
> We must ask whether it remains trustworthy, safe, and operationally sound under adversarial pressure.

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

## Lecture Roadmap

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

## 1. Why Adversarial ML Matters in Networking

In ordinary machine learning, we often study whether a model can generalize to unseen but natural data.  
In adversarial machine learning, we study what happens when an intelligent attacker deliberately tries to manipulate the system.

This distinction matters enormously in networking.

A network AI system often operates in an environment where at least some participants are strategic and adversarial. That means the data is not merely noisy or incomplete. It may be intentionally shaped to deceive the model.

### Examples

- An attacker may modify malicious traffic to avoid an intrusion detector.
- A malware author may alter code structure to fool a classifier while preserving malicious intent.
- An attacker may poison security training data so that future models become weaker.
- A malicious insider may inject crafted content into an LLM-assisted troubleshooting workflow.
- A hostile actor may manipulate graph structure so that graph-based threat analytics misclassify risky nodes or edges.
- An attacker may exploit an RL-based controller by inducing states that trigger harmful actions.

So the problem is not only that AI systems can make mistakes. The problem is that those mistakes can be **induced strategically**.

A model that performs well under benign conditions may fail badly under adaptive attack.

That is why adversarial ML matters so much in networking and cybersecurity.

---

## 2. From Attacking Networks to Attacking Models

Traditional network security focuses on attacks against:

- hosts,
- services,
- protocols,
- infrastructure,
- and users.

But once AI becomes part of the network stack, a new possibility appears:

> the attacker can attack the decision-making layer itself.

This creates a shift from:
- attacking the network directly

to:
- attacking the models that interpret, classify, rank, recommend, or control within the network.

This is especially important because AI systems may influence:

- blocking decisions,
- alert prioritization,
- routing support,
- automated mitigation,
- service classification,
- operator guidance,
- and policy recommendations.

So if the model is deceived, the network may make the wrong operational choice even if the infrastructure itself is otherwise healthy.

This makes ML models part of the defensive surface and part of the attack surface at the same time.

---

## 3. What Is Adversarial Machine Learning?

Adversarial machine learning studies attacks and defenses involving machine learning systems under malicious pressure.

At a high level, an AML attack tries to cause one or more of the following outcomes:

- misclassification,
- stealthy evasion,
- model degradation,
- false alarms,
- hidden trigger behavior,
- information leakage,
- unsafe control output,
- or analyst manipulation.

AML includes attacks against:

- the **input** to the model,
- the **training data**,
- the **model internals**,
- the **prediction interface**,
- the **deployment pipeline**,
- or the **human-AI interaction loop**.

The central idea is this:

> the model should not be treated as a neutral function operating on passive data.  
> In adversarial settings, both the data and the model may be strategically targeted.

---

## 4. Why Network and Security ML Is Especially Vulnerable

Adversarial ML can matter in many domains, but networking and cybersecurity are especially exposed for several reasons.

### 4.1 The environment is adversarial by nature

Many networking AI systems are deployed specifically in contested environments:
- intrusion detection,
- malware classification,
- anomaly detection,
- abuse prevention,
- traffic filtering,
- and automated defense.

This means attackers are strongly motivated to manipulate them.

### 4.2 Inputs are often controllable by attackers

Attackers may directly or indirectly influence:
- packets,
- flows,
- protocol usage,
- timing behavior,
- DNS patterns,
- binary structure,
- process traces,
- graph relationships,
- and even prompt context in AI assistants.

This gives attackers leverage over model inputs.

### 4.3 Labels and training data are often weak

Security datasets may be:
- incomplete,
- noisy,
- outdated,
- weakly labeled,
- or partially generated by existing detectors.

This creates opportunities for poisoning and evaluation illusion.

### 4.4 AI outputs may affect operations

A poor prediction does not just reduce benchmark performance. It may cause:
- a missed attack,
- a false mitigation,
- wasted analyst time,
- policy misconfiguration,
- unsafe automation,
- or degraded service.

So the stakes are high.

---

## 5. Threat-Model Vocabulary

A recurring lesson of this week is:

> Adversarial claims are meaningful only if the threat model is clear.

A threat model should describe:

### Attacker goals
What does the attacker want?

Examples:
- evade detection,
- reduce model availability,
- implant a hidden trigger,
- extract the model,
- cause analyst confusion,
- induce unsafe control actions.

### Attacker knowledge
How much does the attacker know?

Examples:
- full knowledge of features and model,
- partial knowledge of data and training procedure,
- only query access to predictions.

### Attacker capabilities
What can the attacker control?

Examples:
- test-time inputs,
- a subset of training data,
- graph edges,
- prompt context,
- query interface,
- reward environment,
- or retrieved operational documents.

### Attacker constraints
What must remain realistic or functional?

Examples:
- traffic must still follow protocol norms,
- malware must still execute,
- graph perturbations must remain plausible,
- prompts must still look operationally believable.

This is crucial in networking because attacks that are mathematically successful but operationally unrealistic are not very convincing.

---

## 6. NIST AML Taxonomy Overview

A useful way to study AML is through a structured taxonomy mindset.

At a high level, attacks are often categorized by:

- **when** they occur:
  - training time
  - inference time

- **what** they target:
  - data
  - model
  - interface
  - workflow

- **what** the attacker wants:
  - confidentiality breach
  - integrity compromise
  - availability degradation

- **how much** the attacker knows:
  - white-box
  - gray-box
  - black-box

This taxonomy helps us move from vague claims like “the model is vulnerable” toward disciplined analysis.

---

## 7. Security Goals for ML Systems

In cybersecurity and networking, it is useful to think of ML security goals in terms similar to system security.

### Integrity
The model should not be easily manipulated into making wrong security decisions.

### Availability
The model should remain usable and not be degraded or overwhelmed.

### Confidentiality
Sensitive information about:
- model parameters,
- training data,
- or protected system behavior

should not be leaked.

### Safety and boundedness
The AI-assisted system should not trigger harmful or unsafe actions under adversarial influence.

This broader framing is especially important once AI participates in operations and control.

---

## 8. Attack Surface in Network AI Pipelines

A network AI system is not just a model. It is a pipeline that may include:

- telemetry collection,
- feature extraction,
- dataset creation,
- model training,
- model serving,
- thresholds or policy logic,
- retrieval systems,
- operator dashboards,
- tool calls,
- and automated actions.

Each of these may become part of the attack surface.

### Example attack surfaces
- poisoned telemetry,
- manipulated logs,
- crafted traffic inputs,
- adversarial graph edges,
- corrupted labels,
- malicious retrieved text,
- prompt injection,
- unsafe tool invocation,
- model-stealing queries.

This reinforces a major theme of the course:

> secure AI is not only about robust models. It is about secure pipelines and bounded operational integration.

---

## 9. Training-Time vs Inference-Time Attacks

This distinction is fundamental.

### Inference-time attacks
These occur when the attacker manipulates inputs at deployment time.

Goal:
- fool the already-trained model.

Examples:
- modify traffic features to evade an IDS,
- reshape malware behavior during execution,
- perturb graph structure at test time,
- inject malicious context into an LLM workflow.

These are often called **evasion attacks**.

### Training-time attacks
These occur before deployment or during model updates.

Goal:
- corrupt the model itself.

Examples:
- poison training data,
- inject mislabeled security samples,
- implant a backdoor,
- corrupt graph training edges,
- influence continual-learning updates.

These are especially dangerous because they may silently degrade future performance.

---

## 10. White-Box, Gray-Box, and Black-Box Attacks

### White-box
The attacker knows:
- model architecture,
- feature representation,
- parameters,
- and perhaps training details.

This is often useful for upper-bound evaluation.

### Gray-box
The attacker knows some but not all details.

This may be more realistic in many operational settings.

### Black-box
The attacker only sees outputs or can query the system indirectly.

This is often operationally important because attackers may not know internals but can still probe behavior.

A realistic adversarial evaluation often considers more than one knowledge assumption.

---

## 11. Evasion Attacks

Evasion attacks are probably the most well-known AML attack type.

The attacker modifies test-time inputs so that malicious behavior appears benign to the model.

### Examples in networking
- alter flow characteristics to evade a traffic classifier or IDS
- pad or reshape malware features
- inject benign-looking communication edges into a graph
- craft prompts that cause LLM-based assistants to misinterpret context

The core idea is:

> preserve malicious intent, but alter representation enough to fool the model.

This is especially important in cyber AI because attackers are often highly motivated to do exactly this.

---

## 12. Poisoning Attacks

Poisoning attacks target training data.

The attacker tries to influence what the model learns by inserting or altering training examples.

### Goals may include
- overall degradation
- targeted misclassification
- weakening detection of a particular attack family
- shifting decision boundaries
- increasing false positives or false negatives

### Examples in networking
- corrupted IDS labels
- injected benign-looking malicious traces
- manipulated telemetry for continual retraining
- malicious data contributions in collaborative or federated settings

Poisoning matters because many cyber datasets are already noisy and weakly labeled, which makes detection of poisoning harder.

---

## 13. Backdoor and Trojan Attacks

A backdoor attack implants hidden trigger behavior into a model.

The model behaves normally on most inputs, but when a specific trigger appears, it produces attacker-desired output.

### Examples
- a malware detector that misclassifies malicious binaries when a trigger pattern exists
- a NIDS that ignores attacks if certain crafted flow conditions are included
- a graph model that mislabels nodes when specific structural motifs appear
- an LLM assistant that behaves unsafely when special prompt phrases are present

Backdoors are especially dangerous because ordinary validation may not reveal them.

---

## 14. Model Extraction and Inference Attacks

Some attacks aim not to misclassify inputs directly, but to learn about the model.

### Model extraction
The attacker queries the model to approximate or reconstruct its behavior.

### Membership or inference attacks
The attacker tries to infer whether certain data was used in training or recover sensitive patterns about the data.

In networking, this may matter if:
- proprietary detection logic is exposed via APIs
- a service leaks model confidence
- a shared cyber platform exposes too much information to external users

These attacks connect AML with privacy and intellectual-property concerns.

---

## 15. Availability Attacks

Availability attacks aim to reduce the usefulness of the AI system.

Examples:
- overwhelm a detector with hard-to-classify inputs
- induce false positives at scale
- force repeated abstention
- create computational bottlenecks
- disrupt graph processing pipelines
- overload LLM workflows with malicious or irrelevant context

In security operations, an AI system that becomes noisy, slow, or unusable may be almost as dangerous as one that is bypassed.

---

## 16. Why Adversarial Examples Work

A useful conceptual question is:

> Why can small or structured changes fool a model?

Several reasons may contribute:

- learned decision boundaries may be brittle
- features may not align perfectly with true semantics
- the model may rely on shortcuts or spurious correlations
- high-dimensional inputs create complex local geometry
- training data may not cover adversarial corners of the space
- attackers may exploit underconstrained feature transformations

In networking, another important reason is that representation itself is often indirect.

For example:
- flow features are summaries, not full traffic truth
- graph construction is partial
- telemetry is sampled
- malware features are only partial views of behavior
- prompts are interpreted through imperfect reasoning

So the model is already operating on abstractions, and those abstractions can be exploited.

---

## 17. Transferability of Attacks

One of the most dangerous properties of adversarial attacks is transferability.

An attacker may craft an attack against one model and still fool another model with different architecture or training details.

This matters greatly in networking because:
- defenders may not know which attack surfaces transfer
- attackers may use surrogate models
- providers may hide model details but still remain vulnerable

Transferability makes black-box attacks more realistic and increases operational risk.

---

## 18. Constraints in Networking AML

A crucial theme of this lecture is realism.

In networking, the constraints are domain-specific.

### A realistic attack should often preserve:
- protocol validity
- traffic functionality
- communication success
- malware executability
- graph plausibility
- operational believability
- timing and system feasibility

This matters because a “successful” attack that breaks the network behavior or makes the sample obviously impossible is not operationally persuasive.

So always ask:

- Does the attack preserve domain constraints?
- Would the flow still work?
- Would the malware still execute?
- Would the graph change look plausible?
- Would the prompt still appear realistic in operations?

This is one of the most important habits in network-domain AML.

---

## 19. Evasion in Flow-Based Models

Flow-based models are common in:
- IDS
- traffic classification
- anomaly detection
- DDoS detection

Attackers may try to perturb features such as:
- packet count
- burst timing
- average packet size
- flow duration
- upstream/downstream ratios
- protocol behavior patterns

But the perturbations must often remain operationally valid.

### Important point
A good AML evaluation for flow models must show not only that features changed, but that the resulting traffic still:
- communicates successfully
- remains protocol-compliant
- and remains plausible in the deployment environment

---

## 20. Poisoning in Security Datasets

Security datasets are particularly vulnerable to poisoning because they are often assembled from:

- automated alerts,
- weak labels,
- retrospective incident tagging,
- mixed benign/malicious environments,
- or continuously updated telemetry streams.

An attacker may exploit this by:
- inserting mislabeled samples
- creating training artifacts
- contaminating benign baselines
- biasing retraining data toward misleading behavior

This is especially important in systems that retrain frequently or use continual learning.

---

## 21. Backdoors in Cyber ML

Backdoors are especially concerning in cyber ML because security operators may assume consistent detector behavior.

Possible trigger forms include:
- a rare feature combination
- a specific byte pattern
- a structural graph motif
- a token sequence in logs or prompts
- a timing pattern in network flows

This matters because a defender may validate a model extensively and still miss the hidden condition that activates the backdoor.

---

## 22. Attacking Graph-Based Network Models

This section connects directly to Week 8.

Graph-based models can be attacked through:

- node feature perturbation
- edge insertion or deletion
- subgraph manipulation
- poisoning of training graphs
- structural camouflage
- trigger subgraphs in backdoor settings

### Examples in networking
- add benign-looking edges around compromised hosts
- distort communication neighborhoods
- manipulate attack-graph relationships
- perturb service dependencies to mislead fault analysis

Because graph learning depends heavily on structure, structural manipulation can be very powerful.

---

## 23. Adversarial Issues in RL-Based Networking

This section connects back to Week 6.

RL-based networking systems may be vulnerable through:

- manipulated observations
- reward tampering
- environment shaping
- state aliasing
- unsafe exploration traps
- induced non-stationarity
- deceptive traffic patterns that bias learned policies

### Examples
- induce misleading congestion signals so the controller learns harmful routing behavior
- manipulate feedback to bias congestion control actions
- create adversarial scenarios that exploit learned policy weaknesses

This matters because RL systems do not just classify. They act.

So adversarial failure in RL-based networking may produce unsafe control behavior, not only wrong predictions.

---

## 24. Adversarial Issues in LLM-Assisted NetOps

This section prepares the transition to Week 11.

LLM-assisted NetOps systems may help with:
- troubleshooting
- summarization
- configuration explanation
- incident triage
- policy reasoning
- knowledge retrieval
- tool-assisted actions

But this creates new attack surfaces.

Possible adversarial issues include:
- prompt injection
- malicious retrieved content
- unsafe tool selection
- instruction hijacking
- hidden context manipulation
- over-trust in generated recommendations

This is why AML in networking now extends beyond classifiers into AI-enabled operations pipelines.

---

## 25. OWASP LLM Risks Relevant to Networking

Many LLM risks become operationally serious in NetOps and SecOps contexts.

Especially relevant categories include:
- prompt injection
- insecure output handling
- excessive agency
- over-permissioned tools
- sensitive information disclosure
- insecure retrieval
- hallucinated operational advice

In a networking setting, these are not only text-quality issues. They may affect:
- incident decisions
- operator trust
- tool execution
- configuration safety
- and defensive workflows

---

## 26. Prompt Injection in Network Operations Assistants

Prompt injection is especially important because LLM-based assistants may consume:
- logs
- tickets
- wiki content
- device outputs
- retrieved documents
- threat reports
- configuration snippets

If an attacker can place malicious instructions inside those sources, the assistant may be manipulated into:
- ignoring relevant evidence
- leaking data
- producing unsafe recommendations
- or attempting inappropriate actions

This is a powerful example of how AI workflow security becomes part of network security.

---

## 27. Defender Mindset: Hardening the Data Pipeline

One of the most important defenses is not model-centric. It is pipeline-centric.

Defenders should harden:
- data ingestion
- telemetry validation
- labeling workflows
- graph construction logic
- retrieval sources
- prompt context boundaries
- data provenance tracking

A secure AI system starts with secure inputs and trustworthy context.

---

## 28. Defender Mindset: Robust Training

Robust training aims to reduce model brittleness.

Possible approaches include:
- adversarial training
- data augmentation under realistic constraints
- regularization
- uncertainty-aware objectives
- robust representation learning
- poisoning-aware dataset curation
- backdoor screening during training

But robust training is helpful, not magical. Many defenses fail when evaluated more rigorously or under stronger adaptive attacks.

---

## 29. Defender Mindset: Runtime Defenses

Runtime defenses operate during deployment.

Examples include:
- anomaly screening before model inference
- confidence thresholds
- abstention on uncertain inputs
- ensemble disagreement checks
- input sanitization
- graph consistency validation
- tool invocation controls
- prompt and retrieval filtering

These are especially important in operations because not every threat can be solved during training.

---

## 30. Defender Mindset: Secure Deployment

Secure deployment goes beyond the model.

Important ideas include:
- least privilege for AI tools
- bounded automation
- approval gates before high-impact actions
- secure logging and traceability
- retrieval isolation
- structured outputs instead of free-form actuation
- human review for unsafe or uncertain cases

This is a central lesson of AI-native networking:

> operational safety often depends more on deployment design than on raw model accuracy.

---

## 31. Evaluation Methodology for AML

Evaluation rigor is essential in adversarial ML.

A convincing AML evaluation should clarify:

- the threat model
- attacker goals
- attacker knowledge
- attacker capabilities
- domain constraints
- success criteria
- baseline models
- defense assumptions
- adaptive-attack setting
- operational plausibility

Without these, robustness claims are often weak.

---

## 32. Why Many AML Defenses Fail

Many AML defenses appear strong because:
- the threat model is weak
- the attacker is not adaptive
- domain constraints are ignored
- comparisons are unfair
- evaluation uses unrealistic settings
- robustness is measured only on narrow attack types
- deployment risks are not considered

This is why adversarial ML requires more methodological discipline than ordinary accuracy benchmarking.

---

## 33. Explainability and Uncertainty in Adversarial Settings

Explainability matters even more in adversarial contexts.

Operators may need to know:
- why an event was flagged
- which inputs drove the decision
- whether the system is confident
- whether the pattern looks adversarially unusual
- whether human review is needed

Uncertainty is also crucial.

A model that can say:
- “high confidence malicious”
- “low confidence”
- “possible adversarial manipulation”
- “unsafe to automate”

may be far more useful than a model that always outputs a forced class label.

---

## 34. Benchmarking Pitfalls

AML benchmarking is especially vulnerable to weak methodology.

Common pitfalls include:
- unrealistic perturbation spaces
- ignoring functional constraints
- hidden train/test leakage
- evaluating only white-box attacks
- no transferability analysis
- overfitting defenses to known attacks
- reporting robustness without operational context
- failing to test adaptive attackers

Strong robustness claims require especially strong evidence.

---

## 35. Case Study: AML Against NIDS

A useful case study is a network intrusion detector using flow features.

### Attack goal
Cause malicious traffic to be classified as benign.

### Possible attacker actions
- modify timing
- pad packets
- change flow segmentation
- alter bidirectional ratios
- inject benign-looking interaction patterns

### Key evaluation question
Would the modified traffic still:
- achieve attacker objectives
- remain protocol-valid
- remain operationally plausible
- avoid obvious degradation?

This case helps connect AML theory to concrete network-defense systems.

---

## 36. Case Study: Attacks on Graph and Network Models

Another useful case study is a graph-based security or topology model.

### Possible targets
- suspicious host detection
- attack propagation prediction
- topology-aware anomaly detection
- service dependency diagnosis

### Possible attack actions
- add or remove graph edges
- perturb node attributes
- inject trigger subgraphs
- poison graph construction data

### Key lesson
When structure matters, structural manipulation becomes an attack vector.

This reinforces the connection between Week 8 and Week 10.

---

## 37. Emerging Direction: Trustworthy AML Evaluation

A promising research direction is more trustworthy AML evaluation for real networked systems.

This includes:
- clearer threat-model reporting
- realistic protocol and functional constraints
- adaptive attacker testing
- multi-layer pipeline evaluation
- uncertainty-aware reporting
- human-in-the-loop robustness assessment
- deployment-oriented safety metrics

The broader direction is toward evaluations that are not only technically impressive, but operationally meaningful.

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

## Summary

Week 10 introduces adversarial machine learning as a central issue for AI-enabled networking and cybersecurity. It shows that once AI systems are integrated into detection, classification, routing, or operations, they themselves become potential targets of attack.

The main goal is to understand that secure AI is not just about model accuracy. It is about:

- **clear threat models**
- **realistic constraints**
- **robust evaluation**
- **pipeline security**
- **and bounded deployment in adversarial environments**

That is the central lesson of this week.

---

[← Previous Week](week9.html) | [Back to Schedule](../schedule.html) | [Next Week →](week11.html)
