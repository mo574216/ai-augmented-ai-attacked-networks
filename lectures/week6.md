---
title:  Week 6- Reinforcement Learning for Routing and Congestion Control
nav_order: 6

---

# Week 6: Reinforcement Learning for Routing and Congestion Control

## Overview

In the previous week, we studied deep learning for network analytics. We saw that deep models are important not only because they can improve prediction, but because they can help networks learn richer internal representations of behavior, performance, structure, and risk.

This week, we take the next major step.

So far, most of our focus has been on how AI helps the network **observe**, **interpret**, and **understand**. Now we move toward a more active question:

> Can the network learn how to act?

This is where reinforcement learning (RL) becomes central.

Routing and congestion control are among the most fundamental functions in computer networking. They are not merely technical subproblems. They shape the efficiency, reliability, fairness, responsiveness, and resilience of the entire system.

Traditionally, these areas have been addressed through:

- protocol design,
- mathematical optimization,
- control theory,
- heuristic adaptation,
- and carefully engineered distributed algorithms.

These approaches remain essential. In fact, they are still the foundation of practical networking.

So why study reinforcement learning here?

Because modern network environments increasingly exhibit properties that are difficult to fully capture through fixed rules alone:

- traffic conditions change dynamically,
- topology and path quality may vary,
- multi-path choices interact in complex ways,
- congestion emerges from many coupled decisions,
- wireless and mobile environments are highly uncertain,
- cloud and edge systems create rapidly changing demand patterns,
- and local decisions can create delayed, system-wide consequences.

In such settings, routing and congestion control are not just calculation problems. They are **sequential decision problems under uncertainty**.

That is the natural domain of reinforcement learning.

But this week follows the same philosophy as the rest of the course: RL is not interesting merely because it offers another optimization method. Its deeper significance is that it can change how we think about network control itself.

Instead of hand-coding all adaptation logic in advance, we can ask whether the network can:

- learn from interaction,
- improve from feedback,
- discover non-obvious control strategies,
- adapt to changing environments,
- and reason over long-term consequences rather than short-term reactions alone.

This week, therefore, studies **reinforcement learning for routing and congestion control** not as a narrow algorithmic topic, but as a broader shift in the idea of intelligent network control.

---

## Learning Objectives

By the end of this week, students should be able to:

1. Explain why routing and congestion control can be formulated as sequential decision problems.
2. Understand the basic reinforcement learning framework of state, action, reward, and policy.
3. Map routing and congestion control problems into RL formulations.
4. Distinguish between classical control approaches and RL-based adaptive control.
5. Analyze the opportunities and risks of applying RL to network decision-making.
6. Explain challenges such as delayed rewards, partial observability, exploration risk, instability, and scalability.
7. Evaluate when RL is a meaningful tool for networking and when other approaches remain preferable.

---

## 1. Why Routing and Congestion Control Matter So Much

A network must do more than forward packets. It must decide how traffic should traverse shared resources and how sending behavior should adapt when those resources become stressed.

These two questions are foundational:

- **Routing** asks: which path or next hop should traffic take?
- **Congestion control** asks: how aggressively should a sender inject traffic into the network?

These decisions affect:

- throughput,
- latency,
- packet loss,
- fairness,
- jitter,
- energy usage in some networks,
- stability,
- and user experience.

Even more importantly, these decisions interact with one another.

A route choice changes:
- load distribution,
- queue dynamics,
- and path delay.

A congestion control decision changes:
- queue buildup,
- competition among flows,
- and pressure on bottlenecks.

So routing and congestion control are not isolated functions. They are part of a coupled dynamic system.

This is one reason RL is attractive here: it is designed for systems where actions influence future states.

---

## 2. From Static Rules to Adaptive Interaction

Classical network control often relies on expert-designed logic.

For routing, this may involve:
- shortest path metrics,
- link-state information,
- path costs,
- ECMP,
- policy constraints,
- and traffic engineering objectives.

For congestion control, this may involve:
- additive increase and multiplicative decrease,
- window adaptation rules,
- loss-based logic,
- delay-based logic,
- model-based controllers,
- or bandwidth estimation.

These methods are powerful because they are:
- interpretable,
- analytically grounded,
- relatively predictable,
- and often robust when carefully designed.

But they also encode an important assumption:

> the designer can specify the adaptation logic in advance.

