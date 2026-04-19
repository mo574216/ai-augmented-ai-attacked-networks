# Week 14: Integration, Case Studies, and Student Presentations

## Overview

This final lecture brings the whole course together. The purpose of Week 14 is not to introduce one more isolated technical topic, but to help students see AI-enabled networking as a **complete system** that includes:

- telemetry and observability
- data representation
- machine learning and deep learning
- graph learning
- reinforcement learning and control
- cybersecurity analytics
- adversarial robustness
- LLM-assisted operations
- trust, governance, and bounded deployment

The central message of this week is that the future of AI in networking is not a collection of disconnected models. It is a movement toward **integrated, monitored, and constrained operational systems**. Recent surveys and deployment reports reinforce this direction: 2024–2026 literature increasingly frames AI-enabled networking around integrated management stacks, autonomous-but-bounded operations, LLM-assisted network management, and digital-twin-based validation rather than isolated model benchmarks. :contentReference[oaicite:0]{index=0}

This week is especially important for graduate students because it provides the bridge from course topics to research directions. By this point, you are no longer just learning techniques. You are in a position to ask stronger research questions:

- What kind of networking problem is truly worth solving?
- What data and representation make the problem meaningful?
- What AI method fits the structure of the problem?
- What would make the result operationally realistic?
- What would be required before such a system could be trusted in deployment?

This week also provides a natural framework for final project presentations and course reflection.

---

## Learning Objectives

By the end of this lecture, students should be able to:

- connect the major course topics into one end-to-end view of AI-enabled networking
- explain the full pipeline from telemetry to AI-assisted action and monitoring
- distinguish between promising demos and operationally realistic systems
- evaluate AI-enabled networking projects using technical, operational, and trustworthiness criteria
- explain the role of humans, safety controls, and governance in AI-driven network operations
- describe major future directions such as intent-based networking, network digital twins, and bounded autonomous operations
- present and discuss final projects in a structured and critical way

---

## Lecture Roadmap

This lecture is organized into five main parts:

1. **Course-wide integration**
2. **End-to-end case-study thinking**
3. **Operational trust and deployment maturity**
4. **Future directions**
5. **Student presentations and course synthesis**

---

## Slide Topics

1. Week 14 title and agenda  
2. Why this final week matters  
3. Recap of the whole course  
4. The big picture architecture  
5. Core pipeline of AI-enabled networking  
6. Where AI adds value in networks  
7. Where AI introduces risk  
8. Mapping course topics to network lifecycle  
9. Telemetry as the foundation  
10. Feature-based ML vs deep learning  
11. Sequential data vs graph data vs text data  
12. Networking tasks revisited  
13. Security tasks revisited  
14. Control tasks revisited  
15. NetOps tasks revisited  
16. A unified AI-for-networks reference architecture  
17. Case study template  
18. Case study 1: traffic classification system  
19. Case study 2: anomaly or IDS pipeline  
20. Case study 3: RL-based control loop  
21. Case study 4: LLM NetOps assistant  
22. What separates demos from real systems?  
23. Evaluation beyond accuracy  
24. Generalization across environments  
25. Human-in-the-loop as a design choice  
26. Trustworthy AI integration checklist  
27. Adversarial thinking checklist  
28. Deployment maturity levels  
29. Intent-based networking as an integration theme  
30. Intent-based lifecycle  
31. AI-based network management agents  
32. Agentic network operations  
33. Why agentic systems need constraints  
34. Network digital twin concept  
35. Digital twins for AI-driven operations  
36. Telemetry for digital twins  
37. Autonomous networking: promise and limits  
38. Research frontier 1: safer autonomy  
39. Research frontier 2: multimodal network intelligence  
40. Research frontier 3: trustworthy evaluation  
41. Student presentation guidance  
42. Final synthesis  
43. Closing slide  

---

## 1. Why This Final Week Matters

