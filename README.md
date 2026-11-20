# SPHEREx_ice_map
Takes inputs from SPHEREx_cube.


An automated Python pipeline for processing 3D astronomical spectral datacubes.

Fits the ice bands in every pixel of a SPHEREx cube and turns them into column densities,
corrected for what the instrument does to a band it cannot resolve.

**How the bands are measured — the same fit for every ice**

* **Each ice in its own window, with its own baseline.** H2O in 2.42–3.82 $\mu$m, CO2 in
  4.00–4.45 $\mu$m, CO + OCN$^-$ in 4.45–4.85 $\mu$m. In each window in logspace the band(s) and a
  straight-line local baseline are fitted together, with the band amplitudes $\geq 0$.  The PAH 3.3/3.4 $\mu$m features are
  fitted first and removed from the spectrum.

* **Widths.** CO and OCN$^-$ are fixed (CO is unresolved by SPHEREx; OCN$^-$ is intrinsically
  ~26 cm$^{-1}$ wide). H2O (asymmetric Gaussian at 3.00 $\mu$m) and CO2 are free, but only within
  laboratory FWHM ranges — H2O 250–600 cm$^{-1}$, CO2 8–30 cm$^{-1}$ — broadened by the SPHEREx
  line spread (nominal $\lambda/R$ for the lower limit, the cube's broader effective line spread
  for the upper limit).
* **Band centres** are the laboratory wavelengths (H2O fixed at 3.00 $\mu$m) plus one shift you set
  for CO2, CO and OCN$^-$ (`band_shift_um`, header BANDSHFT); SPHEREx wavelengths can sit
  ~0.01 $\mu$m off.
* **OCN$^-$** is in the CO fit in every pixel, so it cannot borrow depth from CO or the reverse;
  its maps are kept only where CO is detected. CO is kept only where H2O is detected.


**What comes out**

`ice_maps_<target>.fits` (column, error, peak $\tau$, S/N, peak wavelength and correction flag per
ice, plus the baselines and the optical-depth cube), the same as a flat table in
`ice_maps_<target>.csv`, a PNG per map, and `continuum_diagnostics_<target>.pdf` with one page per
pixel — a random sample of the ice pixels plus the pixels where each band is strongest. 

Added also correction from Simulation