RL challenges that assumption.

It asks whether part of the adaptation logic can instead be **learned through experience**.

This is not always desirable. But when the environment is too complex for stable manual tuning, it becomes a compelling possibility.

---

## 3. Why Reinforcement Learning Fits Network Control

Reinforcement learning is a natural fit for problems with the following properties:

- the agent repeatedly interacts with an environment,
- actions influence future states,
- outcomes are observed through feedback,
- and the objective is long-term cumulative performance.

Routing and congestion control both fit this pattern.

### Routing example
A controller observes:
- topology state,
- link loads,
- queue lengths,
- delay measurements,
- path failures,
- and traffic demand patterns.

It chooses:
- path selection,
- next-hop decisions,
- traffic splitting ratios,
- or re-routing actions.

The consequences unfold over time:
- queues grow or shrink,
- delays change,
- bottlenecks shift,
- and new traffic interactions emerge.

### Congestion control example
A sender or controller observes:
- RTT,
- packet loss,
- ACK arrival behavior,
- throughput,
- jitter,
- or congestion signals.

It chooses:
- sending rate,
- congestion window adjustments,
- pacing behavior,
- or target bandwidth changes.

Again, the result is delayed and dynamic:
- future queue states change,
- packet losses may appear later,
- fairness behavior emerges over time,
- and the system may stabilize or oscillate.

This is exactly the kind of environment RL is meant to handle.

---

## 4. The Reinforcement Learning Framework

To use RL in networking, we must express the control problem in terms of four core elements:

- **state**
- **action**
- **reward**
- **policy**

## 4.1 State

The state is the information available to the agent when making a decision.

In networking, possible state variables include:
- queue lengths,
- RTT,
- link utilization,
- packet loss,
- throughput,
- topology changes,
- channel quality,
- traffic demand estimates,
- historical observations,
- and local or global telemetry summaries.

### Important point
The true network state is often larger than what is observable. So many networking RL problems are actually **partially observable**.

This matters a lot.

---

## 4.2 Action

The action is what the agent is allowed to do.

### Routing actions
- choose next hop,
- select end-to-end path,
- split traffic across paths,
- update forwarding weights,
- reroute selected flows.

### Congestion control actions
- increase or decrease sending rate,
- update congestion window,
- change pacing rate,
- adjust control parameters,
- choose among predefined control modes.

The design of the action space strongly affects feasibility and safety.

---

## 4.3 Reward

The reward tells the agent how good an outcome is.

This is one of the most important and difficult parts of RL design.

Possible reward objectives include:
- high throughput,
- low delay,
- low packet loss,
- fairness,
- energy efficiency,
- link utilization balance,
- low jitter,
- SLA satisfaction,
- or stability.

### Why reward design is difficult
Many of these objectives conflict with one another.

For example:
- maximizing throughput alone may create unfairness,
- minimizing delay alone may underutilize links,
- aggressively avoiding loss may reduce efficiency,
- prioritizing short-term gains may create long-term instability.

So the reward is not just a score. It encodes the network’s control philosophy.

---

## 4.4 Policy

The policy is the mapping from states to actions.

A policy may be:
- table-based,
- parameterized by a neural network,
- stochastic,
- deterministic,
- centralized,
- or distributed.

The learned policy becomes the network’s control behavior.

This is why RL is powerful and also risky: it does not merely optimize a number. It learns a style of decision-making.

---

## 5. Routing as a Sequential Decision Problem

Routing is often introduced in networking as a graph problem:
- shortest path,
- least cost path,
- constrained path,
- traffic engineering,
- multi-commodity flow optimization.

These views remain valid.

But RL highlights another aspect:

> Routing is also an ongoing process of adaptive path selection under uncertainty.

This becomes especially important when:
- traffic changes rapidly,
- link quality is unstable,
- failures occur,
- wireless conditions fluctuate,
- mobility affects topology,
- or centralized optimization is too slow or incomplete.

### Why RL can help
An RL agent can try to learn:
- which path choices lead to lower delay over time,
- how congestion propagates after rerouting,
- when it is better to spread traffic vs concentrate it,
- how to respond under incomplete or delayed information,
- and how short-term decisions shape future bottlenecks.

This turns routing from a static calculation into an adaptive learning problem.

---