A common weakness in technical courses is that students finish with many tools but no systems view. They may know about classifiers, GNNs, RL, LLMs, or trustworthiness in isolation, yet still struggle to answer a more important question:

> How do these pieces fit together in a real networking system?

This final lecture is designed to close that gap.

It asks you to think like a researcher and a systems designer at the same time. A useful AI-enabled networking solution is rarely just:
- a dataset,
- a model,
- and a result table.

Instead, it is usually a workflow with:
- telemetry,
- representation choices,
- modeling,
- evaluation,
- operational constraints,
- human decision points,
- and rollback or containment mechanisms.

That systems view is exactly where much of the strongest recent work is heading. Large-scale LLM network-management frameworks, recent autonomous-network surveys, and digital-twin surveys all treat AI as part of a broader operational architecture rather than as a standalone predictor. :contentReference[oaicite:1]{index=1}

---

## 2. Recap of the Whole Course

A good way to summarize the course is to view it as a progression from **observation** to **understanding**, then to **decision**, and finally to **trustworthy operational integration**.

### Observation
We began with telemetry, measurement, and observability.  
Without meaningful data, no network intelligence is possible.

### Representation
We then examined feature-based ML, deep learning, graph learning, and sequential learning.  
The key lesson was that the right representation often matters as much as the right model.

### Decision and control
We studied routing, congestion control, SDN, resource management, and reinforcement learning.  
The key shift was from passive analysis toward active decision-making.

### Defense and adversaries
We studied IDS, malware, DDoS defense, adversarial ML, and LLM dual use.  
The key lesson was that AI in networks operates in contested environments.

### Operations and trust
We ended with LLM-based NetOps and trustworthy AI.  
The key lesson was that AI becomes operationally meaningful only when bounded by governance, verification, and deployment realism.

That full arc is the intellectual backbone of the course.

---

## 3. The Big Picture Architecture

A useful way to unify the course is with a reference architecture:

1. **Telemetry and observability layer**  
   logs, metrics, traces, flow records, graph structure, configs, tickets, documentation

2. **Representation layer**  
   tabular features, temporal windows, graph structures, text context, multimodal evidence

3. **Modeling layer**  
   ML, DL, GNNs, RL, LLMs, hybrid or agentic systems

4. **Decision-support layer**  
   ranking, diagnosis, prediction, summarization, recommendation, policy translation

5. **Actuation or workflow layer**  
   human review, ticket creation, SDN policy updates, bounded automation, tool calls

6. **Monitoring and governance layer**  
   drift detection, calibration checks, logging, rollback, access control, auditability

Recent work on LLM-based network management and intent-driven autonomous operations closely matches this layered interpretation: models are useful only when they are integrated with tooling, validation, observability, and human/model interaction patterns. :contentReference[oaicite:2]{index=2}

---

## 4. Core Pipeline of AI-Enabled Networking

Across the course, the same operational pipeline kept appearing in different forms:

**sense → represent → learn → decide → verify → act → monitor**

This pipeline is more important than any individual algorithm.

### Sense
Collect meaningful operational evidence.

### Represent
Choose forms that fit the problem:
- tabular
- temporal
- graph
- textual
- multimodal

### Learn
Apply appropriate methods:
- classical ML
- deep learning
- graph learning
- RL
- LLM systems

### Decide
Turn outputs into something operationally useful:
- classification
- ranking
- diagnosis
- control recommendation
- incident summary
- mitigation support

### Verify
Check syntax, safety, confidence, policy, and evidence.

### Act
Either:
- advise humans,
- require approval,
- or act within bounded authority.

### Monitor
Track drift, failures, trust signals, and operational consequences.

This pipeline is also a good way to structure research proposals and final projects.

---

## 5. Where AI Adds Value in Networks

Across all weeks, AI added value mainly in situations where networks are:

- high-dimensional
- dynamic
- difficult to model analytically
- partially observable
- knowledge-heavy
- or too operationally complex for purely manual management

