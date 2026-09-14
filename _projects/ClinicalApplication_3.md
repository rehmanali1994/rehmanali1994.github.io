---
layout: page
title: Quantitative Liver Imaging
description: Pulse-echo ultrasound-based liver fat fraction assessment based on quantitative sound speed estimation and aberration correction
img: assets/img/QuantitativeLiverUltrasound.png
importance: 4
category: Clinical Applications
related_publications: true
---

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2021LayeredMedia.png" title="Ali2021LayeredMedia" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/LiverLayers.png" title="LiverLayers" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Early Layered Medium Model for Sound Speed Estimation.  During my PhD, I developed one of the first quantitative methods to estimate sound speed directly from pulse-echo data. The key idea is to use the beamforming sound speed to measure the average sound speed in the tissue.  In layered media, the profile of the average sound speed that best focuses the signal at each depth can be inverted to recover the local depth-wise profile {% cite Ali2021LayeredMedia %}.  This layered-medium approach has also been tried with plane waves {% cite Ali2020PlaneWaveSoS %} and with common midpoint gathers {% cite Ali2020CMP Brevett2022CMP %}.  This model was very useful for quantifying sound speed inside the liver to help diagnose fatty liver disease.  
</div>



<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/RatLayers.png" title="RatLayers" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Example of Liver Imaging in Rats with Average and Local Sound Speed Estimates {% cite Ali2021LayeredMedia %}. (Top) First rat shown is a female obese Zucker rat with a steatosis grade of 1. The local sound speed in the liver was measured to be 1562.8 m/s. The sound speed measured in the excised liver sample was 1557 m/s. (Bottom) Second rat is a female obese Zucker rat with a steatosis grade of 3. The local sound speed in the liver was measured to be 1522.4 m/s. The sound speed measured in the excised liver sample was 1511 m/s.  See the complete study on liver steatosis in obese Zucker rats {% cite Telichko2022RatStudy %}.
</div>


