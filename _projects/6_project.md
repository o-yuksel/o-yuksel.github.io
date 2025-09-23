---
layout: page
title: "Visualizing Evolutionary Prediction: A Simulation of Developmental Dynamics"
description:
img: assets/img/publication_preview/Scenario1_Slow_Speed.webp
importance: 1
category: work
related_publications: false
selected: true
---

Predicting the course of evolution is a fundamental challenge in biology. The complexity of development, where genes and environment interact in non-linear ways, often makes it seem daunting to foresee the phenotypic consequences of any given change. However, a recent theoretical framework by Milocco and Uller (2024) offers an optimistic perspective, proposing that by representing development as a dynamical system, we can uncover the underlying logic of how variation is generated and, in turn, predict evolutionary trajectories.


Inspired by this work, the following in silico experiment, circular_tracking_evolution_analysis.m, provides a dynamic visualization of these principles. It brings the paper's theory to life by simulating how a population adapts under selection, demonstrating the profound link between plastic responses and long-term genetic change.

The Simulation: A GRN in a Changing World
The script implements a population-based genetic algorithm centered on a Gene Regulatory Network (GRN), a classic model system used in the Milocco and Uller paper. The simulation places a population of these GRNs in an environment where the optimal phenotype is not static but moves along a circular path. The population must continuously evolve its genetic makeup to track this moving target.


This setup allows us to directly observe the concepts of plasticity and evolvability. The animation below shows the simulation's output. We can see three key elements:

The Optimum (red 'x'), representing the ideal phenotype dictated by the environment at each generation.

The Average Reference Phenotype (green square), showing the population's genetically determined state in a neutral environment. Its movement over generations represents genetic adaptation.

The Average Expressed Phenotype (blue circle), showing the population's actual state under the influence of the current environment. The vector between the green square and blue circle is the population's plastic response.

As the simulation runs, we can see how the population leverages its immediate plastic response to survive while longer-term genetic adaptation gradually shifts the reference phenotype to better align with the moving optimum.

<div class="row">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid path="assets/img/publication_preview/Scenario1_Slow_Speed.webp" title="GRN Adaptation" class="img-fluid rounded z-depth-1" %}
</div>
</div>
<div class="">
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/publication_preview/Scenario2_Fast_Speed.webp" title="LV" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="">
</div>

The Mathematical Foundation
The behavior visualized in the simulation is grounded in the mathematical framework of dynamical systems. The paper elegantly formalizes development with a general equation, capturing how the phenotypic state, x, changes over time.


 $$
\dot{x}=f(t,x,\lambda), x(t_{0})=x_{0}
 $$


This equation states that the rate of change of the phenotype (x˙) is a function, f, of time (t), the current phenotype itself (x), and a set of developmental parameters (λ) which can be genetic or environmental.



The framework then allows us to predict the effect of a small perturbation (a change in λ) on the phenotype. This is described by the sensitivity vector, s_λ(t), which quantifies the direction and magnitude of the phenotypic change.

 $$
s_{\lambda}(t)=\frac{\partial x(t,\lambda)}{\partial\lambda}|_{\lambda=\lambda^{*}}
 $$

The simulation specifically uses a GRN model, where the change in gene expression for each gene i is a function of regulatory inputs from other genes and the environment. This is a concrete implementation of the general function f.

 <summary>Gene Regulatory Network Dynamics</summary>
 $$
\dot{x}{i}=\frac{r(b{i})}{K_{i}+r(b_{i})}-\mu_{i}x_{i}; b_{i}=\sum_{j=1}^{n}\theta_{j}x_{j}+u_{j}
 $$

Here, the change in expression x˙∗i depends on Michaelis-Menten dynamics, a degradation rate μ∗i, and the total regulatory input b_i, which is a sum of effects from all other genes (θ_ijx_j) and the environment (u_j).


Discussion
This simulation provides a powerful, visual confirmation of the core thesis presented by Milocco and Uller. By observing the interplay between the reference (genetic) and expressed (plastic) phenotypes, we can see how the immediate response to the environment provides a "look-ahead" for the direction of future genetic adaptation. The alignment between the plastic response vector and the eventual vector of genetic change is not a coincidence but a predictable outcome of the underlying developmental dynamics.


By providing a computational sandbox to explore these ideas, this script serves as a valuable tool for building intuition. It reinforces the concept that development is not an inscrutable black box but a structured process whose internal dynamics shape and channel evolution in predictable ways.