### Common value zones include:
- traffic understanding
- anomaly detection
- intrusion detection
- control adaptation
- topology-aware inference
- log and ticket summarization
- knowledge retrieval
- operational workflow support
- proactive rather than reactive management

Recent surveys on LLM-based network/service management and autonomous network management both emphasize this shift toward broader operational value rather than single-task gains. :contentReference[oaicite:3]{index=3}

---

## 6. Where AI Introduces Risk

The course also showed repeatedly that AI does not only add value. It also adds risk.

### Common risk zones include:
- weak or partial observability
- misleading datasets
- brittle generalization
- drift
- adversarial manipulation
- hallucination
- unsafe tool use
- overtrust by operators
- unclear governance
- hidden coupling between AI and live network behavior

This is why strong systems thinking matters. A powerful model in a weak operational pipeline may be more dangerous than a modest model in a well-governed one.

---

## 7. Mapping Course Topics to the Network Lifecycle

A useful synthesis for students is to map topics to the lifecycle of network operations.

### Before incidents
- observability
- forecasting
- proactive analytics
- digital-twin validation
- configuration understanding

### During incidents
- anomaly detection
- IDS
- alert triage
- LLM-assisted diagnosis
- graph-based threat context
- bounded mitigation support

### During optimization and change
- SDN resource management
- RL-based control
- policy translation
- intent handling
- human-approved automation

### After incidents and changes
- postmortem summarization
- trust review
- drift monitoring
- retraining
- governance updates
- assurance and audit

This view helps students see AI not as one task, but as something that can appear across the operational lifecycle.

---

## 8. Telemetry as the Foundation

If one lesson from the course should remain after everything else is forgotten, it is this:

> AI in networking starts with telemetry.

No matter how advanced the model is, weak telemetry creates weak intelligence.

This is also why many future directions still come back to observability, structured context, and richer evidence pipelines. Industry and research discussions around autonomous operations, LLM-enabled NSM, and AI-era observability all place high importance on robust data foundations. :contentReference[oaicite:4]{index=4}

---

## 9. Feature-Based ML vs Deep Learning

A mature student should no longer ask:

- “Which is better, ML or deep learning?”

The better question is:

- “What structure does the problem have, and what representation does it require?”

### Feature-based ML is often strong when:
- domain features are meaningful
- interpretability matters
- data is limited
- deployment cost must remain low

### Deep learning is often stronger when:
- the structure is complex
- temporal or high-dimensional patterns matter
- representation learning itself is valuable
- handcrafted features are limiting

This is a research design lesson, not just a model-selection lesson.

---

## 10. Sequential Data vs Graph Data vs Text Data

One of the most important intellectual transitions in the course was understanding that not all network data should be represented the same way.

### Sequential data
Useful for:
- traffic evolution
- congestion dynamics
- staged incidents
- system-call or alert sequences

### Graph data
Useful for:
- topology
- host communication
- service dependency
- propagation structure
- attack graphs

### Text data
Useful for:
- logs
- tickets
- documentation
- change records
- analyst notes
- runbooks

A strong research project usually starts by getting this choice right.

---

## 11. Networking Tasks Revisited

Looking back, core networking tasks in the course included:

- traffic classification
- routing support
- congestion control
- resource allocation
- topology-aware prediction
- configuration understanding
- network observability support
- intent handling

These are not disconnected problems. They occupy different points in the same operational system.

---

## 12. Security Tasks Revisited

Similarly, the security-focused tasks included:

- IDS
- anomaly detection
- malware analysis
- DDoS defense
- graph-based threat reasoning
- adversarial robustness
- LLM-supported incident analysis
- misuse-aware workflow design

A useful research direction often appears where networking tasks and security tasks overlap.

---

## 13. Control Tasks Revisited

Control-oriented AI tasks included:

- routing
- congestion control
- SDN actuation
- bounded mitigation
- tool-assisted operations
- policy-aware orchestration

These are high-impact tasks. They are also the tasks where trust and bounded deployment matter most.

---

