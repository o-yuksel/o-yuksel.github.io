---
layout: page
title: Self developing strategies with trait correlations in adaptive landscapes
description:
img: assets/img/publication_preview/long.webp
importance: 1
category: work
related_publications: false

---

How ecologically relevant (Qualitative) types arise from vast space of quantitative field of genotypes? (e.g. De-novo mutations in cancer)

Introducing developmental mechanisms into well-defined evolutionary models, both as enabling and disabling constraints, may provide valuable insights and help us find the answers we seek.

During development, organisms form a distributed associative memory that allows for the "storage" and "recall" of multiple past phenotypes. This capability enables the accurate reconstruction of complete adult phenotypic patterns, even from partial or corrupted embryonic phenotypes. Additionally, this system "generalizes" by utilizing evolved developmental modules to generate new combinations of phenotypic features  (Richard A. Watson1 and Eörs Szathmáry, 2016).
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/GRN.png" title="LV" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Figure 1. A Recurrent Gene Regulation Network (GRN) Evolved in a Dynamic Environment Demonstrates Associative Learning (Richard A. Watson1 and Eörs Szathmáry, 2016).
    The evolution of connections within a GRN follows Hebbian learning principles, resulting in the network forming an associative memory of previously selected phenotypes. This allows the GRN to spontaneously recreate those phenotypes as developmental attractors and also produce new, generalized phenotypes. (A–D) The GRN is evolved to generate alternating phenotypes: A represents Charles Darwin, and B represents Donald Hebb, the originator of Hebbian learning principles. The phenotypic outcome is not simply a blend of the two selected patterns. Instead, various embryonic phenotypes (e.g., random starting conditions C and D) develop into distinct adult phenotypes that align with either A or B. These phenotypes can arise from genotypes differing by a single mutation. (E–J) In a separate trial, selection alternates through a series of target phenotypes (E–H). The GRN develops phenotypes matching previously selected patterns (e.g., I), but also generalizes by producing novel phenotypes structurally related to the selected ones. For example, it combines evolved modules to form a developmental attractor for a phenotype featuring all four loops (J). This illustrates how evolution can generate phenotypic novelty, similar to how neural networks generalize from past learning experiences.
</div>
<div class="">
</div>


In this work, I aim to develop new models that incorporate trait variation, non-linear trait correlations, and frequency-dependent fitness. My hypothesis is that players will acquire abilities, such as recalling and innovating their own strategies, by leveraging previous associations.

In this example, two identical populations engage in a Lotka-Volterra Big Bully Game within a symmetrical setting. The initial traits and sizes of these populations determine how they impact one another—for instance, a larger population tends to bully the smaller one. 
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

References

How Can Evolution Learn?
Watson, Richard A. et al.
Trends in Ecology & Evolution, Volume 31, Issue 2, 147 - 157
