---
layout: page
title: Making FWI Robust Against False Minima
description: Variants of FWI robust against false minima caused by cycle skipping
img: assets/img/CycleSkipping.png
importance: 3
category: Full-Waveform Inversion (FWI) for UST/USCT
related_publications: true
---

### Cycle Skipping in FWI

Full-waveform inversion is highly sensitive to the starting model.  When the predicted and measured waveforms are shifted by more than half a cycle, the FWI objective function develops local minima and the inversion can converge toward the wrong solution.  This phenomenon, known as cycle skipping, is particularly problematic in ultrasound tomography because the sound-speed contrast between the initial model and tissue can be large.

The standard way to reduce cycle skipping is to begin the inversion at low frequencies and progressively introduce higher frequencies.  Low-frequency waveforms have longer periods, making the inversion less sensitive to the initial travel-time error.  However, ultrasound transducers are often designed for higher-frequency imaging and may have insufficient bandwidth at the frequencies needed to initialize FWI.  The examples below illustrate this problem.  In transcranial ultrasound tomography, FWI can converge successfully when sufficiently low-frequency data are available, but starting at a higher frequency produces cycle-skipping artifacts.  Similar artifacts emerge in breast ultrasound tomography as the starting frequency is increased.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/CycleSkipping.png" title="CycleSkipping" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2023HomogeneousStartingModelFWI.png" title="Ali2023HomogeneousStartingModelFWI" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2023StartingModelFWI.png" title="Ali2023StartingModelFWI" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Cycle Skipping in FWI.  (Top Left) Schematic.  (Top Right) Transcranial UST simulation where cycle skipping occur starting at 300 kHz but not 100 kHz {% cite Ali2023HomogeneousStartingModelFWI %}.  (Bottom) Emergence of artifacts as the starting frequency of FWI increases in a breast UST simulation {% cite Ali2023StartingModelFWI %}.
</div>

### Frequency-Difference FWI (FD-FWI)

To overcome the lack of low-frequency measurements, I developed a frequency-differencing approach that synthesizes low-frequency signals from the available high-frequency data.  The key observation is that signals at two different frequencies can be combined to produce a signal at their frequency difference (or beat frequency).  When the two frequencies are close together, the difference frequency can be substantially lower than either measured frequency.These synthesized low-frequency signals can then be used to initialize FWI before progressively returning to the original measured frequencies.  This approach effectively creates the low-frequency information needed to avoid cycle skipping without requiring the transducer to operate outside its normal bandwidth.  In simulations and phantom experiments, frequency differencing produced substantially improved reconstructions compared with starting FWI directly from a homogeneous sound-speed model.  

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/FrequencyDifferenceFWI.png" title="FrequencyDifferenceFWI" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2024FrequencyDifferenceFWI.png" title="Ali2024FrequencyDifferenceFWI" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Frequency-Difference FWI (FD-FWI) Overcomes Cycle Skipping in Simulations and Phantom Experiments {% cite Ali2024FrequencyDifferenceFWI %}.  Data-domain frequency differencing refers to the generation of low-frequency data via frequency-differencing without changing the FWI forward model.  Data domain frequency differencing was performed using multiple frequency pairs.  On the other hand, model-domain frequency differencing (or FD-FWI) incorporates frequency differencing directly into the forward model.  However, the initial implementation of model-domain frequency differencing was restricted to a single frequency pair due to computational complexity; this ultimately limited the stability of model-domain frequency differencing.  Later, FD-FWI was reimplemented using multiple frequency pairs {% cite Klaben2026JAX %}, improving the stability of FD-FWI.
</div>

An important distinction is between data-domain and model-domain frequency differencing.  In the data-domain approach, low-frequency data are generated from multiple frequency pairs in the measured signals and then supplied to an otherwise conventional FWI algorithm {% cite Ali2025FrequencyDifferencing %}.  In the model-domain formulation, also known as frequency-difference FWI (FD-FWI), frequency differencing is incorporated directly into the forward model used during inversion.  The initial model-domain implementation was computationally limited to a single frequency pair, which reduced the stability of the approach {% cite Ali2024FrequencyDifferenceFWI %}.  Subsequent work extended the formulation to multiple frequency pairs, providing a more stable implementation of FD-FWI while retaining the benefits of model-domain frequency differencing {% cite Klaben2026JAX %}.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/FrequencyDifferencingInSilico.png" title="FrequencyDifferencingInSilico" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/FrequencyDifferencingInVitro.png" title="FrequencyDifferencingInVitro" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2025FrequencyDifferencing.png" title="Ali2025FrequencyDifferencing" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/TranscranialFrequencyDifferencing.png" title="TranscranialFrequencyDifferencing" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2024FrequencyDifferencing.png" title="Ali2024FrequencyDifferencing" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Data-Domain Frequency-Differencing Method to Kickstart FWI Without Cycle Skipping {% cite Ali2024FrequencyDifferencing Ali2025FrequencyDifferencing %}.
</div>

