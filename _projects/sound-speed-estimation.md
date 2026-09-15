---
layout: page
title: Sound Speed Estimation
description: Inverse problem of reconstructing the sound speed profile of tissue from limited-angle pulse-echo data
img: assets/img/SoundSpeedEstimation.png
importance: 1
category: Pulse-Echo Ultrasound
related_publications: true
---

Accurate knowledge of tissue sound speed is fundamental to ultrasound imaging and has important clinical applications such as [cancer detection](https://rehmanali1994.github.io/projects/breast-cancer-screening/) and [staging of fatty liver disease](https://rehmanali1994.github.io/projects/quantitative-liver-imaging/).  Conventional beamforming typically assumes a fixed sound speed, but the true sound speed varies spatially with tissue composition.  When this assumption is incorrect, the resulting timing errors cause aberration, defocusing, and incorrect spatial localization of structures.  Therefore, sound speed is not only a quantitative biomarker but it can play a fundamental role in ultrasound image quality.

### From Beamforming Sound Speed to Local Sound Speed

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2021LayeredMedia.png" title="Ali2021LayeredMedia" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/LiverLayers.png" title="LiverLayers" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Early Layered Medium Model for Sound Speed Estimation.
</div>

During my PhD, I developed one of the first quantitative approaches for estimating sound speed directly from pulse-echo ultrasound data.  The key observation is that the sound speed used for beamforming contains information about the propagation speed of the tissue itself.  For a layered medium, the beamforming sound speed that produces the best focus at a given depth can be interpreted as an estimate of the average sound speed above that depth.  This turns the beamforming problem into an inverse problem: rather than treating the sound speed as a fixed imaging parameter, we can measure how the optimal focusing sound speed changes with depth and invert this relationship to recover a local, depth-wise sound-speed profile {% cite Ali2021LayeredMedia %}.  This provides a way to obtain quantitative sound-speed information using the same pulse-echo data that are already acquired for conventional ultrasound imaging.  The layered-medium formulation also provided a useful framework for investigating different acquisition strategies. We demonstrated related approaches using plane-wave imaging {% cite Ali2020PlaneWaveSoS %} and common-midpoint gathers {% cite Ali2020CMP Brevett2022CMP %}. 

### [Quantitative Liver Sound Speed Imaging](https://rehmanali1994.github.io/projects/quantitative-liver-imaging/)

The ability to estimate local sound speed from pulse-echo measurements also opened the possibility of using ultrasound as a quantitative tool for characterizing tissue composition.  One application that motivated this work was [liver imaging](https://rehmanali1994.github.io/projects/quantitative-liver-imaging/).  Changes in liver composition, including those associated with fatty liver disease, can alter the acoustic properties of the tissue.  The sound-speed estimates therefore provide information that is complementary to conventional B-mode reflectivity.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/RatLayers.png" title="RatLayers" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Example of Liver Imaging in Rats with Average and Local Sound Speed Estimates.
</div>

The figure above illustrates an example in which the estimated sound speed in the liver is compared with measurements obtained from excised tissue {% cite Ali2021LayeredMedia Telichko2022RatStudy %}.  In the first obese Zucker rat, corresponding to a lower steatosis grade (Steatosis Grade 1), the local sound speed was estimated as 1562.8 m/s, compared with 1557 m/s measured from the excised liver.  In the second rat, with a higher steatosis grade (Steatosis Grade 3), the estimated local sound speed was 1522.4 m/s compared with 1511 m/s ex vivo.  These measurements demonstrated that pulse-echo ultrasound could recover meaningful quantitative differences in liver sound speed in vivo.  More broadly, this work showed that sound-speed estimation could move beyond being merely an image-quality correction and become a potential source of tissue-specific quantitative information.

### Generalizing Beyond Layered Media

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2019Average2LocalSoS.png" title="Ali2019Average2LocalSoS" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2022DistributedAberrationCorrection.png" title="Ali2022DistributedAberrationCorrection" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Generalized Distributed Local Sound Speed Estimation in Layered Media.  I generalized the relationship between the average focusing sound speed to a point and the local profile of sound speed in the medium to account for all paths to a point {% cite Ali2019Average2LocalSoS %}.  However, as later shown in {% cite Ali2022DistributedAberrationCorrection %}, these simplifications in layered media quickly break down as lateral variations in sound speed increase.  
</div>

The initial layered-medium model makes an important simplifying assumption: sound speed varies primarily with depth.  Under this assumption, the relationship between an average focusing sound speed and the underlying local sound-speed profile can be derived relatively simply.  I subsequently generalized this relationship to account for the collection of propagation paths contributing to the focusing of a point {% cite Ali2019Average2LocalSoS %}.  This provided a more general description of how local sound-speed variations affect the effective focusing speed measured by the imaging system.  However, this generalization also exposed a fundamental limitation of the layered model.  Real biological tissue is not necessarily laterally homogeneous.  As lateral sound-speed variations become significant, the assumption that the medium can be represented by a one-dimensional depth profile becomes increasingly inaccurate {% cite Ali2022DistributedAberrationCorrection %}.  The focusing errors are then no longer described adequately by a single depth-dependent sound-speed value.  This limitation motivated a shift from estimating a one-dimensional sound-speed profile toward explicitly modeling the spatially distributed aberration produced by heterogeneous tissue.

### From a Layered Profile to Complete Spatial Variation in Sound Speed

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/HandheldUltrasound.png" title="HandheldUltrasound" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/RayModeling.png" title="RayModeling" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Ray-Based Modeling of Aberration Delays in Ultrasound Beamforming. 
</div>

For a handheld ultrasound system, the propagation paths between the transducer and an imaging target can pass through tissue with spatially varying sound speed. Rather than assuming that all of the aberration can be represented by a layered model, we can instead model the additional travel-time delays introduced by the heterogeneous medium.  A ray-based description provides a useful intermediate model.  The acoustic paths are approximated using rays, and the accumulated travel-time differences are used to estimate the aberration delays across the transducer aperture.  These delays can then be incorporated into beamforming to compensate for the spatially varying sound speed.  This led to an iterative approach in which sound-speed estimation and aberration correction are performed together {% cite Ali2023IterativeAberrationCorrection Ali2023DistributedAberrationCorrection %}.  

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

### Velocity–Depth Ambiguity

Moving beyond layered media, however, reveals a deeper problem with pulse-echo sound-speed estimation: the data do not uniquely determine both the sound speed and the location of the reflecting structures.  A change in sound speed changes the estimated travel time to an imaging target.  But the same observed travel time can often be explained by placing that target at a different physical depth.  Consequently, different sound-speed models can produce similarly focused images while placing the underlying structures at different depths.  This velocity–depth ambiguity makes the inverse problem highly nonlinear. In iterative optimization, the solution can become attracted to a local minimum associated with the initial sound-speed estimate rather than converging to the true medium.  The example above illustrates this ambiguity.  Different sound-speed estimates can produce comparable improvements in image focusing, while the primary difference is the inferred depth of the targets.  Improving image sharpness alone is therefore not sufficient to guarantee an accurate sound-speed reconstruction.  This observation changed the goal of the problem: rather than simply finding the sound-speed model that produces the sharpest image, we need an inversion framework that accounts explicitly for the coupled relationship between wave propagation, image formation, and target position.

### Following the Image Targets while Estimating the Medium's Sound Speed

One approach we explored was to allow the imaging grid itself to adapt as the sound-speed estimate changes.  Instead of assuming that the locations of image targets remain fixed while the propagation model is updated, the imaging coordinates can be allowed to follow the targets through the evolving model.  This target-following or Lagrangian viewpoint helps reduce some of the nonlinear behavior associated with the velocity–depth ambiguity  {% cite Ali2026TargetFollowingLagrangianApproach %}.  It does not, however, eliminate the underlying ill-posedness of the problem.  Limited-angle pulse-echo measurements without absolute time-of-flight information simply do not contain enough independent information to uniquely recover an arbitrary three-dimensional sound-speed distribution and the associated reflector geometry without additional constraints.  This limitation motivated the next step in the progression: moving from ray-based travel-time models to full-wave modeling.

### Full-Wave Sound Speed Estimation

The ray-based approaches described above approximate ultrasound propagation using travel times along individual acoustic paths.  While this approximation is useful for estimating aberration delays, it becomes increasingly limited in heterogeneous media where diffraction and wave interference play an important role in image formation.  A more complete approach is to model the full acoustic wavefield and use reverse-time migration (RTM) to directly connect the sound-speed distribution to the reconstructed image.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/SoundSpeedEstimation.png" title="SoundSpeedEstimation" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2026DifferentiableRTM.gif" title="Ali2026DifferentiableRTM" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Full-Wave Sound Speed Estimation and Aberration Correction Using Image-Difference WEMVA {% cite Ali2026DifferentiableRTM %}.
</div>

Wave-equation migration velocity analysis (WEMVA) provides such a framework.  Instead of estimating sound speed by fitting differential travel-time measurements, WEMVA evaluates how errors in the sound-speed model affect the reconstructed image and uses this information to update the model.  In this way, sound-speed estimation is performed directly through the image-formation process.  Because the wave propagation and imaging operations are differentiable with respect to sound speed, errors between partial images are used to determine how the sound speed model should be updated.  Unlike full-waveform inversion, which minimizes the difference between measured and modeled channel data, WEMVA operates in the image domain.  This distinction is particularly useful for ultrasound imaging, where the objective of sound-speed estimation is ultimately to correct the focusing and localization of structures in the reconstructed image.

Therefore, this work {% cite Ali2026DifferentiableRTM %} provides a transition from ray-based sound-speed estimation to full-wave modeling, allowing the estimation process to account for the complete physics of ultrasound propagation rather than only travel-time differences.

### Subsurface-Offset WEMVA

A second formulation uses a subsurface-offset extension of RTM, which introduces a lateral subsurface offset between the transmit and receive wavefields.  For an accurate sound-speed model, image energy should concentrate at zero subsurface offset; sound-speed errors instead produce energy distributed across nonzero subsurface offsets.  Therefore, WEMVA updates the sound-speed model by minimizing the extended image away from zero subsurface offset.  This formulation provides an alternative to comparing partial images and, importantly, avoids the angular-resolution tradeoff (uncertainty principle!) associated with common-midangle methods: the full angular diversity need to resolve an image point can be retained while aberrations associated with individual propagation paths can estimated from the subsurface-offset-extended images {% cite Ali2026WEMVA %}.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/Map2.gif" title="Map2" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/Map5.gif" title="Map5" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/SuperficialLayers.gif" title="SuperficialLayers" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/PhantomVSX4_2.gif" title="PhantomVSX4_2" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Full-Wave Sound Speed Estimation and Aberration Correction Using Subsurface-Offset WEMVA {% cite Ali2026WEMVA %}.
</div>

<br>
