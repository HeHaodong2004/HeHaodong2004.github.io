---
title: 'Before the Algorithm: How I Search for Research Problems'
date: 2026-11-05
permalink: /posts/2026/11/before-the-algorithm/
tags:
  - robotics
  - research
  - decision-making
---

A robot approaches a blind corner. Someone may be moving on the other side, but the robot cannot see them yet. Should it slow down, move forward to get a better view, or wait?

There are many ways to make this problem difficult: occlusion, unpredictable motion, limited braking, delayed sensing, and an imperfect planner. When a robot fails, which of these actually matters? And would improving one of them change the decision?

I have been using questions like these to explore how I want to do research. My instinct is to start by making the world smaller: turn a complex situation into a few controlled changes, build a model that can challenge my assumptions, and map out where the answers change. This note describes that process, using an ongoing study of navigation around occlusions as an example.

## From a complicated scene to a set of switches

The first step is to choose what to simplify and what to preserve. For the blind corner, I might start with three factors:

- **Partial observability (P):** is the other agent visible, or hidden until the robot reaches a sight line?
- **Dynamics (D):** does the other agent follow a known motion, or can its behavior change unpredictably?
- **Robot capability (R):** can the robot stop or change its motion quickly enough after it sees the other agent?

These are not complete descriptions of the real world. They are experimental switches: a way to create related worlds that differ in controlled respects. Their definitions matter. For example, an agent moving along a known trajectory is dynamic in ordinary language, but in a particular experiment the D switch might instead compare *known* and *stochastic* motion. I need to say which comparison I am making.

Once the switches expose a mechanism, they can be replaced or supplemented by continuous parameters: braking strength, time spent out of sight, the rate of changes in motion, or observation delay. The objective is not to make everything binary; it is to make the first question precise enough to answer.

## The smallest world that can prove me wrong

I like minimal models because they make assumptions visible. A short approach to a single blind corner may be enough to ask whether a robot should slow down before it sees a moving obstacle. It can also make a tempting intuition fail.

For instance, it is easy to assume that hidden, unpredictable motion must always make an extra observation valuable. But the answer depends on what the robot can do with that observation, when it arrives, and what sensing costs. If the same action is optimal regardless of what the robot learns, better information may not change the decision. If the robot can safely observe before it must commit, the loss from being temporarily blind may be small.

A model should expose possibilities like these, rather than being constructed only to confirm the story I started with. A negative result can be useful: it tells me which conditions a proposed mechanism actually needs.

## What do the counterfactuals tell us?

An oracle is an idealized reference designed to answer a particular question. Different oracles answer different questions:

- A decision-maker with the same observations but optimal computation helps probe the cost of an imperfect algorithm.
- One that sees the obstacle's current state reveals the potential value of that additional observation.
- One that knows the obstacle's future has a stronger advantage and answers a different question again.

A gap to one reference does not automatically measure the cost of everything at once. Even an optimal-information gap depends on the objective, action set, timing and model assumptions. Conversely, a small gap under one set of assumptions does not prove that the practical problem is unimportant everywhere.

I also want to know whether two sources of difficulty interact. Let **J(P, D)** be a cost under a specified choice of switches, with the remaining conditions held fixed. The two-factor interaction is:

**I(P, D) = J(1, 1) − J(1, 0) − J(0, 1) + J(0, 0).**

This compares the effect of changing P when D is on with its effect when D is off. If it is positive, the joint cost exceeds the sum of the two changes measured from the chosen baseline; if negative, it falls below that sum. Zero means the effects are additive for this particular measure and comparison. This is a finite-difference analogue of a mixed derivative, but its value can depend on how the switches, baseline and cost are defined.

## From a single result to a map

A single experiment may tell me that a method works. A map can help me ask *where* and *why* it works.

<figure>
  <img src="{{ '/images/research-notes/blind-corner-regime-map.png' | relative_url }}" alt="A regime map showing different blind-corner maneuvers across obstacle randomness and robot commitment, with interaction-cost contours and hatched regions." loading="lazy">
  <figcaption><strong>An example from an ongoing simplified blind-corner study.</strong> The horizontal axis is the rate of random direction changes multiplied by the time the obstacle is hidden; the vertical axis is braking distance at the initial speed divided by the distance available after the obstacle becomes visible. Colors show the model's preferred maneuver: orange = commit, green = slow to a critical speed and peek, blue = peek at normal speed, purple = slow before reaching the sight line. The thick line marks a commitment ratio of 1; thin contours show the P × D interaction cost in seconds. In the upper hatched region the approach is too short to brake to the critical speed; the right-hand hatched region is under-resolved at the chosen simulation time step. This is one model and one set of parameters, not a general map of real-world navigation.</figcaption>
</figure>

In this example, the horizontal line has a physical interpretation: at a ratio of one, the initial stopping distance matches the distance available after the sight line. The colors change across parts of that boundary because the available choices change. The thin contours ask a separate question: how large is the additional interaction cost in this particular model?

The two need not have the same boundary. A threshold that changes what the robot can physically do does not by itself prove that the interaction cost suddenly becomes dominant at precisely that threshold. Likewise, a jagged boundary on a numerical grid may reflect resolution or model choices. That is why the hatched regions and the assumptions behind the figure matter.

I think of these as **regime maps**: maps of conditions under which different decisions or mechanisms matter. They are inspired by phase diagrams, although a change in the preferred policy is not necessarily a phase transition in the strict mathematical sense.

## From a map back to a research question

The map is not the final destination. It is a way to generate better questions.

If the advantage of an oracle is substantial only in a narrow region, what makes that region special? If it persists across variations in dynamics and sensing, can a practical policy recover some of it? If a mechanism disappears after adding a realistic delay, was the original explanation too fragile, or did the delay reveal a different bottleneck?

The next step is to put the model back in contact with the world: test whether its assumptions correspond to a real failure, add complexity selectively, and eventually check whether the proposed mechanism survives in simulation and on physical robots. Real-world needs also provide a separate starting point: an elegant boundary is more interesting when it explains a failure that someone actually encounters.

I do not see this as a universal recipe. It is a way of delaying commitment to a solution until I understand the question better. The most valuable outcome may be a new algorithm, a useful bound, or the realization that the question I originally wanted to solve was not quite the right one.
