---
layout: page
title: Wave-Equation Migration
description: Reverse-Time Migration, Fourier/Stolt Mapping, and Frequency-Domain Beamforming
img: assets/img/Siemens5C1_TimeDomain.gif
importance: 3
category: Pulse-Echo Ultrasound
related_publications: true
---



<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2021FourierSyntheticAperture.gif" title="Ali2021FourierSyntheticAperture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/FieldII_TimeDomain.gif" title="FieldII_TimeDomain" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Reverse-Time Migration based on the Time-Domain Cross-Correlation of Transmitted and Backpropagated Receive Wavefields {% cite Ali2020WavefieldCorrelation %}.  This wave-propagation-based imaging framework for pulse-echo ultrasound generalizes across imaging geometries and transmit schemes.  (Top) Focused transmission from a linear array {% cite Ali2021FourierSyntheticAperture %}.  (Bottom) Single-element diverging-wave transmit from a curvilinear array {% cite Ali2022CurvilinearAngularSpectrumMethod %}.
</div>




<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Siemens5C1_TimeDomain.gif" title="Siemens5C1_TimeDomain" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/FocusedTxSyntheticAperture.png" title="FocusedTxSyntheticAperture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Curvilinear Extension of the Angular Spectrum Method Used in Reverse-Time Migration and its Application to Abdominal (Liver + Kidney) Imaging {% cite Ali2022CurvilinearAngularSpectrumMethod %}.
</div>




<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Ali2026FourierBeamforming_Poster.png" title="Ali2026FourierBeamforming_Poster" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Fast Fourier Beamforming for Arbitrary Ultrasound Imaging Sequences Based on a K-Space Implementation of Reverse-Time Migration {% cite Ali2026FourierBeamforming %}.
</div>





<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2026DifferentiableRTM.gif" title="Ali2026DifferentiableRTM" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/PhantomVSX4_2.gif" title="PhantomVSX4_2" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Wave-Equation Migration Velocity Analysis (WEMVA) for Sound Speed Estimation and Aberration Correction.  Reverse-time migration (RTM) is also known as wave-equation migration (WEM); both terminologies come from seismic imaging.  When RTM is differentiated with respect to sound speed and used to minimize aberrations in the image, the resulting form of diffraction tomography becomes WEMVA, also known as differentiable RTM in the ultrasound imaging community.  (Left) My initial adaptation of WEMVA to medical pulse-echo ultrasound was based on minimizing the difference between partial images from individual transmissions {% cite Ali2026DifferentiableRTM %}.  (Right) Later, I introduced the subsurface-offset form of WEMVA, the modern form of WEMVA in seismic imaging that overcomes the inherent Fourier uncertainty principles associated with sound speed estimation and aberration correction {% cite Ali2026WEMVA %}.  Both animation correspond to channel data from the same phantom experiment—subsurface-offset WEMVA yields better aberration corrections in fewer iterations than image-difference WEMVA.
</div>




