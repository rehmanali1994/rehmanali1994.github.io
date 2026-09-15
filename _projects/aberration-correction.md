---
layout: page
title: Aberration Correction
description: Aberration correction for pulse-echo ultrasound imaging and beamforming
img: assets/img/PhantomVSX2.gif
importance: 2
category: Pulse-Echo Ultrasound
related_publications: true
---



### Beamforming Foundations of Aberration Correction

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

Phase aberration occurs when spatial variations in sound speed distort the propagation of ultrasound through tissue, causing the wavefronts received by the transducer elements to become misaligned.  Correcting these delays requires access to the individual transmit-and-receive propagation paths, which are not directly available in conventional focused ultrasound acquisitions.  As a foundation for aberration correction, I contributed to Retrospective Encoding For Conventional Ultrasound Sequences (REFoCUS), a synthetic-aperture beamforming framework that recovers the equivalent multistatic dataset from arbitrary transmit sequences {% cite Ali2019REFoCUS %}.  This provides access to individual transmit-and-receive channels and enables independent correction of aberration on both transmission and reception.

A complementary challenge is estimating the aberration delays themselves.  I developed an optimal transmit apodization based on the van Cittert–Zernike theorem that maximizes short-lag spatial coherence between neighboring receive channels {% cite Ali2023OptimalApodization %}.  This improves the accuracy of aberration-delay estimation using nearest-neighbor cross-correlation, providing a more reliable measurement of the phase errors that need to be corrected.





### Distributed Aberration Correction

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2022DistributedAberrationCorrection.png" title="Ali2022DistributedAberrationCorrection" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Distributed Aberration Correction in Layered Media {% cite Ali2022DistributedAberrationCorrection %}.  As lateral variations in sound speed increase, aberration correction requires moving beyond the layered medium model towards ray-based modeling of aberrations. 
</div>

Traditional phase-aberration correction typically estimates an independent delay profile for each imaging point.  This works well as a local correction, but it does not explicitly model the physical origin of the aberration: spatial variations in the sound speed throughout the tissue.  Therefore, I developed distributed aberration correction methods that use a tomographic sound-speed estimate to model the propagation of ultrasound through heterogeneous tissue.  Rather than assigning arbitrary delays to each imaging point, the correction is derived from a spatially varying sound-speed map.  Two approaches were developed.  The first solves the eikonal equation to calculate travel times through the heterogeneous medium and uses these times directly in delay-and-sum beamforming.  The second propagates the transmit and receive wavefields through the estimated sound-speed distribution and forms an image from their cross-correlation.  Both approaches allow the aberration correction to account for distributed sound-speed variations rather than treating aberration as a purely local phase error.




### Ray-Based Modeling of Aberration Delays

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/RayModeling.png" title="RayModeling" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2026MidFieldPhaseScreenModel.png" title="Ali2026MidFieldPhaseScreenModel" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2023AberrationCorrectionReview.png" title="Ali2023AberrationCorrectionReview" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Ray-Based Modeling of Aberration Delays in Ultrasound Beamforming {% cite Ali2023AberrationCorrectionReview %}.  (Top-Left) Time-of-flight based on line integrals over slowness (reciprocal of sound speed).  (Top Right) Simplified modeling of time-of-flight based on multiple mid-field phase screens {% cite Ali2026MidFieldPhaseScreenModel %}.  (Bottom) Refraction-based modeling of time-of-flight based on the eikonal equation.
</div>

Once aberration is modeled using a spatially varying sound-speed distribution, the next challenge is calculating the propagation paths through that distribution.  A simple approximation treats the travel time between two points as a line integral of slowness {% cite Ali2023AberrationCorrectionReview %}, while more accurate models account for refraction by solving the eikonal equation.  I also explored intermediate phase-screen models that approximate the heterogeneous propagation using a sequence of mid-field phase screens {% cite Ali2026MidFieldPhaseScreenModel %}.  These mid-field phase models provide a compromise between the computational simplicity of straight-ray propagation and the more complete treatment of refraction provided by eikonal-based models.  These different formulations provide a hierarchy of models for estimating aberration delays, ranging from simple straight-ray approximations to refraction-aware propagation through a spatially varying sound-speed field.


