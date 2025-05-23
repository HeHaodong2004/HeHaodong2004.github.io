---
title: "Map-Prediction Guided Planning under Uncertainty"
excerpt: "<br/><img src='/images/inpainting1.png'>"
collection: portfolio
---

![CogniPlan Project](/images/inpainting2.png)

### Overview

In real-world environments, mobile robots are often tasked to explore, navigate, or search in spaces that are partially observed, dynamic, and inherently uncertain. Traditional planners typically assume static or fully known maps, leading to limited adaptability and poor long-term decision making in such settings.

My research focuses on leveraging map predictions to bridge the gap between incomplete observations and high-level planning, enabling robots to anticipate multiple possible environment configurations and make risk-aware, long-horizon planning decisions. This paradigm, which I term **Map-Prediction Guided Planning under Uncertainty**, offers a general framework applicable to a wide range of tasks, from exploration and navigation to adversarial pursuit-evasion, by combining generative environment reasoning with graph-based planning.

---

### Focus Project: CogniPlan: Uncertainty-Guided Path Planning with Conditional Layout Prediction

As part of this research direction, I developed **CogniPlan**, a planning framework that integrates **conditional generative inpainting models** with **graph attention-based reasoning**.

CogniPlan enables robots to infer multiple plausible layouts from partial observations and dynamically reason over these predictions to guide their actions, much like humans rely on mental maps when navigating unknown areas.

We demonstrated CogniPlan's effectiveness in both **exploration** and **point-goal navigation** tasks, significantly outperforming state-of-the-art planners across challenging benchmark datasets and realistic indoor scenarios **without any finetuning**.