## 14. NetOps Tasks Revisited

NetOps tasks increasingly include:

- summarization
- troubleshooting support
- incident reporting
- config explanation
- retrieval over operational corpora
- tool-using assistants
- human-approved change support
- management agents

Recent surveys and deployment reports suggest that LLMs and multi-agent systems are being explored less as generic chatbots and more as bounded workflow components integrated with existing network-management tools. :contentReference[oaicite:5]{index=5}

---

## 15. A Unified AI-for-Networks Reference Architecture

A useful reference architecture for research and practice can therefore be summarized as:

- **data plane and telemetry plane**
- **representation and context plane**
- **reasoning and learning plane**
- **decision-support and validation plane**
- **actuation and governance plane**

This architecture is especially important because it gives you a template for evaluating papers and designing projects:
- Where does the data come from?
- What is the representation?
- What role does the model play?
- What validation occurs before action?
- What monitoring follows deployment?

---

## 16. Case Study Template

For the rest of the lecture, every case study should be analyzed with the same template:

1. What problem is being solved?
2. Why does it matter operationally?
3. What data is available?
4. How is the problem represented?
5. What AI method is used?
6. What action or workflow does the output support?
7. What risks or limitations remain?
8. Should the system be:
   - advisory only,
   - human approved,
   - or partially autonomous?

This template is also the right structure for final project presentations.

---

## 17. Case Study 1: Traffic Classification System

A traffic classification system may look technically simple, but a full systems view asks:

- How is data collected?
- Are labels realistic?
- Does the model generalize across environments?
- What operational action depends on the output?
- What happens under encryption drift or adversarial mimicry?
- Is the result useful for QoS, policy, or security?

This helps separate a publishable demo from a deployable system.

---

## 18. Case Study 2: Anomaly or IDS Pipeline

A strong IDS pipeline is not just:
- a dataset
- and a classifier.

It includes:
- telemetry design
- labeling assumptions
- alert thresholds
- ranking logic
- analyst workflow impact
- adversarial robustness
- and false-positive burden

This is why trustworthy evaluation matters so much in cyber AI.

---

## 19. Case Study 3: RL-Based Control Loop

An RL control loop should be evaluated not only by reward.

Important questions include:
- What is the state?
- What action authority exists?
- What is the fallback if the policy behaves badly?
- Is simulation realistic enough?
- What rollout stage is appropriate?
- What human oversight is required?

This is where the difference between research novelty and operational maturity becomes very visible.

---

## 20. Case Study 4: LLM NetOps Assistant

A useful LLM NetOps assistant may:
- retrieve operational evidence
- summarize logs
- explain configs
- propose next troubleshooting steps
- and require human review before action

A weak version may be just a fluent chatbot.  
A stronger version is grounded, evidence-linked, tool-bounded, and safe by design.

The Meta **Confucius** framework is a useful recent example of this trend: it reports a multi-agent LLM framework for network management that integrates with existing management tools, uses RAG, supports structured human/model interaction, and includes validation to prevent regressions; the paper describes it as production-ready and operational for two years with more than 60 applications onboarded. :contentReference[oaicite:6]{index=6}

---

## 21. What Separates Demos from Real Systems?

This is one of the most important questions for graduate students.

A strong demo may show:
- an interesting idea
- a good result
- a clever model
- a benchmark improvement

A more realistic system also addresses:
- data quality
- actionability
- trust
- monitoring
- rollback
- human role
- adversarial concerns
- deployment cost
- and organizational fit

This distinction should shape how you read papers and how you define your own research.

---

## 22. Evaluation Beyond Accuracy

By the end of the course, students should no longer think that accuracy alone is a satisfactory evaluation language for AI in networking.

Important additional dimensions include:
- calibration
- robustness
- drift sensitivity
- false-positive burden
- groundedness
- latency
- operator usefulness
- rollback success
- abstention quality
- safety under uncertainty
- and deployment cost

