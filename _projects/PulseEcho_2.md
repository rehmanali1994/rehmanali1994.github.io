---
layout: page
title: Aberration Correction
description: Aberration correction for pulse-echo ultrasound imaging and beamforming
img: assets/img/PhantomVSX2.gif
importance: 2
category: Pulse-Echo Ultrasound
---



<div class="row justify-content-sm-center">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2019REFoCUS.png" title="Ali2019REFoCUS" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2023OptimalApodization.png" title="Ali2023OptimalApodization" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Beamforming Foundations of Aberration Correction.  (Left) As a foundation for aberration correction, I contributed to a novel synthetic-aperture beamforming framework known as Retrospective Encoding For Conventional Ultrasound Sequences (REFoCUS) that recovers multistatic synthetic aperture channel data from arbitrary transmit sequences and enables complete transmit-and-receive aberration corrections {% cite Ali2019REFoCUS %}.  (Right) I also developed the optimal transmit apodization to maximize the short-lag spatial coherence of receive signals for aberration delay estimation via nearest-neighbor cross-correlation {% cite Ali2023OptimalApodization %}.
</div>



<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2022DistributedAberrationCorrection.png" title="Ali2022DistributedAberrationCorrection" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Distributed Aberration Correction in Layered Media {% cite Ali2022DistributedAberrationCorrection %}.  As lateral variations in sound speed increase, aberration correction requires moving beyond the layered medium model towards ray-based modeling of aberrations. 
</div>




<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/RayModeling.png" title="RayModeling" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2026MidFieldPhaseScreenModel.png" title="Ali2026MidFieldPhaseScreenModel" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2023AberrationCorrectionReview.png" title="Ali2023AberrationCorrectionReview" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Ray-Based Modeling of Aberration Delays in Ultrasound Beamforming {% cite Ali2023AberrationCorrectionReview %}.  (Top) Time-of-flight based on line integrals over slowness (reciprocal of sound speed).  (Bottom Left) Simplified modeling of time-of-flight based on multiple mid-field phase screens {% cite Ali2026MidFieldPhaseScreenModel %}.  (Bottom Right) Refraction-based modeling of time-of-flight based on the eikonal equation.
</div>






<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/IterativeAberrationCorrection.png" title="IterativeAberrationCorrection" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2023IMPACT.png" title="Ali2023IMPACT" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Iterative Sound Speed Estimation and Aberration Correction Based on Ray Tomography with Aberration Delays {% cite Ali2023IterativeAberrationCorrection Ali2023DistributedAberrationCorrection %}.  On the right, I demonstrate the velocity-depth ambiguity that arises when the sound speed estimate is no longer constrained to layered media {% cite Ali2023IMPACT %}.  In practice, different sound speed estimates can provide similar improvements in the focusing of the image with the only difference being the depth placements of those imaging targets.  In an effort to mitigate the nonlinearity associated with the velocity depth ambiguity that locks the solution to the false minimum closest to the initial sound speed guess, we began to implement an adaptive imaging grid that follows the image targets as the sound speed estimate changes {% cite Ali2026TargetFollowingLagrangianApproach %}.  However, the fundamental ill-posedness and ill-conditioning of the inverse problem (also associated with the velocity-depth ambiguity) remain.
</div>




<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/SoundSpeedEstimation.png" title="SoundSpeedEstimation" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2026DifferentiableRTM.gif" title="Ali2026DifferentiableRTM" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Full-Wave Sound Speed Estimation and Aberration Correction Using Image-Difference WEMVA {% cite Ali2026DifferentiableRTM %}.
</div>




<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/PhantomVSX2.gif" title="PhantomVSX2" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2026WEMVA.gif" title="Ali2026DifferentiableRTM" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/PhantomVSX4_1.gif" title="PhantomVSX4_1" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/PhantomVSX4_2.gif" title="PhantomVSX4_2" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/Rat11_Acq2.gif" title="Rat11_Acq2" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/RatAbdomenL12-3v.gif" title="RatAbdomenL12-3v" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Full-Wave Sound Speed Estimation and Aberration Correction Using Subsurface-Offset WEMVA {% cite Ali2026WEMVA %}.
</div>



