---
layout: page
title: "An In Silico Exploration of Developmental Bias and Evolutionary Trajectories"
description: "A computational model that visualizes how differences in a founder genotype's developmental bias affect the speed and direction of multiple, independent evolutionary trajectories."
img: assets/img/publication_preview/MutationRace.webp
importance: 1
category: work
related_publications: false
selected: true
github: https://github.com/yourusername/evolutionary-trajectory-simulation
---

<div class="badges" style="margin-bottom: 20px;">
    <a href="https://github.com/o-yuksel/evolutionary-trajectory-simulation">
        <img src="https://img.shields.io/badge/GitHub-Code-blue?style=flat-square&logo=github" alt="GitHub">
    </a>
    <a href="https://github.com/o-yuksel/evolutionary-trajectory-simulation">
        <img src="https://img.shields.io/badge/MATLAB-R2019b+-orange?style=flat-square&logo=mathworks" alt="MATLAB">
    </a>
</div>

A central goal in evolutionary biology is to understand how the generative process of development constrains or facilitates adaptive change by shaping the phenotypic variation available to selection. While quantitative genetics often approximates this relationship with linear models, research in evolutionary developmental biology (evo-devo) has highlighted the profoundly complex and nonlinear nature of the Genotype-Phenotype Map (GPM). These nonlinearities can lead to the rapid evolution of heritable variance (Milocco and Salazar-Ciudad, 2022) and can cause predictions from linear models to fail (Milocco and Salazar-Ciudad, 2020).

A powerful alternative is to model development mechanistically as a dynamical system, providing a "bottom-up" framework to predict the effects of perturbations (Milocco and Uller, 2024). This project uses this framework to visually explore a key question: how do differences in the initial developmental bias of a founder organism affect the subsequent speed and direction of multi-lineage evolution?

## Interactive Demo & Code

<div class="repo-card" style="border: 1px solid #ddd; border-radius: 8px; padding: 20px; margin: 20px 0; background: #f8f9fa;">
    <div style="display: flex; align-items: center; margin-bottom: 15px;">
        <svg height="24" width="24" viewBox="0 0 16 16" style="margin-right: 10px;">
            <path fill="#24292e" d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"></path>
        </svg>
        <h3 style="margin: 0;">Full Implementation Available</h3>
    </div>
    <p>The complete MATLAB implementation with documentation, examples, and sample outputs is freely available on GitHub.</p>
    <div style="display: flex; gap: 10px; flex-wrap: wrap;">
        <a href="https://github.com/o-yuksel/evolutionary-trajectory-simulation" class="btn btn-primary" style="text-decoration: none;">
            <i class="fab fa-github"></i> View on GitHub
        </a>
        <a href="https://github.com/o-yuksel/evolutionary-trajectory-simulation/archive/refs/heads/main.zip" class="btn btn-secondary" style="text-decoration: none;">
            <i class="fas fa-download"></i> Download ZIP
        </a>
        <a href="https://github.com/o-yuksel/evolutionary-trajectory-simulation/blob/main/docs/usage_guide.md" class="btn btn-info" style="text-decoration: none;">
            <i class="fas fa-book"></i> Documentation
        </a>
    </div>
</div>

### Quick Start

```matlab
% Clone the repository
git clone https://github.com/yourusername/evolutionary-trajectory-simulation.git
cd evolutionary-trajectory-simulation

% Run the simulation
evolutionary_trajectory_sim
```

### The Simulation: A Multi-Lineage Exploration

The model simulates an "evolutionary race" using a Gene Regulatory Network (GRN) as the underlying developmental system. The simulation begins with a seeded GRN that has balanced responsiveness in both horizontal and vertical directions.

From the chosen founder, nine identical lineages are cloned and subjected to selection toward nine different, fixed directional targets. Their evolution is tracked in a series of adaptive "epochs," which end when the system's predictability fails.

<div class="row justify-content-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Initial_Potential_Map.png" title="Figure 1: Initial Sensitivity Map" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Figure 1 shows the full sensitivity map for a founder population.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/MutationRace.webp" title="Figure 2: Animated Multi-Lineage Evolution" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Figure 2 shows the animation from a run with the Founder population. The blue arrow is the predicted sensitivity vector for an epoch, the red is the evolving reality, and a white diamond marks the Forecast Horizon.
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

### Key Features

<div class="row">
    <div class="col-md-6">
        <h4><i class="fas fa-network-wired"></i> Mechanistic GRN Model</h4>
        <p>Implements Michaelis-Menten dynamics for realistic gene regulation</p>
    </div>
    <div class="col-md-6">
        <h4><i class="fas fa-compass"></i> Sensitivity Analysis</h4>
        <p>Calculates developmental potential in all phenotypic directions</p>
    </div>
</div>

<div class="row">
    <div class="col-md-6">
        <h4><i class="fas fa-code-branch"></i> Multi-Lineage Evolution</h4>
        <p>Tracks 9 independent trajectories simultaneously</p>
    </div>
    <div class="col-md-6">
        <h4><i class="fas fa-dna"></i> Targeted Mutagenesis</h4>
        <p>Optional acceleration of specific gene mutations</p>
    </div>
</div>

### Reproducibility & Extensions

All code, parameters, and configurations are version-controlled and documented. The modular design allows researchers to:

- Modify GRN architectures
- Test different selection regimes
- Implement custom mutation schemes
- Export data for further analysis

### Discussion

This simulation provides a clear, visual demonstration of how initial developmental bias can predict and influence long-term evolutionary trajectories (Uller et al., 2024). By comparing the results from the 'Standard Founder' and 'Modified Founder' runs, one can directly observe how the engineered increase in vertical sensitivity leads to dramatically faster adaptation for lineages selected along that axis.

The **Forecast Horizon** provides a tangible basis for the decay of evolutionary predictability. An epoch ends not after a fixed time, but when the system's internal dynamics have changed significantly, measured by the deviation of the current sensitivity vector from the initial prediction

$$
||s_{current} - s_{start}|| / ||s_{start}|| > 0.25
$$

This visually connects the macroscopic pattern of evolution to the microscopic changes in the underlying developmental rules, reinforcing the idea that evolvability is not a static property but is itself an evolving feature of the system.

Models like this one serve as a crucial bridge between the formal mathematical theory of developmental dynamics and a more intuitive, visual grasp of its evolutionary consequences. By visualizing the evolution of the sensitivity map, the simulation reinforces the concept that development is not an inscrutable black box but a structured, generative process that imposes predictable biases on the variation available to selection. This framework's ability to mechanistically link plasticity with evolvability moves beyond simple forecasting and opens new avenues for exploring the concept of **evolutionary control**, where a deep understanding of developmental rules could be used to guide or accelerate adaptation.

---


### References

Milocco, L., and Salazar-Ciudad, I. (2020). Is evolution predictable? Quantitative genetics under complex genotype-phenotype maps. *Evolution, 74*(2), 230-244.

Milocco, L., and Salazar-Ciudad, I. (2022). Evolution of the G Matrix under Nonlinear Genotype-Phenotype Maps. *The American Naturalist, 199*(3).

Milocco, L., and Uller, T. (2024). Utilizing developmental dynamics for evolutionary prediction and control. *PNAS, 121*(14).

Uller, T., Milocco, L., Isanta-Navarro, J., Cornwallis, C. K., and Feiner, N. (2024). Twenty years on from Developmental Plasticity and Evolution: middle-range theories and how to test them. *Journal of Experimental Biology, 227*.
