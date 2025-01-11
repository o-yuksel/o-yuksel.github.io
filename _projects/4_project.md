---
layout: page
title: Self developing strategies with trait correlations in adaptive landscapes
description:
img: assets/img/publication_preview/long.webp
importance: 1
category: work
related_publications: false

---

This project explores how developmental mechanisms shape trait correlations in evolutionary models, with a focus on adaptive landscapes and frequency-dependent fitness.

How do ecologically relevant qualitative traits emerge from the vast quantitative space of genotypes? (e.g. De-novo mutations in cancer).

Introducing developmental mechanisms into well-defined evolutionary models, both as enabling and disabling constraints, may provide valuable insights and help us find the answers we seek.

During development, organisms form a distributed associative memory that allows for the "storage" and "recall" of multiple past phenotypes. This capability enables the accurate reconstruction of complete adult phenotypic patterns, even from partial or corrupted embryonic phenotypes. Additionally, this system "generalizes" by utilizing evolved developmental modules to generate new combinations of phenotypic features  (Richard A. Watson and Eörs Szathmáry, 2016).
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/GRN.png" title="LV" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Figure 1. A Recurrent Gene Regulation Network (GRN) Evolved in a Dynamic Environment Demonstrates Associative Learning (Richard A. Watson1 and Eörs Szathmáry, 2016). (A–D) The GRN evolves to alternate between phenotypes: A (Charles Darwin) and B (Donald Hebb). The phenotypes are not averages of prior patterns but instead distinct adult forms from random embryonic states (C, D), each matching A or B. These phenotypes can differ by just a single mutation. (E–J) In another experiment, the GRN is exposed to multiple target phenotypes (E–H). It not only replicates past phenotypes (e.g., I) but also produces novel combinations (e.g., J). This demonstrates evolution’s ability to generate new phenotypes, akin to how neural networks generalize from prior learning.
</div>
<div class="">
</div>


In this work, I aim to develop new models that incorporate trait variation, non-linear trait correlations, and frequency-dependent fitness. My hypothesis is that players will acquire abilities, such as recalling and innovating their own strategies, by leveraging previous associations.
This work pioneers models that integrate developmental memory and nonlinear trait correlations, providing a new perspective on how populations can evolve adaptive strategies through past experiences.

As my template, two identical populations engage in a Lotka-Volterra Big Bully Game within a symmetrical setting. The initial traits and sizes of these populations determine how they impact one another—for instance, a larger population tends to bully the smaller one. 
# Lotka-Volterra Big Bully Game

The struggle for existence is given by the fitness-generating function (G-function / Darwinian dynamics)

<details>
 <summary>General form</summary>
 $$
  G(\mathbf{v}, \mathbf{u}, \mathbf{x}) \big|_{\mathbf{v} = \mathbf{u}_i}
 $$
</details>

$$
G(\mathbf{v}, \mathbf{u}, \mathbf{x}) = \frac{r}{K(\mathbf{v})} \left[ K(\mathbf{v}) - \sum_{j=1}^r a(\mathbf{v}, \mathbf{u}_j) x_j \right]
$$

<details>
 <summary>Carrying capacity</summary>
 Carrying capacity takes on a maximum value at v =0.The variance oft his distribution, σ2 k , determines the severity with which an individual loses carrying capacity as its strategy deviates from v = 0. With a larger variance, the individual suffers less from a deviation.
</details>

$$
K(\mathbf{v}) = (1 - v_2^2) K_{\text{max}} \exp \left( -\frac{v_1^2}{2\sigma_k^2} \right)
$$

<details>
 <summary>Competition term</summary>
 The competition term is a normal distribution with respect to v and takes on a maximum when v =uj. Its variance, σ2 a, determines how quickly the competition coefficient changes a scompetitors deviate in their strategy values. A large variance means that the competition coefficient changes slowly with changes in v. The term β introduces an asymmetry into the competition. When β>0, an individual with a larger value for v1 has a larger negative effect on an individual with a smaller v1.
</details>

$$
a(\mathbf{v}, \mathbf{u}_j) = 1 + B_j \exp \left[ -\frac{(v_1 - u_{j1} + \beta)^2}{2\sigma_a^2} \right] - \exp \left[ -\frac{\beta^2}{2\sigma_a^2} \right]
$$

<details>
 <summary>The bully function</summary>
 The bully function, describes forms of competition where being slightly larger than your neighbor confers a competitive advantage by reducing the negative effects of others and increasing one’s own negative effect on others.
</details>

$$
B_j = 1 + B_{\text{max}} (u_{j2} - v_2)
$$

Population dynamics:

$$
\frac{dx_i}{dt} = x_i \cdot G \big|_{\mathbf{v} = \mathbf{u}_i}
$$

Strategy dynamics:

$$
\frac{du_i}{dt} = \sigma_i^2 \frac{\partial G}{\partial \mathbf{v}} \big|_{\mathbf{v} = \mathbf{u}_i}
$$

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/publication_preview/lvbigbully.webp" title="LV" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The sizes of the populations are represented by the diameters of their corresponding circles.
</div>
<div class="">
</div>

I've integrated developmental memory into the model, allowing the correlation between traits to be stored as populations evolve toward more optimal conditions. This stored information shapes the future evolution of the populations, reflected as the planes that represent nearby mutants constricts and rotates.

Single step non-linear G-P mapping:

$$
p_{u_i} = u_i + \tau_1 \tanh(c \cdot u_j) - \tau_2 u_i
$$

Additional dynamics for trait correlation:

$$
\frac{dc}{dt} = (0.066 \cdot \sigma_i^2) \frac{dG}{dc}
$$

In the first scenario, the traits of the populations are near their equilibrium points, resulting in little to no evolution of trait correlations.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/short.webp" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


In the second scenario, the blue population starts from a more distant point. As traits evolve, the trait correlations adjust accordingly. The plane rotates due to the evolving trait correlations and constricts in the middle, reflecting the nonlinear nature of these correlations.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/long.webp" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Populations indicated in blue and yellow share the same 3D seascape, represented by two overlapping 2D landscapes. The omitted Z-plane reflects the correlation between Trait 1 and Trait 2.
</div>
<div class="">
</div>

By integrating developmental memory and trait correlations, this research opens new pathways for understanding how populations evolve complex strategies over time. These models can be applied in diverse fields to better understand and predict the direction of evolution.

References

Watson, R.A. and Szathmáry, E. (2016) ‘How can evolution learn?’, Trends in Ecology &amp; Evolution, 31(2), pp. 147–157. doi:10.1016/j.tree.2015.11.009.
