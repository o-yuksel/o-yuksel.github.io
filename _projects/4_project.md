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

### Ultimate aim

In this work, I aim to develop new models that incorporate trait variation, non-linear trait correlations, and frequency-dependent fitness. My hypothesis is that players will acquire abilities, such as recalling and innovating their own strategies, by leveraging previous associations.
This work pioneers models that integrate developmental memory and nonlinear trait correlations, providing a new perspective on how populations can evolve adaptive strategies through past experiences.

### Proximal aim

For this preliminary work, I limit myself to 2 traits instead of 42 traits that make up Charles Darwin and Donald Hebb's picture. Therefore, I will postpone the desired effects of modularity, such as the use of novel combinations. The problem becomes apparent when there is a game, and the traits have a bearing on each other. We have to clarify how some traits affect others, etc. Therefore, for now, my aim is to create a game where there are genotype and phenotype levels and a non-linear transformation in between.

Here I use two trait Loka-Volterra Big Bully Game as my template, (Vincent and Brown, 2005). The initial traits and sizes of these populations determine how they impact one another—for instance, a larger population tends to bully the smaller one. 

### Lotka-Volterra Big Bully Game

The struggle for existence is given by the fitness-generating function (G-function / Darwinian dynamics) "The G function describes the per capita growth rate of individuals of an evolutionarily identical group, removing the need to define different functions for evolutionarily identical individuals that use different strategies." (Bukkuri and Brown, 2021)

<details>
 <summary>General form</summary>
 $$
  G(\mathbf{v}, \mathbf{u}, \mathbf{x}) \big|_{\mathbf{v} = \mathbf{u}_i}
 $$
</details>


$$
G(\mathbf{v}, \mathbf{u}, \mathbf{x}) = \frac{r}{K(\mathbf{v})} \left[ K(\mathbf{v}) - \sum_{j=1}^r a(\mathbf{v}, \mathbf{u}_j) x_j \right]
$$

Vector-valued strategy has two components. The first component influences both the **carrying capacity** and the **competition coefficient** .The second component, v2, influences both the carrying capacity and the competition coefficients via a **“bully” function**.

<details>
 <summary>Carrying capacity</summary>
 Carrying capacity takes on a maximum value at v =0.The variance oft his distribution, σ2 k , determines the severity with which an individual loses carrying capacity as its strategy deviates from v = 0. With a larger variance, the individual suffers less from a deviation.
</details>


$$
K(\mathbf{v}) = (1 - v_2^2) K_{\text{max}} \exp \left( -\frac{v_1^2}{2\sigma_k^2} \right)
$$

<details>
 <summary>Competition term</summary>
 The competition term is a normal distribution with respect to v and takes on a maximum when v =uj. Its variance, σ2 a, determines how quickly the competition coefficient changes as competitors deviate in their strategy values. A large variance means that the competition coefficient changes slowly with changes in v. The term β introduces an asymmetry into the competition. When β>0, an individual with a larger value for v1 has a larger negative effect on an individual with a smaller v1.
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
   Figure 2. The Lotka-Volterra Big Bully Game.  The sizes of the populations are represented by the diameters of their corresponding circles.
</div>
<div class="">
</div>

I've integrated developmental memory into the model, allowing the correlation between traits to be stored as populations evolve toward more optimal conditions. This stored information shapes the future evolution of the populations, reflected as the planes that represent nearby mutants constricts and rotates.

Single step non-linear G-P mapping: Here I implemented a single step transformation on traits v1 and v2. Assigning original traits as genetic and transformed traits as phenotypic traits. The game is played on the phenotype level, however the evolution is still on the genotypic level as genotypes that lead to succesfull phenotypes rewarded.

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
    <div class="caption">
    Figure 3. Near equilibrium Lotka-Volterra Big Bully Game with non-linear GP mapping. Axes represent genotypes. Populations indicated in blue and yellow share the same 3D seascape, represented by two overlapping 2D landscapes. The omitted Z-plane reflects the correlation between Trait 1 and Trait 2.
</div>
</div>


In the second scenario, the blue population starts from a more distant point. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/long.webp" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
   Figure 4. Far from equilibrium Lotka-Volterra Big Bully Game with non-linear GP mapping. Axes represent genotypes. Populations indicated in blue and yellow share the same 3D seascape, represented by two overlapping 2D landscapes. The omitted Z-plane reflects the correlation between Trait 1 and Trait 2.
</div>
<div class="">
</div>

As traits evolve, trait correlations adjust accordingly. We can observe that the blue population has formed a memory, which is the correlation between its two traits. In turn, the upper plane, which represents nearby mutants, rotates and constricts in the middle, reflecting the nonlinear nature of these correlations. Here, this mechanistic model demosnstrates the influence of natural selection in shaping [developmental bias](https://pubmed.ncbi.nlm.nih.gov/30049818/#&gid=article-figures&pid=figure-2-uid-1), and conversely, the influence of developmental bias in shaping subsequent opportunities for adaptation (Uller et al., 2018). 

### Next steps

In my preliminary attempt to merge Darwinian dynamics with non-linear developmental memory, I focused on a two-trait game and added a third trait as their correlation for simplicity. Although this combination successfully captured both frequency-dependent and developmental dynamics, it was limited to two genetic traits, falling short of encompassing the 42 traits that make up the images of Charles Darwin and Donald Hebb. Consequently, we do not observe modular strategy shifts or the utilization of novel trait combinations. To capture such phenomena, we need frequency-dependent models that account for a broader range of traits, enabling the emergence of novel combinations, correlations, and the apparent strategies observed empirically.

### References

Watson, R.A. and Szathmáry, E. (2016) ‘How can evolution learn?’, Trends in Ecology &amp; Evolution, 31(2), pp. 147–157. doi:10.1016/j.tree.2015.11.009.

Uller, T. et al. (2018) ‘Developmental Bias and Evolution: A Regulatory Network Perspective’, Genetics, 209(4), pp. 949–966. Available at: https://doi.org/10.1534/genetics.118.300995.

Bukkuri, A. and Brown, J.S. (2021) ‘Evolutionary game theory: Darwinian dynamics and the g function approach’, Games, 12(4). Available at: https://doi.org/10.3390/g12040072.

Vincent, T.L. and Brown, J.S. (2005) Evolutionary Game Theory, Natural Selection, and Darwinian Dynamics. Cambridge: Cambridge University Press. Available at: https://doi.org/10.1017/CBO9780511542633.

Watson, R.A. et al. (2014) ‘The Evolution Of Phenotypic Correlations And “Developmental Memory”’, Evolution, 68(4), pp. 1124–1138. Available at: https://doi.org/10.1111/evo.12337.
