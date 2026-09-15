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
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/CycleSkipping.png" title="CycleSkipping" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2023HomogeneousStartingModelFWI.png" title="Ali2023HomogeneousStartingModelFWI" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2023StartingModelFWI.png" title="Ali2023StartingModelFWI" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Cycle Skipping in FWI.  (Top Left) Schematic.  (Top Right) Transcranial UST simulation where cycle skipping occur starting at 300 kHz but not 100 kHz {% cite Ali2023HomogeneousStartingModelFWI %}.  (Bottom) Emergence of artifacts as the starting frequency of FWI increases in a breast UST simulation {% cite Ali2023StartingModelFWI %}.
</div>



<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/FrequencyDifferenceFWI.png" title="FrequencyDifferenceFWI" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2024FrequencyDifferenceFWI.png" title="Ali2024FrequencyDifferenceFWI" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Frequency-Difference FWI (FD-FWI) Overcomes Cycle Skipping in Simulations and Phantom Experiments {% cite Ali2024FrequencyDifferenceFWI %}.  Data-domain frequency differencing refers to the generation of low-frequency data via frequency-differencing without changing the FWI forward model.  Data domain frequency differencing was performed using multiple frequency pairs.  On the other hand, model-domain frequency differencing (or FD-FWI) incorporates frequency differencing directly into the forward model.  However, the initial implementation of model-domain frequency differencing was restricted to a single frequency pair due to computational complexity; this ultimately limited the stability of model-domain frequency differencing.  Later, FD-FWI was reimplemented using multiple frequency pairs {% cite Klaben2026JAX %}, improving the stability of FD-FWI.
</div>



<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/FrequencyDifferencingInSilico.png" title="FrequencyDifferencingInSilico" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/FrequencyDifferencingInVitro.png" title="FrequencyDifferencingInVitro" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2025FrequencyDifferencing.png" title="Ali2025FrequencyDifferencing" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/TranscranialFrequencyDifferencing.png" title="TranscranialFrequencyDifferencing" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2024FrequencyDifferencing.png" title="Ali2024FrequencyDifferencing" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Data-Domain Frequency-Differencing Method to Kickstart FWI Without Cycle Skipping {% cite Ali2024FrequencyDifferencing Ali2025FrequencyDifferencing %}.
</div>



<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/LowFrequencyExtrapolation.png" title="LowFrequencyExtrapolation" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Owolabi2026LowFrequencyExtrapolation.png" title="Owolabi2026LowFrequencyExtrapolation" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Least-Squares Autoregressive Model for Low-Frequency Extrapolation to Overcome Cycle Skipping in FWI {% cite Owolabi2026LowFrequencyExtrapolation %}.
</div>





<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/FDFWI.png" title="FDFWI" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/AWI.png" title="AWI" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Cycle-Skipping-Robust FWI Techniques: Frequency-Difference Full-Waveform Inversion (FD-FWI) vs. Adaptive Waveform Inversion (AWI) {% cite Klaben2026JAX %}.
</div>





<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Klaben2026JAX_BreastOnly.png" title="Klaben2026JAX_BreastOnly" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Frequency-Difference Full-Waveform Inversion (FD-FWI) and Adaptive Waveform Inversion (AWI) vs Conventional FWI in Numerical Breast Phantom at 400 kHz {% cite Klaben2026JAX %}.
</div>





<div class="row justify-content-sm-center">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/NumericalBrainPhantom.png" title="NumericalBrainPhantom" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/NumericalBrainPhantomResults.png" title="NumericalBrainPhantomResults" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Frequency-Difference Full-Waveform Inversion (FD-FWI) and Adaptive Waveform Inversion (AWI) vs Conventional FWI in Numerical Transcranial Imaging Phantom at 100 and 200 kHz {% cite Klaben2026JAX Singh2026TranscranialUST Mitcham2025TranscranialUST Ali2023HomogeneousStartingModelFWI %}.
</div>







<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/OtherCycleSkippingRobustTechniques.png" title="OtherCycleSkippingRobustTechniques" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Other Proposed Cycle-Skipping Robust Formulations of FWI: (1) Optimal Transport, (2) Learned Low-Frequency Extrapolation, and (3) Learning the Optimal Transformation of the Ultrasound Signal.
</div>
