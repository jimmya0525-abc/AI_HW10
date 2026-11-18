# Ultrafast Ultrasound Localization Microscopy for Deep Super-Resolution Vascular Imaging (ULM)

- **Authors**: Claudia Errico, Juliette Pierre, Sophie Pezet, Yann Desailly, Zsolt Lenkei, Olivier Couture, Mickael Tanter
- **Affiliation**: Institut Langevin, ESPCI Paris, CNRS UMR 7587, INSERM U979; Brain Plasticity Unit, CNRS UMR 8249, Paris, France
- **Venue**: Nature 527, 499–502 (November 2015)
- **DOI**: 10.1038/nature15707

## Abstract
In vivo optical microscopy methods are fundamentally limited by photon scattering, restricting sub-wavelength resolution imaging to depths of a few hundred micrometres. Ultrasound can image deep within organs, but acoustic diffraction imposes a fundamental physical trade-off between spatial resolution and penetration depth (typically $\sim 150\,\mu\text{m}$ resolution at $15\,\text{MHz}$ probe frequency). Inspired by optical photoactivated localization microscopy (PALM/STORM), we introduce Ultrafast Ultrasound Localization Microscopy (ULM). By tracking millions of intravenously injected biocompatible microbubble contrast agents moving through the vascular tree using ultrafast plane-wave imaging ($>1,000$ frames per second), we achieve non-invasive, deep-tissue super-resolution vascular imaging in vivo at microscopic scale ($\sim 10\,\mu\text{m}$), overcoming the wave diffraction limit by more than an order of magnitude.

## Theoretical Principles & Algorithm
1. **The Acoustic Wave Diffraction Limit**:
   - Classical lateral resolution dictated by Rayleigh or Abbe criterion:
     $$R = \frac{\lambda \cdot F}{D} \approx 1.22 \frac{c \cdot z}{f_0 \cdot D}$$
     where $\lambda$ is acoustic wavelength, $c$ is speed of sound ($\approx 1540\,\text{m/s}$ in soft tissue), $f_0$ is transducer center frequency, $z$ is depth, and $D$ is aperture size.
   - For a 15 MHz transducer, $\lambda \approx 100\,\mu\text{m}$, precluding visualization of microcapillaries ($5-10\,\mu\text{m}$).
2. **Super-Localization Principle**:
   - Gas-filled lipid-shelled microbubbles (e.g. Sonovue, Definity, diameter $1-3\,\mu\text{m}$) act as isolated point scatterers.
   - When microbubble concentration is sparse, each echo corresponds to the Point Spread Function (PSF) of the imaging system.
   - The centroid of the microbubble echo is localized with sub-pixel precision using 2D Gaussian fitting or radial symmetry:
     $$\sigma_{\text{localization}} \approx \frac{\text{FWHM}}{\sqrt{N_{\text{photons/echoes}}}}$$
3. **Ultrafast Plane Wave Imaging**:
   - Steering unfocused plane waves at high pulse repetition frequencies (1,000 to 10,000 Hz) captures bubble trajectories across cardiac cycles without motion blurring.
   - Singular Value Decomposition (SVD) spatiotemporal clutter filtering separates slowly moving tissue background echoes from fast-moving intravascular microbubble echoes.
4. **Trajectory Tracking & Vessel Density Reconstruction**:
   - Hungarian algorithm or Kalman filter links localized centroids across frames into continuous streamlines.
   - Measures blood flow velocity vectors and microvascular density, resolving cerebral capillaries and tumor neoangiogenesis.
5. **Modern AI / Deep Learning Extensions**:
   - High-density microbubble separation using deep convolutional networks (e.g., Deep-ULM, ULM-Net) to resolve overlapping PSFs and accelerate acquisition time by 10x-100x.
