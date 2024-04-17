---
layout: page
title: Gradual Evolution of Cancer into Resistant States
description:
img: assets/img/publication_preview/nsclcs.webp
importance: 1
category: work
related_publications: false

---
Resistance mechanisms can occur as alternate states that are independent of the index oncogenic pathway. These mechanisms confer drug resistance even when the index drug target and its downstream outputs are continuously inhibited (represented by "Alternate oncogenic output" in the figure). In other words, although we may effectively block one oncogenic pathway, there might be an alternative pathway that promotes tumor progression.

In certain cases, another drug may be effective against the alternate cell state. This line of thinking has potential benefits. Current models assume that all acquired resistance is against our chosen drug, which is true. However, the tumor may become sensitive to another drug, providing us with additional options for optimizing adaptive therapy.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/nsclcs.webp" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    EGFR-mutated NSCLC with osimertinib, followed by histologic transformation to SCLC, and ultimately incorporating chemotherapy and its corresponding evolution of resistance. Circle size corresponds to the population size.
</div>
<div class="">
</div>

To accommodate these considerations, I had to incorporate at least two cell states. Creating two separate G-functions and segregating populations from each other posed challenges: The frequency of the phenotype would only be affected by growth and death rates. However, we want to include the de novo acquisition of states, as cells should be able to change their state depending on drug exposure. Furthermore, at the population level, we would observe a mixture of cell states, so I assumed it is a continuous trait on population level.

Histologic transformations occur in approximately 10-15% of patients. Additionally, there are other resistance mechanisms to osimertinib, such as HER2 amplification and MET amplification, which are also frequently observed. These mechanisms are typically treated with immunotherapy and molecular targeted therapy, respectively.
