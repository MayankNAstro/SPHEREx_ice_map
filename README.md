# SPHEREx_ice_map
Takes inputs from SPHEREx_cube 


An automated Python pipeline for processing 3D astronomical spectral datacubes (1.4–5.0 $\mu\mathrm{m}$).
It performs cosmic ray cleaning, PCHIP continuum fitting, conditional polycyclic aromatic hydrocarbon (PAH)
emission modeling, and optical depth ($\tau$) profile fitting to extract column densities of interstellar/circumstellar ices
($\mathrm{H_2O}$, $\mathrm{CO_2}$, and $\mathrm{CO}$). 

Features 
+++ Spike & Cosmic Ray Cleaning: Removes hot pixels and transient spikes using a rolling-median baseline combined 
with a Median Absolute Deviation (MAD) threshold. 

+++ Non-Parametric Continuum Modeling: Interpolates continuum levels across molecular band gaps using 
monotonic Piecewise Cubic Hermite Interpolating Polynomials (PchipInterpolator).

+++ S/N-Gated PAH Subtraction: Evaluates local signal-to-noise ratios (S/N) to conditionally fit 
single or double Gaussian profiles to $3.3\,\mu\mathrm{m}$ and $3.4\,\mu\mathrm{m}$ emission features before opacity conversion.

+++ Ice Opacity Fitting:Asymmetric Gaussian modeling for broad $3.0\,\mu\mathrm{m}$ $\mathrm{H_2O}$ ice. 

+++ Gaussian profile fitting for $4.25\,\mu\mathrm{m}$ $\mathrm{CO_2}$ and $4.65\,\mu\mathrm{m}$ $\mathrm{CO}$ ice bands.

Conversion of integrated optical depth to column densities ($\mathrm{molecules\ cm^{-2}}$) using intrinsic band strengths.

Comprehensive Diagnostic Outputs: Exports 2D FITS maps, publication-ready PNGs, 
pixel-by-pixel multi-page PDF diagnostics, and tabular CSV data with World Coordinate System (WCS) celestial positions.

Added correction factor based on simulation. 
