---
layout: page
title: Quantitative Liver Imaging
description: Pulse-echo ultrasound-based liver fat fraction assessment based on quantitative sound speed estimation and aberration correction
img: assets/img/QuantitativeLiverUltrasound.png
importance: 4
category: Clinical Applications
related_publications: true
---

### Early Liver Sound Speed Estimation Based on Layered Abdomen Model

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

Early work focused on estimating liver sound speed from pulse-echo ultrasound using a layered model of the abdomen {% cite Ali2021LayeredMedia Ali2020PlaneWaveSoS Ali2020CMP Brevett2022CMP %}.  The beamforming sound speed that produced the best focus at a given depth was related to the average sound speed of the tissue above that depth, allowing the measured depth-dependent values to be inverted to estimate a local sound-speed profile.  This approach was demonstrated in obese Zucker rats with different grades of hepatic steatosis {% cite Ali2021LayeredMedia Telichko2022RatStudy %}. The estimated liver sound speeds agreed closely with measurements from the corresponding excised liver samples, demonstrating the potential of pulse-echo ultrasound for quantitative assessment of liver tissue.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/RatLayers.png" title="RatLayers" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/publication_preview/Telichko2022RatStudy.png" title="Telichko2022RatStudy" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/RatLiverStudy.png" title="RatLiverStudy" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Example of Liver Imaging in Rats with Average and Local Sound Speed Estimates {% cite Ali2021LayeredMedia %}. (Top) First rat shown is a female obese Zucker rat with a steatosis grade of 1. The local sound speed in the liver was measured to be 1562.8 m/s. The sound speed measured in the excised liver sample was 1557 m/s. (Bottom) Second rat is a female obese Zucker rat with a steatosis grade of 3. The local sound speed in the liver was measured to be 1522.4 m/s. The sound speed measured in the excised liver sample was 1511 m/s.  See the complete study on liver steatosis in obese Zucker rats {% cite Telichko2022RatStudy %}.
</div>

<br>

### Quantitative Full-Wave Estimation of Liver Sound Speed

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/Map1.gif" title="Map1" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/Map2.gif" title="Map2" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/Map3.gif" title="Map3" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/Map4.gif" title="Map4" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/Map5.gif" title="Map5" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/Map6.gif" title="Map6" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Subsurface-Offset WEMVA for Sound Speed Estimation and Aberration Correction in Simulations of the Abdominal Wall {% cite Ali2026WEMVA %}.
</div>

The layered-medium model provides a useful estimate of liver sound speed, but it cannot adequately describe the lateral sound-speed variations encountered in the abdomen.  These variations produce both travel-time errors and diffractive effects that degrade the image when conventional beamforming assumes a constant sound speed.  To address this limitation, I developed wave-equation migration velocity analysis (WEMVA) for sound-speed estimation and aberration correction in pulse-echo ultrasound.  WEMVA uses reverse-time migration (RTM) to reconstruct the image by cross-correlating the transmitted and backpropagated received wavefields.  Because the RTM image is differentiable with respect to the sound-speed distribution, the image-domain error can be used to iteratively update the sound speed estimate.  My most recent form of WEMVA uses extended RTM images with a subsurface offset between the transmit and receive wavefields.  The correct sound speed profile should focus the extended image at zero subsurface offset; sound speed errors produce residual energy at nonzero subsurface offsets.  Driving this energy toward zero subsurface offset provides an image-domain criterion for estimating the sound speed profile {% cite Ali2026WEMVA %}. 

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/Rat11_Acq2.gif" title="Rat11_Acq2" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/RatAbdomenL12-3v.gif" title="RatAbdomenL12-3v" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/Rat10_Acq3.gif" title="Rat10_Acq3" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/SuperficialLayers.gif" title="SuperficialLayers" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Subsurface-Offset WEMVA in the Abdomen of Obese Zucker Rats and a Healthy Human Subject {% cite Ali2026WEMVA %}.
</div>

<br>

### Future Work: Extending WEMVA to Curvilinear Human-Abdominal Imaging

The initial WEMVA formulation was developed for linear arrays, whereas clinical abdominal ultrasound commonly uses curvilinear probes.  Extending WEMVA to these probes requires the wave-propagation model to account for the curved transducer geometry rather than treating the aperture as planar.  I have previously extended the angular spectrum method used in RTM to a polar coordinate system for curvilinear arrays {% cite Ali2022CurvilinearAngularSpectrumMethod %}.  The formulation propagates the transmitted and received wavefields in the polar geometry of the curved probe, while retaining the Fourier-domain efficiency of the angular spectrum method.  This provides the wave-propagation engine needed to apply RTM and WEMVA directly to curvilinear abdominal acquisitions.  The underlying curvilinear angular-spectrum formulation was validated against Field II simulations and demonstrated using in-vivo abdominal channel data.  Combining this propagation model with WEMVA would enable sound speed estimation and aberration correction using conventional curvilinear abdominal imaging probes.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Siemens5C1_TimeDomain.gif" title="Siemens5C1_TimeDomain" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/FocusedTxSyntheticAperture.png" title="FocusedTxSyntheticAperture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Curvilinear Extension of the Angular Spectrum Method in Reverse-Time Migration and its Application to Liver + Kidney Imaging {% cite Ali2022CurvilinearAngularSpectrumMethod %}.
</div>

<br>
