# SAMUS: Adapting Segment Anything Model for Clinically-Friendly Ultrasound Image Segmentation

- **Authors**: Xian Lin, Xiangde Luo, Yang Chen, Kai Huang, Guanbin Li, Guoyan Zheng
- **Affiliation**: Shanghai Jiao Tong University; Sun Yat-sen University; SenseTime Research
- **Venue**: IEEE Transactions on Medical Imaging (TMI), 2023 / arXiv:2309.06824
- **DOI / ArXiv**: arXiv:2309.06824

## Abstract
The Segment Anything Model (SAM) has emerged as a groundbreaking foundation model for natural image segmentation. However, directly applying SAM to ultrasound images leads to significant performance degradation due to modality discrepancies: ultrasound features low signal-to-noise ratio, speckle noise, blurred anatomical boundaries, and operator-dependent artifacts. Furthermore, SAM requires heavy computational resources (ViT-H backbone), making real-time clinical deployment impractical. In this work, we propose SAMUS, a universal, clinically-friendly adaptation of SAM tailored for ultrasound image segmentation. SAMUS introduces a Cross-Branch Attention (CBA) adapter module that injects ultrasound-specific inductive biases into the frozen image encoder, alongside a lightweight CNN branch to capture low-level local acoustic boundaries. Comprehensive experiments across 7 ultrasound datasets (covering breast, thyroid, cardiac, musculoskeletal, and fetal domains) demonstrate that SAMUS substantially outperforms direct SAM zero-shot prompting and rivals task-specific fully supervised networks with far fewer trainable parameters.

## Core Innovations & Architecture
1. **Motivation & Domain Gap**:
   - Natural images have clear continuous object boundaries and high RGB contrast.
   - Ultrasound images exhibit acoustic reverberation, refraction, speckle noise, acoustic shadows, and tissue attenuation. SAM's global attention overfits to salient natural patterns and misses faint acoustic interfaces.
2. **Dual-Branch Architecture**:
   - **Foundation Transformer Branch (Frozen SAM ViT)**: Preserves generalized structural representations learned from 11 million natural images.
   - **CNN Spatial Feature Branch**: Lightweight convolutional network processing high-resolution raw ultrasound frames to extract high-frequency acoustic texture and edge gradients.
3. **Cross-Branch Attention (CBA) & Adapter**:
   - Position-aware adapter layers inserted between Transformer blocks.
   - Cross-attention mechanism fusing local acoustic gradients with global semantic embeddings without updating the multi-gigabyte foundation weights.
4. **Prompting Flexibility**:
   - Supports single-point, multi-point, bounding-box, and prompt-free automatic segmentation modes.
5. **Experimental Results**:
   - Benchmarked across BUSI, TN3K, CAMUS, DDTI, and private clinical cohorts.
   - Achieved 88.4% mean Dice across multi-organ datasets, outperforming MedSAM by 4.2% and vanilla SAM by over 15.6%.
   - Parameter efficiency: Updates only ~3.2% of total SAM parameters during adaptation.
