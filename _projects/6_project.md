---
layout: page
title: "Visualizing Modes of Adaptation in a Changing World"
description: "A simulation demonstrating how the pace of environmental change dictates whether a population adapts through slow genetic assimilation or rapid phenotypic plasticity."
img: assets/img/publication_preview/Scenario1_Slow_Speed.webp
importance: 1
category: work
related_publications: true
selected: true
---

A key challenge in biology is to understand how the process of development shapes the phenotypic variation that natural selection can act upon. One powerful approach is to represent development as a dynamical system to reveal the underlying logic of how this variation is generated (**Milocco and Uller, 2024**). This in-silico experiment provides a dynamic visualization of these principles by exploring a critical question: how does the **pace** of environmental change affect a population's **mode** of adaptation?

### The Simulation: Genetic Assimilation vs. Plasticity

The script uses a population-based genetic algorithm where a Gene Regulatory Network (GRN) must adapt to a moving environmental optimum. This setup allows us to explore how a population copes with different rates of environmental change.

The animations below show a direct comparison between two scenarios. We can observe three key elements:

* **The Optimum (red 'x')**: The ideal phenotype dictated by the environment at each generation.
* **The Average Reference Phenotype (green square)**: The population's genetically determined state in a neutral environment. Its movement represents genetic adaptation.
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

### Mathematical Foundation

The simulation is grounded in two core mathematical components: the GRN's developmental dynamics and the evolutionary fitness model.

1.  **GRN Dynamics**: Development is modeled as a dynamical system where the change in gene expression ($$\dot{x}_i$$) for each gene is a function of regulatory inputs from other genes ($$\theta_{ij}$$) and the environment ($$u_j$$). The script numerically integrates the following differential equation to find the steady-state phenotype:
    $$
    \dot{x}_{i}=\frac{r(b_{i})}{K_{i}+r(b_{i})}-\mu_{i}x_{i}; \quad b_{i}=\sum_{j=1}^{n}\theta_{ij}x_{j}+u_{j}
    $$

2.  **Evolutionary Fitness**: Selection is modeled using a Gaussian fitness function. An individual's fitness ($$w$$) decreases exponentially with the squared Euclidean distance ($$d^2$$) between its phenotype and the moving optimum. Individuals are selected as parents for the next generation with a probability proportional to their fitness.
    $$
    w = e^{-k \cdot d^2}
    $$

### Discussion

This comparative simulation provides a powerful, visual demonstration of how the rate of environmental change dictates a population's adaptive strategy (**Uller et al., 2024**). Under slow, predictable change, the population relies on **genetic assimilation**, where its underlying genetics gradually evolve to match the environment. Under rapid change, however, this process is too slow. Survival depends on leveraging existing **phenotypic plasticity** as a short-term solution to keep pace.

This visually reinforces the concept that plasticity can "take the lead" in adaptive evolution, serving as a crucial first step that allows a population to persist in a new environment while slower genetic changes follow.

{% raw %}
```plaintext
//=========================================================================
// ALGORITHM: GRN Adaptation to a Moving Optimum
//=========================================================================

// --- 1. System Initialization ---
params <- Load_Configuration_Data()
founder_genotype <- Initialize_Founder_GRN()
initial_population <- Create_Initial_Population(founder_genotype, params.n_pop)

// --- 2. Pre-calculate Environmental Trajectories ---
// For each scenario (e.g., slow_speed, fast_speed):
optimum_path <- Generate_Optimum_Trajectory(params.speed, params.n_generations)
environmental_inputs <- Generate_Environmental_Inputs(optimum_path)

// --- 3. Run Evolutionary Scenarios ---
// For each scenario to be run:
    Run_Scenario(scenario_name, initial_population, optimum_path, environmental_inputs)

// --- Core Evolutionary Function: Evolve_One_Generation ---
FUNCTION Evolve_Population(population, optimum_path, environmental_inputs)
    FOR gen = 1 TO params.n_generations
        current_optimum <- optimum_path[gen]
        current_env_input <- environmental_inputs[gen]
        
        // --- 3A. Calculate Fitness ---
        FOR each individual IN population
            // Calculate phenotype with environmental influence (plastic)
            expressed_phenotype <- Find_Steady_State(individual.genotype, current_env_input)
            
            // Calculate phenotype without environmental influence (genetic)
            reference_phenotype <- Find_Steady_State(individual.genotype, neutral_input)
            
            distance_to_optimum <- Euclidean_Distance(expressed_phenotype, current_optimum)
            individual.fitness <- Calculate_Gaussian_Fitness(distance_to_optimum)
            
            // Store results for this generation
            history.expressed_phenotypes[individual] <- expressed_phenotype
            history.reference_phenotypes[individual] <- reference_phenotype
        END FOR
        
        // --- 3B. Reproduction ---
        selected_parents <- Select_Parents_By_Fitness(population)
        new_population <- Create_Offspring(selected_parents, params.mutation_rate)
        population <- new_population
        
        // --- 3C. Visualization & Logging ---
        Update_Animation_Frame(history, gen)
        Save_GIF_Frame()
        
    END FOR
    RETURN population, history
END FUNCTION

//=========================================================================
```
{% endraw %}

### References
Milocco, L., and Uller, T. (2024). Utilizing developmental dynamics for evolutionary prediction and control. PNAS, 121(14).

Uller, T., Milocco, L., Isanta-Navarro, J., Cornwallis, C. K., and Feiner, N. (2024). Twenty years on from Developmental Plasticity and Evolution: middle-range theories and how to test them. Journal of Experimental Biology, 227.
