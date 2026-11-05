---
title: 'Before the Algorithm: How I Search for Research Problems'
date: 2026-11-05
permalink: /posts/2026/11/before-the-algorithm/
tags:
  - robotics
  - research
  - decision-making
---

Choosing a research problem is often harder than choosing a method. A problem can sound important while hiding several different questions, only some of which may be worth pursuing. Before committing to an algorithm, I find it useful to ask: **what makes this problem difficult, and under what conditions does that difficulty matter?**

Here are some practices I have been using to turn broad questions into more concrete research problems. They are not a recipe; they are a way to make my assumptions easier to test and my next steps easier to choose.

## Turn a broad question into controllable factors

When a problem feels too complicated to reason about, I try to identify a small number of factors that might explain the behavior I care about. I then ask what it would mean to change each factor while keeping the others fixed.

A useful first experiment is often a switch: compare a setting where a capability or constraint is present with one where it is absent. The switch need not be realistic in isolation. Its purpose is to make a comparison interpretable.

The hard part is deciding what the switch actually changes. If changing it also changes the objective, the available actions, or the difficulty of another part of the task, the result may have several explanations. Writing down these choices before running the experiment makes disagreements much easier to resolve.

Binary switches are only a starting point. Once I have a clearer hypothesis, I vary the underlying quantities continuously. This lets me ask not just *whether* something matters, but *how much*, and whether its effect changes across conditions.

## Build the smallest experiment that could change your mind

A minimal experiment should preserve the mechanism being tested while removing details that make its outcome hard to interpret. Depending on the question, that might mean a mathematical model, a small simulation, or a carefully chosen subset of a larger system.

I try to write down a prediction before looking at the result: what do I expect to happen, and what outcome would make me reconsider the explanation? If all possible outcomes can be fitted into the original story, the experiment is unlikely to teach me much.

A failed prediction is useful when it tells me which assumption was doing the work. It can also suggest a more precise question. Rather than asking whether a factor is *always* important, I can ask which conditions make it important and which make it irrelevant.

## Use counterfactuals to understand the gap

When a practical method performs poorly, I want to know what improvement is possible and what would be required to obtain it. An idealized reference, or *oracle*, can help, provided its advantage is clearly specified.

For example, one oracle might have access to additional information. Another might have the same information as the practical method but be able to find an optimal decision. A third might have more time or a larger set of actions. These comparisons answer different questions, so I try to change one advantage at a time.

The size of the gap matters, but so does its sensitivity. Does the gap remain when assumptions change? Does it disappear under a reasonable baseline? Does an oracle's advantage depend on information or computational resources that a practical system could never obtain? A large gap is an invitation to investigate, not yet a guarantee that it can be closed.

## Look for interactions, not just individual effects

Two factors can each have a small effect on their own but matter a great deal together. They can also partly cancel each other. To see the difference, I compare all combinations rather than varying only one factor at a time.

Let **Jₐᵦ** denote the cost when switches A and B take values *a* and *b*. One way to measure their interaction is:

**Interaction = J₁₁ − J₁₀ − J₀₁ + J₀₀.**

This asks whether the effect of changing A depends on the setting of B. The sign tells us whether the combined effect is greater or smaller than the sum of the individual effects, relative to the chosen baseline. A value near zero means the effects are approximately additive under that particular cost and comparison.

For continuous variables, mixed derivatives can express a related idea locally. Neither a derivative nor a finite difference is automatically an explanation: I still need to understand the mechanism behind it and check whether the comparison changes only what I intended.

## Map where the answer changes

A single result is a point in a larger space of possible conditions. I find it helpful to vary important parameters and visualize how the outcome changes across that space.

The most interesting parts of a map are often the boundaries. Where does the preferred decision change? Where does a gap become large or small? Does an interaction change sign? Are the boundaries stable when I change the model or the numerical resolution?

<figure>
  <img src="{{ '/images/research-notes/blind-corner-regime-map.png' | relative_url }}" alt="An example regime map showing decision regions, cost contours, and hatched regions across two model parameters." loading="lazy">
  <figcaption><small>An example from an ongoing simplified navigation study. The horizontal axis varies obstacle randomness; the vertical axis is the ratio of stopping distance to the distance available after visibility. Colors indicate preferred maneuvers; thin contours show an interaction cost. The upper hatching marks a limited approach distance, while the right-hand hatching marks a numerically under-resolved region. The map reflects one model and parameter choice.</small></figcaption>
</figure>

I use *regime map* as a practical term for this kind of visualization. It can reveal policy changes, sensitivity, and regions worth investigating. A boundary in such a map is not necessarily a phase transition in the strict mathematical sense, and its location may depend on the assumptions used to construct it.

## Decide what deserves more work

An experiment is most useful when it changes what I do next. If a gap is negligible across plausible conditions, I might look for a different problem. If it is large only in a narrow region, I want to know whether that region occurs in practice. If an effect is robust and its mechanism is clear, I can ask whether it suggests a better representation, decision rule, or algorithm.

I also want to move in the other direction: start with a failure that matters in the world, talk to people who encounter it, and use those observations to decide which factors to model. A clean abstraction is valuable only if its assumptions and predictions eventually meet evidence outside the abstraction.

For me, the goal is not to draw a map for every problem. It is to make a better decision about what to work on: identify the assumptions, find the conditions that change the answer, and let the experiment challenge the original idea.
