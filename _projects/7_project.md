---
layout: page
title: "An In Silico Race: How Initial Developmental Bias Shapes Evolutionary Trajectories"
description: "A computational model that visualizes how differences in a founder genotype's developmental bias affect the speed and direction of a multi-lineage evolutionary race."
img: assets/img/publication_preview/FinalRace.gif
importance: 1
category: work
related_publications: true
selected: true
---

A central goal in evolutionary biology is to understand how the generative process of development constrains or facilitates adaptive change by shaping the phenotypic variation available to selection. While quantitative genetics often approximates this relationship with linear models, research in evolutionary developmental biology (evo-devo) has highlighted the profoundly complex and nonlinear nature of the Genotype-Phenotype Map (GPM). These nonlinearities can lead to the rapid evolution of heritable variance (Milocco and Salazar-Ciudad, 2022) and can cause predictions from linear models to fail (Milocco and Salazar-Ciudad, 2020).

A powerful alternative is to model development mechanistically as a dynamical system, providing a "bottom-up" framework to predict the effects of perturbations (Milocco and Uller, 2024). This project, `final_publication_race.m`, uses this framework to visually explore a key question: how do differences in the initial developmental bias of a founder organism affect the subsequent speed and direction of multi-lineage evolution?

### The Simulation: An Evolutionary Race Between Two Founder Types

The model simulates an "evolutionary race" using a Gene Regulatory Network (GRN) as the underlying developmental system. The script can be run in two modes, controlled by a toggle:
1.  **Standard Founder:** The simulation begins with a seeded GRN that has balanced responsiveness in both horizontal and vertical directions.
2.  **Modified Founder:** The simulation begins with the same GRN, but with the specific interaction strength that controls the vertical phenotype ($$x_4$$) doubled. This creates a founder organism with an inherent **developmental bias** toward high vertical evolvability.

From the chosen founder, nine identical lineages are cloned and subjected to selection toward nine different, fixed directional targets. Their evolution is tracked in a series of adaptive "epochs," which end when the system's predictability fails.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Initial_Potential_Map.png" title="Figure 1: Initial Sensitivity Map" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Figure 1 shows the full sensitivity map for a founder population. Running the script in its two different modes will produce two distinct maps; the 'Modified Founder' map would show visibly longer vectors along the vertical axis, quantifying its engineered developmental bias.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/FinalRace.gif" title="Figure 2: Animated Evolutionary Race" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Figure 2 shows the animation from a run with the 'Modified Founder'. The lineages with vertical targets (top-left, top, top-right) travel a much greater distance, demonstrating how the initial developmental bias accelerates adaptation along that axis. The blue arrow is the predicted sensitivity vector for an epoch, the red is the evolving reality, and a white diamond marks the Forecast Horizon.
</div>

### The Mathematical Foundation
The simulation's behavior is grounded in the mathematical framework of dynamical systems, which represents development with a general equation (Milocco and Uller, 2024).

$$
\dot{x}=f(t,x,\lambda)
$$

This equation states that the rate of change of the phenotype ($$\dot{x}$$) is a function, $$f$$, of time ($$t$$), the current phenotype itself ($$x$$), and developmental parameters ($$\lambda$$). The framework allows for the prediction of a perturbation's effect via the **sensitivity vector**, $$s_{\lambda}(t)$$.

$$
s_{\lambda}(t)=\frac{\partial x(t,\lambda)}{\partial\lambda}|_{\lambda=\lambda^{*}}
$$

Our script uses a specific GRN model as a concrete implementation of the function $$f$$, where the change in expression for gene $$i$$ depends on regulatory inputs ($$b_i$$) and Michaelis-Menten dynamics (Milocco and Uller, 2024).

$$
\dot{x}_{i}=\frac{r(b_{i})}{K_{i}+r(b_{i})}-\mu_{i}x_{i}; b_{i}=\sum_{j=1}^{n}\theta_{ij}x_{j}+u_{j}
$$

### Discussion
This simulation provides a clear, visual demonstration of how initial developmental bias can predict and influence long-term evolutionary trajectories (Uller et al., 2024). By comparing the results from the 'Standard Founder' and 'Modified Founder' runs, one can directly observe how the engineered increase in vertical sensitivity leads to dramatically faster adaptation for lineages selected along that axis.

The animation's core mechanic—the **Forecast Horizon**—provides a tangible basis for the decay of evolutionary predictability. An epoch ends not after a fixed time, but when the system's internal dynamics have changed significantly, measured by the deviation of the current sensitivity vector from the initial prediction ($$||s_{current} - s_{start}|| / ||s_{start}|| > 0.25$$). This visually connects the macroscopic pattern of evolution to the microscopic changes in the underlying developmental rules, reinforcing the idea that evolvability is not a static property but is itself an evolving feature of the system.

### References
Milocco, L., and Salazar-Ciudad, I. (2020). Is evolution predictable? Quantitative genetics under complex genotype-phenotype maps. *Evolution, 74*(2), 230-244.

Milocco, L., and Salazar-Ciudad, I. (2022). Evolution of the G Matrix under Nonlinear Genotype-Phenotype Maps. *The American Naturalist, 199*(3).

Milocco, L., and Uller, T. (2024). Utilizing developmental dynamics for evolutionary prediction and control. *PNAS, 121*(14).

Uller, T., Milocco, L., Isanta-Navarro, J., Cornwallis, C. K., and Feiner, N. (2024). Twenty years on from Developmental Plasticity and Evolution: middle-range theories and how to test them. *Journal of Experimental Biology, 227*.