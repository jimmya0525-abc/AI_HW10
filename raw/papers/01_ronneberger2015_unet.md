# U-Net: Convolutional Networks for Biomedical Image Segmentation

- **Authors**: Olaf Ronneberger, Philipp Fischer, Thomas Brox
- **Affiliation**: Computer Science Department and BIOSS Centre for Biological Signalling Studies, University of Freiburg, Germany
- **Venue**: Medical Image Computing and Computer-Assisted Intervention (MICCAI 2015)
- **DOI / ArXiv**: arXiv:1505.04597

## Abstract
There is large consent that successful training of deep networks requires many thousand annotated training samples. In this paper, we present a network and training strategy that relies on the strong use of data augmentation to use the available annotated samples more efficiently. The architecture consists of a contracting path to capture context and a symmetric expanding path that enables precise localization. We show that such a network can be trained end-to-end from very few images and outperforms the prior best method (a sliding-window convolutional network) on the ISBI challenge for segmentation of neuronal structures in electron microscopic stacks. Using the same network trained on transmitted light microscopy images (phase contrast and DIC), we won the ISBI cell tracking challenge 2015 in these categories by a large margin. Moreover, the network is fast: segmentation of a 512x512 image takes less than a second on a recent GPU.

## Core Architecture & Methodology
1. **Encoder-Decoder with Skip Connections**:
   - Contracting path (left side): Repeated application of two 3x3 convolutions (unpadded), each followed by a rectified linear unit (ReLU) and a 2x2 max pooling operation with stride 2 for downsampling. At each downsampling step, feature channels are doubled.
   - Expanding path (right side): Up-convolution (transposed convolution) of 2x2 halving the number of feature channels, concatenation with the correspondingly cropped feature map from the contracting path, and two 3x3 convolutions followed by ReLU.
2. **Skip Connections Role**:
   - Directly propagates high-resolution spatial feature representations from contracting layers to expanding layers, preserving sharp boundary information that is otherwise lost during pooling.
3. **Loss Formulation & Energy Function**:
   - Pixel-wise soft-max combined with cross-entropy loss:
     $$E = \sum_{\mathbf{x} \in \Omega} w(\mathbf{x}) \log(p_{k(\mathbf{x})}(\mathbf{x}))$$
   - Weight map $w(\mathbf{x})$ introduced to compensate for class frequency and separate touching objects:
     $$w(\mathbf{x}) = w_c(\mathbf{x}) + w_0 \cdot \exp\left(-\frac{(d_1(\mathbf{x}) + d_2(\mathbf{x}))^2}{2\sigma^2}\right)$$
4. **Data Augmentation**:
   - Heavy elastic deformations using random displacement vectors on a coarse grid, crucial for biomedical imaging where soft tissue exhibits natural geometric variations.

## Relevance to Ultrasound Imaging
- The U-Net architecture has served as the baseline backbone for virtually all medical ultrasound segmentation tasks (breast tumors, cardiac left ventricle, thyroid nodules, fetal biometry).
- The skip-connection design directly addresses ultrasound's severe boundary blurring, low contrast-to-noise ratio (CNR), and acoustic acoustic shadow artifacts by fusing contextual semantics with localized acoustic edge gradients.
