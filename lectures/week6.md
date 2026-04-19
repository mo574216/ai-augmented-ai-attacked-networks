# Week 6 — Reinforcement Learning for Routing and Congestion Control

## Overview

This lecture introduces **reinforcement learning (RL)** as a framework for networking problems that involve repeated decision-making under changing conditions. Unlike supervised learning, which learns from fixed labeled examples, reinforcement learning learns by interaction with an environment and by observing the consequences of actions over time.

In networking, this is especially relevant for problems such as routing, congestion control, traffic engineering, and adaptive resource allocation. These are not one-time prediction problems. They are **control problems** in which actions affect future network states, performance, and stability.

The lecture focuses on understanding how routing and congestion control can be formulated as RL problems, what the main difficulties are, and why practical deployment remains challenging even when simulation results look promising.

---

## Learning Objectives

By the end of this lecture, students should be able to:

- explain why routing and congestion control are sequential decision problems
- describe the difference between reinforcement learning and supervised learning in networking contexts
- formulate a networking problem using the main RL concepts: state, action, reward, policy, and environment
- explain how RL can be applied to routing and congestion control
- distinguish between Q-learning, Deep Q-Networks, policy-gradient methods, and actor-critic methods at a conceptual level
- discuss the challenges of reward design, exploration, safety, fairness, and generalization in network RL
- evaluate RL-based networking studies critically, including the role of simulation and baseline comparison
- understand why operational deployment of RL in real networks is difficult

---

## Lecture Structure

This lecture is organized into five main parts:

1. **Why reinforcement learning matters in networking**
2. **Core RL concepts for network control**
3. **RL for routing**
4. **RL for congestion control**
5. **Deployment challenges, realism, and future directions**

---

## Slide Topics

1. Week 6 title and agenda  
2. Recap of Week 5  
3. Why routing and congestion control are sequential problems  
4. What RL adds beyond supervised learning  
5. MDP view of networking  
6. Agent and environment in networks  
7. Reward design basics  
8. Multi-objective reward tradeoffs  
9. State representation for routing  
10. State representation for congestion control  
11. Action space for routing  
12. Action space for congestion control  
13. Episodes and time steps in networking  
14. Q-learning intuition  
15. Deep Q-Networks  
16. Policy-gradient intuition  
17. Actor-critic intuition  
18. Multi-agent RL intuition  
19. Centralized vs decentralized training  
20. Exploration vs exploitation  
21. Offline vs online RL in networking  
22. Simulation environments  
23. Why simulation matters  
24. Routing fundamentals refresh  
25. RL for adaptive routing  
26. Case: decentralized RL routing  
27. Topology dynamics and routing  
28. Congestion control fundamentals refresh  
29. RL for TCP-style congestion control  
30. Datacenter congestion control with RL  
31. Fairness in RL congestion control  
32. Stability and oscillation risks  
33. Generalization challenge  
34. Reward hacking and unintended behavior  
35. Sample efficiency issues  
36. Safety-aware RL for networks  
37. Hybrid methods  
38. Explainability for RL policies  
39. Benchmarking RL in networking  
40. Emerging direction: continual RL  
41. Emerging direction: LLM-guided control ideas  
42. Preview of Week 7  
43. Wrap-up and reading assignment  

---

## Key Themes

### 1. RL is naturally suited to network control problems
Routing and congestion control require repeated decisions under uncertainty. Actions affect future delays, losses, and queue states, which makes RL conceptually attractive.

### 2. Problem formulation matters more than algorithm names
In networking, the success of RL often depends less on whether we use DQN or actor-critic and more on whether the state, action, and reward are defined in a meaningful and safe way.

### 3. Reward design is one of the hardest parts
If the reward emphasizes throughput too much, latency or fairness may suffer. If the reward is too complex, learning may become unstable or produce unintended behavior.

### 4. Simulation success does not guarantee deployment success
Many RL studies in networking work well only in narrow environments. Real networks introduce drift, unseen traffic patterns, safety constraints, and operational requirements that make direct deployment difficult.