This is especially relevant in recent discussions of trustworthy AI and bounded autonomy. :contentReference[oaicite:7]{index=7}

---

## 23. Generalization Across Environments

A recurring challenge across almost every topic in the course was transfer:

- does the model still work on another topology?
- another traffic mix?
- another organization?
- another attacker style?
- another observability stack?

A paper that ignores this question is often less mature than it first appears.

---

## 24. Human-in-the-Loop as a Design Choice

A human-in-the-loop system is not automatically “less advanced.”

In many high-stakes networking settings, keeping humans in the loop is a sign of maturity, not weakness.

The real question is:
- Where should the human review happen?
- What should be automated?
- What should remain advisory?
- What should require explicit approval?

Recent intent-driven and autonomous-operations discussions increasingly frame human oversight as part of the architecture rather than as an afterthought. :contentReference[oaicite:8]{index=8}

---

## 25. Trustworthy AI Integration Checklist

A useful checklist for any project is:

- Is the data trustworthy?
- Is the representation appropriate?
- Is the model calibrated?
- Is uncertainty handled honestly?
- Are outputs grounded in evidence?
- Is the action path bounded?
- Is rollback possible?
- Is drift monitored?
- Is audit logging present?
- Is the human role explicit?

If several of these questions are unanswered, the project is probably not close to deployment maturity.

---

## 26. Adversarial Thinking Checklist

A second checklist is adversarial:

- How could an attacker evade this?
- Could the data be poisoned?
- Could the retrieval context be manipulated?
- Could the graph be perturbed?
- Could the model be overtrusted by operators?
- Could unsafe automation amplify the failure?

This mindset should now feel natural after Weeks 9–13.

---

## 27. Deployment Maturity Levels

A useful maturity ladder is:

### Level 0: Research-only
Offline experiments only.

### Level 1: Shadow mode
The system observes and predicts, but does not influence operations.

### Level 2: Advisory mode
Humans see outputs and decide.

### Level 3: Human-approved action
The AI prepares or recommends actions, but humans approve.

### Level 4: Bounded autonomy
The AI acts only within strict limits, with rollback and monitoring.

### Level 5: Broader autonomy
Only justified if trust, controls, and evidence are exceptionally strong.

This maturity view is often more useful than simply asking whether a system is “automated.”

---

## 28. Intent-Based Networking as an Integration Theme

Intent-based networking is a natural integration theme because it connects:

- human goals
- policy translation
- observability
- validation
- orchestration
- and bounded automation

Recent industry and research work increasingly ties intent-based operations to AI, observability, layered autonomy, and strong human oversight. Ericsson’s 2026 discussion of autonomous network operations explicitly frames intent, bounded autonomous domains, observability, AI/ML, and human oversight as central architectural components. :contentReference[oaicite:9]{index=9}

---

## 29. Intent-Based Lifecycle

A useful intent lifecycle is:

1. express intent
2. interpret and validate intent
3. map intent to policy or workflow
4. act within bounded domains
5. observe outcomes
6. resolve conflicts
7. adjust intent fulfillment over time

This lifecycle is also a good example of why networking AI is now a systems problem rather than a single-model problem.

---

## 30. AI-Based Network Management Agents

A major future direction is the emergence of AI-based network management agents that:
- retrieve knowledge
- plan multi-step workflows
- use bounded tools
- validate outputs
- and cooperate with humans and existing management systems

The recent **Confucius** framework is again relevant here because it treats network-management workflows as DAGs, uses multiple agents, integrates with tools, uses RAG, and emphasizes validation and structured human/model interaction. :contentReference[oaicite:10]{index=10}

---

## 31. Agentic Network Operations

Agentic operations are promising because they may reduce cross-tool friction and improve workflow orchestration.

But they also increase risk because:
- action chains become longer
- error propagation becomes easier
- overtrust becomes more dangerous
- and verification becomes more important

This is why agentic systems should be studied together with constraints and trust, not separately.

---

## 32. Why Agentic Systems Need Constraints

