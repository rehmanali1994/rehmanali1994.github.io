---
layout: page
title: 3D FWI
description: Fast, scalable, and accurate implementations/approximations of the 3D wave equation + UST/USCT systems to support 3D FWI
img: assets/img/MultiRowRingArray.png
importance: 3
category: Full-Waveform Inversion (FWI) for UST/USCT
related_publications: true
---


<div class="row justify-content-sm-center">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/MultiRowRingArray.png" title="MultiRowRingArray" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/MultiRowRingArrayDesign.png" title="MultiRowRingArrayDesign" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Multi-Row Ring-Array Transducer Design.
</div>



<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2025_3DFWI.png" title="Ali2025_3DFWI" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Comparison of 2D slicewise to 3D FWI with simulated multi-row ring array {% cite Ali2025_3DFWI %}. Cylindrical wave transmits from a multi-row ring-array (32 rows; 256 elements per row; 22 cm diameter; 2.4 mm between rows) were simulated in three different numerical breast phantoms. Orthographic slice views of the reconstructed volumes intersect at suspicious high sound speed masses in each phantom (cancers in phantoms 1 and 2, and dense breast tissue in phantom 3). Each sound speed images is displayed in grayscale from 1400 to 1600 m/s: (Left Column) ground-truth sound speed image; (Middle Column) volume reconstructed using 2D slicewise FWI; (Right Column) volume reconstructed using 3D FWI.
</div>



<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/HelmholtzMatrixBlocks.png" title="HelmholtzMatrixBlocks" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/HelmholtzMatrixBlockLU.png" title="HelmholtzMatrixBlockLU" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/HelmholtzMatrixApplyLU.png" title="HelmholtzMatrixApplyLU" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2024OneWayDecomposition.png" title="Ali2024OneWayDecomposition" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Block LU Factorization of the Helmholtz Equation and Its Interpretation as a Cascade of One-Way Sweeps {% cite Ali2024_BlockLU_2DFWI %}.
</div>




<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/OneWayLU.png" title="OneWayLU" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/OneWayLUvsBlockLU.png" title="OneWayLUvsBlockLU" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    One-Way Wave Equations as the PDE-Equivalent of the LU Decomposition {% cite Ali2024OneWayDecomposition %}.  Phase-shift-plus-interpolation (PSPI) is an extension of the Fourier split-step method used to implement the one-way wave equations more accurately.  This numerical method could lead to a much more memory and computation efficient implementation of 3D FWI.
</div>



