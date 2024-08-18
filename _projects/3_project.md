---
layout: page
title: Stable state finder
description:
img: assets/img/publication_preview/stable.webp
importance: 1
category: work
related_publications: false

---
Evolutionary stability analysis is performed with successive forward simulations:

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/methodfores.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
</div>
<div class="">
</div>

In order to find the equilibrium frequencies of the player types we need to find the attractors of the system which corresponds to the Evolutionarily stable states. The attractors are dependent on the initial frequencies of the player types. Here, the attractors of the system are found by analyzing different sets of initial frequencies. Each arrangement of initial frequencies is used as initial condition and simulated for specified time. If the end frequencies have differed from the initial frequencies than the end frequencies are used as initial conditions for the next simulation. If the end frequencies are the same as the input frequencies than it is concluded that the system has reached to the steady state.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/stable.webp" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Blue strategy starts with %99 frequency in the first subplot, %1 frequency in the second. The arrow indicates the frequency that current simulation (xy plane) partakes in.
</div>
<div class="">
</div>
