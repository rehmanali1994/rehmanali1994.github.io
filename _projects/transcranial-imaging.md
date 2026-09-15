---
layout: page
title: Transcranial Imaging
description: Whole-brain transcranial ultrasound computed tomography for rapid point-of-care assessment of acute neurological conditions
img: assets/img/TranscranialUST.png
importance: 2
category: Clinical Applications
related_publications: true
---

### Ultrasound Computed Tomography Through the Skull

Ultrasound computed tomography (USCT) offers the possibility of imaging the entire brain using a surrounding array of transducers, providing quantitative information about the acoustic properties of tissue rather than relying only on conventional pulse-echo images. For transcranial imaging, however, the skull presents a major challenge. Its strong acoustic heterogeneity, attenuation, and mode conversion distort the ultrasound wavefield before it reaches the brain, making conventional ultrasound imaging assumptions inadequate.  The goal of this work is to develop full-wave methods that can account for these effects and enable whole-brain USCT through the skull. Such a system could provide rapid, portable imaging for acute neurological conditions, where access to conventional neuroimaging may be limited by cost, availability, or the need to transport critically ill patients.

### Initial Phantom Experiments

We first investigated whether transmission ultrasound could be used to image through a skull-like acoustic barrier.  These experiments used tissue-mimicking phantoms containing skull and brain-equivalent materials to evaluate the effects of the skull on ultrasound propagation and the ability of full-wave methods to recover the underlying structures.  The phantom experiments established the feasibility of reconstructing quantitative brain images despite the presence of the skull.  They also highlighted the central challenge for transcranial USCT: the skull introduces large travel-time errors and strong waveform distortion, so the success of full-waveform inversion depends critically on the quality of the starting model and the ability to account for the skull in the forward model.  These experiments provided the foundation for subsequent studies in more realistic brain models and biological specimens.

<div class="row">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/TranscranialPhantom1.png" title="TranscranialPhantom1" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/TranscranialPhantomResult1.png" title="TranscranialPhantomResult1" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/TranscranialPhantom2.png" title="TranscranialPhantom1" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/TranscranialPhantomResult2.png" title="TranscranialPhantomResult1" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Initial Phantom Experiments of Ultrasound Computed Tomography Through the Skull {% cite Mitcham2024ImagingStroke Marty2024ElasticBoneCharacterization %}.
</div>

### Whole-Brain Transcranial Imaging Using the Macaque Brain

We next moved from simplified phantoms to an ex-vivo macaque brain model to investigate whole-brain transcranial USCT under more realistic conditions.  The experiments allowed us to evaluate the reconstruction of brain structures after propagation through a skull with realistic acoustic properties.  The resulting images demonstrate that quantitative information about the brain can be recovered through the skull using full-wave modeling.  At the same time, the experiments revealed strong artifacts linked to FWI cycle skipping caused by the strong acoustic contrast and attenuation of the skull.  This motivated the use of low-frequency information and [cycle-skipping-robust inversion strategies](https://rehmanali1994.github.io/projects/FWI-cycle-skipping/) specifically for transcranial imaging.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/MacaqueBrainExperiments.png" title="MacaqueBrainExperiments" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/MacaqueBrainResults.png" title="MacaqueBrainResults" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2025FrequencyDifferencing.png" title="Ali2025FrequencyDifferencing" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/TranscranialFrequencyDifferencing.png" title="TranscranialFrequencyDifferencing" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Whole-Brain and Transcranial Ultrasound Computed Tomography Based on Frequency Differencing and Full-Waveform Inversion {% cite Mitcham2025TranscranialUST Ali2025FrequencyDifferencing %}.
</div>


### Ex-Vivo Human Whole-Brain Imaging

The next step was to evaluate transcranial USCT using an ex-vivo human cadaver brain.  This provides a substantially more realistic test of the complete imaging problem, including the geometry and acoustic properties of the human skull and the complexity of the human brain.  The experiments demonstrate the potential of whole-brain USCT to recover quantitative acoustic information through the human skull. They also provide an important test of the computational methods developed for [cycle-skipping mitigation and low-frequency extrapolation](https://rehmanali1994.github.io/projects/FWI-cycle-skipping/).  Moving from phantoms and animal models to the human cadaver is an important step toward understanding which aspects of the reconstruction are limited by the [imaging physics](https://rehmanali1994.github.io/projects/FWI-multiparametric-elastic/) and which are determined by the available acquisition and computational methods.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/TranscranialExperiments.png" title="TranscranialExperiments" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/TranscranialExperimentResults.png" title="TranscranialExperimentResults" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Ex-Vivo Human Cadaver Whole-Brain and Transcranial Ultrasound Computed Tomography {% cite Owolabi2026LowFrequencyExtrapolation Marini2026TranscranialUST %}.
</div>


### [Cycle-Skipping Robust FWI](https://rehmanali1994.github.io/projects/FWI-cycle-skipping/) for Transcranial Imaging

The strong acoustic heterogeneity of the skull makes transcranial FWI particularly susceptible to cycle skipping.  Several strategies can mitigate this problem.  Frequency-difference FWI (FD-FWI) synthesizes low-frequency information from pairs of measured higher-frequency signals, providing the long-wavelength information needed to initialize FWI.  Adaptive waveform inversion (AWI) takes a different approach, replacing direct waveform matching with a filter-based objective that encourages the transformation between simulated and measured signals to approach a zero-lag delta function.  Other approaches, including optimal transport, low-frequency extrapolation, and learned signal transformations, seek to provide similar robustness without requiring additional low-frequency measurements.  The comparison below illustrates the behavior of FD-FWI and AWI relative to conventional FWI in a numerical transcranial imaging phantom {% cite Klaben2026JAX %}. These cycle-skipping-robust approaches provide complementary strategies for overcoming the severe initialization problem introduced by the skull.

<div class="row">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/NumericalBrainPhantom.png" title="NumericalBrainPhantom" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/NumericalBrainPhantomResults.png" title="NumericalBrainPhantomResults" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Frequency-Difference Full-Waveform Inversion (FD-FWI) and Adaptive Waveform Inversion (AWI) vs Conventional FWI in a Numerical Transcranial Imaging Phantom at 100 and 200 kHz {% cite Klaben2026JAX Singh2026TranscranialUST Mitcham2025TranscranialUST Ali2023HomogeneousStartingModelFWI%}.
</div>

### Toward Point-of-Care Whole-Brain Imaging

Together, these studies form a progression from simulations and controlled phantoms to animal experiments and finally to ex-vivo human whole-brain imaging. The underlying goal is to make quantitative, full-wave ultrasound imaging robust enough to operate through the skull while remaining compatible with practical ultrasound hardware.  A successful transcranial USCT system could provide whole-brain acoustic imaging without ionizing radiation and with substantially less infrastructure than conventional neuroimaging systems.  The combination of full-wave modeling, cycle-skipping-robust FWI, and low-frequency extrapolation provides a path toward making that possibility practical for rapid assessment of acute neurological conditions.  We also need to address the potential complications that may result from [higher order physics such as mode-conversion at the bone-tissue interface](https://rehmanali1994.github.io/projects/FWI-multiparametric-elastic/).  Ultimately, this research represents a new frontier for medical ultrasound imaging and tomography that will test the limits of our understanding of physics, optimization, and inverse problems.

<br>
