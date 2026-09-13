---
layout: page
title: Sound Speed Estimation
description: Inverse problem of reconstructing the sound speed profile of tissue from limited-angle pulse-echo data
img: assets/img/SoundSpeedEstimation.png
importance: 1
category: Pulse-Echo Ultrasound
related_publications: true
---

<div class="row justify-content-sm-center">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2021LayeredMedia.png" title="Ali2021LayeredMedia" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/LiverLayers.png" title="LiverLayers" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Early Layered Medium Model for Sound Speed Estimation.  During my PhD, I developed one of the first quantitative methods to estimate sound speed directly from pulse-echo data. The key idea is to use the beamforming sound speed to measure the average sound speed in the tissue.  In layered media, the profile of the average sound speed that best focuses the signal at each depth can be inverted to recover the local depth-wise profile {% cite Ali2021LayeredMedia %}.  This model was very useful for quantifying sound speed inside the liver to help diagnose fatty liver disease.  
</div>



<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/RatLayers.png" title="RatLayers" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Example of liver imaging in rats with average and local sound speed estimates {% cite Ali2021LayeredMedia %}. (Top) First rat shown is a female obese Zucker rat with a steatosis grade of 1. The local sound speed in the liver was measured to be 1562.8 m/s. The sound speed measured in the excised liver sample was 1557 m/s. (Bottom) Second rat is a female obese Zucker rat with a steatosis grade of 3. The local sound speed in the liver was measured to be 1522.4 m/s. The sound speed measured in the excised liver sample was 1511 m/s.  See the complete study on liver steatosis in obese Zucker rats {% cite Telichko2022RatStudy %}.
</div>



<div class="row justify-content-sm-center">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2019Average2LocalSoS.png" title="Ali2019Average2LocalSoS" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Ali2022DistributedAberrationCorrection.png" title="Ali2022DistributedAberrationCorrection" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Generalized Distributed Local Sound Speed Estimation in Layered Media.  I generalized the relationship between the average focusing sound speed to a point and the local profile of sound speed in the medium to account for all paths to a point {% cite Ali2019Average2LocalSoS %}.  However, as later shown in {% cite Ali2022DistributedAberrationCorrection %}, these simplifications in layered media quickly break down as lateral variations in sound speed increase.  
</div>

