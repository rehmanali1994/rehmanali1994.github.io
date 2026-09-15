---
layout: page
title: 3D FWI
description: Fast, scalable, and accurate implementations/approximations of the 3D wave equation + UST/USCT systems to support 3D FWI
img: assets/img/MultiRowRingArray.png
importance: 3
category: Full-Waveform Inversion (FWI) for UST/USCT
related_publications: true
---

### 3D Full-Waveform Inversion (FWI) for Ultrasound Computed Tomography (UST/USCT)

Full-waveform inversion (FWI) provides a framework for reconstructing quantitative acoustic properties of tissue by explicitly modeling the propagation of ultrasound through the imaging volume.  In ultrasound computed tomography (USCT/UST), this can provide high-resolution maps of sound speed and other acoustic parameters, but accurate 3D FWI is substantially more challenging than conventional 2D reconstruction.  Most practical USCT systems use ring arrays with elevation-focused transducers.  A common reconstruction strategy treats each position of the ring array independently and performs 2D slicewise FWI before stacking the reconstructed slices into a volume. While computationally convenient, this approach does not account for wave propagation in the elevation direction or the finite elevation focusing of the transducers.  My goal is to simultaneously develop 3D FWI techniques that explicitly account for the actual 3D wave propagation and develop a multi-row ring-array acquisition geometry that can best leverage 3D FWI for volumetric imaging.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ElevationFocusing.png" title="ElevationFocusing" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/MultiRowRingArray.png" title="MultiRowRingArray" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/MultiRowRingArrayDesign.png" title="MultiRowRingArrayDesign" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Current 2D Slicewise FWI Enabled by Elevation-Focused Ring-Array Transducer vs. Envisioned Multi-Row Ring-Array Transducer Design.
</div>

### From 2D Slicewise FWI to 3D FWI

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2025_3DFWI.png" title="Ali2025_3DFWI" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    Comparison of 2D slicewise to 3D FWI with simulated multi-row ring array {% cite Ali2025_3DFWI %}. Cylindrical wave transmits from a multi-row ring-array (32 rows; 256 elements per row; 22 cm diameter; 2.4 mm between rows) were simulated in three different numerical breast phantoms. Orthographic slice views of the reconstructed volumes intersect at suspicious high sound speed masses in each phantom (cancers in phantoms 1 and 2, and dense breast tissue in phantom 3). Each sound speed images is displayed in grayscale from 1400 to 1600 m/s: (Left Column) ground-truth sound speed image; (Middle Column) volume reconstructed using 2D slicewise FWI; (Right Column) volume reconstructed using 3D FWI.
</div>

A natural way to obtain true volumetric FWI is to replace the conventional single-row ring array with a multi-row ring array.  The additional rows provide three-dimensional illumination of the breast, while the full-wave model accounts for propagation both within and between the imaging planes.  Simulations with multi-row ring-array data demonstrated the limitations of 2D slicewise reconstruction.  Although slicewise FWI can recover the general structure of the sound-speed distribution, it cannot correctly model the out-of-plane propagation and therefore produces errors in the reconstructed volume.  Note that this particular slicewise reconstruction is significantly worse than it would be with an elevation-focused ring-array because no effort is made to collimate the ultrasound to a thin volume that can effectively be treated as a slice.

In contrast, 3D FWI uses the complete multi-row dataset and a 3D wave-equation model. The reconstructed sound-speed distributions more closely reproduce the ground truth, particularly around suspicious high-sound-speed structures such as breast lesions and regions of dense tissue. {% cite Ali2025_3DFWI %}.  These results demonstrate that moving from 2D slicewise FWI to true 3D inversion is not simply a matter of adding more slices: the forward model itself must account for the three-dimensional physics of the acquisition.

### Making 3D FWI Computationally Practical

The main obstacle to routine 3D FWI is computational cost. In the frequency domain, each FWI iteration requires repeatedly solving the 3D Helmholtz equation for many source locations and frequencies.  Directly factorizing and solving these large sparse systems quickly becomes prohibitively expensive in both memory and computation.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/HelmholtzMatrixBlocks.png" title="HelmholtzMatrixBlocks" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/HelmholtzMatrixBlockLU.png" title="HelmholtzMatrixBlockLU" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/HelmholtzMatrixApplyLU.png" title="HelmholtzMatrixApplyLU" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Ali2024OneWayDecomposition.png" title="Ali2024OneWayDecomposition" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Block LU Factorization of the Helmholtz Equation and Its Interpretation as a Cascade of One-Way Sweeps {% cite Ali2024_BlockLU_2DFWI %}.
</div>

I began investigating structured approaches to solving the 2D Helmholtz equation that exploit the relationship between its block structure and one-way wave propagation.  The block LU factorization of the 2D Helmholtz system reveals the solution as a cascade of one-way sweeps {% cite Ali2024_BlockLU_2DFWI %}.  While the block LU factorization is no longer computationally tractable in 3D, the decomposition into one-way sweeps continues to extend nicely into the 3D Helmholtz equation.  This connection provides both a useful interpretation of the numerical linear algebra and a route toward more efficient wave-equation solvers for 3D FWI.

### One-Way Wave Equations as an Approximation

The connection between block LU factorization and one-way wave equations suggests a further approximation.  Instead of performing the full block factorization, the original 3D Helmholtz equation operator can be decomposed into a cascade of one-way wave equation operators.  Phase-shift-plus-interpolation (PSPI) provides an efficient way to implement these one-way operators in heterogeneous media.  By performing wave propagation primarily in the Fourier domain, the approach can substantially reduce the memory and computational requirements associated with full 3D wave-equation modeling.  The goal is therefore not simply to replace the full wave equation with a less accurate approximation, but to identify where the computational structure of the full problem can be exploited without losing the wave-physics needed for quantitative reconstruction.  Together, these developments address two complementary requirements for 3D FWI in USCT: an accurate representation of the 3D acquisition physics and scalable methods for solving the resulting wave equation.

<div class="row justify-content-sm-center">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/OneWayLU.png" title="OneWayLU" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/WavefieldsLU.png" title="OneWayLUvsBlockLU" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/OneWayLUvsBlockLU.png" title="OneWayLUvsBlockLU" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption" style="text-align: justify;">
    One-Way Wave Equations as the PDE-Equivalent of the LU Decomposition {% cite Ali2024OneWayDecomposition %}.  Phase-shift-plus-interpolation (PSPI) is an extension of the Fourier split-step method used to implement the one-way wave equations more accurately.  This numerical method could lead to a much more memory and computation efficient implementation of 3D FWI.
</div>

<b>


