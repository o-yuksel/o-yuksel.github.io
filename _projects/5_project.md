---
layout: page
title: A Novel LV-RPS Model in Evolutionary Game Theory
description:
img: assets/img/publication_preview/lvrps2crop.webp
importance: 1
category: work
related_publications: false
selected: true
---

Traditional evolutionary game theory (EGT) often assigns discrete strategies to distinct populations. However, many natural interactions—such as those observed in mutualistic relationships rely on subtle, continuous trait matching. Inspired by recent work on reconciling ecology with EGT (Tarnita and Traulsen, 2024), a new Lotka Volterra Rock, Paper, Scissors model is presented. This framework considers two identical populations, each employing all three strategies as continuous traits, and explores how nuanced trait alignments can drive differential outcomes in competitive interactions.

### Model development
In the novel LV–RPS model, rather than segregating strategies into distinct groups, both populations simultaneously display the strategies, here labeled as R, P, and S as continuous variables. The model defines success in interactions through the alignment of traits, for instance, the first population achieves a competitive edge when its R trait closely matches the opposing population’s S trait, while simultaneously diverging from its P trait.
Two simulation scenarios illustrate the model’s dynamics:

## Scenario One

The simulation begins with the green population’s R trait converging toward the purple population’s S trait. This alignment is quantified by measuring the “distance” between the interacting traits, where a closer match translates to a positive interaction outcome and subsequent growth in the green population.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/publication_preview/lvrps1.webp" title="LV" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="">
</div>

### Scenario Two

Altering the initial trait values produces a different dynamic. In this case, the green population gains an advantage when the green lines are relatively longer than the purple lines, and vice versa.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/publication_preview/lvrps2.webp" title="LV" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="">
</div>


The struggle for existence is given by the fitness-generating function (G-function / Darwinian dynamics) "The G function describes the per capita growth rate of individuals of an evolutionarily identical group, removing the need to define different functions for evolutionarily identical individuals that use different strategies." (Bukkuri and Brown, 2021)

<details>
 <summary>General form</summary>
 $$
  G(\mathbf{v}, \mathbf{u}, \mathbf{x}) \big|_{\mathbf{v} = \mathbf{u}_i}
 $$
</details>

$$
G(\mathbf{v}, \mathbf{u}, \mathbf{x}) = \frac{r}{K} \left[ K - \sum_{j=1}^r a(\mathbf{v}, \mathbf{u}_j) x_j \right]
$$

Competition term

$$
a(\mathbf{v}, \mathbf{u}_j) = 1 + B_j \exp \left[ -\frac{(v_1 - u_{j1} + \beta)^2}{2\sigma_a^2} \right] - \exp \left[ -\frac{\beta^2}{2\sigma_a^2} \right]
$$

Population dynamics:

$$
\frac{dx_i}{dt} = x_i \cdot G \big|_{\mathbf{v} = \mathbf{u}_i}
$$

Strategy dynamics:

$$
\frac{du_i}{dt} = \sigma_i^2 \frac{\partial G}{\partial \mathbf{v}} \big|_{\mathbf{v} = \mathbf{u}_i}
$$

### Discussion

This continuous traits framework extends the application of EGT to phenomena where matching is critical. Trait matching is ubiquitous in nature; one illustrative example is pollination. Successful interactions between pollinators and flowering plants depend on the precise alignment of morphological and phenological traits a concept supported by research showing that such matching enhances the spatio temporal stability and functionality of plant pollinator interactions (Peralta et al., 2020) 

The development of a continuous traits LV–RPS model represents a significant step in extending evolutionary game theory beyond conventional boundaries. Future research in this direction may reveal further nuances in the interplay between ecological dynamics and evolutionary strategies, paving the way for a richer understanding of natural systems.

### References

Bukkuri, A. and Brown, J.S. (2021) ‘Evolutionary game theory: Darwinian dynamics and the g function approach’, Games, 12(4). Available at: https://doi.org/10.3390/g12040072.

Vincent, T.L. and Brown, J.S. (2005) Evolutionary Game Theory, Natural Selection, and Darwinian Dynamics. Cambridge: Cambridge University Press. Available at: https://doi.org/10.1017/CBO9780511542633.

Peralta, G. et al. (2020) ‘Trait matching and phenological overlap increase the spatio-temporal stability and functionality of plant–pollinator interactions’, Ecology Letters, 23(7), pp. 1107–1116. Available at: https://doi.org/10.1111/ele.13510.

Tarnita, C.E. and Traulsen, A. (2024) ‘Reconciling ecology and evolutionary game theory or “When not to think cooperation”’. bioRxiv, p. 2024.07.10.602961. Available at: https://doi.org/10.1101/2024.07.10.602961.