## 6. Congestion Control as a Sequential Decision Problem

Congestion control is an especially natural RL candidate because it is deeply temporal.

A sender does not just choose a rate once. It continuously adjusts behavior based on feedback.

### Classical view
Congestion control is a control loop driven by:
- packet loss,
- RTT,
- explicit congestion signals,
- and ACK timing.

### RL view
Congestion control is a repeated decision process in which the sender learns how actions affect future network response.

This matters because congestion is often:
- delayed,
- nonlinear,
- shared among many competing flows,
- and environment-dependent.

An RL-based controller may try to learn:
- when to increase aggressively,
- when to back off early,
- how to avoid oscillation,
- how to behave across varying RTTs,
- or how to balance throughput against latency.

This is especially appealing in environments where traditional assumptions are less reliable, such as:
- wireless systems,
- datacenters,
- heterogeneous edge environments,
- or rapidly changing mobile networks.

---

## 7. RL Changes the Way We Think About Network Control

This week is not just about applying RL algorithms. It is about a deeper conceptual shift.

## 7.1 From Fixed Control Laws to Learned Policies

Traditionally, routing and congestion control are designed by explicitly defining the adaptation law.

RL introduces the possibility that the control law itself can be learned.

That is a major change.

It means we ask not only:
- what should the controller do?

but also:
- how can the controller learn what works?

---

## 7.2 From Immediate Reaction to Long-Term Consequence Awareness

Many classical rules are strongly local and immediate.

RL is designed to optimize cumulative reward over time.

This means it can, at least in principle, learn to prefer actions that:
- look slightly worse now,
- but improve the overall trajectory later.

For example:
- early rerouting to avoid later congestion,
- cautious rate increase to avoid severe queue buildup,
- short-term sacrifice for long-term fairness or stability.

This long-horizon perspective is one of the strongest conceptual reasons to study RL.

---

## 7.3 From Static Tuning to Environment-Sensitive Adaptation

Classical controllers often depend on parameters chosen offline.

RL opens the possibility of adapting policy behavior to:
- topology,
- workload,
- congestion regime,
- wireless quality,
- traffic burstiness,
- or application mix.

This is important in modern networks because fixed tuning may not transfer well across environments.

---

## 7.4 From Network-Wide Design to Local Learning Agents

Some RL-based networking systems are centralized. Others are distributed.

This raises a major design possibility:
Can network control emerge from multiple interacting agents rather than a single fixed protocol logic?

This is especially relevant for:
- multi-hop routing,
- wireless coordination,
- edge networks,
- IoT systems,
- and decentralized network control.

It also introduces serious challenges, which we will discuss later.

---

## 8. Core RL Families Relevant to Networking

The course does not require full mathematical derivations here, but students should know the main styles.

## 8.1 Value-Based Methods

These methods estimate how good actions are in different states.

Examples:
- Q-learning
- Deep Q Networks (DQN)

### Networking relevance
Useful when:
- the action space is discrete,
- decisions are structured enough for action enumeration,
- and the state-action value is meaningful to estimate.

### Example uses
- next-hop selection,
- path choice among a limited set,
- discrete congestion control actions.

---

## 8.2 Policy-Based Methods

These methods directly learn the policy.

### Networking relevance
Useful when:
- the action space is large,
- actions are continuous,
- or stochastic behavior is useful.

### Example uses
- continuous rate control,
- traffic splitting ratios,
- adaptive parameter tuning.

---

## 8.3 Actor-Critic Methods

These combine value estimation with direct policy learning.

### Why they matter
They often provide a good balance between:
- learning stability,
- flexibility,
- and efficiency.

### Networking relevance
Common in more advanced continuous or large-scale control tasks.

---

## 8.4 Multi-Agent Reinforcement Learning

In many network settings, there is not just one agent.

Possible agents include:
- routers,
- switches,
- wireless nodes,
- senders,
- edge devices,
- or services.

### Why this matters
Network behavior often emerges from multiple interacting controllers.

### Promise
- decentralized adaptation,
- scalability,
- local autonomy.

### Challenge
- coordination difficulty,
- instability,
- non-stationary learning environment,
- fairness and convergence issues.

Multi-agent RL is especially important for networking because networks are inherently distributed systems.

---

## 9. RL for Routing: Concrete Application Areas

