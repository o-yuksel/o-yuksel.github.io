---

layout: page

title: "An In Silico Exploration of Developmental Bias and Evolutionary Trajectories"

description: "A computational model that visualizes how differences in a founder genotype's developmental bias affect the speed and direction of multiple, independent evolutionary trajectories."

img: assets/img/publication_preview/MutationRace.webp

importance: 1

category: work

related_publications: true

selected: true

---



A central goal in evolutionary biology is to understand how the generative process of development constrains or facilitates adaptive change by shaping the phenotypic variation available to selection. While quantitative genetics often approximates this relationship with linear models, research in evolutionary developmental biology (evo-devo) has highlighted the profoundly complex and nonlinear nature of the Genotype-Phenotype Map (GPM). These nonlinearities can lead to the rapid evolution of heritable variance (Milocco and Salazar-Ciudad, 2022) and can cause predictions from linear models to fail (Milocco and Salazar-Ciudad, 2020).



A powerful alternative is to model development mechanistically as a dynamical system, providing a "bottom-up" framework to predict the effects of perturbations (Milocco and Uller, 2024). This project, uses this framework to visually explore a key question: how do differences in the initial developmental bias of a founder organism affect the subsequent speed and direction of multi-lineage evolution?



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

Figure 2 shows the animation from a run with the Founder pupolation. The blue arrow is the predicted sensitivity vector for an epoch, the red is the evolving reality, and a white diamond marks the Forecast Horizon.

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



The animation's core mechanic—the **Forecast Horizon**—provides a tangible basis for the decay of evolutionary predictability. An epoch ends not after a fixed time, but when the system's internal dynamics have changed significantly, measured by the deviation of the current sensitivity vector from the initial prediction

$$

||s_{current} - s_{start}|| / ||s_{start}|| > 0.25

$$

This visually connects the macroscopic pattern of evolution to the microscopic changes in the underlying developmental rules, reinforcing the idea that evolvability is not a static property but is itself an evolving feature of the system.

Models like this one serve as a crucial bridge between the formal mathematical theory of developmental dynamics and a more intuitive, visual grasp of its evolutionary consequences. By visualizing the evolution of the sensitivity map, the simulation reinforces the concept that development is not an inscrutable black box but a structured, generative process that imposes predictable biases on the variation available to selection. This framework's ability to mechanistically link plasticity with evolvability moves beyond simple forecasting and opens new avenues for exploring the concept of **evolutionary control**, where a deep understanding of developmental rules could be used to guide or accelerate adaptation.

{% raw %}

```text
//=========================================================================
// ALGORITHM: Mechanistic Forecasting of Evolutionary Trajectories
//=========================================================================

// --- 1. System Initialization ---
params <- Load_Configuration_Data()
founder_genotype <- Initialize_Founder_GRN(params.seed_type)
lineages[1...N] <- Create_Initial_Lineages(founder_genotype, params.n_lineages)

// --- 2. Static Analysis of Initial Potential ---
initial_sensitivity_map <- Characterize_Full_Potential(lineages[1].population)
Generate_Figure_1(initial_sensitivity_map, lineages)

// --- 3. Headless Simulation Pass ---
FOR gen = 1 TO params.n_generations
    active_count <- 0
    FOR each lineage IN lineages
        IF lineage.is_active
            active_count <- active_count + 1
            Evolve_One_Generation(lineage)
            
            IF Is_Check_Interval(gen)
                s_current <- Calculate_On_Axis_Sensitivity(lineage)
                change_score <- Compare_Sensitivity(s_current, lineage.s_start_of_epoch)
                
                IF change_score >= params.threshold
                    Update_For_New_Epoch(lineage, gen, s_current)
                END IF
            END IF
        END IF
    END FOR
    
    IF active_count == 0, BREAK
END FOR
max_gen_reached <- gen

// --- 4. Animation Replay Pass ---
axis_bounds <- Determine_Axis_Bounds(lineages)
handles <- Setup_Animation_Figure(axis_bounds)

FOR gen = 1 TO max_gen_reached
    Update_Animation_Frame(handles, lineages, gen)
    Save_GIF_Frame()
END FOR
Finalize_Animation_Frame(handles, max_gen_reached)

// --- 5. Final Trajectory Analysis ---
distances <- Calculate_Trajectory_Distances(lineages)
Print_Final_Results(distances)

//=========================================================================
```

{% endraw %}

### References

Milocco, L., and Salazar-Ciudad, I. (2020). Is evolution predictable? Quantitative genetics under complex genotype-phenotype maps. *Evolution, 74*(2), 230-244.



Milocco, L., and Salazar-Ciudad, I. (2022). Evolution of the G Matrix under Nonlinear Genotype-Phenotype Maps. *The American Naturalist, 199*(3).



Milocco, L., and Uller, T. (2024). Utilizing developmental dynamics for evolutionary prediction and control. *PNAS, 121*(14).



Uller, T., Milocco, L., Isanta-Navarro, J., Cornwallis, C. K., and Feiner, N. (2024). Twenty years on from Developmental Plasticity and Evolution: middle-range theories and how to test them. *Journal of Experimental Biology, 227*.