Agentic systems should usually have:
- bounded tools
- limited write authority
- approval gates
- explicit logs
- policy checks
- rollback paths
- and safe failure behavior

This is one of the clearest integrations of Weeks 10–13.

---

## 33. Network Digital Twin Concept

A **network digital twin** is a virtual representation of a network or its relevant behavior that can support:
- simulation
- validation
- what-if analysis
- planning
- optimization
- or safer testing of control and policy changes

This is an increasingly important area. A 2024 survey on digital twins for future networks emphasizes software frameworks, standardization efforts, use cases, and open challenges, while a 2026 survey on AI-driven digital twin networks signals continuing momentum in AI-enabled DTNs. :contentReference[oaicite:11]{index=11}

---

## 34. Digital Twins for AI-Driven Operations

Digital twins are especially attractive for AI-driven operations because they may help with:
- safer experimentation
- control validation
- replay of incidents
- capacity planning
- closed-loop testing
- and reduced risk before live rollout

That is why digital twins are increasingly linked to autonomous management, safer control, and evaluation realism in the literature. :contentReference[oaicite:12]{index=12}

---

## 35. Telemetry for Digital Twins

A digital twin is only useful if it remains meaningfully synchronized with the real system.

That means telemetry still matters:
- topology state
- performance state
- faults
- workloads
- and policy context

In that sense, digital twins do not replace observability. They depend on it.

---

## 36. Autonomous Networking: Promise and Limits

The promise of autonomous networking is clear:
- faster adaptation
- reduced operational burden
- more proactive optimization
- and better scaling of complex operations

But the limits are equally important:
- drift
- unsafe autonomy
- weak observability
- adversarial manipulation
- poor explainability
- and organizational overtrust

Recent surveys and industry architecture discussions tend to frame autonomy as **layered, bounded, and observability-driven**, not as unconstrained self-driving behavior. :contentReference[oaicite:13]{index=13}

---

## 37. Research Frontier 1: Safer Autonomy

One strong future research direction is safer autonomy:
- constrained agents
- confidence-aware control
- bounded intent realization
- simulation-backed rollout
- human override mechanisms
- and stronger assurance cases

This is likely to matter more than pure autonomy claims.

---

## 38. Research Frontier 2: Multimodal Network Intelligence

Another major frontier is **multimodal network intelligence**.

Future network AI systems will increasingly combine:
- telemetry
- time series
- graphs
- logs
- documents
- tickets
- configs
- and possibly vision-like or topology-rendered inputs

This direction is already visible in recent LLM-for-NSM work, multi-agent network-management frameworks, and digital-twin-oriented integration discussions. :contentReference[oaicite:14]{index=14}

---

## 39. Research Frontier 3: Trustworthy Evaluation

Perhaps the biggest open challenge is not inventing one more model.

It is designing evaluations that reflect:
- real environments
- adversarial pressure
- drift
- bounded autonomy
- human factors
- and deployment consequences

This is a strong and important research direction for graduate students because it is both scientifically meaningful and operationally necessary.

---

## 40. Student Presentation Guidance

A strong final project presentation should answer the following clearly:

- What problem are you solving?
- Why does it matter?
- What data or environment do you use?
- Why is your representation appropriate?
- Why is your method appropriate?
- What baselines did you compare against?
- What are the limitations?
- What are the operational risks?
- Should the system be advisory, human-approved, or partially autonomous?
- What would still be needed before deployment?

A strong presentation is not just a success story.  
It is a technically honest and operationally realistic argument.

---

## 41. Final Synthesis

If the course has one unifying systems lesson, it is this:

> AI in networking is not a model contest.  
> It is the design of a trustworthy operational system.

By now, students should be able to think across:
- telemetry
- representation
- learning
- control
- security
- LLM workflows
- adversarial risk
- deployment maturity
- and governance

That integrated mindset is the real achievement of the course.

---

## Key Themes