To keep examples fresh and non-repetitive, this section emphasizes distinct forms of transformation.

---

## 9.1 Adaptive Path Selection Under Dynamic Load

Instead of always choosing a path from static link costs, an RL agent may learn to route based on:
- evolving delay,
- queue buildup,
- link contention,
- and demand changes.

### Why this matters
Routing becomes anticipatory rather than purely reactive.

---

## 9.2 Traffic Splitting Across Multiple Paths

Many networks support multipath routing.

RL can help decide:
- how much traffic to place on each path,
- when to rebalance,
- how to avoid synchronized overload,
- and how to exploit path diversity.

### Why this matters
The problem is not only selecting a best path, but learning a dynamic allocation strategy.

---

## 9.3 Routing in Mobile or Wireless Environments

In mobile ad hoc, mesh, vehicular, or wireless sensor networks, routing conditions change rapidly.

RL can help learn:
- path quality under changing radio conditions,
- route reliability over time,
- energy-aware forwarding strategies,
- or mobility-sensitive path decisions.

### Why this matters
These environments often violate the assumptions of stable static routing.

---

## 9.4 Topology-Aware Control in SDN

In software-defined networks, a controller may have a broader view of network state.

RL can be used to learn:
- which rerouting actions best relieve stress,
- how to balance controller knowledge with fast reaction,
- and how to optimize network-wide objectives under changing demand.

### Why this matters
It brings learning into programmable network control.

---

## 9.5 Resilience and Failure Recovery

After a link or node failure, the network must adapt.

RL can help learn:
- which rerouting patterns reduce secondary congestion,
- how to recover gracefully,
- how to maintain service continuity,
- and how to respond under uncertainty.

### Why this matters
Recovery is not just recomputation. It is a dynamic adaptation process.

---

## 10. RL for Congestion Control: Concrete Application Areas

---

## 10.1 Learning Rate Adaptation in Variable Environments

An RL-based sender can learn how different signals relate to future performance in a given environment.

### Why this matters
Instead of following a fixed increase/decrease rule, the sender may learn context-sensitive adaptation.

---

## 10.2 Latency-Aware Congestion Control

Traditional congestion control often emphasizes throughput and loss. But in many modern services, latency is critical.

RL can help learn control behaviors that better balance:
- delay,
- throughput,
- jitter,
- and stability.

### Why this matters
The controller can be optimized toward application-aware goals rather than one generic notion of performance.

---

## 10.3 Congestion Control in Wireless and Mobile Networks

Wireless networks complicate congestion signals because losses may not indicate congestion alone.

RL may help learn:
- how to interpret noisy feedback,
- how to adapt across rapidly changing quality,
- and how to separate channel effects from queue effects.

### Why this matters
This is a case where fixed control assumptions often struggle.

---

## 10.4 Joint Sender-Environment Adaptation

In complex systems, congestion control may interact with:
- scheduling,
- edge offloading,
- service orchestration,
- or application adaptation.

RL can support more integrated control strategies.

### Why this matters
Congestion is not always a single-loop problem anymore. It can be part of a broader adaptive ecosystem.

---

## 10.5 Fairness-Aware Control

Congestion control is not only about maximizing one sender’s rate.

RL can be designed to incorporate:
- fairness,
- coexistence,
- queue discipline compatibility,
- and service differentiation goals.

### Why this matters
It allows us to ask what kind of sharing behavior the network should learn.

---

## 11. The Central Design Challenge: Reward Engineering

One of the hardest parts of RL in networking is designing the reward.

Suppose we define reward as:

- throughput minus delay minus loss

This sounds reasonable, but several questions immediately arise:

- How much delay is too much?
- How should fairness be included?
- Should packet loss and jitter be weighted equally?
- Is short-term throughput more important than long-term stability?
- Should rewards differ by application class?

These are not merely tuning questions. They are policy questions.

### Example tension
A reward that strongly emphasizes throughput may produce aggressive behavior.  
A reward that strongly penalizes queueing may become too conservative.  
A reward that ignores fairness may exploit the environment in undesirable ways.

Thus, reward design is one of the places where networking knowledge matters most.

---

## 12. Partial Observability in Real Networks

In textbooks, RL is often introduced with full knowledge of state.

In real networks, this is rarely true.

A sender usually does not see:
- all queue states,
- competing flows,
- future traffic demand,
- full topology condition,
- or the precise source of delay.

