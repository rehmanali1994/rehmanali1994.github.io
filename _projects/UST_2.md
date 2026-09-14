---
layout: page
title: Making FWI Robust Against False Minima
description: Variants of FWI robust against false minima caused by cycle skipping
img: assets/img/CycleSkipping.png
importance: 3
category: Full-Waveform Inversion (FWI) for UST/USCT
related_publications: true
---


<div class="row justify-content-sm-center">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/CycleSkipping.png" title="CycleSkipping" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2023HomogeneousStartingModelFWI.png" title="Ali2023HomogeneousStartingModelFWI" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2023StartingModelFWI.png" title="Ali2023StartingModelFWI" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Cycle Skipping in FWI.  (Top Left) Schematic.  (Top Right) Transcranial UST simulation where cycle skipping occur starting at 300 kHz but not at 100 kHz {% cite Ali2023HomogeneousStartingModelFWI %}.  (Bottom) Emergence of cycle skipping artifacts as the starting frequency of FWI increases in a breast UST simulation {% cite Ali2023StartingModelFWI %}.
</div>
