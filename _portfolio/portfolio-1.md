---
title: "Multi-Agent Search in Adversarial Environments"
excerpt: "<br/><img src='/images/adversarial1.png'>"
collection: portfolio
---

![ViPER Project](/images/adversarial2.png)

### Overview
The problem of multi-agent search in adversarial environments is fundamentally different from traditional multi-agent path finding tasks. In such scenarios, robots must operate in dynamic and uncertain environments where targets may behave strategically to avoid detection, such as hiding behind obstacles or exploiting blind spots.

This creates unique challenges that go beyond solving path conflicts and deadlocks, demanding high-level coordination strategies where agents must collectively explore, clear, monitor, and defend the environment against intelligent opponents. I am particularly interested in how agents can balance competing objectives, such as area clearing and team assistance, while operating under partial observability and resource constraints, where individual sacrifices may be necessary to ensure overall mission success.

---

### Focus Project: Visibility-Based Pursuit-Evasion (ViPER)
Within this broader context, I chose to focus on the **visibility-based pursuit-evasion** problem as a representative and challenging entry point into adversarial search.

In this task, a team of pursuers must detect evaders that can move arbitrarily fast and are aware of the pursuers' strategies, often in environments with complex occlusions and unknown layouts.

To tackle this, I developed **ViPER**, a novel framework that leverages **graph attention networks** and **multi-agent reinforcement learning** to enable distributed yet tightly coordinated pursuit behaviors.

ViPER allows agents to dynamically balance exploration and guarding tasks, demonstrating emergent cooperation that surpasses existing non-learning methods both in simulation and real-world quadrotor deployments.

---

 