A router often sees only:
- local queue information,
- recent packets,
- local measurements,
- and perhaps limited shared state.

This means real RL for networking often operates in partially observable settings.

### Why this matters
The agent must learn under uncertainty.  
Its observations may be delayed, noisy, incomplete, or ambiguous.

This makes network RL substantially harder than many toy RL environments.

---

## 13. Exploration: The Promise and the Danger

Reinforcement learning typically learns through exploration.

But in networking, exploration is risky.

A bad exploratory action can cause:
- congestion,
- packet loss,
- service disruption,
- unstable paths,
- unfairness,
- or SLA violations.

This creates one of the deepest practical tensions in network RL:

> How can a network learn safely while still improving?

Possible strategies include:
- simulation-first learning,
- offline RL,
- constrained RL,
- safe exploration,
- staged deployment,
- or learning only in low-risk subspaces.

This is one reason why operational deployment of RL in networking remains challenging.

---

## 14. Stability and Oscillation

Network control must be stable.

A controller that learns aggressively but oscillates is often worse than a simpler one that behaves predictably.

RL introduces additional stability concerns because:
- the policy may change during learning,
- multiple agents may co-adapt,
- rewards may be delayed,
- and feedback loops are nonlinear.

### Example
A routing policy that shifts traffic too quickly may create new congestion elsewhere.  
A congestion policy that reacts too strongly may cause repeated over-correction.

Thus, one of the key questions in RL-based networking is not only:
- does it learn?

but also:
- does it behave stably?

---

## 15. Simulation, Emulation, and Reality Gap

Most RL for networking is first developed in:
- simulation,
- emulation,
- controlled labs,
- or trace-driven environments.

This is natural because direct online experimentation is risky.

But it creates a serious problem:

> Will the learned policy transfer to real networks?

Differences may arise from:
- inaccurate traffic models,
- simplified link behavior,
- unrealistic failure patterns,
- missing human or application feedback,
- timing mismatch,
- or unmodeled adversarial behavior.

This is known as the **reality gap**.

It is one of the biggest reasons why strong RL results in papers do not automatically imply deployment readiness.

---

## 16. Multi-Agent RL and the Distributed Nature of Networks

Many network control problems are naturally distributed.

A separate agent may exist at each:
- node,
- link,
- sender,
- wireless device,
- or forwarding element.

This fits the architecture of real networks, but creates serious complexity.

### Benefits
- local autonomy,
- scalability,
- reduced need for central coordination,
- adaptability to local conditions.

### Challenges
- agents affect each other’s environment,
- learning becomes non-stationary,
- selfish or unstable behavior may emerge,
- coordination is difficult,
- global objectives are harder to enforce.

This is why multi-agent RL is both highly relevant and deeply challenging in networking.

---

## 17. Worked Example: RL for Adaptive Routing

## Problem
A network experiences dynamic demand shifts and occasional hotspots. Static shortest-path routing often overloads certain links.

## RL formulation

### State
- current link utilization,
- recent queue lengths,
- delay statistics,
- demand estimates,
- and path history.

### Action
- select among candidate paths,
- or adjust traffic splitting ratios.

### Reward
- high delivery efficiency,
- low end-to-end delay,
- low packet loss,
- balanced utilization.

## Why RL is attractive
The effect of a routing decision is delayed and network-wide. A slightly longer path now may avoid severe future queue buildup.

## What makes it hard
- action effects interact across many flows,
- observation may be incomplete,
- exploration may harm performance,
- reward balancing is delicate.

This example shows why routing is both promising and difficult for RL.

---

## 18. Worked Example: RL for Congestion Control

## Problem
A sender operates in a heterogeneous environment with variable RTT, competing flows, and rapidly changing conditions.

## RL formulation

### State
- recent RTT samples,
- ACK dynamics,
- throughput history,
- packet loss signals,
- pacing history.

### Action
- increase, decrease, or maintain sending rate,
- or choose a continuous rate update.

### Reward
- high throughput,
- low delay,
- low loss,
- smooth stable behavior.

## Why RL is attractive
The sender can potentially learn how different network conditions relate to future performance, rather than relying only on one fixed handcrafted control law.

## What makes it hard
- congestion signals are ambiguous,
- rewards are delayed,
- exploration can be harmful,
- coexistence with other flows matters.

