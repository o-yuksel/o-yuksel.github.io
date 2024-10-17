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

During development, organisms form a distributed associative memory that allows for the "storage" and "recall" of multiple past phenotypes. This capability enables the accurate reconstruction of complete adult phenotypic patterns, even from partial or corrupted embryonic phenotypes. Additionally, this system "generalizes" by utilizing evolved developmental modules to generate new combinations of phenotypic features.

In this work, I aim to develop new models that incorporate trait variation, non-linear trait correlations, and frequency-dependent fitness. My hypothesis is that players will acquire abilities, such as recalling and innovating their own strategies, by leveraging previous associations.

In this example, two identical populations engage in a Lotka-Volterra Big Bully Game within a symmetrical setting. The initial traits and sizes of these populations determine how they impact one another—for instance, a larger population tends to bully the smaller one. 
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/publication_preview/lvbigbully.webp" title="LV" class="img-fluid rounded z-depth-1" %}
  </div>

I've integrated developmental memory into the model, allowing the correlation between traits to be stored as populations evolve toward more optimal conditions. This stored information shapes the future evolution of the populations, reflected as the planes that represent nearby mutants constricts and rotates.

In the first scenario, the traits of the populations are near their equilibrium points, resulting in little to no evolution of trait correlations.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/short.webp" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The sizes of the populations are represented by the diameters of their corresponding circles.
</div>
<div class="">
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
