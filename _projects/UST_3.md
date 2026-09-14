---
layout: page
title: Multiparametric and Elastic FWI
description: Extending the wave physics model and FWI to reconstruct multiple tissue mechanical properties
img: assets/img/kWave_BreastCT.gif
importance: 4
category: Full-Waveform Inversion (FWI) for UST/USCT
related_publications: true
---


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/TransmissionVsReflection.png" title="TransmissionVsReflection" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Transmission vs Reflection in UST/USCT. (Left) The transmission of ultrasound through the breast is primarily impacted by sound speed and attenuation. Sound speed primarily affects the shape of the transmitted wavefront by advancing and delaying the wave. Attenuation affect the amplitude of the transmitted wave. (Right) Ultrasound backscatter reflected by the tissue is the result of spatial changes in the impedance Z=ρc (a product of sound speed c and density ρ). Although density has a small impact on the waveform transmitted through tissue, it plays a much more significant role on the backscattered reflections, so we theorize that modeling the reflected ultrasound signals should enable imaging of the mass density in the breast.
</div>



<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/kWave_BreastCT.gif" title="kWave_BreastCT" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/kWave_BreastMRI.gif" title="kWave_BreastMRI" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    FWI Reconstruction of Sound Speed and Attenuation in UST/USCT Simulations {% cite Ali2024_BlockLU_2DFWI %}. 
</div>




<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/VSX_YezitronixPhantom1.gif" title="VSX_YezitronixPhantom1" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/VSX_YezitronixPhantom2.gif" title="VSX_YezitronixPhantom2" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    FWI Reconstruction of Sound Speed and Attenuation in Phantoms {% cite Ali2024_BlockLU_2DFWI %}. 
</div>



<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/BenignCyst.gif" title="BenignCyst" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2024_BlockLU_2DFWI.gif" title="Ali2024_BlockLU_2DFWI" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    FWI Reconstruction of Sound Speed and Attenuation in the Breast {% cite Ali2024_BlockLU_2DFWI %}. (Top) Benign Cyst. (Bottom) Malignancy.
</div>











