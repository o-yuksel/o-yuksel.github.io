---
layout: page
title: "Visualizing Modes of Adaptation in a Changing World"
description: "A simulation demonstrating how the pace of environmental change dictates whether a population adapts through slow genetic assimilation or rapid phenotypic plasticity."
img: assets/img/publication_preview/Scenario1_Slow_Speed.webp
importance: 1
category: work
related_publications: false
selected: true
---

Predicting the course of evolution is a fundamental challenge in biology. A recent theoretical framework proposes that by representing development as a dynamical system, we can predict evolutionary trajectories. Inspired by this work, the following in silico experiment provides a dynamic visualization of these principles, demonstrating the profound link between plastic responses and long-term genetic change.

### The Simulation: A Tale of Two Speeds

The script implements a population-based genetic algorithm where a Gene Regulatory Network (GRN) must adapt to a moving environmental optimum. This setup allows us to explore a key question: how does the *pace* of environmental change affect the *mode* of adaptation?

The animations below show a direct comparison between two scenarios. We can see three key elements:

* **The Optimum (red 'x')**: The ideal phenotype dictated by the environment at each generation.
* **The Average Reference Phenotype (green square)**: The population's genetically determined state. Its movement represents genetic adaptation.
* **The Average Expressed Phenotype (blue circle)**: The population's actual state under environmental influence. The vector between the green square and blue circle is the plastic response.

<div class="row">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid path="assets/img/publication_preview/Scenario1_Slow_Speed.webp" title="Slow Change: Genetic Assimilation" class="img-fluid rounded z-depth-1" %}
</div>
</div>
<div class="caption">
Under slow environmental change, the population has time to adapt genetically. The green square (genetics) closely tracks the red 'x' (optimum).
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/publication_preview/Scenario2_Fast_Speed.webp" title="Fast Change: Plastic Reliance" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Under rapid environmental change, genetic adaptation cannot keep up. The population survives by relying on its immediate plastic response (the blue circle) to track the optimum.
</div>

### The Mathematical Foundation

The behavior visualized is grounded in the mathematics of dynamical systems, where the change in a phenotypic state, $$x$$, is captured by a general equation.

$$
\dot{x}=f(t,x,\lambda), x(t_{0})=x_{0}
$$

This states that the rate of change of the phenotype ($$\dot{x}$$) is a function of time ($$t$$), the current phenotype ($$x$$), and developmental parameters ($$\lambda$$). The framework allows us to predict the effect of a small perturbation on the phenotype via the **sensitivity vector**, $$s_{\lambda}(t)$$.

$$
s_{\lambda}(t)=\frac{\partial x(t,\lambda)}{\partial\lambda}|_{\lambda=\lambda^{*}}
$$

The simulation uses a specific GRN model as a concrete implementation of the general function $$f$$.

$$
\dot{x}_{i}=\frac{r(b_{i})}{K_{i}+r(b_{i})}-\mu_{i}x_{i}; b_{i}=\sum_{j=1}^{n}\theta_{ij}x_{j}+u_{j}
$$

### Discussion

This comparative simulation provides a powerful, visual demonstration of how the rate of environmental change dictates a population's adaptive strategy. Under slow, predictable change, the population relies on **genetic assimilation**, where its underlying genetics gradually evolve to match the environment. Under rapid change, however, this process is too slow. Survival depends on leveraging existing **phenotypic plasticity** as a short-term solution to keep pace.

By providing a computational sandbox to explore these ideas, this script reinforces the concept that development is not an inscrutable black box but a structured process whose internal dynamics shape and channel evolution in predictable ways.
