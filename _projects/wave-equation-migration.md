---
layout: page
title: Wave-Equation Migration
description: Reverse-Time Migration, Fourier/Stolt Mapping, and Frequency-Domain Beamforming
img: assets/img/Siemens5C1_TimeDomain.gif
importance: 3
category: Pulse-Echo Ultrasound
related_publications: true
---

### Reverse-Time Migration (RTM) for Pulse-Echo Ultrasound

Conventional ultrasound beamforming relies on geometric assumptions about how acoustic waves propagate between the transducer and the imaging target.  Reverse-time migration (RTM) takes a different approach: rather than approximating propagation with delays, it explicitly models the propagation of the transmitted and received wavefields and formulates pulse-echo ultrasound based on the cross-correlation of the transmitted and backpropagated receive wavefields {% cite Ali2020WavefieldCorrelation %}.  The measured channel data are backpropagated through the imaging medium, and the interaction with incident wavefield forms the image.  Because the method models wave propagation directly, the same framework can be applied across different array geometries, transmit schemes, and imaging configurations.  This provides a general wave-propagation framework for pulse-echo imaging rather than a beamformer tied to a particular acquisition sequence.

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
    Reverse-Time Migration based on the Time-Domain Cross-Correlation of Transmitted and Backpropagated Receive Wavefields.  (Top) Focused transmission from a linear array {% cite Ali2021FourierSyntheticAperture %}.  (Bottom) Single-element diverging-wave transmit from a curvilinear array {% cite Ali2022CurvilinearAngularSpectrumMethod %}.
</div>

### Fourier-Domain RTM and its Adaptation to Curvilinear Arrays

Although time-domain RTM provides a general formulation, time-domain wave propagation over the imaging domain can be computation and memory intensive.  Therefore, I developed Fourier-domain formulations that accelerate RTM by performing propagation in the spatial-frequency domain {% cite Ali2021FourierSyntheticAperture %}.  For linear-array imaging, Fourier-domain propagation leads naturally to synthetic-aperture imaging methods that can reconstruct images using frequency-domain operations. The same framework can be extended to different transmit configurations, including focused transmissions, plane-wave and diverging-wave transmissions.

A generalized Stolt mapping provides a particularly efficient formulation of this approach {% cite Ali2026FourierBeamforming %}.  By mapping the measured frequency-domain data onto the appropriate wavenumber coordinates, RTM can be performed using fast Fourier transforms rather than explicit time-domain wave propagation.  The resulting framework connects the physics of RTM with the computational efficiency of Fourier-domain beamforming.

For curvilinear arrays, the geometry of the transducer must be incorporated into the wave-propagation model rather than assuming a planar imaging geometry.  I developed a curvilinear extension of the angular spectrum method, allowing RTM to be applied directly to curved transducer geometries {% cite Ali2022CurvilinearAngularSpectrumMethod %}.  The approach was demonstrated for abdominal imaging, including liver and kidney imaging, where curvilinear arrays are commonly used.  This work showed that the same underlying wave-propagation framework can accommodate substantially different acquisition geometries without changing the fundamental imaging principle.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Siemens5C1_TimeDomain.gif" title="Siemens5C1_TimeDomain" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/FocusedTxSyntheticAperture.png" title="FocusedTxSyntheticAperture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Curvilinear Extension of the Angular Spectrum Method in RTM and its Application to Liver + Kidney Imaging {% cite Ali2022CurvilinearAngularSpectrumMethod %}.
</div>

### Differentiable RTM: Wave Equation Migration Velocity Analysis (WEMVA)

The next step was to make the RTM imaging process differentiable with respect to the acoustic properties of the medium.  Rather than treating the sound speed profile as a fixed parameter, differentiable RTM enables the forward and adjoint mapping between changes in the sound speed profile and linearized perturbations to the reconstructed images.  This results in an inverse problem: the sound speed profile can be updated according to how it affects image quality.  In seismic imaging, RTM and wave-equation migration (WEM) are interchangeable terminologies for the same technique.  When WEM is differentiated with respect to sound speed and used to minimize aberrations in the image, the resulting form of diffraction tomography becomes wave-equation migration velocity analysis (WEMVA).  In pulse-echo ultrasound, this provides a direct connection between wave propagation, [aberration correction](https://rehmanali1994.github.io/projects/aberration-correction/), and [sound speed estimation](https://rehmanali1994.github.io/projects/sound-speed-estimation/).  

My initial implementation used the difference between images reconstructed from individual transmissions as the objective.  This image-difference formulation provided the first demonstration of wave-equation migration velocity analysis (WEMVA) for medical pulse-echo ultrasound {% cite Ali2026DifferentiableRTM %}.  The same framework subsequently led to subsurface-offset WEMVA, which uses the behavior of the extended image with subsurface offset to estimate sound speed {% cite Ali2026WEMVA %}.  These developments connect wave-equation migration with the broader problem of [quantitative sound speed estimation](https://rehmanali1994.github.io/projects/sound-speed-estimation/) and [aberration correction](https://rehmanali1994.github.io/projects/aberration-correction/) in heterogeneous tissue.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2026DifferentiableRTM.gif" title="Ali2026DifferentiableRTM" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/PhantomVSX4_2.gif" title="PhantomVSX4_2" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Wave-Equation Migration Velocity Analysis (WEMVA) for Sound Speed Estimation and Aberration Correction.  Both animations correspond to channel data from the same phantom experiment.  (Left) Image-Difference WEMVA {% cite Ali2026DifferentiableRTM %}.  (Right) Subsurface-Offset WEMVA {% cite Ali2026WEMVA %}.  Subsurface-offset WEMVA yields better aberration corrections in fewer iterations than image-difference WEMVA.
</div>

<b>
