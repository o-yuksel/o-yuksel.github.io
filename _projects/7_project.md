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
    <a href="[https://github.com/o-yuksel/evolutionary-trajectory-simulation](https://github.com/o-yuksel/evolutionary-trajectory-simulation/blob/cb27ff9f45c34e3029d3cd67f90dba058b0a2d0d/src/evolutionary_trajectory_sim.m)">
        <img src="https://img.shields.io/badge/MATLAB-R2019b+-orange?style=flat-square&logo=mathworks" alt="MATLAB">
    </a>
        <a href="[https://github.com/o-yuksel/evolutionary-trajectory-simulation](https://github.com/o-yuksel/evolutionary-trajectory-simulation/blob/cb27ff9f45c34e3029d3cd67f90dba058b0a2d0d/src/evolutionary_trajectory_sim.py)">
        <img src="https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=fff)" alt="python">
    </a>
</div>

A central goal in evolutionary biology is to understand how the generative process of development constrains or facilitates adaptive change by shaping the phenotypic variation available to selection. While quantitative genetics often approximates this relationship with linear models, research in evolutionary developmental biology (evo-devo) has highlighted the profoundly complex and nonlinear nature of the Genotype-Phenotype Map (GPM). These nonlinearities can lead to the rapid evolution of heritable variance (Milocco and Salazar-Ciudad, 2022) and can cause predictions from linear models to fail (Milocco and Salazar-Ciudad, 2020).

A powerful alternative is to model development mechanistically as a dynamical system, providing a "bottom-up" framework to predict the effects of perturbations (Milocco and Uller, 2024). This project uses this framework to visually explore a key question: how do differences in the initial developmental bias of a founder organism affect the subsequent speed and direction of multi-lineage evolution?


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

#### Developmental Bias Shapes Evolutionary Trajectories
The simulation is initialized with a founder GRN that has balanced, symmetric sensitivity, meaning there is no strong pre-existing "grain" favoring one direction of evolution over another. However, a subtle bias does emerge from the inherent nonlinearity of the system's Michaelis-Menten kinetics. This creates a slight preference for lower gene expression levels, which can be seen in the slightly longer trajectories of lineages evolving downwards and to the left. This demonstrates that even without major engineered constraints, the fundamental properties of the underlying developmental system can still introduce subtle and predictable asymmetries into evolution.

#### The Forecast Horizon: Where Prediction Fails
One of the most important conceptual contributions of this framework is the Forecast Horizon, which provides a mechanistic explanation for why evolutionary prediction inevitably breaks down. Unlike traditional models that assume constant genetic architectures, this simulation explicitly tracks how the developmental system itself evolves.

An epoch ends not arbitrarily, but when the system's internal dynamics have fundamentally changed:

$$
||s_{current} - s_{start}|| / ||s_{start}|| > 0.25
$$

This 25% threshold marks the point where the original sensitivity vector, our prediction of how the system will respond to mutations, has become unreliable. The developmental landscape has been reshaped by evolution itself. This creates a natural limit to predictability. We can forecast evolution accurately within an epoch, but as the GRN structure changes, new sensitivities emerge and old predictions fail.

The white diamonds in our animation mark these Forecast Horizons, moments when evolution has fundamentally restructured the rules governing what variation is possible. This visually reinforces a key insight: the developmental system and evolutionary trajectory co-evolve, each reshaping the other in an ongoing dance.

#### Evolvability as an Evolving Property
Perhaps the most striking feature visible in the trajectories is that evolvability itself evolves. Each epoch change marks not just a new position in phenotype space, but a reorganization of the system's capacity to generate future variation. As regulatory connections strengthen or weaken, new sensitivities emerge. What was once difficult to evolve may become easy; what was once evolvable may become constrained.

This has profound implications for understanding long-term evolution. Organisms are not static bundles of traits being shaped by external selection. They are active participants in their own evolution, with developmental systems that determine not just what they are, but what they can become. The GRN is simultaneously the object of evolution and the generator of evolutionary potential.

#### Bridging Theory and Intuition
Models like this one serve as a crucial bridge between formal mathematical theory and intuitive understanding. The dynamical systems framework (with its Jacobian matrices, sensitivity vectors, and differential equations) can seem abstract and impenetrable. But when we visualize trajectories fanning out across phenotype space, when we see sensitivity vectors rotating as epochs change, and when we watch the lineages progress, the mathematics becomes tangible.

The simulation reinforces the concept that development is not an inscrutable black box but a structured, generative process that imposes predictable, if temporary, biases on the variation available to selection. By making the invisible visible, transforming abstract developmental dynamics into concrete evolutionary trajectories, this tool helps build intuition about how mechanistic processes at one level (gene regulation) constrain and facilitate outcomes at another (phenotypic evolution).

---


### References

Milocco, L., and Salazar-Ciudad, I. (2020). Is evolution predictable? Quantitative genetics under complex genotype-phenotype maps. *Evolution, 74*(2), 230-244.

Milocco, L., and Salazar-Ciudad, I. (2022). Evolution of the G Matrix under Nonlinear Genotype-Phenotype Maps. *The American Naturalist, 199*(3).

Milocco, L., and Uller, T. (2024). Utilizing developmental dynamics for evolutionary prediction and control. *PNAS, 121*(14).

Uller, T., Milocco, L., Isanta-Navarro, J., Cornwallis, C. K., and Feiner, N. (2024). Twenty years on from Developmental Plasticity and Evolution: middle-range theories and how to test them. *Journal of Experimental Biology, 227*.
