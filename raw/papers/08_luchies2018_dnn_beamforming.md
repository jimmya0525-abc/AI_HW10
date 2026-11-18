# Deep Neural Networks for Ultrasound Beamforming

- **Authors**: Adam C. Luchies, Brett C. Byram
- **Affiliation**: Department of Biomedical Engineering, Vanderbilt University, Nashville, TN, USA
- **Venue**: IEEE Transactions on Ultrasonics, Ferroelectrics, and Frequency Control (TUFFC), Vol. 65, No. 5, May 2018
- **DOI**: 10.1109/TUFFC.2018.2809541

## Abstract
Ultrasound beamforming combines raw radio frequency (RF) signals received across an aperture of transducer elements into a coherent B-mode image. Conventional Delay-and-Sum (DAS) beamforming assumes a homogeneous acoustic speed of sound and suffers from acoustic clutter, phase aberration, and limited contrast resolution due to off-axis scattering. Adaptive beamformers, such as Minimum Variance (Capon) beamforming, improve resolution but incur $O(M^3)$ computational complexity and exhibit sensitivity to signal cancellation. We propose a deep neural network (DNN) framework trained directly on raw delayed RF channel data to perform beamforming. The neural network learns the non-linear mapping from multi-channel pre-beamformed RF data to high-contrast, clutter-free target echoes, outperforming DAS in lateral resolution, contrast ratio, and lesion detectability without the severe computational penalties of matrix inversion.

## Beamforming Fundamentals & Formulation
1. **Classical Delay-and-Sum (DAS)**:
   $$s(t, \mathbf{x}_p) = \sum_{m=1}^{M} w_m \cdot y_m(t - \tau_m(\mathbf{x}_p))$$
   where $M$ is the number of transducer elements, $y_m$ is the RF signal received by element $m$, $\tau_m(\mathbf{x}_p)$ is the acoustic geometric flight time delay from focus $\mathbf{x}_p$ to element $m$, and $w_m$ is an apodization window (e.g. Hanning).
2. **Failure Modes in In Vivo Tissue**:
   - **Phase Aberration**: Inhomogeneous sound speed in heterogeneous layers (fat $c \approx 1450\,\text{m/s}$, muscle $c \approx 1580\,\text{m/s}$) creates destructive interference.
   - **Acoustic Clutter**: Off-axis reverberation and multi-path scattering corrupt low-echogenicity cysts and vascular lumens.
3. **Deep Learning Beamformer Architecture**:
   - Fully Connected and Convolutional Deep Networks taking $M$-channel delayed RF vectors $\mathbf{Y} \in \mathbb{R}^{M \times K}$ as input.
   - Trained against synthetic Field II ultrasound simulations or high-quality coherent plane-wave compounding targets.
   - Loss function combines Mean Squared Error (MSE) and envelope Contrast-to-Noise Ratio (CNR) regularization:
     $$\mathcal{L} = \frac{1}{N}\sum \|\hat{s} - s_{\text{clean}}\|^2 + \gamma \cdot \mathcal{L}_{\text{contrast}}$$
4. **Experimental Findings**:
   - Contrast ratio improved by up to 14.8 dB compared to standard DAS.
   - Reduced full-width at half-maximum (FWHM) of point targets by 40-50%, demonstrating superior lateral resolution.
   - Demonstrated feasibility of executing high-resolution beamforming in real-time on GPU/FPGA hardware for edge and handheld ultrasound devices.
