---
layout: page
title: Breast Cancer Screening
description: Low-cost, quantitative, high-resolution, and ionizing-radiation-free imaging of the whole breast based on ultrasound computed tomography
img: assets/img/BreastUST.png
importance: 1
category: Clinical Applications
related_publications: true
---

### Ultrasound Computed Tomography for Breast Cancer Screening

Ultrasound computed tomography (USCT) provides a different approach to breast imaging than conventional pulse-echo ultrasound. Rather than relying only on backscattered echoes, a ring of transducers records ultrasound transmitted through the breast as well as reflections generated within the tissue. These measurements provide complementary information about the acoustic properties of the breast and enable quantitative image reconstruction. The goal is to develop a low-cost, radiation-free alternative for whole-breast imaging that combines the quantitative information of tomography with the spatial resolution of modern wave-equation imaging.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/OverviewUST.png" title="OverviewUST" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Ring-based UST/USCT records transmissions through and reflections from tissue.  In-vivo comparison of FWI-based UST to MRI for breast imaging.
</div>

### Quantitative Breast Imaging with Full-Waveform Inversion

Full-waveform inversion (FWI) reconstructs tissue properties by matching the measured ultrasound waveforms to waveforms simulated through a model of the breast.  In transmission, sound speed primarily controls the phase and arrival time of the waveform, while attenuation controls its amplitude.  By explicitly modeling wave propagation, FWI can use these effects to reconstruct quantitative maps of sound speed and attenuation rather than producing only a qualitative echo image.  This approach enables the reconstruction of breast anatomy directly from the acoustic properties of tissue.  The resulting images can reveal lesions through changes in sound speed and attenuation while retaining the quantitative character of tomographic imaging.  Numerical and experimental studies demonstrate that FWI can recover these properties in breast phantoms, including both benign and malignant lesions {% cite Ali2024_BlockLU_2DFWI %}.

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
<div class="caption">
    FWI Reconstruction of Sound Speed and Attenuation in the Breast {% cite Ali2024_BlockLU_2DFWI %}.  (Top) Benign Cyst.  (Bottom) Malignancy.
</div>

### From Screening to Diagnosis

The resolution of FWI reconstructions can be increased by incorporating progressively higher frequencies.  Lower frequencies provide more robust recovery of the large-scale sound-speed structure, while higher frequencies provide finer spatial detail.  This creates a natural tradeoff between image resolution and computational cost: a screening scan can first identify suspicious regions, after which additional high-frequency reconstruction can be used to characterize those regions in greater detail.  This suggests a workflow in which USCT serves not only as a screening modality, but also as a quantitative tool for investigating suspicious findings.  Rather than acquiring a single image optimized for every diagnostic task, the reconstruction can be adapted to the clinical question by varying the frequency content and computational effort.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ScreeningToDiagnosis.png" title="ScreeningToDiagnosis" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Screening to Diagnosis.  In each case, the spatial resolution of the FWI sound speed reconstruction increases with frequency but may requires longer compute times to confirm suspected cancers. 
</div>

### Comparison with MRI

The quantitative nature of FWI makes USCT particularly interesting as a potential alternative to MRI for breast imaging.  MRI provides excellent soft-tissue contrast but requires expensive equipment.  USCT uses non-ionizing ultrasound and can acquire whole-breast measurements using a surrounding transducer array.  The goal is not necessarily to replace MRI but to reduce the clinical burden on MRI by enabling ultrasound to answer the same fundamental clinical questions.  The FWI reconstructions below show that quantitative sound-speed imaging can produce structural and contrast information that is visually comparable to T1-weighted breast MRI. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/USTvsFWI.png" title="USTvsFWI" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    UST/USCT FWI Sound Speed Reconstruction vs. Contrast-Enhanced (T1-Weighted) MRI for Breast Imaging.
</div>

### Detecting Mammographically Occult Lesions

<div class="row">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Mammogram.png" title="Mammogram" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/BreastImagingSequences.png" title="BreastImagingSequences" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Mammographically Occult Breast Cancer. (Left) Mammography. (Right) Cancer visualized on B-mode, sound speed, and attenuation.
</div>

A particularly important application is the detection of cancers that are difficult to identify with mammography.  Dense breast tissue and other imaging limitations can obscure lesions in conventional mammographic images.  Because USCT provides complementary measurements and reconstructs quantitative acoustic properties, lesions that are inconspicuous on mammography may become visible in sound-speed, attenuation, or reflection images.  The examples above and below illustrate this complementary information across multiple breast lesions, including invasive ductal carcinomas and cases in which the cancer is occult on mammography.  The combination of FWI-derived quantitative images with conventional reflection imaging provides multiple signatures with which to identify and characterize suspicious tissue.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/USTvsMammogram.png" title="USTvsMammogram" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Three Case Examples of Breast Cancers Detected using UST.  (Top Row) Fibroadenoma.  (Middle Row) Invasive Ductal Carcinoma Visible on Mammogram.  (Bottom
Row) Invasive Ductal Carcinoma Occult on Mammogram. (Left Column) Mammography.  (Middle Column) FWI sound speed. (Right Column) B-mode reflection.
</div>

### Toward Quantitative Whole-Breast Imaging and Screening

The broader objective is to combine the advantages of ultrasound tomography, full-waveform inversion, and modern computational imaging into a practical breast-screening system.  Transmission and reflection measurements provide complementary sensitivity to tissue properties, while FWI allows those measurements to be interpreted through a physics-based model of wave propagation.  The resulting framework moves breast ultrasound from qualitative detection toward quantitative tissue characterization: instead of asking only whether a structure reflects ultrasound, the reconstruction asks how its acoustic properties differ from surrounding tissue.  Improving the accuracy, resolution, and computational efficiency of these reconstructions could ultimately enable USCT to provide a radiation-free and quantitative approach to whole-breast screening and follow-up diagnosis.  Future direction for whole-breast USCT include 3D volumetric FWI and USCT acquisition systems {% cite Ali2024_BlockLU_2DFWI %}, and data efficiency for rapid screening via transmit-receive downsampling {% cite Nketia2026Downsampling %}.

<br>
