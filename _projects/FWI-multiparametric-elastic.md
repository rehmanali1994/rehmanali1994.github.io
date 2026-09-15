---
layout: page
title: Multiparametric and Elastic FWI
description: Extending the wave physics model and FWI to reconstruct multiple tissue mechanical properties
img: assets/img/kWave_BreastCT.gif
importance: 4
category: Full-Waveform Inversion (FWI) for UST/USCT
related_publications: true
---


### Multiparametric Imaging with Acoustic FWI

Full-waveform inversion provides a framework for reconstructing quantitative tissue properties by matching measured and simulated ultrasound waveforms.  Much of my earlier work focused on reconstructing the sound-speed distribution, which primarily controls the phase and arrival time of transmitted ultrasound.  However, the acoustic wave equation contains additional parameters that influence the measured signals, including attenuation and density.

These parameters do not affect the data in the same way.  Sound speed primarily changes the timing and shape of the transmitted wavefield, while attenuation reduces its amplitude.  Density has a comparatively small effect on the transmitted waveform, making it difficult to recover reliably from transmission measurements alone.

The situation is different for reflected ultrasound.  Backscattered signals arise from spatial variations in acoustic impedance Z = ρc, where ρ is density and c is sound speed.  Consequently, density can have a much stronger influence on the reflected signal than on the transmitted wavefield.  This suggests that combining transmission and reflection measurements could provide information about tissue density that is difficult to obtain from transmission tomography alone.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/TransmissionVsReflection.png" title="TransmissionVsReflection" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Transmission vs Reflection in UST/USCT. (Left) The transmission of ultrasound through the breast is primarily impacted by sound speed and attenuation. Sound speed primarily affects the shape of the transmitted wavefront by advancing and delaying the wave. Attenuation affect the amplitude of the transmitted wave. (Right) Ultrasound backscatter reflected by the tissue is the result of spatial changes in the impedance Z=ρc (a product of sound speed c and density ρ). Although density has a small impact on the waveform transmitted through tissue, it plays a much more significant role on the backscattered reflections, so we theorize that modeling the reflected ultrasound signals should enable imaging of the mass density in the breast.
</div>


### Sound Speed and Attenuation Based on Transmission Tomography

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

As a first step toward multiparametric reconstruction, I extended FWI for transmission ultrasound computed tomography to simultaneously estimate sound speed and attenuation by modeling each set of parameters as the real and imaginary parts, respectively, of the complex slowness {% cite Ali2024_BlockLU_2DFWI %}.  This ultimately treats attenuation as a frequency-dependent loss of acoustic energy alongside sound speed.  The simulations above demonstrate simultaneous reconstruction of these two properties in breast models.  The recovered sound-speed distributions capture the large-scale acoustic structure of the breast, while the attenuation reconstructions provide an additional quantitative property of the tissue.  This multiparametric formulation was also evaluated using experimental phantom data below.  The reconstructions demonstrate that the additional degrees of freedom can be recovered from the measured waveforms when the forward model accounts for their distinct effects on the data.

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

### [Quantitative Reconstruction in the Breast](https://rehmanali1994.github.io/projects/breast-cancer-screening/)

The ability to reconstruct multiple acoustic properties is particularly relevant to [breast imaging](https://rehmanali1994.github.io/projects/breast-cancer-screening/).  Conventional B-mode ultrasound primarily depicts spatial variations in scattering, while transmission ultrasound provides quantitative information about the acoustic properties along propagation paths.  In the breast, multiparametric FWI can recover both sound speed and attenuation while preserving the spatial localization of lesions and other structures.  The key limitation, however, is that an acoustic model still treats the tissue as a fluid and therefore does not model shear-wave propagation or the full mechanical response of tissue.

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

The examples above show in-vivo breast reconstructions differentiating between a benign cyst and and a diagnosed malignancy, demonstrating the potential of FWI to provide diagnostically relevant tissue characterization in addition to anatomical imaging {% cite Ali2024_BlockLU_2DFWI %}.  For example, although the fluid-filled cyst has a higher sound speed than the fat background of the breast, the attenuation is through the same region is low, and the globular morphology of the cyst is indicative of a fluid filled pocket of tissue.  However, the malignancy is a spiculated mass with branching tissue indicative of tissue scarring that has both high sound speed and attenuation.  This ultimately differentiates the malignancy from the fluid-filled cyst.

### From the Acoustic to the Fully Elastic Wave Equation

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ElasticWaveEquation.png" title="ElasticWaveEquation" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    From the Acoustic to the Fully Elastic Wave Equation
</div>

To recover a more complete description of tissue mechanics, the forward model can be extended from the acoustic wave equation to the fully elastic wave equation.  Elastic propagation introduces additional mechanical parameters and supports both compressional and shear waves.  This provides a path toward reconstructing properties that cannot be represented by an acoustic model alone.  In principle, a fully elastic FWI framework could recover multiple tissue mechanical properties from the way both compressional and shear components propagate, reflect, and interact within the [breast](https://rehmanali1994.github.io/projects/breast-cancer-screening/).  In fact, beyond breast imaging, several diagnostic applications involving bone, particularly [transcranial imaging](https://rehmanali1994.github.io/projects/transcranial-imaging/), ultimately require full-wave elastic modeling at the bone tissue interface {% cite Marty2024ElasticBoneCharacterization %}.  Therefore, the transition from acoustic to elastic FWI therefore represents a broader shift in this work: from estimating individual acoustic parameters to using increasingly complete wave physics to quantitatively characterize tissue.

<b>