---

## Suggested Instructor Flow

A possible lecture flow is:

### Part 1: Why RL matters in networking
Slides 1–8  
Explain why routing and congestion control are sequential decision problems and introduce the control-oriented motivation for RL.

### Part 2: Core RL concepts
Slides 9–23  
Introduce state, action, reward, policy, Q-learning, DQN, policy-gradient methods, actor-critic methods, multi-agent settings, and the role of simulation.

### Part 3: RL for routing
Slides 24–27  
Review routing basics and show how adaptive routing can be learned using RL, especially in dynamic or decentralized settings.

### Part 4: RL for congestion control
Slides 28–38  
Discuss congestion-control fundamentals, RL for TCP-style and datacenter settings, fairness, stability, reward hacking, and safety-aware control.

### Part 5: Evaluation and future directions
Slides 39–43  
Focus on benchmarking, generalization, continual RL, LLM-guided control ideas, and the transition to Week 7 on SDN and network resource management.

---

## Suggested Reading

### Core reinforcement learning foundation
- Richard S. Sutton and Andrew G. Barto, *Reinforcement Learning: An Introduction*

### Recommended topic readings
- survey papers on reinforcement learning for routing
- papers on RL for datacenter congestion control
- papers on RL-based TCP or rate control
- papers on continual reinforcement learning in networking
- critical papers on generalization and fairness in learned congestion-control systems

---

## Suggested Discussion Questions

1. Why is reward design harder in networking than in many classical RL benchmark tasks?
2. Should RL systems ever be allowed to explore directly in a production network?
3. Is fairness a separate optimization objective, or should it be built into the reward from the beginning?
4. Can RL-based congestion control be trusted if it fails under unseen conditions?

---

## Suggested Lab / Activity

### Week 6 Lab
**RL for adaptive routing or congestion control**

#### Option A: Routing
Possible tasks:
- define a small topology in Mininet, ns-3, or a simplified simulator
- expose a state such as queue length or link utilization
- let the agent choose paths or next-hop preferences
- compare RL routing with a shortest-path or heuristic baseline
- measure delay, throughput, and packet loss

#### Option B: Congestion control
Possible tasks:
- define changing network conditions such as varying bandwidth and RTT
- let the agent adjust a simple rate or congestion-window-like action
- compare against a fixed or heuristic baseline
- evaluate throughput, queueing delay, and fairness

### Week 6 Discussion
Students can discuss one question such as:

**What should count as a convincing RL result in networking: benchmark performance, fairness, stability, or generalization?**

---

## Practical Emphasis

This week should help students build four important habits:

1. **Formulate before optimizing**  
   The quality of an RL solution depends heavily on how the networking problem is formulated.

2. **Think in terms of tradeoffs**  
   Throughput, delay, fairness, and stability often conflict, so reward design must reflect these tensions.

3. **Treat safety as a first-class issue**  
   Exploration, unstable policies, and unexpected actions are especially dangerous in operational networks.

4. **Test outside the training environment**  
   An RL policy should be evaluated on unseen scenarios, not only on the same environment in which it was trained.

---

## References

### Core references
1. Richard S. Sutton and Andrew G. Barto, *Reinforcement Learning: An Introduction*  

### Recommended topic areas for supporting readings
- reinforcement learning for routing
- RL in software-defined networking
- learned congestion control
- fairness and generalization in RL-based networking
- safe and continual RL for network control

---

## Summary

Week 6 introduces reinforcement learning as a framework for control-oriented networking problems such as routing and congestion control. It helps students understand why RL is conceptually appealing in networking, but also why real deployment remains difficult.

The main goal is to help students think critically about RL in networked systems: good results depend not only on the learning algorithm, but also on **state design, reward design, safe exploration, fairness, and generalization beyond the training environment**.

---

[← Previous Week](week5.html) | [Back to Schedule](../schedule.html) | [Next Week →](week7.html)