This example shows why RL may offer richer adaptation, but also why safe deployment is difficult.

---

## 19. What Students Should Learn to Notice

After this week, students should begin noticing that RL changes network control at a deep level.

They should see that RL allows us to ask new questions:

- Can routing policies be learned rather than fully specified?
- Can congestion control become more environment-sensitive?
- Can long-term control objectives be learned directly from feedback?
- Can multiple agents coordinate in a distributed network?
- Can the network discover better trade-offs than static tuning offers?

At the same time, they should also notice the limitations:

- RL is not automatically stable,
- reward design is hard,
- safe exploration is a major challenge,
- simulation success may not transfer,
- and classical control methods remain extremely important.

That balance is essential.

---

## 20. Summary

This week studied reinforcement learning for routing and congestion control.

We examined:

- why routing and congestion control are sequential decision problems,
- how they can be formulated using state, action, reward, and policy,
- how RL changes network control from fixed logic toward learned adaptation,
- concrete application areas in routing and congestion control,
- and the major challenges of reward design, partial observability, exploration risk, stability, scalability, and transfer to real networks.

The central takeaway is:

> Reinforcement learning is important in networking not merely because it offers another optimization technique, but because it introduces the possibility of learned control policies that adapt through feedback and reason over long-term network consequences.

This makes RL one of the most conceptually important AI paradigms for the future of intelligent network control.

---

## Key Terms

- Reinforcement Learning
- State
- Action
- Reward
- Policy
- Value Function
- Q-learning
- Actor-Critic
- Multi-Agent Reinforcement Learning
- Routing
- Congestion Control
- Safe Exploration
- Partial Observability
- Stability
- Reality Gap
- Fairness
- Long-Term Reward

---

## Suggested In-Class Discussion Questions

1. Why are routing and congestion control natural sequential decision problems?
2. In what sense does RL change the philosophy of network control?
3. Why is reward design especially difficult in networking?
4. Why is exploration more dangerous in networking than in many toy RL environments?
5. What are the main challenges in transferring RL policies from simulation to real networks?

---

## Suggested Short Exercises

### Exercise 1: RL Formulation for Routing
Formulate a routing problem as an RL task. Specify:
- state,
- action,
- reward,
- and one major practical challenge.

### Exercise 2: RL Formulation for Congestion Control
Formulate a congestion control problem as an RL task.  
Discuss what the reward should include and why.

### Exercise 3: Classical Control vs RL
Choose either routing or congestion control and compare:
- a classical approach,
- and an RL-based approach.

Discuss:
- interpretability,
- adaptability,
- stability,
- deployment difficulty,
- and expected strengths and weaknesses.

---

## Mini Practical Activity

### Title
Designing an RL Controller for a Network Problem

### Objective
Help students translate a real networking control problem into a reinforcement learning formulation while recognizing practical constraints.

### Task
Students form small groups and choose one of the following:

- adaptive multipath routing,
- wireless route selection,
- datacenter congestion control,
- edge offloading control,
- fairness-aware bandwidth adaptation,
- failure-aware rerouting.

For the chosen problem, the group must specify:

1. What is the environment?
2. What is the agent?
3. What observations define the state?
4. What actions are possible?
5. What reward captures the real networking objective?
6. What exploration risks exist?
7. What makes this problem hard in the real world?

### Deliverable
A short markdown report or 5-minute presentation.

---

## Recommended Reading

### Topics to Review
- Reinforcement learning fundamentals
- RL for network routing
- RL-based congestion control
- Multi-agent RL in distributed systems
- Safe RL and constrained RL
- Learning-based control in communication networks

### Reading Perspective
While reading, students should ask:

- What is the actual control problem being learned?
- Is RL truly necessary here?
- How is the reward designed?
- What is assumed about observability?
- How is safety handled?
- Would the learned policy realistically transfer beyond the lab?

---

## Preview of Next Week

Next week, we move from RL-based control toward a broader systems perspective on **AI-native network management and autonomous network operations**.

We will study how AI can support not only one control loop, but a larger operational fabric including:

- configuration,
- fault management,
- performance assurance,
- anomaly response,
- policy adaptation,
- and closed-loop automation.

The key transition will be:

> From learning isolated control decisions to building networks that can manage themselves more intelligently.

---