### 1. AI in networking is a system, not just a model
A useful AI-enabled networking solution includes data pipelines, telemetry, evaluation design, operational constraints, human oversight, and rollback or containment logic.

### 2. The strongest projects connect technical quality with operational realism
A model is not impressive just because it performs well on a benchmark. It should also make sense in deployment, support meaningful actions, and address risks and limitations honestly.

### 3. The future is likely to involve bounded autonomy
The course suggests a future in which AI agents, intent-based workflows, and digital twins support networking operations. But this autonomy must remain constrained, monitored, and verifiable. :contentReference[oaicite:15]{index=15}

### 4. Trustworthy evaluation is a central research frontier
One of the biggest open challenges is how to evaluate AI-enabled network systems in ways that reflect real operations, adversarial pressure, changing environments, and safety requirements.

---

## Recent Papers to Prioritize

For students who want current directions rather than only classic foundations, the following recent papers and reports are especially worth reading:

- a 2025 SIGCOMM paper on **Confucius**, a multi-agent LLM framework for network management at Meta, valuable for understanding agentic-but-validated management workflows :contentReference[oaicite:16]{index=16}
- a 2025 survey on **LLMs for communication, network, and service management**, useful for seeing how LLMs are being positioned across monitoring, planning, deployment, and continuous support :contentReference[oaicite:17]{index=17}
- a 2025 survey on **autonomous network management for 6G**, useful for seeing the broader self-management and autonomy landscape :contentReference[oaicite:18]{index=18}
- a 2024 survey on **digital twins for future networks**, useful for validation, synchronization, architecture, and standardization challenges :contentReference[oaicite:19]{index=19}
- a 2026 industry architecture discussion on **intent-driven autonomous network operations**, useful for seeing how bounded autonomy, observability, and human oversight are being framed in practice :contentReference[oaicite:20]{index=20}
- a 2025 World Economic Forum report on **AI in telecommunications**, useful for the broader operational and industry context around AI- and genAI-enabled network management :contentReference[oaicite:21]{index=21}

---

## Suggested Discussion Questions

1. Which parts of network operations should realistically become autonomous first?
2. Is a digital twin necessary for trustworthy AI-driven network control?
3. Does intent-based networking become more practical or more dangerous when combined with LLMs and agents?
4. What is the minimum evidence required before an AI system should influence a live network?

---

## Suggested Activity

### Week 14 Activity
**Final project integration and presentation**

Each student or team should present:

- the problem being addressed
- why the problem matters
- the dataset or experimental environment
- the AI method used and why it was chosen
- evaluation design and baseline comparisons
- limitations and operational risks
- trust, safety, or adversarial considerations
- whether the system should be advisory, human-approved, or partially autonomous

### Optional final discussion
Reflect on the question:

**What would make an AI-enabled networking system genuinely ready for operational deployment?**

---

## Practical Emphasis

This week should help students build four final habits:

1. **Integrate rather than isolate**  
   Think about AI-enabled networking as a complete workflow, not as an isolated model.

2. **Judge realism seriously**  
   Strong systems are not only accurate. They are also deployable, explainable, and operationally meaningful.

3. **Treat autonomy with caution**  
   Automation can be valuable, but bounded control, verification, and rollback remain essential.

4. **Present work critically and honestly**  
   A strong final project clearly states not only what worked, but also what failed, what remains uncertain, and what would be needed for real deployment.

---

## Summary

Week 14 closes the course by integrating all earlier topics into one operational view of AI-enabled networking. The future of this field is not built from isolated models, but from **carefully designed systems that combine telemetry, AI, operations, human oversight, and safety mechanisms**. Recent work on LLM-based network management, autonomous operations, and digital twins strongly supports this systems-level direction. :contentReference[oaicite:22]{index=22}

The main goal is to leave students with a systems mindset: the important question is not only **which model works best**, but also **how AI, networking, operations, trust, and governance should work together in a real environment**.

---

[← Previous Week](week13.html) | [Back to Schedule](../schedule.html)