A particularly useful application of frequency differencing is to use the synthesized low-frequency data only to generate a better starting model. FWI is first performed on the extrapolated low-frequency data, and the resulting sound-speed distribution is then supplied as the initial model for conventional FWI using the measured data.  This separates the two roles of the inversion: the synthesized low frequencies provide the large-scale information needed to avoid cycle skipping, while the measured high-frequency data provide the resolution needed for the final reconstruction.  In breast phantom experiments, this strategy substantially improved the recovered sound-speed values compared with FWI initialized from a homogeneous model. The reconstructed background, lesion, and cyst sound speeds were all brought much closer to their expected values.  Importantly, the approach can be used with the transducer's normal operating frequency. This avoids the practical limitations of deliberately exciting the transducer at frequencies far below its nominal bandwidth, while still providing FWI with the low-frequency information needed to initialize the inversion.


### Low-Frequency Extrapolation Beyond Frequency Differencing

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/LowFrequencyExtrapolation.png" title="LowFrequencyExtrapolation" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Owolabi2026LowFrequencyExtrapolation.png" title="Owolabi2026LowFrequencyExtrapolation" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Least-Squares Autoregressive Model for Low-Frequency Extrapolation to Overcome Cycle Skipping in FWI {% cite Owolabi2026LowFrequencyExtrapolation %}.
</div>

Frequency differencing is one way to overcome the lack of low-frequency information, but it is not the only possible approach.  I have also explored low-frequency extrapolation using a least-squares autoregressive model, which estimates missing low-frequency content directly from the measured signal spectrum.  The underlying goal is the same: construct a starting model that contains the large-scale structure of the acoustic medium before introducing the higher frequencies responsible for fine spatial detail.

### Frequency-Difference FWI (FD-FWI) vs. Adaptive Waveform Inversion (AWI)

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/FDFWI.png" title="FDFWI" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/AWI.png" title="AWI" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Cycle-Skipping-Robust FWI: Frequency-Difference Full-Waveform Inversion (FD-FWI) vs. Adaptive Waveform Inversion (AWI) {% cite Klaben2026JAX %}.
</div>

Adaptive waveform inversion (AWI) represents another strategy to overcome cycle skipping.  Rather than focus on extrapolating low-frequency signals, AWI circumvents cycle skipping by modeling the transformation from measured to simulated signals as a filter.  If the simulated and measured signals are correctly aligned, the required transformation is simply an identity filter—a delta function at zero time lag.  Therefore, the goal of AWI is to drive that filter towards a zero-lag delta function.  The AWI objective penalizes energy in the filter away from zero lag rather than directly minimizing the sample-by-sample waveform difference. This changes the shape of the inversion objective and makes it much less susceptible to the local minima caused by cycle skipping in FWI.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Klaben2026JAX_BreastOnly.png" title="Klaben2026JAX_BreastOnly" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Frequency-Difference Full-Waveform Inversion (FD-FWI) and Adaptive Waveform Inversion (AWI) vs Conventional FWI in Numerical Breast Phantom at 400 kHz {% cite Klaben2026JAX %}.
</div>

Here FD-FWI and AWI are compared with conventional FWI in numerical breast and transcranial imaging phantoms {% cite Klaben2026JAX %}.  The comparison highlights two fundamentally different approaches to the same problem: FD-FWI constructs a low-frequency surrogate model to improve convergence towards the global minimum, whereas AWI modifies the data-matching objective so that inversion can proceed without requiring those low frequencies.  AWI is ultimately the more robust strategy.  We theorize that AWI better preserves the true global minimum of FWI while creating a cycle-skipping-free path to that minimum

<div class="row justify-content-sm-center">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/NumericalBrainPhantom.png" title="NumericalBrainPhantom" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/NumericalBrainPhantomResults.png" title="NumericalBrainPhantomResults" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Frequency-Difference Full-Waveform Inversion (FD-FWI) and Adaptive Waveform Inversion (AWI) vs Conventional FWI in Numerical Transcranial Imaging Phantom at 100 and 200 kHz {% cite Klaben2026JAX Singh2026TranscranialUST Mitcham2025TranscranialUST Ali2023HomogeneousStartingModelFWI %}.
</div>

### Alternative and Future Strategies

In addition to AWI, optimal transport is another promising approach to overcome cycle skipping.  Optimal transport essentially involves converting the measured and simulated waveforms into probability density functions (PDF), which are then converted to cumulative density functions (CDF).  There are several ways to transform the waveforms into PDF, including using the absolute value, the envelope of the signal, separating positive and negative lobes of the signal, introducing a constant offset, exponentiation, etc.  Similarly there are different norms that can be applied between the resulting CDFs such as the direct least-squares difference, Wasserstein-1, and Wasserstein-2 norms.

Other approaches include learned low-frequency extrapolation and learning the optimal transformation of the ultrasound waveform that best preserves the solution to the inverse problem while circumventing cycle skipping.  Rather than requiring hardware capable of measuring sufficiently low frequencies, learned transformations could potentially extract or synthesize the information needed to constrain the long-wavelength structure of the sound speed reconstruction.  Together, these approaches point toward a broader class of strategies for making FWI less dependent on low-frequency measurements and less sensitive to the choice of starting model.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/OtherCycleSkippingRobustTechniques.png" title="OtherCycleSkippingRobustTechniques" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Other Proposed Cycle-Skipping Robust Formulations of FWI: (1) Optimal Transport, (2) Learned Low-Frequency Extrapolation, and (3) Learning the Optimal Transformation of the Ultrasound Signal.
</div>

<b>