### Iterative Sound Speed Estimation and Aberration Correction

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/IterativeAberrationCorrection.png" title="IterativeAberrationCorrection" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2023IMPACT.png" title="Ali2023IMPACT" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Iterative Sound Speed Estimation and Aberration Correction Based on Ray Tomography with Aberration Delays {% cite Ali2023IterativeAberrationCorrection Ali2023DistributedAberrationCorrection %}.  On the right, I demonstrate the velocity-depth ambiguity that arises when the sound speed estimate is no longer constrained to layered media {% cite Ali2023IMPACT %}.  In practice, different sound speed estimates can provide similar improvements in the focusing of the image with the only difference being the depth placements of those imaging targets.
</div>

Estimating the sound-speed distribution and correcting aberration can also be performed iteratively {% cite Ali2023IterativeAberrationCorrection Ali2023DistributedAberrationCorrection %}.  Aberration delays measured from the ultrasound data provide information about the underlying sound-speed distribution, while the updated sound-speed estimate can then be used to calculate improved propagation delays and reconstruct a better-focused image.  This creates an iterative loop between sound-speed estimation and aberration correction.  However, allowing the sound speed to vary laterally introduces a fundamental velocity–depth ambiguity: different sound-speed distributions can produce similarly focused images while placing structures at different depths {% cite Ali2023IMPACT %}.  This makes the inverse problem nonlinear and can cause iterative optimization to converge to a solution near the initial sound-speed estimate.  One approach we explored was to use an adaptive imaging grid that follows the image targets as the estimated sound speed changes {% cite Ali2026TargetFollowingLagrangianApproach %}.  This reduces some of the nonlinearity associated with the changing target locations, but the underlying ill-posedness of the joint sound-speed and image reconstruction problem remains.


### Towards a Full-Waveform Distributed Aberration Correction Framework

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

These limitations motivate a shift from ray-based propagation models to full-wave modeling.  Instead of representing aberration only through travel-time corrections, wave-equation migration velocity analysis (WEMVA) models complete wave propagation and uses reverse-time migration (RTM) to reconstruct the image based on the estimated sound-speed distribution.  In the image-difference formulation of WEMVA, the effect of changes in the sound-speed model on the errors between partial images is used to determine an update to the sound speed estimate {% cite Ali2026DifferentiableRTM %}.  Because the wave propagation and reconstruction are differentiable with respect to sound speed, this provides a direct way to optimize the propagation model through the image-formation process.  This approach replaces the explicit ray-based aberration correction step with an image-domain full-wavefom inversion in which the sound-speed distribution and image focusing are optimized together.



### Circumventing the Fourier Uncertainty Principle: Subsurface-Offset WEMVA

The main challenge associated with image-difference WEMVA is that multiple propagation path contribute to spatial resolution at an image point.  However, the partial images compared in the image-difference approach restrict the angular diversity needed to fully resolve each image point.  However, it becomes necessary to restrict that angular diversity to better isolate aberrations along individual propagation paths.  This ultimately results in a Fourier uncertainty principle between image resolution and path-based modeling of aberration.  If we restrict angular diversity to isolate propagation paths, it becomes difficult to accurately localize the aberrations in space due to the loss of spatial resolution; conversely, if we focus on maximally resolving each image point, it becomes difficult to isolate the impact of a particular propagation path on measured aberrations.  

A second formulation uses a subsurface-offset extension of RTM, which introduces a lateral subsurface offset between the transmit and receive wavefields.  For an accurate sound-speed model, image energy should concentrate at zero subsurface offset; sound-speed errors instead produce energy distributed across nonzero subsurface offsets.  Therefore, WEMVA updates the sound-speed model by minimizing the extended image away from zero subsurface offset.  This formulation provides an alternative to comparing partial images and, importantly, avoids the Fourier uncertainty principle associated with the image-difference approach: the full angular diversity need to resolve an image point can be retained while aberrations associated with individual propagation paths can estimated from the subsurface-offset-extended images {% cite Ali2026WEMVA %}.

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

<br>

