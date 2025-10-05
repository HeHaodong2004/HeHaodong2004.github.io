---
title: "Heterogeneous Multi-Agent Systems under Communication and Planning Constraints"
excerpt: "<br/><img src='/images/cbs1.png'>"
collection: portfolio
---

![CBS Protocol Project](/images/Cantwell@basic.scen_n7_s117_custom.mp4)

### Big Picture: Heterogeneous Multi-Agent Systems

The future of autonomy will not be dominated by a single type of robot or a single algorithm. Instead, it will involve **teams of heterogeneous agents**—aerial drones and ground vehicles, manipulators and mobile bases, learning-driven agents and classical optimizers—working together in complex, uncertain environments.  

Heterogeneity appears in **three dimensions**:  

- **Hardware diversity**: robots differ in form factors, sensing modalities, and actuation capabilities.  
- **Algorithmic diversity**: planners span heuristic search, sampling methods, optimization, diffusion models, and reinforcement learning.  
- **Operational diversity**: agents face varying levels of uncertainty, resource constraints, and communication availability.  

To unlock the full potential of such systems, we need **general coordination frameworks** that:  
1. **Abstract away low-level differences**, so that agents can cooperate without having to conform to a single planning or control paradigm.  
2. **Adapt to uncertainty and partial information**, enabling resilience in real-world deployments.  
3. **Balance autonomy and cooperation**, letting agents contribute individually while still aligning with team-level goals.  

My research vision is to build this umbrella of **heterogeneous multi-agent autonomy**, where different agents can be integrated seamlessly into a shared decision-making protocol.  

---

### Focus Project: CBS Protocol  
(*Joint work with [Rishi Veerapaneni](https://rishi-v.github.io/)*)

One concrete step toward this vision is the **CBS Protocol**, where we extend the well-known **Conflict-Based Search (CBS)** framework.  
🔗 [Project Page](https://rishi-v.github.io/CBS-Protocol/)

The **CBS Protocol** extends the classic **Conflict-Based Search (CBS)** framework (Sharon et al., 2015) to act as a **general coordination protocol** for heterogeneous agents.

- **Key Idea**: Require only one API from each agent: the ability to return a collision-free path that satisfies given **space-time constraints**.  
- **Planner-Agnostic**: With this interface, agents can be powered by **A\***, **RRT**, **Direct Collocation**, **Diffusion Models**, or **Reinforcement Learning**—and CBS can still coordinate them.  
- **Centralized Conflict Resolution**: A central planner uses CBS to resolve conflicts at the team level, ensuring global collision-free trajectories while leaving local planning details to each agent’s algorithm.  
- **Outcome**: This protocol demonstrates, for the first time, efficient **multi-agent motion planning with algorithmically heterogeneous teams** performing independent tasks.
---

### Looking Ahead

The CBS Protocol highlights a promising direction: **treating coordination not as a monolithic algorithm, but as a protocol** that can flexibly integrate heterogeneous planning modules. Looking forward, I aim to extend these principles toward **large-scale multi-robot systems** that combine the **guarantees of classical planning** with the **adaptability of learning-based methods**, all under a unifying coordination framework.
